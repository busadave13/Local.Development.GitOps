# Docker Desktop Dev Machine Setup

This repository contains instuctions to setup a development machine to work with Docker Desktop and Kubernetes.
It also provides gitops support using Flux to automate the deployment of Kubernetes resources.

## Prerequisites

Run this command from an elevated PowerShell prompt.

Install [chocolatey package manager](https://chocolatey.org/)

``` bash
winget install chocolatey
```

Install [Git Bash](https://git-scm.com/)

``` bash
choco install git
```

Install [Helm](https://helm.sh/)

``` bash
choco install kubernetes-helm
```

Install [Flux](https://fluxcd.io/flux)

```bash
choco install flux
```

Install [K9s](https://k9scli.io/)

```bash
choco install k9s
```

Install [Slack](https://slack.com/)

```bash
choco install slack
```

Install [Visual Studio Code](https://code.visualstudio.com/)

```bash
choco install vscode
```

Install [Node.js](https://nodejs.org/)

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
    memory=8GB                           # Max memmory
    processors=4                         # Virtual CPUs
    swap=8GB                             # Sets amount of swap storage space to 8GB, default is 25% of available RAM
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
  
## Flux Setup

Create environment variable named `GITHUB_TOKEN` with a personal access token.

```bash
export GITHUB_TOKEN=<personal-access-token>
```

Bootstrap the Flux repository.

```bash
flux bootstrap github \
  --token-auth \
  --owner=my-github-username \
  --repository=https://github.com/busadave13/Local.Development.GitOps.git \
  --branch=main \
  --path=clusters/development \
  --personal
```
