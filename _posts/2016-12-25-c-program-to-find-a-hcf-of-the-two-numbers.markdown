---
layout: post
title:  "C program to find a HCF of the two numbers"
date:   2016-12-25 13:19:47 +0545
categories: jekyll update
---

{% highlight ruby %}
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

