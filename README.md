# Terraform Beginner Bootcamp 2023

## Semantic Versioning :monkey:
In this project is using scmentic versioning [semver.org](https://semver.org/)
Given a version number **MAJOR.MINOR.PATCH**, increment the:
- **MAJOR** version when you make incompatible API changes
- **MINOR** version when you add functionality in a backward compatible manner
- **PATCH** version when you make backward compatible bug fixes
Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.
for eg.  1.0.2

### How to check which linux you are using
In this project we are using ubuntu system.

[How To Check OS Version in Linux](
https://www.cyberciti.biz/faq/how-to-check-os-version-in-linux-command-line/)

checking OS Version:

```
$ cat /etc/os-release

PRETTY_NAME="Ubuntu 22.04.3 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.3 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
```

## Install the Terraform CLI

### Considerations with the Terraform CLI changes
The Terraform CLI installation instructions have changed due to gpg keyring changes. 
So we needed refer to the latest install CLI instructions via Terraform Documentation and change the scripting to install terraform.

[Install Terraform CLI from here ](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)

### Create a Bash Script to install terraform.  :penguin:

While fixing the Terraform CLI gpg depreciation issues we notice that bash scripts steps were a considerable amount more code. 
So we decided to create a bash script to install the Terraform CLI.

This bash script is located here: [./bin/install_terraform](./bin/install_terraform)

- This will keep the Gitpod Task File ([.gitpod.yml](.gitpod.yml)) small and clear.
- This allow us an easier to debug and execute manually Terraform CLI installiation commands.
- This will allow better portablity for other projects that need to install Terraform CLI.

#### Shebang Considerations.  :penguin:

A Shebang (prounced Sha-bang) tells the bash script what program that will interpet the script. eg. `#!/bin/bash`

ChatGPT recommended this format for bash: `#!/usr/bin/env bash`

- for portability for different OS distributions 
- will search the user's PATH for the bash executable

https://en.wikipedia.org/wiki/Shebang_(Unix)

#### Execution Considerations

When executing the bash script we can use the `./` shorthand notiation to execute the bash script.

eg. `./bin/install_terraform_cli`

If we are using a script in .gitpod.yml  we need to point the script to a program to interpert it.

eg. `source ./bin/install_terraform_cli`

#### Linux Permissions Considerations

In order to make our bash scripts executable we need to change linux permission for the fix to be exetuable at the user mode.

```sh
chmod u+x ./bin/install_terraform_cli
```

alternatively:

```sh
chmod 744 ./bin/install_terraform_cli
```

https://en.wikipedia.org/wiki/Chmod

## Gitpod Lifecycle

We need to be careful when using the Init because it will not rerun if we restart an existing workspace.

https://www.gitpod.io/docs/configure/workspaces/tasks

