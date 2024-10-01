# Description

_docker-compose.yml_
```yml
services:
  altv:
    image: altmp/altv-server:release
    volumes:
      - /root/alteravitarp/data-altv/resources:/altv/resources
      - /root/alteravitarp/data-altv/server.toml:/altv/server.toml
    environment:
      ALTV_USE_ENV_CONFIG: 'false'
    ports:
      - 7788:7788
      - 7788:7788/udp
```

_server.toml_
```toml
name = 'xxxxxxxxxx (alt:v, development)'
port = 7788
players = 177
# password = 'xxxxx123'
announce = false
gamemode = 'xxxxxx'
website = 'discord.gg/xxxxx'
language = 'de'
description = 'Entwicklungsserver'
modules = ['js-bytecode-module', 'js-module', 'csharp-module']

resources = [
  'test',
]

debug = true
```

The resource is located in this repository. Dependencies are installed using a docker command in the resource directory.
```bash
docker run --rm -it -v $(pwd):/host -w /host node:18 yarn install
```
