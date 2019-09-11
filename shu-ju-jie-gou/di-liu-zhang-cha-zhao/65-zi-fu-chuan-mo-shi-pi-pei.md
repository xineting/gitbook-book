# 6-5-串匹配算法-KMP算法\*

## 1-串的基本概念

> 是由零个或多个字符组成的有限序列。一般记为S

若两个串长度相等且每个对应位置的字符都相等时，称这两个串是相等的

### 1-2-子串

串中任意个连续的字符组成的子序列称为该串的子串，包含子串的串为主串通常称字符在序列中的序号为该字符在串中的位置。

子串在主串中的位置是以子串的第一个字符在主串的位置来表示的

## 2-串模式匹配

```cpp
int Index(SString S,SString T,int pos){
    int i=pos,j=1;
    while(i<=S.length && j<=T.length){
        if(S.ch[i]==T.ch[j]){
            i++;
            j++;
        }
        else{
            i=i-j+1;
            j=1;
        }
        if(j>T.length)
           return i-T.length;
       else{
           return 0;
       }
    }
}
```

O\(mn\)

## 3-KMP算法

* 前缀：除最后一个字符外，字符串的所有头部子串 
* 后缀：除第一个字符外，字符串的所有尾部子串 部分匹配值
* 字符串前缀和后缀最长相等前后缀的长度
* 
![](../../.gitbook/assets/image%20%28244%29.png)

![](../../.gitbook/assets/image%20%28110%29.png)

