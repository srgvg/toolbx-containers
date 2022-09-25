# Toolbx containers
Source to build `toolbox` container images containing all tools and config that I use on a daily basis.

⚠️⚠️ __DISCLAIMER__: This project is still in flux and should be used at your own risk ⚠️⚠️

![toolbox](https://w7.pngwing.com/pngs/844/934/png-transparent-car-icon-toolbox-miscellaneous-brown-text-thumbnail.png)

this project currently has 2 images:

- base-toolbox toolbox (general purpose toolbox)
- vim-toolbox (uses base-toolbox as a base + neovim)

## Motivation
I work as a freelance Cloud Engineer / SRE and often need seperate environments
for different customers. Sometimes I even need different environments for
multiple teams at a single customer.

## Requirements
<TBD>

## What's in the toolboxes?
### Packages
- tmux
- asdf

### NeoVim
- Plugins are managed by `Packer` which seems to be the go-to plugin manager for Neovim.
- Language server (LSP) is handled by `neovim-lsp`.
- `Telescope` takes care of fuzzy finding.

## How binaries are managed.
A lot of the tools that I use can be installed by downloading a binary, make it
executable and add it to a location in $PATH. Example: Terraform, kubectl,
golang, ...

Adding all these to the container image would cause it to become quite big
which is something I want to prevent. therefore the useful
[asdf]([https://github.com/asdf-vm/asdf) tool will be used. This tool will
install and manage the versions for the binaries we need, but will put them on
the host system (so not in the container - `$ASDF_DATA_DIR`). 

Best way to explain it is by showing some examples

### Example: Install golang
```
asdf install golang 1.19.1
```

## How to use the toolbox
<TBD>

## References
- https://github.com/containers/toolbox
