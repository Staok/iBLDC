以下文章不一定按顺序看，先整体看，再选择性的、针对性的去看。做好总结，内化。

无感BLDC六步法实施记录：

- 启动：起步时候是开关启动（只给步），当有感应电动势时候再根据BEMF来正常转动。这里有讲bldc启动 [跟着高手学！DIY无刷电机控制器：画板、打样、焊接、调... - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/472639823)。

FOC实施：

- 启动：可以HALL 方波六步法启动，然后再切为FOC转动。
- 一种冗余设计：正常电流采样时候测流三相电流得到id\iq进行正常转动，当电流采样不正常时候则用三相电压进行变换得到vd\vq来进行控制转动（SimpleFOC之前版本是这种方法；有的地方叫“电压模式”，转动效果也还行，但是没有电流环、力矩控制是开环的、效率降低、电流波形差、负载波动、震动或噪音；低速低动态可以因为此时电压矢量和电流矢量近似，其他情况则差别很大），电压模式这是备用方案，不至于电流采样部分坏掉系统不会一下子不工作。

基础学习，进阶补充：

 [无刷电机 - 知乎 (zhihu.com)](https://www.zhihu.com/topic/20054359/hot)，[电机矢量控制 - 收藏夹 - 知乎 (zhihu.com)](https://www.zhihu.com/collection/576911917)。

 [电机控制知乎好帖汇总 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/354827838)

[如何学习嵌入式电机控制? - 知乎 (zhihu.com)](https://www.zhihu.com/question/324921110/answer/2206814434)

[永磁同步电机启动时使用霍尔传感器，转速上来后切换到无感矢量闭环控制，这种方法的可行性如何？ - 知乎 (zhihu.com)](https://www.zhihu.com/question/282034438/answer/2154193563)，无感 FOC 的三段式启动过程分析。

[直接转矩控制和矢量控制区别？ - 知乎 (zhihu.com)](https://www.zhihu.com/question/43572058)。



[电机控制杂谈 - 知乎 (zhihu.com)](https://www.zhihu.com/column/c_1116148192206675968)

[电机控制电流环设计笔记 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/493236707).



[无感FOC性能到底能做到怎么样？ - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/61688599)。里面的后面有**五个foc文章** 记录。**无感foc，比低速，比加速，比高速，比重载**。



**反电动势估计**：

[【学习笔记】转子位置估算-反电势法 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/459302432)。[PMSM角度观测器——扩展反电动势(EEMF)直接计算法 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/382337513)。

**观测器估计**：

[基于滑模观测器的无位置传感器控制 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/394599297)

[永磁同步电机无速度传感器控制（一）——滑模观测器（三）【由扩展反电势得到电机位置和速度信息】 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/372118384)

[彻底吃透滑模观测器（PMSM无感算法）（理论精讲+推导+算法+调参+硬件运行） - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/416224632)

[【电机控制】无感FOC与滑模观测器 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/127170880)

[无感PMSM四种种常见观测器特性比较：龙伯格观测器+PLL、滑模观测器+PLL、扩展卡尔曼滤波观测器以及非线性磁链观测器。 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/355512103)。

**高频注入**：

[永磁同步电机 spmsm 和 ipmsm 的区别总结_小麦大叔的博客-CSDN博客_ipmsm](https://blog.csdn.net/u010632165/article/details/103637894)。



[高频注入（HFI）原理分析Part1 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/362399772)，还有part2、3...

[高频脉振电压注入 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/271269368)

[产品级IPMSM高频注入低速无传感器控制方法_转子磁场定向的博客-CSDN博客](https://blog.csdn.net/RotorandStator/article/details/108917678)。

[ HFI高频注入代码解读_转子磁场定向的博客-CSDN博客_高频注入法源码](https://blog.csdn.net/RotorandStator/article/details/111994878)。

**参数辨识**：

[参数辨识最小二乘法——永磁同步电机矢量控制课题拓展 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/369949394)

**其它方法**

[一种新颖的PMSM转子初始位置检测_转子磁场定向的博客-CSDN博客_转子初始位置检测](https://blog.csdn.net/RotorandStator/article/details/118359917)。

[基于磁链模型的非线性观测器_转子磁场定向的博客-CSDN博客_磁链观测器](https://blog.csdn.net/RotorandStator/article/details/118026889)。



**ST MCSDK**：

[STM32电机库（ST-MC-Workbench）学习记录——无感FOC代码生成 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/377112424)
