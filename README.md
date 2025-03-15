# DB Role

This role creates and manages an AWS RDS MySQL instance and its associated subnet group. It also sets facts for the RDS endpoint and other outputs.

## Requirements

- **Ansible**: Version 2.9 or higher.
- **AWS Credentials**: Configured on the target machine (e.g., using `aws configure` or environment variables).
- **Python Dependencies**:
  - `boto3` and `botocore` (required for AWS modules).
  - Install them using:
    ```bash
    pip install boto3 botocore
    ```
- **Ansible Collections**:
  - `community.aws` (for AWS modules).
  - Install it using:
    ```bash
    ansible-galaxy collection install community.aws
    ```

## Role Variables

### Default Variables (defined in `vars/main.yml`)
- `aws_region`: The AWS region where the RDS instance will be created. Default: `"us-east-1"`.
- `db_instance_identifier`: The identifier for the RDS instance. Default: `"mydatabase"`.
- `engine`: The database engine. Default: `"mysql"`.
- `engine_version`: The database engine version. Default: `"8.0"`.
- `db_instance_class`: The instance class for the RDS instance. Default: `"db.t3.micro"`.
- `allocated_storage`: The allocated storage size in GB. Default: `20`.
- `username`: The master username for the RDS instance. Default: `"admin"`.
- `password`: The master password for the RDS instance (encrypted using Ansible Vault).
- `db_name`: The name of the database to create. Default: `"todos"`.
- `sg_name`: The name of the security group for the RDS instance. Default: `"WebSG"`.
- `db_subnet_group_name`: The name of the RDS subnet group. Default: `"my-rds-subnet-group"`.

### Output Variables (Set as Facts)
- `RDS_ENDPOINT`: The endpoint address of the RDS instance.

## Dependencies

This role does not depend on any other roles. However, it requires the following:
- The `community.aws` collection (installed via Ansible Galaxy).
- AWS credentials configured on the target machine.
