# IDEs and Plugins for Go

  * **[Atom](https://atom.io/)**: JavaScript-based editor from GitHub. Go support at [go-plus](https://github.com/joefitzgerald/go-plus)
  * **[BBedit](https://www.barebones.com/products/bbedit/)**: commercial text editor for macOS.
    * Basic Go support available with the [module](https://www.barebones.com/products/bbedit/)
    * [Go-bbpackage](https://github.com/ascarter/go-bbpackage) with clippings, ctags standard library completion, better syntax highlighting, and tools
  * **[Brackets](http://brackets.io)**: a modern, open source text editor that understands web design.
    * [go-ide](https://github.com/David5i6/Brackets-Go-IDE) Go support with autocompletion through gocode.
  * **[Builder](https://github.com/chergert/gnome-builder)**: A toolsmith for GNOME-based applications
    * Synatax highlighting and completion build-in.
  * **[Eclipse IDE](https://www.eclipse.org/)**: a very popular, open-source, cross-platform IDE. [GoClipse](https://goclipse.github.io/) plugin enables Go support.
  * **[Emacs](https://www.gnu.org/software/emacs/)**: Extensible and customizable text editor.
    * Mode file maintained at https://github.com/dominikh/go-mode.el.
    * [GoFlyMake](https://github.com/dougm/goflymake) Flymake-style syntax checking for Go
    * [go-errcheck.el](https://github.com/dominikh/go-errcheck.el) Errcheck integration for Emacs
    * [flycheck-metalinter](https://github.com/favadi/flycheck-gometalinter) Flycheck integration for go-metalinter utility
    * [go-playground](https://github.com/grafov/go-playground) Local playground inside Emacs
  * **[Gedit](https://wiki.gnome.org/Apps/Gedit)**: Official text editor for the GNOME Desktop. [Plugin for Auto-Completion and Code-Formatting available](https://bitbucket.org/fzzbt/go-gedit-plugin/).
  * **[Geany](https://www.geany.org/)**: Geany is a text editor using the GTK2 toolkit with basic features of an integrated development environment. Supports Go syntax highlighting out of the box.
  * **[gitpod.io](https://gitpod.io)**: GitHub integrated cloud IDE with full Go support.
  * **[Gocode](https://github.com/nsf/gocode)**: An autocompletion daemon that includes support for emacs and vim.
  * **[godef](https://github.com/rogpeppe/godef)**: Prints the source location of definitions in Go programs. Integrates with acme, emacs, vim and SublimeText.
  * **[GoLand](https://www.jetbrains.com/go/)**: JetBrains's cross-platform, [fully featured](https://www.jetbrains.com/go/features/) Go IDE (commercial). Free for students, teachers, open-source developers, and user-groups ([see details](https://www.jetbrains.com/go/buy/#edition=discounts)).
  * **[Gotags](https://github.com/jstemmer/gotags)**: Generates ctags-compatible tag files
  * **[GoWorks](http://tunnelvisionlabs.com/products/demo/goworks)**: [NetBeans](http://netbeans.org/) based open source Go IDE.
  * **[IntelliJ IDEA Ultimate](https://www.jetbrains.com/idea/)**: Cross-platform, polyglot IDE (commercial). Free for students, teachers, open-source developers, and user-groups ([see details](https://www.jetbrains.com/idea/buy/#edition=discounts)).
  * **[jEdit](http://www.jedit.org/)**: open-source, cross-platform text editor written in Java. [Syntax-highlighting file available](https://code.google.com/archive/p/go-stuff/source/default/source).
  * **[joe](http://joe-editor.sourceforge.net/)**: JOE is a full featured terminal-based screen editor which is distributed under the GNU General Public License (GPL). Supports Go syntax highlighting out of the box.
  * **[Kate](https://kate-editor.org/)** Kate is an advanced, cross-platform text editor developed by KDE, with Go support out-of-the-box.
  * **[Komodo IDE](https://www.activestate.com/komodo-ide)** Powerful cross-platform IDE with built-in Go support
  * **[Komodo Edit](https://www.activestate.com/komodo-edit)** Powerful cross-platform text editor, Go-lang support available via [plugin](https://github.com/Komodo/komodo-go)
  * **[Lime Text](http://limetext.org/)**: Developed in Go, aims to be a Free and open-source software alternative to Sublime Text. Not quite ready yet but welcoming contributions to the progress. https://github.com/limetext/lime
  * **[LiteIDE](https://github.com/visualfc/liteide)**: A simple, open source and cross-platform Go IDE
  * **[Notepad++](http://notepad-plus-plus.org/)**: Free source code editor for Windows.
    * [notepadplus-go](https://github.com/chai2010/notepadplus-go) Syntax highlighting, functions list panel (for code browsing), code completion for keywords & builtins.
    * The GOnpp plugin (available **via Notepad++'s built-in Plugin Manager**) provides code completion (requires gocode), function calltips, goimports integration, and keyboard shortcuts for common go commands. [[sources](https://github.com/tike/GOnpp), [binaries](http://sourceforge.net/projects/gonpp/files/)].
    * [GoAutocomplete](https://github.com/steve-perkins/GoAutocomplete) is another code completion plugin.
  * **[Source Insight](https://www.sourceinsight.com)**: Commercial programming editor & code browser with built-in live analysis for C, C++, C#, Java, and more; helping you understand large projects.
    * [golang.xclf](https://www.sourceinsight.com/pub/languages/golang.xclf) is a [Custom Language](https://www.sourceinsight.com/download/custom-languages/) file adding syntax formatting and some parsing support to Source Insight for Go language.
  * **[Sublime Text](http://www.sublimetext.com/)**: Commercial text editor.
    * [GoSublime](https://github.com/DisposaBoy/GoSublime) is a plugin collection with IDE-like features available.
    * [Golang Build](https://github.com/golang/sublime-build) is the official Sublime Text package for Go build system integration.
  * **[Textadept](http://foicica.com/textadept/)**:  Textadept is a fast, minimalist, and remarkably extensible cross-platform text editor. Supports Go syntax highlighting out of the box.
  * **[TextMate](http://macromates.com/)**: Commercial text editor for macOS. [Source code available](https://github.com/textmate/textmate) under the GPLv3. [Bundle for Go available](https://github.com/syscrusher/golang.tmbundle).
  * **[TextWrangler](http://www.barebones.com/products/textwrangler/)**: free _little brother_ of BBedit. Both the Go module and Go.bbpackage for BBedit work for TextWrangler as well.
  * **[Vim](http://www.vim.org/)** & **[Neovim](https://neovim.io/)**: Vi Improved. There are a number of plugins available that make editing Go code easier.
    * The [vim-go](https://github.com/fatih/vim-go) plugin includes misc/vim and has many other new improvements.
    * The [Syntastic](https://github.com/scrooloose/syntastic) plugin gives instant feedback on compile errors
    * The [tagbar](https://github.com/majutsushi/tagbar) plugin uses Gotags, above, to show an outline of the current file
    * A [vim compiler plugin](https://github.com/rjohnsondev/vim-compiler-go) for syntax checking
    * A [vim-godef](https://github.com/dgryski/vim-godef) plugin integrates with the 'godef' tool, above
    * A [vim-go-extra](https://github.com/vim-jp/vim-go-extra) is vim plugin based on misc/vim in go repository. This works fine on windows too!
    * A [vim-bootstrap](https://vim-bootstrap.com/) is generator provides a simple method of generating a .vimrc configuration for vim
  * **[Visual Studio](https://www.visualstudio.com/)**: Commercial IDE by Microsoft for Windows. A [Go Language Support](https://visualstudiogallery.msdn.microsoft.com/bd7675ba-1bf5-4395-8c5a-4fc19dfc0d76) extension is available for Visual Studio 2010, 2012 and 2013 Pro, Enterprise, and Community.
  * **[Visual Studio Code](https://code.visualstudio.com/)**: Free & open source IDE by Microsoft. Visual Studio Code supports Go syntax highlighting out of the box. Additional features are provided by the [vscode-go](https://github.com/Microsoft/vscode-go) plugin.
  * **[GNU Nano](http://golang.cat-v.org/text-editors/nano/)**: a simple .nanorc for GNU Nano ("pico").
  * **[Zeus](http://www.zeusedit.com/go.html)**: Commercial IDE for Go (Windows or Linux with Wine).
  
## Cloud Based IDEs

Currently Wide is the only "cloud IDE" that supports go version 1.8.  

  * **[Cloud9](https://c9.io/)**: "blank" template includes go 1.7.1.
  * **[CodeEnv](https://codeenv.com/)**: A cloud-based IDE.  Supports go1.5 out of the box, which is not something I'd describe as "[full Go support](https://codeenv.com/env/codeenv/7/go/)".
  * **[Wide](https://github.com/b3log/wide)**: A Web-based <b>IDE</b> for Teams using Go programming language/Golang.


Other environments such as Xcode and Kate also had minor support checked in to the Go tree up until Go 1.3. If you want these, search the standard repository's history. Here is a link: https://github.com/golang/go/tree/release-branch.go1.3/misc