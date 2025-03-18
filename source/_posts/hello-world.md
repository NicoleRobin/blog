---
title: Hello World
date: 2018-02-01 10:44:23
tags: 
  - code
---
C
{% codeblock hello_world.c lang:c %}
#include <stdio.h>

int main(int argc, char **argv)
{
    printf("Hello world!\n");
    return 0;
}
{% endcodeblock %}

C++ 
{% codeblock hello_world.cpp lang:cpp %}
#include <iostream>

using namespace std;
int main(int argc, char **argv)
{
    cout << "Hello world!" << endl;
    return 0;
}
{% endcodeblock %}

python
{% codeblock hello_world.py lang:python %}
print 'Hello world!'
{% endcodeblock %}

shell
{% codeblock hello_world.sh lang:shell %}
echo 'Hello world!'
{% endcodeblock %}

go
{% codeblock hello_world.go lang:go %}
package main

import "fmt"

func main() {
    fmt.Println("hello world!")
}
{% endcodeblock %}
