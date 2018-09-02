scoop install go 
setx GOPATH "%scoopApps%/go"
echo %GOPATH%
setx GOBIN "%GOPATH%/bin" /M
echo %GOBIN%
setx PATH "%PATH%;%GOBIN%" /M