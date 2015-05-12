tcpdump
===

Monitor all traffic on a remote machine via ssh and view it on local wireshark:

`ssh root@myserver 'tcpdump -n -U -s0 -w -0 "not port 22"' | wireshark -k -i -`

To speed up processing, we can use a weaker cipher such as RC4 for remote monitoring

`ssh -c arcfour root@myserver "tcpdump -n -U -s0 -w -0 'not port 22'" | wireshark -k -i -`

Print all prinatable strings:

`tcpdump -i int -n -w - -l -s 1500 | strings`




