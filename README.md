# nix-config

This repository contains my private Nix configuration for macOS. It's also meant as a protocol to get going.

## Setup

> [!IMPORTANT]
> For reasons unknown, I was not able to install Nix on older versions of macOS. Any of the following installations methods got stuck. My first successful attempt was on macOS 15.5, the latest version at the time of this writing.

### 1. Install Nix

There are several ways to install Nix on a Mac. Since the official Nix installer does not provide an uninstaller, the [Nix installer by Determinate Systems](https://github.com/DeterminateSystems/nix-installer?tab=readme-ov-file#determinate-nix-installer) or the [Lix installer](https://lix.systems/install/#on-any-other-linuxmacos-system) are widely considered better alternatives. I'm using the former in the following.

> [!WARNING]
> Make sure to read this chapter until the end before running the command.

```sh
curl -fsSL https://install.determinate.systems/nix | sh -s -- install
```

The first dialog in the installer will ask you whether to "Install Determinate Nix?". Suprisingly, the answer is "No", we're going to use the installer to install Nix from NixOS.

### 2. Install Nix-Darwin

Since this repository already includes my `flake.nix`, we can clone it to a location of our liking.

```sh
git clone https://github.com/idleberg/nix-config ~/nix
```

Install `nix-darwin`

```sh
sudo nix run nix-darwin/master#darwin-rebuild -- switch --flake .#
```

## Todos

Unfortunately, not all parts are yet automated and I have not yet investigated into how to solve the following todos properly

- [ ] `xcode-select --install`
- [ ] `softwareupdate --install-rosetta`

## Acknowledgments

Videos

- [Nix explained from the ground up](https://www.youtube.com/watch?v=5D3nUU1OVx8), if you're new to Nix
- [Nix is my favorite package manager to use on macOS](https://www.youtube.com/watch?v=Z8BL8mdzWHI)
- [Use nix on macOS to declare victory over your configs](https://www.youtube.com/watch?v=qUmZtC6ts0M)

Configs

- [Mitchell Hashimoto](https://github.com/mitchellh/nixos-config)
- [ironicbadger](https://github.com/ironicbadger/nix-config)
