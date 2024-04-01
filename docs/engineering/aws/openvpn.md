# Installing the OpenVPN Connect Client on Windows

## Download the Installer
- Visit the download link provided: [OpenVPN Connect v3](https://openvpn.net/downloads/openvpn-connect-v3-windows.msi).
- Click on "Download OpenVPN Connect v3".

## Run the Installer
- Locate the `.msi` file you downloaded and double-click it to start the installation process.

## Installation Assistant
- Follow the instructions in the installation wizard. This usually includes agreeing to the terms of the license agreement and selecting the destination folder for installation.

## Finish Installation
- Once the wizard is finished, click "Finish" to complete the installation.
- More details available at [OpenVPN Connect Client for Windows](https://openvpn.net/client/client-connect-vpn-for-windows/).

## Using the OpenVPN Connect Client to connect to a VPN

## Launch OpenVPN Connect Client
- Look for OpenVPN Connect in the Windows Start menu and open it.

## Import VPN Profile
- On the main interface, click on "Import Profile".
- You have two options:
  - **URL**: Enter the URL provided by your VPN administrator.
  - **FILE**: Drag and drop the `.ovpn` file into the window or click "BROWSE" to locate and select the file on your computer.
- Note: Import the `.ovpn` files generated for Navigator's DEV and PROD connections here.

## Connect to the VPN
- Enter your username and password provided by the VPN administrator.
- Click "Connect" to establish the connection to the VPN server.

## Connection Verification
- Verify that the connection is successful.

## Using the VPN
- With the VPN connected, all your internet activities will go through the VPN.
- To disconnect, open OpenVPN Connect and click Disconnect.

## Profile Management
- Manage multiple VPN profiles within the app.
- To switch between profiles, disconnect from the current VPN and repeat the connection process with the desired profile.



# Getting Started with OpenVPN 3 Linux

OpenVPN 3 Linux is a modern client using the OpenVPN 3 Core Library. It enables unprivileged users to initiate and manage VPN sessions through D-Bus, enhancing privilege separation. This client is optimized for contemporary Linux distributions, but it's compatible with any platform that supports D-Bus.

## Pre-built Packages

OpenVPN 3 Linux v21 offers pre-built packages for various distributions. For production environments, opt for stable releases. Development or beta releases provide more frequent updates.

### Supported Distributions

- Debian (Buster, Bullseye, Bookworm)
- Fedora (37, 38, Rawhide)
- Red Hat Enterprise Linux / CentOS (7, 8, 9)
- Ubuntu LTS (Focal, Jammy)
- Ubuntu (Kinetic, Lunar, Mantic)

## Installation Instructions

### 1. Add the Repository:

For Debian / Ubuntu, start by installing necessary packages:

```bash
sudo apt install apt-transport-https curl
```

### 2. Retrieve and Add the Package Signing Key:

Create a directory for the keyrings, if needed:

```bash
mkdir -p /etc/apt/keyrings 
```

Download and add the OpenVPN Inc package signing key:

```bash
curl -sSfL https://packages.openvpn.net/packages-repo.gpg > /etc/apt/keyrings/openvpn.asc
```

Add the OpenVPN repository to your system's source list:

```bash
echo "deb [signed-by=/etc/apt/keyrings/openvpn.asc] https://packages.openvpn.net/openvpn3/debian [DISTRIBUTION] main" | tee /etc/apt/sources.list.d/openvpn3.list
```

Replace `[DISTRIBUTION]` with your specific Linux distribution release name (e.g., buster, bullseye, bookworm for Debian; focal, jammy for Ubuntu LTS).

### 3. Install OpenVPN 3 Linux:

Update your package list and install OpenVPN 3 Linux:

```bash
sudo apt update 
sudo apt install openvpn3
```

## Using OpenVPN 3 Linux

### Start a One-Shot Configuration Profile:

```bash
openvpn3 session-start --config [config-file.ovpn]
```

### Import a Configuration File for Re-Use:

```bash
openvpn3 config-import --config [config-file.ovpn]
```

### Start a New VPN Session:

```bash
openvpn3 session-start --config [config-file.ovpn]
```

### Manage a Running VPN Session:

Manage sessions with the `openvpn3` command. For example, to disconnect:

```bash
openvpn3 sessions-list 
openvpn3 session-manage --session-path [session-path] --disconnect
```

## Further Information

- For comprehensive instructions, visit the OpenVPN 3 Linux project page and its release notes.
- ARM64/aarch64 architectures are in tech-preview, and feedback from users on this platform is encouraged.
- Fedora Copr repository instructions are available separately for Fedora and Red Hat Enterprise Linux users.
- Note that some architectures may have only tech-preview support or be available in specific repositories.
- This guide provides a general overview. Always refer to the latest official OpenVPN 3 Linux documentation and your distribution's specific guidelines for up-to-date information.
```