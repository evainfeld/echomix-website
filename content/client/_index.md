---
title: "Download EchoMix"
linkTitle: "Downloads"
description: "Download and install the EchoMix chat client"
---

## EchoMix Client (Beta)

The EchoMix client — **katzenqt** — is a Qt/QML desktop application for Linux that connects to the Katzenpost anonymity network.

{{< alert color="warning" >}}
**Beta software.** Do not rely on this software for anonymity, security, or privacy. It is intended for developers and early testers only.
{{< /alert >}}

## Prerequisites

The following must be installed before proceeding:

- Linux (Debian/Ubuntu recommended)
- `git` and `make`

```bash
sudo apt install -y git make
```

## Quick Start

For most users, two commands are enough:

```bash
git clone https://www.github.com/katzenpost/katzenqt ~/katzenqt
cd ~/katzenqt
make deps
make run
```

## Full Setup (if Quick Start fails)

Run the following targets in order:

```bash
git clone https://www.github.com/katzenpost/katzenqt ~/katzenqt
cd ~/katzenqt

make system-setup
make setup-uv
make setup
make test
make kpclientd
make install-kpclient
make kpclientd.service
make status
```

If `make status` shows the following, the background daemon is running correctly:

```
backend: uv
venv: .venv
kpclientd(bin): /home/user/.local/bin/kpclientd
kpclientd(service): active
kpclientd(path): found
```

Then launch the UI:

```bash
make run
```

## Network Configuration

katzenqt needs configuration files pointing to a Katzenpost mixnet. Place them at:

```
~/.local/katzenpost/client.toml
~/.local/katzenpost/thinclient.toml
```

To connect to the **namenlos** public testnet, clone its config repo and copy the files:

```bash
git clone https://github.com/katzenpost/namenlos ~/namenlos
mkdir -p ~/.local/katzenpost/
cp ~/namenlos/configs/client.toml     ~/.local/katzenpost/client.toml
cp ~/namenlos/configs/thinclient.toml ~/.local/katzenpost/thinclient.toml
cp ~/namenlos/configs/thinclient.toml ~/katzenqt/configs/thinclient.toml
```

## Source Code

The full source is available on GitHub:

**[github.com/katzenpost/katzenqt](https://github.com/katzenpost/katzenqt)**
