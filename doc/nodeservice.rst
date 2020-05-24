Node服务相关笔记
===========================
PM2使用
~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. code-block:: shell
    :linenos:
    
    pm2 start （启动服务)
    pm2 save (保存当前已经启动了的服务)
    pm2 startup (设置开机自启的配置)
    
    # 一般的服务器，执行上面的三个步骤，就可以了，会看下下面命令的反馈
    # [PM2] [v] Command successfully executed.
    # +---------------------------------------+
    # [PM2] Freeze a process list on reboot via:
    # $ pm2 save
    # [PM2] Remove init script via:
    # $ pm2 unstartup systemd

如果，你的服务器有异常，那你可能需要自己执行某些命令，往下看

.. code-block:: shell
    :linenos:
    
    # 执行pm2 startup以后会得到以下提示 设置环境变量
    # [PM2] Init System found: upstart
    # [PM2] To setup the Startup Script, copy/paste the following command:
    # sudo env PATH=$PATH:/opt/bitnami/nodejs/bin /opt/bitnami/nodejs/lib/node_modules/pm2/bin/pm2 startup upstart -u bitnami --hp /home/bitnami

粘贴复制 sudo env….这一部分的命令 执行命令

设置完成，sudo reboot 手动重启服务器pm2 list 查看验证