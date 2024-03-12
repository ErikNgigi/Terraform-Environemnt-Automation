# Terraform Decoded: Automating Your Setup Environment for Efficiency

This shell script is designed to create a specific directory structure for managing infrastructure code, specifically tailored for projects utilizing Terraform for infrastructure provisioning. The script prompts the user to create a root directory and then generates the required directories and files within it. Below is an explanation of its functionality:

## Directory Structure

The script generates the following directory structure:

- **Documentation**: Directory for storing documentation files.
- **Environment**: (Optional) Directory for managing different environment setups such as development, staging, and production.
- **Infrastructure**: Directory for housing Terraform configuration files.
    - **Modules**: Directory for storing Terraform modules.
        - **Containers**: Directory for container-related Terraform modules.
        - **Instances**: Directory for instance-related Terraform modules.
        - **Database**: Directory for database-related Terraform modules.
        - **Management**: Directory for management-related Terraform modules.
        - **Network**: Directory for network-related Terraform modules.
        - **Notifications**: Directory for notification-related Terraform modules.
        - **Scaling**: Directory for scaling-related Terraform modules.
        - **Security**: Directory for security-related Terraform modules.
        - **Storage**: Directory for storage-related Terraform modules.
        - **Templates**: Directory for storing Terraform template files.
- **Files**: Directory for storing miscellaneous files.

```markdown
|-- terraform-projects
    |-- .gitignore
    |-- README.md
    |-- directoryList.md
    |-- documentation
    |-- files
    |   |-- two-tier-architecture.mdj
    |-- infrastructure
        |-- main.tf
        |-- outputs.tf
        |-- provider.tf
        |-- terraform.tfvars
        |-- variables.tf
        |-- modules
            |-- containers
            |   |-- main.tf
            |   |-- outputs.tf
            |   |-- variables.tf
            |   |-- versions.tf
            |   |-- templates
            |       |-- app.json.tpl
            |-- database
            |-- instances
            |   |-- main.tf
            |   |-- outputs.tf
            |   |-- variables.tf
            |   |-- versions.tf
            |-- management
            |   |-- main.tf
            |   |-- outputs.tf
            |   |-- variables.tf
            |   |-- versions.tf
            |-- network
            |   |-- main.tf
            |   |-- outputs.tf
            |   |-- variables.tf
            |   |-- versions.tf
            |-- notifications
            |   |-- main.tf
            |   |-- outputs.tf
            |   |-- variables.tf
            |   |-- versions.tf
            |   |-- templates
            |       |-- email-sns-stack.json.tpl
            |-- scaling
            |   |-- main.tf
            |   |-- outputs.tf
            |   |-- variables.tf
            |-- security
            |   |-- main.tf
            |   |-- outputs.tf
            |   |-- variables.tf
            |   |-- versions.tf
            |   |-- templates
            |       |-- ecs-ec2-role-policy.json.tpl
            |       |-- ecs-ec2-role.json.tpl
            |       |-- ecs-service-role.json.tpl
            |-- storage
                |-- main.tf
                |-- outputs.tf
                |-- variables.tf
                |-- versions.tf
```

## Terraform Configuration Files

For each module, the script generates the following Terraform configuration files:

- **main.tf**: Main Terraform configuration file.
- **outputs.tf**: File for defining output variables.
- **variables.tf**: File for defining input variables.
- **versions.tf**: File for specifying Terraform version constraints.

Additionally, for certain modules, the script creates a **templates** directory for storing Terraform template files.

## Provider Configuration

The script appends provider configuration information to the `provider.tf` file within the **Infrastructure** directory. It configures the AWS provider with the specified region and profile.

## Usage

1. Clone the Repository: Clone this repository to your local machine.

```bash
```

2. Navigate to the Script: Using a terminal, navigate to the directory where the script is located.
3. Make the Script Executable: If necessary, make the script executable by running chmod +x script_name.sh.
4. Run the Script: Execute the script by running ./script_name.sh.
5. Follow the Prompts: The script will prompt you to create a root directory and provide a name for it. Only letters, numbers, hyphens (-), and underscores (_) are allowed in the directory name.
6. Confirmation: Upon successful execution, the script will display a confirmation message indicating that the directory structure has been created.

Note: If a directory with the provided name already exists, the user is prompted to enter a new directory name.

Feel free to modify the script as needed to suit your specific requirements.

## Excluding Specific Files and Folders in Git

To enhance security and adhere to best practices when using Git with Terraform, it's crucial to exclude certain files and directories that contain sensitive information or are not relevant for version control. The following script demonstrates how to create a .gitignore file tailored for Terraform projects:

```bash
#!/bin/bash

# create terraform gitignore file
touch .gitignore

# append details to the gitignore file
cat <<EOF >> .gitignore
# Local .terraform directories
**/.terraform/*

# .tfstate files
*.tfstate
*.tfstate.*

# Crash log files
crash.log
crash.*.log

# Exclude all .tfvars files, which are likely to contain sensitive data, such as
# password, private keys, and other secrets. These should not be part of version 
# control as they are data points which are potentially sensitive and subject 
# to change depending on the environment.
*.tfvars
*.tfvars.json

# Ignore override files as they are usually used to override resources locally and so
# are not checked in
override.tf
override.tf.json
*_override.tf
*_override.tf.json

# Include override files you do wish to add to version control using negated pattern
# !example_override.tf

# Include tfplan files to ignore the plan output of command: terraform plan -out=tfplan
# example: *tfplan*

# Ignore CLI configuration files
.terraformrc
terraform.rc
EOF

# output message
echo "Terraform Gitignore Created Succesfully"
```

## Explanation:

1. Local .terraform Directories: Excludes local Terraform directories that are created during initialization and execution.
2. .tfstate Files: Ignores Terraform state files which contain sensitive information about the infrastructure managed by Terraform.
3. Crash Log Files: Excludes crash log files generated during execution.
4. .tfvars Files: Excludes variables files which often contain sensitive data like passwords or private keys.
5. Override Files: Ignored as they're typically used for local resource overrides.
6. CLI Configuration Files: Excludes Terraform CLI configuration files.

## Usage
1. Clone the Repository: Clone this repository to your local machine.

```bash
```

2. Navigate to the Script: Using a terminal, navigate to the directory where the script is located.

```bash
```

3. Make the Script Executable: If necessary, make the script executable by running chmod +x script_name.sh.

```bash
```

4. Run the Script: Execute the script by running ./script_name.sh

```bash
```

By adding these rules to your .gitignore file, you ensure that sensitive information is not inadvertently added to version control, promoting security and best practices in your Terraform projects.
