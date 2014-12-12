# IDEs and Plugins for Go

  * **[Atom](http://www.atom.io)**: javascript-based editor from GitHub.  Go support at [go-plus](https://github.com/joefitzgerald/go-plus)
  * **[BBedit](http://www.barebones.com/products/bbedit/)**: commercial text editor for OS X.
    * Basic Go support available with the module http://pine.barebones.com/extensions/Go.plist.zip
    * [Go.bbpackage](https://github.com/ascarter/go.bbpackage) with clippings, ctags standard library completion, better syntax highlighting, and tools
  * **[Eclipse IDE](http://www.eclipse.org/)**: Very popular open source cross-platform IDE. [GoClipse](http://code.google.com/p/goclipse/) plugin enables Go support.
  * **[Emacs](https://www.gnu.org/software/emacs/)**: Extensible and customizable text editor.
    * Mode file maintained at https://github.com/dominikh/go-mode.el.
    * [GoFlyMake](https://github.com/dougm/goflymake) Flymake-style syntax checking for Go
    * [go-errcheck.el](https://github.com/dominikh/go-errcheck.el) Errcheck integration for Emacs
  * **[Gedit](http://projects.gnome.org/gedit/)**: Official text editor for the GNOME Desktop. [Plugin for Auto-Completion and Code-Formatting available](https://bitbucket.org/fzzbt/go-gedit-plugin/).
  * **[Gocode](https://github.com/nsf/gocode)**: An autocompletion daemon that includes support for emacs and vim.
  * **[godef](https://code.google.com/p/rog-go/source/browse/exp/cmd/godef/)**: Prints the source location of definitions in Go programs. Integrates with acme and emacs.
  * **[Gotags](https://github.com/jstemmer/gotags)**: Generates ctags-compatible tag files
  * **[GoWorks](http://tunnelvisionlabs.com/products/demo/goworks)**: [NetBeans](http://netbeans.org/) based open source Go IDE.
  * **[IntelliJ IDEA](http://www.jetbrains.com/idea/)**: Commercial cross-platform IDE, [free Community Edition available](http://www.jetbrains.com/idea/download/index.html). [Plugin for Go](http://plugins.jetbrains.com/plugin/?idea&id=5047) support available.
  * **[jEdit](http://www.jedit.org/)**: Open source cross-platform text editor. [Syntax-highlighting file available](http://code.google.com/p/go-stuff/source/browse/editors/jEdit/go.xml).
  * **[LiteIDE](http://code.google.com/p/golangide/)**: A simple, open source and cross-platform Go IDE
  * **[Notepad++](http://notepad-plus-plus.org/)**: Free source code editor for Windows.
    * [notepadplus-go](https://github.com/chai2010/notepadplus-go) Syntax highlighting, functions list panel (for code browsing), code completion for keywords & builtins.
    * The GOnpp plugin (available **via Notepad++'s built-in Plugin Manager**) provides code completion (requires gocode), function calltips, goimports integration, and keyboard shortcuts for common go commands. [[sources](https://github.com/tike/GOnpp), [binaries](http://sourceforge.net/projects/gonpp/files/)].
    * [GoAutocomplete](https://github.com/steve-perkins/GoAutocomplete) is another code completion plugin.
  * **[Sublime Text](http://www.sublimetext.com/)**: Commercial text editor. [Plugin collection with IDE-like features available](https://github.com/DisposaBoy/GoSublime).
  * **[TextMate](http://macromates.com/)**: Commercial text editor for OS X. [Source code available](https://github.com/textmate/textmate) under the GPLv3. [Bundle for Go available](https://github.com/AlanQuatermain/go-tmbundle).
  * **[TextWrangler](http://www.barebones.com/products/textwrangler/)**: free _little brother_ of BBedit. Both the Go module and Go.bbpackage for BBedit work for TextWrangler as well.
  * **[Vim](http://www.vim.org/)**: Vi Improved. There are a number of plugins available that make editing Go code easier.
    * The [vim-go](https://github.com/fatih/vim-go) plugin includes misc/vim and has many other new improvements.
    * The [Syntastic](https://github.com/scrooloose/syntastic) plugin gives instant feedback on compile errors
    * The [tagbar](https://github.com/majutsushi/tagbar) plugin uses Gotags, above, to show an outline of the current file
    * A [vim compiler plugin](https://github.com/rjohnsondev/vim-compiler-go) for syntax checking
    * A [vim-godef](https://github.com/dgryski/vim-godef) plugin integrates with the 'godef' tool, above
    * A [vim-go-extra](https://github.com/vim-jp/vim-go-extra) is vim plugin based on misc/vim in go repository. This works fine on windows too!
  * **[GNU Nano](http://golang.cat-v.org/text-editors/nano/)**: a simple .nanorc for GNU Nano ("pico").
  * **[Zeus](http://www.zeusedit.com/go.html)**: Commercial IDE for Go.

Other environments such Xcode and kate also had minor support checked in to the Go tree up until Go 1.3. If you want these, search the standard repository's history. Here is a link: https://code.google.com/p/go/source/browse/misc/?name=release-branch.go1.3