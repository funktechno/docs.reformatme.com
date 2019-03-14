---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Headers
nav_order: 5
description: Headers returned in the ReformatMe service.
---
# Headers

Headers will return in the following format assuming that the header `Accept: application/json` is given.

```js
HTTP/1.1 200 OK
Date: Thu, 14 Mar 2019 00:27:37 GMT
Server: Apache
Cache-Control: no-cache
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: POST
Access-Control-Allow-Headers: Origin, X-Requested-With, Content-Type, Accept
x-powered-by: ReformatMe_API/1.0.1
X-Response-Time: 14.52ms
Vary: Accept-Encoding,User-Agent
Content-Encoding: gzip
Content-Length: 103
Connection: close
Content-Type: application/json; charset=utf-8
```

The expected time is under `3000ms`. Please report a bug and the request made if this performance is not maintained.