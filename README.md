# Fearlix Dev Containers

A collection of containerized development environments for building and deploying Fearlix projects. These containers provide pre-configured development tools for different tech stacks, making it easy to set up your development environment without worrying about dependency conflicts on your host machine.

## Prerequisites

Before you can use these containers, you need to [install distrobox](https://distrobox.it/#installation)

## Available Containers

### 🎯 Base
The foundation for all other containers. Contains essential development tools like git, curl, and necessary build utilities.

**Usage**: This is automatically used as the base for other containers. You typically don't create this directly.

### 📱 Flutter
Complete Flutter development environment for building mobile and desktop applications.

**Includes**:
- Flutter SDK (stable version)
- Java 17 (required by Flutter)
- Android SDK with emulator
- All necessary build tools and dependencies

**Best for**: Flutter app development (iOS, Android, desktop)

### 🐹 Go
Golang development environment with useful tools for backend development.

**Includes**:
- Go 1.x
- Delve (Go debugger)
- Goose (database migration tool)

**Best for**: Go backend development

### 📦 Node
Node.js and JavaScript/TypeScript development environment.

**Includes**:
- Node.js
- Yarn package manager

**Best for**: Web frontend development, Node.js backend

### 🗄️ Database
Database tools and GUI for managing databases.

**Includes**:
- MariaDB client and server
- MongoDB tools
- DBeaver Community Edition (database GUI)

**Best for**: Database development, schema management, data exploration

### ☁️ Cloud
Cloud infrastructure and deployment tools.

**Includes**:
- OpenTofu (Infrastructure as Code, Terraform-compatible)
- Ansible (Configuration management)
- AWS CLI (Amazon Web Services)

**Best for**: Infrastructure management, deployment, cloud provisioning

## Quick Start Guide

### Step 1: Create a Container

Choose the container you need and create it:

```bash
# For Flutter development
distrobox create -i ghcr.io/fearlix-srl/flutter

# For Go development
distrobox create -i ghcr.io/fearlix-srl/go

# For Node.js development
distrobox create -i ghcr.io/fearlix-srl/node

# For database work
distrobox create -i ghcr.io/fearlix-srl/database

# For cloud infrastructure
distrobox create -i ghcr.io/fearlix-srl/cloud
```

**What's happening here?**
- `distrobox create` creates a new container
- `-i` specifies which container image to use

The first time you create a container, it will download the image from the internet, which may take a few minutes.

### Step 2: Enter the Container

Once created, you can enter the container like it's a regular machine:

```bash
# Enter the flutter container
distrobox enter flutter

# You'll now be inside the container - notice your prompt changes
# You can now use all the tools in that container
```

### Step 3: Run Post-Install Setup

Most containers have a post-install script that finishes setting up the environment:

```bash
# Inside the container, run:
post-install.sh
```

This script handles any final configuration needed for that container.

## Useful Commands

### List all your containers:
```bash
distrobox list
```

### Run a command in a container without entering it:
```bash
distrobox run -n flutter flutter doctor
```

### Delete a container (when you don't need it anymore):
```bash
distrobox rm flutter
```

### Share files between host and container:
By default, your home directory is automatically shared. You can access files from both the host and inside the container.

If you need additional tools in a container, you can:

1. Enter the container
2. Install tools with the package manager (e.g., `dnf install package-name`)
3. Your changes persist in that container instance

---

**Happy containerized development!** 🐳
