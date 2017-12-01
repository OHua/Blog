# 使我感到詭異的Comprehension in Python
這幾天就為了把兩行的程式碼想說改寫成精幹一點的一行搞定，於是一頭栽入了 Python 的 Comprehension，一開始對於語言的美麗感到興奮有趣，隨後慢慢就不這麼想了...

## coding途中記錄下來的五種範例
```python
>>> Aset = ['a','b','c','d','e']
>>> Bset = ['a','b','x','y','z']
>>> [ item for item in Aset if item not in Bset ]
['c','d','e']
```

```python
>>> Aset = ['a','b','c','d','e']
>>> Bset = ['a','b','x','y','z']
>>> [ item+':True' if item in Aset else item+':False' for item in Bset ]
['a:True', 'b:True', 'x:False', 'y:False', 'z:False']
```

```python
>>> Aset = ['a','b','c','d','e']
>>> Bset = ['a','b','x','y','z']
>>> print( item+':True' if item in Aset else item+':False' for item in Bset )
<generator object <genexpr>>> at 0x0000027202AB1990>>>
>>> print( [ item+':True' if item in Aset else item+':False' for item in Bset ] )
['a:True', 'b:True', 'x:False', 'y:False', 'z:False']
```

```python
>>> Aset = ['a','b','c','d','e']
>>> Bset = ['a','b','x','y','z']
>>> [ item+':True' if item in Aset for item in Bset ]
SyntaxError: invalid syntax
```

```python
>>> Aset = ['a','b','c','d','e']
>>> Bset = ['a','b','x','y','z']
>>> [ item+':True' for item in Bset if item in Aset ]
['a:True', 'b:True']
```

## 結論
* 挺方便的，「概念簡單」的程式碼可以直接寫成一行完成
* 懂 Comprehension 就好，不需要刻意去使用它，它不適合用在複雜的結構中且不易讀
* 若是 for if 內要執行的事情有2個步驟以上，則不適用 Comprehension
