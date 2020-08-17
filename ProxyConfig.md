
# NPM configuration
* Use these commands:
```bash
npm config set proxy http://username:password@host:port
npm config set https-proxy http://username:password@host:port
```
* Or you can edit directly your ~/.npmrc file:
```bash
proxy=http://username:password@host:port
https-proxy=http://username:password@host:port
https_proxy=http://username:password@host:port
```
# Git configuration
1. Use the below command
```bash
git config --global http.proxy http://username:password@host:port
git config --global https.proxy http://username:password@host:port
```
2. Or Edit directly your ~/.gitconfig file:
```bash
[http]
        proxy = http://username:password@host:port
[https]
        proxy = http://username:password@host:port
```
