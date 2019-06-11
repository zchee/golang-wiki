`gopls` (pronounced: "go please") is an implementation of the Language Server Protocol (LSP) server for Go.
The LSP allows any text editor to be extended with IDE-like features (see https://langserver.org/ for details). It is currently in alpha, so it is not stable.

# Table of Contents  
[Status](#status)  
[Troubleshooting](#troubleshooting)  
[Installation](#installation)  
[Known Issues](#known-issues)  
[Contributing](#contributing)  
[FAQ](#faq)  
[Integrator FAQ](#integrator-faq)  
[Additional Information](#additional-information)  

## Status

`gopls` is currently under active development by the Go team. The code is in the x/tools repository, in [golang.org/x/tools/internal/lsp](https://golang.org/x/tools/internal/lsp) and [golang.org/x/tools/cmd/gopls](https://golang.org/x/tools/cmd/gopls). Because we are actively working on `gopls`, it is not stable. If you choose to use it, be aware that things may regularly break or change. For more `gopls` discussion, join the `#gopls` channel in the [Gopher Slack](https://invite.slack.golangbridge.org).

## Troubleshooting

If you see a `gopls` error or crash, or `gopls` just stops working, please capture your `gopls` log and file an issue on the [Go issue tracker](https://github.com/golang/go/issues/new?title=x%2Ftools%2Fcmd%2Fgopls%3A%20%3Cfill%20this%20in%3E). Please attach the log and any other relevant information, or if you have one, a case that reproduces the issue. For VSCode users, the `gopls` log can be found by going to "View: Debug Console" -> "Output" -> "Tasks" -> "gopls". 

If possible, it is helpful to mention an estimated timestamp for when the problem first occurred, or an approximate timestamp for when you reproduced the problem. It is also helpful to see your `gopls` editor configurations, such as a VSCode `settings.json` file. 

You can then try to restart your `gopls` instance by restarting your editor, which, in most cases, should correct the problem.

Feel free to ask questions about `gopls` on the `#gopls` [Gopher Slack](https://invite.slack.golangbridge.org) channel.

## Installation

First, install `gopls` by running `go get -u golang.org/x/tools/cmd/gopls`.

At the moment, we suggest using VSCode.

### Integration with your text editor

#### VSCode

Use the [VSCode-Go](https://github.com/microsoft/vscode-go) plugin, with the following configuration:

```json5
"go.useLanguageServer": true,
"go.languageServerExperimentalFeatures": {
        "diagnostics": true, // for build and vet errors as you type
        "findReferences": true // for finding in-package references
},
"[go]": {
    "editor.snippetSuggestions": "none",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
        "source.organizeImports": true
    }
},
"gopls": {
    "usePlaceholders": true // add parameter placeholders when completing a function
},
"files.eol": "\n", // formatting only supports LF line endings
```

VSCode will complain about the `"gopls"` settings, but they will still work. Once we have a consistent set of settings, we will make the changes in the VSCode plugin necessary to remove the errors.

If you encounter problems with import organization, please try setting a higher code action timeout (any value greater than 750ms), for example:

```go
"[go]": {
  "editor.codeActionsOnSaveTimeout": 3000
}
```

---

#### Vim / Neovim

Use [vim-go](https://github.com/fatih/vim-go) ver 1.20+, with the following configuration:

```
let g:go_def_mode='gopls'
let g:go_info_mode='gopls'
```

**or**

Use [LanguageClient-neovim](https://github.com/autozimu/LanguageClient-neovim), with the following configuration:

```
" Launch gopls when Go files are in use
let g:LanguageClient_serverCommands = {
       \ 'go': ['gopls']
       \ }
" Run gofmt and goimports on save
autocmd BufWritePre *.go :call LanguageClient#textDocument_formatting_sync()
```

**or**

Use [ale](https://github.com/w0rp/ale):

```vim
let g:ale_linters = {
	\ 'go': ['gopls'],
	\}
```

see [this issue](https://github.com/w0rp/ale/issues/2179)

**or**

Use [vim-lsp](https://github.com/prabirshrestha/vim-lsp/), with the following configuration:

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

**or**

Use [coc.nvim](https://github.com/neoclide/coc.nvim/), with the following `coc-settings.json` configuration:

```json
  "languageserver": {
    "golang": {
      "command": "gopls",
      "rootPatterns": ["go.mod", ".vim/", ".git/", ".hg/"],
      "filetypes": ["go"]
    }
  }
```

---

#### Vim (classic only)

Use the experimental [`govim`](https://github.com/myitcv/govim), simply follow the [install steps](https://github.com/myitcv/govim/blob/master/README.md#govim---go-development-plugin-for-vim8).

---

#### Emacs

Use [lsp-mode](https://github.com/emacs-lsp/lsp-mode). gopls is built in now as a client, so no special config is necessary. You first must install gopls and put it somewhere in your PATH. Here is an example (assuming you are using [use-package](https://github.com/jwiegley/use-package)) to get you started:

```lisp
(use-package lsp-mode
  :commands lsp)

(add-hook 'go-mode-hook #'lsp)

;; optional - provides fancier overlays
(use-package lsp-ui
  :commands lsp-ui-mode)

;; if you use company-mode for completion (otherwise, complete-at-point works out of the box):
(use-package company-lsp
  :commands company-lsp)
``` 

Common errors:
- Emacs must have your environment set properly (PATH, GOPATH, etc). You can run `M-x getenv <RET> PATH <RET>` to see if your PATH is set in Emacs. If not, you can try starting Emacs from your terminal, using [this package](https://github.com/purcell/exec-path-from-shell), or moving your shell config from .bashrc into .bashenv (or .zshenv).
- Make sure `lsp-mode`, `lsp-ui` and `company-lsp` are up-to-date, and make sure `lsp-go` is _not_ installed.

To troubleshoot, look in the `*lsp-log*` buffer for errors.

---

#### Acme

Use the experimental [`acme-lsp`](https://github.com/fhs/acme-lsp), simply follow the [install steps](https://github.com/fhs/acme-lsp#gopls).

---

#### Sublime Text

Use the [LSP](https://packagecontrol.io/packages/LSP) package. Once that is installed:

* Open the **Command Palette**
* Find and run the command **LSP: Enable Language Server Globally**
* Find the **gopls** item and select it. Be careful not to select the similarly named *golsp* by mistake.

After doing the above, you might want to take a look at the LSP package's settings files for reference. You can view them by selecting the menu item **Preferences > Package Settings > LSP > Settings**.

---

## Known Issues

* Cursor resets to the beginning or end of file on format: [#31937](https://github.com/golang/go/issues/31937).
* "no room in queue" error: [#32467](https://github.com/golang/go/issues/32467).

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