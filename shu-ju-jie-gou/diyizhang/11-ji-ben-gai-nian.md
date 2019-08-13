# 1-1-基本概念

## 1-1-1-概念

1. 数据：数据是信息的载体，是描述客观事物属性的数、字符以及所有能够输入到计算机中并被计 算机程序识别和处理的符号的集合。
2. 数据元素：数据元素是数据的基本单位，通常作为一个整体进行考虑和处理。一个数据元素可由若干 个数据项组成，数据项是构成数据元素的不可分割的最小单位。例如，学生记录就是一个 数据元素，它由学号、姓名、性别等数据项组成。
3. 数据类型：数据类型是一个值的集合和定义在此集合上一组操作的总称。1\)原子类型:其值不可再分的数据类型。2\)结构类型:其值可以再分解为若干成分\(分量\)的数据类型。3\)抽象数据类型:抽象数据组织和与之相关的操作。
4. 抽象数据类型：理解抽象数据类型\(ADT\)是指一个数学模型以及定义在该模型上的一组操作。抽象数据类型 的定义仅取决于它的一组逻辑特性，而与其在计算机内部如何表示和实现无关。通常用 \(数据对象、数据关系、基本操作集\)这样的三元组来表示抽象数据类型。
5. 数据结构在任何问题中，数据元素都不是孤立存在的，而是在它们之间存在着某种关系，这种数据 元素相互之间的关系称为结构\(Structure\)。数据结构是相互之间存在一种或多种特定关系的数据元素的集合。数据结构包括三方面的内容:逻辑结构、存储结构和数据的运算。数据的逻辑结构和存储结构是密不可分的两个方面，一个算法的设计取决于所选定的逻辑 结构，而算法的实现依赖于所采用的存储结构。

## 1-1-2-逻辑结构

数据元素之间的逻辑关系，即从逻辑关系上描述数据。它与数据的存储无关，是独立于计算机的 数据的逻辑结构分为线性结构和非线性结构

![](../../.gitbook/assets/image%20%2841%29.png)

* 集合：结构中的数据元素之间除了“同属于一个集合”的关系外，别无其他关系。 类似于数学上的集合
* 线性结构 结构中的数据元素之间只存在一对一的关系。比如排队
* 树形结构 结构中的数据元素之间存在一对多的关系。比如家族族谱
* 图状结构或网状结构 结构中的数据元素之间存在多对多的关系。 比如地图

## 1-1-3-物理结构

顺序存储、链式存储、索引存储和散列存储。




