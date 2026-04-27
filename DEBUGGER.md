# Debug using [Visual Studio Code]

## [devcontainer]

When [Visual Studio Code] offers, click __Reopen in Container__.

## Integrate

> [!WARNING]
> This method updates package*.json to integrate eufy-security-client into the debugger, but
>
> Changes to package*.json and eufy-security-client __MUST NOT__ be committed at this level!

```bash
git submodule update --init
git update-index --skip-worktree package*.json eufy-security-client
```

## Prepare

Execute these commands after every container {,re}build.

```bash
sudo ln -s $PWD /data
sudo ln -s $PWD /usr/src/app
(cd eufy-security-client && npm install . --prefix=../ && npm run build)
```

## Configure

Read [these warnings](https://github.com/fuatakgun/eufy_security#how-is-this-working) and create a secondary account for eufy_security!

Change the following as appropriate:

```bash
cat >.env <<'EOF'
USERNAME=you@me.com
PASSWORD="supersecret"
COUNTRY=US
EOF
```

Optionally configure any of the following into [.env](./.env):

* EVENT_DURATION_SECONDS
* LANGUAGE
* P2P_CONNECTION_SETUP
* POLLING_INTERVAL_MINUTES
* ACCEPT_INVITATIONS
* TRUSTED_DEVICE_NAME
* STATION_IP_ADDRESSES
* PORT
* DEBUG

## Launch Server

Press __F5__ or click __Run and Debug__ in left sidebar then click the Play button to __Start Debugging__.

[devcontainer]: https://code.visualstudio.com/docs/devcontainers/containers
[Visual Studio Code]: https://code.visualstudio.com/
