

# Launching a Windows EC2 Instance on AWS

This guide walks you through the process of launching a Windows-based EC2 instance on AWS, step-by-step.

---

## Step 1: Sign in to AWS Console

(screenshots-folder/Screenshot 1.png)

- Go to the [AWS Management Console](https://aws.amazon.com/console/).
- Click on the **Sign in** button at the top right corner.

---

## Step 2: Launch a New EC2 Instance – Name and OS

- Click **Launch Instance** from the EC2 dashboard.
- Under **Name and tags**, enter a name for your instance (e.g., `My Web Server`).
- Scroll down to **Application and OS Images**:
  - Select the operating system you want to install (such as Ubuntu, Windows, etc.).

---

## Step 3: Choose Instance Type and Set Up Key Pair

- **Instance Type**:  
  - Select an instance type from the list (e.g., `t3.micro`, `t2.micro`, etc.).  
  - Choose one that's eligible for the AWS Free Tier if you're just testing.

- **Key Pair (login)**:  
  - Select an existing key pair or click **Create new key pair**.
  - **Note**: For **Windows instances**, this key is used to decrypt the administrator password needed for remote login.

---

## Step 4: Configure Network and Firewall (Security Group)

- Under **Network settings**:
  - Keep the default **VPC** and **Subnet** unless you have a specific configuration.
  - Ensure **Auto-assign public IP** is **enabled**.

- Under **Firewall (security groups)**:
  - Select **Create security group**.
  - Make sure the following rules are enabled:
    - ✅ **Allow RDP traffic** from **Anywhere (0.0.0.0/0)** – Required for Windows Remote Desktop.
    - ✅ **Allow HTTPS traffic** from the internet.
    - ✅ **Allow HTTP traffic** from the internet.

> ⚠️ Allowing 0.0.0.0/0 means access from all IPs. For better security, restrict to known IPs.

---

## Step 5: Instance Launched Successfully

- Once the instance is launched, you'll see a green success message.
- Options available post-launch:
  - Click **Connect to instance** to access it.
  - Optionally create billing alerts, snapshot policies, or monitoring.

---

## Step 6: View and Connect to the Instance

- Go to the **Instances** section in the EC2 Dashboard.
- Your instance should show a green **Running** status.
- Select your instance and click **Connect**.
- Choose your connection method (RDP for Windows) and log in.

---

✅ Your Windows EC2 instance is now up and running!


---

## Step 7: Connect to Windows Instance via RDP

- On the instance details page, go to the **Connect** section and select the **RDP client** tab.
- Click **Download remote desktop file** – this `.rdp` file lets you launch a remote session quickly.
- Under **Password**, click **Get password**:
  - Upload your `.pem` key pair file to decrypt the administrator password.
- Use the following to log in:
  - **Public DNS** or IP address
  - **Username**: `Administrator`
  - **Decrypted password**

Open the `.rdp` file and enter your credentials to connect.

---

✅ Your Windows EC2 instance is fully set up and accessible via Remote Desktop.


### Step 7.1: Decrypt the Administrator Password

To get the password required for RDP login:

1. Click on **Get password**.
2. Click **Upload private key file** and select your `.pem` key pair file.
3. Then, click the **Decrypt password** button.
4. Copy the decrypted password and use it along with the Administrator username when logging in via RDP.

> 🔐 This step ensures you can securely access your Windows EC2 instance.

---

✅ You are now ready to securely log in and use your Windows EC2 server.
