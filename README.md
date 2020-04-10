# Windows服务器自动化部署模板

本模板是用于控制Windows服务器Ansible自动化部署项目模板

## 项目命名

win-ansible-repositoryName

例如：win-ansible-wamp, win-ansible-wampserver

## 项目结构

|   项   |      |      |
| ---- | ---- | ---- |
|   .github   |  Github通过的在线action服务    |      |
|   docs   |   产品文档   |      |
|    vars  |   全局变量   |      |
|    roles  |   所有roles   |      |
|    ansible.cfg  |   项目配置文件   |      |
|    sample.yml  |   项目入口文件   |      |
|    requirements.yml  |   项目所依赖的模块化公共roles下载列表   |  项目运行的时候    |
|    Changelog.md  |   日志   |      |
|    License.md  |   开源协议   |      |
|    project_readme.md  |   项目概要   |  替换现有README.md    |
|    Readme.md  |   模板说明   |  需删除    |

## 项目运行

通过如下4个步骤即可启动项目运行

```
pip install ansible
git clone https://github.com/Websoft9/win-ansible-sample.git
cd win-ansible-sample
ansible-galaxy install -r requirements.yml -f
ansible-playbook -i hosts sample.yml -c local  -e init=0
```