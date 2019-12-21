# Issues

## 问题定位

如果某些命令的执行文件目录不在sudo运行的默认目录下，则需要指定目录的完整路径:

**问题原因：**

{% hint style="info" %}
 因为当在Linux下用sudo执行某一命令时，是在原进程（parent process）的基础上fork出来一个子进程（child process），这个子进程是以root权限执行的。然后在子进程中，执行你在sudo后面跟的命令。 在子进程中是无法调用涉及到父进程的状态的一些命令的，所以**非系统内置命令会被拒绝**。这就是为什么会出现command not found的提示。
{% endhint %}



**解决方法1**： 在/etc/sudoers文件内增加这么一行:Defaults secure\_path=”/bin:/usr/bin:/usr/local/bin:…”, 把要用的命令path包括进去。

```bash
$ sudo vi /etc/sudoers 
```

**解决方法2**：重新编译sudo，不带 -with-secure-path选项

record issues and solutions

