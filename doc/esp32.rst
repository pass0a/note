esp32的笔记
=====================
esp32开发环境搭建
---------------------
因为esp32的开发环境搭建较为复杂，所以我们直接使用docker来搭建。
（国内环境，请先设置到镜像加速 :ref:`my-reference-label`.）

.. code-block:: shell
    :linenos:
    
    # 拉取esp32开发环境
    sudo docker pull espressif/idf
    # 运行容器
    sudo docker run -v $PWD:/home/passoa/git/esp -w /home/passoa/git/esp -it espressif/idf
    # 更新apt
    apt-get update
    # 安装openssh-server
    apt-get install openssh-server    
    # 修改/etc/ssh/sshd_config中的如下两项
    # PermitRootLogin yes  
    # UsePAM no
    # 启动sshd
    mkdir -p /var/run/sshd
    /usr/sbin/sshd -D &
    # 映射端口号
    sudo docker run --rm -p "2020:22" -v $PWD:/home/passoa/git/esp -w ~/esp -it esp32
    # 修改后需要保存镜像
    sudo docker commit $container_id new_name #container_id 是指docker ps 显示出来的id

vscode配合
--------------
配合vscode设置esp32开发环境，修改~/.ssh/config文件如下。

.. code-block:: shell
    :linenos:

    Host linux_esp
    HostName 192.168.56.101
    User passoa
    Port 22
    IdentityFile C:/Users/hsae/.ssh/id_rsa

    Host docker_esp
    HostName 192.168.56.101
    User root
    Port 2020
    IdentityFile C:/Users/hsae/.ssh/id_rsa


快速问题
------------
1、出现GPG error和NO PUBKEY错误，请下载指定的key
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. code-block:: shell
    :linenos:

    apt-key adv --recv-keys --keyserver keyserver.ubuntu.com $PUBKEY

2、 apt更新软件慢
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
更新souces.list，并替换/etc/apt/sources.list

.. code-block:: shell
    :linenos:

    cp ./sources.list /etc/apt/sources.list
    
sources.list内容如下：

.. code-block:: yaml
    :linenos:

    # 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
    deb http://mirrors.tuna.tsinghua.edu.cn/debian/ stretch main contrib non-free
    # deb-src http://mirrors.tuna.tsinghua.edu.cn/debian/ stretch main contrib non-free
    deb http://mirrors.tuna.tsinghua.edu.cn/debian/ stretch-updates main contrib non-free
    # deb-src http://mirrors.tuna.tsinghua.edu.cn/debian/ stretch-updates main contrib non-free
    deb http://mirrors.tuna.tsinghua.edu.cn/debian/ stretch-backports main contrib non-free
    # deb-src http://mirrors.tuna.tsinghua.edu.cn/debian/ stretch-backports main contrib non-free
    deb http://mirrors.tuna.tsinghua.edu.cn/debian-security stretch/updates main contrib non-free
    # deb-src http://mirrors.tuna.tsinghua.edu.cn/debian-security stretch/updates main contrib non-free

3、 安装openssh-server不成功
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
安装openssh-server出现如下错误

.. code-block:: shell
    :linenos:

    openssh-server : Depends: openssh-client (= 1:7.4p1-10+deb9u7) but 1:7.6p1-4ubuntu0.3 is to be installed

那么需要把client的版本更新或降级到指定版本。

.. code-block:: shell
    :linenos:
    
    apt-get install openssh-client=1:7.4p1-10+deb9u7
