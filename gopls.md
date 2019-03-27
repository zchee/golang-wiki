`gopls` (pronounced: "go please") is an implementation of the Language Server Protocol (LSP) server for Go.
The LSP allows any text editor to be extended with IDE-like features (see https://langserver.org/ for details).

## Status

`gopls` is currently under active development by the Go team. The code is in the x/tools repository, in [golang.org/x/tools/internal/lsp](https://golang.org/x/tools/internal/lsp) and [golang.org/x/tools/cmd/gopls](https://golang.org/x/tools/cmd/gopls). Because we are actively working on `gopls`, it is not stable. If you choose to use it, be aware that things may regularly break or change.

## Installation

First, install `gopls` by running `go get -u golang.org/x/tools/cmd/gopls`. We suggest using VSCode with the Go plugin.

Turning off both build and vet on save is useful to avoid duplicating diagnostics from both gopls and VSCode-Go. `gopls` also runs both `gofmt` and `goimports`.

### Editors instructions
* VSCode, through the [VSCode-Go](https://github.com/microsoft/vscode-go) plugin, with the following configuration:
```json
"go.useLanguageServer": true,
"go.alternateTools": {
     "go-langserver": "gopls"
},
"go.languageServerExperimentalFeatures": {
    "format": true,
    "autoComplete": true,
    "goToDefinition": true,
    "hover": true,
    "signatureHelp": true,
    "goToTypeDefinition": true
},
"go.buildOnSave": "off",
"go.vetOnSave": "off",
"editor.formatOnSave": true,
"editor.codeActionsOnSave": {
    "source.organizeImports": true
},
```
* Vim, through [vim-go](https://github.com/fatih/vim-go), with the following configuration:
```
g:go_def_mode='gopls'
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
* Vim/Neovim, though [vim-lsp](https://github.com/prabirshrestha/vim-lsp/), with the following configuration:
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
" This works but is not officially supported
let g:ale_go_bingo_executable = 'gopls'
```
see [this issue](https://github.com/w0rp/ale/issues/2179)
* Emacs, through [lsp-mode](https://github.com/emacs-lsp/lsp-mode), with the following configuration:

```lisp
(use-package lsp-mode
  :commands lsp
  :init
  (lsp-register-client
   (make-lsp-client :new-connection (lsp-stdio-connection "gopls")
                    :major-modes '(go-mode)
                    :server-id 'gopls)))
``` 

## Contributing

Contributions are welcome, but since development is so active, we request that you file an issue and claim it before starting to work on something. Otherwise, it is likely that we might already be working on a fix for your issue. 

Please see all available issues under the [gopls label](https://github.com/golang/go/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+label%3Agopls) on the Go issue tracker. Any issue without an assignee and with the label "Suggested" is fair game - just assign yourself or comment on the issue before you begin working!

## FAQ

- **Why is it called `gopls`?** Since `gopls` works both as a language server and as a command line tool, we wanted a name that could be used as a verb. For example, `gopls check` should read as "go please check." See: [golang.org/cl/158197](https://golang.org/cl/158197).

## Integrator FAQ

What follows is a list of questions/ideas/suggestions for folks looking to integrate `gopls` within an editor/similar. 

A good starting point for any integrator is the [Language Service Protocol Specification](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md). [`golang.org/x/tools/internal/lsp/protocol`](https://godoc.org/golang.org/x/tools/internal/lsp/protocol) represents a Go definition of the spec. 

* **What does `gopls` support?** - the most accurate answer to this question is to examine the `InitializeResult` response to [`Initialize`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#initialize-request-leftwards_arrow_with_hook), specifically the `capabilities` field of type `ServerCapabilities`
* **UTF-8, UTF-16 and position information** - as an example, the [`Hover`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#hover-request-leftwards_arrow_with_hook) method takes [`TextDocumentPositionParams `](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#textdocumentpositionparams) which has a `position` field of type [`Position`](https://github.com/Microsoft/language-server-protocol/blob/gh-pages/specification.md#text-documents). The key point to note from that last link is the following:

> A position inside a document (see Position definition below) is expressed as a zero-based line and character offset. The offsets are based on a UTF-16 string representation. So a string of the form a𐐀b the character offset of the character a is 0, the character offset of 𐐀 is 1 and the character offset of b is 3 since 𐐀 is represented using two code units in UTF-16. 

i.e. integrators will need to calculate UTF-16 based column offsets. For Go-based integrators, the [`golang.org/x/tools/internal/span`](https://godoc.org/golang.org/x/tools/internal/span#NewPoint) will be of use. [#31080](https://github.com/golang/go/issues/31080) tracks making `span` and other useful packages non-internal.

## Additional Information

Questions can be directed toward [@stamblerre](https://github.com/stamblerre) or [@ianthehat](https://github.com/ianthehat). For consistent updates on the development progress of gopls, see the notes from the golang-tools meetings (https://github.com/golang/go/wiki/golang-tools).