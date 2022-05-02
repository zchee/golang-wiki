as title, when i build with -ldflags "-X ..." in shell scripts, build failed and report some error 

```bash
go build -o /home/kun1h/git/soulma/bin/slm -ldflags "-X=svr/app/lib.version=c0f634fd -X=svr/app/lib.builtAt=1651459267 -X=svr/app/lib.buildMode=Debug" main.go
# terminal working, shell script report "flag provided but not defined: -X"
```

```bash
go build -o /home/kun1h/git/soulma/bin/slm -ldflags "-X svr/app/lib.version=c0f634fd -X svr/app/lib.builtAt=1651459267 -X svr/app/lib.buildMode=Debug" main.go
#terminal working, shell script report "invalid value "\"-X" for flag -ldflags: missing =<value> in <pattern>=<value>"
```

```bash
go build -o /home/kun1h/git/soulma/bin/slm -ldflags "-X=svr/app/lib.version=c0f634fd" -ldflags "-X=svr/app/lib.builtAt=1651459267" -ldflags "-X=svr/app/lib.buildMode=Debug" main.go
#this can build, but not set versions.
```

...