python笔记
=====================
conda镜像加速
---------------------
参考如下即可
https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/

conda更新所有包
~~~~~~~~~~~~~~~~~~~~~~
.. code-block:: shell
    :linenos:

    conda update --strict-channel-priority --all

补全问题
~~~~~~~~~~~~~~~~~~~~~~~~
在vscode+python中，很多时候实例化对象后，无法进行智能提示，原因是vscode不能推测如（wave.open）返回的类型是啥，可以通过注释来告诉IDE

.. code-block:: python
    :linenos:
    
    import wave
    fo = wave.open(u"test.wav", "wb")  # type: wave.Wave_write
    fo.setnchannels(1)
    fo.setsampwidth(16)
