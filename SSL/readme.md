### How to create .pfx file from certificate and private key? 
openssl pkcs12 -export -out bioage.pfx -inkey private.key -in bioage.crt -in gd-g2-g1.crt
