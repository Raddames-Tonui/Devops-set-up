# Devops-set-up

# SETTING UP DOCKER

## Prerequisites

### Enable WSL2 and Install a Linux Distribution
Enable WSL and set it to use WSL2 by default if you haven’t done so already. Then, install a Linux distribution (e.g., Ubuntu) from the Microsoft Store.

```powershell
wsl --install
wsl --set-default-version 2
```

### Set Up Docker in WSL2
Docker works well with WSL2 when integrated with Docker Desktop for Windows.

1. **Download and Install Docker Desktop for Windows:**  
   Go to the [Docker Desktop](https://www.docker.com/products/docker-desktop/) website and download Docker Desktop for Windows.  
   After installation, open Docker Desktop and go to **Settings > Resources > WSL Integration**. Enable integration with your WSL2 distribution (e.g., Ubuntu).

2. **Verify Docker in WSL2:**  
   Open your WSL terminal and confirm Docker is working:

   ```bash
   docker --version
   ```

3. **Run a Docker Test:**  
   Run a test container to ensure everything is set up correctly:

   ```bash
   docker run hello-world
   ```

---

## Vagrant & VirtualBox

### Step 1: Download and Install the Vagrant Package
Update and install dependencies:

```bash
sudo apt update
sudo apt install -y wget gpg
```

Add the HashiCorp GPG key:

```bash
wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
```

Add the HashiCorp package repository:

```bash
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
```

Update the package list again and install Vagrant:

```bash
sudo apt update
sudo apt install -y vagrant
```

### Step 2: Verify the Installation
Once installation completes, verify that Vagrant is installed correctly by running:

```bash
vagrant --version
```

This should display the version number, confirming that Vagrant is now installed on your system. Let me know if you run into any issues!

---

## Setting Up Ansible in WSL2
Ansible works well within WSL2 and is easy to set up.

### Install Ansible
Install Ansible directly from the package manager:

```bash
sudo apt update
sudo apt install -y ansible
```

### Verify Ansible
Confirm Ansible is installed:

```bash
ansible --version
```

### Configure SSH for Ansible
Generate SSH keys if you plan to connect to remote servers:

```bash
ssh-keygen -t rsa -b 4096
```

Use the private key to connect to your servers or set up a configuration in the `~/.ssh/config` file for easier management.

---

## Set Up Minikube with Docker in WSL2
Minikube works well in WSL2 when Docker is set as its driver.

### Download Minikube
Download the Minikube binary, make it executable, and move it to `/usr/local/bin`:

```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

### Start Minikube with Docker
Ensure Docker is running and start Minikube with Docker as the driver:

```bash
minikube start --driver=docker
```

### Verify Minikube
Check that Minikube started successfully:

```bash
minikube status
```
