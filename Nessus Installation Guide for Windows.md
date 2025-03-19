# Nessus Installation Guide

## Description
This guide provides a detailed step-by-step process for installing and registering Nessus on a Windows operating system. Nessus is a powerful vulnerability scanning tool used for security assessments and vulnerability management.

## Purpose
To provide a step-by-step guide for installing Nessus, a widely used vulnerability scanning tool, on a Windows operating system and completing its registration process. This ensures that the software is properly set up for conducting security assessments and vulnerability management.

## Procedure:

### 1. Verify System Requirements
Ensure your system meets the minimum requirements:
- **Operating System**: Windows 10, Windows 11, or Windows Server (2016, 2019, or 2022).
- **RAM**: Minimum 4 GB (8 GB or higher recommended).
- **Disk Space**: At least 30 GB of free space.

### 2. Download the Nessus Installer
- Open a web browser and navigate to the official Tenable Nessus download page: [Nessus Downloads](https://www.tenable.com/downloads/nessus).
- Select the appropriate version of Nessus (e.g., Nessus Professional, Nessus Essentials) based on your license or trial.
- Choose the Windows option from the list of available downloads.
- Click the **Download** button and save the installer file (e.g., `Nessus-x.x.x-win32.msi`) to a location on your system (e.g., Desktop or Downloads folder).
- On the download page, locate and note the provided hash value (e.g., SHA-256 or MD5) for the installer file. This is typically listed next to the download link.

### 3. Check the Hash Value of the Downloaded File
- Open **Command Prompt**.
- Navigate to the directory where the installer was downloaded:
  ```sh
  cd C:\Users\<YourUsername>\Downloads
  ```
- Use the `certutil` command to generate the hash of the downloaded file:
  - For SHA-256:  
    ```sh
    certutil -hashfile Nessus-x.x.x-win32.msi SHA256
    ```
  - For MD5:  
    ```sh
    certutil -hashfile Nessus-x.x.x-win32.msi MD5
    ```
  - Replace `Nessus-x.x.x-win32.msi` with the exact filename of your downloaded installer.
- Compare the calculated hash with the hash provided on the Tenable download page.
  - ✅ If they match, the file is authentic and untampered. Proceed to the next step.
  - ❌ If they do not match, delete the file and re-download it from the official source.

### 4. Install Nessus
- Locate the verified `.msi` installer file and double-click it to begin the installation process.
- If prompted by **User Account Control (UAC)**, click **Yes** to allow the installer to make changes to your system.
- In the Nessus Setup Wizard:
  - Click **Next** on the welcome screen.
  - Review and accept the **End User License Agreement (EULA)** by selecting **I accept the terms in the license agreement**, then click **Next**.
  - Choose the installation directory (default: `C:\Program Files\Tenable\Nessus`), or customize it if needed, then click **Next**.
  - Click **Install** to begin the installation process.
- Wait for the installation to complete (this may take a few minutes).
- Once finished, click **Finish** to close the wizard. Nessus services will start automatically in the background.

### 5. Access Nessus Web Interface
- Open a web browser (e.g., Chrome, Firefox, or Edge).
- Enter the following URL in the address bar: [https://localhost:8834/](https://localhost:8834/) (Nessus runs on port 8834 by default).
- If a security warning appears (due to a self-signed certificate), proceed by clicking **Advanced** and then **Accept the Risk and Continue**.
- The Nessus initialization page will load. Wait for the initial setup process to complete (this may take a few minutes).

### 6. Register Nessus
- On the Nessus welcome screen, select the product version you are installing:
  - **Nessus Essentials**: Free version for personal or educational use (up to 16 IPs).
  - **Nessus Professional**: Paid version for commercial use.
  - **Nessus Expert**: Advanced paid version with additional features.
- Click **Continue**.
- Enter your activation code:
  - If you don’t have an activation code, select **Register for Nessus Essentials** and follow the prompts to sign up for a free code via email.
  - If you have a code, paste it into the **Activation Code** field (e.g., `XXXX-XXXX-XXXX-XXXX`).
- Click **Next**.
- Nessus will connect to the Tenable servers to validate the code and download necessary plugins. This requires an active internet connection and may take several minutes.
- Once the plugins are downloaded and installed, you’ll be prompted to create an admin account.

### 7. Set Up Admin Account
- On the **Create an account** screen:
  - Enter a **username** (e.g., `admin`).
  - Enter a **strong password** (minimum 8 characters, including letters, numbers, and special characters).
  - Confirm the password.
- Click **Submit** to finalize the setup.

### 8. Log In and Verify Installation
- After account creation, you’ll be redirected to the Nessus login page.
- Enter your **username and password**, then click **Log In**.
- Verify that the **Nessus dashboard** loads successfully, indicating the installation and registration are complete.
- Optionally, check the **About** section (under **Settings**) to confirm the version and license status.

### 9. Post-Installation Configuration (Optional)
- Configure **scan policies, schedules, or credentials** as needed for your use case.
- Ensure the **system firewall** allows traffic on port **8834** if accessing Nessus from another device.

### 10. Starting Nessus Manually (Optional)
- If Nessus does not start automatically or you need to restart it manually:
  - **Via Services:**
    1. Press `Win + R`, type `services.msc`, and press **Enter**.
    2. Scroll down to find **Tenable Nessus** in the list of services.
    3. Right-click **Tenable Nessus** and select **Start** (or **Restart** if it’s already running).
    4. Wait a few moments for the service to initialize.
  - **Via Command Line:**
    1. Open a **Command Prompt** with administrative privileges.
    2. Navigate to the Nessus installation directory:
       ```sh
       cd C:\Program Files\Tenable\Nessus
       ```
    3. Run the command to start Nessus:
       ```sh
       net start "Tenable Nessus"
       ```
    4. To stop Nessus (if needed):
       ```sh
       net stop "Tenable Nessus"
       ```
- Verify Nessus is running by accessing [https://localhost:8834/](https://localhost:8834/) in your browser and confirming the login page loads.

## Notes
- Keep your activation code secure and do not share it publicly.
- Nessus requires periodic plugin updates, which will download automatically when connected to the internet.
- If the hash verification fails repeatedly, contact Tenable support to ensure the integrity of the download source.
- If issues arise (e.g., port conflicts, failed registration, or service startup problems), refer to the Tenable support documentation at [https://docs.tenable.com/](https://docs.tenable.com/) or contact Tenable support.

## Disclaimer
This guide is provided for informational purposes only. Follow all security best practices when installing and configuring Nessus. The author and publisher are not responsible for any issues, damages, or security risks that may arise from the use of this guide. Always refer to the official Tenable documentation for the most up-to-date instructions and support.
