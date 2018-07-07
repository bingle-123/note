# 如何去重列表中的元素 #

## 用集合 ## 

**list(set(1))**

## 用字典 ##
```
l1 = ['b','c','d','c','a','a']

l2 = dict.fromkeys(l1,'字符串')

l3 = dict.fromkeys(l1)

l4 = {}.fromkeys(l1)

l5 = {}.fromkeys(l1).keys()

print(l2)
print(l3)
print(l4)
print(l5)
> {'b': '字符串', 'c': '字符串', 'd': '字符串', 'a': '字符串'}
> {'b': None, 'c': None, 'd': None, 'a': None}
> {'b': None, 'c': None, 'd': None, 'a': None}
> dict_keys(['b', 'c', 'd', 'a'])

```
## 用字典并保持顺序 ##
```
l1 = ['b','c','d','b','c','a','a']

l2 = list(set(l1))

l2.sort(key=l1.index)

print (l2)

> ['b', 'c', 'd', 'a']

```

## 列表推导式 ##

```
l1 = ['b','c','d','b','c','a','a']
l2 = []
[l2.append(i) for i in l1 if not i in l2]

print(l2)

> ['b', 'c', 'd', 'a']

```

## sorted排序并且用列表推导式 ##

```
l = ['b','c','d','b','c','a','a']

single = []

[single.append(i) for i in sorted(l) if i not in single]

print (single)

> ['a', 'b', 'c', 'd']

```
## list=[2,3,5,4,9,6]，从小到大排序，不许用sort，输出[2,3,4,5,6,9] ##

```
list = [2,3,5,9,6]

new_list = []

def get_min(list):
    # 获取列表最小值
    a = min(list)
    # 删除最小值
    list.remove(a)
    # 将最小值加入新列表中
    new_list.append(a)
    # 保证最后里面有值，递归调用获取最小值
    # 直到所有值获取完，并加入新列表中返回
    if len(list)>0:
        get_min(list)
    return new_list
    
new_list= get_min(list)
print(new_list)
```
