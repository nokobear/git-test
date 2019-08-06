# git-test
This is my test repository to test how to use git and github effectively.

## git frontends
- browser (github)
- git (local)
- tig (local)

## git commands

clone
```sh
git clone https://github.com/nokobear/git-test
```

view

```sh
git log
git status
```

action

```sh
git add .
git commit -m "title"
git tag 0.1.0 105e2e57fff64791b5899f569b30272ae063f4ef
```

push

```sh
git push origin master
```

## push without password

There are 4 ways to do it.

1. use ssh
2. use https and cached password
3. use https and .netrc (bad way at security.)
4. use https and .netrc.gpg

1-3. omit
### 4. use https and .netrc.gpg

create `~/.netrc`

```sh
touch ~/.netrc
chmod 600 ~/.netrc
vim ~/.netrc
```

~/.netrc

    machine github.com
      login nokobear
      password xxxxxxxxxxxx
      protocol https
    
    machine gist.github.com
      login  nokobear
      password xxxxxxxxxxx
      protocol https

push test.

```sh
cd git-test
git push origin master
```

gpg encrypt.

```sh
gpg --gen-key
# (keytype:RSA and RSA, bitlength:2048, limit:0day(unlimited),
#  name:nokobear, email:email_address, comment:
 password:)
gpg -e -r email_address ~/.netrc
rm ~/.netrc
```

setup git-credential-netrc

```sh
# (download to ~/bin)
curl -o ~/bin/git-credential-netrc https://raw.githubusercontent.com/git/git/master/contrib/credential/netrc/git-credential-netrc
chmod 755 ~/bin/git-credential-netrc
git config --global credential.helper "netrc -f ~/.netrc.gpg -v"
```

optional
modify ~/.netrc

```sh
gpg -d ~/.netrc.gpg > ~/.netrc
vim ~/.netrc
gpg -e -r email_address ~/.netrc
```

## test show image
![hello](./img/hello.png)

