What follows is a list of questions/ideas/suggestions for folks looking to integrate `gopls` within an editor/similar. 

A good starting point for any integrator is the [Language Service Protocol Specification](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md). [`golang.org/x/tools/internal/lsp/protocol`](https://godoc.org/golang.org/x/tools/internal/lsp/protocol) represents a Go definition of the spec. 

## What does `gopls` support?

The most accurate answer to this question is to examine the `InitializeResult` response to [`Initialize`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#initialize-request-leftwards_arrow_with_hook), specifically the `capabilities` field of type `ServerCapabilities`

## UTF-8, UTF-16 and position information

As an example, the [`Hover`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#hover-request-leftwards_arrow_with_hook) method takes [`TextDocumentPositionParams `](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#textdocumentpositionparams) which has a `position` field of type [`Position`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#text-documents). The key point to note from that last link is the following:

> A position inside a document (see Position definition below) is expressed as a zero-based line and character offset. The offsets are based on a UTF-16 string representation. So a string of the form a𐐀b the character offset of the character a is 0, the character offset of 𐐀 is 1 and the character offset of b is 3 since 𐐀 is represented using two code units in UTF-16. 

i.e. integrators will need to calculate UTF-16 based column offsets. For Go-based integrators, the [`golang.org/x/tools/internal/span`](https://godoc.org/golang.org/x/tools/internal/span#NewPoint) will be of use. [#31080](https://github.com/golang/go/issues/31080) tracks making `span` and other useful packages non-internal.

## `textDocument/formatting` response

At the time of writing (2019-03-28) the [`[]TextEdit`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#textedit) response to [`textDocument/formatting`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#document-formatting-request--leftwards_arrow_with_hook) comprises range-based deltas. The spec is not explicit about how these deltas should be applied, instead simply stating:

> If multiple inserts have the same position, the order in the array defines the order in which the inserted strings appear in the resulting text.

i.e. it specifies only the resulting state of the document. 

Applying the array of deltas received in reverse order achieves the desired result that holds with the spec.

## RPC response errors

https://go-review.googlesource.com/c/tools/+/170958 and related discussions are looking to help shape what it means for a server method to return an error. i.e. 

* Under what conditions would the `Format` method return an error? 
* On a syntax error, or just for low-level LSP/transport issues? 
* What should editors do in response to such errors?

This answer is therefore a WIP.

## Files that change "outside the editor"

For example, files that are created/modified/removed as a result of `go generate`. Per [@ianthehat](https://github.com/ianthehat):

> The plan is to have the client do all the work for us. Specifically we are going to start using `workspace/didChangeWatchedFiles` to monitor all the files we are caching AST's for

This is currently not implemented (see [#31553](https://github.com/golang/go/issues/31553)).