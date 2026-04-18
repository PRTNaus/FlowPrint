> [!IMPORTANT]
> ⚠️ Project Status: On Hold/Private
> This project is currently **on hold**.
> Due to time constraints and other ongoing commitments, I am unable to develop the public facing repo. 
> If there is enough interest in this project, I will:
> ```
> - Publish the current working version
> - Provide updated documentation and relevant information
> - Outline next steps for anyone interested in continuing or contributing
> ```
> If this project is something you would like to see continued releases of, feel free to open an issue to express your interest.




# 🖨️ FlowPrint

<div align="center">

![FlowPrint Banner](https://img.shields.io/badge/Python-3.7+-blue.svg)
![License](https://img.shields.io/badge/License-GPL%203.0-green.svg)
![Status](https://img.shields.io/badge/Status-Active-success.svg)

**Automatic Email-to-Print Service for Shopify Orders**

*Turn your computer into a smart print server that automatically prints orders, receipts, and shipping labels from your email inbox.*

[🚀 Quick Start](#-quick-start) • [📖 Installation](#-installation) • [🛍️ Shopify Setup](#️-shopify-integration) • [❓ FAQ](#-faq)

</div>

---

## 📑 Table of Contents

- [What is FlowPrint?](#-what-is-flowprint)
- [How It Works](#-how-it-works)
- [Features](#-features)
- [Quick Start](#-quick-start)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Shopify Integration](#️-shopify-integration)
- [Email Server Setup](#-email-server-setup)
- [Running FlowPrint](#-running-flowprint)
- [Troubleshooting](#-troubleshooting)
- [FAQ](#-faq)
- [Security](#-security)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🎯 What is FlowPrint?

FlowPrint is a Python-based service that **monitors your email inbox and automatically prints HTML-formatted emails** using Google Chrome. It's perfect for Shopify store owners who want to automate their order printing workflow without expensive third-party services.

### Perfect For:
- 📦 **Shopify store owners** who need automated order printing
- 🏪 **Small businesses** looking to streamline fulfillment
- 📮 **Shipping departments** that handle high order volumes
- 🖨️ **Anyone** who needs to automatically print formatted emails

---

## 🔄 How It Works

```
┌─────────────┐         ┌──────────────┐         ┌─────────────┐
│   Shopify   │ ──────> │     Email    │ ──────> │  FlowPrint  │
│    Store    │ Order   │   Inbox      │ IMAP    │  Service    │
└─────────────┘ Created └──────────────┘ Monitor └─────────────┘
                                                         │
                                                         │ Auto Print
                                                         ▼
                                                   ┌──────────┐
                                                   │ Printer  │
                                                   │  🖨️      │
                                                   └──────────┘
```

1. **Customer places order** on your Shopify store
2. **Shopify Flow sends email** with order details to your monitored inbox
3. **FlowPrint detects the email** (by subject prefix like `[PRINT PACK]`)
4. **Chrome automatically prints** the formatted HTML email
5. **Order is ready** for picking and packing!

---

## ✨ Features

<table>
<tr>
<td width="50%">

### 🎨 **Modern Web Dashboard**
- Real-time status monitoring
- Live job statistics
- Easy configuration interface
- Dark/Light theme toggle

### 📧 **Smart Email Monitoring**
- IMAP inbox monitoring
- Customizable subject filters
- Duplicate detection
- Support for Gmail, Outlook, etc.

</td>
<td width="50%">

### 🖨️ **Automatic Printing**
- Chrome headless printing
- HTML email rendering
- Custom print settings
- Multi-page support

### 🔧 **Flexible & Reliable**
- Web-based configuration
- Detailed logging
- Temp file cleanup
- Cross-platform support

</td>
</tr>
</table>

---

## 🚀 Quick Start

**Get FlowPrint running in 3 minutes:**

```bash
# 1. Clone the repository
git clone https://github.com/NotDonaldTrump/FlowPrint.git
cd FlowPrint

# 2. Run FlowPrint (auto-installs dependencies)
python FlowPrint.py
```

That's it! FlowPrint will:
- ✅ Check for and install any missing dependencies
- ✅ Open the web dashboard in your browser
- ✅ Guide you through configuration

> **Note:** First-time users should set up in manual mode to configure printer settings. [See Installation Guide](#-installation)

---

## 📖 Installation

### Prerequisites

Before installing FlowPrint, ensure you have:

| Requirement | Download Link | Notes |
|------------|---------------|-------|
| **Python 3.7+** | [python.org](https://www.python.org/downloads/) | ✅ Check "Add Python to PATH" during install |
| **Google Chrome** | [google.com/chrome](https://www.google.com/chrome/) | Must be installed in default location |
| **Email Account** | - | Gmail, Outlook, or any IMAP-enabled email |

### Step-by-Step Installation

#### 1️⃣ Download FlowPrint

**Option A: Git Clone (Recommended)**
```bash
git clone https://github.com/NotDonaldTrump/FlowPrint.git
cd FlowPrint
```

**Option B: Download ZIP**
1. Go to [GitHub Repository](https://github.com/NotDonaldTrump/FlowPrint)
2. Click "Code" → "Download ZIP"
3. Extract the ZIP file
4. Open terminal/command prompt in the extracted folder

#### 2️⃣ First Run

```bash
python FlowPrint.py
```

FlowPrint will automatically:
- ✅ Detect missing Python packages
- ✅ Install Flask, Flask-SocketIO, and dependencies
- ✅ Open web dashboard at `http://localhost:5000`

> **Windows Users:** If Python isn't recognized, use `python3` or `py` instead of `python`

#### 3️⃣ Configure Your Settings

The web dashboard will open automatically. You'll need to configure:

**Email Settings:**
- IMAP Server (e.g., `imap.gmail.com`)
- Email address and password/app password
- Mailbox folder (usually `Inbox`)

**Behavior Settings:**
- Subject prefix filter (e.g., `[PRINT PACK]`)
- Polling interval (how often to check for emails)
- Auto-print enabled/disabled

[See Configuration Guide](#-configuration) for detailed settings.

---

## ⚙️ Configuration

FlowPrint is configured through the **web dashboard** at `http://localhost:5000`

### 📧 Email Settings Tab

Configure your email server connection:

| Setting | Example | Description |
|---------|---------|-------------|
| **IMAP Server** | `imap.gmail.com` | Your email provider's IMAP server |
| **Port** | `993` | IMAP SSL port (usually 993) |
| **Use SSL** | ✅ Enabled | Always use SSL for security |
| **Email Address** | `orders@mystore.com` | Your email account |
| **Password** | `app-password-here` | Email password or app-specific password |
| **Mailbox** | `Inbox` | Folder to monitor |

### 🔧 Behavior Settings Tab

Configure how FlowPrint processes emails:

| Setting | Default | Description |
|---------|---------|-------------|
| **Polling Interval** | `30` seconds | How often to check for new emails |
| **Subject Prefix** | `[PRINT PACK]` | Only emails starting with this will print |
| **Auto Print** | ✅ Enabled | Automatically print without dialog |
| **Delete After Print** | ❌ Disabled | Delete email after successful print |

> ⚠️ **Warning:** Only enable "Delete After Print" after thorough testing!

### ⚙️ Advanced Settings Tab

Fine-tune performance and behavior:

| Setting | Default | Description |
|---------|---------|-------------|
| **Chrome Path** | Auto-detect | Custom Chrome installation path |
| **Print Wait Time** | `8` seconds | How long to wait before closing Chrome |
| **Temp Cleanup** | ✅ Enabled | Automatically clean temporary files |
| **Cleanup Interval** | `6` hours | How often to cleanup temp files |

---

## 🛍️ Shopify Integration

FlowPrint integrates with Shopify using **Shopify Flow** to automatically send order notifications that get printed.

### 📋 Shopify Flow Setup Overview

```
Shopify Order Created → Shopify Flow → Send Email → FlowPrint → Printer
```

### Step-by-Step Shopify Flow Configuration

#### 1️⃣ Access Shopify Flow

Navigate to: **Shopify Admin → Apps → Shopify Flow**

> **Don't see Flow?** You need Shopify Plus, or install the [Shopify Flow app](https://apps.shopify.com/flow) (available on Advanced plans)

#### 2️⃣ Create New Workflow

1. Click **"Create workflow"**
2. Name it: `FlowPrint - Auto Print Orders`
3. Add a description (optional)

#### 3️⃣ Add Trigger

**Choose Trigger:** `Order created`

This fires when any new order is placed in your store.

**Optional Filters** (click "Add condition"):
- ✅ Financial status = Paid
- ✅ Fulfillment status = Unfulfilled
- ✅ Shipping method = specific methods
- ✅ Order tags = specific tags

#### 4️⃣ Add Email Action

1. Click **"Then..."** → **"Add action"**
2. Search for: **"Send internal email"**
3. Configure email:

**📧 To:** Your monitored email (e.g., `orders@mystore.com`)

**📝 Subject:**
```
[PRINT PACK] Order {{order.name}}
```

> ⚠️ **CRITICAL:** Subject MUST start with your configured prefix (default: `[PRINT PACK]`)

**📄 Body:** Use the provided template below or create your own

#### 5️⃣ Shopify Flow Email Template

FlowPrint includes a complete example template: `example-shopify-flow-email-template.html`

This template includes:
- 📄 **Page 1:** Staff summary with key order details
- 📄 **Page 2:** Detailed packing list with all items
- 📄 **Page 3:** Customer shipping address (large, easy to read)

**To use the template:**

1. Open `example-shopify-flow-email-template.html` in a text editor
2. Customize the store name and logo section
3. Copy the entire HTML content
4. Paste into the "Body" field in Shopify Flow
5. Customize any additional fields as needed

**Key Liquid Variables Available:**
- `{{order.name}}` - Order number
- `{{order.customer.firstName}}` - Customer first name
- `{{order.email}}` - Customer email
- `{{order.currentTotalPrice}}` - Order total
- `{{order.shippingAddress.address1}}` - Shipping address
- And many more! [See Shopify Liquid docs](https://shopify.dev/docs/api/liquid)

#### 6️⃣ Test Your Workflow

1. Click **"Turn on workflow"** in Shopify Flow
2. Place a test order in your store
3. Watch FlowPrint dashboard for incoming email
4. Verify print output matches your expectations

### 📝 Customizing Print Templates

**Tips for great print templates:**

✅ **DO:**
- Use clear, readable fonts (Arial, Helvetica)
- Include page breaks: `<div class="page-break"></div>`
- Use high contrast (black text on white background)
- Test print output before going live
- Include all information pickers need

❌ **DON'T:**
- Use tiny font sizes (< 10pt)
- Rely on color coding alone
- Create overly complex layouts
- Forget to test with real order data

---

## 📧 Email Server Setup

### Gmail Configuration

Gmail requires an **App Password** for IMAP access:

#### Step 1: Enable 2-Step Verification
1. Go to [Google Account Security](https://myaccount.google.com/security)
2. Enable **2-Step Verification** if not already enabled

#### Step 2: Create App Password
1. Scroll to **"App passwords"** section
2. Click **"Select app"** → Choose **"Mail"**
3. Click **"Select device"** → Choose **"Other"** → Enter "FlowPrint"
4. Click **"Generate"**
5. Copy the 16-character password (no spaces)

#### Step 3: Enable IMAP
1. Open [Gmail Settings](https://mail.google.com/mail/u/0/#settings/fwdandpop)
2. Go to **"Forwarding and POP/IMAP"** tab
3. Enable **"IMAP access"**
4. Click **"Save Changes"**

#### FlowPrint Configuration for Gmail:
```
IMAP Server: imap.gmail.com
Port: 993
Use SSL: ✅ Enabled
Email: your-email@gmail.com
Password: [16-character app password]
```

---

### Outlook/Hotmail Configuration

#### Step 1: Enable IMAP Access
IMAP is enabled by default for Outlook.com accounts

#### Step 2: Allow Less Secure Apps (if needed)
1. Go to [Microsoft Account Security](https://account.microsoft.com/security)
2. Check for any security alerts
3. Approve FlowPrint access if prompted

#### FlowPrint Configuration for Outlook:
```
IMAP Server: outlook.office365.com
Port: 993
Use SSL: ✅ Enabled
Email: your-email@outlook.com
Password: [your account password]
```

---

### Custom Email Server

Using a custom email server? You'll need:

| Information | Where to Find |
|-------------|---------------|
| **IMAP Server Address** | Contact your email provider or IT admin |
| **IMAP Port** | Usually `993` (SSL) or `143` (non-SSL) |
| **SSL Enabled** | Recommended for security |
| **Username** | Usually your full email address |
| **Password** | Your email account password |

**Common Business Email Providers:**

| Provider | IMAP Server | Port |
|----------|-------------|------|
| **Google Workspace** | `imap.gmail.com` | 993 |
| **Microsoft 365** | `outlook.office365.com` | 993 |
| **Yahoo Mail** | `imap.mail.yahoo.com` | 993 |
| **iCloud Mail** | `imap.mail.me.com` | 993 |
| **Zoho Mail** | `imap.zoho.com` | 993 |

---

## 🏃 Running FlowPrint

### Manual Mode (Testing & Setup)

**Recommended for first-time setup:**

```bash
python FlowPrint.py
```

1. Dashboard opens at `http://localhost:5000`
2. Configure your email settings
3. Click **"Save"** to save configuration
4. Click **"Start"** to begin monitoring
5. Send a test email with your subject prefix
6. Verify the print settings and output
7. Adjust Chrome print settings if needed

**First Print Setup:**
- FlowPrint will open Chrome's print dialog on first run
- Set your default printer
- Configure paper size, orientation, margins
- Check "System dialog" if you need advanced options
- These settings are saved automatically

---

### Running as a Service

Once you've tested and configured FlowPrint, run it as a system service for automatic startup.

#### 🪟 Windows - Task Scheduler

**Option 1: Basic Startup (Current User)**

1. Press `Win + R`, type `shell:startup`, press Enter
2. Create a shortcut to `FlowPrint.py`
3. Right-click shortcut → Properties
4. Set "Target" to:
   ```
   C:\Path\To\python.exe "C:\Path\To\FlowPrint\FlowPrint.py"
   ```
5. Click OK

**Option 2: Task Scheduler (All Users, Best for Production)**

1. Open **Task Scheduler** (`taskschd.msc`)
2. Click **"Create Basic Task"**
3. Name: `FlowPrint Service`
4. Trigger: **"When the computer starts"**
5. Action: **"Start a program"**
6. Program: `C:\Path\To\python.exe`
7. Arguments: `"C:\Path\To\FlowPrint\FlowPrint.py"`
8. Start in: `C:\Path\To\FlowPrint`
9. Check **"Run whether user is logged on or not"**
10. Check **"Run with highest privileges"**

---

#### 🐧 Linux - systemd Service

**Create service file:**

```bash
sudo nano /etc/systemd/system/flowprint.service
```

**Add this content:**

```ini
[Unit]
Description=FlowPrint Automatic Email-to-Print Service
After=network.target

[Service]
Type=simple
User=yourusername
WorkingDirectory=/path/to/FlowPrint
ExecStart=/usr/bin/python3 /path/to/FlowPrint/FlowPrint.py
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

**Enable and start:**

```bash
# Reload systemd
sudo systemctl daemon-reload

# Enable service (start on boot)
sudo systemctl enable flowprint

# Start service now
sudo systemctl start flowprint

# Check status
sudo systemctl status flowprint

# View logs
sudo journalctl -u flowprint -f
```

**Useful commands:**
```bash
sudo systemctl stop flowprint     # Stop service
sudo systemctl restart flowprint  # Restart service
sudo systemctl disable flowprint  # Disable auto-start
```

---

#### 🍎 macOS - launchd

**Create plist file:**

```bash
nano ~/Library/LaunchAgents/com.flowprint.plist
```

**Add this content:**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.flowprint</string>
    
    <key>ProgramArguments</key>
    <array>
        <string>/usr/local/bin/python3</string>
        <string>/path/to/FlowPrint/FlowPrint.py</string>
    </array>
    
    <key>WorkingDirectory</key>
    <string>/path/to/FlowPrint</string>
    
    <key>RunAtLoad</key>
    <true/>
    
    <key>KeepAlive</key>
    <true/>
    
    <key>StandardOutPath</key>
    <string>/tmp/flowprint.log</string>
    
    <key>StandardErrorPath</key>
    <string>/tmp/flowprint.error.log</string>
</dict>
</plist>
```

**Load and start:**

```bash
# Load the service
launchctl load ~/Library/LaunchAgents/com.flowprint.plist

# Unload (stop)
launchctl unload ~/Library/LaunchAgents/com.flowprint.plist

# View logs
tail -f /tmp/flowprint.log
```

---

## 🔧 Troubleshooting

### Common Issues & Solutions

<details>
<summary><b>🔴 "Authentication Failed" Error</b></summary>

**Problem:** Can't connect to email server

**Solutions:**
1. ✅ Gmail users: Create and use an **App Password** (not regular password)
2. ✅ Outlook users: Ensure IMAP is enabled
3. ✅ All users: Double-check username and password (no typos!)
4. ✅ Verify IMAP server address is correct
5. ✅ Check port is 993 with SSL enabled
6. ✅ Disable 2FA temporarily to test (not recommended long-term)

</details>

<details>
<summary><b>🔴 Nothing Prints When Email Arrives</b></summary>

**Problem:** Emails detected but not printing

**Solutions:**
1. ✅ Check "Auto Print Enabled" is turned ON in dashboard
2. ✅ Verify default printer is set in your OS
3. ✅ Ensure printer is online and has paper/ink
4. ✅ Check `flowprint.log` file for error messages
5. ✅ Test print from another application to verify printer works
6. ✅ Try increasing "Chrome Print Wait Time" to 15 seconds

</details>

<details>
<summary><b>🔴 Prints Are Cut Off or Incomplete</b></summary>

**Problem:** Printed output is truncated

**Solutions:**
1. ✅ Increase "Chrome Print Wait Time" to 15+ seconds
2. ✅ Check paper size matches template design (usually Letter or A4)
3. ✅ Verify printer settings (margins, orientation)
4. ✅ Test with simpler template to isolate issue
5. ✅ Check Chrome print preview (disable auto-print temporarily)

</details>

<details>
<summary><b>🔴 "Chrome Not Found" Error</b></summary>

**Problem:** FlowPrint can't locate Google Chrome

**Solutions:**
1. ✅ Install Google Chrome from [google.com/chrome](https://www.google.com/chrome/)
2. ✅ Install in default location (don't use portable version)
3. ✅ Windows: Check `C:\Program Files\Google\Chrome\Application\chrome.exe` exists
4. ✅ Mac: Check `/Applications/Google Chrome.app` exists
5. ✅ Linux: Install via `sudo apt install google-chrome-stable`
6. ✅ Or set custom path in "Advanced Settings" → "Chrome Path"

</details>

<details>
<summary><b>🔴 Dashboard Won't Open</b></summary>

**Problem:** Browser doesn't open or shows error

**Solutions:**
1. ✅ Manually open browser and go to `http://localhost:5000`
2. ✅ Check port 5000 isn't already in use by another app
3. ✅ Try different port (edit `FlowPrint.py` if needed)
4. ✅ Check firewall isn't blocking Python
5. ✅ Verify Flask installed correctly: `pip list | grep Flask`

</details>

<details>
<summary><b>🔴 High CPU Usage</b></summary>

**Problem:** FlowPrint uses too much CPU

**Solutions:**
1. ✅ Increase polling interval (try 60 seconds instead of 30)
2. ✅ Disable temp file cleanup if not needed
3. ✅ Check for stuck Chrome processes: `ps aux | grep chrome`
4. ✅ Restart FlowPrint service
5. ✅ Review `flowprint.log` for repeated errors

</details>

<details>
<summary><b>🔴 Duplicate Prints</b></summary>

**Problem:** Same email prints multiple times

**Solutions:**
1. ✅ Don't run multiple FlowPrint instances on same email
2. ✅ Check `printed_uids.txt` file exists and isn't corrupted
3. ✅ Verify polling interval isn't too short (minimum 15 seconds)
4. ✅ Ensure email isn't being moved/copied to monitored folder repeatedly

</details>

### 📋 Viewing Logs

**Log file location:** `flowprint.log` in FlowPrint directory

**View logs:**

```bash
# Windows (PowerShell)
Get-Content flowprint.log -Tail 50 -Wait

# Linux/Mac
tail -f flowprint.log

# Search for errors
grep ERROR flowprint.log
```

**Log format:**
```
[2024-11-18 14:30:22] [INFO] Service started
[2024-11-18 14:30:25] [SUCCESS] Connected to mailbox
[2024-11-18 14:31:10] [SUCCESS] Printed: Order #1234
[2024-11-18 14:32:00] [ERROR] Print failed: Chrome timeout
```

---

## ❓ FAQ

<details>
<summary><b>Q: Do I need Shopify to use FlowPrint?</b></summary>

**A:** No! FlowPrint works with **any email source**. While it's designed for Shopify stores, you can use it with:
- WooCommerce
- BigCommerce
- Etsy
- eBay
- Any system that sends HTML emails
- Manual emails you send yourself

Just ensure emails have the correct subject prefix.

</details>

<details>
<summary><b>Q: Can I print to multiple printers?</b></summary>

**A:** Currently FlowPrint prints to your system's default printer. To use multiple printers:
- Run multiple FlowPrint instances (different folders)
- Use different email addresses or subject prefixes for each
- Change default printer between instances
- Or modify the code to specify printers (advanced)

</details>

<details>
<summary><b>Q: Can I print to PDF instead of a physical printer?</b></summary>

**A:** Yes! Set your default printer to:
- Windows: "Microsoft Print to PDF"
- Mac: "Save as PDF"
- Linux: "Print to File"

</details>

<details>
<summary><b>Q: How many emails can FlowPrint handle per hour?</b></summary>

**A:** FlowPrint has been tested with **100+ emails per hour**. Performance depends on:
- Print speed of your printer
- Complexity of email templates
- Chrome print wait time setting
- Computer specifications

</details>

<details>
<summary><b>Q: What happens if my computer restarts?</b></summary>

**A:** If you've set up FlowPrint as a service (see [Running as a Service](#running-as-a-service)), it will:
- ✅ Automatically start when computer boots
- ✅ Resume monitoring from where it left off
- ✅ Not reprint already-printed emails (tracked in `printed_uids.txt`)

</details>

<details>
<summary><b>Q: Is my email password secure?</b></summary>

**A:** FlowPrint stores your password in `flowprint_config.json` as plain text on your local computer. Security recommendations:
- ✅ Use app-specific passwords (Gmail, Outlook)
- ✅ Keep FlowPrint computer physically secure
- ✅ Don't share the config file
- ✅ Use a dedicated email account for printing only
- ✅ For production, consider environment variables (advanced)

</details>

<details>
<summary><b>Q: Can multiple computers monitor the same email?</b></summary>

**A:** Not recommended - this causes duplicate prints. Instead:
- Use one FlowPrint instance per email account
- Or use different subject prefixes for different printers
- Or use email folders and have each instance monitor a different folder

</details>

<details>
<summary><b>Q: Does FlowPrint have a web dashboard?</b></summary>

**A:** Yes! FlowPrint includes a modern web dashboard at `http://localhost:5000` with:
- Real-time service status
- Live job statistics
- Configuration interface
- Dark/Light theme toggle
- Manual email checking
- Recent job history

</details>

<details>
<summary><b>Q: Can I customize the email templates?</b></summary>

**A:** Yes! FlowPrint prints whatever HTML is in the email body. You can:
- Modify the included `example-shopify-flow-email-template.html`
- Create your own templates using HTML/CSS
- Use Shopify Flow's email editor
- Add your own branding, logos, colors
- Include multiple pages with page breaks

</details>

<details>
<summary><b>Q: What if I delete the printed_uids.txt file?</b></summary>

**A:** FlowPrint will reprint all emails in your inbox that match the subject prefix. To safely reset:
1. Stop FlowPrint service
2. Delete `printed_uids.txt`
3. Manually clean out your email inbox (or use a different folder)
4. Start FlowPrint service

</details>

---

## 🔐 Security

### Best Practices

#### ✅ Email Security
- **Use app-specific passwords** (Gmail, Outlook, etc.) instead of main account passwords
- **Enable 2FA** on your email account
- **Use SSL** for all IMAP connections (always enabled in FlowPrint)
- **Dedicated email account** - Consider a separate email just for printing
- **Regular password rotation** - Change passwords periodically

#### ✅ Physical Security
- **Printed documents contain customer data** - Ensure physical security of printer area
- **Secure the computer** running FlowPrint - Use password protection
- **Lock the room** where printer is located if handling sensitive information

#### ✅ Configuration Security
- **Don't commit passwords to Git** - Add `flowprint_config.json` to `.gitignore`
- **Restrict file permissions** on Linux/Mac:
  ```bash
  chmod 600 flowprint_config.json
  ```
- **Use environment variables** for production (advanced users):
  ```python
  import os
  IMAP_PASSWORD = os.getenv('FLOWPRINT_PASSWORD', 'fallback')
  ```

#### ✅ Network Security
- **Use secure networks** - Avoid public WiFi when possible
- **Consider VPN** for remote FlowPrint servers
- **Firewall rules** - Restrict access to port 5000 if needed

#### ⚠️ Delete After Print Warning

The "Delete Email After Print" option is available but **use with extreme caution**:

- ❌ **Don't enable** until thoroughly tested
- ❌ **Don't rely** on this as your only order record
- ✅ **Do maintain** separate order backups (Shopify has this built-in)
- ✅ **Do test** extensively in a test environment first
- ✅ **Consider** using email rules to move to "Processed" folder instead

---

## 🤝 Contributing

Contributions are welcome! FlowPrint is open-source and community-driven.

### How to Contribute

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/amazing-feature`
3. **Make your changes**
4. **Test thoroughly** (see testing guidelines below)
5. **Commit your changes**: `git commit -m 'Add amazing feature'`
6. **Push to the branch**: `git push origin feature/amazing-feature`
7. **Open a Pull Request**

### Testing Guidelines

Before submitting a PR, please test:

- ✅ Different email providers (Gmail, Outlook, etc.)
- ✅ Both auto-print and manual print modes
- ✅ Various email template formats
- ✅ Error handling (wrong credentials, network issues)
- ✅ Startup/shutdown behavior
- ✅ Cross-platform compatibility (if possible)

### Code Style

- Follow [PEP 8](https://pep8.org/) Python style guide
- Add comments for complex logic
- Update README for new features
- Keep functions focused and modular
- Maintain existing code structure

### Reporting Issues

Found a bug? Please create an issue with:

- **Clear description** of the problem
- **Steps to reproduce**
- **Expected vs actual behavior**
- **Your environment**: OS, Python version, email provider
- **Log excerpts** from `flowprint.log` (remove sensitive info!)

### Feature Requests

Have an idea? Create an issue describing:

- **What problem** it solves
- **How it would work**
- **Why it would be useful** to other users

---

## 📜 License

This project is licensed under the **GNU General Public License v3.0**.

### What This Means:

✅ **You CAN:**
- Use FlowPrint commercially
- Modify the source code
- Distribute modified versions
- Use it privately

❌ **You MUST:**
- Keep the same GPL-3.0 license
- Disclose source code of modifications
- State changes you made
- Include the original copyright notice

📄 **Full license:** See [LICENSE](LICENSE) file

---

## 🙏 Acknowledgments

- Built for the **Shopify community**
- Inspired by the need for **simple, reliable automated printing**
- Thanks to all **contributors and users**!

---

## 📞 Support & Links

- 🐛 **Issues**: [GitHub Issues](https://github.com/NotDonaldTrump/FlowPrint/issues)
- 📂 **Repository**: [github.com/NotDonaldTrump/FlowPrint](https://github.com/NotDonaldTrump/FlowPrint)
- 📖 **Documentation**: This README
- 💬 **Discussions**: [GitHub Discussions](https://github.com/NotDonaldTrump/FlowPrint/discussions)

---

<div align="center">

**Made with ❤️ for the Shopify community**

⭐ **Star this repo** if FlowPrint helps your business!

</div>
