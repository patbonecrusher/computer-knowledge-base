---
creation date: 04/01/2025
tags:
  - tips/macos
---
---
```cardlink
url: https://dev.to/siddhantkcode/enable-touch-id-authentication-for-sudo-on-macos-sonoma-14x-4d28
title: "Enable Touch ID Authentication for sudo on macOS Sonoma 14.x"
description: "Operating Environment:     OS: MacOS Sonoma 14.5  Device: M1 MacBook Pro           ..."
host: dev.to
favicon: https://media2.dev.to/dynamic/image/width=32,height=,fit=scale-down,gravity=auto,format=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F8j7kvp660rqzt99zui8e.png
image: https://media2.dev.to/dynamic/image/width=1000,height=500,fit=cover,gravity=auto,format=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F9vnfzdnrbrwgx98c1ol3.png
```

[![Cover image for Enable Touch ID Authentication for sudo on macOS Sonoma 14.x](https://media2.dev.to/dynamic/image/width=1000,height=420,fit=cover,gravity=auto,format=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F9vnfzdnrbrwgx98c1ol3.png)](https://media2.dev.to/dynamic/image/width=1000,height=420,fit=cover,gravity=auto,format=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F9vnfzdnrbrwgx98c1ol3.png)

[Siddhant Khare](https://dev.to/siddhantkcode)

Posted on Jun 22, 2024

# Enable Touch ID Authentication for sudo on macOS Sonoma 14.x


### [Operating Environment](https://dev.to/siddhantkcode/enable-touch-id-authentication-for-sudo-on-macos-sonoma-14x-4d28#operating-environment)

- **OS:** MacOS Sonoma 14.5
- **Device:** M1 MacBook Pro

## [Explanation](https://dev.to/siddhantkcode/enable-touch-id-authentication-for-sudo-on-macos-sonoma-14x-4d28#explanation)

In macOS Sonoma, a new method has been introduced to enable Touch ID when running `sudo`
commands, making it more persistent across system updates. Previously, editing the
`/etc/pam.d/sudo` file was necessary, but these changes would often revert after an update,
requiring reconfiguration. With Sonoma, the settings can be added to a separate file
`/etc/pam.d/sudo_local`, which isn't overwritten during updates, allowing Touch ID to remain
enabled for `sudo` commands consistently.

## [Steps to Enable Touch ID for `sudo`](https://dev.to/siddhantkcode/enable-touch-id-authentication-for-sudo-on-macos-sonoma-14x-4d28#steps-to-enable-touch-id-for-raw-sudo-endraw-)

### [1. Create and Edit the Configuration File](https://dev.to/siddhantkcode/enable-touch-id-authentication-for-sudo-on-macos-sonoma-14x-4d28#1-create-and-edit-the-configuration-file)

Create a new configuration file based on the template provided in macOS Sonoma.

```


sudo cp /etc/pam.d/sudo_local.template /etc/pam.d/sudo_local


```

Edit the newly created file with your preferred text editor:

```


sudo vim /etc/pam.d/sudo_local


```

In the file, locate the following line, Uncomment it by removing the `#`:

```


- #auth       sufficient     pam_tid.so
+ auth       sufficient     pam_tid.so


```

### [Alternative Method Using `sed` and `tee`](https://dev.to/siddhantkcode/enable-touch-id-authentication-for-sudo-on-macos-sonoma-14x-4d28#alternative-method-using-raw-sed-endraw-and-raw-tee-endraw-)

You can achieve the same result with a single command using `sed` and `tee`:

```


sed -e 's/^#auth/auth/' /etc/pam.d/sudo_local.template | sudo tee /etc/pam.d/sudo_local


```

### [2. Confirm the Operation](https://dev.to/siddhantkcode/enable-touch-id-authentication-for-sudo-on-macos-sonoma-14x-4d28#2-confirm-the-operation)

Open a new terminal session and run a `sudo` command to test the setup:

```


sudo ls


```

You should be prompted to authenticate using Touch ID. If the command executes after Touch ID authentication, the setup is complete.

[![Screenshot 2024-06-22 at 4 48 00 PM](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fgist.github.com%2Fassets%2F55068936%2Fce9c32f4-a1e2-44bb-99e2-7a31af15309f)](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fgist.github.com%2Fassets%2F55068936%2Fce9c32f4-a1e2-44bb-99e2-7a31af15309f)

### [Background](https://dev.to/siddhantkcode/enable-touch-id-authentication-for-sudo-on-macos-sonoma-14x-4d28#background)

Previously, enabling Touch ID for `sudo` required modifying `/etc/pam.d/sudo`, but these changes did not persist through macOS updates. By leveraging the new `/etc/pam.d/sudo_local` configuration in macOS Sonoma, we can ensure that Touch ID settings for `sudo` remain intact even after system updates.

The `/etc/pam.d/sudo` file now includes the following:

```


# sudo: auth account password session
auth       include        sudo_local
auth       sufficient     pam_smartcard.so
auth       required       pam_opendirectory.so
account    required       pam_permit.so
password   required       pam_deny.so
session    required       pam_permit.so


```

This configuration ensures that the settings in `/etc/pam.d/sudo_local` are loaded and used, maintaining Touch ID functionality for `sudo` commands.

Please note that for macOS versions earlier than Sonoma, manual editing of `/etc/pam.d/sudo` is still required to enable Touch ID for `sudo` commands.