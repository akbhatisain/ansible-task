# Ansible Project: Configure CA Certificates and Deploy Python Application


## Introduction
This Ansible project aims to:
1. Configure standard and custom Certificate Authority (CA) certificates on target hosts.
2. Deploy a Python Flask application into a virtual environment.

## Project Structure
The project has the following structure:

Ansible-Assessment/
├── CA1.key
├── CA2.key
├── CA3.key
├── README.md
├── app.py
├── certs
│   ├── CA1.crt
│   ├── CA2.crt
│   └── CA3.crt
├── group_vars
│   └── all.yml
├── inventory
├── playbook.yml
├── roles
│   ├── custom_ca
│   │   ├── files
│   │   │   ├── CA1.crt
│   │   │   ├── CA2.crt
│   │   │   └── CA3.crt
│   │   ├── handlers
│   │   │   └── main.yml
│   │   └── tasks
│   │       └── main.yml
│   ├── deploy_app
│   │   ├── files
│   │   │   └── Example-1.1.1-py3-none-any.whl
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── templates
│   │       ├── app.py.j2
│   │       └── files
│   │           └── app.py
│   └── standard_ca
│       └── tasks
│           └── main.yml
└── test

14 directories, 22 files

## Requirements
- Ansible 2.9 or higher
- Target hosts should be accessible via SSH with appropriate permissions

## Setup Instructions
1. **Clone the repository**:
    ```bash
    git clone <repository_url>
    cd <repository_directory>
    ```

2. **Ensure you have the necessary inventory file**:
    The `inventory` file should list your target hosts. For example:
    ```
    [all]
    192.168.1.100
    192.168.1.101
    ```

3. **Update `group_vars/all.yml`**:
    Set the necessary variables such as `deploy_path`, `app_port`, and `wheel_file`.

    ```yaml
    deploy_path: /opt/example
    app_port: 5000
    wheel_file: Example-1.1.1-py3-none-any.whl
    ```

## Running the Playbook
1. **Run the playbook**:
    ```bash
    ansible-playbook -i inventory playbook.yml
    ```

2. **Monitor the execution**:
    The playbook will:
    - Configure standard CA certificates.
    - Validate and install custom CA certificates.
    - Deploy the Python Flask application into a virtual environment at the specified location.

## Variables
The following variables can be configured in `group_vars/all.yml`:
- `deploy_path`: Path where the Python application will be deployed. Default is `/opt/example`.
- `app_port`: Port on which the Flask application will run. Default is `5000`.
- `wheel_file`: Name of the wheel file for the Flask application. Default is `Example-1.1.1-py3-none-any.whl`.


