# How to convert .ppk key to OpenSSH key under Linux?

* Ubuntu sudo `apt-get install putty-tools`
* Debian-like `apt-get install putty-tools`
* RPM based `yum install putty`
* Gentoo `emerge putty`

etc.
* OS X: Install Homebrew (http://brew.sh/), then run `brew install putty`

## To generate the private key:

```bash
cd ~
puttygen id_dsa.ppk -O private-openssh -o id_dsa
```

and to generate the public key:

```bash
puttygen id_dsa.ppk -O public-openssh -o id_dsa.pub
```

Move these keys to `~/.ssh` and make sure the permissions are set to private for your private key:

```bash
mkdir -p ~/.ssh
mv -i ~/id_dsa* ~/.ssh
chmod 600 ~/.ssh/id_dsa
chmod 666 ~/.ssh/id_dsa.pub
```

If you have already tried to perform a 'git clone' operation you might need to do this also

```bash
chmod 666 ~/.ssh/known_hosts
```
