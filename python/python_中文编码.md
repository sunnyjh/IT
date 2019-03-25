## python2 decode和encode原理

   Python2默认代码编码格式为ASCII码，正常情况下，Python2处理思路为默认先decode ASCII字符为unicode,然后再进行各种操作，最后encode为ASCII字符输出，这些都是隐式的。但是当代码中出现非ASCII字符时，由于无法对非ASCII进行decode，会报Non-ASCII错误。一般会出现如下三种常见的编码问题：

## 问题

错误1：
![](python2_chinese_encode_error1.png)


错误2：
![](python2_chinese_encode_error2.png)

## 2.

## 2.1 
str
unicode
http://python.jobbole.com/80831/
http://www.wklken.me/posts/2013/08/31/python-extra-coding-intro.html
