---
title: C++ program of transfering balance from one account to another
date: 2018-07-20 11:13:47 Z
permalink: cplus-balance-transfer/
category:
- c++ program
layout: post
comments: true
---

{% highlight ruby %}

/******************************************************************************

Author Madhav Paudel
C++ program of transfering balance from one account to another. Account consists
of name, accno and balance

*******************************************************************************/

#include <iostream>
#include<iomanip>
using namespace std;
class Account
{
	string name;
	long int accno;
	long int balance;
	
	public:
	Account()
	{
	    name = "";
	    accno = 0;
	    balance = 0;
	};
	Account(string name, long int accno,long int balance)
	{
	    name = name;
	    accno = accno;
	    balance = balance;
	};
	void setData()
	{
		cout<<"Enter name : ";
		getline (cin, name);
		cout<<"Enter account number : ";
		cin>>accno;
		cout<<"Enter balance : ";
		cin>>balance;
	};
	void display()
	{
		cout<<setw(20)<<name<<setw(15)<<accno<<setw(15)<<balance
			<<endl;
	};
	Account transferBalance(Account A2, long int tbalance)
	{
	    if (balance > tbalance)
	    {
	        balance -= tbalance;
	        A2.balance += tbalance;
	    }
	    else
	    {
	        cout<<endl
	            <<"Sorry! Transfer failed! Reason: Insufficient Balance."
	            <<endl;
	    }
	    return A2;
	};
};

int main()
{
	Account A1, A2;
	long int tbalance;
	cout<<"Enter Details of transfering Account(Account 1)\n";
	A1.setData();
	cout<<endl
	    <<"Enter Details of receiving Account(Account 2)\n";
	cin.ignore(); A2.setData();
	cout<<endl
	    <<"Enter total amount which you want to transfer from Account 1 to Account 2: ";
	cin>>tbalance;
	A2 = A1.transferBalance(A2, tbalance);
	cout<<endl;
	cout<<setw(29)<<"Name"<<setw(15)<<"Accno"<<setw(15)<<"Balance"<<endl;
	cout<<"Account 1";A1.display();
	cout<<"Account 2";A2.display();
	return 0;	
}

{% endhighlight %}
