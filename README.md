
# WordPress_IAC

## Infrastructure as Code (IaC) with Vagrant and WordPress Setup (Local Environment Context)

This DevOps project demonstrates setting up a WordPress web server on an Ubuntu 20.04 (Focal Fossa) virtual machine using Vagrant. The server is pre-configured to host a WordPress site, offering a simple introduction to Infrastructure as Code (IaC) in a local development environment with Vagrant provisioning.

## Requirements

-   [Vagrant](https://www.vagrantup.com/downloads) (version 2.x)
-   [VirtualBox](https://www.virtualbox.org/wiki/Downloads) (version 6.x or later)

Be sure to install these tools before proceeding.

---

### Virtual Machine Characteristics

The virtual machine configured by this Vagrant setup has the following specifications:

-   **Base Box**: Ubuntu 20.04 (Focal Fossa)
-   **Memory Allocation**: 1600 MB
-   **CPU Allocation**: 1 CPU
-   **Storage**:
    -   Disk Size: 10 GB (default size for the base box)
-   **Network Configuration**:
    -   Private Network IP: `192.168.56.10`
    -   Public Network (optional)
-   **Provisioning**:
    -   Apache web server installed and configured
    -   MySQL server installed and configured
    -   WordPress downloaded and set up

These specifications provide a lightweight environment suitable for local WordPress development and testing.

---

## Getting Started

Follow these steps to set up your Vagrant environment:

1.  **Clone the Repository:**

    ```bash
    git clone https://github.com/yourusername/wordpress_IAC.git
    cd wordpress_IAC
    ```

2. **Initialize the Vagrant Environment:**

    ```bash
    vagrant up  # Run this command in the folder where your Vagrantfile is located
    ```

    This command will download the necessary box, set up the virtual machine, and run the provisioning script to install Apache, MySQL, and WordPress.

### Choosing the Bridge Network Interface

During the `vagrant up` command, you may be prompted to select a network interface for the bridge connection. This bridge interface allows the VM to access the same network as the host machine. You'll see a list similar to this:

```plaintext
1) wlp0s20f3
2) enp2s0
3) vmnet1
4) vmnet8
==> default: When choosing an interface, it is usually the one that is
==> default: being used to connect to the internet.
==> default: 
default: Which interface should the network bridge to?
```

To identify which interface to select:

1. **Identify Your Active Network Interface:**  
   Run the following command in your shell to view your active network interfaces:

   ```bash
   ip a
   ```

   Look for the interface connected to the internet (often labeled with `inet <IP address>`).

2. **Select the Correct Interface:**  
   When prompted, enter the number of the interface connected to the internet. For example, if `wlp0s20f3` is your active Wi-Fi connection, you would enter `1`.

This selection allows the VM to use the same network as your host, enabling easier access to the internet and local resources.

---

3. **Access the Server:**

    - Open your web browser and navigate to [http://192.168.56.10](http://192.168.56.10) to view the deployed WordPress site.

4. **SSH into the VM (Optional):**

    For debugging or development purposes, you can access the VM using SSH:

    ```bash
    vagrant ssh
    ```

5. **Stop the VM:**

    To stop the virtual machine, run:

    ```bash
    vagrant halt
    ```

6. **Destroy the VM:**

    To completely remove the virtual machine and its resources, run:

    ```bash
    vagrant destroy
    ```

---

## Provisioning Script
# WordPress_IAC

## Infrastructure as Code (IaC) with Vagrant and WordPress Setup (Local Environment Context)

This DevOps project demonstrates setting up a WordPress web server on an Ubuntu 20.04 (Focal Fossa) virtual machine using Vagrant. The server is pre-configured to host a WordPress site, offering a simple introduction to Infrastructure as Code (IaC) in a local development environment with Vagrant provisioning.

## Requirements

-   [Vagrant](https://www.vagrantup.com/downloads) (version 2.x)
-   [VirtualBox](https://www.virtualbox.org/wiki/Downloads) (version 6.x or later)

Be sure to install these tools before proceeding.

---

### Virtual Machine Characteristics

The virtual machine configured by this Vagrant setup has the following specifications:

-   **Base Box**: Ubuntu 20.04 (Focal Fossa)
-   **Memory Allocation**: 1600 MB
-   **CPU Allocation**: 1 CPU
-   **Storage**:
    -   Disk Size: 10 GB (default size for the base box)
-   **Network Configuration**:
    -   Private Network IP: `192.168.56.10`
    -   Public Network (optional)
-   **Provisioning**:
    -   Apache web server installed and configured
    -   MySQL server installed and configured
    -   WordPress downloaded and set up

These specifications provide a lightweight environment suitable for local WordPress development and testing.

---

## Getting Started

Follow these steps to set up your Vagrant environment:

1.  **Clone the Repository:**

    ```bash
    git clone https://github.com/yourusername/wordpress_IAC.git
    cd wordpress_IAC
    ```

2. **Initialize the Vagrant Environment:**

    ```bash
    vagrant up  # Run this command in the folder where your Vagrantfile is located
    ```

    This command will download the necessary box, set up the virtual machine, and run the provisioning script to install Apache, MySQL, and WordPress.

### Choosing the Bridge Network Interface

During the `vagrant up` command, you may be prompted to select a network interface for the bridge connection. This bridge interface allows the VM to access the same network as the host machine. You'll see a list similar to this:

```plaintext
1) wlp0s20f3
2) enp2s0
3) vmnet1
4) vmnet8
==> default: When choosing an interface, it is usually the one that is
==> default: being used to connect to the internet.
==> default: 
default: Which interface should the network bridge to?
```

To identify which interface to select:

1. **Identify Your Active Network Interface:**  
   Run the following command in your shell to view your active network interfaces:

   ```bash
   ip a
   ```

   Look for the interface connected to the internet (often labeled with `inet <IP address>`).

2. **Select the Correct Interface:**  
   When prompted, enter the number of the interface connected to the internet. For example, if `wlp0s20f3` is your active Wi-Fi connection, you would enter `1`.

This selection allows the VM to use the same network as your host, enabling easier access to the internet and local resources.

---

3. **Access the Server:**

    - Open your web browser and navigate to [http://192.168.56.10](http://192.168.56.10) to view the deployed WordPress site.

4. **SSH into the VM (Optional):**

    For debugging or development purposes, you can access the VM using SSH:

    ```bash
    vagrant ssh
    ```

5. **Stop the VM:**

    To stop the virtual machine, run:

    ```bash
    vagrant halt
    ```

6. **Destroy the VM:**

    To completely remove the virtual machine and its resources, run:

    ```bash
    vagrant destroy
    ```

---

## Provisioning Script

The provisioning script performs the following tasks:

- Updates package lists
- Installs Apache, MySQL, and necessary PHP modules
- Downloads and extracts the latest version of WordPress
- Configures Apache for the WordPress site
- Sets up the WordPress database and user
- Copies and modifies the sample WordPress configuration file
- Restarts MySQL and Apache to apply changes

---

## Customization

Feel free to modify the Vagrantfile and provisioning script as needed. You can adjust the database name, user credentials, or other configuration settings for your WordPress site.

## Contributing

To contribute to this project, please fork the repository and submit a pull request with your changes.

Additionally, consider reviewing the first project of this series, which us
# WordPress_IAC

## Infrastructure as Code (IaC) with Vagrant and WordPress Setup (Local Environment Context)

This DevOps project demonstrates setting up a WordPress web server on an Ubuntu 20.04 (Focal Fossa) virtual machine using Vagrant. The server is pre-configured to host a WordPress site, offering a simple introduction to Infrastructure as Code (IaC) in a local development environment with Vagrant provisioning.

## Requirements

-   [Vagrant](https://www.vagrantup.com/downloads) (version 2.x)
-   [VirtualBox](https://www.virtualbox.org/wiki/Downloads) (version 6.x or later)

Be sure to install these tools before proceeding.

---

### Virtual Machine Characteristics

The virtual machine configured by this Vagrant setup has the following specifications:

-   **Base Box**: Ubuntu 20.04 (Focal Fossa)
-   **Memory Allocation**: 1600 MB
-   **CPU Allocation**: 1 CPU
-   **Storage**:
    -   Disk Size: 10 GB (default size for the base box)
-   **Network Configuration**:
    -   Private Network IP: `192.168.56.10`
    -   Public Network (optional)
-   **Provisioning**:
    -   Apache web server installed and configured
    -   MySQL server installed and configured
    -   WordPress downloaded and set up

These specifications provide a lightweight environment suitable for local WordPress development and testing.

---

## Getting Started

Follow these steps to set up your Vagrant environment:

1.  **Clone the Repository:**

    ```bash
    git clone https://github.com/yourusername/wordpress_IAC.git
    cd wordpress_IAC
    ```

2. **Initialize the Vagrant Environment:**

    ```bash
    vagrant up  # Run this command in the folder where your Vagrantfile is located
    ```

    This command will download the necessary box, set up the virtual machine, and run the provisioning script to install Apache, MySQL, and WordPress.

### Choosing the Bridge Network Interface

During the `vagrant up` command, you may be prompted to select a network interface for the bridge connection. This bridge interface allows the VM to access the same network as the host machine. You'll see a list similar to this:

```plaintext
1) wlp0s20f3
2) enp2s0
3) vmnet1
4) vmnet8
==> default: When choosing an interface, it is usually the one that is
==> default: being used to connect to the internet.
==> default: 
default: Which interface should the network bridge to?
```

To identify which interface to select:

1. **Identify Your Active Network Interface:**  
   Run the following command in your shell to view your active network interfaces:

   ```bash
   ip a
   ```

   Look for the interface connected to the internet (often labeled with `inet <IP address>`).

2. **Select the Correct Interface:**  
   When prompted, enter the number of the interface connected to the internet. For example, if `wlp0s20f3` is your active Wi-Fi connection, you would enter `1`.

This selection allows the VM to use the same network as your host, enabling easier access to the internet and local resources.

---

3. **Access the Server:**

    - Open your web browser and navigate to [http://192.168.56.10](http://192.168.56.10) to view the deployed WordPress site.

4. **SSH into the VM (Optional):**

    For debugging or development purposes, you can access the VM using SSH:

    ```bash
    vagrant ssh
    ```

5. **Stop the VM:**

    To stop the virtual machine, run:

    ```bash
    vagrant halt
    ```

6. **Destroy the VM:**

    To completely remove the virtual machine and its resources, run:

    ```bash
    vagrant destroy
    ```

---

## Provisioning Script

The provisioning script performs the following tasks:

- Updates package lists
- Installs Apache, MySQL, and necessary PHP modules
- Downloads and extracts the latest version of WordPress
- Configures Apache for the WordPress site
- Sets up the WordPress database and user
- Copies and modifies the sample WordPress configuration file
- Restarts MySQL and Apache to apply changes

---

## Customization

Feel free to modify the Vagrantfile and provisioning script as needed. You can adjust the database name, user credentials, or other configuration settings for your WordPress site.

## Contributing

To contribute to this project, please fork the repository and submit a pull request with your changes.

Additionally, consider 
# WordPress_IAC

## Infrastructure as Code (IaC) with Vagrant and WordPress Setup (Local Environment Context)

This DevOps project demonstrates setting up a WordPress web server on an Ubuntu 20.04 (Focal Fossa) virtual machine using Vagrant. The server is pre-configured to host a WordPress site, offering a simple introduction to Infrastructure as Code (IaC) in a local development environment with Vagrant provisioning.

## Requirements

-   [Vagrant](https://www.vagrantup.com/downloads) (version 2.x)
-   [VirtualBox](https://www.virtualbox.org/wiki/Downloads) (version 6.x or later)

- [Git Bash](https://gitforwindows.org/) (for Windows users): This provides a Unix-like terminal, making it easier to run commands as outlined in this guide.

- macOS users can proceed directly with the instructions without Git Bash.

Be sure to install these tools before proceeding.

---

### Virtual Machine Characteristics

The virtual machine configured by this Vagrant setup has the following specifications:

-   **Base Box**: Ubuntu 20.04 (Focal Fossa)
-   **Memory Allocation**: 1600 MB
-   **CPU Allocation**: 1 CPU
-   **Storage**:
    -   Disk Size: 10 GB (default size for the base box)
-   **Network Configuration**:
    -   Private Network IP: `192.168.56.10`
    -   Public Network (optional)
-   **Provisioning**:
    -   Apache web server installed and configured
    -   MySQL server installed and configured
    -   WordPress downloaded and set up

These specifications provide a lightweight environment suitable for local WordPress development and testing.

---

## Getting Started

Follow these steps to set up your Vagrant environment:

1.  **Clone the Repository:**

    ```bash
    git clone https://github.com/rdplus2015/wordpress_IAC.git
    ```

2. **Initialize the Vagrant Environment:**

    ```bash
    vagrant up  # Run this command in the folder where your Vagrantfile is located
    ```

    This command will download the necessary box, set up the virtual machine, and run the provisioning script to install Apache, MySQL, and WordPress.

### Choosing the Bridge Network Interface

During the `vagrant up` command, you may be prompted to select a network interface for the bridge connection. This bridge interface allows the VM to access the same network as the host machine. You'll see a list similar to this:

```plaintext
1) wlp0s20f3
2) enp2s0
3) vmnet1
4) vmnet8
==> default: When choosing an interface, it is usually the one that is
==> default: being used to connect to the internet.
==> default: ---

default: Which interface should the network bridge to?
```

To identify which interface to select:

1. **Identify Your Active Network Interface:**  
   Run the following command in your shell to view your active network interfaces:

   ```bash
   ip a
   ```

   Look for the interface connected to the internet (often labeled with `inet <IP address>`).

2. **Select the Correct Interface:**  
   When prompted, enter the number of the interface connected to the internet. For example, if `wlp0s20f3` is your active Wi-Fi connection, you would enter `1`.

This selection allows the VM to use the same network as your host, enabling easier access to the internet and local resources.

---

3. **Access the Server:**

    - Open your web browser and navigate to [http://192.168.56.10](http://192.168.56.10) to view the deployed WordPress site.

4. **SSH into the VM (Optional):**

    For debugging or development purposes, you can access the VM using SSH:

    ```bash
    vagrant ssh
    ```

5. **Stop the VM:**

    To stop the virtual machine, run:

    ```bash
    vagrant halt
    ```

6. **Destroy the VM:**

    To completely remove the virtual machine and its resources, run:

    ```bash
    vagrant destroy
    ```



## Provisioning Script

The provisioning script performs the following tasks:

- Updates package lists
- Installs Apache, MySQL, and necessary PHP modules
- Downloads and extracts the latest version of WordPress
- Configures Apache for the WordPress site
- Sets up the WordPress database and user
- Copies and modifies the sample WordPress configuration file
- Restarts MySQL and Apache to apply changes


## Customization

Feel free to modify the Vagrantfile and provisioning script as needed. You can adjust the database name, user credentials, or other configuration settings for your WordPress site.

## Contributing

To contribute to this project, please fork the repository and submit a pull request with your changes.

Additionally, consider reviewing the first project of this series, which uses a simple HTML and CSS website instead of WordPress [here](https://github.com/rdplus2015/minifinance_IAC)




## License

This project is licensed under the MIT License. See the LICENSE file for details.
