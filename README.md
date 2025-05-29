# Grafana

A useful tool to monitor application or servers 

## Get SSL Certificate Using Certbot
Run this once to generate SSL cert:
```bash 
docker run --rm \
  -v $(pwd)/certbot/www:/var/www/certbot \
  -v $(pwd)/certbot/conf:/etc/letsencrypt \
  certbot/certbot certonly \
  --webroot \
  --webroot-path=/var/www/certbot \
  --email your@email.com \
  --agree-tos \
  --no-eff-email \
  -d grafana.yourdomain.com
```
- then restart docker 

## Set Up Auto-Renew for SSL
Add a cron job to renew SSL every month:
```bash
0 0 1 * * docker run --rm \
  -v /path/to/certbot/www:/var/www/certbot \
  -v /path/to/certbot/conf:/etc/letsencrypt \
  certbot/certbot renew --webroot -w /var/www/certbot && docker restart nginx
```

## Weather and Disaster Forecast
- typhoon Ver.1
- earthquake Ver.1
- air quality Ver.1