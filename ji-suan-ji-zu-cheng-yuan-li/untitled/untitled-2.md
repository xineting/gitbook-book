# 2-4-浮点数的表示

## 1-浮点数的基本格式

![](../../.gitbook/assets/image%20%28199%29.png)

## 2-浮点数的规格化

规格化:规定尾数的最高数位必须是一个有效值 。

* 左规:当浮点数运算的结果为非规格化时要进行规格化处理，
* 将尾数左移一位，阶码减1\(基数为2时\)。
* * 右规:当浮点数运算的结果尾数出现溢出\(双符号位为01或10\)时，
* 将尾数右移一位，阶码加1\(基数为2时\)

![](../../.gitbook/assets/image%20%28376%29.png)

![](../../.gitbook/assets/image%20%28114%29.png)

## 3-IEEE 754标准

![](../../.gitbook/assets/image%20%28256%29.png)

![](../../.gitbook/assets/image%20%2859%29.png)

![](../../.gitbook/assets/image%20%28156%29.png)

