# Why and what ?

I use [devilbox](https://github.com/cytopia/devilbox)
as local development and found devilbox is very
convenient .

Later i want to use devilbox as prouduction platform.  
but i need https support for devilbox .

So , It is a reverse proxy with https for supporting devilbox.

### usage :

1. Disable expose 80,443 ports in devilbox (in .env config devilbox set port 80 -> 8000, 443 - 4443)  
2. git clone https://github.com/bigxu/nginx-acme.git
3. cd nginx-acme && docker-compose up -d  
4. openssl dhparam -out /acme.sh/dhparam.pem 4096  
5. docker-compose exec acme-sh sh  
acme.sh --issue -d test.example.com --server letsencrypt --standalone

#### notice: acme-sh will open 80 port and create /\.well-known/acme-challenge/ in container

6. create nginx conf for your vhost. there is a example
example443.conf.txt

7. docker-compose exec nginx-srv -s reload.

#### end
