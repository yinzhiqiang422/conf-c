conf-c
======

基于C语言的轻量级读取/创建配置文件的函数库

简介
====

conf-c是使用c语言开发的读取/创建配置文件的函数库，它的参数数据结构为
CONF_VALUE *
CONF_VALUE结构有两个参数，一个键key和一个字符数组value
key为键，value为参数，其中value[0]为第一个参数，value[1]为第二个参数(如果有的话)

读取的配置文件为键/多值参数对并将其放入一个散列表里，再通过使用conf_value_get函数得到一个CONF_VALUE的键/多参数对，具体的使用方法请看两个示例文件.

配置文件的格式为

key = arg1,arg2,arg3,...

并以#字开头为注释行

如若想在参数中添加特殊符号如' " ,空白符以及#等可以使用成对出现的'或者"

比如：
key=1234 5678
这是一个错误的参数格式
正确的格式应为
key='1234 5678'
或
key="1234 5678"
当参数中有"时使用'当参数中有'时则使用"
在没有使用'或者"包裹的参数行中逗号,表示多个参数的分隔符,即

key=1234,5678
则value[0]为1234 value[1]为5678 (CONF_VALUE结构)

*使用gcc编译时需要使用-lconf参数

安装
====

make
make install (需要root权限)

卸载
====

make uninstall (需要root权限)
