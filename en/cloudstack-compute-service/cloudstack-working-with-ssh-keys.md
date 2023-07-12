---
title: "CloudStack: Working with SSH Keys"
slug: cloudstack-working-with-ssh-keys
---


Instead of using only password to login your instance, CloudMC supports the push of SSH keys. This article covers the different prerequisites for this feature to work, and how to generate and upload a SSH key.

### Prerequisites
This feature will work properly only if:
- Your template has the SSH Key option enabled. *AND*...
- Your template contains either:
   - A properly installed and configured cloud-init package. Our public templates have that already.
   - You installed the script cloud-set-guest-sshkey from the Apache CloudStack community. See the [CloudStack documentation](http://cloudstack-administration.readthedocs.org/en/4.4/virtual_machines.html?highlight=authentication#using-ssh-keys-for-authentication).
   - You installed a custom made script capable of manipulating the SSH Keys.

### Generate a SSH Key
We will assume you are on Linux or macOS. For Windows, this can be achieved by using PuTTY, which will not be covered in this article.

First, check to see if you have an existing SSH key-pair on your computer. On a Linux terminal, type:

```
ls -al ~/.ssh
```

If you see something like `id_rsa` and `id_rsa.pub`, it means you have a key-pair already that you can use. If you want a new one, follow the next steps:

```
ssh-keygen -t rsa
Enter file in which to save the key (/Users/rwalker/.ssh/id_rsa): rwalker_ssh_key
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in rwalker_ssh_key.
Your public key has been saved in rwalker_ssh_key.pub.
```

To copy the contents of the public key, either open the file and copy the contents, or:

```
pbcopy < ~/.ssh/rwalker_ssh_key.pub
```

### Manually upload a SSH Key
In this step, we upload the public part of our key-pair (the `rwalker_ssh_key.pub` file). It is really important to keep the private key (`rwalker_ssh_key`) secured on your system.

In the SSH Key tab, click on **Add SSH Key**. A new pop-up will show up. Put a name on your key and the content of the public key like shown below.

![Add SSH key](/assets/add-an-ssh-key-en.jpeg)

Once done, click on **Add**. The SSH Key will then show up in the list, and also when you want to deploy an instance using a SSH Key enabled template.
