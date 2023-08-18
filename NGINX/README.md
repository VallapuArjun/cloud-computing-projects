# what is nginx?
* It is a webserver.
* It accept request via https/s and respond to display website content through storing,proccessing and delivering webpages to users.
* It is used as reverse proxy,load balancer,mail proxy and http cache.
# Launching an Amazon EC2 Instance:
## Log in to AWS Console:
Log in to your AWS account console.

## Navigate to EC2:
Go to the EC2 dashboard.

## Launch Instance:
Click on the "Launch Instance" button.

## Choose an Amazon Machine Image (AMI):
Select an AMI that fits your requirements. For example, you can choose an Amazon Linux 2 AMI.

## Choose an Instance Type:
Select an instance type based on your needs.

## Configure Instance:
Configure instance settings such as number of instances, network, subnet, etc.

## Add Storage:
Configure the storage for your instance.

## Add Tags:
Add any relevant tags for identification.

## Configure Security Group:
Configure security group settings to allow access to your instance.

## Review and Launch:
Review your instance configuration and launch the instance.

## Select a Key Pair:
Choose an existing key pair or create a new one. This will allow you to SSH into the instance.

## Launch Instances:
Click the "Launch Instances" button to launch the EC2 instance.


# Nginx's Roles Practically:
## Nginx as a Web Server:
### SSH into your EC2 instance and install Nginx:

```bash
sudo yum update -y
sudo amazon-linux-extras install nginx1.12 -y
sudo systemctl start nginx
```
Open a web browser and enter your instance's public IP or DNS to see the default Nginx welcome page.

## Nginx as a Proxy Server:
Modify the Nginx configuration to act as a reverse proxy. Edit /etc/nginx/nginx.conf or create a new .conf file in /etc/nginx/conf.d/:

nginx
```
server {
    listen 80;
    server_name example.com;

    location / {
        proxy_pass http://your_backend_server;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```
Replace example.com with your domain and your_backend_server with the actual backend server.

Reload Nginx configuration:

```bash
sudo systemctl reload nginx
```
## Nginx as a Load Balancer:
Edit your Nginx configuration to set up a load balancer. For example, you can modify /etc/nginx/nginx.conf or create a new .conf file:

nginx
```
upstream backend_servers {
    server backend1.example.com;
    server backend2.example.com;
}

server {
    listen 80;
    server_name loadbalancer.example.com;

    location / {
        proxy_pass http://backend_servers;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```
Replace backend1.example.com and backend2.example.com with your actual backend server addresses.

Reload Nginx configuration:

```bash
sudo systemctl reload nginx
```
This setup demonstrates how Nginx can be used practically as a web server, reverse proxy, and load balancer on an Amazon EC2 instance. Keep in mind that these are simplified examples, and real-world scenarios might involve more complex configurations and security measures.







