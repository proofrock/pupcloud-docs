# 🗝 Authentication

You can set a password for accessing pupcloud, by using the `-P` parameter on the commandline. You must provide the SHA-256 sum of the password you want to use, in hex format.

You can provide the whole hash, or just the first part, of any length you want to keep the commandline short. Of course, the longer the hash, the safer the system.

```bash
# Password is "ciao", with 128 bit of strength (truncated at 16 bytes)
pupcloud -r /my/dir -P b133a0c0e9bee3be20163d2ad31d6248
```

You can use [this site](https://emn178.github.io/online-tools/sha256.html) to hash the password, it doesn't send the password on the net (at least at the time I am writing, you may want to check).

{% hint style="danger" %}
The password is sent in clear text over the net, so _always use a HTTPS-capable reverse proxy_ if you plan to serve over the public internet.
{% endhint %}
