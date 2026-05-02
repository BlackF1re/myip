# myip by BlackF1re

Portable shell utility for checking public IP and basic geolocation info.

## Features

- POSIX `sh` script
- `curl` first, `wget` fallback
- `ipapi.co` primary backend with `2ip.me` fallback
- Self-install into a user `bin` directory
- Safe in-place updates with version checks
- Colored output for IP and country

## Usage

```sh
chmod +x ./myip
./myip
./myip --ip
./myip --json
./myip --version
./myip --remove
MYIP_GITHUB_REPO=owner/repo ./myip --update
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

## GitHub updates

When your repository exists, set:

```sh
export MYIP_GITHUB_REPO=owner/repo
```

After that:

- `myip`, `myip --ip`, `myip --json`, and `myip --version` can show an update notice
- `myip --update` downloads the latest `myip` from `main`
