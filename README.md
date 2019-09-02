# Terraform Version Manager

Install and quickly switch terraform versions

## Usage

List versions:

```sh
$ tfm versions
  0.11.14
  0.12.6
* 0.12.7
```

Switch version:

```sh
$ tfm use 0.12.6
Done, current terraform version is 0.12.6
$ terraform version
Terraform v0.12.6

```

Install (see https://releases.hashicorp.com/terraform/):

```sh
$ tfm install 0.12.5
...
```

## Customization

By default, terraform versions are installed in `~/.tfm` and the `terraform` binary will be linked to `~/.opt/bin`. macOS will be assumed as operating system.

Some env vars can be used to customize those defaults. Run `tfm printenv` to see which ones exist and what the current values are:

```
$ tfm printenv
TFM_PREFIX: ~/.opt/bin
TFM_DIR: ~/.tfm
TFM_OS: darwin_amd64
```

## Acknowledgements

Thanks to [Hashicorp](https://www.hashicorp.com/) for building Terraform and making IaC a thing - and for breaking compatibility to badly that this tool became necessary.
