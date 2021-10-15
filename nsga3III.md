# NSGA-III解读
## 需要解决的问题
- 多目标优化问题只能处理低维度优化问题。随着维度的增加，非支配解会急剧增多，难以区分个体之间的好坏（选择压力下降），导致产生新解的空间不大
- 高维目标的多样性指标测量的所花费的计算量会变大，任何更快的近似计算可能会使最终解集的分布产生巨大的偏差
- 重组算子可能会变得低效，因为如果只有少数的非支配解高维度空间被找到，那么他们可能相距很远，而且产生的后代也和父代相差很远
- 可视化困难，不够直观

### 多目标问题

- 随机选择k个个体是否有影响？
> 不会，只是用来满足群体数目为N的要求

- 为什么设置的超平面就是接近帕累托最优平面
> ~~因为构造参考平面所使用的算法就是构造帕累托最优平面~~


## 名词
- fixed con-domination and variable con-domination （固定锥形支配和可变锥形支配）
- differential evolution (DE)

## NSGA-III取代NSGA-II的crowding distance的做法

1. 还是先按照非支配排序
2. 定义超平面参考点
3. 自适应归一化种群成员
4. 使用参考点关联操作
5. 利好的保存点操作

## 算法流程
![](https://gitee.com/wheatdll/picbed/raw/master/uPic/sNvuXF.png)


### 架构

### 结果
> For the five-objective DTLZ1 problem, MOEA/D performs better than NSGA-III, but in 8, 10, and 15objective problems, NSGA-III performs better.

> For DTLZ2 problems, the performance of MOEA/D-PBI is consistently better than NSGA-III, however NSGA-III performs better than MOEA/D-TCH approach. Figures 8, 9 and 10 show the distribution of obtained points for NSGAIII, MOEA/D-PBI, and MOEA/D-TCH algorithms on threeobjective DTLZ2 problem, respectively.
------
**conclude**

(i)MOEA/D-PBI performs consistently better than MOEA/DTCH approach, 
(ii) MOEA/D-PBI performs best in some problems, whereas the proposed NSGA-III approach performs best in some other problems, and 
(iii) in a non-uniformly distributed Pareto-optimal front (like in the DTLZ4 problem), both MOEA/D approaches fail to maintain a good distribution of points, while NSGA-III performs well.


在对DTLZ的放缩问题上，NSGA-III的处理也要比MOEA/D好，表现为IGD更低
-----
- 如何求向量的垂直距离

