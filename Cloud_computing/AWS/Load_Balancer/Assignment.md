Setting Up Two NGINX Web Servers with an Elastic Load Balancer (ELB) on AWS for Load Distribution

## 1. Launch Two EC2 Instances (Web Servers)

- Step 1: Go to the AWS Management Console, navigate to EC2, and click on **Launch Instance**.
- Step 2: Choose **Amazon Linux 2 AMI** as the base image.
- Step 3: Choose an instance type such as **t2.micro** (eligible for free tier).
- Step 4: Configure Security Groups:
  - Add a rule to allow **HTTP (port 80)** traffic from Anywhere (0.0.0.0/0).
  - Add a rule to allow **SSH (port 22)** traffic from Your IP.
- Step 5: Launch the instance and wait until it is running.
- Step 6: Repeat the process to create a second EC2 instance.


## 2. Configure NGINX on Both EC2 Instances

Login to EC2 instances via SSH:

```bash
# Switch to the root user
sudo -i

# Update the instance
yum update -y

# Install NGINX
yum install nginx -y

# Start NGINX
systemctl start nginx

# Check NGINX status
systemctl status nginx

# Enable NGINX to start on boot
systemctl enable nginx
```

## 3. Configure Web Content for Each Server

Now, add unique content to each web server to differentiate between them.

On Web Server 1:

```bash
# Go to the NGINX HTML directory
cd /usr/share/nginx/html

# Replace the default index.html file with custom content
echo "I am CloudDevOpshub batch36 student created Web Server 1" > index.html
```

On Web Server 2:

```bash
# Go to the NGINX HTML directory
cd /usr/share/nginx/html

# Replace the default index.html file with custom content
echo "I am CloudDevOpshub batch36 student created Web Server 2" > index.html
```

## 4. Create an Elastic Load Balancer (ELB)

Now, create an Elastic Load Balancer (ELB) that will distribute traffic between these two web servers.

- Step 1: In the AWS Management Console, go to **EC2 > Load Balancers** and click **Create Load Balancer**.
- Step 2: Select **Application Load Balancer**.
- Step 3: Configure the Load Balancer:
  - Name: **MyELB**
  - Scheme: **Internet-facing**
  - Listeners: **HTTP on port 80**
  - Availability Zones: Select the same region and Availability Zone where your EC2 instances are located.

- Step 4: Configure the target group:
  - Target Type: **Instance**
  - Protocol: **HTTP**
  - Port: **80**
  - Health Checks: **HTTP**, path `/`.

- Step 5: Register the EC2 instances (Web Server 1 and Web Server 2) to the target group.
- Step 6: Review and create the Load Balancer.

## 5. Test the Load Balancer

Once the Load Balancer is active, you can test it by visiting the Load Balancer's DNS name (found in the Load Balancer details) in your browser:

```
http://<ELB-DNS-Name>
```

You should see the content from either Web Server 1 or Web Server 2, and it will alternate as the load balancer distributes traffic between the two.
