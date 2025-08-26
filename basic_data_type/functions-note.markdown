# Python 語法筆記

## 索引

- [`list` & `set` 轉換](#list--set-轉換)
- [`map()`](#map)
- [`max()`](#max)
- [負索引 `arr[-2]`](#負索引-arr-2)
- [`.remove()`](#remove)
- [`set()`](#set)
- [`sorted()`](#sorted)
- [`List Comprehension`](#List_Comprehension )

---

## `map()`

**用途：** 對序列中的每個元素應用指定函數

**語法：** `map(function, iterable)`

**特性：**
- 返回 `map object`（迭代器）
- 懶加載，節省記憶體
- 一次性使用，消耗後變空

**範例：**
```python
# 將字串列表轉換為整數列表
arr = map(int, ['1', '2', '3'])
print(list(arr))  # [1, 2, 3]

# 常見用法：處理輸入
arr = map(int, input().split())
scores = list(arr)  # 轉成 list 使用
```

**注意：** `map object` 需要用 `list()` 轉換才能看到內容

---

## `sorted()`

**用途：** 對序列中的每個元素應用指定函數

**語法：** `map(function, iterable)`

**特性：**
- 返回 `map object`（迭代器）
- 懶加載，節省記憶體
- 一次性使用，消耗後變空

**範例：**
```python
# 將字串列表轉換為整數列表
arr = map(int, ['1', '2', '3'])
print(list(arr))  # [1, 2, 3]

# 常見用法：處理輸入
arr = map(int, input().split())
scores = list(arr)  # 轉成 list 使用
```

**注意：** `map object` 需要用 `list()` 轉換才能看到內容

---

## `sorted()`

**用途：** 對可迭代物件進行排序

**語法：** `sorted(iterable, reverse=False)`

**特性：**
- 返回**新的**排序列表
- 不修改原始資料
- 預設由小到大排序

**範例：**
```python
numbers = [3, 1, 4, 1, 5]
result = sorted(numbers)      # [1, 1, 3, 4, 5]
reverse_result = sorted(numbers, reverse=True)  # [5, 4, 3, 1, 1]

print(numbers)  # [3, 1, 4, 1, 5] (原始資料不變)
```

**對比：** `list.sort()` 會修改原列表並返回 `None`

---

## `set()`

**用途：** 創建集合，自動去除重複元素

**語法：** `set(iterable)`

**特性：**
- 無序
- 唯一元素（自動去重）
- 可進行集合運算

**範例：**
```python
numbers = [1, 2, 2, 3, 3, 3]
unique = set(numbers)         # {1, 2, 3}
unique_list = list(unique)    # [1, 2, 3] (轉回 list)

# 常見用法：去重複後排序
sorted_unique = sorted(set(numbers))  # [1, 2, 3]
```

**注意：** `set` 無序，需要排序時要配合 `sorted()`

---

## `list` & `set` 轉換

**用途：** 在列表和集合之間轉換

**常見模式：**
```python
# 去重複的標準做法
original = [1, 2, 2, 3, 3, 3]
step1 = set(original)           # {1, 2, 3} - 去重複
step2 = list(step1)             # [1, 2, 3] - 轉回 list
step3 = sorted(step2)           # [1, 2, 3] - 排序

# 一行寫法
result = sorted(set(original))   # [1, 2, 3]
```

**使用場景：**
- 需要去除重複元素
- 保持資料為 list 格式方便索引

---

## 負索引 `arr[-2]`

**用途：** 從列表末尾開始計算索引

**語法：** `list[negative_index]`

**索引對照：**
```python
arr = [10, 20, 30, 40, 50]
#      0   1   2   3   4   (正索引)
#     -5  -4  -3  -2  -1   (負索引)

print(arr[-1])   # 50 (最後一個)
print(arr[-2])   # 40 (倒數第二個)
print(arr[-3])   # 30 (倒數第三個)
```

**常見用法：**
```python
# 找最大和第二大
sorted_scores = sorted(set(scores))
max_score = sorted_scores[-1]      # 最大
second_max = sorted_scores[-2]     # 第二大
```

---

## `.remove()`

**用途：** 從列表中移除指定元素的第一個出現

**語法：** `list.remove(value)`

**特性：**
- **修改原列表**
- **返回 `None`**
- 只移除第一個匹配的元素
- 如果元素不存在會報錯

**範例：**
```python
scores = [1, 2, 3, 2, 4]
scores.remove(2)        # 移除第一個 2
print(scores)           # [1, 3, 2, 4]

# 錯誤用法
result = scores.remove(3)  # result 是 None！
print(result)              # None

# 正確用法
scores.remove(3)           # 只是移除，不獲取返回值
print(max(scores))         # 然後對修改後的列表操作
```

**常見錯誤：** `max(scores.remove(item))` → 錯誤！

---

## `max()`

**用途：** 找出可迭代物件中的最大值

**語法：** `max(iterable)` 或 `max(a, b, c, ...)`

**特性：**
- 返回最大值（不是索引）
- 可比較數字、字串等
- 空序列會報錯

**範例：**
```python
numbers = [3, 1, 4, 1, 5]
largest = max(numbers)          # 5

# 多個參數
largest = max(3, 1, 4, 1, 5)    # 5

# 字串比較（字典序）
words = ['apple', 'banana', 'cherry']
last_word = max(words)          # 'cherry'

# 空列表會報錯
# max([])  # ValueError!
```

**配對函數：** `min()` 找最小值


---

## `List Comprehension`

**用途：** 簡化迴圈的使用來創建list，可以把迴圈和條件濃縮成一行。

**語法：** 
```python
    # 基本格式
    [expression for item in iterable] 
    # 帶有條件的格式
    [expression for item in iterable if condition] 
```

**範例：**
```python

# 一、列表運算

    # 傳統
    numbers = [1,2,3,4,5]
    results = []
    for i in numbers:
        results.append(i ** 2)
    print(results)  # [1,4,9,16,25]

    # list comprehension
    numbers = [1,2,3,4,5]
    results = [i ** 2 for i in numbers] # 不用再建立空回圈＋append
    print(results)  # [1,4,9,16,25]

# 二、字串處理

    # 傳統
    words = ['apple', 'banana', 'cherry']
    upper = []
    for i in words:
        upper.append(i.upper())
    print(upper)  # ['APPLE', 'BANANA', 'CHERRY']

    # list comprehension
    words = ['apple', 'banana', 'cherry']
    upper = [i.upper() for i in words] # 不用再建立空回圈＋append
    print(upper)  # ['APPLE', 'BANANA', 'CHERRY']

# 三、加上條件判斷（只要偶數，再平方）

    # 傳統
    numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    even = []
    for i in numbers:
        if i % 2 == 0:
            even.append(i ** 2)
    print(even)  # [4,16,36,64,100]

    # list comprehension
    numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    even = [i ** 2 for i in numbers if i % 2 == 0]
    print(even)  # [4,16,36,64,100]

```

**相關函數：**`.append()`, `.upper()`, `.lower()` or 建立空list or if等條件式
