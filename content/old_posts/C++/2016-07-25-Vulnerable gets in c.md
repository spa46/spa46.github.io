+++
title = "Vulnerable gets() in C"
date = 2016-07-25
weight = 200
tags = ["secure coding"]
+++

Recently, as the growth of advanced technology, more people concern about digital system vulnerability, and the demand is continuously increasing as shown below.

![tree](/images/secureCoding/seccode01.jpg)

Particularly in C/C++, gets() has been deprecated due to security issues which can cause the program segmentation fault. For this reason, alternative functions are recommended: getdelim() or getline().


In this post, I studied what caused gets deprecated from the given code by gdb.

Following is the code:

	#include <stdio.h>

	int main() {
	    int cookie;
	    char buf[80];

	    printf("buf: %08x cookie: %08x\n", &buf, &cookie);
	    gets(buf);

	    if(cookie == 0x000a0d00)
	        printf("you win!\n");
	}

The address for cookie and buf variables:

char buf[80]: 7efff564
int  cookie:  7efff5b4

<br>

# 1. Input: 80 'a' characters
![tree](/images/secureCoding/seccode02.jpg)

<br>

# 2. input: 81 'a' characters as shown below
![tree](/images/secureCoding/seccode03.jpg)


<b>Overflow</b> occurred on buf, and the contents of cookie changed.
i.e. cookie has a value of 'a'

<br>

# 3. input: 82 'a' characters as shown below
![tree](/images/secureCoding/seccode04.jpg)

<b>Overflow</b> occurred on buf, and the contents of cookie changed.
i.e. cookie has a value of 'aa'

<br>

# 4. input: 83 'a' characters as shown below
![tree](/images/secureCoding/seccode05.jpg)

<b>Segmentation fault</b> occurred.
