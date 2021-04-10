# SSH Login without password

## SSH无密码登陆的设置步骤
1. 在我们的电脑上生成一对SSH Key:SSH密钥和SSH公钥
2. 将公钥上传到你要登陆的Linux服务器上


### 1.在我们的电脑上生成一对SSH Key:SSH密钥和SSH公钥
打开纵断使用下面的命令行生成RSA密钥和公钥.`-t 表示type`
`ssh-keygen -t rsa`
rsa是默认的加密类型，所以可以只输入`ssh-keygen`.默认的RSA长度是2048位.也可以指定长度4096位。
`ssh-keygen -b 4096 -t rsa`

生成`SSH Key`时会要求你指定一个文件来保存密钥，按Enter键使用默认的文件．然后需要输入一个密码来加密你的SSH Key．密码至少要20位长度．SSH密钥会保存在home目录下的`.ssh/id_rsa`文件中．SSH公钥保存在`.ssh/id_rsa.pub`文件．

```
Generating public/private rsa key pair.
Enter file in which to save the key (/home/linux/.ssh/id_rsa): 　按Enter键
Enter passphrase (empty for no passphrase): 　　输入一个密码
Enter same passphrase again: 　　再次输入密码
Your identification has been saved in /home/linux/.ssh/id_rsa.
Your public key has been saved in /home/linux/.ssh/id_rsa.pub.
The key fingerprint is:
e1:dc:ab:ae:b6:19:b0:19:74:d5:fe:57:3f:32:b4:d0 matrix@vivid
The key's randomart image is:
+---[RSA 4096]----+
| .. |
| . . |
| . . .. . |
| . . o o.. E .|
| o S ..o ...|
| = ..+...|
| o . . .o .|
| .o . |
| .++o |
+-----------------+
```

### 2. 将公钥上传到你要登陆的Linux服务器上

`ssh-copy-id username@remote-server`
输入远程用户的密码后，SSH公钥就会自动上传．SSH公钥保存在远程Linux服务器的.ssh/authorized_keys文件中．

上传完成后，SSH登录就不需要输入密码．但是首次使用SSH Key登录时需要输入一次SSH密钥的加密密码．

使用scp命令来传送文件时也不需要输入密码．
