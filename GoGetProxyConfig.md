Setting proxies for source code used by ` go get ` (listed in GoGetTools)

## git
```
$ git config [--global] http.proxy http://proxy.example.com:port
```

## mercurial
Edit ` ~/.hgrc ` and add the following:
```
[http_proxy]
host=proxy.example.com:port
```

## svn
Edit ` ~/.subversion/servers ` and add the following:
```
[Global] 
http-proxy-host=proxy.example.com
http-proxy-port=xxxx 
```