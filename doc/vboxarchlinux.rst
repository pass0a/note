vbox下arclinux的笔记
=====================
enp0s8没有ip
---------------------
如果设置完hostonly后，发现enp0s8没有IP，或者有时候会突然丢失IP，那么可以直接通过pacman安装NetManager来解决这个问题，当然要记得启动NetworkManager服务。

.. code-block:: shell
    :linenos:

    pacman -S NetworkManager
    systemctl enable NetworkManager
    systemctl start NetworkManager
    systemctl status NetworkManager
