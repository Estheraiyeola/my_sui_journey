
# Sui Development Setup on Windows via WSL

## Prerequisites
1. Windows 10/11 with administrative privileges
2. Stable internet connection
3. Minimum 8GB RAM (16GB recommended)

---

## 1. Set Up WSL & Ubuntu

### 1.1 Enable WSL
```powershell
# Run in PowerShell as Administrator
wsl --install
```
Restart your computer when prompted

### 1.2 Install Ubuntu
1. Launch Microsoft Store
2. Search for "Ubuntu 22.04 LTS"
3. Click Install
4. Launch Ubuntu from Start Menu
5. Create UNIX username/password

### 1.3 System Configuration
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y software-properties-common
```

---

## 2. Install Development Tools

### 2.1 Core Dependencies
```bash
sudo apt install -y \
  git cmake pkg-config \
  libssl-dev libclang-dev \
  build-essential libpq-dev \
  curl protobuf-compiler
```

### 2.2 Rust Toolchain
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
source $HOME/.cargo/env
rustup default stable
rustup update
```

### 2.3 Sui CLI
```bash
cargo install --locked \
  --git https://github.com/MystenLabs/sui.git \
  --branch testnet sui
```

Verify installation:
```bash
sui --version  # Should show 1.18.0 or higher
```

---

## 3. Configure VS Code Environment

### 3.1 Install VS Code
1. [Download VS Code](https://code.visualstudio.com/)
2. Install "Remote - WSL" extension

### 3.2 Essential Extensions
1. Sui Move Analyzer
2. Move Language Support
3. Even Better TOML
4. Rust Analyzer

### 3.3 sui-move-analyzer Setup
```bash
# Download latest binary
wget https://github.com/movebit/sui-move-analyzer/releases/download/v1.1.8/sui-move-analyzer-ubuntu22.04-x86_64-v1.1.8

# Install system-wide
chmod +x sui-move-analyzer-ubuntu22.04-x86_64-v1.1.8
sudo mv sui-move-analyzer-ubuntu22.04-x86_64-v1.1.8 /usr/local/bin/sui-move-analyzer
```

Verify analyzer:
```bash
sui-move-analyzer --version
```

---

## 4. Environment Validation

### 4.1 System Check
```bash
# Verify tool versions
rustc --version
cargo --version
sui --version
git --version
```

### 4.2 Test Sui Configuration
```bash
mkdir sui-test && cd sui-test
sui move new hello_world
cd hello_world && sui move build
```

Expected output:
```
Build Successful
```

---

## 5. Maintenance Tips

### Update Tools
```bash
# Update Rust
rustup update

# Update Sui CLI
cargo install --locked \
  --git https://github.com/MystenLabs/sui.git \
  --branch testnet sui --force
```

### Cleanup
```bash
# Clear build artifacts
cargo clean
sui client purge-network
```

---

## Troubleshooting

**Common Issues**:
- `E: Unable to locate package` → Run `sudo apt update`
- Rust linkage errors → Run `source $HOME/.cargo/env`
- Analyzer not working → Check VS Code extension permissions
- Network errors → Verify WSL internet connection

