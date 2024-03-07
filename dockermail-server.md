## DKIM Configuration

```sh
docker exec -it mailserver setup config dkim
docker exec -it mailserver setup config dkim domain filipelopes.me
```

dkim_signing.conf
```conf
# documentation: https://rspamd.com/doc/modules/dkim_signing.html

enabled = true;

sign_authenticated = true;
sign_local = true;
try_fallback = false;

use_domain = "header";
use_redis = false; # don't change unless Redis also provides the DKIM keys
use_esld = true;
allow_username_mismatch = true;

check_pubkey = true; # you want to use this in the beginning

domain {
    meuexa.me {
        path = "/tmp/docker-mailserver/rspamd/dkim/rsa-2048-mail-meuexa.me.private.txt";
        selector = "mail";
    }
    filipelopes.me {
        path = "/tmp/docker-mailserver/rspamd/dkim/rsa-2048-mail-filipelopes.me.private.txt";
	      selector = "mail";
    }
}
```

docker exec -it <CONTAINER NAME> setup config dkim domain <DOMAIN>
