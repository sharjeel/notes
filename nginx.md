Automatically restart nginx upon configuration modifications: 

`sudo python -m pyinotify -r -e IN_MODIFY,IN_CLOSE_WRITE,IN_CREATE -c "service nginx restart" -v /etc/nginx/`
