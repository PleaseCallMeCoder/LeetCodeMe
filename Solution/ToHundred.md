# 问题描述

有1-9九个数,现向九个数中间加入+号-号,使得最后的运算结果等于100,请求出所有可能解.

# 解决方案 1

* 求所有可能解,即遍历所有情况,判断是否是解.
* 题目要求:向1-9中插入符号,有8个空位,每个空位有'+','-','',三种情况,最后所有可能情况为3^8=6561种
* 直接按照循环嵌套的写法需要八层循环才能完成所有遍历,这里可以引入进制的概念,取3进制,八位三进制数可以表示所有情况.

# 代码示例
	
	
		String[] mark= new String[]{"+","+-",""};
		
		for(int i=0;i<3*3*3*3*3*3*3*3;i++){
			int num=i;
			int sum=0;
			String shi="1";
			for(int j=2;j<10;j++){
				shi=shi+mark[num%3]+j;
				num = num/3;
			}
			String[] split = shi.split("\\+");
			for (int s = 0; s < split.length; s++) {
				sum = sum + new Integer(split[s]);
			}
			if(sum==100){
				System.out.println(shi.replace("+-", "-")+"=100");
			}
			
		}
