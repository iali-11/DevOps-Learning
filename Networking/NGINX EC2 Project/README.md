# NGINX EC2 Project 🔥

- Given the task to create an EC2 instance running NGINX on port 80.
- Add an A record to Cloudflare and point it to the EC2 instance.
- Enable access NGINX webpage. 

## 1️⃣ Purchase a Domain on Cloudflare
- Cost ranges between $5 - $10

## 2️⃣ Launched EC2 instance
- AMI: Amazon Linux 2023
- Instance type: t3.micro
- Create key pair
- Security Group:
  - SSH (port 22)
  - HTTP (port 80)
<img width="1658" height="65" alt="Screenshot 2025-11-08 at 21 43 56" src="https://github.com/user-attachments/assets/6505596a-fbcb-40a4-a423-5fb1865a4eea" />

---
### Note: Hold onto public IP address, will be utilised later on!
---

## 3️⃣ Connect EC2 Instance to Terminal via SSH

From your terminal:
- ssh -i /path/to/your-key.pem ec2-user@(your-ec2-public-ip)

<img width="817" height="37" alt="Screenshot 2025-11-08 at 21 52 00" src="https://github.com/user-attachments/assets/0058204d-7458-49a3-a899-cccda723405d" />

## 4️⃣ Install and Run NGINX
Run code in Terminal:
- sudo dnf install nginx -y
- sudo systemctl enable nginx
- sudo systemctl start nginx

## 5️⃣ Add an A Record in Cloudflare
<img width="1104" height="168" alt="Screenshot 2025-11-08 at 15 22 36" src="https://github.com/user-attachments/assets/16b97a2d-6809-4eaf-be83-df1a18f9a576" />

Configure the new record:
- Type: A
- Name: nginx (creates nginx.[yourdomain])
- IPv4 address: your EC2 public IP
- Proxy status: Proxied
- TTL: Auto

## 6️⃣ Test in Terminal

Run code:
  - dig +short nginx.[yourdomain].

Response: Public IP address provided by EC2 instance.

<img width="574" height="45" alt="Screenshot 2025-11-08 at 21 54 10" src="https://github.com/user-attachments/assets/2233c0a2-480e-4a1e-9026-607321adee2b" />

## 7️⃣ Test in browser
Visit: http://nginx.ibrahimalitech.com

You should NGINX default welcome page provided via EC2 instance.🎉
<img width="1104" height="717" alt="Screenshot 2025-11-08 at 15 15 22" src="https://github.com/user-attachments/assets/6eabcd72-b0c8-43e5-bb38-71daf112e4b4" />





