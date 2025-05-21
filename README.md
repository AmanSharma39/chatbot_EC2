# 🧠 Simple Flask Chatbot on AWS EC2

This project demonstrates how to deploy a basic chatbot API built with Python and Flask on an AWS EC2 instance.

---

## 🚀 Features

- Lightweight Python Flask app
- POST endpoint to simulate a chatbot
- Deployed on Ubuntu EC2 instance
- Uses virtual environment for clean Python package management

---

## 📁 Project Structure


---

## 🛠 Setup Instructions

### 1. Launch EC2 Instance

- Instance type: `t2.micro`
- OS: Ubuntu
- Open ports: 
  - `22` (SSH)
  - `5000` (Custom TCP for Flask testing)
  - *(or use port 80 if deploying in production with sudo)*

### 2. SSH into Instance

```bash
ssh -i your-key.pem ubuntu@<EC2_PUBLIC_IP>
```
## Install Python & Set Up Virtual Environment

sudo apt update
sudo apt install python3-venv -y
python3 -m venv chatbotenv
source chatbotenv/bin/activate
pip install flask

## Create chatbot.py

from flask import Flask, request, jsonify

app = Flask(__name__)

```bash
@app.route("/", methods=["GET"])
def home():
    return "Flask Chatbot is running!"

@app.route("/chat", methods=["POST"])
def chat():
    user_input = request.json.get("message")
    response = "Hello! You said: " + user_input
    return jsonify({"response": response})

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

##  Run the Chatbot

```bash
python chatbot.py
```

## Test the Chatbot
### From Browser
http://<EC2_PUBLIC_IP>:5000/

## From Terminal (POST request)

```bash
curl -X POST http://<EC2_PUBLIC_IP>:5000/chat \
     -H "Content-Type: application/json" \
     -d '{"message":"Hi"}'
```

### Expected response:
