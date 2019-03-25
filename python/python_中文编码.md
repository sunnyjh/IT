## python2 decode和encode原理

   Python2默认代码编码格式为ASCII码，正常情况下，Python2处理思路为默认先decode ASCII字符为unicode,然后再进行各种操作，最后encode为ASCII字符输出，这些都是隐式的。但是当代码中出现非ASCII字符时，由于无法对非ASCII进行decode，会报Non-ASCII错误。一般会出现如下三种常见的编码问题：

## 问题

### 1、SyntaxError: Non-ASCII character
这种异常最不容易出现，也最容易处理，主要原因是Python源码文件中有非ASCII字符，而且同时没有声明源码编码格式，例如：

    Python
    s = '中文'
    print s     # 抛出异常

### 2、UnicodeDecodeError
这个异常有时候会在调用decode方法时出现，原因是Python打算将其他编码的字符转化为Unicode编码，但是字符本身的编码格式和decode方法传入的编码格式不一致，例如：
    
    Python

    #!/usr/bin/python
    # -*- coding: utf-8 -*-
    s = '中文'
    s.decode('gb2312') # UnicodeDecodeError: 'gb2312' codec can't decode bytes in position 2-3: illegal multibyte sequence
    print s

上面这段代码中字符串s的编码格式是utf-8，但是在使用decode方法转化为Unicode编码时传入的参数是‘gb2312’，因此在转化的时候抛出UnicodeDecodeError异常。还有一种情况是在encode的时候：
   
    Python

    #!/usr/bin/python
    # -*- coding: utf-8 -*-
    s = '中文'
    s.encode('gb2312') # UnicodeDecodeError: 'ascii' codec can't decode byte 0xe4 in position 0: ordinal not in range(128)
    print s

### 3、UnicodeEncodeError
错误的使用decode和encode方法会出现这种异常，比如：使用decode方法将Unicode字符串转化的时候：

    Python

    #!/usr/bin/python
    # -*- coding: utf-8 -*-
    s = u'中文'
    s.decode('utf-8') # UnicodeEncodeError: 'ascii' codec can't encode characters in position 0-1: ordinal not in range(128)
    print s

当然，除了上面列出的几种出现异常的情况之外还有很多可能出现异常的例子，这里就不在一一说明了。

## 解决方法

对于以上的几个异常，有以下几个处理的方法和原则。

### 1、遵循PEP0263原则，声明编码格式

在PEP0263 — Defining Python Source Code Encodings中提出了对Python编码问题的最基本的解决方法：在Python源码文件中声明编码格式，最常见的声明方式如下：

    Python

    #!/usr/bin/python
    # -*- coding: <encoding name> -*-
 
其中<encoding name>是代码所需要的编码格式，它可以是任意一种Python支持的格式，一般都会使用utf-8的编码格式。**这种方法能解决上述的问题一。**

### 2、使用u’中文’替代’中文’

    Python

    str1 = '中文编码'
    str2 = u'中文编码'

Python中有以上两种声明字符串变量的方式，它们的主要区别是编码格式的不同，其中，str1的编码格式和Python文件声明的编码格式一致，而str2的编码格式则是Unicode。如果你要声明的字符串变量中存在非ASCII的字符，那么最好使用str2的声明格式，这样你就可以不需要执行decode，直接对字符串进行操作，可以避免一些出现异常的情况。

### 3、Reset默认编码

Python中出现这么多编码问题的根本原因是Python 2.x的默认编码格式是ASCII，所以你也可以通过以下的方式修改默认的编码格式：

    Python

    import sys
    sys.setdefaultencoding('utf-8')

这种方法是可以解决部分编码问题，但是同时也会引入很多其他问题，得不偿失，不建议使用这种方式。

### 4、终极原则：decode early, unicode everywhere, encode late

    最后分享一个终极原则：decode early, unicode everywhere, encode late，即：在输入或者声明字符串的时候，尽早地使用decode方法将字符串转化成unicode编码格式；然后在程序内使用字符串的时候统一使用unicode格式进行处理，比如字符串拼接、字符串替换、获取字符串的长度等操作；最后，在输出字符串的时候（控制台/网页/文件），通过encode方法将字符串转化为你所想要的编码格式，比如utf-8等。

按照这个原则处理Python的字符串，基本上可以解决所有的编码问题（只要你的代码和Python环境没有问题）。。。

### 5、升级Python 2.x到3.x

最后一个方法，升级Python 2.x，使用Python 3.x版本。。这样说主要是为了吐槽Python 2.x的编码设计问题。当然，升级到Python 3.x肯定可以解决大部分因为编码产生的异常问题。毕竟Python 3.x版本对字符串这部分还是做了相当大的改进的，具体的下面会说。。。。

    Python 3.x中的Unicode

    在Python 3.0之后的版本中，所有的字符串都是使用Unicode编码的字符串序列，同时还有以下几个改进：

    1、默认编码格式改为unicode
    2、所有的Python内置模块都支持unicode
    3、不再支持u’中文’的语法格式
所以，对于Python 3.x来说，编码问题已经不再是个大的问题，基本上很少遇到上述的几个异常。关于Python 2.x str&unicode和Python 3.x str&bytes的更多说明和对比，大家可以看一下：Python中字符编码的总结和对比


## 参考链接
http://python.jobbole.com/80831/
http://www.wklken.me/posts/2013/08/31/python-extra-coding-intro.html
[Python中字符编码的总结和对比](https://www.crifan.com/summary_python_string_encoding_decoding_difference_and_comparation_python_2_x_str_unicode_vs_python_3_x_bytes_str/)
