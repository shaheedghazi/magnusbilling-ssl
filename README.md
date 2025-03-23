Here are the **correct and simplest steps** to set up **SSL with Certbot** on **Debian 12** for **MagnusBilling**:

---

### **Step 1: Update System & Install Certbot**
Run the following commands to update your system and install Certbot with the Apache plugin:
```bash
apt update && apt upgrade -y
apt install -y certbot python3-certbot-apache
```

---

### **Step 2: Run Certbot to Obtain and Install SSL**
Let Certbot do the work:
```bash
certbot --apache -d voip.vfree.one
```
- It will:
  - Verify your domain.
  - Obtain an SSL certificate from Let's Encrypt.
  - Configure Apache to use the certificate.
  - Set up automatic HTTP → HTTPS redirection (if you choose this option).

---

### **Step 3: Verify SSL Installation**
Once Certbot finishes, test if your SSL certificate is working:
- Open **https://voip.vfree.one** in your browser.
- Check your certificate status with:
  ```bash
  certbot certificates
  ```

---

### **Step 4: Enable Automatic Renewal**
Certbot should automatically renew your SSL certificate. Ensure the renewal service is active:
```bash
systemctl enable certbot.timer
systemctl start certbot.timer
```
You can test renewal with:
```bash
certbot renew --dry-run
```

---

✅ **That’s it!** Certbot automatically handled the SSL installation and Apache configuration for you. 🚀
