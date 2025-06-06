基本概念约定
========================

简单抽卡模型
------------------------

定义每次抽卡至多获得一个道具，每次获得道具所需抽数为独立同分布的随机变量 :math:`X` ，且所有概率都分布在正整数范围上，那么此抽卡模型为简单抽卡模型。
如每次抽卡都是独立伯努利试验，固定概率为 :math:`P` 的抽卡模型是简单抽卡模型，其获得道具所需抽数分布为几何分布。

.. note::
    
    现实情况中很少出现一抽能同时获得多个道具的情况，将讨论局限于简单抽卡模型是有好处的。
    如简单抽卡模型中，可以将所有当前条件概率的表述等价转化为当前获取道具所需抽数分布的形式，同理也可以反向转换。这样的性质可以为很多操作带来方便。
    以 :math:`E(X)` 表示模型获得道具的期望，:math:`P_{avg}(X)` 表示模型获得道具的综合概率。

简单保底抽卡模型
------------------------

如果一个简单抽卡模型获得道具所需抽数是具有 **有限支持** (finite support)的，即随机变量的概率分布在有限个值上的取值不为零，有限个值之外的所有其他值上，概率分布为零。则将这种抽卡模型称为 **简单保底抽卡模型**。
常见带保底的抽卡模型大都可以归类为简单保底抽卡模型。例如原神获取五星物品的模型，每次获得五星物品所耗费抽数都是独立同分布的，并在有限抽内一定能获得五星物品。

简单保底抽卡模型的性质
--------------------------

.. admonition:: 符号约定
    :class: note

    :math:`p_i` 表示在前 ``i-1`` 抽没有获得道具，第 ``i`` 抽获得道具的条件概率。

    :math:`P(X=i)` 表示获得一个道具时，恰好用了 ``i`` 抽的概率。或 :math:`X` 的分布律在 ``i`` 处的值。

    :math:`n` 表示硬保底抽数，也即简单保底抽卡模型至多使用多少抽才可以获得道具，也是随机变量分布有概率位置的最大值。

**求简单保底抽卡模型的期望与综合概率**

简单保底抽卡模型的期望为 :math:`E(X)=\sum_{k=1}^{n}{p_k\cdot k}` 。其综合概率 :math:`P_{avg}(X)=1/E(X)` ，意义为同一个玩家进行了无穷次抽卡尝试后道具出现的频数。

**已知条件概率求抽数分布**

获得一个道具时，恰好花费 ``i`` 抽的概率 :math:`P(X=i)=p_i\prod_{n=1}^{i-1}{(1-p_n)}` 

**已知抽数分布求条件概率**

在已经有 ``i-1`` 抽没有获得道具的情况下，第 ``i`` 抽获得道具的条件概率 :math:`p_i=\frac{P(X=i)}{\sum_{k=i}^{n}{P(X=k)}}` 

.. note::

    简单保底抽卡模型第 ``n`` 抽的位置对应条件概率为1，即保底位置一定能获得道具。

.. **获得多个道具时所需抽数分布**

.. 实际情况中也关心要获取多个道具时所需抽数的分布，即求获取 :math:`n` 个道具所用抽数这个随机变量的分布 :math:`X_{total}=X_1+X_2+...+X_n` 。
.. 已知获取一个道具的分布情况下，利用动态规划或是卷积求获得多个道具的分布是非常容易的。

.. .. note::
    
..     继续以原神五星的抽卡模型举例，已知抽一个五星道具所需的抽数分布，现在想知道如果连续抽。

.. 说明一下问题，通俗举例，然后可以用随机变量相加解释。
.. 可以采用的方法有很多，模拟、转移矩阵、动态规划、卷积。
.. 先以获得两个道具的抽数分布举例
.. :math:`P(X_{UP}=i)=0.5\cdot P(X_1=i)+0.5\cdot P(X_2=i)`


.. 两类问题（这部分拆到运气衡量部分）
.. ------------------------

.. 一个是抽n个道具，需要花费抽数的分布

.. 一个是投入k抽，能抽到道具个数的分布