
# Commands I used in this project

This file lists all the commands I used to set up my cloud project on AWS EC2.  
Each command has an explanation about what it does and why it’s important.

---

## 1. SSH into EC2

```bash
ssh -i ~/.ssh/cloud-portfolio-key.pem ec2-user@<PUBLIC_IP>
````

**What it does:** Connects your local computer to the EC2 server securely over SSH. <br>
**Why it’s important:** You need this to run commands, install software, and manage your website remotely.

---

## 2. Update the server packages

```bash
sudo yum update -y
```

**What it does:** Updates all installed packages to the latest versions.

* `sudo` - runs as administrator.
* `-y` - automatically confirms updates.

**Why it’s important:** Keeps your server secure and ensures compatibility with the latest software.

---

## 3. Install software that I need (Apache, PHP)

```bash
sudo yum install httpd php -y
```

**What it does:** Installs Apache web server and PHP. <br>
**Why it’s important:** Apache serves your website files to visitors, and PHP allows dynamic content like the server time.

---

## 4. Start and enable services

```bash
sudo systemctl start httpd
sudo systemctl enable httpd
```

**What it does:**

* `start httpd` - starts Apache immediately
* `enable httpd` - makes Apache start automatically on reboot

**Why it’s important:** Ensures your website is always running, even after restarting the instance.

---

## 5. Check Apache status (this is optional but it's helpful for troubleshooting)

```bash
sudo systemctl status httpd
```

**What it does:** Shows whether Apache is running and displays recent logs.<br>
**Why it’s important:** Helps confirm that your server is working and troubleshoot errors.

---

## 6. Navigate to the website folder

```bash
cd /var/www/html
```

**What it does:** Moves into the folder where Apache serves web files.<br>
**Why it’s important:** This is where you place your `index.php` or HTML files so they can be seen in the browser.

---

## 7. Remove default Apache page

```bash
sudo rm /var/www/html/index.html
```

**What it does:** Deletes the default “It works!” page.<br>
**Why it’s important:** Clears the way for your own portfolio website files.

---

## 8. Create your own website page

```bash
sudo nano index.php
```

**What it does:** Opens a text editor to create your main PHP page.

**Example content:**

```php
<?php
echo "<h1>Welcome to My Cloud Portfolio</h1>";
echo "<p>Server Time: " . date('Y-m-d H:i:s') . "</p>";
?>
```

**Why it’s important:** This is the file Apache serves; PHP allows dynamic content like displaying the current server time.

---

## 9. Restart Apache after changes

```bash
sudo systemctl restart httpd
```

**What it does:** Restarts Apache to apply any changes in files or configuration.<br>
**Why it’s important:** Ensures your new files or edits are displayed correctly in the browser.

---

## 10. Configure Security Groups

**What it does:** Make sure your EC2 instance allows **HTTP (port 80)** and **HTTPS (port 443)** traffic. <br>

**Why it’s important:** By default, AWS blocks all traffic except SSH. Opening these ports lets anyone view your website.

---

## 11. Elastic IP setup (manual step in AWS Console)

**What it does:** Allocate an **Elastic IP** and attach it to your instance.<br>

**Why it’s important:** Gives your website a **permanent public IP**, so links in your portfolio or projects don’t break when the server restarts.

---

## Key Concepts Learned

* **SSH & key pairs:** secure remote access
* **Apache & PHP:** dynamic web hosting
* **Document root (`/var/www/html`)**: where your website lives
* **Security groups:** firewall controlling access
* **Elastic IP:** permanent public IP for consistent website links


