---
title: Python HTTP Server
description: Python HTTP Server
date: 2022-08-20
tags:
  - python
  - http
---

Python HTTP Server module is a very handy tool and is the newer version of Python SimpleHTTPServer for python 3. You can use Python HTTP Server to turn any directory into a simple HTTP web server.

**Python SimpleHTTPServer supports only two HTTP methods - GET and HEAD.** So it’s a good tool to share files over network. Python SimpleHTTPServer has been migrated to python `http.server` module in python 3

## Python HTTP Server

To use python http server, open a terminal and run:

```sh
$python3 -m http.server 9000
```

You can run python on any port. The default port is 8000. To avoid conflicts, use a port greater than 1024. 

View your page by opening a browser at `localhost:9000`. If there is an `index.html` file, then it will be served to the browser, otherwise a directory listing will be shown. If you know your IP address, you can replace `localhost` with `ip_address` and access the directory at `127.0.0.1:9000`

### Python HTTP Server vs. Python SimpleHTTPServer

The terminal output from pyton 3 http server is cleaner with clearer messages. The python http server module doesn't show the details on quitting from keyboard, which is a cleaner approach.

### More Reference

[Python Beginner Tutorial](https://www.digitalocean.com/community/tutorials/python-tutorial-beginners)