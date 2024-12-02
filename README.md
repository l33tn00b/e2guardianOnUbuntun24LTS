# e2guardianOnUbuntun24LTS
E2Guardian on U24LTS  
Squidguard isn't available, anymore. So we need something else...
Some ideas for bad words: 
- https://github.com/LDNOOBW/List-of-Dirty-Naughty-Obscene-and-Otherwise-Bad-Words
- https://github.com/surge-ai/profanity
- https://github.com/BurntRouter/filtered-word-lists
- https://github.com/web-mech/badwords

Maybe you just pipe those into an AI Agent of your choice. Preferably one, that doesn't mind creating (more) profanity (Hello, Grok). You may thus considerably extend the word lists...

# pre-setup
- enable unattended upgrades
- install mc
- `apt install e2guardian` (should come as 5.3.5 with -enable-sslmitm activated)

# create ssl certificates
As per https://github.com/e2guardian/e2guardian/wiki/MITM---Filtering-HTTPS
- `sudo mkdir /etc/e2guardian/private`
- `openssl genrsa 4096 > private_root.pem`
- `openssl req -new -x509 -days 3650 -key private_root.pem -out my_rootCA.crt`
- `openssl x509 -in my_rootCA.crt -outform DER -out my_rootCA.der`
- `openssl genrsa 4096 > private_cert.pem`
