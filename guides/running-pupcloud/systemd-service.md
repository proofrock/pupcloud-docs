# ⌨ Systemd Service

Here follows an example file to configure pupcloud as a systemd service. I saved it into `/etc/systemd/system/pupcloud.service`.

```systemd
[Unit]
Description=Pupcloud

[Service]
Type=simple
User=myUser
Group=myUser
ExecStart=/home/myUser/local/pupcloud -r /mnt/myRootDir

[Install]
WantedBy=multi-user.target
```

Then you can `systemctl start pupcloud`, `systemctl status pupcloud`, `systemctl enable pupcloud` as normal.

{% hint style="warning" %}
**Always run as non-root** (as setup by lines 7-8 of the script). Pupcloud needs to be explicitly authorized to run as root, and it's seldom a good idea.
{% endhint %}
