# NTFY 

BASIC SETUP
sudo docker run -p 80:80 -itd binwiederhier/ntfy serve

 

 

ADVANCED SETUP
sudo docker run \
-v /var/cache/ntfy:/var/cache/ntfy \
-v /etc/ntfy:/etc/ntfy \
-p 80:80 \
-itd \
binwiederhier/ntfy \
serve \
--cache-file /var/cache/ntfy/cache.db


####################################################

Server config file (server.yml): https://github.com/binwiederhier/ntfy/blob/main/server/server.yml

NTFY DOCS: https://docs.ntfy.sh/



Setting up cloudflare tunnel ( Pre-requisite domain name)
1. Login to Cloudflare and go to zero trust dashboard
2. Create a new tunnnel ( copy the docker run command and run on the linux server. remember to include -itd flag to run in detached mode )
3. Add a public hostname (using your domain) and select HTTP and the local host IP and port running the NTFY server

The NTFY service should be reachable on the domain. If not accessible check the Firewall or add the port in Iptables to allow access

Sample curl request 
curl -d "message" notifyservice.domain.com/subscription
