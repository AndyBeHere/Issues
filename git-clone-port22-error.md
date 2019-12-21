# git clone port22 error

## git clone port22 error

### 问题定位

1.确认authentication没有问题：

```bash
ssh -T git@github.com
```

2.由于报错原因为**port 22: Operation timed out**, 可将端口改为443尝试。

**解决方法1**：在存放公钥和私钥的文件里，新建config文本。命令sudo vi ~/.ssh/config,输入以下内容，将端口配置为443。

> ```text
> Host github.com
> User YourEmail@163.com
> Hostname ssh.github.com
> PreferredAuthentications publickey
> IdentityFile ~/.ssh/id_rsa
> Port 443
> ```

:wq退出，然后在terminal进行如下配置。

```bash
$ git config --global user.name "XXX"
$ git config --global user.email XXX@xx.com
```

\*\*\*\*

