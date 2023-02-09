.. _git:

Git
===========


分支管理
-----------

创建空白分支，查看提交信息

.. code-block:: bash

    git checkout --orphan emptybranch
    git log --graph --pretty=oneline --abbrev-commit
    git log --oneline --graph --decorate --all

合并分支
~~~~~~~~~~~

当一个正在开发的 feature、bugfix 分支完成后，需要提交Merge Request请求合并入 master 或其他分支。解决冲突的一种方法是将 master 分支合入到当前分支。

rebase在git中是一个非常有魅力的命令，使用得当会极大提高自己的工作效率；相反，如果乱用，会给团队中其他人带来麻烦。

它的作用简要概括为：可以对某一段线性提交历史进行编辑、删除、复制、粘贴；因此，合理使用rebase命令可以使我们的提交历史干净、简洁！


补丁管理
-----------

生成补丁文件

.. code-block:: bash

    git format-patch 8d3ce02436066e3 --stdout > test.patch
    git format-patch -2  //生成距离HEAD最近的2个patch
    git diff > test.patch
    git apply test.patch
