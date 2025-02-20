
# Sui Move Setup on Ubuntu

This repository provides a detailed walkthrough for installing Sui Move on Ubuntu. You'll find instructions for installing the Sui CLI, setting up the `sui-move-analyzer` language server, and configuring Visual Studio Code (VSCode) for an optimized development environment.

## Prerequisites

Before you begin, make sure your system is up-to-date and that you have all the necessary dependencies.

### 1. Update Your System
```bash
sudo apt-get update
```

### 2. Install Essential Dependencies
```bash
sudo apt-get install curl git-all cmake gcc libssl-dev pkg-config libclang-dev libpq-dev build-essential
```

## Installing Rust

### 3. Ensure `curl` is Installed
Verify the installation of `curl`:
```bash
curl --version
```
If it's missing, install it with:
```bash
sudo apt install curl
```

### 4. Install or Update Rust
For a fresh install, run:
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
If Rust is already installed, update it to the latest stable version:
```bash
rustup update stable
```

## Installing the Sui CLI

### 5. Install the Sui CLI
Run the following command to install the Sui CLI:
```bash
cargo install --locked --git https://github.com/MystenLabs/sui.git --branch testnet sui --features tracing
```

### 6. Confirm the Installation
Verify the Sui CLI installation by checking its version:
```bash
sui --version
```

## Setting Up the `sui-move-analyzer` Language Server

### 7. Download the Binary
Download the latest precompiled binary for Ubuntu from the [releases page](https://github.com/movebit/sui-move-analyzer/releases/download/v1.1.8/sui-move-analyzer-ubuntu22.04-x86_64-v1.1.8).

### 8. Rename and Move the Binary
Rename the file to `sui-move-analyzer` and move it to a directory in your PATH (e.g., `/usr/local/bin`):
```bash
sudo mv sui-move-analyzer /usr/local/bin
```

### 9. Grant Execute Permissions
Make the binary executable:
```bash
sudo chmod +x /usr/local/bin/sui-move-analyzer
```

### 10. Verify the Language Server Installation
Check that the language server is installed correctly:
```bash
sui-move-analyzer --version
```

## Installing VSCode

### 11. Download VSCode
Download the latest `.deb` package for VSCode from the [official website](https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64).

### 12. Install VSCode
Navigate to your Downloads folder and install the package:
```bash
cd ~/Downloads/
sudo apt install ./code*.deb
```

## Recommended VSCode Extensions

For the best development experience, install these VSCode extensions:
- [Sui Move Analyzer](https://marketplace.visualstudio.com/items?itemName=MoveBit.sui-move-analyzer)
- [Even Better TOML](https://marketplace.visualstudio.com/items?itemName=tamasfe.even-better-toml)
- [Move by MystenLabs](https://marketplace.visualstudio.com/items?itemName=mysten.move)
- [Move Syntax by Damir Shamanaev](https://marketplace.visualstudio.com/items?itemName=damirka.move-syntax)

## Video Walkthrough

For a visual guide to the entire setup process, check out the video walkthrough linked below:
[Video Guide](#)

