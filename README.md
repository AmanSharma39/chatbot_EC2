# 🧠 Simple Flask Chatbot on AWS EC2

This project demonstrates how to deploy a basic chatbot API built with Python and Flask on an AWS EC2 instance.

---

## 🚀 Features

- Lightweight Python Flask app
- POST endpoint to simulate a chatbot
- Deployed on Ubuntu EC2 instance
- Uses virtual environment for clean Python package management


## 📁 Project Structure

## 🛠 Setup Instructions

### 1. Launch EC2 Instance

- Instance type: `t2.micro`
- OS: Ubuntu
- Open ports: 
  - `22` (SSH)
  - `5000` (Custom TCP for Flask testing)
  - *(or use port 80 if deploying in production with sudo)*


![image alt](https://github.com/AmanSharma39/chatbot_EC2/blob/9dcfa929a00e7ae9c5d41326fa7c5acc91894f46/Screenshot%202025-05-21%20111911.png)

### 2. SSH into Instance

```bash
ssh -i your-key.pem ubuntu@<EC2_PUBLIC_IP>
```
## 3. Install Python & Set Up Virtual Environment
```
sudo apt update
sudo apt install python3-venv -y
python3 -m venv chatbotenv
source chatbotenv/bin/activate
pip install flask
```

## 4. Create chatbot.py
```
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route("/chat", methods=["POST"])
def chat():
    user_input = request.json.get("message")
    response = "Hello! You said: " + user_input
    return jsonify({"response": response})

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)

```

## 5. Run the Chatbot
```bash
python chatbot.py
```

## 🧪Test the Chatbot
### ✅From Browser
http://<EC2_PUBLIC_IP>:5000/

## ✅From Terminal (POST request)

```bash
curl -X POST http://<EC2_PUBLIC_IP>:5000/chat \
     -H "Content-Type: application/json" \
     -d '{"message":"Hi"}'
```
![image alt](https://github.com/AmanSharma39/chatbot_EC2/blob/9dcfa929a00e7ae9c5d41326fa7c5acc91894f46/Screenshot%202025-05-21%20114542.png)

### Expected response:
```
{"response": "Hello! You said: Hi"}
```
