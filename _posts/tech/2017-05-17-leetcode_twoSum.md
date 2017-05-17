---
layout: post
title: leetcode_twoSum
category: 技术
tags: centos,ftp,Apache,GPL,leetcode_twoSum
description: 
---

leetcode_twoSum

```javascript

int* twoSum(int* nums,int numSize,int target)
{
int *a = (int *)malloc(2*sizeof(int));
for (int i = 0;i < numSize;i ++)
{
for (int j = i + 1;j<numSize && j != i ;j++)
{
if(nums[i] + nums[j] == target)
{
a[0] = i;
a[1] = j;
}
}

}
return a;
}


int* twoSum1(int* nums,int numSize,int target)
{
int min = 2147483647;
int i = 0;
for (i = 0;i < numSize;i ++)
{
if (nums[i] < min)
{
min = nums[i];
}
}

int max = target - min;
int len = max - min + 1;
int *table = (int *)malloc(len*sizeof(int));
int *indice = (int *)malloc(2*sizeof(int));
for (int i = 0;i < len;i++)
{
table[i] = -1;
}

for (int i = 0;i < numSize; i ++)
{
if (nums[i]-min < len)
{
if (table[target-nums[i]-min] != -1)
{
indice[0] = table[target - nums[i] - min];
indice[1] = i;
return indice;
}
table[nums[i] - min] = i;
}
}
free(table);
return indice;
}


```

---


<script language="javascript" type="text/javascript" src="//js.users.51.la/19176892.js"></script>
<noscript><a href="//www.51.la/?19176892" target="_blank"><img alt="&#x6211;&#x8981;&#x5566;&#x514D;&#x8D39;&#x7EDF;&#x8BA1;" src="//img.users.51.la/19176892.asp" style="border:none" /></a></noscript>

