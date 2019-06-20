## 本地windows安装软件
>git  
>vscode  
>Python
## vscode安装插件
>Chinese (Simplified) Language Pack for Visual Studio Code  
>Code Runner  
>Python
# 一.配置vscode远程开发
## 1.1 Windows安装OpenSSH
使用 PowerShell 安装 OpenSSH
```
Get-WindowsCapability -Online | ? Name -like 'OpenSSH*'

# This should return the following output:

Name  : OpenSSH.Client~~~~0.0.1.0
State : NotPresent
Name  : OpenSSH.Server~~~~0.0.1.0
State : NotPresent
```
然后，安装服务器和/或客户端功能：
```
# Install the OpenSSH Client
Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0

# Install the OpenSSH Server
Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0

# Both of these should return the following output:

Path          :
Online        : True
RestartNeeded : False
```
## 1.2 vscode安装插件
>Remote Development
## 1.3 打开cmd配置ssh密钥
```
ssh-keygen -t rsa -C "yaolisong@aliyun.com"
```
## 1.4 配置C:\Users\woyuc\.ssh\config文件
```
Host woyuchengying
    HostName 192.168.5.21
    User root
    IdentityFile C:\Users\woyuc\.ssh\id_rsa
```
## 1.5 配置远程服务器/root/.ssh/authorized_keys文件，文件内容为C:\Users\woyuc\.ssh\id_rsa.pub文件内容
## 1.6 点击vscode远程连接按钮开始连接
## 1.7 安装vscode插件
```
>vscode  
>Python
```
# 二.vscode连接GitHub
## 2.1 本地windows创建Github目录,vscode打开此文件夹之后使用git进行初始化
## 2.2 打开cmd配置ssh密钥
```
ssh-keygen -t rsa -C "yaolisong@aliyun.com"
```
## 2.3 在GitHub上《Settings》->《SSH and GPG keys》中配置sshkey,文件内容为C:\Users\woyuc\.ssh\id_rsa.pub文件内容,且去掉末尾邮箱信息
## 2.4 右击选择《在终端中打开》,执行相关命令
```
git remote add origin https://github.com/woyuchengying/python3.git
git clone https://github.com/woyuchengying/python3
cd python3
echo "" > README.md
git add README.md
git commit -m "first commit"
git push -u origin master
```