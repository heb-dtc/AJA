## show headers
curl -v <url>

## show response header only
curl -I <url>

## do not print response to STDOUT
curl <url> -o /dev/null

## accept compressed response
curl --compress <url>

## send custom headers along request
curl -I --header 'If-Modified-Since: Mon, 08 Aug 2016 22:15:01 GMT' --header 'Accept-Encoding: gzip, deflated' <url>
