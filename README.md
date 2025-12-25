Here is a **GitHub-ready `README.md`** you can copy-paste directly into your repository.
It’s clean, professional, and formatted using standard Markdown.

---

````md
# Splunk Enterprise Installation on AWS Linux (EC2)

This repository provides a **step-by-step guide** to install and run **Splunk Enterprise 9.0.1** on an **AWS EC2 Linux instance**.

---

## 📌 Prerequisites

Before starting, ensure you have:

- An AWS EC2 instance (Amazon Linux 2 / RHEL / CentOS / Ubuntu)
- Instance type: `t2.medium` or higher (recommended)
- Minimum **2 GB RAM**
- Root or `sudo` access
- Internet connectivity
- Port **8000** open in the EC2 Security Group

---

## 🔐 AWS Security Group Configuration

Add the following **Inbound Rule** to your EC2 Security Group:

| Type        | Protocol | Port | Source        |
|-------------|----------|------|---------------|
| Custom TCP  | TCP      | 8000 | Your IP / 0.0.0.0/0 |

⚠️ **Note:** For production environments, restrict access to trusted IPs only.

---

## 🚀 Installation Steps

### Step 1: Connect to Your EC2 Instance

```bash
ssh -i your-key.pem ec2-user@<EC2_PUBLIC_IP>
````

> Use `ubuntu@<EC2_PUBLIC_IP>` for Ubuntu instances.

---

### Step 2: Navigate to `/opt` Directory

```bash
cd /opt
```

---

### Step 3: Download Splunk Enterprise

```bash
wget -O splunk-9.0.1-82c987350fde-Linux-x86_64.tgz \
https://download.splunk.com/products/splunk/releases/9.0.1/linux/splunk-9.0.1-82c987350fde-Linux-x86_64.tgz
```

---

### Step 4: Extract the Package

```bash
tar xvzf splunk-9.0.1-82c987350fde-Linux-x86_64.tgz
```

This will create the directory:

```bash
/opt/splunk
```

---

### Step 5: Start Splunk Enterprise

```bash
cd /opt/splunk/bin
sudo ./splunk start --accept-license
```

During the first startup:

* Accept the license agreement
* Create an **admin username and password**

---

### Step 6: Enable Splunk at Boot

```bash
sudo ./splunk enable boot-start
```

This ensures Splunk starts automatically after system reboots.

---

## 🌐 Access Splunk Web Interface

Open your browser and navigate to:

```
http://<EC2_PUBLIC_IP>:8000
```

Example:

```
http://3.237.40.224:8000
```

Log in using the admin credentials you created earlier.

---

## 🛠 Common Splunk Commands

| Action       | Command                               |
| ------------ | ------------------------------------- |
| Start Splunk | `sudo /opt/splunk/bin/splunk start`   |
| Stop Splunk  | `sudo /opt/splunk/bin/splunk stop`    |
| Restart      | `sudo /opt/splunk/bin/splunk restart` |
| Check Status | `sudo /opt/splunk/bin/splunk status`  |

---

## 📁 Important Directories

* **Splunk Home:** `/opt/splunk`
* **Configuration Files:** `/opt/splunk/etc`
* **Logs:** `/opt/splunk/var/log/splunk`

---

## 📈 Next Steps

* Add data sources: **Settings → Add Data**
* Install apps: **Apps → Find More Apps**
* Configure indexes and inputs
* Enable SSL and role-based access
* Set up Universal Forwarders

---

## ⚠️ Notes

* Suitable for **learning, labs, and demos**
* For production deployments, consider:

  * Dedicated EBS volumes
  * SSL/TLS configuration
  * Backups and monitoring
  * Indexer and Search Head separation

---

## 📜 License

Splunk Enterprise is subject to Splunk’s license terms.
Refer to the official Splunk documentation for licensing details.


