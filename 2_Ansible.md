# Ansible and Essential Linux Commands

## Introduction
Ansible is an open-source automation tool that simplifies cloud provisioning, configuration management, application deployment, and intra-service orchestration. This document combines essential Linux commands with Ansible concepts to aid in your preparation for Ceph training.

## What is Ansible?
Ansible allows you to automate IT processes using a declarative language to describe the desired state of systems. It connects to target machines over SSH, executing necessary commands to achieve that state.

## Ansible Architecture
Ansible consists of the following key components:
- **Control Node:** The machine where Ansible is installed and from which automation is executed.
- **Managed Nodes:** The target machines that Ansible manages.
- **Inventory:** A list of managed nodes that Ansible can connect to.
- **Modules:** Reusable units of code that perform specific tasks.
- **Playbooks:** YAML files that define the desired state of managed nodes.

## Ansible Playbook Structure
Ansible Playbooks are structured in YAML and consist of several key elements:
- **Hosts:** The target hosts or groups to be configured.
- **Tasks:** Actions to be performed on the target hosts.
- **Variables:** Data used throughout the playbook.
- **Handlers:** Actions triggered by changes in the system.

### Example Playbook Structure
Here’s a simple example of a playbook structure:

```yaml
- hosts: all
  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present
```

### Ansible Roles
Ansible Roles help to organize Playbooks into reusable components, making them modular and maintainable. They allow you to encapsulate tasks, handlers, variables, and files.

### Creating an Ansible Playbook Example
Let's create a playbook with two plays to perform specific tasks.

Playbook Overview
    - Play 1:
        - Execute a command on host1
        - Execute a script on host1

    - Play 2:
        - Execute a script on host2
        - Install Nginx on host2

Here’s how the playbook would look:
```yaml
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
```

### Setting up the Master and Slave Nodes
To set up Ansible for managing nodes, follow these steps:

- Install Ansible on the Master Node: This is the control node where Ansible will be executed.
- Configure the Inventory: Create an inventory file listing the IP addresses or hostnames of the target machines.
- Configure SSH Access: Set up SSH key-based authentication for passwordless access to slave nodes.
- Test the Connection: Use the following command to test connectivity:

`ansible -m ping all`

### Popular Ansible Commands
Here are some commonly used Ansible commands:

- `ansible -m ping <host>`: Ping a server to check if it is accessible.
- `ansible-playbook <playbook.yml>`: Execute an Ansible Playbook.
- `ansible-vault encrypt <file>`: Encrypt a file containing sensitive data.
- `ansible-galaxy init <role_name>`: Create a new Ansible role.
- `ansible-config dump`: Display the current Ansible configuration.