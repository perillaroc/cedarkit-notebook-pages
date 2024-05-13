安装
=====

本节介绍如何在 CMA 国家级超算子系统 1 上安装 cedarkit 工具栈。

cedarkit 工具栈
----------------

cedarkit 工具栈均在 GitHub 开源，并可以通过 pip 安装。

使用 pip 在线安装 cedarkit-maps：

.. code-block:: bash
    
    pip install reki cedarkit-comp cedarkit-maps

如果想要获取最新代码，可以访问 GitHub 代码库克隆主分支：

- reki: https://github.com/cemc-oper/reki
- cedarkit-comp: https://github.com/cemc-oper/cedarkit-comp
- cedarkit-maps: https://github.com/cemc-oper/maps

附加工具库
----------

从 METCODE 中下载 cemc-meda-data 包并安装。
项目地址（需要 CEMC 组权限）： http://codingcorp.mc.met.cma/p/cedarkit/d/cemc-meda-data/git

.. code-block:: bash
    
    cd cemc-meda-data
    pip install .

.. note::
    如果使用 CMA 超算平台，可以设置 CMA 的 PYPI 镜像，支持内网访问，详情请参考 `PyPI 镜像使用帮助 <http://mirrors.cma.cn/help/pypi.html>`_。

    例如上述安装 cedarkit 工具栈的命令可以修改为

    .. code-block:: bash

        pip install reki cedarkit-comp cedarkit-maps \
            -i http://pypi.mirrors.cma.cn:8080/root/pypi/+simple/ \
            --trusted-host pypi.mirrors.cma.cn 

预安装环境
----------

CMA 国家级超算子系统 1 和 2 可以使用 **wangdp** 账户预安装 conda 环境 (**py312-cedar**) 进行测试，使用方法如下：

激活 conda 环境

.. code-block:: bash

    module load conda/2023.03.01
    eval "$(/g1/app/apps/anaconda/2023.03.01/condabin/conda shell.bash hook)"

添加 wangdp 账户 conda 环境目录

.. code-block:: bash

    conda config --add envs_dirs /g1/u/wangdp/.conda/envs

激活 py312-cedar 环境

.. code-block:: bash

    conda activate py312-cedar

.. warning::

    该环境仅供测试，请不要在业务环境中使用。
    个人账户环境可能会有变动，如果无法使用，请及时联系账户负责人。