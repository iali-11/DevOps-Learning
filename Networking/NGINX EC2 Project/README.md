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

---
### Note: Hold onto public IP address, will be utilised later on!
---

## 3️⃣ Connect EC2 Instance to Terminal via SSH

From your terminal:
- ssh -i /path/to/your-key.pem ec2-user@(your-ec2-public-ip)

## 4️⃣ Install and Run NGINX
Run code in Terminal:
- sudo dnf install nginx -y
- sudo systemctl enable nginx
- sudo systemctl start nginx

## 5️⃣ Add an A Record in Cloudflare

<img width="1104" height="168" alt="Screenshot 2025-11-08 at 15 22 36" src="https://github.com/user-attachments/assets/7ec419c7-e43d-45dc-b760-252976275534" />

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

## 7️⃣ Test in browser
Visit:
- nginx.[yourdomain]

You should NGINX default welcome page provided via EC2 instance.🎉

<img width="1104" height="717" alt="Screenshot 2025-11-08 at 15 15 22" src="https://github.com/user-attachments/assets/1ff2c2e4-4915-46b3-9586-ae605b7371e3" />
