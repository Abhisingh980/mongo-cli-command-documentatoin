Certainly! Here's a README.md formatted documentation for using MongoDB Atlas CLI commands, including authentication, listing clusters, and managing database users. This guide assumes you have MongoDB CLI tools installed and configured.

---

# MongoDB Atlas CLI Documentation

## Overview

This document provides a guide for using MongoDB Atlas CLI commands to manage clusters and database users. It covers how to authenticate, list clusters, and create database users.

## Prerequisites

- MongoDB CLI installed (`mongocli` or `atlas` CLI)
- Access to a MongoDB Atlas account
- API Key or Username/Password for authentication

## Installation

### **Install MongoDB CLI (`mongocli`):**

- **macOS:**
  ```bash
  brew tap mongodb/brew
  brew install mongodb-database-tools
  brew install mongodb/mongodb-atlas/mongocli
  ```

- **Windows:**
  Download the `.msi` installer from the [MongoDB Download Center](https://www.mongodb.com/try/download/cli).

- **Linux:**
  Download the `.tar.gz` file from the [MongoDB CLI Documentation](https://www.mongodb.com/docs/mongodb-shell/), extract it, and follow the installation instructions.

## Authentication

### **Login to MongoDB Atlas:**

To authenticate with MongoDB Atlas, use the following command:

```bash
atlas auth login
```

Follow the prompts to log in using your credentials.

## Cluster Management

### **List Clusters:**

To list all clusters in your MongoDB Atlas project:

```bash
atlas clusters ls
```

For detailed output, you can use:

```bash
atlas clusters ls -o plaintext
```

### **Additional Cluster Commands:**

- **Get Cluster Information:**

  ```bash
  atlas clusters describe <cluster-name>
  ```

- **Create a Cluster:**

  ```bash
  atlas clusters create <cluster-name> --tier M10 --provider AWS --region US_EAST_1
  ```

- **Delete a Cluster:**

  ```bash
  atlas clusters delete <cluster-name>
  ```

## Database User Management

### **List Database Users:**

To list all database users in your MongoDB Atlas project:

```bash
atlas dbuser ls
```

For detailed output, you can use:

```bash
atlas dbuser ls -o plaintext
```

### **Create a Database User:**

To create a new database user with the `clusterMonitor` role:

```bash
atlas dbuser create --username <username> --password <password> --roles clusterMonitor --authDatabase admin
```

Replace `<username>` and `<password>` with the desired username and password. Ensure the role is correctly specified as `clusterMonitor`.

### **Additional Database User Commands:**

- **Get User Information:**

  ```bash
  atlas dbuser describe <username>
  ```

- **Update a User:**

  ```bash
  atlas dbuser update --username <username> --roles <new-roles>
  ```

- **Delete a User:**

  ```bash
  atlas dbuser delete <username>
  ```

## Configuration

### **Initialize Configuration:**

To initialize the MongoDB CLI configuration:

```bash
atlas config init
```

Set up your API keys or credentials as required.

### **Environment Variables:**

Export your API key or other configuration details if needed:

```bash
export api_mongo="<your-api-key>"
```

Source your `.zshrc` or `.bashrc` file to apply changes:

```bash
source ~/.zshrc
```

## Troubleshooting

### **Common Errors:**

- **Invalid Role Error:**

  Ensure the role specified is valid. Use `clusterMonitor` instead of `clustermonitor`.

  Example of valid user creation:

  ```bash
  atlas dbuser create --username bubu --password <your-password> --roles clusterMonitor --authDatabase admin
  ```

- **Authentication Issues:**

  Verify that your API keys or login credentials are correct and have the necessary permissions.

---

The `atlas process` command is part of the MongoDB Atlas CLI and is used for managing and interacting with processes within your MongoDB Atlas environment. This includes tasks such as listing, describing, and managing database processes.

Here’s a detailed guide on using the `atlas process` command:

### **1. **Overview**

The `atlas process` command is used to manage and interact with the processes running in your MongoDB Atlas clusters. This typically includes operations related to the individual processes that make up your MongoDB deployments, such as the primary and secondary nodes in a replica set or the shards in a sharded cluster.

### **2. **Common Commands**

#### **List Processes**

To list all processes in your MongoDB Atlas project:

```bash
atlas process ls
```

This command will display a list of all processes, including their statuses and other relevant details.

#### **Describe a Process**

To get detailed information about a specific process, use:

```bash
atlas process describe <process-id>
```

Replace `<process-id>` with the ID of the process you want to describe. This will provide detailed information about the specified process, including its status, configuration, and other attributes.

#### **Monitor a Process**

While `atlas process` does not directly include monitoring commands, you can use other commands to monitor processes in real-time. For example, you might use `atlas clusters describe <cluster-name>` to get information about the health and status of the cluster, which indirectly includes process information.

### **3. **Examples**

Here are a few examples of using the `atlas process` command:

- **List All Processes:**

  ```bash
  atlas process ls
  ```

- **Describe a Specific Process:**

  ```bash
  atlas process describe <process-id>
  ```

  Example:

  ```bash
  atlas process describe 12345
  ```

### **4. **Additional Considerations**

- **Permissions:** Ensure you have the necessary permissions to view and manage processes. You may need to have appropriate roles assigned in MongoDB Atlas.

- **API Keys:** If you’re using API keys, ensure they have the necessary scopes and permissions to interact with processes.

- **Command Help:** For help and additional options related to `atlas process`, you can always use:

  ```bash
  atlas process --help
  ```

### **5. **Related Commands**

- **List Clusters:**

  ```bash
  atlas clusters ls
  ```

- **Describe Cluster:**

  ```bash
  atlas clusters describe <cluster-name>
  ```

- **List Database Users:**

  ```bash
  atlas dbuser ls
  ```

- ** aditional commad always give by --help in any where in atlas command
- ** use mongosh with atlas give u a very powerfull tool to do database operation using command line into cluster or server side conection

### **6. **Resources**

- [MongoDB Atlas CLI Documentation](https://www.mongodb.com/docs/mongocli/)
- [MongoDB Atlas Documentation](https://www.mongodb.com/docs/atlas/)

