# QUICKSTART

```shell
$ mkdir -p /var/www/wwwroot
$ cd /var/www/wwwroot
$ cat << EOF > index.html
> First App
> EOF
$ mkdir conf
$ cat << EOF > default.conf
> server {

    listen 80 default_server;
    listen [::]:80 default_server ipv6only=on;

    server_name localhost;
    root /var/www;
    index index.html index.htm;

    location / {
         try_files $uri $uri/ /index.php$is_args$args;
    }

    location ~ /\.ht {
        deny all;
    }
}
> EOF
$ git clone https://github.com/ConserveLee/quick-kubernetes-deploy.git quick-k8s
$ cd quick-k8s/pv
$ kubectl apply -f pv.yaml
$ kubectl apply -f app.yaml
```





- ### [blog](http://http://www.lizhongyuan.net)

  