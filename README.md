# EC2andRoute53
Hosting a website using EC2, Mapped domain name with Public IP , Secured website with SSI certificate
# Hosting a website using EC2 and Route53
## Steps to Deploy
### 1: Launch an EC2 Instance
- Go to AWS Management Console -> EC2 -> Launch Instance
- Choose **Ubuntu**
- Create and Use key pair
- Use Putty
- Allow **HTTP (80)**, **HTTPS (443)**, and **SSH (22)**
- Launch instance
  ## Launched EC2 Instance
  ![EC2 Instance](https://github.com/RiyaRiya184/EC2andRoute53/blob/e9fd8d2a98563e5169c16194aaab8aca6df9aa03/CLOUD%201.png) 


### 2. Connect to EC2 (using PuTTY/SSH)  
- Download Putty.exe file and install it in your device.
- Go to connection.
- Go to SSH
- Go to Auth
- Choose key pair file you made while creating instance.
```bash
login as username: ubuntu
```

### 3. Install Apache  
```bash
sudo apt install apache2
```

Check in browser → `http://yourpublicip`
- An Apache page will be shown to your public ip.

```bash
cd /var/www/html
sudo rm index.html
sudo vi index.html
```
- Press I to insert your own html code.
- Write your own code.
- After writing all code , Press Ctrl+C and then write ":wq" and Press Enter.

### 4. Map Domain with Route 53  
- Register your own domain name.
- Go to Route 53 on AWS, Click on Hosted Zones.
## Route 53 Hosted Zone
![Route 53 Hosted Zone]()
- You will get four NS name server.
## NS Name Servers
  ![NS Name servers]()
- Then update these name server in your domain.
## Domain Name adding Name server
![Nameservereditedondomain]()
- Create **A record**
- Set your domain, Enter your allotted Public IP and then Map it.
## Website before SSL certfication (Showing Not Secure)
![Webiste before SSL certification](https://github.com/RiyaRiya184/EC2andRoute53/blob/25f37a267d393c916f07bddf3f23e663c95a9f49/uuid%3DD2E2C507-2D2D-478A-8F22-8C86E8102577%26library%3D1%26type%3D1%26mode%3D1%26loc%3Dtrue%26cap%3Dtrue.png)

### 5. Enable SSL (HTTPS) using Certbot  
```bash
sudo apt update
sudo apt install certbot python3-certbot-apache -y
sudo certbot --apache
```
- Then it will ask an email.
- Then it will ask your domain name , So just write it.
- Then SSL certification will deployed to your domain name.
  Check in browser → `https://yourpublicip`

## Website after SSL certfication using https (Showing Connection is Secure)
![Webiste ater SSL certification](cloudimages/securedsite.png)
