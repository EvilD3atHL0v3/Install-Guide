# Installing Burp Suite on Windows

## Description
Burp Suite is a powerful cybersecurity tool used for web application security testing. It is widely used by security professionals and ethical hackers for performing penetration tests, identifying vulnerabilities, and analyzing HTTP/S traffic.

## Purpose
To provide clear and concise instructions for installing Burp Suite, a widely used security testing tool, on a Windows operating system. This procedure ensures that users can set up Burp Suite efficiently to perform web application security testing, vulnerability assessments, and penetration testing.

## Procedure

### 1. Verify System Requirements
Ensure your system meets the minimum requirements:
- **Operating System**: Windows 7, 8, 10, or 11 (32-bit or 64-bit)
- **RAM**: Minimum 4 GB (8 GB or higher recommended)
- **Disk Space**: At least 1 GB of free space

### 2. Download Burp Suite
- Visit the official PortSwigger website: [Burp Suite Releases](https://portswigger.net/burp/releases)
- Choose the appropriate edition:
  - **Community Edition**: Free version with basic features.
  - **Professional Edition**: Paid version with advanced tools (requires a license).
- Click the **Download** button for your selected edition.
- Select the Windows installer (e.g., `.exe` file) compatible with your system (32-bit or 64-bit).
- Save the installer file to a location on your computer (e.g., `Downloads` folder).

### 3. Check the Hash Value of the Downloaded File
- On the PortSwigger download page, locate the provided hash value (e.g., SHA-256) for the installer file.
- Open **Command Prompt** on Windows:
  - Press `Win + R`, type `cmd`, and press `Enter`.
- Navigate to the download directory:
  ```sh
  cd C:\Users\<YourUsername>\Downloads
  ```
- Verify the hash value:
  ```sh
  certutil -hashfile <filename.exe> SHA256
  ```
  Example:
  ```sh
  certutil -hashfile burpsuite_community_windows-x64_v2023_x_x_x.exe SHA256
  ```
- Compare the calculated hash with the hash provided on the PortSwigger website.
  - ✅ If they match, proceed to the next step.
  - ❌ If they do not match, delete the file and re-download it from the official source.

### 4. Install Burp Suite
- Navigate to the folder where the installer was downloaded.
- Double-click the `.exe` file (e.g., `burpsuite_community_windows-x64_v2023_x_x_x.exe`).
- If prompted by **User Account Control (UAC)**, click **Yes**.
- Follow the setup wizard:
  - Click **Next** on the welcome screen.
  - Choose the installation directory (default: `C:\Program Files\BurpSuite`).
  - Click **Next** to proceed.
  - Select additional options (e.g., create a desktop shortcut) if desired.
  - Click **Install** and wait for completion.
  - Click **Finish** to close the wizard.

### 5. Launch Burp Suite
- Locate the Burp Suite shortcut on your desktop or in the Start menu.
- Double-click the shortcut to launch the application.
- On first launch, you may be prompted to:
  - Accept the **End User License Agreement (EULA)**.
  - Choose between a temporary project or a saved configuration (**Temporary Project** is recommended for initial use).
- Click **Start Burp** to open the main interface.

### 6. Verify Installation
- Ensure the **Burp Suite dashboard** loads successfully.
- Check the **Target**, **Proxy**, and **Scanner** (if applicable) tabs to confirm functionality.
- If using the **Professional Edition**, enter your license key when prompted and activate it online.

### 7. Configure Browser (Optional)
To use Burp Suite with a web browser, configure it to route traffic through Burp Suite and install the CA certificate:

#### Set Up Proxy Settings:
- Open your browser (e.g., **Firefox, Chrome**).
- Navigate to the proxy settings:
  - **Firefox**: `Settings > General > Network Settings > Manual Proxy Configuration`
  - **Chrome**: Use system proxy settings or a proxy extension.
- Set the **HTTP Proxy** to `127.0.0.1` and **Port** to `8080` (Burp Suite’s default).
- Save the settings.

#### Install the Burp Suite CA Certificate:
- Ensure the **Proxy listener** is running (`127.0.0.1:8080`).
- Open your browser and navigate to `http://burp` (or `http://127.0.0.1:8080`).
- Click the **CA Certificate** link to download (e.g., `cacert.der`).
- Import the certificate into your browser:

  **For Firefox:**
  - `Settings > Privacy & Security > Certificates > View Certificates > Authorities > Import`
  - Select `cacert.der`, check **Trust this CA to identify websites**, and click **OK**.

  **For Chrome:**
  - `Settings > Privacy and Security > Security > Manage Certificates`
  - Switch to the **Trusted Root Certification Authorities** tab.
  - Click **Import**, browse to select `cacert.der`, and click **Next**.
  - Ensure it's placed in **Trusted Root Certification Authorities** and click **Finish**.

- Restart your browser.
- Test the setup by visiting an HTTPS website (e.g., `https://example.com`).
- If Burp Suite captures traffic in `Proxy > HTTP History`, the CA certificate is correctly installed.

### 8. Troubleshooting (If Needed)
- **If browser traffic isn’t intercepted:**
  - Verify **proxy settings** and ensure the **Burp Proxy listener** is running.
  - Check that the **CA certificate** is trusted by the browser.
- If errors persist, consult the [PortSwigger Troubleshooting Guide](https://portswigger.net/burp/documentation/desktop/troubleshooting/troubleshooting).

## Notes
- Always download Burp Suite from the **official PortSwigger website** to avoid malicious versions.
- **Verifying the hash value** ensures the integrity and authenticity of the downloaded file.
- Installing the **CA certificate** is essential for intercepting **HTTPS traffic** without SSL errors.
- For **Professional Edition** users, ensure an **active internet connection** during license activation.
- Regularly update Burp Suite to access the **latest features and security patches**.
