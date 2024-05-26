## Thanks
[coder/code-server](https://github.com/coder/code-server)

[linuxserver/docker-code-server](https://github.com/linuxserver/docker-code-server)

## Description
Use totp as password to login code-server. NOT 2fa (both password and totp).
## Note
linuxserver/code-server SHOULD use version 4.89.1
## Use
```sh
wget patch.tar.gz

tar -zxf patch.tar.gz -C ~/patch

TOTPSECRET=<YOUR TOTP SECRET>   # also add to your authenticator APP

docker run -dt --rm \
    --name=cs \
    -p 8443:8443 \
    -e DEFAULT_WORKSPACE=/config/workspace \
    -e PASSWORD=${TOTPSECRET} \
    -v ~/patch/node_modules:/app/code-server/node_modules:ro \
    -v ~/patch/out:/app/code-server/out:ro \
    linuxserver/code-server:4.89.1
```

Enjoy
