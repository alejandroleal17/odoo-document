# Sticky Bits Installation and Configuration Guide

## Introduction to Sticky Bits
Sticky Bits is a special type of file permission in Unix and Linux systems. When the sticky bit is set on a directory, it means that only the file's owner, the directory's owner, or the root user can rename, move, or delete the contained files, regardless of the file's individual permissions. This feature is particularly useful for directories like `/tmp`, where multiple users have permission to write, but should not be able to delete or rename each other's files.

## Prerequisites:
- Ensure `gcc` is installed. You can install it using the following command:
  ```bash
  sudo apt install gcc
  ```
- Install `acl` using the command below:
  ```bash
  sudo apt-get install acl
  ```
- Create the `dataintegrator` group and associate it with users:

  - Creating the group:
    ```bash
    sudo groupadd dataintegrator
    ```
    Verify that the group has been created:
    ```bash
    grep 'dataintegrator' /etc/group
    ```

  - Associate users with the group:
    ```bash
    sudo usermod -aG dataintegrator user
    ```
    Create the `dataintegrator` user and associate it with the group:
    ```bash
    sudo usermod -aG dataintegrator dataintegrator
    ```

- Create a folder in the directory:
  ```bash
  mkdir /home/ubuntu/symbist/
  ```

To assign permissions:

```bash
sudo setfacl -Rdm g:dataintegrator:rx /home/ubuntu/symbits/
sudo chgrp dataintegrator /home/ubuntu/symbits/ -fR
sudo chmod g+s /home/ubuntu/symbits -fR
```

Apply permissions to the directory:

```bash
chmod 775 /home/ubuntu/symbits
```

Ensure to follow these steps carefully for the successful installation and configuration of Sticky Bits.

