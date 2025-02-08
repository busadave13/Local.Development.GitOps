# Docker Desktop Dev Machine Setup

This document describes how to set up a Docker Desktop development machine on Windows 11.

## Prerequisites

Run this command from an elevated PowerShell prompt.

Install chocolatey package manager

``` bash
winget install chocolatey
```

Install Git Bash

``` bash
choco install git
```

Install Helm

``` bash
choco install kubernetes-helm
```

Install Flux

```bash
choco install flux
```

Install K9s

```bash
choco install k9s
```

Install Slack

```bash
choco install slack
```

Install Visual Studio Code

```bash
choco install vscode
```

Install Node.js

```bash
choco install nodejs
```

## Install and Configure Docker Desktop

- Install Docker Desktop from [docker.com](https://www.docker.com/products/docker-desktop).
- Configure minumum resources for Docker Desktop.
  - Create a file named `.wslconfig` in your user profile directory (%userprofile%).
  - Add the following content to the file to set the memory and processor limits for WSL 2.

  ```bash
    [wsl2]
    memory=8GB   # Limits VM memory in WSL 2 to 8 GB
    processors=4 # Limits VM to use 4 virtual processors
  ```

  - Save the file and run the following command at the command prompt.
  
  ```bash
    wsl --shutdown
  ```

  - Restart Docker Desktop.
- Enable Kubernetes in Docker Desktop.
  - Right-click on the Docker Desktop icon in the system tray.
  - Click on Settings.
  - Click on Kubernetes and enable Kubernetes.
  - Click on Apply & Restart.
  - Wait for Kubernetes to start.
  - Open a Git Bash terminal and run the following command to verify that Kubernetes is running.

  ```bash
    kubectl get nodes
    # Output
    NAME             STATUS   ROLES           AGE   VERSION
    docker-desktop   Ready    control-plane   10h   v1.31.4
  ```
  
