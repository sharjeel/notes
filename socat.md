General format:

`socat <input> <output>`

Where `-` for as input or output would go to STDIN and STDOUT respectively. Otherwise the format is `PROTOCL:HOST:PORT[,options]`.

Connect to an SSL server and read from STDIN

`socat - OPENSSL:localhost:443`

Listen to port 10000 for SSL connections

```
openssl req -new -x509 -days 365 -nodes -out cert.pem -keyout cert.key # Certificates generation
socat OPENSSL-LISTEN:10000,cert=./cert.pem,key=./cert.key -
```

Listen to traffic coming to SSL server:

```
socat -v OPENSSL-LISTEN:10000,cert=./cert.pem,key=./cert.key,fork OPENSSL:localhost443 
````
