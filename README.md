On a server with SELinux enabled, for Apache httpd to use the certificate files in this repository's `/etc/pki/tls/certs` directory, their SELinux type must be set to `cert_t`. Sample syntax (presumes this repository has been cloned to `/dmanchester.com`):

```
semanage fcontext -a -t cert_t "/dmanchester.com/etc/pki/tls/certs/.+"
restorecon -v /dmanchester.com/etc/pki/tls/certs/*
```

