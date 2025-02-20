```markdown
# Agent Installation

The Agent can run on local hosts (Linux, Windows, MacOS), containerized environments (Docker, Kubernetes), and on-premise data centers. You can manage the Agent's operating status, start/stop, upgrade, and uninstall through the full interface.

## Linux Agent Installation

The supported Linux operating systems and their corresponding CPU architectures are as follows:

Supported: ✅, Not Supported: ✖️, Unverified: ❓

| Operating System             | Processor Architecture      | Support Status | Keta-Agent Supported Versions | APM Auto Injection | Remarks                                  |
|------------------------------|-----------------------------|----------------|--------------------------------|--------------------|------------------------------------------|
| Kylin (银河麒麟) V10         | x86_64                      | ✅             | v1.3.3.2 ~ newest             | ✅                 |                                          |
| Kylin (银河麒麟) V10         | aarch64                     | ✅             | v1.3.3.2 ~ newest             | ✅                 |                                          |
| Kylin (银河麒麟) V10         | Haiguang (based on x86_64)  | ✅             | v1.3.3.2 ~ newest             | ❓                 |                                          |
| Kylin (银河麒麟) V10         | Kunpeng (based on aarch64)  | ✅             | v1.3.3.2 ~ newest             | ✅                 |                                          |
| CentOS/RHEL6.x               | x86_64, aarch64             | ✅             | v1.3.4.2 ~ newest             | ✖️                 | Ensure "link data collection" is turned off during installation |
| CentOS/RHEL7.x               | x86_64                      | ✅             | v1.2.3 ~ newest               | ✅                 |                                          |
| CentOS8.x                    | x86_64, aarch64             | ✅             | v1.2.3 ~ newest               | ✅                 |                                          |
| RHEL8.x                      | x86_64, aarch64             | ✅             | v1.2.3 ~ newest               | ✖️                 |                                          |
| Ubuntu14.04                  | x86_64                      | ✅             | v1.2.3 ~ newest               | ✅                 |                                          |
| Ubuntu16.04                  | x86_64                      | ✅             | v1.2.3 ~ newest               | ✅                 |                                          |
| Ubuntu18.04                  | x86_64                      | ✅             | v1.2.3 ~ newest               | ✅                 |                                          |
| Ubuntu20.04                  | x86_64, aarch64             | ✅             | v1.2.3 ~ newest               | ✅                 |                                          |
| Ubuntu22.04                  | x86_64, aarch64             | ✅             | v1.2.3 ~ newest               | ✅                 |                                          |
| Debian7.4                    | x86_64                      | ✅             | v1.2.3 ~ newest               | ✅                 |                                          |
| Debian8.11                   | x86_64                      | ✅             | v1.2.3 ~ newest               | ✅                 |                                          |
| Debian9.0                    | x86_64                      | ✅             | v1.2.3 ~ newest               | ✅                 |                                          |
| Debian10.12                  | x86_64                      | ✅             | v1.2.3 ~ newest               | ✅                 |                                          |
| Debian11.4                   | x86_64                      | ✅             | v1.2.3 ~ newest               | ✅                 |                                          |
| Debian12.0                   | x86_64                      | ✅             | v1.2.3 ~ newest               | ✅                 |                                          |
| Debian12.0                   | aarch64                     | ✅             | v1.2.3 ~ newest               | ✅                 |                                          |

Linux supports both manual and automatic installations:
- **Manual Installation**: Install a new Agent on the machine via an installation script. You can choose or create tags, fill in the network card name, and choose whether to enable auto-start (the installing user must have root privileges). You can click to get the installation password command and install on the corresponding machine.
- **Automatic Installation**: Install the Agent automatically via SSH connection. The machine must have SSH enabled, and its IP must be accessible to the Agent service.

### Manual Installation
Install a new client manually on the machine via an installation script. You can choose or create tags, fill in the network card name, and choose whether to enable auto-start (the installing user must have root privileges). After clicking to get the installation command, you can install it on the corresponding machine.

Installation steps are as follows:

1. Go to **Machine Management > Add Machine**
2. Choose Linux > Manual Installation, and complete the following configuration to get the installation command:
   ![Select Machine]( /appassets/keta_docs/image/static/assets/agent_machine/197d9258-3300-4df8-aeb2-8e59726cd613.png)

| Configuration Item  | Description |
|---------------------|-------------|
| Machine Tag         | Fill in the tags for the machine to be installed with the collection client. Tags serve as client grouping attributes, making it easier to manage machine resources and distribute collection tasks across machine groups. Separate multiple tags with commas. |
| Network Card Name   | Input the network card name. If left blank, the system will automatically detect the available network card. |
| Installation Path   | Specify the installation path for the client. If left blank, the system will install it to the default path: root user: `/usr/local/ketad/agent`, non-root user: `$HOME/ketad/agent`. |
| System Architecture | Choose the system architecture based on the operating system. The default is the latest version. |
| Agent Version       | Choose the version of the Agent to install based on the operating system and architecture. The default is the latest version. |
| Auto-start          | If enabled, the client will automatically start after the server boots. |

3. Click "Get Installation Command," copy the command, and install it on the machine.
4. After installation is complete, go back to the machine management page and refresh to see the added machine.

### Automatic Installation
The Agent can be installed automatically via SSH. The machine must have SSH enabled, and its IP must be accessible to the Agent service.

Installation steps are as follows:

1. Go to **Machine Management > Add Machine**
2. Choose Linux > Automatic Installation, and complete the following configuration:
   ![Linux Manual]( /appassets/keta_docs/image/static/assets/agent_machine/513dc2bb-239b-4998-9580-97ddfda49fc5.png)

| Configuration Item  | Description |
|---------------------|-------------|
| Machine IP          | Fill in the machine's IP address. Separate multiple IPs with commas. |
| Network Card Name   | If the machine has multiple network cards, specify the one to be used. If left blank, the system will automatically detect the available network card. |
| Installation Path   | Specify the installation path for the client. If left blank, the system will install it to the root directory. |
| SSH Port            | Input the SSH port number. If left blank, the default port 22 will be used. |
| Login Method        | Choose the login method: password or SSH key. If password is chosen, enter the username and password. If SSH key is chosen, enter the username and upload the private key file. Steps for generating keys: 1. Use `ssh-keygen -m PEM` to generate the key. 2. Write the public key (`id_rsa.pub`) to `~/.ssh/authorized_keys` on the machine where the Agent will be installed. Upload the private key file (`id_rsa`) to KetaOps. |
| Machine Tag         | Fill in the tags for the machine to be installed with the collection client. Tags serve as client grouping attributes. |
| System Architecture | Choose the system architecture based on the operating system. The default is the latest version. |
| Agent Version       | Choose the version of the Agent to install based on the operating system and architecture. The default is the latest version. |

3. Click "Verify Connectivity" to test SSH connectivity. The Agent can only be installed if the machine is connected.
4. After confirming connectivity, click "Install" to complete the automatic installation. The client installation will take some time. Click "Close" to exit the current page and continue installation in the background. After installation is complete, you can check the installation status in the notification center.
5. Go back to the machine management page and refresh to see the added machine.

Note that the default installation directories for automatic installations are:

- For Linux root users: `/usr/local/ketad/agent`
- For Linux non-root users: `$HOME/ketad/agent` (in the user's home directory).
```