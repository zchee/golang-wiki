`gopls` (pronounced: "go please") is an implementation of the Language Server Protocol (LSP) server for Go.
The LSP allows any text editor to be extended with IDE-like features (see https://langserver.org/ for details). It is currently in alpha, so it is not stable. 

To install: `go get golang.org/x/tools/gopls@latest`.

For folks with questions about integrating gopls within an editor, see https://github.com/golang/go/wiki/gopls-integrator-FAQ.

# Table of Contents  
[Status](#status)  
[Troubleshooting](#troubleshooting)  
[Known Issues](#known-issues)  
[Installation](#installation)  
[Supported Features](#supported-features)  
[Contributing](#contributing)  
[FAQ](#faq)
[Additional Information](#additional-information)  

## Status

`gopls` is currently under active development by the Go team. The code is in the x/tools repository, in [golang.org/x/tools/internal/lsp](https://golang.org/x/tools/internal/lsp) and [golang.org/x/tools/cmd/gopls](https://golang.org/x/tools/cmd/gopls). Because we are actively working on `gopls`, it is not stable. If you choose to use it, be aware that things may regularly break or change. For more `gopls` discussion, join the `#gopls` channel in the [Gopher Slack](https://invite.slack.golangbridge.org).

## Troubleshooting

If you see a `gopls` error or crash, or `gopls` just stops working, please capture your `gopls` log and file an issue on the [Go issue tracker](https://github.com/golang/go/issues/new?title=x%2Ftools%2Fcmd%2Fgopls%3A%20%3Cfill%20this%20in%3E). Please attach the log and any other relevant information, or if you have one, a case that reproduces the issue. For VSCode users, the `gopls` log can be found by going to "View: Debug Console" -> "Output" -> "Tasks" -> "gopls". 

To increase the level of detail in your logs, start `gopls` with the `-rpc.trace` flag. To start a debug server that will allow you to see profiles and memory usage, start `gopls` with `serve --debug=localhost:6060`. See the editor configurations section below for information on how to pass these flags via your editor.

If possible, it is helpful to mention an estimated timestamp for when the problem first occurred, or an approximate timestamp for when you reproduced the problem. It is also helpful to see your `gopls` editor configurations, such as a VSCode `settings.json` file. 

You can then try to restart your `gopls` instance by restarting your editor, which, in most cases, should correct the problem. In VSCode, the easiest way to restart the language server is by opening the command palette (Ctrl + Shift + P) and selecting "Go: Restart Language Server".

Feel free to ask questions about `gopls` on the `#gopls` [Gopher Slack](https://invite.slack.golangbridge.org) channel.

## Known Issues

* Cursor resets to the beginning or end of file on format: [#31937](https://github.com/golang/go/issues/31937).
* Editing multiple modules in one editor window: [#32394](https://github.com/golang/go/issues/32394).
* Language features do not work with `cgo`: [#32898](https://github.com/golang/go/issues/32898).
* Does not work with build tags: [#29202](https://github.com/golang/go/issues/29202).
* Find references and rename only work in a single package: [#32869](https://github.com/golang/go/issues/32869), [#32877](https://github.com/golang/go/issues/32877).
* Completion does not work well after `go` or `defer` statements: [#29313](https://github.com/golang/go/issues/29313).

## Installation

First, install `gopls` by running `go get golang.org/x/tools/gopls@latest`.

At the moment, we suggest using VSCode.

### Integration with your text editor

#### VSCode

Use the [VSCode-Go](https://github.com/microsoft/vscode-go) plugin, with the following configuration:

```json5
"go.useLanguageServer": true,
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

```json5
"[go]": {
  "editor.codeActionsOnSaveTimeout": 3000
}
```

To enable more detailed debug information, add the following to your VSCode settings:

```json5
"go.languageServerFlags": [
    "-rpc.trace", // for more detailed debug logging
    "serve",
    "--debug=localhost:6060", // to investigate memory usage, see profiles 
],
```

You can disable features through the `"go.languageServerExperimentalFeatures"` section of the config. An example of a feature you may want to disable is `"documentLink"`, which opens Godoc links when you click on import statements in your file.

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

The `editor.action.organizeImport` code action will auto-format code and add missing imports. To run this automatically on save, add the following line to your `init.vim`:

```vim
autocmd BufWritePre *.go :call CocAction('runCommand', 'editor.action.organizeImport')
```

---

#### Vim (classic only)

Use the experimental [`govim`](https://github.com/myitcv/govim), simply follow the [install steps](https://github.com/myitcv/govim/blob/master/README.md#govim---go-development-plugin-for-vim8).

---

#### Emacs

Use [lsp-mode](https://github.com/emacs-lsp/lsp-mode). gopls is built in now as a client, so no special config is necessary. You first must install gopls and put it somewhere in your PATH. Here is an example (assuming you are using [use-package](https://github.com/jwiegley/use-package)) to get you started:

```lisp
(use-package lsp-mode
  :commands (lsp lsp-deferred))

(add-hook 'go-mode-hook #'lsp-deferred)

;; optional - provides fancier overlays
(use-package lsp-ui
  :commands lsp-ui-mode)

;; if you use company-mode for completion (otherwise, complete-at-point works out of the box):
(use-package company-lsp
  :commands company-lsp)
``` 

Common errors:
- When prompted by Emacs for your project folder, if you are using modules you must select the module's root folder (i.e. the directory with the "go.mod"). If you are using GOPATH, select your $GOPATH as your folder.
- Emacs must have your environment set properly (PATH, GOPATH, etc). You can run `M-x getenv <RET> PATH <RET>` to see if your PATH is set in Emacs. If not, you can try starting Emacs from your terminal, using [this package](https://github.com/purcell/exec-path-from-shell), or moving your shell config from .bashrc into .bashenv (or .zshenv).
- Make sure `lsp-mode`, `lsp-ui` and `company-lsp` are up-to-date, and make sure `lsp-go` is _not_ installed.

To troubleshoot, look in the `*lsp-log*` buffer for errors.

---

#### Acme

Use the experimental [`acme-lsp`](https://github.com/fhs/acme-lsp), simply follow the [install steps](https://github.com/fhs/acme-lsp#gopls).

---

#### Sublime Text

Use the [LSP](https://packagecontrol.io/packages/LSP) package. After installing it using Package Control, do the following:

* Open the **Command Palette**
* Find and run the command **LSP: Enable Language Server Globally**
* Select the **gopls** item. Be careful not to select the similarly named *golsp* by mistake.

Finally, you should familiarise yourself with the LSP package's *Settings* and *Key Bindings*. Find them under the menu item **Preferences > Package Settings > LSP**.

---

## Supported Features

* Autocompletion
* Jump to definition
* Signature help
* Hover
* Document symbols
* References
* Rename

## Contributing

Contributions are welcome, but since development is so active, we request that you file an issue and claim it before starting to work on something. Otherwise, it is likely that we might already be working on a fix for your issue. 

Please see all available issues under the [gopls label](https://github.com/golang/go/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+label%3Agopls) on the Go issue tracker. Any issue without an assignee and with the label "Suggested" is fair game - just assign yourself or comment on the issue before you begin working!

## FAQ

- **Why is it called `gopls`?** Since `gopls` works both as a language server and as a command line tool, we wanted a name that could be used as a verb. For example, `gopls check` should read as "go please check." See: [golang.org/cl/158197](https://golang.org/cl/158197).

## Additional Information

Questions can be directed toward [@stamblerre](https://github.com/stamblerre) or [@ianthehat](https://github.com/ianthehat). For consistent updates on the development progress of gopls, see the notes from the golang-tools meetings (https://github.com/golang/go/wiki/golang-tools).