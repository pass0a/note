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
    # 启动nsis打包nsis安装包
    sudo docker run --name nsis \
        -it \
        -v /home/passoa/tmp:/container \
        flow123d/nsis-3.05-1 \
        /container/install.nsi