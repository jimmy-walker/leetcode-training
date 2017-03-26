Use lists unless you want some very specific features that are in the C array libraries.

J用python中的list来处理编程中array的问题。

python really has four primitive data structures.元祖，列表，字典，集合。

```python
tuple = ('a','a','c') #tuple元祖是可以重复的。
list = ['a','b','c'] #list列表可以通过索引查找数值，但是不能对整个列表进行数值运算,np.array是数组，也可以通过索引值查找数据，但是能对整个数组进行数值运算。
dict = {'a':1, 'b': true, 'c': "name"} #dict字典的key不能重复。
s = set(['A', 'B', 'C']) #set集合，是无序的，内容不能重复，可以利用.remove(key)形式删除元素。
#通过调用set()方法创建，创建方式与其他三种有所不同。注意必须是iterator才能创建，比如set([1])可以,set(1)就不可以。 
```

besides that there exists string：

```python
str = “Hello My friend” #字符串（即不能修改的字符list）
```

