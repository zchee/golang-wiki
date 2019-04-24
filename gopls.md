`gopls` (pronounced: "go please") is an implementation of the Language Server Protocol (LSP) server for Go.
The LSP allows any text editor to be extended with IDE-like features (see https://langserver.org/ for details).

## Status

`gopls` is currently under active development by the Go team. The code is in the x/tools repository, in [golang.org/x/tools/internal/lsp](https://golang.org/x/tools/internal/lsp) and [golang.org/x/tools/cmd/gopls](https://golang.org/x/tools/cmd/gopls). Because we are actively working on `gopls`, it is not stable. If you choose to use it, be aware that things may regularly break or change.

## Installation

First, install `gopls` by running `go get -u golang.org/x/tools/cmd/gopls`. We suggest using VSCode with the Go plugin.

Turning off both build and vet on save is useful to avoid duplicating diagnostics from both gopls and VSCode-Go. `gopls` also replicates the functionality of both `gofmt` and `goimports`.

### Editors instructions
* VSCode, through the [VSCode-Go](https://github.com/microsoft/vscode-go) plugin, with the following configuration:
```json5
"go.useLanguageServer": true,
"[go]": {
    "editor.snippetSuggestions": "none",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
        "source.organizeImports": true
    },
},
"gopls": {
    "usePlaceholders": true, // add parameter placeholders when completing a function
    "enhancedHover": true,   // experimental to improve quality of hover (will be on by default soon)
}
```

VSCode will complain about the `"gopls"` settings, but they will still work. Once we have a consistent set of settings, we will make the changes in the VSCode plugin necessary to remove the errors.

* Vim, through [vim-go](https://github.com/fatih/vim-go), with the following configuration:
```
let g:go_def_mode='gopls'
```
* Neovim, through [LanguageClient-neovim](https://github.com/autozimu/LanguageClient-neovim), with the following configuration:
```
" Launch gopls when Go files are in use
let g:LanguageClient_serverCommands = {
       \ 'go': ['gopls']
       \ }
" Run gofmt and goimports on save
autocmd BufWritePre *.go :call LanguageClient#textDocument_formatting_sync()
```
* Vim/Neovim, through [vim-lsp](https://github.com/prabirshrestha/vim-lsp/), with the following configuration:
```vim
augroup LspGo
  au!
  autocmd User lsp_setup call lsp#register_server({
      \ 'name': 'go-lang',
      \ 'cmd': {server_info->['gopls']},
      \ 'whitelist': ['go'],
      \ })
  autocmd FileType go setlocal omnifunc=lsp#complete
  "autocmd FileType go nmap <buffer> gd <plug>(lsp-definition)
  "autocmd FileType go nmap <buffer> ,n <plug>(lsp-next-error)
  "autocmd FileType go nmap <buffer> ,p <plug>(lsp-previous-error)
augroup END
```
* Vim, through [ale](https://github.com/w0rp/ale):
```vim
let g:ale_go_langserver_executable = 'gopls'
```
see [this issue](https://github.com/w0rp/ale/issues/2179)
* Emacs, through [lsp-mode](https://github.com/emacs-lsp/lsp-mode), with the following configuration:

```lisp
(use-package lsp-mode
  :commands lsp
  :config
  (lsp-register-client
   (make-lsp-client :new-connection (lsp-stdio-connection "gopls")
                    :major-modes '(go-mode)
                    :server-id 'gopls)))
``` 

* Vim through the experimental [`govim`](https://github.com/myitcv/govim), simply follow the [install steps](https://github.com/myitcv/govim/blob/master/README.md#govim---go-development-plugin-for-vim8).

## Contributing

Contributions are welcome, but since development is so active, we request that you file an issue and claim it before starting to work on something. Otherwise, it is likely that we might already be working on a fix for your issue. 

Please see all available issues under the [gopls label](https://github.com/golang/go/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+label%3Agopls) on the Go issue tracker. Any issue without an assignee and with the label "Suggested" is fair game - just assign yourself or comment on the issue before you begin working!

## FAQ

- **Why is it called `gopls`?** Since `gopls` works both as a language server and as a command line tool, we wanted a name that could be used as a verb. For example, `gopls check` should read as "go please check." See: [golang.org/cl/158197](https://golang.org/cl/158197).

## Integrator FAQ

What follows is a list of questions/ideas/suggestions for folks looking to integrate `gopls` within an editor/similar. 

A good starting point for any integrator is the [Language Service Protocol Specification](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md). [`golang.org/x/tools/internal/lsp/protocol`](https://godoc.org/golang.org/x/tools/internal/lsp/protocol) represents a Go definition of the spec. 

#### What does `gopls` support?

The most accurate answer to this question is to examine the `InitializeResult` response to [`Initialize`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#initialize-request-leftwards_arrow_with_hook), specifically the `capabilities` field of type `ServerCapabilities`

#### UTF-8, UTF-16 and position information

As an example, the [`Hover`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#hover-request-leftwards_arrow_with_hook) method takes [`TextDocumentPositionParams `](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#textdocumentpositionparams) which has a `position` field of type [`Position`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#text-documents). The key point to note from that last link is the following:

> A position inside a document (see Position definition below) is expressed as a zero-based line and character offset. The offsets are based on a UTF-16 string representation. So a string of the form a𐐀b the character offset of the character a is 0, the character offset of 𐐀 is 1 and the character offset of b is 3 since 𐐀 is represented using two code units in UTF-16. 

i.e. integrators will need to calculate UTF-16 based column offsets. For Go-based integrators, the [`golang.org/x/tools/internal/span`](https://godoc.org/golang.org/x/tools/internal/span#NewPoint) will be of use. [#31080](https://github.com/golang/go/issues/31080) tracks making `span` and other useful packages non-internal.

#### `textDocument/formatting` response

At the time of writing (2019-03-28) the [`[]TextEdit`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#textedit) response to [`textDocument/formatting`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#document-formatting-request--leftwards_arrow_with_hook) comprises range-based deltas. The spec is not explicit about how these deltas should be applied, instead simply stating:

> If multiple inserts have the same position, the order in the array defines the order in which the inserted strings appear in the resulting text.

i.e. it specifies only the resulting state of the document. 

Applying the array of deltas received in reverse order achieves the desired result that holds with the spec.

#### RPC response errors

https://go-review.googlesource.com/c/tools/+/170958 and related discussions are looking to help shape what it means for a server method to return an error. i.e. 

* Under what conditions would the `Format` method return an error? 
* On a syntax error, or just for low-level LSP/transport issues? 
* What should editors do in response to such errors?

This answer is therefore a WIP.

#### Files that change "outside the editor"

For example, files that are created/modified/removed as a result of `go generate`. Per [@ianthehat](https://github.com/ianthehat):

> The plan is to have the client do all the work for us. Specifically we are going to start using `workspace/didChangeWatchedFiles` to monitor all the files we are caching AST's for

This is currently not implemented (2019-04-15).

## Additional Information

Questions can be directed toward [@stamblerre](https://github.com/stamblerre) or [@ianthehat](https://github.com/ianthehat). For consistent updates on the development progress of gopls, see the notes from the golang-tools meetings (https://github.com/golang/go/wiki/golang-tools).