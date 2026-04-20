# 💾 Ansible
[![Static Badge](https://img.shields.io/badge/Linux-white?style=flat&logo=linux&logoColor=white&logoSize=auto&labelColor=black)](https://www.linux.org/)
[![Static Badge](https://img.shields.io/badge/Ansible-Automation-white?style=flat&logo=ansible&logoColor=white&logoSize=auto&labelColor=black)](https://docs.ansible.com/)
[![Static Badge](https://img.shields.io/badge/GPL-V3-white?style=flat&logo=gnu&logoColor=white&logoSize=auto&labelColor=black)](https://www.gnu.org/licenses/gpl-3.0.en.html/)

Ansible, a suite of software tools that enables infrastructure as code.

📖 [Ansible Documentation](https://docs.ansible.com/)

Ansible playbooks for my personal use. Tested in my production environment.
- **Servers** —  Debian based systems
- **Laptop** — Arch based systems


## ✨ Features

- **Package Management** — Install, remove, and update packages via apt
- **Service Control** — Start, stop, and restart systemd services
- **System Operations** — Reboot, shutdown, and gather system info
- **Multi-host Support** — Target single hosts, groups, or patterns with `--limit`

## 🚀 Quick Start

### Prerequisites

**On target servers:**
```sh
sudo apt install openssh-server
```

**On Ansible host (Arch Linux):**
```sh
pacman -S ansible-core
```

### Verify connectivity
```sh
ansible all -m ping --limit <HOST>
```

### Usage Examples

```sh
# Update and upgrade servers
ansible-playbook apt-update_pb.yml --limit webservers -K

# Install packages
ansible-playbook apt-install_pb.yml --limit pi -K -e "packages=['htop','curl']"

# Remove packages
ansible-playbook apt-remove_pb.yml --limit dbservers -K -e "packages=nginx"

# Restart a service
ansible-playbook service-restart_pb.yml --limit mail -K -e "service=postfix"

# Get system info
ansible-playbook system-info_pb.yml --limit deadpool

# Dry run (check mode)
ansible-playbook apt-update_pb.yml --limit all -K --check
```

## 🔧 Configuration

### Ansible Options

| Flag | Description |
|------|-------------|
| `-K` | Prompt for sudo password |
| `-i` | Path to inventory file |
| `--limit` | Target specific hosts/groups |
| `--check` | Dry run (no changes) |
| `-e` | Pass extra variables |

### List inventory
```sh
ansible-inventory --graph -i hosts
```

## 📝 Directory Structure

```
ansible/
├── apt-install_pb.yml    # Install packages
├── apt-remove_pb.yml     # Remove packages
├── apt-update_pb.yml     # Update & upgrade system
├── ping_pb.yml           # Test connectivity
├── ping-all_pb.yml       # Ping all hosts
├── reboot_pb.yml         # Reboot servers
├── shutdown_pb.yml       # Shutdown servers
├── service-start_pb.yml  # Start services
├── service-stop_pb.yml   # Stop services
├── service-restart_pb.yml# Restart services
└── system-info_pb.yml    # Display system information
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 🆘 Support

If you encounter any issues or need support, please file an issue on the GitHub repository.

## 📄 License

This project is licensed under the GNU GENERAL PUBLIC LICENSE v3.0 - see the [LICENSE](LICENSE) file for details.