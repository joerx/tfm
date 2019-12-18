# Terraform Version Manager

Install and quickly switch terraform versions

## Setup

- Clone this repo and copy [tfm](./tfm) somewhere into your `$PATH`
- Make sure `~/.opt/bin` exists and is on your path
- Alternatively, set `TFM_PREFIX` to a different value in your shell profile

```sh
# ~/.bash_profile
export PATH=$HOME/.opt/bin:$PATH

# or:

export PATH=$HOME/.bin
TFM_PREFIX=$HOME/.bin
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

By default, terraform versions are installed in `~/.tfm` and the `terraform` binary will be linked to `~/.opt/bin`. macOS will be assumed as operating system (contributions welcome).

Some env vars can be used to customize those defaults. Run `tfm printenv` to see which ones exist and what the current values are:

```
$ tfm printenv
TFM_PREFIX: ~/.opt/bin
TFM_DIR: ~/.tfm
TFM_OS: darwin_amd64
```

## Acknowledgements

Thanks to [Hashicorp](https://www.hashicorp.com/) for building Terraform and making IaC a thing - and for breaking compatibility to badly that this tool became necessary.
