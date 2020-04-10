# Windows服务器自动化部署模板

本模板作为创建Ansible自动化部署项目（Windows平台）模板，任何新建的Ansible项目，必须基于此模板修改。同时，任何项目格式的优化变更，必须由开发团队持续维护和修正。

## 项目命名

win-ansible-repositoryName    

例如：win-ansible-wamp, win-ansible-wampserver  

前缀**win**的作用主要是区别于Linux项目，便于在项目库中识别。

## 项目结构

|   项   |  说明    |   备注   |
| ---- | ---- | ---- |
|   .github   |  Github通过的在线action服务    |      |
|   docs   |   产品文档   |      |
|    vars  |   全局变量   |      |
|    roles  |   所有roles   |      |
|    ansible.cfg  |   项目配置文件   |      |
|    sample.yml  |   项目入口文件   |      |
|    requirements.yml  |   项目所依赖的模块化公共roles下载列表   |  项目运行的时候[下载](https://github.com/websoft9win)    |
|    Changelog.md  |   日志   |      |
|    License.md  |   开源协议   |      |
|    project_readme.md  |   项目概要   |  替换现有README.md    |
|    Readme.md  |   模板说明   |  需删除    |

## 运行项目

### 前置条件

下面分别就主动端和被控端所需的条件进行精准的说明

#### 主控端

主控端必须是Linux系统，然后在Ansible的标准安装之上增加如下：

```
pip install pywinrm
apt-get install libkrb5-dev
pip install kerberos
pip install paramiko PyYAML Jinja2 httplib2 six
```

#### 被控端

Ansible可以管理包括Windows 7、8.1和10的桌面操作系统以及包括Windows Server 2008、2008 R2、2012、2012 R2、2016和2019的服务器操作系统。但需要如下的前置条件：

* Windows主机上安装PowerShell 3.0或更高版本，并且至少要安装.NET 4.0。
* Windows主机上启动WinRM服务
* WinRM 会用到5985端口，所以防火墙必须做开放处理

### 运行测试

当Windows服务器具备Ansible的前置条件后，在控制端可以通过如下4个步骤启动项目运行： 

```
pip install ansible
git clone https://github.com/Websoft9/win-ansible-sample.git
cd win-ansible-sample
ansible-galaxy install -r requirements.yml -f
ansible-playbook -i hosts sample.yml -e init=0
```
