`ssh {username}@{host}`

## Send files:

Using rsync command

https://www.tecmint.com/rsync-local-remote-file-synchronization-commands/



## Generate key:

`$cd ~/.ssh`

`$ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

It will ask for a place to save the key generated

Then, it will generate two key: id_rsa and id_rsa.pub

复制公钥到剪贴板`$pbcopy < ~/.ssh/id_rsa.pub`

Ssh到服务器，在根目录~下mkdir .ssh

`$cd .ssh`  下面有一个文件authorized_keys, 没有的话mkdir 一个

`$nano authorized_keys`

打开文件后粘贴剪贴板里的公钥,保存退出

`$ssh-add ~/.ssh/id_rsa` 来添加私钥文件到ssh

`$ssh root@{host}` 即可登陆远程服务器

自此之后登陆服务器都不需要密码，可以ssh直接登录



显示本机所有身份`$ssh -L`

删除所有身份`$ssh -D`