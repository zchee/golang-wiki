This page is meant to provide information to those who are developing LSP clients to integrate with `gopls`. Examples of such clients include [VSCode-Go](https://github.com/microsoft/vscode-go), [vim-go](https://github.com/fatih/vim-go), [govim](https://github.com/myitcv/govim), [emacs-lsp](https://github.com/emacs-lsp/lsp-mode), and many others. For a more complete list, see all of the editors that support gopls [here](https://github.com/golang/go/wiki/gopls#installation).

The best starting point for any integrator is the [Language Service Protocol Specification](https://microsoft.github.io/language-server-protocol/specification).
[`golang.org/x/tools/internal/lsp/protocol`](https://godoc.org/golang.org/x/tools/internal/lsp/protocol) represents a Go definition of the spec.

Feel free to add additional questions and answers here as they come up. To ask a question that isn't answered here, please reach out to the `gopls` developers either by filing an issue in the [Go issue tracker](https://github.com/golang/go/issues) or by sending a message to the `#gopls` channel in the [Gophers Slack](https://invite.slack.golangbridge.org/). 

# Table of Contents  
* [Supported Features](#supported-features)
* [UTF-8, UTF-16 and position information](#utf-8-utf-16-and-position-information)
* [`[]TextEdit` responses](#textedit-responses)
* [RPC response errors](#rpc-response-errors)
* [Files that change outside of the editor](#files-that-change-outside-of-the-editor)

## Supported features

The most accurate answer to this question is to examine the `InitializeResult` response to [`Initialize`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#initialize-request-leftwards_arrow_with_hook), specifically the `capabilities` field of type `ServerCapabilities`

## UTF-8, UTF-16 and position information

As an example, the [`Hover`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#hover-request-leftwards_arrow_with_hook) method takes [`TextDocumentPositionParams `](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#textdocumentpositionparams) which has a `position` field of type [`Position`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#text-documents). The key point to note from that last link is the following:

> A position inside a document (see Position definition below) is expressed as a zero-based line and character offset. The offsets are based on a UTF-16 string representation. So a string of the form a𐐀b the character offset of the character a is 0, the character offset of 𐐀 is 1 and the character offset of b is 3 since 𐐀 is represented using two code units in UTF-16. 

i.e. integrators will need to calculate UTF-16 based column offsets. For Go-based integrators, the [`golang.org/x/tools/internal/span`](https://godoc.org/golang.org/x/tools/internal/span#NewPoint) will be of use. [#31080](https://github.com/golang/go/issues/31080) tracks making `span` and other useful packages non-internal.

## `[]TextEdit` responses

At the time of writing (2019-07-15) the [`[]TextEdit`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#textedit) response to [`textDocument/formatting`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#document-formatting-request--leftwards_arrow_with_hook) and the [`WorkspaceEdit`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#workspaceedit) response to [`textDocument/rename`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#textDocument_rename) comprises range-based deltas. The spec is not explicit about how these deltas should be applied, instead simply stating:

> If multiple inserts have the same position, the order in the array defines the order in which the inserted strings appear in the resulting text.

All `[]TextEdit` are sorted such that applying the array of deltas received in reverse order achieves the desired result that holds with the spec.

## RPC response errors

https://go-review.googlesource.com/c/tools/+/170958 and related discussions are looking to help shape what it means for a server method to return an error. i.e. 

* Under what conditions would the `Format` method return an error? 
* On a syntax error, or just for low-level LSP/transport issues? 
* What should editors do in response to such errors?

This answer is therefore a WIP.

## Files that change outside of the editor

For example, files that are created/modified/removed as a result of `go generate`. Per [@ianthehat](https://github.com/ianthehat):

> The plan is to have the client do all the work for us. Specifically we are going to start using `workspace/didChangeWatchedFiles` to monitor all the files we are caching AST's for

This is currently not implemented (see [#31553](https://github.com/golang/go/issues/31553)).