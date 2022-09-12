# for HTTPS dev environment for localhost

## Stack

- `mkcert`: to generate `TLS` certs
- `docker`: to run container
- `traefik`: reverse proxy for docker environment

# how to use

## install mkcert 

### Linux 

#### install certutil
``` bash 
sudo apt install libnss3-tools
```
#### install homebrew
refer below link to install `homebrew` for linux  
https://docs.brew.sh/Homebrew-on-Linux
#### install mkcert 
```bash
brew install mkcert
```

### Mac
#### install mkcert
```bash
brew install mkcert
```

### Windows
#### install chocolatey
refer below link to install `chocolatey`  
https://chocolatey.org/install
#### install mkcert
```bash
choco install mkcert
```

## generate certs
### install mkcert as CA
```bash
mkcert -install
```
### generate certs
generate cert files for `*.dev.com` as `local-cert.pem` and `local-key.pem` 
```bash
mkcert \
-cert-file local-cert.pem \
-key-file local-key.pem \
*.dev.com dev.com
```

## for WSL
if you use `WSL` as your dev environment, you need to proceed below to get correct `TLS` certs for `traefik`.   
1. install `mkcert` and create certs for both of `WSL` linux OS and `Windows` host OS.  
2. Copy certs of `Windows` host OS to linux `WLS` OS and use that certs for `traefik` container.  
This is because the target you are connecting to is the host machine, not `WSL` linux OS.  

## Run application 

Your application should be served on port 3000.  
And you will access that service by address `app.dev.com`  
You can change the service port and domain from `dynamic_conf.yaml` file. 

## Run docker compose
```bash
docker-compose up -d
```

then you can connect `app.dev.com` 
