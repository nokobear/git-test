# git-test
test (how to use git repository)

## test show image
![hello](./img/hello.png)

## frontends
- browser(github)
- git(local)
- tig(local)

## git commands

clone

    git clone https://github.com/nokobear/git-test

view

    git log
    git status

action

    git add .
    git commit -m "title"
    git tag 0.1.0 105e2e57fff64791b5899f569b30272ae063f4ef

push

    git push origin master

## push without password

1. use ssh
2. use https and credential-helper
3. use https and .netrc
4. use https and .netrc.gpg

1-3. omit
### use https and .netrc.gpg

create `~/.netrc`

    touch ~/.netrc
    chmod 600 ~/.netrc
    vim ~/.netrc

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

    cd git-test
    git push origin master

gpg encrypt.

    gpg --gen-key
    gpg -e -r email_address ~/.netrc

