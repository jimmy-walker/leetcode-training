Use lists unless you want some very specific features that are in the C array libraries.

J用python中的list来处理编程中array的问题。

python really has four primitive data structures.

```python
tuple = ('a','a','c') #tuple是可以重复的。
list = ['a','b','c'] #list可以通过索引查找数值，但是不能对整个列表进行数值运算,np.array是数组，也可以通过索引值查找数据，但是能对整个数组进行数值运算。
dict = {'a':1, 'b': true, 'c': "name"} #dict的key不能重复。
s = set(['A', 'B', 'C']) #set就像是把Dict中的key抽出来了一样，类似于一个List，但是内容又不能重复，通过调用set()方法创建，创建方式与其他三种有所不同。
```

besides that there exists string： 

```python
str = “Hello My friend” #字符串（即不能修改的字符list）
```
