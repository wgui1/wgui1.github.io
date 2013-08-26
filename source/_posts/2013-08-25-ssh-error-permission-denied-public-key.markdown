---
layout: post
title: "ssh error: Permission denied(public_key)"
date: 2013-08-25 12:37
comments: true
categories: ssh git heroku
---

I met the ssh error while I publish application to heroku. And I googled for a solution.

By chance I found this comment from the same question that Travis.Jensen asked one year ago.
>I'm just stuck banging my head against a keyboard with no recourse but to hope the almighty god of Google can answer it.

[git push heroku master Permission denied (publickey). fatal: The remote end hung up unexpectedly](http://stackoverflow.com/questions/12206779/git-push-heroku-master-permission-denied-publickey-fatal-the-remote-end-hung)

Fortunitely, I have answer from Almighty god of Google one year later.
The key point of public key problem may be related with both client and server side.

1. first, check client site if ssh key is properly configured. use 'ssh-add -l' to check if the key properly loaded in SSH.

2. if there is no ssh key listed, generate a ssh key by using 'ssh-keygen' to generate one.

3. register ssh key to remote server, like git, heroku servers.

For github related, please refer to FAQ: [git: Generate SSH keys](https://help.github.com/articles/generating-ssh-keys)

For heroku related, [heroku: Managing Your SSH keys](https://devcenter.heroku.com/articles/keys)


