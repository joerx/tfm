# Terraform Version Manager

Install and quickly switch terraform versions

## Requirements

Only Linux and macOS are supported. OS detection only works for `amd64` since I don't have an arm device for testing. This is a bash script, no native Windows support is planned. 

## Setup

- Clone this repo and copy [tfm](./tfm) somewhere into your `$PATH`
- Make sure `~/.local/bin` exists and is on your path
- Alternatively, set `TFM_PREFIX` to a different value in your shell profile

```sh
# ~/.bash_profile
export PATH=$HOME/.local/bin:$PATH

# or:

export PATH=$HOME/.bin:$PATH
export TFM_PREFIX=$HOME/.bin
```

## Usage

Usage: 

```sh
$ tfm
Usage: tfm <subcommand> [args]
...
```

List versions:

```sh
Versions:
* 0.11.14
  0.12.16

Aliases:
  terraform = 0.11.14
  tf12 = 0.12.18
```

Switch default version:

```sh
$ tfm use 0.12.18
Aliased terraform version 0.12.18 to terraform
Current terraform version is 0.12.18

$ terraform version
Terraform v0.12.18
```

Set an alias:

```sh
$ tfm alias 0.12.18 tf12
Aliased terraform version 0.12.18 to tf12
```

Install:

```sh
$ tfm install 0.12.5
...
```

List installation candidates:

```sh
$ tfm list-remote | grep ^0.12
```

## Customization

By default, terraform versions are installed in `~/.tfm` and the `terraform` binary will be linked to `~/.local/bin`.

Some env vars can be used to customize those defaults. Run `tfm printenv` to see which ones exist and what the current values are:

```
$ tfm printenv
TFM_PREFIX: ~/.opt/bin
TFM_DIR: ~/.tfm
```

## Acknowledgements

Thanks to [Hashicorp](https://www.hashicorp.com/) for Terraform and nvm for inspiration.
