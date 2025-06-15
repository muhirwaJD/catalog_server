# 📦 Catalog Server

A simple Flask-based product catalog server backed by a MySQL database and hosted on an AWS EC2 instance. The app exposes RESTful API endpoints for managing product data.

---

## 🚀 Features

- View all products (`GET /products`)
- Built using Flask and SQLAlchemy
- Uses MySQL as the backend database (hosted on AWS RDS)
- Environment variables managed via `.env`
- Production-ready deployment using NGINX as a reverse proxy

---

## 🛠️ Technologies Used

- Python 3.12
- Flask
- SQLAlchemy
- PyMySQL
- dotenv
- MySQL (RDS)
- AWS EC2 (Ubuntu)
- NGINX
- systemd or tmux for persistent hosting

---

## 📂 Project Structure

```
catalog_server/
├── app.py
├── models.py
├── .env
├── requirements.txt
└── venv/
```

---

## ⚙️ Setup Instructions

### 1. Clone the Repo
```bash
git clone https://github.com/your-user/catalog_server.git
cd catalog_server
```

### 2. Create a Python Virtual Environment
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Requirements
```bash
pip install -r requirements.txt
```

### 4. Set Environment Variables
Create a `.env` file in the root directory:
```env
DB_HOST=your-rds-endpoint
DB_PORT=3306
DB_USER=catalog_user
DB_PASSWORD=your_password
DB_NAME=catalog
```

### 5. Run Flask App (Development)
```bash
python app.py
```

OR with tmux for persistent hosting:
```bash
tmux new -s flaskapp
python app.py
```

---

## 🖥️ Access
Once running, access your app at:

- EC2 Public IP (e.g., `http://<EC2_IP>/products`)
- Or your configured domain (e.g., `http://catalog-server.infy.uk/products`)

---

## 🧱 NGINX Setup (Optional)

Example `/etc/nginx/sites-available/catalog` config:
```nginx
server {
    listen 80;
    server_name your-domain.com;

    location / {
        proxy_pass http://127.0.0.1:5000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```
Then link and reload:
```bash
sudo ln -s /etc/nginx/sites-available/catalog /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx
```

---

## 📬 Sample Response
```json
[
  {
    "id": 1,
    "name": "Laptop",
    "description": "A high-end laptop",
    "price": 1200.00
  },
  {
    "id": 2,
    "name": "Phone",
    "description": "Latest smartphone",
    "price": 800.00
  }
]
```

---

## 🧪 API Testing
```bash
curl http://<EC2_IP>/products
```

---

## ✅ Status
Deployment complete and API is accessible.

---


