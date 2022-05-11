##包含min的函数的栈
使用归并排序的思路

**定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。**

由于需要保证时间复杂度为 O(1)，则采用 空间换时间 的方案，使用辅助栈 minSta 进行存储

* push 操作
数据栈 sta：直接 push 数值元素

辅助栈 minSta：将 数据栈 sta 中最小的元素 push 进辅助栈

* pop 操作
数据栈 sta：直接移除栈顶元素

辅助栈 minSta：判断 数据栈 sta 中刚移除的栈顶元素是否等于 辅助栈 minSta 中的栈顶元素。
如果相等，则删除 辅助栈 minSta 的栈顶元素，否则不执行操作。
目的： 为了让 辅助栈中的栈顶元素始终是数据栈中的最小值

* top 操作
数据栈 sta：返回栈顶元素

辅助栈 minSta：不执行操作

* min 操作
数据栈 sta：不执行操作

辅助栈 minSta：返回栈顶元素



	class MinStack {
	    // 创建两个栈：数据栈 sta、辅助栈 minSta
	    stack<int> Sta;
	    stack<int> minSta;
	public:
	    /** initialize your data structure here. */
	    MinStack() {
	        minSta.push(INT_MAX);
	    }
	    
	    void push(int x) {
	        Sta.push(x);
	        // ::因为题目中已经有了min函数，加::是为了调取库函数中的min函数
	        minSta.push(::min(minSta.top(), x));
	    }
	    
	    void pop() {
	        Sta.pop();
	        minSta.pop();
	    }
	    
	    int top() {
	        return Sta.top();
	    }
	    
	    int min() {
	        return minSta.top();
	    }
	};

