docker的笔记
=====================
docker 指令简介
---------------------

.. code-block:: shell
    :linenos:
    
    # 显示所有镜像
    sudo docker images
    # 显示所有容器
    sudo docker ps -a
    # 删除所有容器
    sudo docker rm $(sudo docker ps -aq)
    # 停止并删除所有容器
    sudo docker stop $(sudo docker ps -q) & sudo docker rm $(sudo docker ps -aq)
    # (例子)启动nsis打包nsis安装包
    sudo docker run --name nsis \
        -it \
        -v /home/passoa/tmp:/container \
        flow123d/nsis-3.05-1 \
        /container/install.nsi
    # 附加到docker交互环境中
    sudo docker attach $container_id #container_id 是指docker ps 显示出来的id


.. _my-reference-label:

docker 镜像加速
-------------------------

对于使用 systemd 的系统，请在 /etc/docker/daemon.json 中写入如下内容（如果文件不存在请新建该文件）：

.. code-block:: json
    :linenos:
    
    {
        "registry-mirrors": ["https://mirror.ccs.tencentyun.com"]
    }

之后重新启动服务：

.. code-block:: shell
    :linenos:
    
    sudo systemctl daemon-reload
    sudo systemctl restart docker
