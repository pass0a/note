Poseidon3笔记
============================
打包流程
~~~~~~~~~~~~~~~~

发布版本

#. 首先提交代码并合并请求(略)
#. git tag v1.0.x
#. git push origin v1.0.x

开发版本

#. 登录https://passoa.coding.net/p/repertory/ci/job?id=246128
#. 点击立即构建即可

flow项目启动
~~~~~~~~~~~~~~~~~~~

.. code-block:: SQL
    :linenos:

    pm2 list  # 查看当前运行的实例
    pm2 start dist/main.js  # 如果找不到flow实例，可以直接启动
    # 如果找到flow实例，可以通过restart/start/stop来重启，启动，停止flow
    # 0由pm2 list显示的id替换
    pm2 restart/start/stop 0 
