1-set proxy in terminal
2-apt install docker.io docker-compose -y
 - set proxy in /etc/systemd/system/docker.service.d/http-proxy.conf
3-create a directory named moodle-docker
4-copy compose.yml file in the directory
5-docker-compose up -d
6-apt install nginx certbot python3-certbot-nginx
7-sudo nano /etc/nginx/sites-available/moodle.conf
8-sudo ln -s /etc/nginx/sites-available/moodle.conf /etc/nginx/sites-enabled/
9-sudo nginx -t  # Test configuration
10-sudo systemctl reload nginx
11-sudo certbot --nginx -d EXAMPLE.COM
