# Ansible AWS Automation

## Overview
This project utilizes Ansible playbooks to automate the creation and management of AWS resources. By defining infrastructure as code, we can easily manage, version control, and reproduce our infrastructure. The goal of this project is to streamline the provisioning and maintenance of AWS resources using Ansible. This includes the creation and management of EC2 instances, VPCs, subnets, security groups, and other essential AWS infrastructure components.

## Features

- Ability to scale infrastructure resources up or down easily.
- Encrypted credentials using Ansible Vault.
- Support for multiple AWS regions and availability zones.
- Support for tagging resources for better organization and management.
- Error handling and reporting for better troubleshooting.

## Implementation

### Prerequisites
- Ansible installed on your local machine.
- AWS CLI configured with appropriate credentials.
- Python libraries `boto3` and `botocore` installed.

### Files
- `ec2_playbook.yml`: The main playbook that defines the tasks for creating and managing AWS resources.
- `secrets.yml`: A file for storing AWS credentials, encrypted using Ansible Vault.
- `dynamic_inventory_aws_ec2.yaml`: A dynamic inventory configuration file for managing AWS EC2 instances.
- `ansible.cfg`: Ansible configuration file for setting default behaviors and paths.

### Steps to Run the Playbook

1. **Encrypt the `secrets.yml` file**:
   ```sh
   ansible-vault encrypt secrets.yml
   ```
2. **Run the playbook**:
   ```sh
   ansible-playbook ec2_playbook.yml --ask-vault-pass
   ```

### Inventory Management
The project utilizes a dynamic inventory configuration (`dynamic_inventory_aws_ec2.yaml`) to automatically discover and manage AWS EC2 instances. This configuration groups instances based on various criteria such as region, environment, and operating system.

### Example Output
After running the playbook, you can verify the created resources and their groupings using the following command:
```sh
ansible-inventory -i dynamic_inventory_aws_ec2.yaml --graph
```

## Conclusion
This project showcases how Ansible can be used to automate the management of AWS infrastructure. By treating infrastructure as code, we can achieve consistent and reproducible deployments, simplifying the management and scalability of our AWS resources.
