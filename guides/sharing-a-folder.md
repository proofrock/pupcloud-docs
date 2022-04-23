# 🤝 Sharing a Folder

Sharing a folder is possible. Pupcloud will launch a separate server, on another port, to allow to remap it on a reverse proxy.

In order to set up a share, one or more _profiles_ must be specified. Each profile is in the form _name_:_secret_, where the secret must not be shared with the recipient, and it's used to protect the confidentiality of the share.

### CLI parameters

Relevant CLI parameters are:

* `--share-profile`: a share profile, in the form _name_:_secret_ (e.g. `Family:abc0123`). Can be repeated for more profiles.
* `--share-port`: the port for the share server; by default `17179`;
* `--share-prefix`: useful when using a reverse proxy, it's the base URL of the share link. By default, `http://localhost:17179`.

{% hint style="info" %}
If you need to specify more than one profile, you can repeat the parameter `--share-profile`.
{% endhint %}

Sharing is enabled if at least one profile is defined.

### Web UI

In the Web interface, the sharing URL can be obtained using the "share" button for the current folder. A dialog will open:

![The sharing dialog](<../.gitbook/assets/immagine (4).png>)

From here you can set:

1. A password (optional);
2. The profile;
3. If the share must be read-only;
4. An expiry date (optional).

Pressing then the button at 5, a link will be generated and copied to the clipboard.

{% hint style="info" %}
If the main app is launched as read-only, all its share links will be read-only. The switch is still enabled, because if in the future the app will be re-launched as read/write, the link will be read/write.
{% endhint %}

### Revoking a share

The share can be "revoked" by relaunching pupcloud without a particular profile, or changing the secret of a profile. All the links tied to that profile will be invalidated.
