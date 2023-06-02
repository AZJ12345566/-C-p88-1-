# -C-p88-1-
C语言学习笔记  p88 函数（1）
//以下几个问题
//1.函数是什么
//2.库函数
//3.自定义函数
//4.函数参数
//5.函数调用
//6.函数的嵌套调用和访问访问
//7.函数的声明和定义
//8.函数递归(重点)

//函数在程序中具有相对独立性
//函数具有参数，有返回值
#include<stdio.h>
#include<string.h>
int Add(int x,int y)
{
    int z=0;
    z=x+y;
    return z;
}
int main()
{
    int a=10;
    int b=20;
    int sum=Add(a,b);
    printf("%d\n",sum);
    return 0;
}

//函数分为两类：1.库函数 2.自定义函数

//常见的库函数：
1.IO函数
2.字符串操作函数
3.字符操作函数
4.内存操作函数
5.时间/日期函数
6.数字函数
7.其它库函数

//库函数
int main()
{
    //strlen-string length-字符串长度有关
    //strcpy-string copy-字符串拷贝
    //char* strcpy(char* destination, const char* source);格式
    char arr1[]="bit";
    char arr2[20]="#########";
    strcpy(arr2,arr1);
    printf("%s\n",arr2);//注：这里的\0也要拷贝进入arr2
    return 0;
}

int main()
{
    //void* memset(void* ptr,int value,size_t num);  人话：将ptr指向的前num个字节的内容设置成指定的value这个值
    char arr[]="hello world";
    memset(arr,'*',5);
    printf("%s\n",arr);
    //输出值为：***** world
    //注：ptr的长度必须要比num大
    return 0;
}

//文档网站：    www.cplusplus.com
//c和c++的官网：http://en.cppreference.com

//自定义函数
需要程序员自己定义函数名，返回类型，函数参数

get_max(int x,int y)
{
    if(x>y)
        return x;
    else
        return y;
}
int main()
{
    int a=10;
    int b=20;
    int max=get max(a,b);
    printf("max=%d\n",max);
    max=get_max(100,300);
    printf("max=%d\n",max);
    return 0;
}

void Swap(int x,int y)
{
    int tmp=0;
    tmp=x;
    x=y;
    y=tmp;
}
int main()
{
    int a=10;
    int b=20;
    int tmp=0;
    //
    printf("a=%d,b=%d\n",a,b);
    Swap1(a,b);
    printf("a=%d,b=%d\n",a,b);
    return 0;
}//注：这里的a，b和x，y半毛钱关系没有，所以输出换不过来

int main()
{
    int a=0;
    int* pa=&a;//pa为指针变量
    *pa=20;//解引用操作
    printrf("%d\n",a);
    return 0;
}
//所以互换值的函数应该如下
void Swap2(int* pa, int* pb)
{
    int tmp=0;
    tmp=*pa;
    *pa=*pb;
    *pb=tmp;
}
int main()
{
    int a=10;
    int b=20;
    printf("a=%d b=%d\n",a,b);
    Swap2(&a,&b);
    printf("a=%d b=%d\n",a,b);
    return 0;
}
//当实参传给形参的时候，形参其实是形参的临时拷贝，对形参的修改是不会改变实参的

//实际参数：真实传给函数的参数，叫实参，实参可以是常量，变量，表达式，函数等。无论实参是那种类型的值，在进行函数调用时，他们都必须有确定的值，以便把值传给形参
//max=get_max(100,300+1);  300+1这个表达式可以当实参用，因为他也是确切的值
//形式参数：形式上的参数，没有实际的变量空间，在函数的调用才实例化


//函数的调用：
//1.传值调用，2.传址调用
//Swap1函数就是典型的传值调用
//传址调用：1.传址调用是把函数外部创建的变量的内存地址传递给函数参数的一种调用函数的方式。
//        2.这种传参方式可以让函数和函数外边的变量建立起真正的联系，也就是函数内部可以直接操作函数外部的变量
          
//这个函数要改变外部的某些变量的时候，就要考虑要传址过去了，如果仅仅要一个值，则直接传值就可以

//是素数返回1，不是素数返回0
void is_prime(int n)
{
    int j=0;
    for(j=2;j<n;j++)
    {
        if(n%j==0)//将2-j的数全部整除一遍
            return 0;
    }
    return 1;
}

int main()
{
    int i=0;
    for(i=100;i<=200;i++)
    {
        //判断i是否为素数
        if(is_prime(i)==1)//这个函数是专门判断一个数是否为素数
            printf("%d",i);
    }
    return 0;
}
