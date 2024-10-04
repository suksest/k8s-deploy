# K8s Deployment with FluxCD

## Requirements

- K8s cluster
- FluxCD
- SOPS
- age file encryption

## Installation

### FluxCD

TBC

### How to install SOPS

1. Download the installer based on your operating system
2. If you're using Debian or Ubuntu, install using this command

    ```bash
    dpkg -i /path-to-file/sops_<version>.deb
    ```

3. Use this command to verify installed version

    ```bash
    sops --version
    ```

If the installation was success, it should display somthing like `sops <version>`

### How to install Age

1. If you're using Debian or Ubuntu, install using this command

    ```bash
    apt install age
    ```

2. Use this command to verify installed version

    ```bash
    age --version
    ```

If the installation was success, it should return installed version of age

## Usage

### flux command

TBC

### SOPS + Age

- Create public key and generate private key

    ```bash
    age -o age.agekey
    ```

- Encrypt file

    ```bash
    sops --age <public-key> --encrypt --in-place <file>
    ```

- Encrypt value only

    ```bash
    sops --age=<public-key> \
    --encrypt --encrypted-regex '^(data|stringData)$' --in-place secret.yaml
    ```

- Decrypt file

    ```bash
    sops --decrypt --in-place <public-key> --encrypt --in-place <file>
    ```
