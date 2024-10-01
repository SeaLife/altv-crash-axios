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

Full server logs:

```txt
altv-1  | [13:21:46] alt:V Server 16.2.13 (release)
altv-1  | [13:21:46] Starting xxxxxxxxxxxxx (alt:v, development) on [::]:7788
altv-1  | [13:21:46] Loading resource test
altv-1  | [13:21:46] Loading resource chat
altv-1  | [13:21:46] Loaded resource chat
altv-1  | [13:21:46] Loaded resource test
altv-1  | [13:21:46] Required server permissions:
altv-1  | [13:21:46] Optional server permissions:
altv-1  | [13:21:46] Starting HTTP server on [::]:7788
altv-1  | [13:21:46] Main thread started (ThreadId: 18)
altv-1  | [13:21:46] SyncSend thread started (ThreadId: 70)
altv-1  | [13:21:46] EntityStreamer thread started (ThreadId: 67)
altv-1  | [13:21:46] SyncSend thread started (ThreadId: 71)
altv-1  | [13:21:46] SyncSend thread started (ThreadId: 69)
altv-1  | [13:21:46] SyncSend thread started (ThreadId: 73)
altv-1  | [13:21:46] SyncSend thread started (ThreadId: 72)
altv-1  | [13:21:46] SyncSend thread started (ThreadId: 74)
altv-1  | [13:21:46] SyncSend thread started (ThreadId: 76)
altv-1  | [13:21:46] SyncSend thread started (ThreadId: 75)
altv-1  | [13:21:46] SyncReceive thread started (ThreadId: 77)
altv-1  | [13:21:46] SyncReceive thread started (ThreadId: 78)
altv-1  | [13:21:46] SyncReceive thread started (ThreadId: 79)
altv-1  | [13:21:46] SyncReceive thread started (ThreadId: 80)
altv-1  | [13:21:46] NetworkWorker #1 thread started (ThreadId: 81)
altv-1  | [13:21:46] Console thread started (ThreadId: 100)
altv-1  | [13:21:46][Warning] Server started in debug mode
altv-1  | /root/entrypoint.sh: line 5:    18 Segmentation fault      (core dumped) ./altv-server "$@"
```
