# Python 語法筆記

## 索引

- [`%` (餘數運算)](#餘數運算)
- [`//` (整除運算)](#整除運算)
- [`.append()`](#append)
- [`.join()`](#join)
---

## `%` (餘數運算)

**用途：** 計算除法的餘數

**語法：** `a % b`

**特性：**
- 返回 a 除以 b 的餘數
- 常用於判斷奇偶數
- 用於週期性計算

**範例：**
```python
print(10 % 3)   # 1 (10 ÷ 3 = 3 餘 1)
print(15 % 4)   # 3 (15 ÷ 4 = 3 餘 3)
print(8 % 2)    # 0 (8 ÷ 2 = 4 餘 0)

# 判斷奇偶數
if year % 2 == 0:
    print("偶數")
else:
    print("奇數")

# 判斷閏年
if year % 4 == 0:
    print("可能是閏年")
```

**常見用法：** 檢查整除、週期計算、奇偶判斷

---

## `//` (整除運算)

**用途：** 執行整數除法，返回商的整數部分

**語法：** `a // b`

**特性：**
- 返回除法結果的整數部分（向下取整）
- 等同於 `int(a / b)`（正數時）
- 可用於快速計算商

**範例：**
```python
print(10 // 3)   # 3 (10 ÷ 3 = 3.333..., 取整數部分)
print(15 // 4)   # 3 (15 ÷ 4 = 3.75, 取整數部分)
print(7 // 2)    # 3 (7 ÷ 2 = 3.5, 取整數部分)

# 對比普通除法
print(10 / 3)    # 3.3333333333333335
print(10 // 3)   # 3

# 計算需要多少組
students = 25
group_size = 4
groups_needed = students // group_size  # 6 組
remaining = students % group_size        # 剩餘 1 人
```

**對比：** `/` 是普通除法，`//` 是整除，`%` 是餘數

---

## `.append()`

**用途：** 在列表末尾添加一個元素

**語法：** `list.append(item)`

**特性：**
- **修改原列表**
- **返回 `None`**
- 只能添加一個元素
- 在列表末尾添加

**範例：**
```python
fruits = ['apple', 'banana']
fruits.append('orange')
print(fruits)  # ['apple', 'banana', 'orange']

# 添加不同類型的元素
numbers = [1, 2, 3]
numbers.append(4)         # 添加數字
numbers.append([5, 6])    # 添加列表作為一個元素
print(numbers)  # [1, 2, 3, 4, [5, 6]]

# 錯誤用法
result = numbers.append(7)  # result 是 None！
```

**相關方法：** `extend()` 添加多個元素，`insert()` 指定位置添加

---

## `.join()`

**用途：** 用指定的分隔符連接字串序列

**語法：** `separator.join(iterable)`

**特性：**
- 分隔符在前，要連接的序列在後
- 只能連接字串元素
- 返回新字串，不修改原資料

**範例：**
```python
# 基本用法
words = ['apple', 'banana', 'cherry']
result = '-'.join(words)        # 'apple-banana-cherry'
result = ', '.join(words)       # 'apple, banana, cherry'
result = ''.join(words)         # 'applebananacherry'

# 連接數字（需先轉字串）
numbers = [1, 2, 3, 4, 5]
result = ''.join(str(x) for x in numbers)  # '12345'
# 或者
result = ''.join(map(str, numbers))        # '12345'

# 常見用法：從輸入建立連續字串
n = 5
result = ''.join(str(i) for i in range(1, n+1))  # '12345'
```
