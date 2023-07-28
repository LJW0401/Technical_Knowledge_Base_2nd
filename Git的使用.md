# Git的使用
- 关于git的一些使用操作介绍，如有补充，欢迎提出。
- 这部分内容主要覆盖GitHub的使用。
## 关于GitHub
- 由于在Gitee中讲述过Gitee了，本部分不在重复讲述。
- GitHub大体上与Gitee差不多，只是在一些细节上有所不同。


# 目录
[GitHub部分](#github部分)<br>
&emsp;&emsp;[Git配置代理网络](#git配置代理网络)<br>
&emsp;&emsp;[GitHub上传大文件](#github上传大文件)<br>
&emsp;&emsp;[将Gitee仓库转存到GitHub](#将gitee仓库转存到github)<br>
[]()<br>
[]()<br>

# GitHub部分
## Git配置代理网络

- 问题：开启梯子的代理后 `pull` `push` `clone` 的速度依然很慢，只有10kb左右
- 原因：虽然开启了代理，但可能 git push 并没有走代理，因为需要在 git 里面进行配置。
- 解决：

    ***！！！梯子 一定要开全局模式！！！***
    ```
    git config --global http.proxy socks5://127.0.0.1:7890
    git config --global https.proxy socks5://127.0.0.1:7890
    ```

    其中`7890`为`Clash for Windows`代理服务器在本机上的端口，具体端口号请查看自己代理的设置

    为了防止对gitee速度的影响，建议只对GitHub采用该规则：
    ```
    git config --global http.https://github.com.proxy socks5://127.0.0.1:7890
    git config --global https.https://github.com.proxy socks5://127.0.0.1:7890
    ```

    取消全局代理的设置：
    ```
    git config --global --unset http.proxy
    git config --global --unset https.proxy
    ```
    参考文章：<br>
    [为什么开了代理，git push 还是很慢或报错](https://blog.csdn.net/qq_42951560/article/details/124332605)<br>
    [解决git clone速度太慢的问题（SS socks5代理）](https://blog.csdn.net/qq_37409292/article/details/83005919)

## GitHub上传大文件
- 下载并安装 [git-lfs-windows-v3.3.0.exe](https://gitee.com/SMBU-POLARBEAR/knowledge_base/blob/master/OtherFiles/git-lfs-windows-v3.3.0.exe)
- 在根文件夹下写配置文件`.gitattributes`

参考文章：<br>

## 将Gitee仓库转存到GitHub
1. 在GitHub上创建一个空的远程仓库（***里面不能有任何东西***）
1. 在要转存的仓库中打开 git 终端
1. 输入以下指令来切断与原有远程仓库的连接。
    ```
    git remote remove origin
    ```
1. 输入以下指令来与新的远程仓库建立连接。（将`<remote-url>`替换为远程仓库地址）
    ```
    git remote add origin <remote-url>.git
    ```
1. 输入以下指令来更换主分支名
    ```
    git branch -M main
    ```
1. 输入以下指令将本地仓库推送到远程仓库
    ```
    git push -u origin main
    ```
- 如果速度很慢请参照[Git配置代理网络](#git配置代理网络)

参考文章：<br>
![push_an_existing_repository](pictures/Git_Use/push_an_existing_repository.png)


小企鹅 编辑于 2023.7.28