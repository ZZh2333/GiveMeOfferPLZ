# 7-13 17:31
巨人网络提前批，提前批可选2个工作岗位，投递结果不影响秋招  
投递平台：牛客网  
无内推  
投递岗位：  
+ 游戏开发工程师
+ 游戏测试开发工程师  

进度查看：微信公众号 牛客招聘助手   

# 7-25 18：00
收到笔试通知，笔试平台：牛客网。  
笔试时间：7-26 19：00  

# 7-26 22：00 笔试题回溯
笔试完了，凉凉  
题型：
+ 20道不定向选择题
+ 2道编程题
+ 2道简答题

 ## 选择题（部分）
1. 赋值语句是否合法：  
> n1 = (n2 = (n3 = 0));  
> 经过编译器测试是合法的，n1值为0
2. 进程间同步方法
> 1. 信号量机制  
> &emsp;&emsp;对信号量使用P和V操作，P将信号量值减一，V将信号量值加一。  
> 当信号量值S大于0时，表示当前可用资源数量；当S小于0时，表示当前正在等待该资源的进程数。  
> 2. 自旋锁管程
> 3. 会合
> 4. 分布式系统
3. C++中不能被重载的运算符 
> c++中不能重载的运算符有5个：“?:”、“.”、“::”、“sizeof”、“ .* ” 。   
> “.”和“::”运算符如果重载，可能会出现混淆；  
> “sizeof”运算符不能重载是因为内部许多指针都依赖它；  
> “ .* ”运算符引用指向类成员的指针。  
4. C++模板类型
5. **C++11**中的关键字
> 1. decltype：自动推导参数的类型。  
> &emsp;&emsp;与auto不同在于，decltype可以推导数组类型，而auto不能；decltype可以进行函数传参，而auto不行。 
> 2. nullptr：空指针。  
> 3. constexpr：常量表达式。  
> &emsp;&emsp;constexpr与const的区别：在不同的使用场景下，const具有不同的意义，不过大多数情况下，const描述的时“运行时常量性”，即在运行时数据具有不可更改性；constexpr是比const更加严格的约束，它修饰的表达式除了具有“运行时常量性”，也具有“编译时常量性”，即constexpr修饰的表达式在编译期间可知。  
> 4. explicit：标明类的构造函数是显示的，不能进行隐式转换。    

6. 下列代码运行的结果
```C++
#include<iostream>
using namespace std;

class A {
public:
	virtual void a() = 0;
	A() {
		cout << "A";
	}
};

class B :public A {
public:
	B() {
		cout << "B";
	}
};

int main() {
	B b;
}
```
>编译器报错  
![巨人网络2022-07-26-22-19-18](https://raw.githubusercontent.com/ZZh2333/picgoResource/main/img/%E5%B7%A8%E4%BA%BA%E7%BD%91%E7%BB%9C2022-07-26-22-19-18.png)  

7. 友元函数能否访问私有成员
> 友元函数可以访问类的私有成员，也能访问其保护成员。  
8. 设计模式问题
9.  C++中不带修饰词的函数默认为什么
> 类class中默认为 **private**  
> 结构体struct中默认为 **public**  
10. 下列代码运行的结果
```C++
#include<iostream>
using namespace std;

int main() {
	int a = 0, x = 0;
	x = (a++)++;
	cout << x;
}
```
> 编译器报错  
> ![巨人网络2022-07-26-22-26-38](https://raw.githubusercontent.com/ZZh2333/picgoResource/main/img/%E5%B7%A8%E4%BA%BA%E7%BD%91%E7%BB%9C2022-07-26-22-26-38.png)  
11. 单例类和静态类的区别

12. 构造函数和析构函数能否为虚函数
> &emsp;&emsp;构造函数不需要也不允许是虚函数。如果构造函数是虚函数，就需要通过虚表指针来调用，可是对象还没有被实例化出来，也就是内存空间还问分配，故没有虚表指针和虚表。  
> &emsp;&emsp;析构函数可以是虚函数。将可能会被继承的父类的析构函数设定为虚函数，可以保证当我们new一个子类，然后使用基类指针指向子类对象，释放基类指针可以释放掉子类的空间，避免内存泄露。  
> &emsp;&emsp;C++默认的析构函数不是虚函数，是因为对于不会被继承的类不需要开辟额外的空间存放虚表和虚表指针。  
> &emsp;&emsp;析构函数不能被重载。
13. 右值引用
## 编程题
1. 在游玩游戏时，有十个任务，输入为任务消耗的时间，如`times[10] = [3,2,4,2,2,5,1,6,4,7]`，任务所得经验分别为`exp[10] = [10,80,101,60,30,120,50,40,70,90]`，现有规定时间`limit_time = 23`，输出规定时间能够获得的最大经验值（531）。
2. 现有若干文件以及其所占存储空间和依赖，求所占存储空间最大的文件编号和其所占空间。  
第一个输入为文件数目，如5。  
依次输入文件编号、空间、依赖
```bash
5
# 文件编号，存储空间，所需依赖
1000,2
1001,3
1002,5,1000,1001
1010,7
1020,2,1010
# 输出：1002，10
```
个人解答（由于笔试时没有做出来，笔试完后补的，用例通过情况还未知）：
```C++
#include<iostream>
#include<unordered_map>
using namespace std;

int main() {
	int cinNum;
	cin >> cinNum;
	unordered_map<int, int> cache;
	int maxIndex = 0, maxCache = 0;
	for (int i = 0; i < cinNum; i++) {
		string s;
		cin >> s;
		int currentNum = 0, dotCnt = 0, cacheIndex = 0, cachesize = 0;
		for (char n : s) {
			if (n >= '0' && n <= '9') {
				currentNum = currentNum * 10 + (n - '0');
			}
			else {
				dotCnt++;
				if (dotCnt == 1) {
					cacheIndex = currentNum;
					currentNum = 0;

				}
				else if (dotCnt == 2) {
					cachesize = currentNum;
					currentNum = 0;

				}
				else {
					cachesize += cache[currentNum];
					currentNum = 0;

				}
			}
		}
		if (dotCnt == 1) {
			cachesize = currentNum;
		}
		else if (dotCnt > 1) {
			cachesize += cache[currentNum];
		}
		cache[cacheIndex] = cachesize;
		if (cachesize > maxCache) {
			maxCache = cache[cacheIndex];
			maxIndex = cacheIndex;
		}
	}
	cout << maxIndex << "," << cache[maxIndex] << endl;
}
```
## 简答题
1. 五选一作答，内含游戏算法（游戏AI设计）、操作系统（进程、线程管理）、计算机图形学等，实在没时间做了，而且都很难，也不会。  
2. 什么是内存对齐？为什么要内存对齐？对齐原则？
> **对齐原因**：  
> &emsp;&emsp;计算机从内存中取数据是按照一个固定长度进行的，如在32位机器上，CPU每次都是取32bit数据的，也就是4个字节；若不进行内存对齐，当需要的数据要从两块地址中取出并进行掩码和移位操作时效率很低。内存对齐一方面可以节省内存，一方面提升数据读取的性能。  
> ***
> **对齐原则**：  
> - 结构体变量的首地址能够被其最宽的基本类型成员的对齐值所整除 
> - 结构体内每一个成员相对于起始位置的偏移量能够被该变量的大小整除
> - 结构体总体大小能够被最宽成员大小整除  
> ***
> **如何对齐**：  
> &emsp;&emsp;声明数据结构时，字节对齐的数据依次声明  
> &emsp;&emsp;小成员组合在一起，能节省内存空间  
> &emsp;&emsp;不要把小成员参杂声明在字节对齐的数据之间  
> ***