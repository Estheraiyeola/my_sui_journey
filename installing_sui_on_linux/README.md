
# Sui Move Setup on Ubuntu

This repository provides a detailed walkthrough for installing Sui Move on Ubuntu. You'll find instructions for installing the Sui CLI, setting up the `sui-move-analyzer` language server, and configuring Visual Studio Code (VSCode) for an optimized development environment.

## Prerequisites

Before you begin, make sure your system is up-to-date and that you have all the necessary dependencies installed.

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
Verify that `curl` is installed:
```bash
curl --version
```
If it’s missing, install it with:
```bash
sudo apt install curl
```

### 4. Install or Update Rust
- **Fresh Install:**
  ```bash
  curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
  ```
- **Update Existing Installation:**
  ```bash
  rustup update stable
  ```

## Installing the Sui CLI

### 5. Install the Sui CLI
Run the following command to install the Sui CLI:
```bash
cargo install --locked --git https://github.com/MystenLabs/sui.git --branch testnet sui --features tracing
```

### 6. Verify the Installation
Check the installed version:
```bash
sui --version
```

#### Troubleshooting: Sui Command Not Found
If you see an error like:
```
Command 'sui' not found, did you mean: ...
```
it might be because the Sui CLI was installed in a hidden folder (for example, `~/.cargo/bin` or another hidden directory). To resolve this:

1. **Locate the Binary:**  
   Check if the Sui binary exists in your Cargo bin directory or another hidden folder:
   ```bash
   ls ~/.cargo/bin/sui
   ls ~/.sui/bin/sui
   ```

2. **Update Your PATH:**  
   If you find the binary, add its directory to your PATH. For example, if it's in `~/.cargo/bin`, add the following line to your shell configuration file (e.g., `~/.bashrc` or `~/.zshrc`):
   ```bash
   export PATH="$HOME/.cargo/bin:$PATH"
   ```
   Then reload your configuration:
   ```bash
   source ~/.bashrc
   ```

3. **Verify Again:**  
   Now, run:
   ```bash
   sui --version
   ```
   The command should be recognized.

## Setting Up the `sui-move-analyzer` Language Server

### 7. Download the Precompiled Binary
Download the latest `sui-move-analyzer` binary for Ubuntu from the [releases page](https://github.com/movebit/sui-move-analyzer/releases/download/v1.1.8/sui-move-analyzer-ubuntu22.04-x86_64-v1.1.8).

### 8. Rename and Move the Binary
Rename the downloaded file:
```bash
mv <downloaded-filename> sui-move-analyzer
```
Move the binary to a directory in your PATH (e.g., `/usr/local/bin`):
```bash
sudo mv sui-move-analyzer /usr/local/bin
```

### 9. Grant Execute Permissions
Make the binary executable:
```bash
sudo chmod +x /usr/local/bin/sui-move-analyzer
```

### 10. Verify the Language Server Installation
```bash
sui-move-analyzer --version
```

## Installing VSCode

### 11. Download VSCode
Download the latest `.deb` package for VSCode from the [official site](https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64).

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

For a visual guide through the setup process, check out the video walkthrough below:
[Video Guide](#)


This guide should help ensure your environment is properly configured, including handling cases where the Sui CLI might reside in a hidden folder. Happy coding!
