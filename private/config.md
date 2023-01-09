# some notes on configuring the Lightsail instance for the lab website

- in the Lightsail console, go to the Networking area and enable HTTPS (443)
- download the key pair PEM file from the Lightsail console; `chmod` it to 600
- using the PEM key pair, `scp` the `id_rsa.pub` file from `~/.ssh` to the
instance
- `ssh` into the instance
- `sudo apt-get update`
- `sudo apt-get install -y emacs`
- `sudo apt-get install -y nginx`
- `sudo emacs -nw /etc/nginx/sites-enabled/default` (change web root directory to
`/home/ubuntu/lab.saramsey.org`)
- `cd /home/ubuntu && git clone https://github.com/ramseylab/lab.saramsey.org.git`
- `sudo apt-get install -y certbot python-certbot-nginx`
- `sudo certbot --nginx -d lab.saramsey.org` (choose option 2, redirect)
- `sudo chmod 755 /home/ubuntu`
- `cp /home/ubuntu/lab.saramsey.org/scripts/update-website.sh ~`
