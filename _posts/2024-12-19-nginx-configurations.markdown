---
layout: post
title:  "Nginx Configurations"
date:   2024-12-19 22:00:00 +0300
categories: nginx
---

## Nginx Configurations

* Deny all private files except start name with ".well-known"

```conf
location ~ /\.(?!well-known).* {
    deny all;
}
```

* Minimum Configurations FasTCGI proxying scenario for PHP

```conf
location ~ \.php$ {
    fastcgi_param REQUEST_METHOD $request_method;
    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    fastcgi_pass 127.0.0.1:9000;
}
```

* This line provide default configurations to this scope.

```conf
location ~ \.php$ {
    include fastcgi_params;
}
```
