# Indexes and search engines

These sites provide indexes and search engines for Go packages:

  * [awesome-go](https://github.com/avelino/awesome-go) - A community curated list of high-quality resources.
  * [Awesome Go @LibHunt](https://go.libhunt.com) - Your go-to Go Toolbox.
  * [godoc.org](http://godoc.org/) - A documentation browser for any Go open source package.
  * [go-hardware](https://github.com/rakyll/go-hardware) - Curated list of resources for using Go on non-standard hardware.
  * [go-patterns](https://github.com/tmrts/go-patterns) - Commonly used patterns and idioms for Go.
  * [gopm.io](http://gopm.io/) - Download Go packages by version
  * [go-search](http://go-search.org/) - Search engine dedicated to Go projects and source.
  * [gowalker](http://gowalker.org/) - API documentation generator and search.
  * [Golang Data Science](http://www.mjhall.org/golang-data-science-libraries/) - Curated list of data science libraries for Go.
  * [Go Report Card](http://goreportcard.com/) - Code quality summaries for any Go project.
  * [Sourcegraph](https://sourcegraph.com/) - Source indexing, analysis and search.


## Dead projects

If you find a project in this list that is dead or broken, please either mark it as such or mention it in the #go-nuts IRC channel.

# Table of Contents
* [Astronomy](#astronomy)
* [Build Tools](#build-tools)
* [Caching](#caching)
* [Cloud Computing](#cloud-computing)
* [Command-line Option Parsers](#command-line-option-parsers)
* [Command-line Tools](#command-line-tools)
* [Compression](#compression)
* [Concurrency and Goroutines](#concurrency-and-goroutines)
* [Configuration File Parsers](#configuration-file-parsers)
* [Console User Interface](#console-user-interface)
* [Continuous Integration](#continuous-integration)
* [Cryptography](#cryptography)
* [Databases](#databases)
* [Data Processing](#data-processing)
* [Data Structures](#data-structures)
* [Date](#date)
* [Development Tools](#development-tools)
* [Distributed/Grid Computing](#distributedgrid-computing)
* [Documentation](#documentation)
* [Editors](#editors)
* [Email](#email)
* [Encodings and Character Sets](#encodings-and-character-sets)
* [Error handling](#error-handling)
* [File Systems](#file-systems)
* [Games](#games)
* [GIS](#gis)
* [Go Implementations](#go-implementations)
* [Graphics and Audio](#graphics-and-audio)
* [GUIs and Widget Toolkits](#guis-and-widget-toolkits)
* [Hardware](#hardware)
* [Language and Linguistics](#language-and-linguistics)
* [Logging & Monitoring](#logging-and-monitoring)
* [Machine Learning & AI](#machine-learning)
* [Mathematics](#mathematics)
* [Microservices](#microservices)
* [Miscellaneous](#miscellaneous)
* [Music](#music)
* [Networking](#networking)
 * [DNS](#dns)
 * [FTP](#ftp)
 * [HTTP](#http)
 * [IMAP](#imap)
 * [Instant Messaging](#instant-messaging)
 * [NNTP](#nntp)
 * [Protocol Buffers](#protocol-buffers)
 * [rsync](#rsync)
 * [Telnet](#telnet)
 * [VNC](#vnc)
 * [Websockets](#websockets)
 * [ZeroMQ](#zeromq)
 * [Misc Networking](#misc-networking)
* [Operating System Interfaces](#operating-system-interfaces)
* [Other Random Toys, Experiments and Example Code](#other-random-toys-experiments-and-example-code)
* [P2P and File Sharing](#p2p-and-file-sharing)
* [Programming](#programming)
* [Resource Embedding](#resource-embedding)
* [RPC](#rpc)
* [Scanner and Parser Generators](#scanner-and-parser-generators)
* [Security](#security)
* [Simulation Modeling](#simulation-modeling)
* [Sorting](#sorting)
* [Source Code Management](#source-code-management)
* [Storage](#storage)
* [Strings and Text](#strings-and-text)
* [Testing](#testing)
* [Unix](#unix)
* [Unsorted](#unsorted-please-help)
* [Validation](#validation)
* [Version Control](#version-control)
* [Virtual Machines and Languages](#virtual-machines-and-languages)
* [Web Applications](#web-applications)
* [Web Libraries](#web-libraries)
* [Windows](#windows)

## Astronomy

  * [go-fits](https://github.com/siravan/fits) - FITS (Flexible Image Transport System) format image and data reader
  * [astrogo/fitsio](https://github.com/astrogo/fitsio) - Pure Go FITS (Flexible Image Transport System) format image and data reader/writer
  * [cosmo](https://github.com/wmwv/cosmo) - Cosmological distance and time calculations for common cosmologies (Friedmann-Lemaître-Robertson-Walker metric).
  * [gonova](https://github.com/pebbe/gonova) - A wrapper for libnova -- Celestial Mechanics, Astrometry and Astrodynamics Library
  * [meeus](https://github.com/soniakeys/meeus) - Implementation of "Astronomical Algorithms" by Jean Meeus
  * [novas](https://github.com/pebbe/novas) - Interface to the Naval Observatory Vector Astrometry Software (NOVAS)

## Build Tools

  * [colorgo](https://github.com/songgao/colorgo) - Colorize go build output
  * [dogo](https://github.com/liudng/dogo) - Monitoring changes in the source file and automatically compile and run (restart)
  * [fileembed-go](https://bitbucket.org/rj/fileembed-go/) - This is a command-line utility to take a number of source files, and embed them into a Go package
  * [gb](http://github.com/skelterjohn/go-gb) - A(nother) build tool for go, with an emphasis on multi-package projects
  * [gg](https://github.com/lukess/gg) - A tiny multi golang projects env/make management tool.
  * [GG](http://www.manatlan.com/page/gg) - A build tool for Go in Go
  * [godag](http://code.google.com/p/godag/) - A frontend to the Go compiler collection
  * [goenv](https://bitbucket.org/ymotongpoo/goenv) - goenv provides Go version and Go workspace management tools
  * [gopei](https://github.com/geosoft1/tools) - Simple Go compiler and LiteIDE installer for Unix/Linux that adds many features like github support and presenter.
  * [go-pkg-config](https://github.com/psilva261/go-pkg-config) - lightweight clone of pkg-config
  * [goscons](https://github.com/alberts/goscons) - Another set of SCons builders for Go
  * [go-server](https://github.com/cheikhshift/Gopher-Sauce) - Agile server framework.
  * [gotgo](https://github.com/droundy/gotgo) - An experimental preprocessor to implement 'generics'
  * [gows](https://github.com/ascarter/gows) - Go workspace manager
  * [goxc](https://github.com/laher/goxc) - A build tool with a focus on cross-compiling, packaging, versioning and distribution
  * [GVM](https://github.com/moovweb/gvm) - GVM provides an interface to manage Go versions
  * [Realize](https://github.com/tockins/realize) - A Go build system with file watchers, output streams and live reload. Run, build and watch file changes with custom paths.
  * [SCons Go Tools](https://launchpad.net/sconsgo) - A collection of builders that makes it easy to compile Go projects in SCons
  * [Task](https://github.com/go-task/task) - A task runner / simple alternative to Make

## Caching

  * [cache](https://github.com/chai2010/cache) - LevelDB style LRU cache for Go, support non GC object cache.
  * [cache2go](https://github.com/muesli/cache2go) - Concurrency-safe caching library with expiration capabilities and access counters
  * [go-cache](http://patrickmylund.com/projects/go-cache/) - An in-memory key:value store/cache (similar to Memcached) library for Go, suitable for single-machine applications
  * [golibs/cache](https://github.com/SimonWaldherr/golibs/tree/master/cache) - A tiny cache package
  * [gomemcached](https://github.com/dustin/gomemcached) - A memcached server in go
  * [gomemcache](https://github.com/kklis/gomemcache) - a memcached client
  * [go-slab](https://github.com/couchbaselabs/go-slab) - Slab allocator for go.
  * [groupcache](https://github.com/golang/groupcache) - Caching and cache-filling library, intended as a replacement for memcached in many cases
  * [libmemcache](https://github.com/valyala/ybc/tree/master/libs/go/memcache) - Fast client and server libraries speaking memcache protocol
  * [memcached-bench](https://github.com/valyala/ybc/tree/master/apps/go/memcached-bench) - Benchmark tool for memcache servers
  * [memcached](https://github.com/valyala/ybc/tree/master/apps/go/memcached) - Fast memcache server, which supports persistence and cache sizes exceeding available RAM
  * [memcache](https://github.com/smallfish/memcache) - go memcached client, forked from YouTube Vitess
  * [rend](https://github.com/Netflix/rend) - A memcached proxy that manages data chunking and L1/L2 caches
  * [YBC bindings](https://github.com/valyala/ybc/tree/master/bindings/go/ybc) - Bindings for YBC library providing API for fast in-process blob cache

## Cloud Computing

  * [LXD](https://github.com/lxc/lxd) Daemon based on liblxc offering a REST API to manage containers
  * [Docker](http://docker.io) - The Linux container runtime. Developed by dotCloud.
  * [Enduro/X ASG](https://github.com/endurox-dev/endurox-go) Application Server for Go. Provides application server and middleware facilities for distributed transaction processing. Supports microservices based application architecture. Developed by ATR Baltic.
  * [Kubernetes](https://github.com/kubernetes/kubernetes) - Container Cluster Manager from Google.
  * [flamingo](https://github.com/tmrts/flamingo) - A Lightweight Cloud Instance Contextualizer.
  * [gocircuit](http://gocircuit.org) - A distributed operating system that sits on top of the traditional OS on multiple machines in a datacenter deployment. It provides a clean and uniform abstraction for treating an entire hardware cluster as a single, monolithic compute resource. Developed by Tumblr.
  * [gosync](https://github.com/brettweavnet/gosync) - A package for syncing data to and from S3.
  * [juju](https://juju.ubuntu.com) - Orchestration tool (deployment, configuration and lifecycle management), developed by Canonical.
  * [mgmt](https://github.com/purpleidea/mgmt/) - Next Generation Configuration Management tool (parallel, event driven, distributed system) developed by [@purpleidea](https://twitter.com/#!/purpleidea), (a Red Hat employee) and the mgmt community.
  * [rclone](http://rclone.org/) - "rsync for cloud storage" - Google Drive, Amazon Drive, S3, Dropbox, Backblaze B2, One Drive, Swift, Hubic, Cloudfiles, Google Cloud Storage, Yandex Files
  * [ShipBuilder](http://shipbuilder.io) - ShipBuilder is a minimalist open source platform as a service, developed by Jay Taylor.
  * [swift](https://github.com/ncw/swift) - Go language interface to Swift / Openstack Object Storage / Rackspace cloud files
  * [Tsuru](http://www.tsuru.io/) - Tsuru is an open source polyglot cloud computing platform as a service (PaaS), developed by Globo.com.
* [aws-sdk-go](https://github.com/aws/aws-sdk-go) - AWS SDK for the Go programming language.

## Command-line Option Parsers

  * [argcfg](http://code.google.com/p/goargcfg/) - Use reflection to populate fields in a struct from command line arguments
  * [autoflags](https://github.com/artyom/autoflags) - Populate go command line app flags from config struct
  * [cobra](http://github.com/spf13/cobra) - A commander for modern go CLI interactions supporting commands & POSIX/GNU flags
  * [command](https://github.com/rakyll/command) - Add subcommands to your CLI, provides help and usage guide.
  * [docopt.go](https://github.com/docopt/docopt.go) - An implementation of docopt in the Go programming language.
  * [getopt](http://code.google.com/p/getopt) - full featured traditional (BSD/POSIX getopt) option parsing in Go style
  * [getopt](https://github.com/timtadh/getopt) - Yet Another getopt Library for Go. This one is like Python's.
  * [gnuflag](https://launchpad.net/gnuflag) - GNU-compatible flag parsing; substantially compatible with flag.
  * [go-commander](https://code.google.com/p/go-commander) - Simplify the creation of command line interfaces for Go, with commands and sub-commands, with argument checks and contextual usage help. Forked from the "go" tool code.
  * [go-flags](https://github.com/jessevdk/go-flags) - command line option parser for go
  * [goopt](https://github.com/droundy/goopt) - a getopt clone to parse command-line flags
  * [go-options](https://github.com/gaal/go-options) - A command line parsing library for Go
  * [options](https://github.com/fd/options/) - Self documenting CLI options parser
  * [opts.go](http://opts-go.googlecode.com/) - lightweight POSIX- and GNU- style option parsing
  * [pflag](https://github.com/ogier/pflag) - Drop-in replacement for Go's flag package, implementing POSIX/GNU-style --flags.
  * [subcommands](https://github.com/maruel/subcommands) - A concurrent, unit tested, subcommand library
  * [uggo](https://github.com/laher/uggo) - Yet another option parser offering gnu-like option parsing. This one wraps (embeds) flagset. It also offers rudimentary pipe-detection (commands like ls behave differently when being piped to).
  * [writ](https://github.com/ziuchkovski/writ) - A flexible option parser with thorough test coverage.  It's meant to "just work" and stay out of the way.
  * [cli](https://github.com/mitchellh/cli) - A Go library for implementing command-line interfaces.
  * [cmdline](https://github.com/galdor/go-cmdline) - A simple parser with support for short and long options, default values, arguments and subcommands.
  * [go-getoptions](https://github.com/DavidGamba/go-getoptions) - Go option parser inspired on the flexibility of Perl’s GetOpt::Long.

## Command-line Tools

  * [awless](https://github.com/wallix/awless) - A Mighty command-line interface for Amazon Web Services (AWS).
  * [boilr](https://github.com/tmrts/boilr) - A blazing fast CLI tool for creating projects from boilerplate templates.
  * [coshell](https://github.com/gdm85/coshell) - A drop-in replacement for GNU 'parallel'.
  * [DevTodo2](https://github.com/alecthomas/devtodo2) - A small command-line per-project task list manager.
  * [dsio](https://github.com/nshmura/dsio) - Command line tool for Google Cloud Datastore.
  * [enumeration](https://bitbucket.org/rickb777/enumeration) - Easy enumeration code generation.
  * [fzf](https://github.com/junegunn/fzf) - A command-line fuzzy finder
  * [gich](http://bitbucket.org/jpoirier/gich) - A cross platform which utility written in Go
  * [git-time-metric](https://github.com/git-time-metric/gtm) - Simple, seamless, lightweight time tracking for Git
  * [gister](https://github.com/dutchcoders/gister) - Manage your github gists from the command-line
  * [gmail2go](https://github.com/rif/gmail2go) - Simple gmail multiple accounts cli mail checker
  * [gocreate](https://bitbucket.org/llg/gocreate/) - Command line utility that create files from templates.
  * [godocdoc](https://github.com/kevinburke/godocdoc) - Start godoc and open it in your browser to the project in the current directory.
  * [gojson](https://github.com/ChimeraCoder/gojson) - Command-line tool for manipulating JSON for use in developing Go code.
  * [gopass](https://github.com/justwatchcom/gopass) - Command line password manager with git syncing capabilities
  * [GoPasswordCreator](https://github.com/d3xter/GoPasswordCreator) - A small tool, which creates random passwords
  * [GoNote](https://github.com/exaroth/gonote) - Command line SimpleNote client.
  * [Grozilla](https://github.com/prashant-agarwala/grozilla) - File downloader utility with resume capability.
  * [jsonpp](http://jmhodges.github.com/jsonpp/) - A fast command line JSON pretty printer.
  * [lsp](https://github.com/dborzov/lsp) - A human-friendlier alternative to `ls`
  * [ltst](https://github.com/marcelpuyat/ltst) - View the latest news of your choosing right in your terminal
  * [passhash](https://github.com/gebi/passhash) - Command-line utility to create secure password hashes
  * [passman](https://github.com/seanpont/passman) - A command-line password manager
  * [pdfcpu](https://github.com/hhrutter/pdfcpu) - PDF processor.
  * [pjs](http://jcasts.github.io/pjs) - Pretty print and search through JSON data structures fast.
  * [project](https://github.com/nildev/project) - Very simple CLI tool to setup new projects from boilerplate templates.
  * [pwdgen](https://github.com/chai2010/pwdgen/) - A small tool, which generate human password, written in Go.
  * [redis-view](https://github.com/dreamersdw/redis-view) - A tree like tool help you explore data structures in your redis server
  * [remote-torrent](https://github.com/brucewangno1/remote-torrent) - A simple tool for downloading Torrent remotely and retrieving files back over HTTP at full speed without ISP Torrent limitation
  * [restic](https://github.com/restic/restic) - A fast, efficient and secure backup program
  * [runtemplate](https://github.com/flowonyx/runtemplate) - A very simple command-line tool for executing Go templates, useful for use with `go generate`.
  * [runtemplate](https://github.com/rickb777/runtemplate) - A simple tool for executing Go templates to support generating Go code for your types.
  * [sift](https://github.com/svent/sift) - A fast and powerful open source alternative to `grep`
  * [tecla](https://github.com/michaelmacinnis/tecla) - Command-line editing library
  * [wlog](https://github.com/dixonwille/wlog) - A simple logging interface that supports cross-platform color and concurrency.
  * [wmenu](https://github.com/dixonwille/wmenu) - An easy to use menu structure for cli applications that prompts users to make choices.
  * [comb-go](https://github.com/bingohuang/comb-go) - A CLI tool implemented by Golang to manage [CloudComb](http://c.163.com) resources.
  * [JayDiff](https://github.com/yazgazan/jaydiff) - A JSON diff utility written in Go.

## Compression
 
  * [brotli](https://github.com/google/brotli/tree/master/go/cbrotli) - go bindings for Brotli algorithm.
  * [compress](https://github.com/klauspost/compress) - Faster drop in replacements for gzip, zip, zlib, deflate
  * [dgolzo](https://github.com/dgryski/dgolzo) - LZO bindings
  * [dictzip](https://github.com/pebbe/dictzip) - A reader and writer for files in the random access ` dictzip ` format
  * [fast-archiver](https://github.com/replicon/fast-archiver) - Alternative archiving tool with fast performance for huge numbers of small files
  * [gbacomp](https://github.com/salviati/gbacomp) - A Go library to (de)compress data compatible with GBA BIOS
  * [go-lz4](https://github.com/bkaradzic/go-lz4) - Port of LZ4 lossless compression algorithm to Go.
  * [go-lzss](https://github.com/salviati/go-lzss) - Implementation of LZSS compression algorithm in Go
  * [go-sevenzip](https://github.com/salviati/go-sevenzip) - Package sevenzip implements access to 7-zip archives (wraps C interface of LZMA SDK)
  * [go-zip](https://github.com/hailiang/go-zip) - A wrapper around C library libzip, providing ability to modify existing ZIP archives.
  * [lzma](http://code.google.com/p/lzma/) - compress/lzma package for Go
  * [pgzip](https://github.com/klauspost/pgzip) - Multicore gzip, compatible with the standard library
  * [snappy-go](http://code.google.com/p/snappy-go/) - Google's Snappy compression algorithm in Go
  * [yenc](https://github.com/chrisfarms/yenc) - yenc decoder package
  * [zappy](https://github.com/cznic/zappy) - Package zappy implements the zappy block-based compression format. It aims for a combination of good speed and reasonable compression.
  * [ppmd-go](https://github.com/zwb-ict/ppmd-go) - Golang bindings for the LZMA SDK library. (Only binded PPMD) 

## Concurrency and Goroutines

  * [grpool](https://github.com/ivpusic/grpool) - Lightweight Goroutine pool.
  * [pool](https://github.com/go-playground/pool) - Go consumer goroutine pool for easy goroutine handling + time saving.
  * [tunny](https://github.com/Jeffail/tunny) - A goroutine pool.
  * [worker](https://github.com/duzy/worker) - An easy and lightweight concurrent job framework.

## Configuration File Parsers

  * [awsenv](https://github.com/soniah/awsenv) - a small binary that loads Amazon (AWS) environment variables for a profile
  * [confl](https://github.com/lytics/confl) - nginx config syntax, lenient, encode/decode, custom marshaling
  * [configor](https://github.com/jinzhu/configor) - Golang Configuration tool that support YAML, JSON, TOML, Shell Environment
  * [flagfile](https://github.com/spacemonkeygo/flagfile) - Adds parsing and serialization support to the standard library flag package (adds a --flagfile option)
  * [gcfg](http://code.google.com/p/gcfg/) - read INI-style configuration files into Go structs; supports user-defined types and subsections
  * [globalconf](https://github.com/rakyll/globalconf) - Effortlessly persist to and read flag values from an ini config file
  * [goconf](http://code.google.com/p/goconf/) - a configuration file parser
  * [goconfig](https://github.com/fulldump/goconfig) - Configuration based on struct introspection, supports environment vars, command line args, and more.
  * [hjson](https://github.com/laktak/hjson-go) - Human JSON, a configuration file format for humans. Relaxed syntax, fewer mistakes, more comments.
  * [jsonconfig](https://github.com/knadh/jsonconfig) - a JSON configuration file parser with comments support
  * [properties](https://github.com/magiconair/properties) - Library for reading and writing properties files
  * [scribeconf](https://godoc.org/github.com/fumin/scribeconf) - Facebook Scribe server configuration file parser
  * [toml](http://github.com/mojombo/toml):
    * [go-toml-config](http://github.com/stvp/go-toml-config) - TOML-based config for Go
    * [go-toml](http://github.com/pelletier/go-toml) - Go library for the TOML language
    * [gp-config](https://github.com/cbonello/gp-config) - Subset of TOML syntax with basic and reflection APIs
    * [toml-go](http://github.com/laurent22/toml-go) - An easy-to-use Go parser for the Toml format
    * [toml](http://github.com/BurntSushi/toml) - TOML parser for Go with reflection
    * [tom-toml](https://github.com/achun/tom-toml) - TOML parser for Go, support comments/formatter/apply.
  * [uConfig](https://github.com/omeid/uconfig) - an unopinionated, extendable and plugable configuration management. Supports YAML, TOML, JSON, Env vars, K8s DAPI, et al.
  * [viper](http://github.com/spf13/viper) - a complete configuration solution supporting YAML, TOML & JSON and integration with command line flags
  * yaml:
    * [yaml](http://github.com/go-yaml/yaml) - YAML support for the Go language, by Canonical
    * [goyaml](http://goyaml.googlecode.com/) - A port of LibYAML to Go

## Console User Interface

  * [ansi](https://github.com/mgutz/ansi) - Easily create ansi escape code strings and closures to format, color console output
  * [ansiterm](https://github.com/hotei/ansiterm) - pkg to drive text-only consoles that respond to ANSI escape sequences
  * [cons](https://github.com/rferrante/cons) - A simple package for building interactive console tools.
  * [gnureadline](https://code.google.com/p/go-gnureadline) - GNU Readline bindings
  * [go-ansiout](https://github.com/tlorens/go-ansiout) - Another ANSI escape code sequence tool for use with command-line applications.
  * [gockel](https://github.com/akrennmair/gockel) - a Twitter client for text terminals
  * [gocui](https://github.com/jroimartin/gocui) - Minimalist library aimed at creating Console User Interfaces
  * [gocurse](https://github.com/jabb/gocurse) - Go bindings for NCurses
  * [gocurses](https://github.com/tncardoso/gocurses) - NCurses wrapper
  * [go-ibgetkey](https://github.com/tlorens/go-ibgetkey) - "hot key" type user input package for use in processing keystrokes in command-line applications.
  * [go.linenoise](https://github.com/GeertJohan/go.linenoise) - Linenoise bindings (simple and easy readline with prompt, optional history, optional tab completion)
  * [goncurses](https://github.com/rthornton128/goncurses) - An ncurses library, including the form, menu and panel extensions
  * [gopass](https://code.google.com/p/gopass/) - Allows typing of passwords without echoing to screen
  * [go-pullbarz](https://github.com/tlorens/go-pullbarz) - Fancy "light bar" menus like in Lotus 123 from the DOS days.  Dependent on go-ibgetkey and go-ansiout.
  * [go.sgr](https://github.com/foize/go.sgr) - Terminal/console colors and text decoration (bold,underlined,etc).
  * [go-stfl](https://github.com/akrennmair/go-stfl) - a thin wrapper around STFL, an ncurses-based widget toolkit
  * [goterminal](https://github.com/apoorvam/goterminal) - A go library that lets you write and then re-write the text on terminal, to update progress. It works on Windows too!
  * [go-web-shell](https://github.com/matiasinsaurralde/go-web-shell) - Remote web shell, implements a net/http server.
  * [igo](https://bitbucket.org/binet/igo) - A simple interactive Go interpreter built on exp/eval with some readline refinements
  * [oh](https://github.com/michaelmacinnis/oh) - A Unix shell written in Go
  * [pty](https://github.com/kr/pty) - obtain pseudo-terminal devices
  * [readline](https://github.com/chzyer/readline) - A pure go implementation for GNU-Readline kind library
  * [termbox-go](https://github.com/nsf/termbox-go) - A minimalist alternative to ncurses to build terminal-based user interfaces
  * [termios](http://bitbucket.org/taruti/termios) - Terminal support
  * [termon](http://termon.googlecode.com/) - Easy terminal-control-interface for Go.
  * [uilive](https://github.com/gosuri/uilive) - uilive is a go library for updating terminal output in realtime.
  * [uiprogress](https://github.com/gosuri/uiprogress) - A library to render progress bars in terminal applications.
  * [uitable](https://github.com/gosuri/uitable) - A library to improve readability in terminal apps using tabular data.
  * [yandex-weather-cli](https://github.com/msoap/yandex-weather-cli) - Command line interface for Yandex weather service

## Continuous Integration

  * [goveralls](https://github.com/mattn/goveralls) - Go integration for Coveralls.io continuous code coverage tracking system.
  * [overalls](https://github.com/go-playground/overalls) - Multi-Package go project coverprofile for tools like goveralls

## Cryptography

  * [BLAKE2b](https://github.com/dchest/blake2b) - Go implementation of BLAKE2b hash function
  * [cryptogo](https://github.com/vgorin/cryptogo) - some useful cryptography-related functions, including paddings (PKCS7, X.923), PBE with random salt and IV
  * [cryptoPadding](https://github.com/apexskier/cryptoPadding) - Block padding schemes implemented in Go
  * [dkeyczar](https://github.com/dgryski/dkeyczar) - Go port of Google'e Keyczar cryptography library
  * [dkrcrypt](https://github.com/dgryski/dkrcrypt) - Korean block ciphers: SEED and HIGHT
  * [dskipjack](https://github.com/dgryski/dskipjack) - Go implementation of the SKIPJACK encryption algorithm
  * [go-cs](https://github.com/akosela/go-cs) - concurrent ssh client.
  * [go-ed25519](https://github.com/tendermint/go-ed25519) - CGO bindings for Floodberry's ed25519-donna.  Fast batch verification.
  * [go-hc128](https://github.com/tomfitzhenry/go-hc128) - Go implementation of HC-128, an eSTREAM stream cipher
  * [go-jose](https://github.com/square/go-jose) - Go implementation of the JOSE standards
  * [go-minilock](https://github.com/cathalgarvey/go-minilock) - Go implementation of the minilock file encryption system.
  * [GoSkein](https://github.com/wernerd/Skein3Fish/tree/master/go) - Implementation of Skein hash and Threefisch crypto for Go
  * [keccak](https://github.com/ebfe/keccak) - A keccak (SHA-3) implementation
  * [ketama.go](https://github.com/mncaudill/ketama.go) - libketama-style consistent hashing
  * [kindi](https://github.com/uwedeportivo/Kindi) - encryption command line tool
  * [openssl](https://github.com/spacemonkeygo/openssl) - openssl bindings for go
  * [otrcat](https://github.com/andrewclausen/otrcat) - a general purpose command-line tool for communicating using the Off-The-Record protocol
  * [scrypt](https://go.googlesource.com/crypto/+/master/scrypt/) - Go implementation of Colin Percival's scrypt key derivation function
  * [simpleaes](https://github.com/tadzik/simpleaes) - AES encryption made easy
  * [siphash](https://github.com/dchest/siphash) - SipHash: a fast short-input pseudorandom function
  * [SRP](https://code.google.com/p/go-srp/) - SRP: Secure Remote Password - Implementation in go
  * [ssh.go](http://bitbucket.org/taruti/ssh.go) - SSH2 Client library
  * [ssh-vault](https://github.com/ssh-vault/ssh-vault) - encrypt/decrypt using ssh keys
  * [themis](https://github.com/cossacklabs/themis) - Multi-platform high-level cryptographic library for protecting sensitive data: secure messaging with forward secrecy, secure data storage (AES256GCM); suits for building end-to-end encrypted applications
  * [tiger](https://github.com/cxmcc/tiger) - Tiger cryptographic hashing algorithm
  * [whirlpool](https://github.com/jzelinskie/whirlpool) - whirlpool cryptographic hashing algorithm
  * [go-lioness](https://github.com/applied-mixnetworks/go-lioness) - Lioness wide-block cipher using Chacha20 and Blake2b
  * [go-sphinxmixcrypto](https://github.com/applied-mixnetworks/go-sphinxmixcrypto) - Sphinx mix network cryptographic packet format operations

## Data Processing

  * [automi](https://github.com/vladimirvivien/automi) - Compose process and integration flows on Go channels
  * [gostatsd](https://github.com/kisielk/gostatsd) - Statsd server and library.
  * [Heka](https://github.com/mozilla-services/heka) - Real time data and log file processing engine.
  * [Kapacitor](https://github.com/influxdb/kapacitor) - Framework for processing, monitoring and alerting on timeseries data.
  * [pipe](https://github.com/lennon-guan/pipe) - Several functional programming supporting in golang (Map/Reduce/Filter)
  * [proto](https://github.com/eblume/proto) - Map/Reduce/Filter etc. for Go using channels as result streams.
  * [regommend](https://github.com/muesli/regommend) - Recommendation engine.
  * [rrd](https://github.com/ziutek/rrd) - Bindings for rrdtool.
  * [XConv](https://github.com/howcrazy/xconv) - Convert any value between types (base type, struct, array, slice, map, etc.)
  * [ratchet](https://github.com/dailyburn/ratchet) - A library for performing data pipeline / ETL tasks in Go.
  * [Glow](https://github.com/chrislusf/glow) - Glow is an easy-to-use distributed computation system, similar to Hadoop Map Reduce, Spark, Flink, Storm.
  * [Gleam](https://github.com/chrislusf/gleam) - Fast, efficient, and scalable distributed map/reduce system, DAG execution, in memory or on disk, runs standalone or distributedly.

## Data Structures

### Collections

  * [collections](https://github.com/cosn/collections) - Several common data structures
  * [data-structures](https://github.com/timtadh/data-structures) - A collection of data-structures (ArrayList, SortedList, Set, AVL Tree, Immutable AVL Tree, B+Tree, Ternary Search Trie, Hash Table (Separate Chaining), Linear Hash Table)
  * [ps](https://github.com/mndrix/ps) - Persistent data structures
  * [Tideland golib](https://github.com/tideland/golib) - A collections library

### Hashtables

  * [gohash](http://code.google.com/p/gohash/) - A simple linked-list hashtable that implements sets and maps
  * [go-maps](https://github.com/serge-hulne/go-maps) - Go maps generalized to interfaces

### Lists

  * [fs2/mmlist](https://github.com/timtadh/fs2#mmlist) - A memory mapped list.
  * [GoArrayList](https://github.com/PhilStephens/GoArrayList) - GoArrayList is a Go language substitute for the Java class ArrayList, with very nearly all features.
  * [goskiplist](https://github.com/ryszard/goskiplist) - A skip list implementation in Go.
  * [itreap](https://github.com/glenn-brown/itreap) - An immutable ordered list, internally a treap.
  * [ListDict](https://bitbucket.org/matrixik/listdict/) - Python List and Dict for Go
  * [skip](https://github.com/glenn-brown/skiplist) - A fast position-addressable ordered map and multimap.
  * [Skiplist](https://github.com/glenn-brown/skiplist) - A fast indexable ordered multimap.
  * [skiplist](https://github.com/huandu/skiplist) - A skip list implementation. Highly customizable and easy to use.
  * [skiplist](https://godoc.org/github.com/fumin/skiplist) - Skiplist data structure ported from Redis's Sorted Sets.
  * [stackgo](https://github.com/alediaferia/stackgo) - A fast slice-based stack implementation.

### Queues

  * [fifo\_queue](https://github.com/yasushi-saito/fifo_queue) - Simple FIFO queue
  * [figo](https://github.com/jasocox/figo) - A simple fifo queue with an optional thread-safe version.
  * [go.fifo](https://github.com/foize/go.fifo) - Simple auto-resizing thread-safe fifo queue.
  * [gopqueue](https://github.com/nu7hatch/gopqueue) - Priority queue at top of container/heap
  * [go-priority-queue](https://code.google.com/p/go-priority-queue/) - An easy to use heap implementation with a conventional priority queue interface.
  * [golibs/stack](https://github.com/SimonWaldherr/golibs/tree/master/stack) - A LIFO and ringbuffer package
  * [gringo](https://github.com/textnode/gringo) - A minimalist queue implemented using a stripped-down lock-free ringbuffer
  * [heap](https://github.com/golangplus/container/tree/master/heap) - A general heap package without converting elements to `interface{}` and back.
  * [queued](https://github.com/timtadh/queued) - A simple network queue daemon
  * [queue](https://github.com/kavehmz/queue) - A queue manager on top of Redis

### Graphs

  * [graph](https://github.com/yourbasic/graph) - Library of basic graph algorithms
  * [graphs](https://github.com/thcyron/graphs) - Implementation of various tree, graph and network algorithms

### Sets

  * [disjoint](https://github.com/spakin/disjoint) - Disjoint sets (union-find algorithm with path compression)
  * [golang-set](https://github.com/deckarep/golang-set) - A full thread-safe and unsafe set implementation for Go.
  * [goset](https://github.com/fatih/goset) - A simple, thread safe Set implementation
  * [set](https://github.com/fatih/set) - Set data structure for Go

### Trees

  * [b](https://github.com/cznic/b) - Package b implements B+trees with delayed page split/concat and O(1) enumeration. Easy production of source code for B+trees specialized for user defined key and value types is supported by a simple text replace.
  * [btree](https://bitbucket.org/santucco/btree) - Package btree implements persistent B-trees with fixed size keys, http://en.wikipedia.org/wiki/Btree
  * [btree](https://github.com/google/btree) - In-memory (not persistent) B-tree implementation, similar API to GoLLRB
  * [go-avltree](https://github.com/ancientlore/go-avltree) - AVL tree (Adel'son-Vel'skii & Landis) with indexing added
  * [go-btree](https://github.com/liangx8/tree.git) - Simple balance tree implementation
  * [go-darts](https://github.com/awsong/go-darts) - Double-ARray Trie System for Go
  * [GoLLRB](https://github.com/petar/GoLLRB) - A Left-Leaning Red-Black (LLRB) implementation of 2-3 balanced binary search trees in Google Go
  * [go-merkle](https://github.com/tendermint/go-merkle) - Merkle-ized binary (search) trees with proofs.
  * [go-stree](https://github.com/toberndo/go-stree) - A segment tree implementation for range queries on intervals
  * [go-radix](https://github.com/armon/go-radix), [go-radix-immutable](https://github.com/hashicorp/go-immutable-radix) - Radix tree implementations.
  * [gtreap](https://github.com/steveyen/gtreap) - Persistent treap implementation.
  * [rbtree](https://github.com/yasushi-saito/rbtree) - Yet another red-black tree implementation, with a C++ STL-like API
  * [rbtree](https://github.com/cdongyang/library/tree/master/rbtree) - A high performance red-black tree with an API similar to C++ STL's for set, map, multiset, multimap.
  * [rtreego](https://github.com/dhconnelly/rtreego) - an R-Tree library
  * [triego](https://github.com/alediaferia/triego) - Simple trie implementation for storing words
  * [prefixmap](https://github.com/alediaferia/prefixmap) - Simple trie-based prefix-map for string-based keys

### Other

  * [aurora](https://github.com/xuri/aurora) - Cross-platform Beanstalk queue server console.
  * [bigendian](https://bitbucket.org/taruti/bigendian) - binary parsing and printing
  * [deepcopy](http://bitbucket.org/taruti/deepcopy) - Make deep copies of data structures
  * [dgobloom](https://github.com/dgryski/dgobloom) - A Bloom Filter implementation
  * [epochdate](https://github.com/extemporalgenome/epochdate) - Compact dates stored as days since the Unix epoch
  * [etree](https://github.com/beevik/etree) - Parse and generate XML easily
  * [excelize](https://github.com/360EntSecGroup-Skylar/excelize) - Golang library for reading and writing Microsoft Excel™ (XLSX) files.
  * [fsm](https://github.com/looplab/fsm) - Minimalistic state machine for use instead of booleans
  * [go-algs/ed](https://github.com/daviddengcn/go-algs) - Generalized edit-distance implementation
  * [go-algs/maxflow](https://github.com/daviddengcn/go-algs) - An energy minimization tool using max-flow algorithm.
  * [go-extractor](https://github.com/salviati/go-extractor) - Go wrapper for GNU libextractor
  * [gocrud](https://github.com/manishrjain/gocrud) - Framework for working with arbitrary depth data structures.
  * [Gokogiri](https://github.com/moovweb/gokogiri) - A lightweight libxml wrapper library
  * [GoNetCDF](https://bitbucket.org/ctessum/gonetcdf) - A wrapper for the NetCDF file format library
  * [goop](https://github.com/lanl/goop) - Dynamic object-oriented programming support for Go
  * [gopart](https://github.com/meirf/gopart)- Type-agnostic partitioning for anything that can be indexed in Go.
  * [gotoc](https://github.com/dsymonds/gotoc) - A protocol buffer compiler written in Go
  * [govalid](https://github.com/gima/govalid) - Data validation library
  * [goxml](https://github.com/jbussdieker/golibxml) - A thin wrapper around libxml2
  * [hyperloglog](https://github.com/clarkduvall/hyperloglog) - An implementation of the HyperLogLog and HyperLogLog++ algorithms for estimating cardinality of sets using constant memory.
  * [itertools](https://github.com/xchapter7x/goutil) - Provides generic iterable generator function along with functionality similar to the itertools python package.
  * [jsonv](https://github.com/gima/jsonv) - A JSON validator
  * [libgob](http://code.google.com/p/libgob/) - A low level library for generating gobs from other languages
  * [ofxgo](https://github.com/aclindsa/ofxgo) - A library for querying OFX servers and/or parsing the responses (and example command-line client).
  * [Picugen](http://patrickmylund.com/projects/picugen/) - A general-purpose hash/checksum digest generator.
  * [tribool](https://github.com/saschpe/tribool) - Ternary (tree-valued) logic for Go
  * [Tuple](https://bitbucket.org/gotamer/tuple) - Tuple is a go type that will hold mixed types / values
  * [vcard](https://bitbucket.org/llg/vcard) - Reading and writing vcard file in go.  Implementation of RFC 2425 (A MIME Content-Type for Directory Information) and RFC 2426 (vCard MIME Directory Profile).
  * [mxj](https://github.com/clbanning/mxj) - Marshal/Unmarshal XML doc from/to `map[string]interface{}` or JSON
  * [xlsx](https://github.com/tealeg/xlsx) - A library to help with extracting data from Microsoft Office Excel XLSX files.
  * [goxlsxwriter](https://github.com/fterrag/goxlsxwriter) - Golang bindings for libxlsxwriter for writing XLSX (Excel) files
  * [simple-sstable](https://github.com/akmistry/simple-sstable) - A simple, no-frills SSTable format and implementation in Go.

## Databases

See also [[SQLDrivers page|SQLDrivers]].

### CockroachDB
  * [cockroachdb](https://github.com/cockroachdb/cockroach) - A Scalable, Survivable, Strongly-Consistent SQL Database

### Hazelcast IMDG
  * [Hazelcast IMDG Go Client](https://github.com/hazelcast/hazelcast-go-client) - The official Go client implementation for [Hazelcast IMDG](http://hazelcast.org), the open source in-memory data grid.

### MongoDB

  * [mgo](http://labix.org/mgo) - Rich MongoDB driver for Go
  * [rocks-stata](https://github.com/facebookgo/rocks-strata) - MongoDB Backup Utility

### MySQL

  * [Go-MySQL-Driver](https://github.com/go-sql-driver/mysql) - A lightweight and fast MySQL-Driver for Go's database/sql package
  * [MyMySQL](https://github.com/ziutek/mymysql) - MySQL Client API written entirely in Go.
  * [TiDB](https://github.com/pingcap/tidb) - MySQL compatible distributed database modeled after Google's F1 design.
  * [vitess](https://github.com/youtube/vitess) - Scaling MySQL databases for the web
  * [mysqlsuperdump](https://github.com/hgfischer/mysqlsuperdump) - Generate partial and filtered dumps of MySQL databases

### ODBC

  * [go-odbc](https://github.com/weigj/go-odbc) - ODBC Driver for Go
  * [odbc3-go](https://bitbucket.org/rj/odbc3-go/) - This package is wrapper around ODBC (version 3).

### PostgreSQL

  * [go-libpq](https://github.com/jgallagher/go-libpq) - cgo-based Postgres driver for Go's database/sql package
  * [go-pgsql](https://github.com/lxn/go-pgsql) - A PostgreSQL client library for Go
  * [pgsql.go](https://github.com/jbarham/pgsql.go) - PostgreSQL high-level client library wrapper
  * [pgx](https://github.com/JackC/pgx) - Go PostgreSQL driver that is compatible with database/sql and has native interface for more performance and features
  * [pq](https://github.com/lib/pq) - Pure Go PostgreSQL driver for database/sql
  * [yoke](https://github.com/nanopack/yoke) - Postgres high-availability cluster with auto-failover and automated cluster recovery
  * [kallax](https://github.com/src-d/go-kallax) - PostgreSQL typesafe ORM

### QL

  * [ql](https://github.com/cznic/ql) - A pure Go embedded (S)QL database.

### Redis

  * [godis](https://github.com/simonz05/godis) - Simple client for Redis
  * [Go-Redis](https://github.com/alphazero/Go-Redis) - Client and Connectors for Redis key-value store
  * [go-redis](https://github.com/fiorix/go-redis) - Redis client built on the skeleton of gomemcache
  * [Redigo](https://github.com/garyburd/redigo) - Go client for Redis.
  * [redis](https://github.com/vmihailenco/redis) - Redis client for Go

### [RethinkDB](http://www.rethinkdb.com/)

  * [GoRethink](https://github.com/dancannon/gorethink) - RethinkDB Driver for Go

### SQLite

  * [gosqlite3](https://github.com/kuroneko/gosqlite3) - Go Interface for SQLite3
  * [gosqlite (forked)](https://github.com/gwenn/gosqlite) - A fork of gosqlite
  * [gosqlite](http://code.google.com/p/gosqlite/) - a trivial SQLite binding for Go.
  * [go-sqlite](https://github.com/mxk/go-sqlite) - A database/sql driver and standalone sqlite3 interface
  * [go-sqlite-lite](https://github.com/bvinc/go-sqlite-lite) - A simple SQLite package for Go.
  * [mattn's go-sqlite3](https://github.com/mattn/go-sqlite3) - sqlite3 driver conforming to the built-in database/sql interface

### ORM

  * [beedb](https://github.com/astaxie/beedb) - beedb is an ORM for Go. It lets you map Go structs to tables in a database
  * [FilterXorm](https://github.com/howcrazy/filterxorm) - Build conditions for xorm project.
  * [go-modeldb](https://github.com/jaekwon/go-modeldb) - A simple wrapper around sql.DB for struct support.
  * [gorm](https://github.com/jinzhu/gorm) - An ORM library for Go, aims for developer friendly
  * [gorp](https://github.com/coopernurse/gorp) - SQL mapper for Go
  * [go-store](https://github.com/gosuri/go-store) - Data-store library for Go that provides a set of platform-independent interfaces to persist and retrieve key-value data.
  * [hood](https://github.com/eaigner/hood) - Database agnostic ORM for Go. Supports Postgres and MySQL.
  * [lore](https://github.com/abrahambotros/lore) - Simple and lightweight pseudo-ORM/pseudo-struct-mapping environment for Go.
  * [qbs](https://github.com/coocood/qbs) - Query By Struct. Supports MySQL, PostgreSQL and SQLite3.
  * [sqlboiler](https://github.com/volatiletech/sqlboiler) - Database-first ORM via code generation.
  * [sqlgen](https://github.com/drone/sqlgen) - Go code generation for SQL interaction.
  * [structable](https://github.com/Masterminds/structable) - Struct-to-table database mapper.
  * [xorm](https://github.com/go-xorm/xorm) - Simple and Powerful ORM for Go.
  * [reform](https://github.com/AlekSi/reform) - A better ORM for Go, based on non-empty interfaces and code generation.
  * [go-queryset](https://github.com/jirfag/go-queryset) - 100% type-safe ORM for Go with code generation and MySQL, PostgreSQL, Sqlite3, SQL Server support.

### Key-Value-Stores

  * [bolt](https://github.com/boltdb/bolt) - Persistent key/value store inspired by LMDB.
  * [dbm](https://github.com/cznic/exp/tree/master/dbm) - Package dbm (WIP) implements a simple database engine, a hybrid of a hierarchical and/or a key-value one.
  * [fs2/bptree](https://github.com/timtadh/fs2#b+tree) - A memory mapped B+Tree with duplicate key support. Appropriate for large amounts of data (aka +100 GB). Supports both anonymous and file backed memory maps.
  * [Diskv](https://github.com/peterbourgon/diskv) - Home-grown, disk-backed key-value store
  * [etcd](https://github.com/coreos/etcd) - Highly-available key value store for shared configuration and service discovery
  * [gkvlite](https://github.com/steveyen/gkvlite) - Pure go, simple, ordered, atomic key-value persistence based on append-only file format.
  * [gocask](http://code.google.com/p/gocask/) - Key-value store inspired by Riak Bitcask. Can be used as pure go implementation of dbm and other kv-stores.
  * [goleveldb](https://github.com/syndtr/goleveldb) - Another implementation of LevelDB key/value in pure Go.
  * [kv](http://github.com/cznic/kv) - Yet another key/value persistent store. Atomic operations, two phase commit, automatic crash recovery, ...
  * [leveldb-go](http://code.google.com/p/leveldb-go/) - This is an implementation of the LevelDB key/value database.
  * [levigo](https://github.com/jmhodges/levigo) - levigo provides the ability to create and access LevelDB databases.
  * [persival](https://github.com/nu7hatch/persival) - Programatic, persistent, pseudo key-value storage

### Graph Databases

  * [cayley](https://github.com/google/cayley) - 100% Go graph database, inspired by Freebase and the Google Knowledge Graph.
  * [Dgraph](https://github.com/dgraph-io/dgraph) - Fast, Distributed Graph DB with a GraphQL-like API.
  * [go-gremlin](https://github.com/go-gremlin/gremlin) - A Go client for the Apache TinkerTop Graph analytics framework (Gremlin server).

### NoSQL

  * [influxdb](https://github.com/influxdb/influxdb) - Scalable datastore for metrics, events, and real-time analytics
  * [ledisdb](https://github.com/siddontang/ledisdb) - A high performance NoSQL like Redis.
  * [nodb](https://github.com/lunny/nodb) - A pure Go embed Nosql database with kv, list, hash, zset, bitmap, set.
  * [tiedot](https://github.com/HouzuoGuo/tiedot) - A NoSQL document database engine using JSON for documents and queries; it can be embedded into your program, or run a stand-alone server using HTTP for an API.

### Other

  * [cabinet](https://bitbucket.org/ww/cabinet) - Kyoto Cabinet bindings for go
  * [camlistore](https://github.com/camlistore/camlistore) - Personal distributed storage system for life.
  * [cdb.go](https://github.com/jbarham/cdb.go) - Create and read cdb ("constant database") files
  * [go-clickhouse](https://github.com/roistat/go-clickhouse) - Connector to Yandex Clickhouse (column-oriented database)
  * [CodeSearch](https://github.com/google/codesearch) - Index and perform regex searches over large bodies of source code
  * [couch-go](http://couch-go.googlecode.com) - newer maintained CouchDB database binding
  * [couchgo](https://github.com/lancecarlson/couchgo) - The most feature complete CouchDB Adapter for Go. Modeled after couch.js.
  * [dbxml](https://github.com/pebbe/dbxml) - A basic interface to Oracle Berkeley DB XML
  * [drive](https://github.com/odeke-em/drive) - A Google drive command line client
  * [Event Horizon](https://github.com/looplab/eventhorizon) - Toolkit for Command Query Responsibility Segregation and Event Sourcing (CQRS/ES)
  * [go-db-oracle](https://code.google.com/p/go-db-oracle/) - GO interface to Oracle DB
  * [gographite](https://github.com/amir/gographite) - statsd server in go (for feeding data to graphite)
  * [gokabinet](https://github.com/fsouza/gokabinet) - Go bindings for Kyoto Cabinet DBM implementation
  * [go-model](https://github.com/jeevatkm/go-model) - Robust & Easy to use struct mapper and utility methods for Go
  * [go-notify](https://github.com/lenormf/go-notify) - GO bindings for the libnotify
  * [goprotodb](http://launchpad.net/goprotodb) - A binding to Berkeley DB storing records encoded as Protocol Buffers.
  * [go-rexster-client](https://github.com/sqs/go-rexster-client) - Go client for the [Rexster graph server](https://github.com/tinkerpop/rexster/wiki) (part of the [TinkerPop](http://www.tinkerpop.com/) suite of graph DB tools)
  * [goriak](https://bitbucket.org/lateefj/goriak/overview) - Database driver for riak database (project homepage is now on bitbucket.org)
  * [goriakpbc](https://github.com/tpjg/goriakpbc) - Riak driver using Riak's protobuf interface
  * [gotyrant](https://github.com/patrickxb/gotyrant) - A Go wrapper for tokyo tyrant
  * [go-wikiparse](https://github.com/dustin/go-wikiparse) - mediawiki dump parser for working with wikipedia data
  * [hdfs](https://github.com/zyxar/hdfs) - go bindings for libhdfs
  * [JGDB](http://www.robotamer.com/html/GoTamer/JGDB.html) - JGDB stands for Json Git Database
  * [mig](https://github.com/jagregory/mig) - Simple SQL-based database migrations
  * [mongofixtures](https://github.com/OwlyCode/mongofixtures) - A Go quick and dirty utility for cleaning MongoDB collections and loading fixtures into them.
  * [Neo4j-GO](https://github.com/davemeehan/Neo4j-GO) - Neo4j REST Client in Go
  * [neoism](https://github.com/jmcvetta/neoism) - Neo4j graph database client, including Cypher and Transactions support.
  * [null](https://github.com/guregu/null) - Package for handling null values in SQL
  * [Optimus Cache Prime](http://patrickmylund.com/projects/ocp/) - Smart cache preloader for websites with XML sitemaps.
  * [piladb](https://github.com/fern4lvarez/piladb) - Lightweight RESTful database engine based on stack data structures.
  * [pravasan](https://pravasan.github.io/pravasan) - Simple Migration Tool (like rake db:migrate with more flexibility)
  * [riako](https://github.com/jkassemi/riako) - High level utility methods for interacting with Riak databases
  * [sqlbuilder](https://github.com/thcyron/sqlbuilder) - SQL query builder with row mapping
  * [sqlf](https://github.com/keegancsmith/sqlf) - Create parameterized SQL statements in Go, sprintf style
  * [squirrel](https://github.com/lann/squirrel) - Fluent SQL generation for Go
  * [Sublevel](https://github.com/fiatjaf/sublevel) - Separate sections of the same LevelDB
  * [Weed File System](https://github.com/chrislusf/seaweedfs) - fast distributed key-file store
  * [whisper-go](https://github.com/kisielk/whisper-go) - library for working with whisper databases
  * [remapper](https://github.com/plandem/remapper) - library to convert/map data from one type to another
  * [xo](https://github.com/xo/xo) - CLI to generate idiomatic Go code for databases
  * [go-batcher](https://github.com/yyh1102/go-batcher) - Simply create and use batch handler in Go

## Date

  * [now](https://github.com/jinzhu/now) - Now is a time toolkit for golang.
  * [date](https://github.com/fxtlabs/date) - A package for working with dates.
  * [date](https://github.com/rickb777/date) - For dates, date ranges, time spans, periods, and time-of-day.
  * [gostrftime](https://github.com/cactus/gostrftime) - strftime(3) like formatting for time.Time
  * [goment](https://github.com/nleeper/goment) - Go time library inspired by Moment.js
  * [tai64](https://github.com/cactus/tai64) - tai64 and tai64n parsing and formatting
  * [tuesday](https://github.com/osteele/tuesday) - A Strftime implementation that's compatible with Ruby's `Time.strftime`
  * [Tideland golib](https://github.com/tideland/golib) - Timex extensions
  * [hijri](https://github.com/younisshah/hijri) - A small helper library to convert a Hijri date to a Gregorian date according to Ummul Qura calendar.

## Development Tools

  * [cwrap](https://github.com/hailiang/cwrap) - Go wrapper (binding) generator for C libraries.
  * [demand](https://github.com/tv42/demand) - Download, build, cache and run a Go app easily.
  * [glib](https://github.com/ziutek/glib) - Bindings for GLib type system
  * [go-callvis](https://github.com/TrueFurby/go-callvis) - Visualize call graph of your Go program using dot format. 
  * [gocog](https://github.com/natefinch/gocog) - A code generator that can generate code using any language
  * [godepgraph](https://github.com/kisielk/godepgraph) - Create a dependency graph for a go package
  * [godev](https://github.com/kdar/godev) - Recompiles and runs your Go code on source change. Also watches all your imports for changes.
  * [godiff](https://github.com/spcau/godiff) - diff file comparison tool with colour html output
  * [gonew](https://github.com/bmatsuo/gonew) - A tool to create new Go projects
  * [go-play](https://code.google.com/p/go-play) - A HTML5 web interface for experimenting with Go code. Like http://golang.org/doc/play but runs on your computer
  * [gore](https://github.com/motemen/gore) - A Go REPL. Featured with line editing, code completion, and more
  * [gorun](https://wiki.ubuntu.com/gorun) - Enables Go source files to be used as scripts.
  * [go-spew](https://github.com/davecgh/go-spew) - Implements a deep pretty printer for Go data structures to aid in debugging
  * [goven](https://github.com/kr/goven) - Easily copy code from another project into yours
  * [gowatcher](https://github.com/nickjj/gowatcher) - Reload a specified go program automatically by monitoring a directory.
  * [GoWatch](https://bitbucket.org/gotamer/gowatch) - GoWatch watches your dev folder for modified files, and if a file changes it restarts the process.
  * [goweb](https://bitbucket.org/santucco/goweb) - Literate programming tools for Go based on CWEB by Donald Knuth and Silvio Levy.
  * [hopwatch](https://github.com/emicklei/hopwatch) - simple debugger for Go
  * [hsandbox](http://labix.org/hsandbox) - Tool for quick experimentation with Go snippets
  * [Inject](https://github.com/facebookgo/inject) - Library for dependency injection in Golang (from Facebook)
  * [liccor](https://github.com/gtalent/liccor) - A tool for updating license headers in Go source files
  * [liteide](https://github.com/visualfc/liteide) - An go auto build tools and qt-based ide for Go
  * [Livedev](https://github.com/qrtz/livedev) - Livedev is a development proxy server that enables live code reloading.
   * [Martian](https://github.com/google/martian) - HTTP proxy designed for use in E2E testing.
  * [nvm-windows](https://github.com/coreybutler/nvm-windows) - Node.js version manager for Windows
  * [prettybenchcmp](https://github.com/im7mortal/prettybenchcmp) - Store and compare benchmarks history locally.
  * [rerun](https://github.com/skelterjohn/rerun) - Rerun watches your binary and all its dependencies so it can rebuild and relaunch when the source changes.
  * [syntaxhighlighter](https://github.com/sourcegraph/syntaxhighlight) - language-independent code syntax highlighting library
  * [toggle](https://github.com/xchapter7x/toggle) - A feature toggle library with built in support for environment variable backed toggling. pluggable backing engine support.
  * [trace](https://bitbucket.org/santucco/trace) - A simple debug tracing

### Emacs Tags

  * [egotags](http://bitbucket.org/scriptdevil/egotags/) - ETags generator
  * [tago1](https://github.com/willoch/tago) - etags generator for go that builds with go 1
  * [tago](https://github.com/AlexCombas/Tago) - Emacs TAGS generator for Go source

## Distributed/Grid Computing

  * [celeriac](https://github.com/svcavallar/celeriac.v1) - A library for adding support for interacting and monitoring Celery workers, tasks and events in Go
  * [donut](https://github.com/dforsyth/donut) - A library for building clustered services in Go
  * [libchan](https://github.com/docker/libchan) - Go-like channels over the network
  * [locker](https://github.com/jagregory/locker) - A distributed lock service built on top of [etcd](https://github.com/coreos/etcd).
  * [dlock](https://github.com/temoto/dlock) - A native Go distributed lock manager (client and server) using gRPC.
  * [mangos](https://github.com/gdamore/mangos) - An implementation of the Scalable Protocols based on [nanomsg](http://nanomsg.org/)
  * [redsync](https://github.com/hjr265/redsync.go) - Redis-based distributed mutual exclusion lock implementation
  * [Skynet](https://github.com/skynetservices/skynet) - Skynet is distributed mesh of processes designed for highly scalable API type service provision.
  * [Tideland golib](https://github.com/tideland/golib) - Includes a map/reduce library

## Documentation

  * [examplgen](https://github.com/gima/examplgen) - Insert code from .go files to documents (examples to project's readme, for instance).
  * [godocdown](https://github.com/robertkrimen/godocdown) - Format package documentation (godoc) as GitHub friendly Markdown
  * [GoDoc.org](http://godoc.org/) - GoDoc.org generates documentation on the fly from source on Bitbucket, Github, Google Project Hosting and Launchpad.
  * [golangdoc](https://github.com/golang-china/golangdoc) - Godoc for Golang, support translate.
  * [Mango](http://code.google.com/p/mango-doc/) - Automatically generate unix man pages from Go sources
  * [redoc](https://github.com/simonz05/redoc) - Commands documentation for Redis
  * [sphinxcontrib-golangdomain](http://pypi.python.org/pypi/sphinxcontrib-golangdomain) - Sphinx domain for Go
  * [test2doc](https://code.google.com/p/test2doc/) - Generate documentation for your go units from your unit tests.

## Editors
  * [A](https://github.com/as/a) - A graphical text and binary editor based on Acme
  * [Conception](https://github.com/shurcooL/Conception) - Conception is an experimental research project, meant to become a modern IDE/Language package.  [demo video](http://youtu.be/DNJ7HqlV55k)
  * [de](https://github.com/driusan/de) - A modal graphical editor with Acme and vi features
  * [Go-bbpackage](https://github.com/ascarter/Go-bbpackage) - BBEdit package for Go development
  * [goclipse](https://github.com/GoClipse/goclipse) - An Eclipse-based IDE for Go.
  * [Go conTEXT](http://www.tc33.org/go/go-programming-highlighter-for-context-editor/) - Highlighter plugin
  * [godev](https://github.com/sirnewton01/godev) - Web-based IDE for the Go language
  * [godit](https://github.com/nsf/godit) - A microemacs-like text editor written in Go.
  * [gofinder](https://github.com/mpl/gofinder) - (code) search tool for acme
  * [go-gedit](http://code.google.com/p/go-gedit3-plugin/) - Google Go language plugin for gedit
  * [golab](https://github.com/mb0/lab) - go local application builder - a web-based Go ide
  * [Google Go for Idea](http://plugins.intellij.net/plugin/?idea&id=5047) - Google Go language plugin for Intellij IDEA
  * [micro](https://github.com/zyedidia/micro) - A modern and intuitive terminal-based text editor.
  * [T](https://github.com/eaburns/T) - An Acme/Sam like text editor
  * [tabby](https://github.com/mikhailt/tabby) - Source code editor
  * [ViGo](https://github.com/kisielk/vigo) - A vim-like text editor.
  * [Wide](https://github.com/b3log/wide) - A Web-based IDE for Teams using Golang.

## Email

  * [Hectane](https://github.com/hectane/hectane) - Lightweight SMTP client including a built-in mail queue backed by on-disk storage.
  * [gmail](https://github.com/SlyMarbo/gmail) - Simple library for sending emails from a Gmail account, for people not interested in dealing with protocol details.
  * [go-mail](https://github.com/ungerik/go-mail) - Email utilities including RFC822 messages and Google Mail defaults.
  * [Gomail](https://github.com/go-gomail/gomail) - A simple and efficient package to send emails.
  * [go-ses](https://github.com/sourcegraph/go-ses) - Amazon AWS Simple Email Service (SES) API client
  * [Inbucket](http://jhillyerd.github.io/inbucket/) - Inbucket is an email testing service; it will accept messages for any email address and make them available to view via a web interface.
  * [mail.go](https://bitbucket.org/taruti/mail.go) - Parse email messages
  * [MailHog](https://github.com/mailhog/MailHog) - Email testing service, inspired by MailCatcher.
  * [MailSlurper](https://github.com/mailslurper/mailslurper) - A handy SMTP mail server useful for local and team application development. Slurp mail into oblivion!
  * [chasquid](https://blitiri.com.ar/p/chasquid) - SMTP server written in Go.

## Error handling
  * [hierr](https://github.com/reconquest/hierr-go) - Nesting errors in hierarchy.
  * [errgo](https://github.com/juju/errgo) - Error tracing and annotation.
  * [errors](https://github.com/juju/errors) - The juju/errors package provides an easy way to annotate errors without losing the original error context, and get a stack trace back out of the error for the locations that were recorded.
  * [errors](https://github.com/aletheia7/errors) - errors augments and error with a file and line number.
  * [goerr](https://github.com/goerr/goerr) - Allows to make a separate(modular) and reusable error handlers. Exception-like panic() recover() mechanism using Return(error) and catching err := OR1(..)
  * [panicparse](https://github.com/maruel/panicparse/) - Parse panics with style.
  * [Space Monkey errors](https://github.com/spacemonkeygo/errors) - Go's missing errors library - stack capture, error hierarchies, error tags
  * [Tideland golib](https://github.com/tideland/golib) - Detailed error values

## Encodings and Character Sets

  * [base58](https://github.com/tv42/base58) - Human input-friendly base58 encoding
  * [bencode-go](https://github.com/jackpal/bencode-go) - Encoding and decoding the bencode format used by the BitTorrent peer-to-peer file sharing protocol
  * [bsonrpc](https://github.com/skelterjohn/bsonrpc) - BSON codec for net/rpc
  * [chardet](https://github.com/saintfish/chardet) - Charset detection library ported from ICU
  * [charmap](https://github.com/disintegration/charmap) - Character encodings in Go
  * [codec-msgpack-binc](https://github.com/ugorji/go/tree/master/codec#readme) High Performance and Feature-Rich Idiomatic Go Library providing encode/decode support for multiple binary serialization formats: [msgpack](http://www.msgpack.org)
  * [colfer](https://github.com/pascaldekloe/colfer) - high-performance binary codec
  * [gobson](http://labix.org/gobson) - BSON (de)serializer
  * [go-charset](http://code.google.com/p/go-charset/) - Conversion between character sets. Native Go.
  * [go.enmime](https://github.com/jhillyerd/go.enmime) - MIME email parser library for Go (native)
  * [go-msgpack](https://github.com/ugorji/go-msgpack) - Comprehensive MsgPack library for Go, with pack/unpack and net/rpc codec support (DEPRECATED in favor of [codec](https://github.com/ugorji/go/tree/master/codec#readme) )
  * [gopack](https://github.com/joshlf13/gopack) - Bit-packing for Go
  * [go-simplejson](https://github.com/bitly/go-simplejson) - a Go package to interact with arbitrary JSON
  * [go-wire](https://github.com/tendermint/go-wire) - Binary and JSON codec for structures and more
  * [go-xdr](https://github.com/davecgh/go-xdr) - Pure Go implementation of the data representation portion of the External Data Representation (XDR) standard protocol as specified in RFC 4506 (obsoletes RFC 1832 and RFC 1014).
  * [iconv-go](https://github.com/djimenez/iconv-go) - iconv wrapper with Reader and Writer
  * [magicmime](https://github.com/rakyll/magicmime) -- Mime-type detection with Go bindings for libmagic
  * [Mahonia](http://code.google.com/p/mahonia/source/browse/) - Character-set conversion library in Go
  * [mimemagic](https://bitbucket.org/taruti/mimemagic) - Detect mime-types automatically based on file contents with no external dependencies
  * [mimemagic](https://github.com/zRedShift/mimemagic) - A pure-Go MIME sniffing library/tool based on the FreeDesktop.org spec
  * [msgpack](https://github.com/vmihailenco/msgpack) - Msgpack format implementation for Go
  * [msgpack-json](https://github.com/tv42/msgpack-json) - Command-line utilities to convert between msgpack and json
  * [nnz](https://sourcegraph.com/github.com/sourcegraph/go-nnz) - String and Int primitives that serialize to JSON and SQL null
  * [storable](https://github.com/kdar/storable) - Write perl storable data
  * [TNetstring](https://github.com/edsrzf/tnetstring-go) - tnetstrings (tagged Netstrings)

## File Systems

  * [afero](https://github.com/spf13/afero) - A File Sytem abstraction system for Go
  * [go.fs](https://github.com/daaku/go.fs) - A virtual file system abstraction layer.
  * [poller](https://github.com/npat-efault/poller) - Package poller is a file-descriptor multiplexer. It allows concurent Read and Write operations from and to multiple file-descriptors.
  * [vfsgen](https://github.com/shurcooL/vfsgen) - Generates a vfsdata.go file that statically implements the given virtual filesystem.


## Games

  * [Bampf](https://github.com/gazed/bampf) - Arcade style game based on the Vu 3D engine.
  * [bloxorz](https://github.com/YouriAckx/bloxorz) - Solver for bloxorz basic levels
  * [ChessBuddy](https://github.com/tux21b/ChessBuddy) - Play chess with Go, HTML5, WebSockets and random strangers!
  * [Fergulator](https://github.com/scottferg/Fergulator) - An NES emulator, using SDL and OpenGL
  * [FlappyBird](https://github.com/himanshushekhar/golang-flappybirdclone) - A simple flappy bird clone written in golang.
  * [godoku](http://code.google.com/p/kylelemons/source/browse?repo=godoku) - Go Sudoku Solver - example of "share by communicating"
  * [Gongo](https://github.com/skybrian/Gongo) - A program written in Go that plays Go
  * [gospeccy](https://github.com/remogatto/gospeccy) - A ZX Spectrum 48k Emulator
  * [Ludo Game](http://ludo.abiosoft.net) - Ludo Board game powered by Go on Appengine
  * [pinkman](https://github.com/jubalh/pinkman) - command line based chess interface to UCI compatible chess engines
  * [Pong](https://github.com/LaurenceGA/Pong) - A simple Pong clone written in golang
  * [pong-command](https://github.com/kurehajime/pong-command) - Joke command,ping-like pong.
  * [Steven](https://github.com/thinkofdeath/steven) - A Minecraft client in Go
  * [ukodus](https://github.com/9nut/ukodus) - Sudoku solver in Go
  * [WolfenGo](https://github.com/gdm85/wolfengo) - A Wolfenstein3D clone in Go, using OpenGL 2.1

## GIS

  * [geojson](https://github.com/kpawlik/geojson) - Go package to quick and easy create json data in geojson format. [description](http://kpawlik.github.io/geojson)
  * [go-geom](https://github.com/twpayne/go-geom) - Efficient Open Geo Consortium-style geometries with native Go GeoJSON and WKB encoding and decoding (work-in-progress)
  * [go.geo](https://github.com/paulmach/go.geo) - Geometry/geography library targeted at online mapping
  * [go.geojson](https://github.com/paulmach/go.geojson) - Marshalling and Unmarshalling of GeoJSON objects
  * [gogeos](http://paulsmith.github.io/gogeos/) - Go library for spatial data operations and geometric algorithms
  * [go-proj-4](https://github.com/pebbe/go-proj-4) - An interface to the Cartographic Projections Library PROJ.4
  * [go-kml](https://github.com/twpayne/go-kml) - Google Earth KML generation
  * [go-polyline](https://github.com/twpayne/go-polyline) - Google Maps polyline encoding and decoding
  * [orb](https://github.com/paulmach/orb) - 2d geometry manipulation (length, area, polygon contains, etc.) with geojson, wkb, mvt support
  * [osm](https://github.com/paulmach/osm) - General purpose library for reading, writing and working with OpenStreetMap data
  * [UTM](https://github.com/im7mortal/UTM) - Bidirectional UTM-WGS84 converter

## Go Implementations

  * [llgo](http://llvm.org/klaus/llgo) - LLVM-based Go compiler, written in Go


## Graphics and Audio

  * [AnsiGo](https://github.com/fcambus/ansigo) - Simple ANSi to PNG converter written in pure Go
  * [Arclight](http://www.angryredplanet.com/exh/arclight/) - Arclight is a tool for rendering images
  * [bild](https://github.com/anthonynsimon/bild) - A collection of image processing algorithms in pure Go
  * [bimg](https://github.com/h2non/bimg) - Small Go library for fast image resize and transformation using libvips
  * [blend](https://github.com/Phrozen/blend) - Image processing library and rendering toolkit for Go.
  * [bpg](https://github.com/chai2010/bpg) - BPG decoder for Go.
  * [chart](https://github.com/vdobler/chart) - Library to generate common chart  (pie, bar, strip, scatter, histogram) in different output formats.
  * [draw2d](https://github.com/llgcode/draw2d) - This package provide an API to draw 2d geometrical form on images. This library is largely inspired by postscript, cairo, HTML5 canvas.
  * [egl](http://godoc.org/github.com/mortdeus/egles/egl) - egl bindings
  * [es2](http://godoc.org/github.com/mortdeus/egles/es2) - es2 bindings
  * [fourcc](https://github.com/reiver/go-fourcc) - Go implementation of FOURCC (four character code) (4CC) identifiers for a video codecs, compression formats, colors, and pixel format used in media files.
  * [freetype-go](http://code.google.com/p/freetype-go/) - a Go implementation of FreeType
  * [gltf](https://github.com/sturfeeinc/glTF) - library for marshaling and unmarshaling glTF
  * [glfw 3](https://github.com/go-gl/glfw3) - Go bindings for GLFW 3 library
  * [glfw](https://github.com/go-gl/glfw) - bindings to the multi-platform library for opening a window, creating an OpenGL context and managing input
  * [glh](https://github.com/go-gl/glh) - OpenGL helper functions to manage text, textures, framebuffers and more
  * [gl](https://github.com/go-gl/gl) - OpenGL bindings using glew
  * [glu](https://github.com/go-gl/glu) - bindings to the OpenGL Utility Library
  * [gmask](https://github.com/fggp/gmask) - Go adaptation of the Cmask utility for Csound
  * [goalsa](https://github.com/cocoonlife/goalsa) - Go bindings for ALSA capture and playback
  * [go-cairo](https://github.com/ungerik/go-cairo) - Go wrapper for the cairo graphics library
  * [gocl](https://github.com/rainliu/gocl) - Go OpenCL (gocl) binding, support OpenCL 1.1/1.2/2.0 on Mac/Linux/Windows/Android
  * [go-csnd6](https://github.com/fggp/go-csnd6) - Go binding to the Csound6 API
  * [go-csperfthread](https://github.com/fggp/go-csperfthread) - Go binding to the CsoundPerformanceThread helper class of the Csound6 API
  * [goexif](https://github.com/rwcarlsen/goexif) - Retrieve EXIF metadata from image files
  * [goflac](https://github.com/cocoonlife/goflac) - Go bindings for decoding and encoding FLAC audio with libFLAC
  * [go-gd](https://github.com/bolknote/go-gd) - Go bingings for GD
  * [GoGL](https://github.com/chsc/GoGL) - OpenGL binding generator
  * [go-gnuplot](https://github.com/sbinet/go-gnuplot) - go bindings for Gnuplot
  * [go-gtk3](https://github.com/norisatir/go-gtk3) - gtk3 bindings for go
  * [go-heatmap](https://github.com/dustin/go-heatmap) - A toolkit for making heatmaps
  * [GoHM](https://github.com/rainliu/GoHM) - H.265/HEVC HM Video Codec in Go
  * [goHorde](https://bitbucket.org/tshannon/gohorde/src) - Go Bindings for the Horde3d Rendering engine.
  * [GoMacDraw](https://github.com/skelterjohn/gmd) - A mac implementation of go.wde
  * [go-openal](https://github.com/phf/go-openal) - Experimental OpenAL bindings for Go
  * [go-opencl](https://github.com/tones111/go-opencl) - A go wrapper to the OpenCL heterogeneous parallel programming library
  * [go-opencv](https://github.com/lazywei/go-opencv) - Go bindings for OpenCV / 2.x API in gocv / 1.x API in opencv
  * [Go-OpenGL](https://github.com/banthar/Go-OpenGL) - Go bindings for OpenGL
  * [Goop](https://github.com/peterbourgon/goop) - Audio synthesizer engine
  * [goray](http://goray.sourceforge.net/) - Raytracer written in Go, based on Yafaray
  * [gosc](https://bitbucket.org/liamstask/gosc) - Pure Go OSC (Open Sound Control) library
  * [go-taglib](https://github.com/wtolson/go-taglib) - Go wrapper for TagLib, an audio meta-data parser
  * [go-tmx](https://github.com/salviati/go-tmx) - A Go library that reads Tiled's TMX files
  * [GoVisa](https://github.com/rainliu/GoVisa) - H265/HEVC Bitstream Analyzer in Go
  * [go-vlc](https://github.com/jteeuwen/go-vlc) - Go bindings for libVLC
  * [go.wde](https://github.com/skelterjohn/go.wde) - A windowing/drawing/event interface
  * [goxscr](http://goxscr.googlecode.com) - Go rewrites of xscreensaver ports
  * [gst](https://github.com/ziutek/gst) - Go bindings for GStreamer
  * [gumble](https://github.com/layeh/gumble) - Client library for the [Mumble](http://mumble.info) VoIP protocol
  * [hgui](https://github.com/zozor/hgui) - Gui toolkit based on http and gtk-webkit.
  * [imaginary](https://github.com/h2non/imaginary) - Simple and fast HTTP microservice for image resizing and manipulation
  * [imaging](https://github.com/disintegration/imaging) - Package imaging provides basic image manipulation functions (resize, rotate, flip, crop, etc.) as well as simplified image loading and saving.
  * [netpbm](https://github.com/spakin/netpbm) - Read and write Netpbm images from Go programs
  * [opencv](https://github.com/chai2010/opencv/) - Go bindings for OpenCV
  * [osmesa](https://github.com/go-gl/osmesa) - Go bindings for osmesa.
  * [phono](https://github.com/dudk/phono) - DSP pipeline.
  * [Plotinum](https://github.com/gonum/plot) - An API for creating plots
  * [portaudio](http://code.google.com/p/portaudio-go/) - A Go binding to PortAudio
  * [pulsego](https://github.com/moriyoshi/pulsego/) - Go binding for PulseAudio
  * [pulse-simple](https://github.com/mesilliac/pulse-simple/) - Go bindings for PulseAudio's Simple API, for easy audio capture and playback.
  * [resize](https://github.com/nfnt/resize) - Image resizing with different interpolations.
  * [RiGO](https://github.com/mae-global/rigo) - RenderMan Interface implementation in Go. 
  * [smartcrop](https://github.com/muesli/smartcrop) - Content aware image cropping
  * [starfish](https://github.com/gtalent/starfish) - A simple Go graphics and user input library, built on SDL
  * [stl](https://github.com/hschendel/stl) - library for reading, writing, and manipulating Stereolithography (.stl) files used in 3D printing
  * [svgo](https://github.com/ajstarks/svgo) - a library for creating and outputting SVG
  * [tag](https://github.com/dhowden/tag) - a library for reading tag metadata and creating metadata-invariant checksums for audio files: FLAC, all IDv3 variants, and MP4 (ACC, ALAC)
  * [tga](https://github.com/ftrvxmtrx/tga) - TARGA image format encoding/decoding library
  * [tiff](https://github.com/chai2010/tiff) - Rich TIFF/BigTIFF/GeoTIFF decoder/encoder for Go.
  * [twilio-go](https://github.com/kevinburke/twilio-go) - Go client for the Twilio API.
  * [videoinput](https://github.com/chai2010/videoinput) - Go bindings for VideoInput (Windows).
  * [vu](https://github.com/gazed/vu) - Virtual Universe. A skeleton 3D engine.
  * [vulkan](https://github.com/vulkan-go/vulkan) - Golang Bindings for Vulkan API.
  * [webp](https://github.com/chai2010/webp) - WebP decoder and encoder for Go.
  * [wg](https://github.com/magsoft-se/wg) - Web Graphics, display real time go graphics in browser, with user input.
  * [window](https://github.com/jbrukh/window) - Optimized moving window for real-time data
  * [wingo](https://github.com/BurntSushi/wingo) - A fully-featured window manager written in Go.
  * [Winhello](https://github.com/MalcolmJSmith/Winhello) - An example Windows GUI hello world application
  * [wxGo](https://github.com/JeroenD/wxGo) - Go Wrapper for the wxWidgets GUI
  * [xgb](https://github.com/BurntSushi/xgb) - A fork of the x-go-binding featuring support for thread safety and all X extensions.
  * [xgbutil](https://github.com/BurntSushi/xgbutil/) - A utility library to make use of the X Go Binding easier. (Implements EWMH and ICCCM specs, key binding support, etc.)
  * [x-go-binding](http://code.google.com/p/x-go-binding/) - bindings for the X windowing system

## GUIs and Widget Toolkits

  * [go-fltk](https://github.com/zot/go-fltk) - FLTK2 GUI toolkit bindings for Go
  * [go-gtk](https://github.com/mattn/go-gtk) - Bindings for GTK
  * [go-qt5](https://github.com/salviati/go-qt5) - QT5 bindings for go
  * [gothic](https://github.com/nsf/gothic) - Tcl/Tk Go bindings
  * [gotk3](https://github.com/gotk3/gotk3) - Go bindings for GTK3, requires GTK version 3.8
  * [go.uik](https://github.com/skelterjohn/go.uik) - A UI kit for Go, in Go. (project is closed)
  * [go-webkit2](https://sourcegraph.com/github.com/sourcegraph/go-webkit2) - Go bindings for the WebKitGTK+ v2 API (w/headless browser & JavaScript support)
  * [Gowut](https://sites.google.com/site/gowebuitoolkit/) - Gowut (Go Web UI Toolkit) is a full-featured, easy to use, platform independent Web UI Toolkit written in pure Go, no platform dependent native code is linked or called.
  * [GXUI](https://github.com/google/gxui) - A Go cross platform UI library.
  * [iup](https://github.com/grd/iup) - Bindings for [IUP](http://www.tecgraf.puc-rio.br/iup)
  * [mdtwm](https://github.com/ziutek/mdtwm) - Tiling window manager for X
  * [qml](https://github.com/niemeyer/qml) - QML support for the Go language
  * [ui](https://github.com/andlabs/ui) - Platform-native GUI library for Go
  * [webview](https://github.com/zserge/webview) - Tiny cross-platform web UI library. Uses WebKit (Gtk/Cocoa) and MSHTML (Windows)

## Hardware

  * [go.hid](https://github.com/GeertJohan/go.hid) - Provides communication with USB Human Interface Devices.
  * [gortlsdr](https://github.com/jpoirier/gortlsdr) - A librtlsdr wrapper, which turns certain USB DVB-T dongles into a low-cost, general purpose software-defined radio receiver.
  * [hwio](https://github.com/mrmorphic/hwio) - Hardware I/O library for SoC boards including BeagleBone Black and Raspberry Pi.
  * [stressdisk](https://github.com/ncw/stressdisk) - Stress test your disks / memory cards / USB sticks before trusting your valuable data to them
  * [gobot](https://gobot.io) - Golang framework for robotics, drones, and the Internet of Things (IoT).

## Language and Linguistics

  * [alpinocorpus-go](https://github.com/rug-compling/alpinocorpus-go) - A reader and a writer for Alpino corpora.
  * [go-aspell](https://github.com/trustmaster/go-aspell) - GNU Aspell spell checking library bindings for Go.
  * [go-language](https://github.com/matiasinsaurralde/go-language) - A simple language detector using letter frequency data.
  * [go-ngram](https://github.com/euskadi31/go-ngram) - An n-gram is a contiguous sequence of n items from a given sequence of text or speech.
  * [go-tokenizer](https://github.com/euskadi31/go-tokenizer) - A Text Tokenizer library for Golang
  * [go.stringmetrics](https://github.com/robyoung/go.stringmetrics) - String distance metrics implemented in Go
  * [goling](https://github.com/gyuho/goling) - String Similarity(Cosine Similarity, Levenshtein Distance), Spell Check, Segmentation
  * [inflect](https://bitbucket.org/pkg/inflect) - Word inflection library (similar to Ruby ActiveSupport::Inflector). Singularize(), Pluralize(), Underscore() etc.
  * [libtextcat](https://github.com/pebbe/libtextcat) - A Go wrapper for libtextcat.
  * [nlp](https://github.com/james-bowman/nlp) - Go Natural Language Processing library supporting LSA (Latent Semantic Analysis).
  * [sego](https://github.com/huichen/sego) - Chinese language segmenter.
  * [snowball](https://github.com/kljensen/snowball) - Snowball stemmers for multiple languages
  * [textcat](https://github.com/pebbe/textcat) - N-gram based text categorization, with support for utf-8 and raw text

## Logging and Monitoring

  * [colog](https://github.com/comail/colog) - CoLog is a prefix-based leveled execution log for Go
  * [cue](https://github.com/bobziuchkovski/cue) - Fast and flexible contextual logger.  Supports output to file, syslog, structured syslog, stdout/stderr, socket, Loggly, Honeybadger, Opbeat, Rollbar, and Sentry.
  * [epazote](https://github.com/epazote/epazote/) - Automated Microservices Supervisor.
  * [factorlog](https://github.com/kdar/factorlog) - Really fast, featureful logging infrastructure (supports colors, verbosity, and many formats)
  * [vlog](https://github.com/better0332/vlog) - Leveled log on std log for Go
  * [glog](https://github.com/golang/glog) - Leveled execution logs for Go
  * [go-logging](https://github.com/op/go-logging) - Supports different logging backends like syslog, file and memory. Multiple backends can be utilized with different log levels per backend and logger.
  * [gomol](https://www.github.com/aphistic/gomol) - A multi-output logging library designed for outputs that support additional metadata with log messages.
  * [graylog-golang](https://github.com/robertkowalski/graylog-golang) - graylog-golang is a full implementation for sending messages in GELF (Graylog Extended Log Format) from Google Go (Golang) to Graylog
  * [jWalterWeatherman](https://github.com/spf13/jwalterweatherman) - Seamless terminal printing and file logging that’s as easy to use as fmt.Println
  * [immortal](https://immortal.run) - A *nix cross-platform (OS agnostic) supervisor
  * [log4go](http://log4go.googlecode.com/) - Go logging package akin to log4j
  * [logger](https://github.com/weatherglass/pkg/tree/master/logger) - Go logging with buffered output and multiple writers
  * [logrus](https://github.com/Sirupsen/logrus) - Structured, pluggable logging for Go with built-in hooks for third-party loggers: Airbrake, Papertrail, Loggly, Sentry...
  * [MailJet Live Event Dashboard](https://github.com/arnaudbreton/mailjet-live-event-dashboard) - API monitoring in real time.
  * [monkit](https://github.com/spacemonkeygo/monkit) - A flexible process data collection, metrics, monitoring, instrumentation, and tracing library for Go
  * [Prometheus](https://github.com/prometheus/prometheus) - Monitoring system and time-series database.
  * [rfw](https://github.com/mipearson/rfw) - Rotating file writer - a 'logrotate'-aware file output for use with loggers
  * [sd](https://github.com/aletheia7/sd) - Writes to the systemd journal, supports user defined systemd journal fields
  * [seelog](https://github.com/cihub/seelog) - Flexible dispatching, filtering, and formatting
  * [snap](https://github.com/intelsdi-x/snap) - Telemetry framework
  * [spacelog](https://github.com/spacemonkeygo/spacelog) - Hierarchical, leveled, and structured logging library for Go
  * [statsgod](https://github.com/acquia/statsgod) - A rewrite of StatsD in Go.
  * [syslog](https://github.com/ziutek/syslog) - With this package you can create your own syslog server with your own handlers for different kind of syslog messages
  * [Tideland golib](https://github.com/tideland/golib) - Flexible logging
  * [timber](https://github.com/ngmoco/timber) - Configurable Logger for Go
  * [ul](https://github.com/aletheia7/ul) - Provides macOS Sierra/OSX Unified Loggging functionality via cgo

## Machine Learning

  * [bayesian](https://github.com/jbrukh/bayesian) - A naive bayes classifier.
  * [ctw](https://github.com/fumin/ctw) - Context Tree Weighting and Rissanen-Langdon Arithmetic Coding
  * [evo](https://github.com/cbarrick/evo) - a framework for implementing evolutionary algorithms in Go.
  * [go-algs/maxflow](https://github.com/daviddengcn/go-algs/tree/master/maxflow) Maxflow (graph-cuts) energy minimization library.
  * [go-galib](https://github.com/thoj/go-galib) - Genetic algorithms.
  * [golinear](https://github.com/danieldk/golinear) - Linear SVM and logistic regression.
  * [go\_ml](https://github.com/alonsovidales/go_ml) - Linear Regression, Logistic Regression, Neural Networks, Collaborative Filtering, Gaussian Multivariate Distribution.
  * [gorgonia](https://github.com/chewxy/gorgonia) - Neural network primitives library (like Theano or Tensorflow but for Go)
  * [go-porterstemmer](https://github.com/reiver/go-porterstemmer) - An efficient native Go clean room implementation of the Porter Stemming algorithm.
  * [go-pr](https://github.com/daviddengcn/go-pr) - Gaussian classifier.
  * [ntm](https://github.com/fumin/ntm) - [Neural Turing Machines](http://arxiv.org/pdf/1410.5401v2.pdf) implementation
  * [paicehusk](https://github.com/Rookii/paicehusk) - Go implementation of the Paice/Husk Stemmer
  * [go-mind](https://github.com/stevenmiller888/go-mind) - A neural network library built in Go
  * [Anna](https://github.com/xh3b4sd/anna) - Artificial Neural Network Aspiration, aims to be self-learning and self-improving software.
  * [Dialex](https://github.com/HyperLab-Solutions-Sdn-Bhd/dialex-sdk-go) - Dialex is a smart pipe that unscrambles text and makes it machine-readable.

## Mathematics

  * [bayesian](https://github.com/jbrukh/bayesian) - Naive Bayesian Classification for Go
  * [blas](https://github.com/ziutek/blas) - Go implementation of BLAS (Basic Linear Algebra Subprograms)
  * [cartconvert](https://github.com/the42/cartconvert) - cartography functions for the Go programming language
  * [clp](https://github.com/lanl/clp) - Go bindings for the COIN-OR Linear Programming (CLP) library
  * [Cvx](https://github.com/hrautila/cvx) - Convex optimization package, port of CVXOPT python package
  * [dice](https://github.com/tonio-ramirez/dice) - Dice rolling library
  * [evaler](https://github.com/soniah/evaler) - A simple floating point arithmetic expression evaluator
  * [fixed](https://github.com/klkblake/fixed) - A fixed point (Q32.32 format) math library
  * [geom](https://github.com/skelterjohn/geom) - 2d geometry
  * [gini](https://github.com/irifrance/gini) - SAT Solver/Boolean Logic Tools
  * [gochipmunk](https://github.com/paulcoyle/gochipmunk) - Go bindings to the Chipmunk Physics library
  * [gocomplex](http://code.google.com/p/gocomplex/) - a complex number library
  * [godec](http://godoc.org/speter.net/go/exp/math/dec/inf) - multi-precision decimal arithmetic
  * [gofd](https://bitbucket.org/gofd/gofd) - concurrent finite domain constraint solver.
  * [go-fftw](https://github.com/runningwild/go-fftw) - Go bindings for FFTW - The Fastest Fourier Transform in the West
  * [go-fn](https://code.google.com/p/go-fn/) - Special functions that would not fit in "math" pkg
  * [gographviz](https://github.com/awalterschulze/gographviz) - Graphviz DOT language parser for Go
  * [go-gt](https://code.google.com/p/go-gt/) - Graph theory algorithms
  * [go-humanize](https://github.com/dustin/go-humanize) - Formatting numbers for humans.
  * [golibs/xmath](https://github.com/SimonWaldherr/golibs/tree/master/xmath) - a collection of math functions (mostly mean algorithms)
  * [go-lm](https://github.com/awblocker/go-lm) - Linear models in Go. Provides WLS and regression with t residuals via a cgo -> BLAS/LAPACK interface.
  * [go.mahalanobis](https://github.com/ant0ine/go.mahalanobis) - Naive implementation of the Mahalanobis distance using go.matrix
  * [gomat](http://code.google.com/p/gomat/) - lightweight FAST matrix and vector math
  * [go\_matrix\_cuda](https://godoc.org/github.com/alonsovidales/go_matrix_cuda) - GPU-Accelerated Linear Algebra Libraries based in CUDA
  * [go.matrix](https://github.com/skelterjohn/go.matrix) - a linear algebra package
  * [gonum](https://github.com/gonum) - Scientific packages (linear algebra, BLAS, LAPACK, differentiation, plots, linear programming, statistics, ...)
  * [go-symexpr](https://github.com/verdverm/go-symexpr) - Symbolic math as an AST with derivatives, simplification, and non-linear regression
  * [gsl](https://bitbucket.org/mingzhi/gsl) - GNU Scientific Library bindings
  * [interval](http://godoc.org/github.com/cznic/interval) - Package interval handles sets of ordered values laying between two, possibly infinite, bounds.
  * [mathutil](http://godoc.org/github.com/cznic/mathutil) - Package mathutil provides utilities supplementing the standard 'math' and 'rand' packages.
  * [mt19937\_64](https://github.com/farces/mt19937_64) - Mersenne Twister int64 random source
  * [permutation](https://github.com/weatherglass/pkg/tree/master/permutation) - Package permutation generates permutations of the indices of a slice
  * [polyclip.go](https://github.com/akavel/polyclip.go) - Go implementation of algorithm for Boolean operations on 2D polygons
  * [primes](https://github.com/fxtlabs/primes) - Simple functionality for working with prime numbers.
  * [prime](https://github.com/kavehmz/prime) - Go version of Segmented Sieve and non Segmented sieve to produce prime numbers
  * [primegen.go](https://github.com/jbarham/primegen.go) - Sieve of Atkin prime number generator
  * [pso-go](https://github.com/tenntenn/pso-go) - A library of PSO (Particle Swarm Optimization) for Go.
  * [rand](https://bitbucket.org/MaVo159/rand) - 64-bit version of the math/rand package with Mersenne twister support.
  * [roger](https://github.com/senseyeio/roger) - A Go client for the RServer, allowing you to invoke R programs from Go.
  * [sparse](https://github.com/james-bowman/sparse) - Go Sparse matrix formats for linear algebra supporting scientific and machine learning applications, compatible with [gonum](https://github.com/gonum/gonum/mat) matrix libraries.
  * [stats](https://github.com/montanaflynn/stats) - A statistics package with common functions missing from the Golang standard library.
  * [statistics](https://github.com/grd/stat) - GNU GSL Statistics (GPLv3)
  * [Tideland golib](https://github.com/tideland/golib) - Numerics package for statistcal analysis
  * [Units](https://github.com/smyrman/units) - Implements types, units, converter functions and some mathematics for some common physical types. lib
  * [vector](https://github.com/proxypoke/vector) - A small vector lib.
  * [humanize](https://bitbucket.org/dchapes/humanize) - formats large numbers into human readable small numbers

## Microservices

  * [gokit](https://github.com/go-kit/kit) - The Go Kit microservice framework (and [author interview](http://www.infoq.com/news/2015/09/microservices-with-go-kit)).
  * [go-micro](https://github.com/micro/go-micro) - Go Micro is a microservices library which provides the fundamental building blocks for writing fault tolerant distributed systems at scale.
  * [kite](https://github.com/koding/kite) - RPC server and client framework.
  * [car_registration](https://github.com/infiniteloopltd/GoCarRegistrationAPI) - API wrapper for worldwide car registration data

## Miscellaneous

  * [atexit](https://bitbucket.org/tebeka/atexit) - Simple atexit library
  * [bíogo](https://github.com/biogo/biogo) - Basic bioinformatics functions for the Go language.
  * [Breaker](https://github.com/matttproud/golang_circuitbreaker) - Breaker enables graceful degraded mode operations by means of wrapping unreliable interservice interface points with circuit breaker primitives.
  * [btcrpcclient](https://github.com/btcsuite/btcrpcclient) - A Websocket-enabled Bitcoin JSON-RPC client.
  * [cast](https://github.com/spf13/cast) - Safe and easy casting from one type to another in Go
  * [CGRates](https://github.com/cgrates/cgrates) - Rating system designed to be used in telecom carriers world
  * [cpu](https://github.com/jpoirier/cpu) - A Go package that reports processor topology
  * [cron](https://github.com/robfig/cron) - A library for running jobs (funcs) on a cron-formatted schedule
  * [daemonigo](https://github.com/tyranron/daemonigo) - A simple library to daemonize Go applications.
  * [dbus-go](http://code.google.com/p/dbus-go/) - D-Bus Go library
  * [desktop](https://bitbucket.org/tebeka/desktop) - Open file/uri with default application (cross platform)
  * [devboard](https://launchpad.net/devboard) - Kanban board application based on Simple-Khanban
  * [dioder-api](https://github.com/piLights/Dioder-API) - An API to IKEA dioder LED-strips
  * [dump](http://code.google.com/p/golang/source/browse/src/pkg/dump/) - An utility that dumps Go variables, similar to PHP's var\_dump
  * [elPrep](https://github.com/ExaScience/elprep) - A high-performance tool for preparing sequence alignment/map files in DNA sequencing pipelines
  * [env](https://github.com/darkhelmet/env) - Easily pull environment variables with defaults
  * [epub](https://gitorious.org/go-pkg/epub) - Bindings for libepub to read epub content.
  * [EventBus](https://github.com/asaskevich/EventBus) - Lightweight event bus with async compatibility for Go .
  * [faker](https://github.com/manveru/faker) - Generate fake data, names, text, addresses, etc.
  * [fsnotify](https://github.com/howeyc/fsnotify) - File system notifications for Go
  * [functional](https://github.com/tcard/functional) - Functional programming library including a lazy list implementation and some of the most usual functions.
  * [GCSE](http://go-search.org/) - Go code search engine. [source](https://github.com/daviddengcn/gcse)
  * [generate](https://github.com/go-playground/generate) - runs go generate recursively on a specified path or environment variable and can filter by regex.
  * [go-amiando](https://github.com/ungerik/go-amiando) - Wrapper for the Amiando event management API
  * [go-bit](http://code.google.com/p/go-bit/) - An efficient and comprehensive bitset implementation with utility bit functions.
  * [go-bitops](https://github.com/cmchao/go-bitops) - common bit operations for 32/64 bit integer
  * [go-business-creditcard](https://github.com/dsparling/go-business-creditcard) - Validate/generate credit card checksums/names.
  * [gochem](http://github.com/rmera/gochem) - A computational chemistry/biochemistry library.
  * [gocsv](http://code.google.com/p/gocsv) - Library for CSV parsing and emitting
  * [go.dbus](https://github.com/guelfey/go.dbus) - Native Go library for D-Bus
  * [go-ean](https://github.com/nicholassm/go-ean) - A minimal utility library for validating EAN-8 and EAN-13 and calculating checksums.
  * [go-eco](https://code.google.com/p/go-eco/) - Functions for use in ecology
  * [go-erx](https://github.com/StepLg/go-erx) - Extended error reporting library
  * [go-eventsocket](https://github.com/fiorix/go-eventsocket) - An event socket client/server library for the [FreeSWITCH](https://freeswitch.org) telephony platform.
  * [GoFakeIt](http://godoc.org/github.com/brianvoe/gofakeit) - Fake Data Generator. 65+ different variations and examples for each
  * [go-fann](https://github.com/white-pony/go-fann) - Go bindings for FANN, library for artificial neural networks
  * [GoFlow](https://github.com/trustmaster/goflow) - Flow-based and dataflow programming library for Go
  * [goga](https://github.com/rrs/goga) - A genetic algorithm framework
  * [gogobject](https://github.com/nsf/gogobject) - GObject-introspection based bindings generator
  * [go-idn](http://code.google.com/p/go-idn/) - a project to bring IDN support to Go, feature compatible with libidn
  * [GoLCS](https://github.com/makokaka/goalgo/tree/master/algo) - Solve Longest Common Sequence problem in go
  * [golibs/as](https://github.com/SimonWaldherr/golibs/tree/master/as) - Converting data types
  * [golife](https://github.com/r2p2/golife) - Implementation of Game of Life for command line
  * [go-magic](https://code.google.com/p/go-magic/) - A Go wrapper for libmagic
  * [go-magic](https://github.com/kwilczynski/go-magic) - Simple interface to libmagic for Go Programming Language
  * [go-metrics](https://github.com/rcrowley/go-metrics) - Go port of Coda Hale's Metrics library
  * [gommap](https://launchpad.net/gommap) - gommap enables Go programs to directly work with memory mapped files and devices in a very efficient way
  * [gomusicbrainz](https://github.com/michiwend/gomusicbrainz) - MusicBrainz WS2 client library
  * [goneuro](https://github.com/jbrukh/goneuro) - Go driver for NeuroSky devices.
  * [goNI488](https://github.com/jpoirier/goNI488) - A Go wrapper around National Instruments NI488.2 General Purpose Interface Bus (GPIB) driver.
  * [go-osx-plist](https://github.com/kballard/go-osx-plist) - CoreFoundation Property List support for Go
  * [go-papi](https://github.com/lanl/go-papi) - Go interface to the PAPI performance API
  * [go.pcsclite](https://github.com/ebfe/go.pcsclite) - Go wrapper for pcsc-lite
  * [Go-PhysicsFS](https://github.com/DeedleFake/Go-PhysicsFS) - Go bindings for the PhysicsFS archive-access abstraction library.
  * [go.pipeline](https://github.com/songgao/go.pipeline) - Library that emulates Unix pipelines
  * [go-pkg-mpd](https://github.com/jteeuwen/go-pkg-mpd) - A library to access the MPD music daemon
  * [go-pkg-xmlx](https://github.com/jteeuwen/go-pkg-xmlx) - Extension to the standard Go XML package. Maintains a node tree that allows forward/backwards browser and exposes some simpel single/multi-node search functions
  * [goplan9](http://code.google.com/p/goplan9/) - libraries for interacting with Plan 9
  * [goPromise](https://github.com/anschelsc/goPromise/) - Scheme-like delayed evaluation for Go
  * [go-qrand](https://github.com/salviati/go-qrand) - Go client for quantum random bit generator service at random.irb.hr
  * [goraphing](http://code.google.com/p/goraphing/) - A tool to generate a simple graph data structures from JSON data files
  * [go-selenium](https://github.com/sourcegraph/go-selenium) - Selenium WebDriver client for Go
  * [go-semvar](http://code.google.com/p/go-semver/) - Semantic versions (see http:/semver.org)
  * [go-serial](https://github.com/mikepb/go-serial) - Go binding to libserialport for serial port functionality (cgo).
  * [goST](https://bitbucket.org/pseudomind/gost) - A steam properties (steam table) library written for Go. This was designed as a native go equivalent to XSteam.
  * [go-taskstats](https://github.com/salviati/go-taskstats) - Go interface for Linux taskstats
  * [gotenv](https://github.com/subosito/gotenv) - Loads environment variables from ` .env ` file
  * [Gotgo](https://github.com/droundy/gotgo) - A Go preprocessor that provides an implementation of generics
  * [go-translate](https://github.com/mattn/go-translate) - Google Language Translate library
  * [go-uuid](https://code.google.com/p/go-uuid/) - Universal Unique IDentifier generator and parser
  * [gouuid](https://github.com/nu7hatch/gouuid) - Pure Go UUID v3, 4 and 5 generator compatible with RFC4122
  * [go-villa](https://github.com/daviddengcn/go-villa) - Some miscellaneous wrapper and small algorithms.(wrappers to slices, priority queues, path related apis, a string set type)
  * [Hranoprovod](https://github.com/aquilax/hranoprovod-go) - Command-line calorie tracking
  * [lineup](https://github.com/jdp/lineup) - A minimalistic message queue server
  * [mitigation](https://github.com/sarnowski/mitigation) - Package mitigation provides the possibility to prevent damage caused by bugs or exploits.
  * [nma.go](https://github.com/dustin/nma.go) - A NotifyMyAndroid client for go.
  * [notify](https://github.com/rjeczalik/notify) - File system event notification library with API similar to os/signal.
  * [pargo](https://github.com/ExaScience/pargo) - A library for parallel programming in Go.
  * [passwd](https://github.com/willdonnelly/passwd) - A parser for the /etc/passwd file
  * [pool](https://github.com/stefantalpalaru/pool) - A generic worker pool
  * [procfile](https://github.com/hecticjeff/procfile) - A Procfile parser
  * [Prometheus Instrumentation/Metrics Client](https://github.com/prometheus/client_golang) - This is a whitebox instrumentation framework for servers written in Go.  It exposes programmatically-generated metrics automatically for use in the Prometheus time series collection and post-processing environment.
  * [randat](https://github.com/extemporalgenome/randat) - Devel tool for generating random bytestrings and encoding files in code-friendly forms
  * [recycler](https://github.com/timtadh/recycler) - A more flexible object recycling system than sync.Pool. Provides constructors and destructors for the objects as well as control over the length the free.
  * [replaykit](https://github.com/dustin/replaykit) - A library for replaying time series data.
  * [serial](https://github.com/ziutek/serial) - Serial ports API (pure Go)
  * [sio](https://github.com/schleibinger/sio) - Package sio lets you access old serial junk. It's a go-gettable fork and modification of dustin's rs232 package.
  * [stats](https://github.com/go-playground/stats) - Monitors Go MemStats + System stats such as Memory, Swap and CPU and sends via UDP anywhere you want for logging etc...
  * [symutils](https://github.com/salviati/symutils) - Various tools and libraries to handle symbolic links
  * [toktok](https://github.com/muesli/toktok) - Creates and resolves unique, typo & error-resilient, human-readable tokens
  * [twitterfetcher](https://bitbucket.org/georgebaev/twitterfetcher) - A tool to make Twitter API requests using the [Application-only authentication](https://dev.twitter.com/docs/auth/application-only-auth)
  * [udis86](https://github.com/jroimartin/udis86) - Go bindings for libudis86
  * [ugo](https://github.com/alxrm/ugo) - underscore.js like toolbox for Go
  * [Vboxgo](https://github.com/th4t/vboxgo) - user-like access to VirtualBox VMs from Go.
  * [Wukong](https://github.com/huichen/wukong) - A highly extensible full-text search engine written in Go.
  * [xplor](http://bitbucket.org/mpl/xplor) - Files tree browser for p9p acme
  * [yubigo](https://github.com/GeertJohan/yubigo) - Yubikey OTP validation and auhtentication API client.

## Music

  * [gmask](https://github.com/fggp/gmask) - Go adaptation of the Cmask utility for Csound
  * [go-csnd6](https://github.com/fggp/go-csnd6) - Go binding to the Csound6 API
  * [go-csperfthread](https://github.com/fggp/go-csperfthread) - Go binding to the CsoundPerformanceThread helper class of the Csound6 API
  * [go-libshout](https://github.com/systemfreund/go-libshout) - Go bindings for libshout
  * [gompd](http://code.google.com/p/gompd/) - A client interface for the MPD (Music Player Daemon)
  * [launchpad](https://github.com/rakyll/launchpad) - A Go client for Novation Launchpad
  * [portmidi](https://github.com/rakyll/portmidi) - Go bindings for libportmidi

## Networking

### DNS
  * [bitz](https://github.com/nictuku/bitz) - BitMessage client node and library
  * [dingo](https://github.com/pforemski/dingo) - A DNS client in Go that supports Google DNS over HTTPS
  * [dns](https://github.com/miekg/dns) - A DNS library in Go
  * [dnsimple](https://github.com/pearkes/dnsimple) - an interface to the DNSimple API
  * [dyndnscd](https://github.com/akrennmair/dyndnscd) - a configurable dyndns client
  * [GeoDNS](https://github.com/abh/geodns) - geo-aware authoritative DNS server
  * [grong](https://github.com/bortzmeyer/grong) - Small authoritative DNS name server
  * [mdns](https://github.com/davecheney/mdns/) - Multicast DNS library for Go
  * [hostsfile](https://github.com/jaytaylor/go-hostsfile) - /etc/hostsfile reverse lookup IP => names
  * [dnss](https://github.com/albertito/dnss) - DNS secure proxy, supports DNS over HTTPS and GRPC
  * [domainerator](https://github.com/hgfischer/domainerator) - Command line tool to combine wordlist and suffixes/TLDs into domain names and check if they are registered or not.
  * [dns](https://github.com/benburkert/dns) - client and server implementations in Go

### FTP
  * [ftp4go](http://code.google.com/p/ftp4go/) - An FTP client for Go, started as a port of the standard Python FTP client library
  * [ftp](https://bitbucket.org/zombiezen/ftp/) - Package ftp provides a minimal FTP client as defined in RFC 959
  * [ftps](https://github.com/webguerilla/ftps) - An implementation of the FTPS protocol
  * [goftp](https://github.com/jlaffaye/) - A FTP client library

### HTTP
  * [apiproxy](https://sourcegraph.com/github.com/sourcegraph/apiproxy/tree) - proxy for HTTP/REST APIs with configurable cache timeouts
  * [boom](https://github.com/rakyll/boom) - HTTP(s) benchmarking tool, Apache Benchmark replacement
  * [eventsource](https://github.com/antage/eventsource) - Server-sent events for net/http server.
  * [fasthttp](https://github.com/valyala/fasthttp) - Fast HTTP package for Go
  * [gbench](https://github.com/sasanrose/gbench) - HTTP(s) Load Testing And Benchmarking Tool inspired by Apache Benchmark and Siege.
  * [gobench](https://github.com/cmpxchg16/gobench) - HTTP/HTTPS load test and benchmark tool
  * [go-curl](https://github.com/andelf/go-curl) - libcurl bingding that supports go func callbacks
  * [goproxy](https://github.com/elazarl/goproxy) - a programmable HTTP proxy.
  * [gostax](https://github.com/maxymania/gostax) - A Streaming API for XML (StAX) in go
  * [handlers](https://github.com/kevinburke/handlers) - Collection of useful HTTP middlewares.
  * [HTTPLab](https://github.com/gchaincl/httplab) - HTTPLabs let you inspect HTTP requests and forge responses.
  * [stress](https://github.com/wenjiax/stress) - Replacement of ApacheBench(ab), support for transactional requests, support for command line and package references to HTTP stress testing tool.
  * [sling](https://github.com/dghubble/sling) - A Go HTTP client library for creating and sending API requests.
  * [httptail](https://github.com/smallfish/httptail) - tools push stdout/stderr to http chunked

### IMAP
  * [go-imap](https://github.com/emersion/go-imap) - An IMAP library for clients and servers.
  * [go-imap](https://github.com/martine/go-imap) - IMAP client library
  * [go-imap](https://github.com/mxk/go-imap) - Implementation of IMAP4rev1 client, as described in RFC 3501

### Instant Messaging
  * [hanu](https://github.com/sbstjn/hanu) - Framework for writing Slack bots
  * [gobir](http://code.google.com/p/kylelemons/source/browse?repo=gobir) - Extensible IRC bot with channel administration, seen support, and go documentation querying
  * [goexmpp](http://code.google.com/p/goexmpp/) - XMPP client implementation
  * [goirc](https://github.com/fluffle/goirc/) - event-based stateful IRC client framework
  * [go-irc](https://github.com/husio/go-irc) - Simple IRC client library
  * [gorobot](https://github.com/aimxhaisse/gorobot) - a modular IRC bot
  * [go-xmpp](https://github.com/mattn/go-xmpp) - XMPP client library
  * [ircflu](https://github.com/muesli/ircflu) - IRC bot with support for commands, scripting and web-hooks
  * [irc.go](http://code.google.com/p/go-bot/source/browse/irc.go) - Go IRC bot framework
  * [sirius](https://github.com/ortuman/sirius) - [link is broken] A fast and ultra-lightweight chat server written in Go
  * [xmpp-client](https://github.com/agl/xmpp-client) - an XMPP client with OTR (off-the-record) support

### NNTP
  * [go-nntp](https://github.com/dustin/go-nntp) - An NNTP client and server library for go

### Protocol Buffers
  * [gogoprotobuf](http://code.google.com/p/gogoprotobuf/) - another Go implementation of Protocol Buffers, but with extensions and code generation plugins.
  * [golang\_protobuf\_extensions](https://github.com/matttproud/golang_protobuf_extensions) - Protocol Buffer extensions to support streaming message encoding and decoding.
  * [goprotobuf](http://code.google.com/p/goprotobuf/) - the Go implementation of Google's Protocol Buffers
  * [protorpc](https://github.com/chai2010/protorpc/) - Google Protocol Buffers RPC for Go and C++

### rsync
  * [replican-sync](https://github.com/cmars/replican-sync) - An rsync algorithm implementation in Go
  * [Rsync](https://github.com/julian-gutierrez-o/rsync) - Rsync algorithm as a Go library

### Telnet
  * [telnet](https://github.com/reiver/go-telnet) - Package telnet provides TELNET and TELNETS client and server implementations, for the Go programming language, in a style similar to the "net/http" library (that is part of the Go standard library) including support for "middleware"; TELNETS is secure TELNET, with the TELNET protocol over a secured TLS (or SSL) connection.
  * [telnet](https://github.com/ziutek/telnet) - A simple interface for interacting with Telnet connection
  * [telnets](https://github.com/reiver/telnets) - A client for the TELNETS (secure TELNET) protocol.

### VNC
  * [glibvnc](https://github.com/LukeMauldin/glibvnc) - Go wrapper using CGO for the libvnc library.

### Websockets
  * [Gorilla WebSocket](https://github.com/gorilla/websocket) - WebSocket protocol implementation
  * [websocketd](https://github.com/joewalnes/websocketd) - HTTP server that converts STDIN/STDOUT program into WebSockets service. Also handles HTML and CGI.
  * [wst](https://github.com/jthestupidkid/wst) - A dead simple WebSocket tester
  * [ws-cli](https://github.com/kseo/ws-cli) - WebSocket command line client

### ZeroMQ
  * [goczmq](https://github.com/zeromq/goczmq) - Wrapper for the CZMQv3 interface - [blog post](http://taotetek.github.io/oldschool.systems/post/goczmq1/)
  * [gozmq](https://github.com/alecthomas/gozmq) - Go Bindings for 0mq (zeromq/zmq)
  * [zmq2](https://github.com/pebbe/zmq2) - A Go interface to ZeroMQ (zmq, 0MQ) version 2.
  * [zmq3](https://github.com/pebbe/zmq3) - A Go interface to ZeroMQ (zmq, 0MQ) version 3.
  * [zmq4](https://github.com/pebbe/zmq4) - A Go interface to ZeroMQ (zmq, 0MQ) version 4.

### Misc Networking
  * [betwixt](https://github.com/zubairhamed/betwixt) - Betwixt implements the OMA Lightweight M2M (LWM2M) protocol for Device Management and Monitoring
  * [canopus](https://github.com/zubairhamed/canopus) - CoAP Client/Server implementation (RFC 7252)
  * [chunkedreader](https://github.com/knadh/chunkedreader) - A light weight library for reading continuous fixed sized messages from TCP streams.
  * [circle](https://github.com/lanl/circle/) - Go interface to the [libcircle](http://hpc.github.io/libcircle/) distributed-queue API
  * [createsend-go](https://sourcegraph.com/github.com/sourcegraph/createsend-go/tree) - API client for [Monitor http://www.campaignmonitor.com](wiki/Campaign) (email campaign service)
  * [dmrgo](https://github.com/dgryski/dmrgo) - Library for with Hadoop Streaming map/reduce
  * [doozerconfig](https://github.com/srid/doozerconfig) - Go package for managing json-encoded configuration in Doozer
  * [doozerd](https://github.com/ha/doozerd) - A consistent distributed data store
  * [endless](https://github.com/fvbock/endless) Zero downtime restarts for go servers (Drop in replacement for http.ListenAndServe/TLS)
  * [gearman-go](https://bitbucket.org/mikespook/gearman-go) - A native implementation for Gearman API with Go.
  * [Glue](https://github.com/desertbit/glue) - Robust Go and Javascript Socket Library (Alternative to Socket.io)
  * [goagain](https://github.com/rcrowley/goagain) - zero-downtime restarts in Go
  * [Go Ajax](https://github.com/jeffreybolle/goajax) - Go Ajax is a JSON-RPC implementation designed to create AJAX powered websites.
  * [gobeanstalk](https://github.com/iwanbk/gobeanstalk) - Go Beanstalkd client library
  * [go-camo](https://github.com/cactus/go-camo) - Go http image proxy (camo clone) to route images through SSL
  * [go-dbus](https://github.com/norisatir/go-dbus) - A library to connect to the D-bus messaging system
  * [go-diameter](https://github.com/fiorix/go-diameter) - Diameter stack and Base Protocol (RFC 6733)
  * [go-smpp](https://github.com/fiorix/go-smpp) - SMPP 3.4 protocol implementation
  * [go-flowrate](https://github.com/mxk/go-flowrate) - Data transfer rate control (monitoring and limiting)
  * [gogammu](https://github.com/ziutek/gogammu) - Library for sending and receiving SMS
  * [go-icap](http://code.google.com/p/go-icap/) - ICAP (Internet Content Adaptation Protocol) server library
  * [gonetbench](https://github.com/nu7hatch/gonetbench) - Simple TCP benchmarking tool
  * [gonetcheck](https://github.com/bjdean/gonetcheck) - package for checking general internet access
  * [goodhosts](https://github.com/lextoumbourou/goodhosts) - Simple hosts file (/etc/hosts) management in Go
  * [gopacket](http://code.google.com/p/gopacket) - Packet encoding/decoding, pcap/pfring/afpacket support, TCP assembly, and more!
  * [gopcap](https://github.com/akrennmair/gopcap) - A simple wrapper around libpcap
  * [goq](https://github.com/anandkunal/goq) - A persistent message queue written in Go.
  * [goradius](https://github.com/kirves/goradius) - A Radius client written in Go
  * [go-rpcgen](https://github.com/kylelemons/go-rpcgen) - ProtoBuf RPC binding generator for net/rpc and AppEngine
  * [gorpc](https://github.com/valyala/gorpc) - RPC optimized for high load
  * [GoRTP](https://github.com/wernerd/GoRTP) - RTP / RTCP stack implementation for Go
  * [GoSIPs](https://github.com/rainliu/gosips) - SIP (Session Initiation Protocol) Stack in Go
  * [mqtt](https://github.com/rainliu/mqtt) - MQTT stack in Go
  * [gosndfile](https://github.com/mkb218/gosndfile) - Go binding for libsndfile
  * [gosnmp](https://github.com/soniah/gosnmp) - an SNMP library written in GoLang.
  * [go-socket.io](https://github.com/madari/go-socket.io) - A Socket.IO backend implementation written in Go
  * [gosocks](https://github.com/hailiang/gosocks) - A SOCKS (SOCKS4, SOCKS4A and SOCKS5) proxy client library in Go.
  * [go-sslterminator](https://github.com/cmpxchg16/go-sslterminator) - SSL terminator proxy
  * [go-statsd-client](https://github.com/cactus/go-statsd-client) - Go statsd client library
  * [Gollum](https://github.com/trivago/gollum) - A n:m multiplexer that gathers messages from different sources and broadcasts them to a set of destinations.
  * [Grumble](https://github.com/mkrautz/grumble) - Mumble (VoIP) server implementation
  * [handlersocket-go](https://github.com/bketelsen/handlersocket-go) - Go native library to connect to HandlerSocket interface of InnoDB tables
  * [HomeControl](https://github.com/brutella/hc) - an implementation of Apple's HomeKit Accessory Protocol (HAP)
  * [Hprose](https://github.com/hprose/hprose-go) - Hprose is a High Performance Remote Object Service Engine.
  * [httpfstream](https://github.com/sourcegraph/httpfstream) - streaming append and follow of HTTP resources (using WebSockets)
  * [ipaddress](https://github.com/llimllib/ipaddress) - Convenient ip address functions: ip -> int, int -> ip, and IPNet broadcast address
  * [iris-go](https://github.com/karalabe/iris-go) - Go binding for the Iris decentralized messaging framework.
  * [iris](http://iris.karalabe.com) - Peer-to-peer messaging for back-end decentralization.
  * [kafka.go](https://github.com/jdamick/kafka.go) - Producer & Consumer for the Kafka messaging system
  * [lcvpn](https://github.com/kanocz/lcvpn) - Decentralized VPN implementation
  * [ldap](https://github.com/mmitton/ldap) - Basic LDAP v3 functionality for the GO programming language.
  * [mbxchan](https://bitbucket.org/levarnon/mbx) - An easy communication between distributed Go applications using standard Go channels and remote procedure calls.
  * [nagiosplugin](https://github.com/fractalcat/nagiosplugin) - package for writing Nagios/monitoring plugins
  * [NATS](https://github.com/apcera/nats) - NATS distributed messaging system client for Go
  * [netsnail](https://github.com/purex01/netsnail) - A low-bandwidth simulator
  * [netutils](https://github.com/timtadh/netutils) - Simple interface for turning TCP Sockets into channels.
  * [npipe](https://github.com/natefinch/npipe) - a pure Go wrapper for Windows named pipes
  * [norm](https://github.com/aletheia7/norm) - reliable UDP using multicast and unicast sockets
  * [opendap](https://github.com/mqu/openldap) - Go wrapper for Openldap
  * [pusher-http-go](https://github.com/pusher/pusher-http-go) - Go library for interacting with the Pusher Realtime API
  * [QRP](https://github.com/liamzebedee/go-qrp) - QRP is a simple packet-based RPC protocol designed as a simple alternative to Go's rpc, that can run over UDP
  * [remotize](https://github.com/josvazg/remotize) - A remotize package and command that helps remotizing methods without having to chaneg their signatures for rpc
  * [Resgate](https://github.com/jirenius/resgate) - A Realtime + REST API Gateway for NATS to create web APIs with live data
  * [rs232](https://github.com/dustin/rs232.go) - Serial interface for those of us who still have modems (or arduinos)
  * [rss](https://github.com/SlyMarbo/rss) - RSS parsing library.
  * [seamless](https://bitbucket.org/tebeka/seamless) - Reverse TCP Proxy with HTTP management API
  * [shell2http](https://github.com/msoap/shell2http) - Executing shell commands via simple http server
  * [sockjs-go](https://github.com/fzzy/sockjs-go) - Implements server side counterpart for the SockJS-client browser library.
  * [SOCKS5 Server](https://code.google.com/p/go-socks5) - Scalable SOCKS5 server with Access Control Lists
  * [spark](https://github.com/rif/spark) - Emergency web server (for static files)
  * [spdy](https://github.com/SlyMarbo/spdy) - SPDY library, wired into net/http, currently supporting servers only.
  * [statsd-go](https://github.com/jbuchbinder/statsd-go) - Statsd implementation in Go, forked from gographite, which submits to Ganglia
  * [stompngo\_examples](https://github.com/gmallard/stompngo_examples) - Examples for stompngo.
  * [stompngo](https://github.com/gmallard/stompngo) - A Stomp 1.1 Compliant Client
  * [tcp\_fallback](https://github.com/Memset/tcp_fallback) - A TCP proxy implementing a simple fallback mechanism.
  * [tcpmeter](https://github.com/9nut/tcpmeter) - A TCP throughput measuring tool
  * [toxiproxy](https://github.com/shopify/toxiproxy) - Framework for simulating network conditions.
  * [traceroute](https://github.com/aeden/traceroute) - A traceroute implementation
  * [traefik](https://github.com/emilevauge/traefik) - Modern, reverse proxy in Go
  * [Uniqush](http://uniqush.org/) - A free and open source software which provides a unified push service for server-side notification to apps on mobile devices.
  * [uritemplates](https://github.com/jtacoma/uritemplates) - A level 4 implementation of URI Templates (RFC 6570)
  * [VDED](https://github.com/jbuchbinder/vded) - Vector Delta Engine Daemon - track deltas in ever-increasing values (written in Go)
  * [zero-downtime-daemon](https://bitbucket.org/PinIdea/zero-downtime-daemon) - Configurable zero downtime daemon (Hot Update) framework for any kind of TCP,HTTP,FCGI services
  * [zeroupgrade](https://github.com/thcyron/zeroupgrade) - Upgrades network servers with zero downtime
  * [cwmp-proxy](https://github.com/FeNoMeNa/cwmp-proxy) - Reverse cwmp proxy
  * [netstat-nat](https://github.com/dominikh/netstat-nat) - Display NAT entries on Linux systems
  * [go-nat-pmp](http://code.google.com/p/go-nat-pmp/) - A client for the NAT-PMP protocol used in Apple and open-source routers
  * [humanize-bytes](https://github.com/tv42/humanize-bytes) - Command-line utilities to convert "MiB" etc to raw numbers, and back

## Operating System Interfaces

  * [Go FUSE file system library](http://bazil.org/fuse/) - From-scratch implementation of the kernel-userspace communication protocol based on Russ Cox'.
  * [Go-fuse](https://github.com/hanwen/go-fuse) - Library to write FUSE filesystems in Go
  * [go-osx-xattr](https://github.com/bitcartel/go-osx-xattr) - Package xattr wraps OS X functions to manipulate the extended attributes of a file, directory and symbolic link.
  * [inspect/os](https://github.com/square/inspect) - Metrics library for operating system measurements (Linux/MacOSX)
  * [service](https://github.com/kardianos/service) - Service will install / un-install, start / stop, and run a program as a service (daemon) on Windows/Linux and OSX.
  * [go-nbd](https://github.com/akmistry/go-nbd) - Library to write block devices for Linux in Go.

## Other Random Toys, Experiments and Example Code

  * [goconc](http://code.google.com/p/goconc/) - A collection of useful concurrency idioms and functions for Go, compiled
  * [go-crazy](https://github.com/droundy/go-crazy) - An experimental source-to-source compiler for go
  * [go-gtk-demo](https://github.com/pebbe/go-gtk-demo) - A demonstration of how to use GTK+ with Go.
  * [go-hashmap](https://github.com/phf/go-hashmap) - A hash table in pure go as an experiment in Go performance
  * [golang-examples](https://github.com/SimonWaldherr/golang-examples) - A bunch of golang examples
  * [GolangSortingVisualization](https://github.com/SimonWaldherr/GolangSortingVisualization) - A visualization of various sorting algorithms in Go
  * [golibs](https://github.com/SimonWaldherr/golibs) - A collection of tiny go packages (and also a test repo for various CI and coverage services)
  * [goplay](https://github.com/timtadh/goplay) - A bunch of random small programs in Go
  * [lifegame-on-golang](https://github.com/horiuchi/lifegame-on-golang) - Game of Life in Go
  * [linear](https://github.com/tychofreeman/Linear) - Playing around with the linear algebra
  * [pl0](http://github.com/cznic/pl0) - PL/0 front end, compiler and VM. .
  * [project euler in go](https://github.com/yyyc514/project_euler_in_go) - Solutions to Project Euler in Go also
  * [shadergo](https://github.com/gyuque/shadergo) - shader test using Go
  * [travisci-golang-example](https://github.com/atotto/travisci-golang-example) - Travis-CI example for Go

## P2P and File Sharing

  * [DHT](https://github.com/nictuku/dht) - Kademlia DHT node used by Taipei-Torrent, compatible with BitTorrent
  * [ed2kcrawler](https://github.com/kevinwatt/ed2kcrawler) - eDonkey2000 link crawler
  * [gop2p](https://github.com/nacmartin/gop2p) - A simple p2p app to learn Go
  * [go-p2p](https://github.com/tendermint/go-p2p/) - P2P module for blockchains and more
  * [GoTella](https://github.com/sourabhdesai/gotella/) - A Go implementation of the Gnutella Protocol
  * [Taipei-Torrent](https://github.com/jackpal/Taipei-Torrent) - A BitTorrent client
  * [Tendermint](https://github.com/tendermint/tendermint) - P2P Byzantine-Fault-Tolerant consensus & blockchain stack
  * [wgo](https://github.com/royger/wgo) - A simple BitTorrent client based in part on the Taipei-Torrent and gobit code
  * [DHT](https://github.com/shiyanhui/dht) - BitTorrent DHT Protocol && DHT Spider.

## Programming

  * [go-clang](http://github.com/go-clang) - cgo bindings to the C-API of libclang
  * [godeferred](https://github.com/mattn/godeferred) - port of jsdeferred: http://cho45.stfuawsc.com/jsdeferred/
  * [go-galib](https://github.com/thoj/go-galib) - a library of Genetic Algorithms
  * [go-intset](https://github.com/phf/go-intset) - a library to work with bounded sets of integers, including multiple alternative implementations
  * [go-parse](https://github.com/vito/go-parse) - a Parsec-like parsing library
  * [sh](https://github.com/mvdan/sh) - a shell/bash parser and formatter
  * [Shuffle](https://github.com/earthboundkid/shuffle) - Implementation of the Fisher–Yates shuffle (or Knuth shuffle) in Go.

## Resource Embedding
  * [fileb0x](https://github.com/UnnoTed/fileb0x) - Simple tool to embed files in go with focus on "customization" and ease to use.
  * [go-bindata](https://github.com/jteeuwen/go-bindata) - Package that converts any file into managable Go source code.
  * [go-resources](https://github.com/omeid/go-resources) - Unfancy resources embedding with Go.
  * [go.rice](https://github.com/GeertJohan/go.rice) - go.rice is a Go package that makes working with resources such as html,js,css,images and templates very easy.
  * [implant](https://github.com/skx/implant/) - implant allows embedding static resources, from a series of directories (recursively).
  * [statics](https://github.com/go-playground/statics) - Embeds static resources into go files for single binary compilation + works with http.FileSystem + symlinks.

## RPC

  * [gowsdl](https://github.com/hooklift/gowsdl) - WSDL code generation
  * [gRPC](https://grpc.io) - Google's multi-language RPC framework with Go support

## Scanner and Parser Generators

  * [ebnf2y](http://github.com/cznic/ebnf2y) - Utility for converting EBNF grammars into yacc compatible skeleton .y files.
  * [gocc](http://code.google.com/p/gocc/) - Go Compiler Compiler
  * [golex](http://github.com/cznic/golex) - Lex/flex like fast (DFA) scanners generator.
  * [gopp](http://github.com/skelterjohn/gopp) - Go Parser Parser
  * [goyacc](http://github.com/cznic/goyacc) - Goyacc is a version of yacc generating Go parsers.
  * [y](http://github.com/cznic/y) - Package y converts .y (yacc) source files to data suitable for a parser generator.
  * [yy](http://github.com/cznic/yy) - yacc to yacc compiler.
  * [flexgo](https://github.com/pebbe/flexgo) - A version of flex that can produce Go code.
  * [fsm](http://github.com/cznic/fsm) - FSM (NFA, DFA) utilities.
  * [Ragel](http://www.complang.org/ragel/) - State Machine Compiler
  * [lexmachine](https://github.com/timtadh/lexmachine) - Lexical Analysis Framework for Golang

## Security

  * [acme](https://github.com/hlandau/acme) - ACME certificate acquisition tool
  * [acra](https://github.com/cossacklabs/acra) - SQL database protection suite: strong selective encryption, SQL injections prevention, intrusion detection system
  * [casbin](https://github.com/hsluoyz/casbin) - An authorization library that supports access control models like MAC, RBAC, ABAC
  * [docker-slim](https://github.com/docker-slim/docker-slim) - Container security and optimization
  * [gryffin](https://github.com/yahoo/gryffin) - A large scale security scanner by Yahoo!
  * [hyperfox](https://github.com/xiam/hyperfox) - a security tool for proxying and recording HTTP and HTTPs communications on a LAN
  * [lego](https://github.com/xenolf/lego) - Let's Encrypt client and ACME library
  * [webseclab](https://github.com/yahoo/webseclab) - a sample set of web security test cases and a toolkit to construct new ones

## Simulation Modeling

  * [godes](https://github.com/agoussia/godes) - Library for building discrete event simulation models

## Sorting

  * [funnelsort](https://github.com/eikeon/funnelsort) - Lazy funnel sort -- a cache-oblivious sorting algorithm
  * [Sortutil](http://patrickmylund.com/projects/sortutil/) - Nested, case-insensitive, and reverse sorting for Go.
  * [sortutil](https://github.com/cznic/sortutil) - Utilities supplemental to the Go standard "sort" package
  * [tarjan](http://github.com/looplab/tarjan) - Graph loop detection function based on Tarjan's algorithm
  * [timsort](https://github.com/psilva261/timsort) - Fast, stable sort, uses external comparator or sort.Interface

## Source Code Management

  * [Gitfile](https://github.com/bradurani/Gitfile) - A lightweight package manager for installing git repos
  * [go-deps](https://github.com/sourcegraph/go-deps) - Analyzes and recursively installs Go package deps (library functionality similar to ` go get `)
  * [go-diff](https://github.com/daviddengcn/go-diff) - A diff command for go languange showing semantic differences of two go source files.
  * [gogitver](https://github.com/aletheia7/gogitver) - Embeds a git tag (version string) into your application
  * [go-many-git](https://github.com/abrochard/go-many-git) - Manage and run commands across multiple git repositories
  * [go-pkgs](https://github.com/sourcegraph/go-pkgs) - Finds all matching packages in all of the GOPATH trees (library functionality similar to ` go list all `)
  * [go-vcs](https://github.com/sourcegraph/go-vcs) - clone and check out revs of VCS repositories (git and hg support)
  * [go-vcsurl](https://github.com/sourcegraph/go-vcsurl) - Lenient VCS repository URL parsing library
  * [hggofmt](http://bitbucket.org/ede/hggofmt/) - A Mercurial/hg extension with a hook to
  * [nut](https://github.com/AlekSi/nut) - Nut is a tool to manage versioned Go source code packages, called "nuts".
  * [vcstool](https://github.com/wjwwood/vcstool) - VCS abstraction tool

## Storage

  * [Minio](https://minio.io/) - Object Storage compatible with Amazon S3 API
  * [libStorage](https://github.com/emccode/libstorage) - an open source, platform agnostic, storage provisioning and orchestration framework, model, and API
  * [OpenEBS](https://openebs.io) - Containerized, Open source block storage for your containers,integrated tightly into K8S and other environments and based on distributed block storage and containerization of storage control

## Strings and Text

  * [allot](https://github.com/sbstjn/allot) - Placeholder and wildcard text parsing for CLI tools and bots
  * [awk](https://github.com/spakin/awk) - Easy AWK-style text processing in Go
  * [binarydist](https://github.com/kr/binarydist/) - Binary diff and patch
  * [Black Friday](https://github.com/russross/blackfriday) - A markdown processor
  * [codename-generator](https://github.com/jgautheron/codename-generator) - A codename generator meant for naming software releases
  * [columnize](https://code.google.com/p/go-columnize/) - format slice or array into aligned columns
  * [csvplus](https://github.com/maxim2266/csvplus) - Extends the standard Go [encoding/csv](https://golang.org/pkg/encoding/csv/) package with fluent interface, lazy stream operations, indices and joins.
  * [csvutil](https://github.com/bmatsuo/csvutil) - A heavy duty CSV reading and writing library.
  * [dgohash](https://github.com/dgryski/dgohash) - Collection of string hashing functions, including Murmur3 and others
  * [douceur](https://github.com/aymerick/douceur) - A simple CSS parser and inliner in Go.
  * [dsv](https://github.com/shuLhan/dsv) - A library for working with delimited separated value (DSV).
  * [flux](https://github.com/alexanderbartels/flux) - Fluent Regular Expressions in golang
  * [genex](https://github.com/alixaxel/genex) - Expansion of Regular Expressions
  * [gettext-go](https://github.com/chai2010/gettext-go/) - GNU's gettext support, written in pure Go
  * [gettext](https://github.com/gosexy/gettext) - Golang bindings for gettext; Feature complete, cgo
  * [go-colortext](https://github.com/daviddengcn/go-colortext) - Change the color of the text and background in the console, working both in Windows and other systems.
  * [go-guess](https://github.com/salviati/go-guess) - Go wrapper for libguess
  * [goagrep](https://github.com/schollz/goagrep) - fast fuzzy string matching using precomputation
  * [goini](https://github.com/glacjay/goini) - A go library to parse INI files
  * [golorem](https://github.com/drhodes/golorem) - lorem ipsum generator
  * [go-migemo](https://github.com/mattn/go-migemo) - migemo extension for go (Japanese incremental text search)
  * [go-ngram](https://github.com/Lazin/go-ngram) N-gram index for Go
  * [goregen](https://github.com/zach-klippenstein/goregen) - A Go library for generating random strings from regular expressions.
  * [goskirt](https://github.com/madari/goskirt) - Upskirt markdown library bindings for Go
  * [gosphinx](https://github.com/kpumuk/gosphinx) - A Go client interface to the Sphinx standalone full-text search engine
  * [govalidator](https://github.com/asaskevich/govalidator) - Package of string validators and sanitizers
  * [gpKMP](https://github.com/paddie/goKMP) - String-matching in Go using the Knuth–Morris–Pratt algorithm
  * [hangul](https://github.com/suapapa/go_hangul) - Handy tools to manipulate Korean character
  * [html2text](https://github.com/jaytaylor/html2text) - Golang HTML to text conversion library
  * [intern](https://github.com/spakin/intern) - Map strings to symbols for constant-time comparisons
  * [kasia.go](https://github.com/ziutek/kasia.go) - Templating system for HTML and other text documents
  * [kview](https://github.com/ziutek/kview) - Simple wrapper for kasia.go templates. It helps to modularize content of a website
  * [liquid](https://github.com/osteele/liquid) - A complete implementation of Shopify Liquid templates
  * [logparse](https://github.com/xojoc/logparse) - Parser for most common log formats
  * [NTemplate](https://github.com/yohcop/ntemplate.go) - Nested Templates
  * [parse](https://github.com/rymis/parse) - PEG parser that uses reflection to define grammar
  * [peg](https://github.com/badgerodon/peg) - Parsing Expression Grammer Parser
  * [pigeon](https://github.com/mna/pigeon) - Parsing Expression Grammar (PEG) Parser generator for Go
  * [plural](https://github.com/rickb777/plural) - No-fuss plurals for formatting both countable and continuous ranges of values.
  * [polyglot](https://github.com/lxn/polyglot) - String translation utilities for Go
  * [pretty.go](https://github.com/kr/pretty.go) - Pretty-printing for go values
  * [raymond](https://github.com/aymerick/raymond) - A complete handlebars implementation in Go.
  * [rubex](https://github.com/moovweb/rubex) - A simple regular expression library that supports Ruby's regex syntax. It is faster than Regexp.
  * [sanitize](https://github.com/kennygrant/sanitize) - Package sanitize provides functions for sanitizing html and text.
  * [scanner](http://code.google.com/p/golang/source/browse/src/pkg/scanner) - A text scanner that parses primitive types, analogous to Java's
  * [segment](https://github.com/llimllib/segment) - An implementation of Norvig's recursive word segmentation algorithm
  * [sprig](https://github.com/Masterminds/sprig) - Template functions for Go templates.
  * [strftime](https://bitbucket.org/tebeka/strftime) - strftime implementation
  * [strit](https://github.com/maxim2266/strit) - Package strit introduces a new type of string iterator, as well as a number of iterator constructors, wrappers and combinators.
  * [strogonoff](https://github.com/jbochi/strogonoff) - Stenography with Go
  * [strutil](https://github.com/cznic/strutil) - Package strutil collects utils supplemental to the standard strings package.
  * [text](https://github.com/kr/text) - Text paragraph wrapping and formatting
  * [Tideland golib](https://github.com/tideland/golib) - Stringex package for statistcal analysis
  * [useragent](https://github.com/xojoc/useragent) - User agent string parser
  * [xurls](https://github.com/mvdan/xurls) - Extract urls from text

## Testing

  * [assert](https://github.com/go-playground/assert) - Basic Assertion Library used along side native go testing, with building blocks for custom assertions
  * [assert](https://github.com/chai2010/assert) - Assert for go test.
  * [assert](https://github.com/golangplus/testing/tree/master/assert) - Handy assert package.
  * [assert](https://github.com/seanpont/assert) - JUnit-like asserts with excellent error messages
  * [biff](https://github.com/fulldump/biff) - Bifurcation testing framework, BDD compatible.
  * [charlatan](https://github.com/percolate/charlatan) - Tool to generate fake interface implementations for tests.
  * [conex](https://github.com/omeid/conex) - Docker containers for integration tests
  * [counterfeiter](https://github.com/maxbrunsfeld/counterfeiter) - Tool for generating self-contained and type-safe mocks.
  * [downtest](https://github.com/jmcvetta/downtest) - Automatically run tests for all known downstream consumers of a Go package.
  * [ginkgo](https://github.com/onsi/ginkgo) - BDD Testing Framework for Go.
  * [go2xunit](https://bitbucket.org/tebeka/go2xunit) - Convert "go test -v" output to xunit XML output
  * [go-assert](http://github.com/daviddengcn/go-assert) - Testing utils for Go.
  * [goautotest](https://github.com/ryanslade/goautotest) - Automatically run unit tests when code changes are made
  * [goblin](https://github.com/franela/goblin) - Minimal and Beautiful Go testing framework
  * [Gocheck](http://labix.org/gocheck) - Rich test framework with suites, fixtures, assertions, good error reporting, etc
  * [GoConvey](http://goconvey.co) - Browser-based reporting, uses ` go test `, supports traditional Go tests, clean DSL
  * [gocov](https://github.com/axw/gocov) - Code coverage testing/analysis tool
  * [gomega](https://github.com/onsi/gomega) - Ginkgo's Preferred Matcher Library.
  * [gomock](http://code.google.com/p/gomock/) - a mocking framework for Go.
  * [GoSpec](https://github.com/orfjackal/gospec) - a BDD framework
  * [gospecify](https://github.com/stesla/gospecify) - another BDD framework
  * [go-stat](https://github.com/mreiferson/go-stat) - performant instrumentation/profiling for Go
  * [go-tap](https://github.com/Merovius/go-tap) - TAP (Test Anything Protocol) parser in Go
  * [gotest.tools](https://github.com/gotestyourself/gotest.tools) - a collection of packages for writing readable tests
  * [gotestsum](https://github.com/gotestyourself/gotestsum) - a test runner with customizable and colored output
  * [gounit](https://github.com/mdwhatcott/gounit) - xunit for Go
  * [GSpec](https://github.com/hailiang/gspec) - _Expressive, reliable, concurrent and extensible_ Go test framework that makes it productive to organize and verify the mind model of software.
  * [httpexpect](https://github.com/gavv/httpexpect) - Concise, declarative, and easy to use end-to-end HTTP and REST API testing
  * [Nitro](https://github.com/spf13/nitro) - A quick and simple profiler For Go
  * [mspec](https://github.com/eduncan911/mspec) - BDD framework that frees you to Stub and Spec your code first with natural BDD language.
  * [muxy](https://github.com/mefellows/muxy) - Simulating real-world distributed system failures.
  * [Pegomock](https://github.com/petergtz/pegomock) - a mocking framework based on [golang/mock](https://github.com/golang/mock), but uses a DSL closely related to [Mockito](http://site.mockito.org/mockito/docs/current/org/mockito/Mockito.html).
  * [terst](https://github.com/robertkrimen/terst) - A terse, easy-to-use testing library for Go
  * [test2doc](https://code.google.com/p/test2doc/) - Generate documentation for your go units from your unit tests.
  * [testfixtures](https://github.com/go-testfixtures/testfixtures) - Rails' like test fixtures for testing database driven apps.
  * [testflight](https://github.com/drewolson/testflight) - Painless http testing in Go
  * [Testify](https://github.com/stretchrcom/testify) - A set of packages that provide many tools for testifying that your code will behave as you intend.
  * [ut](https://github.com/philpearl/ut) - Awesome mocks without magic.

## Validation

  * [validator](https://github.com/go-playground/validator) - Go Struct and Field validation, including Cross Field, Cross Struct, Map, Slice and Array diving
  * [validation](https://github.com/kdar/validation) - Simple independent struct/key-value validation

## Version Control

  * [git (in go)](https://github.com/dskinner/git) - Minimal working git client in Go
  * [gogs](http://gogs.io/) - Self-hosting Git Server in Go
  * [semver](https://github.com/blang/semver) - Semantic Versioning (SemVer) library

## Virtual Machines and Languages

  * [agora](https://github.com/PuerkitoBio/agora) - A dynamically typed, garbage collected, embeddable programming language built with Go
  * [anko](https://github.com/mattn/anko) - Scriptable interpreter written in golang
  * [forego](https://github.com/unixdj/forego) - Forth virtual machine  
  * [Gelo](http://code.google.com/p/gelo/) - Extensible, embeddable interpreter
  * [GoAwk](https://github.com/benhoyt/goawk) - An implementation of awk in golang.
  * [GoBASIC](https://github.com/skx/gobasic) - An embeddable BASIC interpreter written in golang.
  * [GoEmPHP](https://github.com/mikespook/goemphp) - This package is built for Embedding PHP into Go
  * [Goja](https://github.com/dop251/goja) - ECMAScript 5.1(+) implementation written in Go (otto fork with byte code compiler)
  * [goenv](https://github.com/smyrman/goenv) - Create an isolated environment where you install Go packages, binaries, or even C libraries. Very similar to virtualenv for Python.
  * [GoForth](https://github.com/ArtemTitoulenko/GoForth) - A simple Forth parser
  * [golemon](https://github.com/nsf/golemon) - A port of the Lemon parser-generator
  * [golem](https://github.com/mjarmy/golem-lang) - A general purpose, interpreted scripting language.
  * [GoLightly](https://github.com/feyeleanor/GoLightly) - A flexible and lightweight virtual machine with runtime-configurable instruction set
  * [goll1e](https://github.com/realistschuckle/goll1e) - An LL(1) parser generator for the Go programming language.
  * [Golog](https://github.com/mndrix/golog) - Prolog interpreter in Go
  * [go-lua](https://github.com/Shopify/go-lua) - Shopify's lua interpreter
  * [golua](https://github.com/aarzilli/golua) - A fork of GoLua that works on current releases of Go
  * [gomruby](https://github.com/AlekSi/gomruby) - mruby (mini Ruby) bindings for Go
  * [gopher-lua](https://github.com/yuin/gopher-lua) - A Lua 5.1 VM and compiler written in Go
  * [go-php](https://github.com/deuill/go-php) - PHP bindings for Go
  * [go-python](https://github.com/sbinet/go-python) - go bindings for CPython C-API
  * [gotcl](http://code.google.com/p/gotcl/) - Tcl interpreter in Go
  * [go.vm](https://github.com/skx/go.vm) - Simple virtual machine which interprets bytecode.
  * [v8](https://github.com/augustoroman/v8) - V8 JavaScript engine bindings for Go (supports V8 builds at least up to 5.8.244)
  * [go-v8](https://github.com/lazytiger/go-v8) - V8 JavaScript engine bindings for Go
  * [LispEx](https://github.com/kedebug/LispEx) - A dialect of Lisp extended to support for concurrent programming, written in Go.
  * [meme](http://bitbucket.org/anacrolix/meme) - Scheme interpreter in Go
  * [Minima](https://github.com/opesun/minima) - A language implemented in Go
  * [ngaro](http://www.anarchyinthetubes.com/hg/go/ngaro) - A ngaro virtual machine to run retroForth images
  * [otto](https://github.com/robertkrimen/otto) - A JavaScript parser and interpreter written natively in Go
  * [RubyGoLightly](https://github.com/feyeleanor/RubyGoLightly) - An experimental port of TinyRb to Go

## Web Applications

  * [Presento](https://github.com/alxrm/presento) - The simplest possible cross-platform remote control for the presentations
  * [Caddy](https://caddyserver.com) - A fast, capable, general-purpose HTTP/2 web server that's easy to use
  * [Dataflowkit](https://github.com/slotix/dataflowkit) - Web scraping Service to turn websites into structured data.
  * [Digestw](https://github.com/mocchira/digestw) - A Web Application - Twitter's Timeline Digest
  * [fabio](https://github.com/eBay/fabio) - A fast zero-conf load balancing HTTP router for microservices.
  * [fourohfourfound](https://github.com/whee/fourohfourfound/) - A fallback HTTP server that may redirect requests with runtime configurable redirections
  * [Fragmenta](http://fragmenta.eu/) - A CMS built in Go
  * [freegeoip](https://github.com/fiorix/freegeoip) - IP geolocation web service (web server of freegeoip.net)
  * [goals-calendar](https://github.com/nono/goals-calendar) - A web-based Seinfeld calendar implemented in Go
  * [goblog](https://github.com/begoon/begoon.github.com) - A static blog engine
  * [gocrawl](https://github.com/PuerkitoBio/gocrawl) - A polite, slim and concurrent web crawler.
  * [goflash](https://sourceforge.net/p/goflash/home/Home/) - Flash player implementation in Go language
  * [gogallery](http://code.google.com/p/gogallery/) - simple web server with an emphasis on easily browsing images
  * [gojekyll](https://github.com/osteele/gojekyll) - A golang clone of the Jekyll static site generator
  * [goof](https://github.com/stone/goof) - A simple http server to exchange files over http (upload/download)
  * [gopages](http://code.google.com/p/gopages/) - A php-like web framework that allows embedding Go code in web pages
  * [go\_spider](https://github.com/hu17889/go_spider) - A flexible ,modularization and concurrent web crawler framework.
  * [GoURLShortener](https://github.com/NickPresta/GoURLShortener) - A frontend for the http://is.gd/ URL shortener
  * [gowall](https://github.com/im7mortal/gowall) - A website and user system
  * [httpfolder](https://github.com/biorisk/httpfolder) - A http server to exchange files over http with basic authentication (upload/download)
  * [Hugo](https://github.com/spf13/hugo) - A fast and flexible static site generator implemented in Go
  * [Já Vai Tarde](https://github.com/nictuku/javaitarde) - Unfollows monitoring for Twitter
  * [kurz.go](https://github.com/fs111/kurz.go) - a url shortener based on web.go and redis
  * [Monsti](https://github.com/chrneumann/monsti) - Resource friendly flat file CMS for private and small business sites.
  * [now.go](https://github.com/alloy-d/now.go) - A simple HTTP-based to-do queue.
  * [Peach](http://peachdocs.org/) - A web server for multi-language, real-time synced and searchable documentation.
  * [rabbitmq-http](https://github.com/smallfish/rabbitmq-http) - REST API for RabbitMQ
  * [serve-files](https://github.com/rickb777/servefiles) - Far-future and gzip wrapper around the standard net/http server.
  * [sf\_server](http://code.google.com/p/rflk/source/browse/#svn%2Ftrunk%2Fsw%2FGo%2Fsend_file_go) - a tiny send file server and client
  * [SuperSaaS API Client](https://github.com/SuperSaaS/supersaas-go-api-client) - HTTP client library for the supersaas.com scheduling/bookings/appointments API
  * [Tideland golib](https://github.com/tideland/golib) - Web package for REST request handling  
  * [Vantaa](https://github.com/nathandao/vantaa) - A modular blogging API engine written in Go, Neo4j and Polymer.
  * [websiteskeleton](https://github.com/jadekler/git-go-websiteskeleton) - Simple net/http website skeleton
  * [webtf](http://code.google.com/p/webtf/) - Web app to graphical visualization of twitter timelines using the HTML5
  * [Wikifeat](https://github.com/rhinoman/wikifeat) - Extensible wiki system using CouchDB written in Golang
  * [Freyr](https://github.com/serdmanczyk/Freyr) - Server for storing and serving readings from plant environment sensors.  Integrates Golang API with ReactJS web app; uses Docker for testing/deployment.
  * [Rickover](https://github.com/Shyp/rickover) - Job queue with a HTTP API, backed by Postgres

## Web Libraries

### Authentication
  * [goth](https://github.com/markbates/goth) - Package goth provides a simple, clean, and idiomatic way to write authentication packages for Go web applications
  * [authcookie](https://github.com/dchest/authcookie) - Package authcookie implements creation and verification of signed authentication cookies.
  * [dgoogauth](https://github.com/dgryski/dgoogauth) - Go port of Google's Authenticator library for one-time passwords
  * [goauth](https://github.com/alloy-d/goauth) - A library for header-based OAuth over HTTP or HTTPS.
  * [GOAuth](https://github.com/hokapoka/goauth) - OAuth Consumer
  * [go-http-auth](https://github.com/abbot/go-http-auth) - HTTP Basic and HTTP Digest authentication
  * [Go-OAuth](https://github.com/garyburd/go-oauth) - OAuth 1.0 client
  * [goha](https://github.com/FeNoMeNa/goha) - Basic and Digest HTTP Authentication for Go http client
  * [hero](https://github.com/gernest/hero) - OAuth server implementation - be an OAuth provider with Go
  * [httpauth-go](https://bitbucket.org/rj/httpauth-go) - Package httpauth provides utilities to support HTTP authentication policies. Support for both the basic authentication scheme and the digest authentication scheme are provided.
  * [httpauth](https://github.com/apexskier/httpauth) - HTTP session (cookie) based authentication and authorization
  * [oauth1a](https://github.com/kurrik/oauth1a) - OAuth 1.0 client library
  * [OAuth Consumer](https://github.com/mrjones/oauth) - OAuth 1.0 consumer implementation
  * [otp](http://tristanwietsma.github.io/otp/) - HOTP and TOTP library with command line replacement for Google Authenticator
  * [securecookie](https://github.com/chmike/securecookie) - Encode and Decode secure cookies
  * [totp](https://github.com/balasanjay/totp) - Time-Based One-Time Password Algorithm, specified in RFC 6238, works with Google Authenticator
  * [go-otp](https://github.com/hgfischer/go-otp) - Package go-otp implements one-time-password generators used in 2-factor authentication systems like RSA-tokens. Currently this supports both HOTP (RFC-4226), TOTP (RFC-6238) and Base32 encoding (RFC-3548) for Google Authenticator compatibility


### DOM handling

  * [Cascadia](http://code.google.com/p/cascadia) - CSS selector library
  * [GoQuery](https://github.com/PuerkitoBio/goquery) - jQuery-like DOM manipulation library, using Go's experimental HTML package.
  * [goq](https://github.com/andrewstuart/goq) - jQuery-like declarative struct tag scraping and unmarshaling based on GoQuery.
  * [html-query](https://github.com/hailiang/html-query) - A fluent and functional approach to querying HTML.
  * [HTML Transform](http://code.google.com/p/go-html-transform/) - A CSS selector based html scraping and transformation library

### Frameworks and Toolkits

  * [aah](https://aahframework.org) - A scalable, performant, rapid development Web framework for Go.
  * [Aero](https://github.com/aerogo/aero) - Fast and secure web server for Go.
  * [Air](https://github.com/sheng/air) - An ideal RESTful web framework for Go.
  * [alien](https://github.com/gernest/alien) - A lightweight and fast http router
  * [app.go](https://github.com/georgenava/appgo) - Web framework for google app engine
  * [arasu](https://github.com/arasuresearch/arasu) - A Lightning Fast Web Framework written in Go & Dart
  * [Beego](http://beego.me/) - Beego is an open source version of the scalable, non-blocking web framework.
  * [browserspeak](https://github.com/xyproto/browserspeak) - Generate HTML templates, CSS or SVG without writing `<` or `>`
  * [httpcoala](https://github.com/goware/httpcoala) - Library for request coalescing - handy for reverse proxies. 
  * [falcore](https://github.com/fitstar/falcore) - Modular HTTP server framework
  * [fcgi\_client](https://bitbucket.org/PinIdea/fcgi_client) - Go fastcgi client with fcgi params support
  * [florest](https://github.com/jabong/florest-core) - High-performance workflow based REST API framework in Go
  * [forgery](http://goforgery.appspot.com/) - A clone of the superb Node.js web framework Express.
  * [gramework](https://github.com/gramework/gramework) - The *truly* fastest web framework for Go. Battle tested, highly effective baseline for your web apps.
  * [Gin Web Framework](https://github.com/gin-gonic/gin) - Martini-like API and httprouter gives it good performance.
  * [Goal](https://github.com/colegion/goal) - A toolkit for high productivity web development in Go language built around the concept of code generation.
  * [Go-Blog](https://github.com/matt-west/go-blog) - Blog framework written in Go
  * [go-fastweb](http://code.google.com/p/go-fastweb/) - aims to be a simple, small and clean MVC framework for go
  * [goku](https://github.com/QLeelulu/goku) - a Web Mvc Framework for Go, mostly like ASP.NET MVC.
  * [Golanger](https://github.com/golangers/framework) - Golanger Web Framework is a lightweight framework for writing web applications in Go.
  * [Goldorak.Go](https://github.com/nono/Goldorak.Go) - a web miniframework built using mustache.go, web.go and Go-Redis
  * [go-restful](https://github.com/emicklei/go-restful) - lean package for building REST-style Web Services
  * [GoRest](http://code.google.com/p/gorest/) - An extensive configuration(tags) based RESTful style web-services framework.
  * [go-rest](https://github.com/ungerik/go-rest) - A small and evil REST framework for Go
  * [gorilla](https://github.com/gorilla) - Gorilla web toolkit
  * [GoSrv](https://github.com/jcasts/gosrv) - A Go HTTP server that provides simple command line functionality, config loading, request logging, graceful connection shutdown, and daemonization.
  * [go-start](https://github.com/ungerik/go-start) - A high level web-framework for Go
  * [go-urlshortener](https://github.com/mattn/go-urlshortener) - interface to google's urlshorten API
  * [goweb](https://github.com/stretchrcom/goweb) - Lightweight RESTful web framework for Go providing Ruby on Rails style routing
  * [go-webproject](http://go-webproject.appspot.com) - Modular web application framework and app server
  * [Gowut](http://code.google.com/p/gowut) - Go Web UI Toolkit is a full-featured, easy to use, platform independent Web UI Toolkit written in pure Go.
  * [HttpRouter](https://github.com/julienschmidt/httprouter) - A high performance HTTP request router that scales well
  * [limiter](https://github.com/ulule/limiter) - Simple rate limter middleware for Go
  * [Macaron](https://github.com/Unknwon/macaron) - Modular web framework in Go
  * [mango](https://github.com/paulbellamy/mango) - Mango is a modular web-application framework for Go, inspired by Rack, and PEP333.
  * [Martini **deprecated**](https://github.com/codegangsta/martini) - Martini is a popular, lightweight, extensible package for writing modular web apps/services in Go
  * [Negroni](https://github.com/codegangsta/negroni) - Idiomatic middleware for Go
  * [restclient](https://github.com/jmcvetta/restclient) - Client library for interacting with RESTful APIs.
  * [resty](https://github.com/go-resty/resty) - REST client library inspired by Ruby rest-client.
  * [Revel](http://robfig.github.com/revel/) - High productivity web framework modeled on Play! Framework
  * [Ringo](https://github.com/jjyr/ringo) - Lighweight MVC web framework inspired by Rails, Gin.
  * [sawsij](https://bitbucket.org/jaybill/sawsij/src) - Provides a small, opinionated web framework.
  * [Tango](https://github.com/lunny/tango) - Micro-kernel & pluggable web framework for Go
  * [Tiger Tonic](https://github.com/rcrowley/go-tigertonic) - framework for building JSON web services inspired by Dropwizard
  * [trinity](https://github.com/cihub/trinity) -  MVC framework
  * [Utron](https://github.com/gernest/utron) - MVC Framework
  * [Violetear](https://github.com/nbari/violetear) - HTTP router
  * [web.go](https://github.com/hoisie/web) - a simple framework to write webapps
  * [wfdr](https://github.com/crazy2be/wfdr) - Simple web framework designed for and written in go. Works with other languages as well, but not as well.
  * [xweb](https://github.com/go-xweb/xweb) - A web framework for Go. Just like Struts for Java.

### HTML forms

  * [form](https://github.com/ajg/form) - Complete bidirectional HTML form encoder & decoder (x-www-form-urlencoded) for arbitrary data (package encoding compatible)
  * [gforms](https://github.com/vmihailenco/gforms) - HTML forms for Go
  * [Go-FORM-it](https://github.com/kirves/go-form-it) - Go library for easy and highly-customizable forms creation and template rendering.
  * [GoForms](https://github.com/absoludity/goforms) - Form data validation, cleaning and error reporting - a la django.forms
  * [htmlfiller](https://github.com/griffy/htmlfiller) - Fills in html forms with default values and errors a la Ian Bicking's htmlfill for Python
  * [MonstiForm](https://github.com/monsti/form) - HTML form generator and validator library
  * [revel-csrf](https://github.com/cbonello/revel-csrf) - Cross-Site Request Forgery (CSRF) attacks prevention for the Revel framework
  * [xsrftoken](http://code.google.com/p/xsrftoken) - A package for generating and validating tokens used in preventing XSRF attacks

### Public API Wrappers

  * [adn](https://github.com/whee/adn/) - Interface to the App.net API
  * [anaconda](https://github.com/ChimeraCoder/anaconda) - Client library for the Twitter 1.1 API
  * [ddg](https://github.com/whee/ddg) - DuckDuckGo API interface
  * [facebook](https://github.com/huandu/facebook) - Up-to-date facebook graph API client. Handy and flexible
  * [filepicker-go](https://github.com/filepicker/filepicker-go) - Go library for the Filepicker's REST API
  * [firebase](https://github.com/cosn/firebase) - Client library for the Firebase REST API
  * [gh](https://github.com/rjeczalik/gh) - Scriptable server and net/http middleware for GitHub Webhooks API
  * [github](https://github.com/google/go-github) - Go library for accessing the GitHub REST API v3
  * [githubql](https://github.com/shurcooL/githubql) - Go library for accessing the GitHub GraphQL API v4
  * [gobo](https://github.com/huichen/gobo) - Client library for Sina Weibo
  * [gocaptcha](https://github.com/GeertJohan/gocaptcha) - gocaptcha provides easy access to the reCaptcha API in go
  * [go-dealmap](https://github.com/ancientlore/go-dealmap) - Go library for accessing TheDealMap's API
  * [go-dropbox](https://github.com/nickoneill/go-dropbox) - API library for dropbox
  * [go-flickr](https://github.com/mncaudill/go-flickr) - A wrapper for Flickr's API
  * [go-get-youtube](https://github.com/knadh/go-get-youtube) - A simple library+client for fetching meta data of, and downloading Youtube videos
  * [go-gravatar](https://github.com/ungerik/go-gravatar) - Wrapper for the Gravatar API
  * [go-hummingbird](https://github.com/nstratos/go-hummingbird) - Go library for accessing the Hummingbird.me API
  * [go-libGeoIP](https://github.com/nranchev/go-libGeoIP) - GO Lib GeoIP API for Maxmind
  * [gominatim](https://github.com/grindhold/gominatim) - Go library to access nominatim geocoding services
  * [gomojo](https://github.com/dotmanish/gomojo) - Instamojo API wrapper
  * [gomwapi](https://github.com/kracekumar/go-mwapi) - Access mediawiki contents like wikipedia, wiktionary in golang
  * [go-myanimelist](https://github.com/nstratos/go-myanimelist) - Go library for accessing the MyAnimeList API
  * [googtrans](https://github.com/bthomson/googtrans) - unofficial go bindings for Google Translate API v2
  * [go-recaptcha](https://github.com/dpapathanasiou/go-recaptcha) - Handles reCaptcha form submissions in Go
  * [gorecurly](https://github.com/mbeale/gorecurly) - A Client app to use with Recurly's api
  * [go.strava](https://github.com/strava/go.strava) - Official client library for the Strava V3 API
  * [go.stripe](https://github.com/bradrydzewski/go.stripe) - a simple credit card processing library for Go using the Stripe API
  * [Gotank](https://github.com/searchify/gotank) - Searchify's Go client for the IndexTank full-text search API
  * [go-tripit](https://github.com/ancientlore/go-tripit) - Go API library for the TripIt web services
  * [GoTwilio](https://github.com/sfreiberg/gotwilio) - Twilio library for Go (golang). Very basic at the moment
  * [gravatar](https://github.com/ftrvxmtrx/gravatar) - Gravatar image/profile API library
  * [jsonapi](https://github.com/shwoodard/jsonapi) - Generate JSON API from Go structs
  * [postmark](https://github.com/gcmurphy/postmark) - Access postmark API from Go
  * [reddit.go](https://github.com/tadzik/reddit.go) - Client library for Reddit API
  * [shorturl](https://github.com/subosito/shorturl) - Generic implementation for interacting with various URL shortening services
  * [Stack on Go](https://github.com/laktek/Stack-on-Go) - Go wrapper for Stack Exchange API
  * [stripe](https://github.com/stripe/stripe-go) - Official Stripe client library 
  * [SocialSharesCount](https://github.com/gssumesh/socialsharescount) - Wrapper API on multiple social websites to get URL share statistics
  * [twilio](https://github.com/subosito/twilio) - Simple Twilio API wrapper
  * [twittergo](https://github.com/kurrik/twittergo) - Client library for Twitter's API
  * [cloudcomb-go-sdk](https://github.com/bingohuang/cloudcomb-go-sdk) - Go client library for  [CloudComb](http://c.163.com)

### Other

  * [adhoc-http](https://github.com/tv42/adhoc-httpd) - Quick & dirty HTTP static file server
  * [assets](https://github.com/mostafah/assets) - Helps prepares CSS and JS files for development and production of Go web apps.
  * [bwl](https://github.com/bobappleyard/bwl) - a set of libraries to help build web sites
  * [captcha](https://github.com/dchest/captcha) - Image and audio captcha generator and server
  * [gaerecords](https://github.com/matryer/gae-records) - Lightweight wrapper around appengine/datastore providing Active Record and DBO style management of data
  * [gcd](https://github.com/thepkg/gcd) - provides helpful functions to work with Google Cloud DataStore.
  * [get2ch-go](https://github.com/tanaton/get2ch-go) - a library to access the 2channel Japanese web bulletin board
  * [gofeed](https://github.com/mmcdole/gofeed) - Parse RSS and Atom feeds in Go
  * [go-gzip-file-server](https://github.com/joaodasilva/go-gzip-file-server) - A net.http.Handler similar to FileServer that serves gzipped content
  * [gohaml](https://github.com/realistschuckle/gohaml) - An implementation of the popular XHTML Abstraction Markup Language using the Go language.
  * [go-httpclient](https://github.com/mreiferson/go-httpclient) - a Go HTTP client with timeouts
  * [gojwt](https://github.com/mzgoddard/gojwt) - Json Web Tokens for Go
  * [go-pkg-rss](https://github.com/jteeuwen/go-pkg-rss) - a packages that reads RSS and Atom feeds
  * [gorefit](http://code.google.com/p/gorefit/) - A library for theming existing websites
  * [goreman](https://github.com/mattn/goreman) - foreman clone
  * [GoRequest](https://github.com/parnurzeal/gorequest) - Simplified HTTP client with rich features such as proxy, timeout, and etc. ( inspired by nodejs SuperAgent )
  * [goroute](https://github.com/johncylee/goroute) - A very simple URL router based on named submatches of regular expression that works well with http.Handler .
  * [gorouter](https://github.com/rsentry/gorouter) - Simple router for go to process url variables
  * [go-rss](https://github.com/KonishchevDmitry/go-rss) - Simple RSS parser and generator
  * [go-rss](https://github.com/ungerik/go-rss) - Simple RSS parser, tested with Wordpress feeds.
  * [goscribble](https://github.com/amir/goscribble) - An MPD Audioscrobble
  * [go-twitter](https://github.com/jb55/go-twitter) - another Twitter client
  * [go-twitter-oauth](https://github.com/montsamu/go-twitter-oauth) - a simple Twitter client (supports OAuth)
  * [grender](https://github.com/peterbourgon/grender) - Go static site generator
  * [halgo](https://github.com/jagregory/halgo) - [HAL](http://stateless.co/hal_specification.html)-compliant API client and serialisation library.
  * [http-gonsole](https://github.com/mattn/http-gonsole) - Speak HTTP like a local. (the simple, intuitive HTTP console, golang version)
  * [httprpc](https://github.com/kdar/httprpc) - HTTP RPC codecs (json2, soap, rest)
  * [HypeCMS](https://github.com/opesun/hypecms) - A flexible CMS built with Go and MongoDb.
  * [Kontl](https://github.com/geovedi/kontl) - A client for kon.tl's URL shortening service
  * [mustache.go](https://github.com/hoisie/mustache.go) - an implementation of the Mustache template language
  * [muxer](http://code.google.com/p/go-muxer/) - Simple muxer for a Go app without regexp
  * [Optimus Sitemap Generator](http://patrickmylund.com/projects/osg/) - A universal XML sitemap generator
  * [passwordreset](https://github.com/dchest/passwordreset) - Creation and verification of secure tokens useful for implementation of "reset forgotten password" feature in web applications.
  * [pat](https://github.com/bmizerany/pat) - A Sinatra style pattern muxer
  * [persona](https://github.com/areed/persona) - remote verification API for persona
  * [plex](https://bitbucket.org/agallego/plex) - simple, small, light, regexp http muxer with chaining
  * [purell](https://github.com/PuerkitoBio/purell) - tiny Go library to normalize URLs
  * [pusher.go](https://github.com/madari/pusher.go) - HTTP Server Push module for the standard http package
  * [rest2go](https://github.com/Kissaki/rest2go) - Based on rest.go, forked for improvements and REST consistency
  * [rest.go (forked)](https://github.com/Kissaki/rest.go) - forked rest.go for improvements and REST consistency
  * [resty](https://github.com/go-resty/resty) - Simple HTTP and REST client for Go inspired by Ruby rest-client.
  * [robotstxt](https://github.com/temoto/robotstxt-go) - The robots.txt exclusion protocol implementation. Allows to parse and query robots.txt file.
  * [seshcookie](https://github.com/bpowers/seshcookie) -  A web session library inspired by Beaker
  * [soy](https://github.com/robfig/soy) - A Go implementation for Soy templates (Google Closure templates). High performance and i18n.
  * [user\_agent](https://github.com/mssola/user_agent) - An HTTP User-Agent parser
  * [webtestutil](https://github.com/chlu/webtestutil) - Web and HTTP functional testing utilities. Includes Gorilla testing support.
  * [aop](https://github.com/gogap/aop) - Aspect Oriented Programming For Go.
  * [yt2pod](https://github.com/frou/yt2pod) - Daemon that monitors YouTube channels and publishes audio podcasts of them

## Windows

  * [gform](https://github.com/AllenDang/gform) - An easy to use Windows GUI toolkit for Go
  * [go-ole](https://github.com/mattn/go-ole/) - win32 ole implementation for golang
  * [go-Windows-begin](https://github.com/yoffset/absolute-Windows---Go-Language-beginner) - for the absolute Windows-Go beginner
  * [w32](https://github.com/AllenDang/w32) - Windows API wrapper for Go.
  * [walk](https://github.com/lxn/walk) - "Windows Application Library Kit" for the Go Programming Language
  * [Windows Command Line Shutdown](http://software-download.name/2012/windows-command-line-shutdown/) - A tool to shutdown Windows Computer from Command Prompt

## Unix

  * [inspect](https://github.com/square/inspect) - Linux and MacOSX systems monitoring and diagnostics
  * [unixsums](https://github.com/cxmcc/unixsums) - Legacy Unix checksums: cksum, sum

## Unsorted; please help!

The following entries have not been filed. Please help by putting these in relevant categories.
  * [GoBot](https://github.com/SaturnsVoid/GoBot) - PoC Go HTTP Botnet
  * [ebml-go](http://code.google.com/p/ebml-go/) - EBML decoder
  * [go-bindata](https://github.com/jteeuwen/go-bindata) - Converts any file into manageable Go source code for embedding binary data into a Go program.
  * [consistent](https://github.com/buraksezer/consistent) - Consistent hashing with bounded loads.
  * [goconsistenthash](https://github.com/caglar10ur/goconsistenthash) - Consistent hashing library (based on http://www.lexemetech.com/2007/11/consistent-hashing.html)
  * [go-cron](https://github.com/rk/go-cron) - A small cron job system to handle scheduled tasks, such as optimizing databases or kicking idle users from chat. The cron.go project was renamed to this for `go get` compatibility.
  * [godebiancontrol](https://github.com/mstap/godebiancontrol) - Golang debian control file parser
  * [go-gmetric](https://github.com/jbuchbinder/go-gmetric) - Ganglia gmetric protocol support
  * [gographviz](http://code.google.com/p/gographviz) - Graphviz DOT language parser for golang
  * [godotviz](http://github.com/sc0rp1us/godotviz) - Rendering graphics files from "DOT language". Written in golang
  * [dotviz-server](http://github.com/sc0rp1us/dotviz-server) - WebBased DOT language visualization tool written in go
  * [goseq](https://github.com/lmika/goseq) - command line tool, written in Go, for creating sequence diagrams using a text-based description language.
  * [golor](https://github.com/hantuo/golor) - golor is a command line tool for golang source code coloring
  * [gopcapreader](http://code.google.com/p/gopcapreader) - Presents realtime pcap data as io.Reader objects
  * [go.psl](https://github.com/ebfe/go.psl) - Go regdom-libs/public suffix list
  * [go-webfinger](https://github.com/ant0ine/go-webfinger) - Simple Client Implementation of WebFinger
  * [img-LinuxFr.org](https://github.com/nono/img-LinuxFr.org) - A reverse-proxy cache for external images used on LinuxFr.org
  * [seed](https://github.com/tv42/seed) - Easily seed PRNGs with some entropy
  * [spellabc](https://github.com/elasticdog/spellabc) - Package spellabc implements spelling alphabet code word encoding.
  * [Twackup](https://github.com/tv42/twackup) - Backs up your tweets into local files
  * [Tasks](https://github.com/thewhitetulip/Tasks) - A simplistic todo list manager written in Go
  * [one-file-pdf](https://github.com/balacode/one-file-pdf) - A minimalist Go PDF writer in <2K lines and 1 file