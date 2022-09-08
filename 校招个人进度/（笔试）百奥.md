# 7-26 14:33
百奥游戏秋招，可投递一个岗位  
投递平台：自家平台  
无内推  
投递岗位：  
+ 游戏开发工程师  

进度查询：[百奥游戏](https://app.mokahr.com/campus_apply/aobi/25016#/candidateHome/applications)

# 8-8 11:45
邮件通知：
> 您好，您的简历已经通过百奥家庭互动有限公司初步筛选，笔试将在9月初安排，请留意后续邮件通知和关注【百奥招聘】公众号，了解更多关于校招的问题和详情 。

# 8-26 18：13
邮件通知笔试时间：9月2日。

# 9-2 18：00 笔试回溯
4道编程题，整体都很简单  
## 1
第一题是return a+b供环境测试用的（白给的第一题）  
## 2
第二题是一个数组[0110011]每次只能从下标i往后全部取反（1->0,0->1），求多少次能全0  
> 0110011   
> 0001100  
> 0000011  
> 0000000  
> 输出：3

思路就是先找到第一个1（如果没有就返回0），然后统计后面的数变化了i次，输出i+1就是结果。

## 3
> int w = 3个窗口  
> arr = [20，5，10，20，5，5]表示若干人需要办理业务的时间  
> 输出string s = "123233"表示这若干人在哪个窗口办理

思路：用的unordered_map<int index,int sum>记录每个窗口的时间  
遍历arr去unordered_map中找sum最小的index加到string s中。

# 4
> &emsp;&emsp;&emsp;&emsp;1  
> &emsp;&emsp;&emsp;4&emsp;&emsp;2  
> &emsp;&emsp;3&emsp;&emsp;6&emsp;&emsp;7  
> &emsp;2&emsp;&emsp;1&emsp;&emsp;9&emsp;&emsp;6  
> 
> 输出从上到下最小的路径和：1+4+3+1=9
本来通过回溯递归做出来了，但是因为递归函数中少了个return而报错，可惜了。

```C++
#include <bits/stdc++.h>
using namespace std;

int ans = -1;
void repeated(vector<vector<int>> arr, int i, int j, int sum) {
	if (i >= arr.size()) {
		if (ans == -1 || ans > sum) {
			ans = sum;
		}
		//漏了return所以报错，其实一开始写的return ans;报错所以删掉了return…………
		return;
	}
	sum += arr[i][j];
	//cout << i << "-" << j << endl;
	repeated(arr, i + 1, j, sum);
	repeated(arr, i + 1, j + 1, sum);
}

int solution(vector<vector<int>> arr)
{
	repeated(arr, 0, 0, 0);
	return ans;
}
```
