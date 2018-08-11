---
title: C++ program of transfering balance from one account to another
date: 2018-07-20 07:34:47 Z
layout: post
permalink: cplus-program-to-transfer-balance/
category:
- c++ program
comments: true
---

{% highlight ruby %}
#include<iostream.h>
#include<conio.h>
#include<fstream.h>
int main()
{
	int roll;
	char name[20];	
	ofstream outf("madhav.txt");	//creates a file madhav.txt
	cout<<"Enter name:";
	cin>>name;
	cout<<"Enter Roll No:";
	cin>>roll;
	outf<<"Name = "<<name;
	outf<<"\nRoll No. = "<<roll;
	outf<<endl;
	cout<<"\nData successfully written to disk.\n";
	outf.close();
	
	const int LEN = 80;
	char text[LEN];
	ifstream infile("madhav.txt");	//file is opened for read operation
	cout<<"\nThe data reading from file is:\n";
	while(infile)
	{
		infile.getline(text,LEN);
		cout<<endl<<text;
	}
	infile.close();
	
	getch();
	return 0;
}
{% endhighlight %}
