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

zsh下配置.bash_profile不起作用
----------------------------------
当使用zsh时，如果直接在.bash_profile中配置，是不会工作的，因为zsh加载的是~/.zshrc。所以可以直接在.zshrc中配置。