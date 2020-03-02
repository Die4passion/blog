# nextcloud配置



### 失效运行

```shell
certbot certonly -d "*.die4passion.com" --manual --preferred-challenges dns --register-unsafely-without-email --server https://acme-v02.api.letsencrypt.org/directory
```

然后，阿里云，域名服务，解析，更改txt值。
