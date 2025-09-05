# Python 語法筆記

## 索引

- [split()+join()](#[split()+join())

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

