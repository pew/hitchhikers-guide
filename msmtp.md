---
date created: Tuesday, September 5th 2023, 10:46:06 am
date modified: Tuesday, September 5th 2023, 10:54:30 am
tags:
  - linux
  - smtp
---

# msmtp

if you just want something super lightweight on a system to send out e-mails using existing SMTP services such as amazon ses or mailgun etc.:

## installation

```shell
apt-get install msmtp
```

## configuration

put the following into `/etc/msmtprc` and make your updates

```
defaults
auth           on
tls            on
tls_trust_file /etc/ssl/certs/ca-certificates.crt
add_missing_from_header on
syslog         on

account        dreamland
host           smtp.example.com
port           465
tls_starttls   off
from           user@example.com
user           user@example.com
password       superSecure

account default : dreamland

aliases               /etc/aliases
```

## sendmail drop-in

save the following as `/usr/sbin/sendmail` (and replace the e-mail with the one you use as `from` from above)

```shell
#!/bin/sh
sed '0,/^\r\?$/ { s/^To:.*/To: user@example.com/ }' | /usr/bin/msmtp "$@"
```
