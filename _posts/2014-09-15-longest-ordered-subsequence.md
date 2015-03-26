---
layout: post
title: "最长升序序列"
description: ""
category: 笔试题
tags: [算法]
---
{% include JB/setup %}
# 最长升序序列
---


	
* **题目描述**

	**网易有道笔试题：**<叠罗汉><br>
	描述：输入的为每个人的（体重，身高），在上面的人必须比下面的人体重小，身高低，问最多能叠多少个罗汉。<br>
	例如：输入(60,165),(78,175),(65,171),(70,178)<br>
	输出：3<br>
	**分析**<br>
	**a.** 先按照身高（或者体重排序）<br>
	【(60,165),(65,171),(78,175),(70,178)】<br>
	**b.** 然后将体重单独取出放到数组中去<br>
	【60,65,78,70】<br>
	**c.** 能够叠罗汉的最多人数就是这个数组的最长升序序列。求最长升序序列可以用以下两种方法：<br>
	**一、动态规划**,复杂度为O(n^2)<br>
	设d[i]表示以a[i]结尾的最长升序子序列的长度，则可以得到状态转移方程为d[i]=max{1,max{d[j]}+1}，其中j=0,1,2,...i-1并且a[j]<a[i]。用一句话概括思路就是每次计算d[i]时，就要扫描数组a中前i-1个元素，如果遇到a[j]>a[i]则跳过a[j]继续扫描j...i-1的元素，否则如果a[j]<a[i]则用以a[j]为结尾的子序列长度+1就是以a[j]为倒数第二个元素，a[i]为倒数第一个元素的最长子序列长度。<br>
	<!--break-->
	**二、栈+二分查找**,复杂度为O(nlgn)<br>
	这种方法很直观，顺次扫描数组，如果a[i]大于栈顶的元素则入栈，否则在栈中找到第一个（最下面那个）大于a[i]的元素temp并用a[i]替换temp。如
	1 7 3 5 9 4 8
	栈为1 7 的时候，输入3，则要替换7变为1 3，然后输入5大于栈顶的3，直接入栈变为1 3 5=>1 3 5 9=>1 3 4 9=>1 3 4 8。最后的top就是最长升序子序列的长度。<br>

	代码：<br>
	`package test;

	import java.util.Stack;
	
	public class LongestOrderedSubsequence {
	
		static Integer a[] = {60,65,78,70};
		static Integer dp[];
		static Stack<Integer> stack = new Stack<Integer>();
	
		// 动态规划
		public static int maxByDP() {
			int n = a.length;
			int i, j, max;
			dp = new Integer[n];
			for (i = 0; i < n; i++)
				dp[i] = 1;
			for (i = 1; i < n; i++) {
				max = -1;
				// j从0开始
				for (j = 0; j < i; j++) {
					if (a[j] >= a[i])
						continue;
					max = (dp[j] > max) ? dp[j] : max;
					dp[i] = (max + 1 > 1) ? max + 1 : 1;
				}
			}
			max = -1;
			for (i = 0; i < n; i++)
				max = (dp[i] > max) ? dp[i] : max;
			return max;
		}
	
		// 栈+二分查找
		public static int maxByStack() {
			int n = a.length;
			int  i, l, m, r;
			stack.push(a[0]);
			for (i = 1; i < n; i++) {
				if (a[i] > stack.peek())
					stack.push(a[i]);
				else {
					l = 0;
					r = stack.size();
					while (l <= r) // 二分查找
					{
						m = (l + r) >> 1;
						if (stack.elementAt(m) < a[i])
							l = m + 1;
						else
							r = m - 1;
					}
					stack.setElementAt(a[i], l);
				}
			}
			return stack.size();
		}
	
		public static void main(String[] args) {
			System.out.println("通过动态规划计算的结果为：" + maxByDP());
			System.out.println("通过栈+二分查找计算的结果为：" + maxByStack());
		}
	
	}
`
	
	
	




 


