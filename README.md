# myip

`myip` is a portable POSIX shell utility for showing your public IP address and basic network/geolocation information from the terminal.

It is designed for Linux, OpenWrt, Termux, WSL, macOS, servers, routers, and small shell scripts where you need a fast `myip`, `myip --ip`, or `myip --json` command.

## Features

- POSIX `sh`, no Bash requirement
- Uses `curl` first and falls back to `wget`
- `ipapi.co` primary backend with `2ip.me` fallback
- Self-installs to a user `bin` directory on first run
- Auto-update on startup from GitHub by default
- Manual `--update` command with syntax and version checks
- Clean stdout for `--ip` and `--json`, suitable for scripts

## Install by copy-paste

```sh
cd /tmp
curl -fsSLO https://raw.githubusercontent.com/BlackF1re/myip/master/myip || wget -O myip https://raw.githubusercontent.com/BlackF1re/myip/master/myip
chmod +x ./myip
./myip
```

After first run, the script tries to install itself to one of these locations:

```text
$PREFIX/bin
~/.local/bin
~/bin
/usr/local/bin
```

Then use:

```sh
myip
```

## Install on OpenWrt

```sh
opkg update
opkg install curl ca-bundle || opkg install wget-ssl ca-bundle
cd /tmp
curl -fsSLO https://raw.githubusercontent.com/BlackF1re/myip/master/myip || wget -O myip https://raw.githubusercontent.com/BlackF1re/myip/master/myip
chmod +x ./myip
./myip
```

## Install on Termux

```sh
pkg update
pkg install curl
cd $HOME
curl -fsSLO https://raw.githubusercontent.com/BlackF1re/myip/master/myip
chmod +x ./myip
./myip
```

## Usage

```sh
myip
myip --ip
myip --json
myip --version
myip --update
myip --remove
```

Examples:

```sh
PUBLIC_IP="$(myip --ip)"
echo "Current public IP: $PUBLIC_IP"

myip --json > ip-info.json
```

## Auto-update

By default, installed copies check this raw script on startup:

```text
https://raw.githubusercontent.com/BlackF1re/myip/master/myip
```

Disable auto-update for one run:

```sh
MYIP_AUTO_UPDATE=0 myip
```

Check at most once per hour:

```sh
MYIP_AUTO_UPDATE_INTERVAL=3600 myip
```

Use another repository or branch:

```sh
MYIP_GITHUB_REPO=owner/repo MYIP_GITHUB_BRANCH=main myip
```

Use a full custom raw URL:

```sh
MYIP_AUTO_UPDATE_URL=https://example.com/myip myip
```

## Troubleshooting

No downloader:

```sh
command -v curl || command -v wget
```

OpenWrt TLS/certificate issues:

```sh
opkg update
opkg install ca-bundle curl
```

Remove installation and config:

```sh
myip --remove
```

## SEO keywords

public IP CLI, public IP shell script, OpenWrt public IP, Termux public IP, Linux public IP, POSIX sh IP checker, geolocation CLI, IP JSON CLI, router IP tool, shell network utility.

## Suggested GitHub topics

`public-ip`, `ip-address`, `cli`, `shell`, `posix-sh`, `openwrt`, `termux`, `linux`, `router`, `network`, `geolocation`, `curl`, `wget`

## License

No license file is included yet. Add a license before accepting outside contributions.
