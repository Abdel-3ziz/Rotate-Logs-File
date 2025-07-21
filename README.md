# 🔁 Log Rotation & Cleanup Script (Bash)

This Bash script automates log management by rotating large log files and cleaning up old compressed logs. It's ideal for system administrators and developers who want to prevent disk usage spikes and manage logs efficiently.

---

## 📁 Project Structure

```bash
logrotate.sh    # Main script to handle log rotation and cleanup
```

---

## ⚙️ Features

- 📦 Rotates `.log` files larger than **5MB**
- 🗜️ Compresses rotated logs using `gzip`
- 🧹 Deletes `.gz` logs older than **30 days**
- 📍 Targets logs in: `/var/log/myapp`

---

## 📄 How It Works

### 🔄 `rotate_logs` Function
- Checks all `.log` files in the target directory.
- If the file size exceeds **5MB**, it:
  1. Renames it with the current date suffix (e.g., `app.log.250721`)
  2. Compresses it with `gzip`

### 🧼 `clean_old_logs` Function
- Finds all `.gz` files older than **30 days**
- Deletes them to free up disk space

---

## 🚀 Usage

1. **Make the script executable:**

```bash
chmod +x logrotate.sh
```

2. **Run the script manually:**

```bash
sudo ./logrotate.sh
```

> ⚠️ Requires `sudo` if writing to `/var/log/`  
> Make sure the directory `/var/log/myapp` exists and is writable.

---

## 🔧 Configuration

You can adjust these variables in the script as needed:

```bash
LOG_DIR="/var/log/myapp"
MAX_LOG_SIZE=5000000   # Size in bytes (5MB)
MAX_LOG_AGE=30         # Days to keep compressed logs
```

---

## 🗓️ Automate with Crontab

To automate the log rotation daily at 2 AM:

```bash
sudo crontab -e
```

Add this line:

```bash
0 2 * * * /path/to/logrotate.sh
```

---

## 📌 Example Output

```bash
Log rotated: /var/log/myapp/server.log
Old logs cleaned up
```

---

## 📌 Author

**Abdelaziz Hassan**  
System Tools | GitHub: [Abdel-3ziz]
