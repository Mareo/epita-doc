# Git configuration

Students at EPITA have to use SSH Key-Based Authentication to access their Git
repositories.

## Generating an SSH Key Pair

OpenSSH provides a tool called `ssh-keygen` to generate and modify key pairs.
You can learn more about its options by running `man 1 ssh-keygen`.

A key pair is composed of a private key (without extension by default) and a
public key (.pub by default).
To generate a key pair, you can use:
```bash
ssh-keygen -f "$HOME/.ssh/id_rsa" -b 4096
```
/!\ It is not recommended to generate a private key without passphrase.

## Pushing your public key

Now that you own a key pair, you need to push your public key on the
[CRI Website](https://cri.epita.fr/accounts/profile/). Your keys can be managed
using `My SSH Keys`.

Your public key can be retrieved using:
```bash
cat "$HOME/.ssh/id_rsa"
```

## Configuring Git

While `git-config` can be used for much more than just configuring your
identity, this will be the only part covered in this documentation.

Your identity, composed of a name and an email will be used to author your
commits. You can set them by using the following commands:
```bash
git config --global user.name 'Firstname LASTNAME'
git config --global user.email 'firstname.lastname@epita.fr'
```

## git-autoconfig

A tool called git-autoconfig is available on Archlinux SUP. This script will
generate a key, configure your git and push your public key on the CRI website.
While this is the easiest way, this tool has its limitations. It is instead
recommended to follow the steps above for learning purpose.
