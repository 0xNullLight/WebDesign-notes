### Introduction

pgAdmin 4 is a versatile, open-source management tool for PostgreSQL, available as both a desktop and web application. This tutorial will guide you through the installation and configuration of pgAdmin 4 on Ubuntu 22.04, and it is also applicable to Linux Mint and other distributions based on Ubuntu.

### Prerequisites

- A system running Ubuntu 22.04 (Jammy), Linux Mint, or another Ubuntu-based distribution.
- Root or sudo privileges.

### Step 1: Install the Public Key

To ensure the authenticity of the packages from the pgAdmin repository, you need to add its public key to your system.

1. Open a terminal and run the following command:

   ```bash
   sudo curl https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo apt-key add
   ```

### Step 2: Add the pgAdmin Repository

Add the pgAdmin repository to your system's list of package sources.

1. Create a new repository configuration file:

   ```bash
   sudo sh -c 'echo "deb https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/jammy pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list'
   ```

2. Update the package list to include the new repository:

   ```bash
   sudo apt update
   ```

   **Note:** The same commands for adding the repository and updating the package list are also valid for Linux Mint and other distributions based on Ubuntu.

### Step 3: Install pgAdmin

You have the option to install pgAdmin in one of three modes:

#### Option 1: Install Both Desktop and Web Modes

To install pgAdmin for both desktop and web modes:

```bash
sudo apt install pgadmin4
```

#### Option 2: Install Desktop Mode Only

To install pgAdmin for desktop mode only:

```bash
sudo apt install pgadmin4-desktop
```

#### Option 3: Install Web Mode Only

To install pgAdmin for web mode only:

```bash
sudo apt install pgadmin4-web
```

### Step 4: Configure the Web Server (for Web Mode Only)

If you opted for the web mode installation, you need to configure the web server.

1. Run the setup script to configure the web server:

   ```bash
   sudo /usr/pgadmin4/bin/setup-web.sh
   ```

   This script will prompt you to enter details such as the email address and password for the pgAdmin web application. Follow the on-screen instructions to complete the setup.

### Conclusion

You have successfully installed and configured pgAdmin 4 on your Ubuntu 22.04 system, Linux Mint, or another Ubuntu-based distribution. Whether you use it as a desktop application or a web application, pgAdmin 4 provides powerful management tools for PostgreSQL. For additional support or information, refer to the official [pgAdmin documentation](https://www.pgadmin.org/docs/) or visit community forums.
