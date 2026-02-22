Minimal Server Menu (Ubuntu 24.04) — Program Description

Minimal Server Menu is a non-graphical, terminal-based administration tool designed for minimal Ubuntu Server 24.04 installations. It provides an installer-style text UI (arrow keys, Enter to select, Space to toggle) built with dialog, allowing administrators to perform common server setup and maintenance tasks quickly and consistently—without requiring any desktop environment (no X11, GNOME, or GUI dependencies).

Key Capabilities

1) Installer-style Text Menu Interface

Launches as an interactive TUI application.

Uses a custom color theme to present a clean, readable layout:

Full blue background/top bar

Light menu interiors (no dark “holes”)

No shadows for clarity on server consoles and SSH terminals

2) Full Logging to ./error.log

Redirects all stdout/stderr output and error messages into ./error.log (or a fallback log location if the current directory is not writable).

Adds structured log headers including start time, user, working directory, and terminal info.

Captures unexpected failures with line numbers and the last executed command for troubleshooting.

3) Safe Startup Validation

Ensures the program runs only in a proper interactive terminal (TTY).

Automatically fixes terminal type issues (e.g., TERM=dumb) to prevent dialog from failing and exiting.

4) Hostname Management (Immediate Apply)

Allows changing the system hostname at any time from the menu.

Applies changes immediately using hostnamectl (static and transient hostnames).

Updates /etc/hosts to ensure the system resolves the new hostname correctly (especially 127.0.1.1 mapping).

5) Batch Software Installation (Multi-select)

Provides software groups and profiles that can be selected with a checklist interface.

Builds a batch install list so multiple packages can be installed in one operation.

Includes curated sets for common minimal server needs:

Web servers (nginx, apache2)

Language stacks (Python 3, PHP, Perl)

Editors (joe, nano, vim)

Developer toolchains (C/C++ build tools, debugging tools, common dev libraries)

System utilities, networking tools, monitoring tools

Supports viewing and clearing the batch before installation.

6) Git Setup Assistant

Detects whether Git is installed and can install it if missing.

Helps configure essential global Git settings:

user.name, user.email

default initial branch name (e.g., main)

Provides credential helper options appropriate for servers:

none (recommended for most servers)

cache in memory (timeout-based)

store (unencrypted, persistent)

7) Firewall (UFW) Administration

Includes a guided firewall menu for easy rule management.

Supports:

enable/disable firewall safely

setting default policies (deny incoming/allow outgoing, etc.)

allowing common services (SSH/HTTP/HTTPS)

allowing custom ports (tcp/udp/both)

viewing numbered rules and deleting by rule number

8) Service Management (systemctl)

Provides a service manager for common services (e.g., ssh, nginx, apache2, php-fpm, fail2ban, ufw).

Allows:

start/stop/restart

enable/disable at boot

view systemd status

view recent logs via journalctl

9) Config Shortcuts (Smart Detection)

Automatically offers configuration shortcuts based on installed packages/services.

Examples:

Edit nginx/apache/ssh configs using $EDITOR (fallback nano)

List enabled sites directories

Run configuration tests (e.g., nginx -t, apachectl -t, sshd -t)

10) Security Hardening Tools

Includes practical “baseline hardening” actions for minimal servers:

enable unattended upgrades

install/enable Fail2ban with a basic SSH jail

SSH hardening wizard:

set SSH port

optionally disable root login

optionally disable password authentication (keys-only)

validates config with sshd -t and creates backups before applying
