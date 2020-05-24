vscode相关设置
==================================

远程SSH编辑编译调试
-----------------------------
前提条件
~~~~~~~~~~~~~~
* 远程系统需要安装openssh，gdb
* 本地系统需要安装git,vscode，Remote-Development扩展 

免密登录ssh
~~~~~~~~~~~~~~~
在git bash中，输入如下指令

.. code-block:: shell
    :linenos:

    ssh-keygen //如果已经生成过，可跳过
    ssh-copy-id -i ~/.ssh/id_rsa.pub  用户名字@192.168.x.xxx
    ssh 用户名字@192.168.x.xxx // 测试连接


调试设置
~~~~~~~~~~~~~~~~~~~~
在项目根目录下新建.vscode/setting.json，输入如下内容

.. code-block:: javascript
    :linenos:

    {
        "version": "0.2.0",
        "configurations": [
            {
                "name": "gdb Remote Launch",
                "type": "cppdbg",
                "request": "launch",
                "program": "~/git/hello/a.out",
                "args": [
                    "myarg1",
                    "myarg2",
                    "myarg3"
                ],
                "stopAtEntry": true,
                "environment": [],
                "externalConsole": false,
                "MIMode": "gdb",
                "miDebuggerPath": "gdb",
                "miDebuggerArgs": "gdb",
                "linux": {
                    "MIMode": "gdb",
                    "miDebuggerPath": "/usr/bin/gdb",
                    "miDebuggerServerAddress": "192.168.56.101:2333",
                },
                "logging": {
                    "moduleLoad": false,
                    "engineLogging": false,
                    "trace": false
                },
                "setupCommands": [
                    {
                        "description": "Enable pretty-printing for gdb",
                        "text": "-enable-pretty-printing",
                        "ignoreFailures": true
                    }
                ],
                "cwd": "${workspaceFolder}",
            }
        ]
    }

本节设置请参考如下网址

1) `使用 VSCode 远程访问代码以及远程 GDB 调试 <https://warmgrid.github.io/2019/05/21/remote-debug-in-vscode-insiders.html>`_
#) `清华大学pypi帮助页面 <https://mirrors.tuna.tsinghua.edu.cn/help/pypi/>`_
#) `conda使用介绍 <https://zhuanlan.zhihu.com/p/57287956>`_

ReadTheDoc设置
--------------------------
安装miniconda,打开conda CMD

.. code-block:: shell
    :linenos:

    conda create -n py37 python=3.7 
    conda activate py37
    pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
    pip install flake8 sphinx sphinx-autobuild sphinx_rtd_theme

如果遇见找不到python的问题，可以通过ctrl+shift+p,输入python:select interpreter来指定python。
    
本节设置请参考如下网址

1) `设置开源镜像加速 <http://vra.github.io/2018/04/18/mirrors-speedup/>`_
#) `清华大学pypi帮助页面 <https://mirrors.tuna.tsinghua.edu.cn/help/pypi/>`_
#) `conda使用介绍 <https://zhuanlan.zhihu.com/p/57287956>`_

远程开发
--------------
