# Server Content

![Platform](https://img.shields.io/badge/platform-linux-lightgrey.svg)
![Go](https://img.shields.io/badge/Go-1.24-blue.svg)

API สำหรับจัดการ content metadata และ video stream

## 🚀 Quick Install (One-line)

```bash
# ติดตั้งทั้ง App + Nginx
curl -fsSL https://raw.githubusercontent.com/zergolf1994/server-content-releases/main/install.sh | sudo -E bash -s -- \
    --port 8082 \
    --domain content.vdohide.com \
    --mongodb-uri "mongodb+srv://user:pass@host/dbname"
```

## 🛠️ Manual Installation

```bash
# Download
chmod +x install.sh

# ติดตั้งทั้งหมด (App + Nginx) ด้วยค่า default
sudo ./install.sh

# ติดตั้งแบบกำหนดค่าเอง
sudo ./install.sh --port 8082 --domain content.vdohide.com --mongodb-uri "mongodb+srv://..."

# ติดตั้งเฉพาะ App
sudo ./install.sh --app --port 8082 --mongodb-uri "mongodb+srv://..."

# ติดตั้งเฉพาะ Nginx
sudo ./install.sh --nginx --domain content.vdohide.com --port 8082

# อัปเดต App อย่างเดียว (ไม่แตะ Nginx)
sudo ./install.sh --app
```

## 🗑️ Uninstall

```bash
curl -fsSL https://raw.githubusercontent.com/zergolf1994/server-content-releases/main/install.sh | sudo -E bash -s -- \
    --uninstall
```

## 📡 API Usage

### Health Check
```
GET /health
```

### Response
```json
{
  "success": true,
  "data": { ... }
}
```

## ⚙️ Service Management

```bash
# Status
systemctl status server-content

# Logs
journalctl -u server-content -f

# Restart
sudo systemctl restart server-content

# Stop
sudo systemctl stop server-content
```

## 📋 Install Options

| Option | Default | Description |
|--------|---------|-------------|
| `--app` | — | ติดตั้ง/อัปเดตเฉพาะ Application |
| `--nginx` | — | ติดตั้ง/อัปเดตเฉพาะ Nginx config |
| `-p, --port` | `8082` | HTTP port |
| `-d, --domain` | `content.vdohide.com` | Domain name สำหรับ Nginx |
| `--mongodb-uri` | — | MongoDB connection string |
| `--uninstall` | — | ลบทั้งหมด (binary, service, nginx config) |
| `-h, --help` | — | แสดง help |

> **Note:** ถ้าไม่ระบุ `--app` หรือ `--nginx` จะติดตั้งทั้ง 2 component
