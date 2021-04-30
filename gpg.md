# GPG Keys Github

## Source

- https://docs.github.com/en/github/authenticating-to-github/generating-a-new-gpg-key

## Installation

### Checking for existing GPG Keys

1. use the `gpg --list-secret-keys --keyid-format LONG` command to list GPG Keys
2. if you already have GPG key you can skip the next step

### Generating a new GPG Keys

1. Generate a GPG Keys pair `$ gpg --full-generate-key`
2. You accept the default `RSA` and `RSA (default)`
3. Enter the desired key size. Your key must be at least `4096` bits.
4. Use the `gpg --list-secret-keys --keyid-format LONG` command to list GPG Keys
5. From the list of GPG keys, copy GPG Keys ID you'd like use. In this example ID is `3AA5C34371567BD2`
```
gpg --list-secret-keys --keyid-format LONG

/Users/hubot/.gnupg/secring.gpg
------------------------------------
sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid                          Hubot 
ssb   4096R/42B317FD4BA89E7A 2016-03-10
```
6. Paste the text below, substituting in the GPG Key ID you'd like to use
`gpg --armor --export 3AA5C34371567BD2`
   
7. Copy your GPG key, beginning with `-----BEGIN PGP PUBLIC KEY BLOCK-----` and ending with 
   `-----END PGP PUBLIC KEY BLOCK-----`.
   
8. Add the GPG key to your Github account

### Telling Git about your signing key

1. List the GPG Keys `gpg --list-secret-keys --keyid-format LONG`
2. retrieve ID key to make the following command `git config --global user.signingkey 3AA5C34371567BD2`
3. To add your GPG key to your bash profile , run the following command: 
`if [ -r ~/.bash_profile ]; then echo 'export GPG_TTY=$(tty)' >> ~/.bash_profile; \
   else echo 'export GPG_TTY=$(tty)' >> ~/.profile; fi`
   

### Setting Commits

1. activate option `Vigilant mode`
2. testing things