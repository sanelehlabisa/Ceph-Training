# Ansible and Essential Linux Commands

## What is Ansible?
Ansible is an open-source software tool for automating cloud provisioning, configuration management, application deployment, intra-service orchestration, and many other IT processes.

## How does Ansible work?
- Ansible uses a declarative language to describe the desired state of a system. 
- It connects to target systems over SSH and executes commands to achieve the desired state.

## Ansible Architecture
- **Control Node:** The machine where Ansible is installed and from where automation is executed.
- **Managed Nodes:** The target machines that Ansible manages.
- **Inventory:** A list of managed nodes that Ansible can connect to.
- **Modules:** Reusable units of code that perform specific tasks.
- **Playbooks:** YAML files defining the desired state of managed nodes.

## Ansible Playbook Structure
Ansible Playbooks are written in YAML and consist of:
- **Hosts:** Target hosts or groups to configure.
- **Tasks:** Actions to be performed on the target hosts.
- **Variables:** Data used throughout the playbook.
- **Handlers:** Actions triggered by changes in the system.

### Example Playbook Structure
```yaml
- hosts: all
  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present
Ansible Roles
Ansible Roles organize Playbooks into reusable components, keeping them modular and maintainable.

Popular Ansible Commands
ansible-playbook: Executes an Ansible Playbook.
ansible-inventory: Displays inventory information.
ansible-vault: Encrypts/decrypts sensitive data.
ansible-galaxy: Manages Ansible Roles and Collections.
ansible-config: Displays and manages Ansible configuration.
Creating an Ansible Playbook Example
Playbook Example
To create a playbook with two plays:

Play 1:

Execute a command on host1
Execute a script on host1
Play 2:

Execute a script on host2
Install Nginx on host2
Example Playbook
Copy
- hosts: host1
  tasks:
    - name: Execute a command
      command: echo "Hello from host1"
      
    - name: Execute a script
      script: /path/to/script.sh

- hosts: host2
  tasks:
    - name: Execute a script
      script: /path/to/script.sh
      
    - name: Install Nginx
      apt:
        name: nginx
        state: present
Setting up the Master and Slave Nodes
Install Ansible on the Master Node: Install Ansible on the control node.
Configure the Inventory: Create an inventory file listing the IP addresses or hostnames of target machines.
Configure SSH Access: Set up SSH key-based authentication for passwordless access.
Test the Connection: Use ansible -m ping all to test connectivity between the master and slave nodes.
Popular Ansible Commands
ansible -m ping <host>: Ping a server to check accessibility.
ansible-playbook <playbook.yml>: Execute an Ansible Playbook.
ansible-vault encrypt <file>: Encrypt a file containing sensitive data.
ansible-galaxy init <role_name>: Create a new Ansible role.
ansible-config dump: Display the current Ansible configuration.