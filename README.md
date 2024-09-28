# Nomadnet, Reticulum, and Tailscale Installation Playbook

This Ansible playbook automates the installation of Nomadnet, Reticulum, and Tailscale on a Raspberry Pi running Debian Bookworm.

## Prerequisites

- Ansible installed on your control machine
- SSH access to the target Raspberry Pi
- Tailscale account and authkey

## Playbook Overview

This playbook performs the following tasks:

1. Updates and upgrades apt packages
2. Installs required system packages
3. Creates a Python virtual environment
4. Installs Nomadnet and its dependencies in the virtual environment
5. Adds Tailscale repository and installs Tailscale
6. Configures and starts Tailscale service
7. Creates and configures systemd services for Nomadnet daemon and Message Board

## Usage

1. Clone this repository or copy the playbook to your local machine.

2. Update the `hosts` field in the playbook to target your Raspberry Pi.

3. Set the Tailscale authkey in the `vars` section:

   ```yaml
   vars:
     tailscale_authkey: "tskey-auth-YOUR-KEY-HERE"
4. Run the playbook:

    ```bash
    ansible-playbook -i your_inventory_file nomadnet_tailscale_playbook.yml
    ```

Replace your_inventory_file with the path to your Ansible inventory file.

## Post-Installation
After running the playbook:

1. Nomadnet daemon and Message Board services will be running and enabled to start on boot.

## Customization
- You can modify the virtual environment path by changing the venv_path variable.
- Adjust the systemd service configurations if needed.

## Notes
This playbook assumes you're using the ansible user on the Raspberry Pi. Modify the user in the systemd service files if necessary.
