# دفترچه راهنمای متدهای [List - لیست](https://docs.python.org/3/library/stdtypes.html#list) در پایتون


در پایتون نوع داده‌ی `list` مجموعه‌ای **مرتب (ordered)** و **قابل تغییر (mutable)** است.
یعنی:

* میتواند انواع داده ها را در خود جای دهد
* ترتیب عناصر حفظ می‌شود
* می‌توان عناصر را تغییر، اضافه یا حذف کرد
* عناصر تکراری مجاز هستند

### تعریف لیست و نمایش مقادیر آن:
```python
>>> etc_list = [10, 'Apple', 3+5j, 4.5, [1, 2, 3], False]
>>> etc_list
[10, 'Apple', 3+5j, 4.5, [1, 2, 3], False]
```

### دسترسی به عناصر با استفاده از اندیس (index):
```python
>>> etc_list = [10, 20, 30, 40, 50, 60]
>>> etc_list[0]
10
>>> etc_list[-1] 
60
```

### برش (Slicing):
```python
>>> etc_list = [10, 20, 30, 40, 50, 60]

>>> etc_list[1:4] # index 4 not included
[20, 30, 40]

>>> etc_list[:3]
[10, 20, 30]

>>> etc_list[3:]
[40, 50, 60]
```

# متد ها - Methods

> ### [list.append(value)](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)
#### به آخرین اندیس لیست مقدار مد نظر خود را اضافه کنید
```python
>>> etc_list = [10, 20, 30]
>>> etc_list.append(40)
>>> etc_list
[10, 20, 30, 40]
```

> ### [list.insert(index, value)](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)
#### مقدار جدید را در اندیس مد نظر درج کنید:
```python
>>> etc_list = [1, 2, 3]
>>> etc_list.insert(1, 10)
>>> etc_list
[1, 10, 2, 3]
```

> ### [list.extend(iterable)](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists) 
#### 2 لیست را باهم تجمیع کنید:
```python
>>> etc_list = [1, 2, 3]
>>> etc_list.extend([4, 5])
>>> etc_list
[1, 2, 3, 4, 5]
```

> ### [list.remove(value)](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)
#### حذف اولین عضو مشخص
```python
>>> etc_list = [1, 2, 3, 2]
>>> etc_list.remove(2)
>>> etc_list
[1, 3, 2]
```

> ### [list.pop(index)](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)
#### آخرین مقدار در لیست را بردارید یا براساس اندیس مد نظر را بردارید و خروجی دهید:
```python
>>> etc_list = [1, 2, 3]
>>> number = etc_list.pop()
>>> number
3
>>> etc_list.pop(0)
1
>>> etc_list
[2]
```

> ### [list.clear()](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)
#### حذف همه اعضا
```python
>>> etc_list = [1, 2, 3]
>>> etc_list.clear()
>>> etc_list
[]
```

> ### [list.index(value[, start[, end]])](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)

#### اندیس عناصر را نمایش دهید:
```python
>>> etc_list = [1, 2, 3, 2, 4]
>>> etc_list.index(2) # اندیس اولین رخداد 2 از چپ را برگشت میدهد 
1 

>>> etc_list = [1, 2, 3, 5, 4]
>>> etc_list.index(5, 2) # از اندیس 2 شروع کنید (آرگومان دوم متد)، اولین 5 در اندیس 3
3

>>> etc_list = [1, 2, 3, 2, 4]
>>> etc_list.index(2, 0, 2) # جستجو بین اندیس ۰ تا ۲، اولین 2 در اندیس ۱ از چپ
1
```

> ### [list.count(value)](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)
#### عناصر مد نظر را شمارش کنید و مقدار را برگشت دهید:
```python
>>> etc_list = [1, 2, 2, 3]
>>> etc_list.count(2)
2
>>> etc_list.count(3)
1
```

>### [list.sort(*, key=None, reverse=False)](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)
### مرتب‌سازی درجا:
```python
>>> etc_list = [3, 1, 2]
>>> etc_list.sort()
>>> etc_list
[1, 2, 3]
```
#### مرتب سازی نزولی:
```python
>>> etc_list = [3, 1, 2]
>>> etc_list.sort(reverse=True)
>>> etc_list
[3, 2, 1]
```
#### مرتب سازی بر اساس طول هر کاراکتر همچنان میتوان از آرگومان reverse استفاده کرد:
```python
>>> etc_list = ["banana", "apple", "kiwi", "strawberry"]
>>> etc_list.sort(key=len) # بر اساس طول هر عنصر مرتب کنید
>>> etc_list
['kiwi', 'apple', 'banana', 'strawberry']
```
#### اعداد منفی را با مقدار قدر مطلق آنها که عددی مثبت است مرتب کنید: 
```python
>>> etc_list = [-5, 3, -1, 4]
>>> etc_list.sort(key=abs) # بر اساس مقدار قدر مطلق مرتب کنید
>>> etc_list
[-1, 3, 4, -5]
```
#### با استفاده از یک تابع عنصر دوم هر تاپل را خارج کنید و بر اساس عنصر دوم هر تاپل مرتب کنید:
```python
>>> etc_list = [(1, 3), (2, 1), (3, 2)]

>>> def second_element(item):
...     return item[1] # عنصر دوم را خروجی میدهد

>>> etc_list.sort(key=second_element) # بر اساس عنصر دوم مرتب میکند
>>> etc_list
[(2, 1), (3, 2), (1, 3)]
```

> ### [sorted(iterable)](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)
#### مرتب‌سازی و بازگشت لیست جدید:
```python
>>> etc_list = [3, 1, 2]

>>> sorted(etc_list)
[1, 2, 3]

>>> etc_list_sorted = sorted(etc_list)
>>> etc_list_sorted
[1, 2, 3]
```

> ### [list.reverse()](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)
#### معکوس کردن درجا:
```python
>>> etc_list = [1, 2, 3]
>>> etc_list.reverse()
>>> etc_list
[3, 2, 1]
```
> ### [list.copy()](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)
#### یک کپی سطحی از لیست برمیگرداند
```python
>>> etc_list = [1, 2, 3]

>>> etc_list.copy()
[1, 2, 3]

>>> etc_list_copy = etc_list.copy()
>>> etc_list_copy
[1, 2, 3]
```

## جمع‌بندی سریع متدهای `list`

| متد     | کاربرد                        |
| ------- | ----------------------------- |
| append  | اضافه کردن عضو به انتهای لیست |
| insert  | درج عضو در موقعیت مشخص        |
| extend  | اضافه کردن چند عضو            |
| remove  | حذف اولین عضو مشخص            |
| pop     | حذف عضو بر اساس اندیس         |
| clear   | حذف همه اعضا                  |
| index   | پیدا کردن اندیس اولین عضو     |
| count   | شمارش تکرار یک عضو            |
| sort    | مرتب‌سازی درجا                |
| sorted  | مرتب‌سازی و بازگشت لیست جدید  |
| reverse | معکوس کردن درجا               |
| copy    | کپی گرفتن                     |


