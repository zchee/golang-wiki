# Editors and IDEs for Go
## Popular
The [Go Developer Survey](https://go.dev/blog/survey2021-results) showed these as the most popular editors.
  * **[Visual Studio Code](https://code.visualstudio.com/)**: Free & open source IDE by Microsoft. Visual Studio Code supports Go syntax highlighting out of the box. Additional features are provided by the official [vscode-go](https://github.com/golang/vscode-go) plugin.
  * **[GoLand](https://www.jetbrains.com/go/)**: JetBrains's cross-platform, [fully featured](https://www.jetbrains.com/go/features/) Go IDE (commercial). Free for students, teachers, open-source developers, and user-groups ([see details](https://www.jetbrains.com/go/buy/#edition=discounts)). Also available as part of IntelliJ IDEA Ultimate.

  * **[Vim](http://www.vim.org/)** & **[Neovim](https://neovim.io/)**: Vi Improved. There are a number of plugins available that make editing Go code easier.
    * The [vim-go](https://github.com/fatih/vim-go) plugin includes misc/vim and has many other new improvements.
    * The [Syntastic](https://github.com/scrooloose/syntastic) plugin gives instant feedback on compile errors
    * The [tagbar](https://github.com/majutsushi/tagbar) plugin uses Gotags, above, to show an outline of the current file
    * A [vim compiler plugin](https://github.com/rjohnsondev/vim-compiler-go) for syntax checking
    * A [vim-godef](https://github.com/dgryski/vim-godef) plugin integrates with the 'godef' tool, above
    * A [vim-go-extra](https://github.com/vim-jp/vim-go-extra) is vim plugin based on misc/vim in go repository. This works fine on windows too!
    * The [go-ide](https://github.com/plentiform/go-ide) is a Neovim configuration file that ties go related plugins together making autocomplete, auto-importing, snippets, code formatting, and file search/browsing easier.
    * [govim](https://github.com/govim/govim) is an LSP-driven vim plugin for Go development, written in Go using Vim8’s channel support.
  * **[Emacs](https://www.gnu.org/software/emacs/)**: Extensible and customizable text editor. It has generic LSP support that works well with gopls, the official Go language server.
    * **[LSP Mode](https://emacs-lsp.github.io/lsp-mode/)** provides LSP support with a batteries-included approach, with many integrations enabled “out of the box” and several additional behaviors provided by lsp-mode itself.
    * **[Eglot](https://github.com/joaotavora/eglot/blob/master/README.md)** provides LSP support with a minimally-intrusive approach, focusing on smooth integration with other established packages. It provides a few of its own eglot- commands but no additional keybindings by default.
    * Mode file maintained at https://github.com/dominikh/go-mode.el.
    * [GoFlyMake](https://github.com/dougm/goflymake) Flymake-style syntax checking for Go
    * [go-errcheck.el](https://github.com/dominikh/go-errcheck.el) Errcheck integration for Emacs
    * [flycheck-metalinter](https://github.com/favadi/flycheck-gometalinter) Flycheck integration for go-metalinter utility
    * [go-playground](https://github.com/grafov/go-playground) Local playground inside Emacs

## Less popular
These editors are less popular, and may have less modern Go support. In particular, they may not support Go modules.
  * **[Atom](https://atom.io/)**: JavaScript-based editor from GitHub. Go support at [go-plus](https://github.com/joefitzgerald/go-plus)
  * **[BBEdit](https://www.barebones.com/products/bbedit/)**: free text editor for macOS (with paid upgrade for pro features). 
    * Go support available with the [Go-bbpackage module](https://github.com/ascarter/go-bbpackage) including syntax highlighting, clippings, ctags standard library completion, and tools
  * **[Brackets](http://brackets.io)**: a modern, open source text editor that understands web design.
    * [go-ide](https://github.com/David5i6/Brackets-Go-IDE) Go support with autocompletion through gocode.
  * **[Chime](https://www.chimehq.com)**: Capable. Focused. Fast. A Go editor for macOS.
  * **[CodePerfect 95](https://codeperfect95.com)**: A blazing fast IDE for Go.
  * **[jEdit](http://www.jedit.org/)**: open-source, cross-platform text editor written in Java. [Syntax-highlighting file available](https://code.google.com/archive/p/go-stuff/source/default/source).
  * **[Kate](https://kate-editor.org/)** Kate is an advanced, cross-platform text editor developed by KDE, with Go support out-of-the-box.
  * **[Komodo IDE](https://www.activestate.com/komodo-ide)** Powerful cross-platform IDE with built-in Go support
  * **[Komodo Edit](https://www.activestate.com/komodo-edit)** Powerful cross-platform text editor, Go-lang support available via [plugin](https://github.com/Komodo/komodo-go)
  * **[LiteIDE](https://github.com/visualfc/liteide)**: A simple, open source and cross-platform Go IDE
  * **[Micro](https://micro-editor.github.io)**: A modern and intuitive terminal-based text editor written in Go
    * Go language support (gofmt and goimports) via [plugin](https://micro-editor.github.io/plugins.html#c-go)
  * **[Notepad++](http://notepad-plus-plus.org/)**: Free source code editor for Windows.
    * [notepadplus-go](https://github.com/chai2010/notepadplus-go) Syntax highlighting, functions list panel (for code browsing), code completion for keywords & builtins.
    * The GOnpp plugin (available **via Notepad++'s built-in Plugin Manager**) provides code completion (requires gocode), function calltips, goimports integration, and keyboard shortcuts for common go commands. [[sources](https://github.com/tike/GOnpp), [binaries](http://sourceforge.net/projects/gonpp/files/)].
    * [GoAutocomplete](https://github.com/steve-perkins/GoAutocomplete) is another code completion plugin.
  * **[Nova](https://nova.app)**: Native Mac code editor.
    * [Go Language Definition for Nova](https://extensions.panic.com/extensions/gwynethllewelyn/gwynethllewelyn.Go/) — _Go syntax highlighting and interface with the Language Server Protocol (LSP) using Google's official [`gopls`](https://pkg.go.dev/golang.org/x/tools/gopls) language server for Go (if installed)._
    * [Go Tools](https://extensions.panic.com/extensions/cloudmanic/cloudmanic.GoTools/) — _Run `goimports` on save or via a command. Syntax highlighting for Go._
  * **[Source Insight](https://www.sourceinsight.com)**: Commercial programming editor & code browser with built-in live analysis for C, C++, C#, Java, and more; helping you understand large projects.
    * [golang.xclf](https://www.sourceinsight.com/pub/languages/golang.xclf) is a [Custom Language](https://www.sourceinsight.com/download/custom-languages/) file adding syntax formatting and some parsing support to Source Insight for Go language.
  * **[Sublime Text](http://www.sublimetext.com/)**: Commercial text editor.
    * (Sublime Text 4 only) [LSP + gopls](https://lsp.sublimetext.io/language_servers/#go) is a plugin collection with IDE-like features available.
    * [GoSublime](https://github.com/DisposaBoy/GoSublime) is a plugin collection with IDE-like features available.
    * [Golang Build](https://github.com/golang/sublime-build) is the official Sublime Text package for Go build system integration.
  * **[Textadept](http://foicica.com/textadept/)**:  Textadept is a fast, minimalist, and remarkably extensible cross-platform text editor. Supports Go syntax highlighting out of the box.
  * **[TextMate](http://macromates.com/)**: Commercial text editor for macOS. [Source code available](https://github.com/textmate/textmate) under the GPLv3. [Bundle for Go available](https://github.com/syscrusher/golang.tmbundle).

## Cloud Based IDEs

  * **[Cloud9](https://aws.amazon.com/cloud9/)**: claims full Go support.
  * **[Gitpod](https://gitpod.io)**: GitHub integrated cloud IDE with full Go support.
