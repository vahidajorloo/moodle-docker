1-set proxy in terminal

2-apt install docker.io docker-compose -y

 - set proxy in /etc/systemd/system/docker.service.d/http-proxy.conf
 
3-create a directory named moodle-docker

4-copy compose.yml file in the directory

5-docker-compose up -d

6-apt install nginx certbot python3-certbot-nginx

7-sudo nano /etc/nginx/sites-available/moodle.conf:

```
server {
    listen 80;
    server_name EXAMPLE.COM;

    location / {
        proxy_pass http://localhost:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}


```


8-sudo ln -s /etc/nginx/sites-available/moodle.conf /etc/nginx/sites-enabled/

9-sudo nginx -t  # Test configuration

10-sudo systemctl reload nginx

11-sudo certbot --nginx -d EXAMPLE.COM

12-crontab -e

0 */12 * * * /usr/bin/certbot renew --quiet



