![1_avSrkx78FxkvQ_EydrSFLA](https://github.com/user-attachments/assets/a44968f1-309d-46d8-8e01-7167f6db6ffd)

# Installing Nessus Essentials

Follow these steps to install Nessus Essentials on your system.

## 1. Download Nessus Essentials

- **Visit the Nessus Downloads Page:** Navigate to the [Nessus Downloads](https://www.tenable.com/downloads/nessus) page.
  - https://www.tenable.com/downloads/nessus?_gl=1*1wy2c7o*_ga*MTc4ODYyMjExNi4xNzEwNDg4MTIx*_ga_HSJ1XWV6ND*MTcxMDU2NjQyMC4zLjEuMTcxMDU2NjYyNy4wLjAuMA..&loginAttempted=true

- **Select Your Platform:** Choose the appropriate installer for your operating system.

- **Download the Installer:** Click on the download link to obtain the installer package.

## 2. Install Nessus Essentials

Open your terminal and execute the following commands:

  - **Navigate to the Download Directory:**

    ```bash
    cd /path/to/download/directory

- **Install the Package:**

    For Debian-based systems, use *dpkg* to install the downloaded package. Replace *filename.deb* with the actual file name of the downloaded Nessus installer.
    ```bash
      sudo dpkg -i filename.deb```

## 3. Start the Nessus Service

After installation, start the Nessus service:

- **Start the Service:**
  ```bash
    sudo systemctl start nessusd

- **SVerify the Service Status:**
  ```bash
    sudo systemctl status nessusd

> **Note:** Ensure that the service is active and running.

## 4. Access the Nessus Web Interface
Open your web browser and navigate to: 
https://127.0.0.1:8834

## 5. Configure Nessus Essentials

- Select "Nessus Essentials": On the welcome screen, choose the "Nessus Essentials" option.

- Register with Your Email: If you haven't already obtained an activation code, register with your email address to receive one. You can do this at the [Nessus Essentials Registration](https://www.tenable.com/products/nessus/nessus-essentials) page .

- Enter the Activation Code: Input the activation code you received via email.

- Create a User Account: Set up a username and password for accessing the Nessus interface.

- Complete the Setup: Follow the on-screen instructions to finalize the configuration.

## 6. Start Using Nessus Essentials
  Once the setup is complete, you can log in to the Nessus web interface using the credentials you created and begin scanning your network for vulnerabilities.






## Screenshots:
![Prebuilt-policies-and-templates](https://github.com/user-attachments/assets/3e9911c2-cfe2-43da-ad11-0073c485f68c)
