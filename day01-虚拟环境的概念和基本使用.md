# day01
## 任务
* 了解虚拟环境的作用和概念
* 虚拟环境及在工程中的作用
* python中虚拟环境的管理模块有几个
* 详细了解virtualenvwrapper虚拟环境管理模块(命令)

## 笔记
* 作用：虚拟环境能够帮助开发人员进行环境隔离，避免项目之间的干扰。

*  安装配置virtualenv
    * 安装：pip install virtualenv
    * 创建目录：mkdir 目录名、进入目录：cd 目录名
    * 创建独立运行环境：virtualenv -p python3 环境名 
    * 进入虚拟环境：source ./环境名/bin/activate 
    * 安装第三方包：(环境名)目录名:pip3 install django 
    * 退出虚拟环境：deactivate

* 安装配置virtualenvwrapper:virtualenv缺点是需要记住每个虚拟环境的activate路径，当然你可以把所有虚拟环境创建在一起。或者使用虚拟环境的管理工具virtualenvwrapper

    * 安装virtualenvwrapper：pip3 install virtualenvwrapper
    * 设置linux环境变量，每次启动加载virtualenvwrapper：
        * 打开.bashrc
        * vim ~/.bashrc
        * 在.bashrc下面添加以下内容：
        ```
            export WORKON_HOME=~/VirtualEnvs   #设置virtualenv的统一管理目录
            export VIRTUALENVWRAPPER_VIRTUALENV_ARGS='--no-site-packages'   #添加virtualenvwrapper的参数，生成干净隔绝的环境
            export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3     #指定默认python解释器 可以用 which python3 查找python3的位置
            source /home/null/.local/bin/virtualenvwrapper.sh #执行virtualenvwrapper安装脚本 使用 sudo find / -name virtualenvwrapper.sh查找vitualenvwrapper.sh的位置
        ```
        * 保存退出后，执行:source ~/.bashrc

* virtualenvwrapper基本使用
    * 创建一个虚拟环境:mkvirtualenv 环境名
    * 进入虚拟环境：workon 环境名
    * workon 可以直接从多个虚拟环境中切换：workon 环境名2
    * 退出虚拟环境：deactivate
    * 列举所有的环境：lsvirtualenv
    * 删除虚拟环境：rmvirtualenv 环境名

* 保证开发与生产虚拟环境所使用的模块的一致性
    * 在开发机的虚拟环境中运行：pip freeze > requirements.txt
    * 在新的虚拟环境中运行：pip install -r requirements.txt 路径