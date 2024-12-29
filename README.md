# Automatic Debian Package Builder

## Overview
The **Automatic Debian Package Builder** is a Bash script designed to simplify the process of building Debian packages. It automates tasks such as creating required Debian package files, managing directory structures, and packaging source files. The script supports both automatic and manual package creation workflows.

## Features
- Reads configuration details from an `env` file.
- Automatically generates Debian package metadata files if they do not exist.
- Supports recursive file inclusion for `src` directory.
- Offers an option to upload packages to Launchpad.
- Manual packaging support for custom workflows.

## Prerequisites
1. A Linux-based system with Bash shell.
2. Required tools:
   - `dpkg-deb`
   - `debuild`
   - `dput`
3. An `env` file containing package metadata.
4. A `src` directory containing the source files to be packaged.

## Usage
### 1. Prepare Environment
Create an `env` file in the script's directory with the following fields:
```
package-name=<name>
version=<version>
author=<author name>
author-email=<author email>
description=<package description>
depends=<dependencies>
homepage=<homepage URL>
upstream-name=<upstream name>
distribution=<distribution>
mainChange=<main change log>
minorChange=<minor change log>
ppa-path=<ppa path>
```

### 2. Script Workflow
#### Automatic Packaging
1. The script prompts whether to build the package automatically.
2. Reads configuration details from the `env` file.
3. Checks if files (`compat`, `rules`, `control`, etc.) exist:
   - Creates default versions if missing.
4. Copies and sets up the `src` folder within the package structure.
5. Assigns appropriate permissions to files.
6. Builds the package using `debuild`.
7. Optionally deploys the package to Launchpad.

#### Manual Packaging
1. The script prompts whether to build the package manually.
2. Performs similar steps as in automatic packaging but uses a different directory structure and builds the package with `dpkg-deb`.

## Directory Structure
The script creates a directory for the package with the following structure:
```
<package-name>.<version>/
|-- DEBIAN/
|   |-- control
|   |-- rules
|   |-- compat
|   |-- copyright
|   |-- changelog
|-- usr/local/bin/
    |-- (source files)
```
## Installation and Usage of the Script

You can choose to install the Automatic Debian Package Builder manually or automatically. 

### Manual Installation
1. Download the latest release from the [GitHub repository](#).  
2. Extract the files and follow the included instructions.  
> **Note:** Manual installation requires you to handle updates on your own.

### Automatic Installation
For a more streamlined experience, you can install the script using its [official PPA](https://launchpad.net/~vin100proflow/+archive/ubuntu/auto-deb-generator).  
Simply add the PPA to your system and install the package:
```bash
sudo add-apt-repository ppa:vin100proflow/auto-deb-generator
sudo apt update
sudo apt install auto-deb-generator
```
### Running the Script
Once installed, to build your Debian package project, simply run:

```bash
generate-debian-package
```
and follow the guided procedure.

### Important Notice
If you wish to publish your project on Launchpad.net (to create a PPA), you’ll need to provide a PGP key. This key is required to link your Launchpad account with your Linux environment.

For a complete guide on creating and configuring PGP keys, I’m planning to release a tutorial or course (your support by purchasing it would be greatly appreciated!). In the meantime, if you encounter issues while generating or configuring PGP keys, feel free to contact me at vincent.legnani.biz@gmail.com, and I’ll gladly provide the necessary steps to simplify the process.


## License
The script is licensed under the MIT License.
---
For detailed documentation and contribution guidelines, please refer to the [homepage](https://github.com/vin100proflow/auto-deb-generator).

