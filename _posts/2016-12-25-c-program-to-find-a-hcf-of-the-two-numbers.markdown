---
title: C program to find the HCF of the two numbers
date: 2016-12-25 07:34:47 Z
permalink: c-program-hcf/
category:
- c program
layout: post
comments: true
---

{% highlight c linenos %}
#include<stdio.h>
#include<conio.h>
int hcfactor(int x,int y)
{
	if(y==0)
	return x;
	else
	return hcfactor(y,x%y);
}
void main()
{
	int a,b,f;
	printf("Enter two numbers:\n");
	scanf("%d%d",&a,&b);
	f=hcfactor(a,b);
	printf("HCF of %d and %d is %d.",a,b,f);
	getch();
}
{% endhighlight %}

