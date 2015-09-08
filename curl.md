Curl
===

Send binary data

`curl --data-binary @requestdata.bin <url>`

Send header

`curl --header "SomeHeader: Somevalue" <url>`

e.g. bytes range header

`curl --header "Range: bytes=0-1024 <url>`

Include header in the output

`curl -i <url>`

Fetch only the header using HEAD command

`curl -I <url>`

Dump the headers to a filename

`curl -D <filename> <url>`

Write output to a file

`curl -o <filename> <url>`
