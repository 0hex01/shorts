# shorts
shorts - Shortcut management for debian. A handy little GUI tool with cli support that allows you to create, edit, and import (existing) shortcuts. Streamline your bash experience by easily creating cmd-line shortcut versions of long commands. With run in background and passwordlerss options.




## shorts v1.1
## Author / Creator: 0hex01 <0hex01@primarymail.org>
## License
GNU General Public License v3.0

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>. Contact <rtfm@labor.dis> for more bs.lite info.

A powerful system-wide shortcut manager for Linux systems that simplifies command execution through an intuitive GUI and CLI interface. Shorts allows you to create, manage, and execute system commands through easy-to-remember shortcuts, eliminating the need to remember complex command sequences.

Designed specifically for Kali Linux and other Debian-based systems, Shorts integrates seamlessly with your system's security model, providing options for both regular and privileged command execution.

Created by: 0hex01

## Features

### Core Functionality
- Create and manage system-wide command shortcuts
- Execute complex commands with simple, memorable names
- Persistent storage of shortcuts across system reboots
- Comprehensive logging of all shortcut operations

### User Interface
- Modern, dark-themed GUI interface built with customtkinter
- Full-featured command-line interface for scripting and automation
- Real-time shortcut management and execution
- Intuitive search functionality for finding shortcuts

### Advanced Features
- Background execution mode using nohup for long-running commands
- Passwordless sudo execution with secure sudoers.d integration
- Automatic script generation with proper permissions
- Error handling and detailed logging

### Security
- Secure storage of shortcuts in user's home directory
- Proper permission management for generated scripts
- Optional sudo integration with secure configuration
- Input validation and sanitization

## System Requirements

### Minimum Requirements
- Linux-based operating system (Debian/Ubuntu/Kali)
- Python 3.8 or higher
- 50MB free disk space
- Basic system utilities (bash, sudo)

### Dependencies
- python3-tk: GUI toolkit
- python3-pip: Python package manager
- python3-venv: Python virtual environment
- customtkinter: Modern UI components

## Installation

### Method 1: Using the Installer Script

```bash
# Clone the repository
git clone https://github.com/0hex01/shorts.git
cd shorts

# Run the installer
sudo ./install.sh
```

### Method 2: Using the Debian Package

```bash
# Download the package
wget https://github.com/0hex01/shorts/releases/download/v1.1/shorts-1.1-kali.deb

# Install the package
sudo dpkg -i shorts-1.1-kali.deb
sudo apt-get install -f  # Install dependencies if needed
```

## Usage

### Understanding Shortcuts
A shortcut in Shorts consists of three main components:
1. **Name**: A unique, memorable identifier (e.g., 'backup', 'update')
2. **Command**: The actual system command to execute
3. **Options**: Additional settings like background execution or sudo access

### GUI Mode
```bash
# Launch the GUI
shorts
```

### CLI Mode
```bash
# View all options
shorts --help

# List all shortcuts
shorts -l

# Create a shortcut
shorts -c myshort -m "command to run"

# Create a background shortcut
shorts -c server -m "python app.py" -b

# Create a passwordless sudo shortcut
shorts -c update -m "apt update" -p

# Delete a shortcut
shorts -d myshort

# Search shortcuts
shorts -s keyword
```

## System Integration

### File Locations
- **Shortcuts Database**: `~/.shortcuts.json`
  - Stores all shortcut definitions
  - JSON format for easy parsing
  - User-specific storage for security

- **Generated Scripts**: `/usr/local/bin/`
  - System-wide accessible location
  - Proper execute permissions
  - Named after shortcut identifiers

- **Log Files**: `/var/log/shorts/shorts.log`
  - Detailed operation logging
  - Error tracking and debugging
  - Rotation-enabled for space management

- **Configuration**: `/etc/shorts/`
  - System-wide configuration
  - Sudo rules and permissions
  - Default settings

### Security Considerations
- Scripts are owned by root:root
- Shortcuts database is user-owned
- Sudo rules are properly confined
- Input validation prevents injection

## Dependencies

- Python 3.8 or higher
- python3-tk
- python3-pip
- customtkinter

## Development

### Setting Up Development Environment
```bash
# Clone the repository
git clone https://github.com/0hex01/shorts.git
cd shorts

# Create virtual environment
python3 -m venv venv
source venv/bin/activate

# Install development dependencies
pip install -r requirements-dev.txt
```

### Running Tests
```bash
# Run unit tests
python -m pytest tests/unit

# Run integration tests (requires sudo)
sudo python -m pytest tests/integration

# Run with coverage
python -m pytest --cov=shorts tests/
```

### Building Packages
```bash
# Build Debian package
./build_deb.sh

# Create source distribution
python setup.py sdist

# Create wheel distribution
python setup.py bdist_wheel
```



Created by: 0hex01

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request
