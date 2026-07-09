# AWS Intern Assignment

## AWS Servers Used
- EC2: Ubuntu 24.04
    - Security Groups: Port 80/22 open for all IPs
    - EBS: gp3 
- VPC
    - Subnets: Public Subnets with Internet Access
- CloudWatch: Default EC2    

## EC2 Setup Steps
 
1. Launched an EC2 instance from the AWS Console:
   - AMI: Ubuntu 24.04 LTS
   - Instance type: t3.micro
   - Key pair: created new `.pem` key pair for SSH access
2. Created a Security Group with inbound rules:
   - SSH (port 22) - restricted to my IP
   - HTTP (port 80) - open to 0.0.0.0/0
3. Launched the instance and waited for it to reach `running` state.
4. Connected via SSH from local machine:
```bash
   chmod 400 TestPair.pem
   ssh -i TestPair.pem ubuntu@65.0.31.84
```
 
## Nginx Installation
 
1. Updated package lists and upgraded existing packages:
```bash
   sudo apt update
   sudo apt upgrade -y
```
2. Installed Nginx:
```bash
   sudo apt install nginx -y
```
3. Checked service status:
```bash
   sudo systemctl status nginx
```
4. Restarted the service to confirm it comes back up cleanly:
```bash
   sudo systemctl restart nginx
```
5. Replaced the default Nginx landing page with a custom `index.html` containing my Name, College, Branch, Email, and Date:
```bash
   sudo nano /etc/nginx/html/index.html
   sudo systemctl restart nginx
```
6. Verified the site loads at `http://65.0.31.84` in a browser.

## Commands Used
 
| Command | Purpose |
|---|---|
| `sudo apt update` | Refresh package index |
| `sudo apt upgrade -y` | Upgrade installed packages |
| `sudo apt install nginx -y` | Install Nginx web server |
| `sudo systemctl status nginx` | Check Nginx service status |
| `sudo systemctl restart nginx` | Restart Nginx service |
| `df -h` | Check disk usage |
| `free -h` | Check memory usage |
| `ps aux \| head -20` | List running processes |
| `sudo nano /etc/nginx/html/index.html` | Edit the website's HTML |
| `chmod 400 TestPair.pem` | Set correct permissions on SSH key |
| `ssh -i TestPair.pem ubuntu@IP` | Connect to the instance via SSH |

### Bonus - Docker Install

```bash
(install commands from Docker docs)
sudo docker run hello-world
```
