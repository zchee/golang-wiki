[tutorial](https://medium.freecodecamp.org/setting-up-go-programming-language-on-windows-f02c8c14e2f)
`setx scoopApps "C:\Users\%username%\scoop\apps" /M`
`echo %scoopApps%`
`scoop install go `
`=======Phase 3: Create the GOPATH environment variable===`
`setx GOPATH "%scoopApps%/go" /M`
`echo %GOPATH%`
`setx GOBIN "%GOPATH%/bin" /M`
`echo %GOBIN%`
`setx PATH "%PATH%;%GOBIN%" /M`
`=======Phase 4: Test and ensure===`
`go get github.com/golang/example/hello`
`%GOPATH%/bin/hello`