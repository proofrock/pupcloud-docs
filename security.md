# 🛡 Security

Pupcloud features authentication for both the "main" interface and the sharing feature. This said, please beware that the password is sent in plain text over the connection to the server, so if you plan to publish it over the internet with authentication, **be sure** to use an HTTPS-capable [reverse proxy](guides/reverse-proxy.md).

{% hint style="danger" %}
Really, again: _**use a reverse proxy**_ to add HTTPS, if you plan to use pupcloud on the public internet!
{% endhint %}

Until pupcloud matures, it may be an idea to consider to disable authentication and enable it on your reverse proxy, that is certainly much more audited and mature.
