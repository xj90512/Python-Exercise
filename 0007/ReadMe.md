## 要点记录

## 题目

第 0007 题：有个目录，里面是你自己写过的程序，统计一下你写过多少行代码。包括空行和注释，但是要分别列出来。

> 因为各种编程语言的注释方式都不尽相同，所以本题以Python 代码文件为统计对象。

## 疑难点记录

这道题运用到了python 中的`xreadlines()`函数，需要统计总行数，空行行数，注释行行数。

总行数用`xreadlines()`函数的for 循环即可解决；空行行数也好解决：

        if file_line == '' or file_line == '\n': #空行检测

但在注释行行数上倒有麻烦，众所周知，python 中有三种注释方式（其他编程语言亦是）：
1、夹带在代码行后面的，不计算注释行行数上；2、单行注释：

	# 我是注释

单行也好解决，用re 模块的match 匹配，因为单行，直接+1

3、多行注释

这个就麻烦了，python 中多行注释如下：

	"""
	我是注释行
	"""
也许你说判断是否是`"""`就好了啊，如下面：

	file_line == "\"\"\"\n"

但是，既然说多行注释，那么固然正常应该是这样：

	"""
	我是注释行1
	我是注释行2
	我是注释行3
	我是注释行4
	....
	"""

所以，最后在http://code.activestate.com/recipes/527746-line-of-code-counter/ 上找到了答案，用的是一种很巧妙的方式
