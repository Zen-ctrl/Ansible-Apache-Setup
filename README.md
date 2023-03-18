# Apache Installation and Configuration Playbook

This Ansible playbook installs and configures the Apache web server on target hosts based on their operating system (OS). It ensures the Apache service is enabled and running, and configures it to listen on ports 80 and 443.

## Prerequisites

- Ansible installed on the control node.
- SSH access to the target hosts with an appropriate user that can escalate privileges using sudo.

## Directory Structure

```

├── install_apache.yml

└── vars

├── Debian.yml


└── RedHat.yml
```



```

- `install_apache.yml`: The main Ansible playbook file.

- `vars/`: Directory containing OS-specific variables.

  - `Debian.yml`: Variables specific to Debian-based systems.
  
  - `RedHat.yml`: Variables specific to Red Hat-based systems.
```


## Usage

1. Clone the repository or copy the playbook files to the Ansible control node.
2. Create an inventory file (e.g., `inventory.ini`) with the target hosts listed under the appropriate groups or as individual hosts.

Example inventory file (`inventory.ini`):




- `install_apache.yml`: The main Ansible playbook file.
- `vars/`: Directory containing OS-specific variables.
  - `Debian.yml`: Variables specific to Debian-based systems.
  - `RedHat.yml`: Variables specific to Red Hat-based systems.

## Usage

1. Clone the repository or copy the playbook files to the Ansible control node.
2. Create an inventory file (e.g., `inventory.ini`) with the target hosts listed under the appropriate groups or as individual hosts.

Example inventory file (`inventory.ini`):

```yaml
[web_servers]

web_server_1.example.com

web_server_2.example.com
```

3. Run the playbook using the following command:

```bash
ansible-playbook -i inventory.ini install_apache.yml
```
Replace inventory.ini with the name of your inventory file.

## Playbook Overview
The install_apache.yml playbook consists of the following tasks:

1. Include OS-specific variables: Includes the variable file that corresponds to the target host's OS family (e.g., vars/RedHat.yml or vars/Debian.yml).
2. Install Apache: Installs the Apache package using the package manager specific to the detected OS.
3. Ensure Apache service is enabled and started: Enables and starts the Apache service on the target host.
4. Configure Apache to listen on ports 80 and 443: Modifies the Apache configuration file to listen on ports 80 and 443.
5. Reload Apache service: Reloads the Apache service to apply the changes.

Contributing
Feel free to submit issues or pull requests to improve the playbook or add support for more operating systems.
