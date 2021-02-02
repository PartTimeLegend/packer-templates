# Packer Templates

HashiCorp Packer is easy to use and automates the creation of any type of machine image. It embraces modern configuration management by encouraging you to use automated scripts to install and configure the software within your Packer-made images. Packer brings machine images into the modern age, unlocking untapped potential and opening new opportunities.

Out of the box Packer comes with support to build images for Amazon EC2, CloudStack, DigitalOcean, Docker, Google Compute Engine, Microsoft Azure, QEMU, VirtualBox, VMware, and more. Support for more platforms is on the way, and anyone can add new platforms via plugins.

## How To

### Firstly install [Chocolatey](https://chocolatey.org) via PowerShell.

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

### Now install Packer 
```powershell
choco install packer -y
```

### Validate Packer Template

```powershell
packer validate -var-file variables.json centos.json
```

### Build Packer Template

```powershell
packer build -var-file variables.json centos.json
```

## Required Files

### variables.json
This file is where the region, vpc, subnet, instance type, naming, and source ami.

#### AWS Example

```json
{
    "aws_region":         "us-east-1",
    "aws_build_vpc":      "vpc-1a2b3c4d",
    "aws_build_subnet":   "subnet-1a2b3c4d",
    "aws_public_ip":      "false",
    "centos_aws_instance_type":  "t2.micro",
    "Windows_Server-2016-English-Full-Base_aws_instance_type":  "m5.large",
    "Windows_Server-2016-English-Full-SQL_2016_SP2_Standard_aws_instance_type":  "m5.2xlarge",
    "Windows_Server-2016-English-Full-SQL_2016_SP2_Enterprise_aws_instance_type":  "m5.2xlarge",
    "Windows_Server-2016-English-Full-SQL_2016_SP2_Express_aws_instance_type":  "m5.2xlarge",
    "Windows_Server-2016-English-Full-Containers_aws_instance_type":  "m5.large",
    "centos_7_ssh_user":  "centos",
    "centos_7_with_ansible_ssh_user":  "centos",
    "ssh_pty":            "true",
    "unique_id":          "{{ uuid }}",
    "Windows_Server-2016-English-Full-Base_aws_source_ami": "ami-0ed417ef057137c75",
    "Windows_Server-2016-English-Full-SQL_2016_SP2_Standard_aws_source_ami": "ami-04a01734fa62e9c89",
    "Windows_Server-2016-English-Full-SQL_2016_SP2_Enterprise_aws_source_ami": "ami-0238c1f3d0ee7810e", 
    "Windows_Server-2016-English-Full-SQL_2016_SP2_Express_aws_source_ami": "ami-08ad77527da9fd0e3",
    "Windows_Server-2016-English-Full-Containers_aws_source_ami": "ami-01fe8bc0abf9f3e99",
    "centos_7_aws_source_ami": "ami-06cf02a98a61f9f5e",
    "centos_7_with_ansible_aws_source_ami": "ami-06cf02a98a61f9f5e",
    "aws_profile": "myAwsProfile",
    "aws_keypair_name": "myKey",
    "aws_private_key_file": "ssh_key",
    "aws_iam_instance_profile": "Subnet_Build",
    "centos_7_ami_name": "CentOS Linux 7 x86_64 HVM EBS ENA {{ uuid }}",
    "centos_7_with_ansible_ami_name": "CentOS Linux 7 with Ansible x86_64 HVM EBS ENA {{ uuid }}",
    "Windows_Server-2016-English-Full-Base_ami_name": "Windows_Server-2016-English-Full-Base {{ uuid }}",
    "Windows_Server-2016-English-Full-SQL_2016_SP2_Standard_ami_name": "Windows_Server-2016-English-Full-SQL_2016_SP2_Standard {{ uuid }}",
    "Windows_Server-2016-English-Full-SQL_2016_SP2_Enterprise_ami_name": "Windows_Server-2016-English-Full-SQL_2016_SP2_Enterprise {{ uuid }}",
    "Windows_Server-2016-English-Full-SQL_2016_SP2_Express_ami_name": "Windows_Server-2016-English-Full-SQL_2016_SP2_Express {{ uuid }}",
    "Windows_Server-2016-English-Full-Containers_ami_name": "Windows_Server-2016-English-Full-Containers {{ uuid }}",
    "winrm_password": "**SUPERSECRETPASSWORD**"
}
```

### ssh_key

This is the SSH key used for communicating with this instance or for use for retrieving the Administrator password for any Windows instance.