# Python 語法和概念筆記

## 索引

- [split()+join()](#split()+join())
- [subtring](#substring)
- [索引迭代](#索引迭代)
- [enumerate](#enumerate)
- [.strip()](#.strip())
---

## `split()+join()` (字串組合技)

**用途：** 幫所有的字串先斷詞，再加上連接符號

**語法：** 
    ```python
        a = a.split(' ')
        a = '-'.join(a)
    ```

**範例：**
```python
def split_and_join(line):
    line  = line.split(' ')
    line = '-'.join(line)
    return line
if __name__ == '__main__':
    line = input()
    result = split_and_join(line)
    print(result)

```

**常見用法：** 字串處理

---

## `subtring` (子字串）

**定義：** 字串裡「連續」的部分

**範例：**
'hello'這個字中，
 - 'he' is substring
 - 'llo' is substring
 - 'ho' is not substring

**常見用法：** 字串處理

---
## `索引迭代` 

**定義：** 透過i, list[i]的特性對應位置與字元

**範例：**
```python
# 直接迭代元素
s = 'amelie'
for i in s:
    print(i) # 結果：a m e l i e
# 索引迭代
s = 'amelie'
for i in len(s):
    print(s[i]) # 結果：a m e l i e
```

**常見用法：** 字串處理、資料結構裡的滑動視窗＆雙指針處理方法都是透過索引的方式處理。

---

## `enumerate()` 

**定義：** 內建函數，用來同時迭代獲得索引和值

**範例：**
```python
# 直接迭代元素
s = 'amelie'
for index. value in enumerate(s):
    print(index, value) 
# 結果：0 a
# 1 m
# 2 e
# 3 l
# 4 i
# 5 e
```

**常見用法：** 同時想列印出索引和值的時候

---

## `.strip()` 

**定義：** 去掉字串前後全部的空字符，就是 excel 中的 trim()

**範例：**
```python
s = ' amelie '
a = s.strip()
# 結果：'amelie'
```

**常見用法：** 字串清理時