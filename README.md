# dmanchester.com

## Setting Up the Live Demo

* Generate an application secret ([instructions](https://playframework.com/documentation/2.6.x/ApplicationSecret#Generating-an-application-secret)).
* Create a distribution of the [`sample-scala` application](https://github.com/dmanchester/playfop/tree/master/sample-scala) ([instructions](https://playframework.com/documentation/2.6.x/Deploying#Using-the-dist-task)). Unzip the distribution to a convenient location.
* Create a start script (you may also include any of the application's [optional system properties](https://github.com/dmanchester/playfop/tree/master/sample-scala#miscellaneous)):
  ```
  nohup path_to_unzipped_dist/bin/sample-scala -Dplay.http.context=/playfop/live-demo '-Dplay.http.secret.key=your_secret_key' &
  ```

## Miscellaneous

On a server with SELinux enabled, for Apache httpd to use the certificate files in this repository's `/etc/pki/tls/certs` directory, their SELinux type must be set to `cert_t`. Sample syntax (presumes this repository has been cloned to `/dmanchester.com`):

```
semanage fcontext -a -t cert_t "/dmanchester.com/etc/pki/tls/certs/.+"
restorecon -v /dmanchester.com/etc/pki/tls/certs/*
```

