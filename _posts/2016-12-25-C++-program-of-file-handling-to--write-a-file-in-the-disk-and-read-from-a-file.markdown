---
title: C++ program of file handling to write a file in the disk and read from a file
date: 2016-12-25 07:34:47 Z
layout: post
permalink: cplus-file-handling/
category:
- c++ program
comments: true
---

{% highlight c++ %}
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
