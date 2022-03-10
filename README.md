# Terraform Version Manager

Lightweight bash script to manage and quickly switch terraform versions

## Requirements

Currently tested on macOS x64 and arm64. May test on Linux when I get to it, contributions welcome. This is a bash script, no native Windows support is planned - If you get this to work on WSL2, let me know ;)

## Setup

- Download https://raw.githubusercontent.com/joerx/tfm/master/tfm and copy somewhere into your `$PATH`
- Make sure `~/.local/bin` exists and is on your `$PATH`
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
* 1.0.11
  1.1.7

Aliases:
  terraform = 1.0.11
  tf10 = 1.0.11
  tf11 = 1.1.7
```

Switch default version:

```sh
$ tfm use 1.1.7
Aliased terraform version 1.1.7 to terraform
Current terraform version is 1.1.7

$ terraform version
Terraform v1.1.7
```

Set an alias:

```sh
$ tfm alias 1.1.7 tf11
Aliased terraform version 1.1.7 to tf11
```

Install:

```sh
$ tfm install 1.1.7
...
```

List installation candidates:

```sh
$ tfm releases | grep ^1.1
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
