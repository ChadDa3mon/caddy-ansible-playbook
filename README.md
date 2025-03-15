# caddy-ansible-playbook
This is a simple ansible playbook that will make it easy to manage your reverse proxies using Caddy. 

While I understand there may be better solutions out there, or better reverse proxies, I've tried most of them and this setup is pretty much the only setup that works reliably for me, and is simple to setup. 

# To Use
Download the files to some folder on your server and modify the `proxies.yaml` and `users.yaml` file to fit your needs. The current `inventory.ini` is set to run against localhost, so if your Caddy reverse proxy is on another host, you'll have to modify the inventory accordingly. 

You will also need to modify the `caddy-playbook.yaml` to change the variables near the top to fit your setup. 

If you want to implement basic auth in front of any proxy, add the flag `require_auth: true` to that proxy in your `proxies.yaml` file (see example in default file). 

When you have everything set, you should be able to run it with `ansible-playbook -i inventory.ini caddy-playbook.yaml`

# Docker Details
I am running the latest version of caddy as a docker file, based on the image `slothcroissant/caddy-cloudflaredns:latest`. As of writing, this is `2.9.1`. I've included a sample of my docker-compose file as well in case it helps anyone. 
