# SSH Configuration and Keys

## 📋 Overview
Secure Shell (SSH) configuration for secure remote access, key management, and connection optimization.

## 🎯 Purpose
Set up secure, passwordless authentication to remote servers and configure SSH client settings for improved security and convenience.

## 💻 Command/Configuration

### SSH Key Generation
```bash
# Generate a new SSH key pair
ssh-keygen -t ed25519 -C "your_email@example.com"

# Generate RSA key (if ed25519 not supported)
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

# Generate key with specific filename
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519_work -C "work_email@company.com"
```

### SSH Configuration (~/.ssh/config)
```bash
# Global settings
Host *
    AddKeysToAgent yes
    UseKeychain yes
    IdentitiesOnly yes

# Specific server configuration
Host myserver
    HostName server.example.com
    User myusername
    Port 22
    IdentityFile ~/.ssh/id_ed25519
    ForwardAgent yes

# Jump host configuration
Host internal-server
    HostName 192.168.1.100
    User admin
    ProxyJump bastion.example.com
```

### Key Management
```bash
# Copy public key to remote server
ssh-copy-id user@server.example.com

# Manual key copying
cat ~/.ssh/id_ed25519.pub | ssh user@server "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"

# Add key to SSH agent
ssh-add ~/.ssh/id_ed25519

# List loaded keys
ssh-add -l

# Remove all keys from agent
ssh-add -D
```

## ⚙️ Options & Parameters
- `-t`: Specify key type (ed25519, rsa, ecdsa, dsa)
- `-b`: Number of bits in the key (for RSA)
- `-C`: Comment to identify the key
- `-f`: Specify output filename
- `-N`: Provide passphrase on command line

## 🔍 Key Points
- Use Ed25519 keys for better security and performance
- Always use strong passphrases for private keys
- Keep private keys secure (never share them)
- Use different keys for different purposes (work, personal, etc.)
- Regularly rotate SSH keys

## ⚠️ Warnings/Gotchas
- Never share private keys (.ssh/id_* files without .pub extension)
- Backup your keys securely
- ~/.ssh directory should have 700 permissions
- Private keys should have 600 permissions
- authorized_keys file should have 600 permissions

## 🔗 Related Topics
- [[Linux/Security/Firewall Configuration]]
- [[Linux/System-Config/User Management]]
- [[Linux/Networking/Remote Access]]

## 📚 References
- `man ssh` - SSH client manual
- `man ssh-keygen` - Key generation manual
- [SSH Academy](https://www.ssh.com/academy/)

## 🏷️ Tags
`#ssh` `#security` `#authentication` `#remote-access` `#config`

---
*Created: 2024-01-15 | Last Updated: 2024-01-15*