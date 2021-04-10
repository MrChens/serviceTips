# SSH Login with privateKey

## SSH无密码登陆的设置步骤
1. 在我们的服务器上生成一对SSH Key:SSH密钥和SSH公钥
2. 在服务器上安装公钥
3. 设置 SSH，打开密钥登录功能
4. 将私钥下载到客户端

### 1. 在我们的服务器上生成一对SSH Key:SSH密钥和SSH公钥
```
ssh-keygen  <== 建立密钥对
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa): <== 按 Enter
Created directory '/root/.ssh'.
Enter passphrase (empty for no passphrase): <== 输入密钥锁码，或直接按 Enter 留空
Enter same passphrase again: <== 再输入一遍密钥锁码
Your identification has been saved in /root/.ssh/id_rsa. <== 私钥
Your public key has been saved in /root/.ssh/id_rsa.pub. <== 公钥
The key fingerprint is:
0f:d3:e7:1a:1c:bd:5c:03:f1:19:f1:22:df:9b:cc:08 root@host
```
密钥锁码在使用私钥时必须输入，这样就可以保护私钥不被盗用。当然，也可以留空，实现无密码登录。

### 2. 在服务器上安装公钥
键入以下命令，在服务器上安装公钥：
```
[root@host ~]$ cd .ssh
[root@host .ssh]$ cat id_rsa.pub >> authorized_keys
```
如此便完成了公钥的安装。为了确保连接成功，请保证以下文件权限正确：
```
[root@host .ssh]$ chmod 600 authorized_keys
[root@host .ssh]$ chmod 700 ~/.ssh
```

### 3. 设置 SSH，打开密钥登录功能

编辑 `/etc/ssh/sshd_config` 文件，进行如下设置：

```
RSAAuthentication yes
PubkeyAuthentication yes
```
另外，请留意 root 用户能否通过 SSH 登录：
```
PermitRootLogin yes
```

当你完成全部设置，并以密钥方式登录成功后，再禁用密码登录：
```
PasswordAuthentication no
```
最后，重启 SSH 服务：
```
[root@host .ssh]$ service sshd restart
```

### 4. 将私钥下载到客户端