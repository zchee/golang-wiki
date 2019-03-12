`gopls` is an implementation of the Language Server Protocol (LSP) server for Go.
The LSP allows any text editor to be extended with IDE-like features;
see https://langserver.org/ for details.

## Status

`gopls` is currently under active development by the Go team. The code is in the x/tools repository, in [golang.org/x/tools/internal/lsp](https://golang.org/x/tools/internal/lsp) and [golang.org/x/tools/cmd/gopls](https://golang.org/x/tools/cmd/gopls). Because we are actively working on `gopls`, it is not stable. If you choose to use it, be aware that things may regularly break or change.

## Contributing

Contributions are welcome, but since development is so active, we request that you file an issue and claim it before starting to work on something. Otherwise, it is likely that we might already be working on a fix for your issue. 

Please see all available issues under the [gopls label](https://github.com/golang/go/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+label%3Agopls) on the Go issue tracker. Any issue without an assignee and with the label "Suggested" is fair game - just assign yourself or comment on the issue before you begin working!

### Installation

First, install `gopls` by running `go install golang.org/x/tools/cmd/gopls`. We suggest using VSCode with the Go plugin. The required settings are:

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
    "goToTypeDefinition": true,
},
"go.buildOnSave": "off",
"go.vetOnSave": "off",
"editor.formatOnSave": true,
"editor.codeActionsOnSave": {
    "source.organizeImports": true,
},
```

Turning off both build and vet on save is useful to avoid duplicating diagnostics from both gopls and VSCode-Go. `gopls` also runs both `gofmt` and `goimports`.

## Additional Information

Questions can be directed toward [@stamblerre](https://github.com/stamblerre) or [@ianthehat](https://github.com/ianthehat). For consistent updates on the development progress of gopls, see the notes from the golang-tools meetings (https://github.com/golang/go/wiki/golang-tools).