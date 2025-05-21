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
