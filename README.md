# myip by BlackF1re

Portable shell utility for checking public IP and basic geolocation info.

## Features

- POSIX `sh` script
- `curl` first, `wget` fallback
- `ipapi.co` primary backend with `2ip.me` fallback
- Self-install into a user `bin` directory
- Auto-update on startup from GitHub by default
- Safe manual updates with syntax and version checks
- Colored output for IP and country

## Usage

```sh
chmod +x ./myip
./myip
./myip --ip
./myip --json
./myip --version
./myip --remove
./myip --update
```

## Install behavior

Run the script from any directory. On first launch it will try to copy itself to:

- `$PREFIX/bin` on Termux-like systems
- `~/.local/bin`
- `~/bin`
- `/usr/local/bin` if writable

It updates older installed copies, refuses to overwrite newer ones, and can report:

```text
myip successfully updated from OLD_VERSION to CURRENT_VERSION
```

For `--ip` and `--json`, install and update service messages go to stderr so stdout stays usable in scripts.

## GitHub updates

By default, installed copies check this raw script on startup:

```text
https://raw.githubusercontent.com/BlackF1re/myip/master/myip
```

If a different valid copy is downloaded, `myip` checks shell syntax, compares versions, replaces the running file, and re-executes the original command.

Manual update:

```sh
myip --update
```

Configuration knobs:

```sh
MYIP_AUTO_UPDATE=0 myip
MYIP_AUTO_UPDATE_INTERVAL=3600 myip
MYIP_GITHUB_REPO=owner/repo MYIP_GITHUB_BRANCH=branch myip
MYIP_AUTO_UPDATE_URL=https://example.com/myip myip
```
