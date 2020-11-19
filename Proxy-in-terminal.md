# Proxy in Terminal

## HTTP Proxy

```
export http_proxy="http://localhost:port"
export https_proxy="http://localhost:port"
```

## Socks5 Proxy

```
export http_proxy="socks5://127.0.0.1:1080"
export https_proxy="socks5://127.0.0.1:1080"

-or-

export ALL_PROXY=socks5://127.0.0.1:1080
```

## Git

```
git config --global http.proxy 'socks5://127.0.0.1:1080' 
git config --global https.proxy 'socks5://127.0.0.1:1080'
```

### `apt`

```
$ sudo vim /etc/apt/apt.conf

Acquire::http::Proxy "http://proxyAddress:port"
```

## Reference

- https://zhuanlan.zhihu.com/p/46973701

