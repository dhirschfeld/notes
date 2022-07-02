---
tags: [System Administration]
title: Creating a GPG Key
created: '2021-02-13T12:29:34.637Z'
modified: '2021-11-25T00:07:10.009Z'
---

# Creating a GPG Key

* https://dev.to/benjaminblack/signing-git-commits-with-modern-encryption-1koh
* https://juliansimioni.com/blog/troubleshooting-gpg-git-commit-signing/

```
gpg --full-generate-key --expert
```
`(9) ECC and ECC`
`(1) Curve 25519`

This creates a master key for signing and certificate creation `[SC]`
and one for encryption `[E]`.

It's not good practice to use your master key for signing so you should
create a separate key for signing `[S]`:
```
gpg --list-keys --keyid-format short
```
```
gpg --expert --edit-key 966FB9DA
```
`(10) ECC (sign only)`
`(1) Curve 25519`

```
❯  gpg --list-keys --keyid-format short
/home/dhirschfeld/.gnupg/pubring.kbx
------------------------------------
pub   ed25519/966FB9DA 2021-02-13 [SC] [expires: 2024-02-13]
      D9498BB26AF45DCB323F1FC93412F198966FB9DA
uid         [ultimate] David Hirschfeld <dave.hirschfeld@gmail.com>
sub   cv25519/93A801E5 2021-02-13 [E] [expires: 2024-02-13]
sub   ed25519/CE44D946 2021-02-13 [S] [expires: 2024-02-13]
```
```
❯ gpg --list-keys --keyid-format long
/home/dhirschfeld/.gnupg/pubring.kbx
------------------------------------
pub   ed25519/3412F198966FB9DA 2021-02-13 [SC] [expires: 2024-02-13]
      D9498BB26AF45DCB323F1FC93412F198966FB9DA
uid                 [ultimate] David Hirschfeld <dave.hirschfeld@gmail.com>
sub   cv25519/E35C038F93A801E5 2021-02-13 [E] [expires: 2024-02-13]
sub   ed25519/5251EFA9CE44D946 2021-02-13 [S] [expires: 2024-02-13]
```

To enable signing to work from a terminal you need to add the below env var to your `.bashrc`
```bash
# enable passphrase prompt for gpg
export GPG_TTY=$(tty)
```

Configure `git`:
```
git config --global commit.gpgsign true
git config --global user.signingkey 0x5251EFA9CE44D946
```

Export keys:
```
gpg --export -a "David Hirschfeld"
gpg --export-secret-key -a "David Hirschfeld"
```


### Note!

After importing keys you need to trust them:
* https://stackoverflow.com/a/34132924
```
gpg --edit-key <KEY_ID>
gpg> trust
```
You will be asked to select the trust level from the following:
```
1 = I don't know or won't say
2 = I do NOT trust
3 = I trust marginally
4 = I trust fully
5 = I trust ultimately
m = back to the main menu
```
Choose 5.



