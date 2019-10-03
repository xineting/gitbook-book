# 3-3-栈的应用

## 1-括号匹配

```c
bool Check(char *str ){
    stack s;
    InitStack(s);
    int len=strlen(str); //字符串长度为len 
    for(int i=0;i<len;++i){
        char a=str[i]; 
        switch(a){
            case '(': 
            case '[':
                Push(s,a);
                break; 
            case ')':
                if( Pop(s)!=‘(‘ ) 
                    return false; //出栈顶。如果不匹配直接返回不合法
                break; 
            case ']':
                if( Pop(s)!=‘]’ ) 
                    return false;
                break; 
        }
    }
    if(Empty(s)) 
        return true; //匹配完所有括号最后要求栈中为空
    else return false
}
```

## 2-表达式求值

![](../../.gitbook/assets/image%20%28238%29.png)



* 规则:从左到右扫描表达式的每个数字和符号，遇到数字就进栈，遇到 符号就将处于栈顶的两个数字出栈然后跟这个符号进行运算，最后将运 算结果进栈，直到最终获得结果
* 以计算\(5+20+1\*3\)/14 为例 它的后缀表达式是5 20 + 1 3 \* + 14 /

![](../../.gitbook/assets/image%20%2811%29.png)



![](../../.gitbook/assets/image%20%28134%29.png)

如何将中缀表达式转换成后缀表达式?



* 按运算符优先级对所有运算符和它的运算数加括号。\(原本的括号不用加\)
* 把运算符移到对应的括号后。
* 去掉括号。

## 3-递归

> 要理解递归，你要先理解递归，直到你能理解递归。   
> 如果在一个函数、过程或数据结构的定义中又应用了它自身，那么这个函数、过程或数据结构称为 是递归定义的，简称递归。  
> 递归最重要的是递归式和递归边界。



