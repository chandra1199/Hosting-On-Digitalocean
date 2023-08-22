# Hosting-On-Digitalocean

# Hosting on Digital Ocean with Docker, NGINX, and SSL

## Setting Up the Server

1. Create a Digital Ocean droplet for the VPN server.
2. Enable reserved IP addresses and note the server's IP address.
3. Access the server using SSH: `ssh root@server_ip`.
4. In your GitHub repo, copy the SSH URL.

If needed, generate an SSH key:
5. Run `ssh-keygen -t rsa -b 8192`.
6. Save the key to `~/.ssh/id_rsa`.

To configure automatic CI/CD:
7. Add the public key to your Digital Ocean account.
8. Install Docker and Docker Compose: `sudo apt install docker docker-compose`.
9. Build and run your Dockerized Next.js app: `docker-compose up --build -d`.

## NGINX Setup

10. Install NGINX: `sudo apt install nginx`.
11. Check NGINX status: `sudo service nginx status`.
12. Configure NGINX to route traffic to your app:
    - Navigate to NGINX's config directory: `cd /etc/nginx/sites-enabled`.
    - Edit the default config file: `sudo vim default`.
    - Configure the server block:

    ```nginx
   
    ```

13. Test NGINX config: `sudo nginx -t`.
14. Restart NGINX: `sudo service nginx restart`.
15. Access your app using your server's IP in a browser.

## Connecting Domain

16. Access your Namecheap account.
17. Go to advanced DNS settings for your domain.
18. Add Host Records:
    - A Record: @ to your_server_ip.
    - A Record: www to your_server_ip.
    
19. Wait for DNS to propagate and access your domain in a browser.

## Adding SSL Certificate

20. Install Certbot: 
    ```
    sudo snap install --classic certbot
    sudo ln -s /snap/bin/certbot /usr/bin/certbot
    ```
21. Obtain an SSL certificate using Certbot and NGINX: `sudo certbot --nginx`.

Your website is now secure with SSL.
