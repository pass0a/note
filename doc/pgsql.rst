TypeOrm 与 SQL笔记
===========================
获取join on最新的记录
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/// @todo 说明没有写

.. code-block:: SQL
    :linenos:

    select * from version_plan a 
     left join (
     select max("id") as id,"versionId" from version_history group by "versionId") b 
     on a.id=b."versionId"
     left join version_history c 
     on c.id=b.id order by c.stage,a.version

ubuntu上配置pgsql
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. /etc/postgresql/9.x/main下修改postgresql.conf，增加一条listen_addresses = '*'
#. /etc/postgresql/9.x/main下修改pg_hba.conf，增加一条host  all  all 0.0.0.0/0 md5
#. 修改密码

.. code-block:: shell
    :linenos:

    sudo -u postgres psql
    \password
    \q
    # sudo /etc/init.d/postgresql start  开启
    # sudo /etc/init.d/postgresql stop  关闭
    sudo /etc/init.d/postgresql restart  重启
    