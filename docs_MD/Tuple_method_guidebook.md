# دفترچه راهنمای متدهای [Tuple - تاپل](https://docs.python.org/3/library/stdtypes.html#tuple) در پایتون

در پایتون نوع داده‌ی `tuple` یک مجموعه **مرتب (ordered)** و **غیرقابل تغییر (immutable)** است.

یعنی:

* می‌تواند انواع داده‌ها را در خود جای دهد
* ترتیب عناصر حفظ می‌شود
* **نمی‌توان** پس از ساخته شدن، عناصر را تغییر، اضافه یا حذف کرد
* عناصر تکراری مجاز هستند
* نسبت به لیست، حافظه کمتری مصرف می‌کند و سریع‌تر است

### تعریف تاپل و نمایش آن

```python
>>> etc_tuple = (10, 'Apple', 3+5j, 4.5, [1, 2, 3], False)
>>> etc_tuple
(10, 'Apple', (3+5j), 4.5, [1, 2, 3], False)
```

### تعریف تاپل بدون پرانتز

```python
>>> etc_tuple = 10, 'Apple', 3.5, True
>>> etc_tuple
(10, 'Apple', 3.5, True)
```

### تاپل یک عنصری

⚠️ برای تعریف تاپل با یک عنصر، حتماً باید از کاما استفاده کنید:

```python
>>> single_tuple = (5,)  # درست
>>> single_tuple
(5,)

>>> not_tuple = (5)  # نادرست - این یک عدد است، تاپل نیست
>>> not_tuple
5
>>> type(not_tuple)
<class 'int'>
```

### تاپل خالی

```python
>>> empty_tuple = ()
>>> empty_tuple
()
```

### دسترسی به عناصر با استفاده از اندیس (index):

```python
>>> etc_tuple = (10, 20, 30, 40, 50)
>>> etc_tuple[0]
10
>>> etc_tuple[-1]
50
>>> etc_tuple[2]
30
```

### برش (Slicing):

```python
>>> etc_tuple = (10, 20, 30, 40, 50, 60)

>>> etc_tuple[1:4]  # اندیس 4 شامل نمی‌شود
(20, 30, 40)

>>> etc_tuple[:3]
(10, 20, 30)

>>> etc_tuple[3:]
(40, 50, 60)

>>> etc_tuple[::2]  # گام 2
(10, 30, 50)
```

# متدها - Methods

تاپل به دلیل غیرقابل تغییر بودن، متدهای کمی دارد. بیشتر عملیات روی تاپل از طریق توابع داخلی پایتون انجام می‌شود.

> ### [tuple.count(value)](https://docs.python.org/3/library/stdtypes.html#tuple.count)

#### تعداد دفعات تکرار یک مقدار در تاپل را برمی‌گرداند:

```python
>>> etc_tuple = (1, 2, 2, 3, 2, 4, 5)
>>> etc_tuple.count(2)
3
>>> etc_tuple.count(5)
1
>>> etc_tuple.count(10)
0
```

> ### [tuple.index(value[, start[, end]])](https://docs.python.org/3/library/stdtypes.html#tuple.index)

#### اندیس اولین رخداد مقدار مورد نظر را برمی‌گرداند (در صورت عدم وجود خطا می‌دهد):

```python
>>> etc_tuple = (1, 2, 3, 2, 4, 5)

>>> etc_tuple.index(2)  # اولین رخداد 2 از چپ
1

>>> etc_tuple.index(2, 2)  # از اندیس 2 به بعد جستجو کن
3

>>> etc_tuple.index(2, 0, 3)  # بین اندیس 0 تا 3 جستجو کن
1

>>> etc_tuple.index(10)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: tuple.index(x): x not in tuple
```

## توابع مفید برای کار با تاپل

> ### [len()](https://docs.python.org/3/library/functions.html#len)

#### تعداد عناصر تاپل را برمی‌گرداند:

```python
>>> etc_tuple = (10, 20, 30, 40, 50)
>>> len(etc_tuple)
5
```

> ### [min()](https://docs.python.org/3/library/functions.html#min)

#### کوچکترین عنصر تاپل را برمی‌گرداند:

```python
>>> etc_tuple = (10, 20, 5, 40, 15)
>>> min(etc_tuple)
5

>>> str_tuple = ('apple', 'banana', 'kiwi')
>>> min(str_tuple)  # بر اساس ترتیب الفبا
'apple'
```

> ### [max()](https://docs.python.org/3/library/functions.html#max)

#### بزرگترین عنصر تاپل را برمی‌گرداند:

```python
>>> etc_tuple = (10, 20, 5, 40, 15)
>>> max(etc_tuple)
40

>>> str_tuple = ('apple', 'banana', 'kiwi')
>>> max(str_tuple)  # بر اساس ترتیب الفبا
'kiwi'
```

> ### [sum()](https://docs.python.org/3/library/functions.html#sum)

#### جمع عناصر عددی تاپل را برمی‌گرداند:

```python
>>> etc_tuple = (10, 20, 5, 40, 15)
>>> sum(etc_tuple)
90

>>> etc_tuple = (1.5, 2.5, 3.5)
>>> sum(etc_tuple)
7.5
```

> ### [sorted()](https://docs.python.org/3/library/functions.html#sorted)

#### یک لیست مرتب‌شده از عناصر تاپل برمی‌گرداند (تاپل اصلی تغییری نمی‌کند):

```python
>>> etc_tuple = (30, 10, 50, 20, 40)
>>> sorted(etc_tuple)
[10, 20, 30, 40, 50]

>>> sorted(etc_tuple, reverse=True)
[50, 40, 30, 20, 10]

>>> str_tuple = ('banana', 'apple', 'kiwi')
>>> sorted(str_tuple, key=len)  # بر اساس طول کلمات
['kiwi', 'apple', 'banana']
```

> ### [tuple()](https://docs.python.org/3/library/stdtypes.html#tuple)

#### تبدیل سایر ساختارهای داده به تاپل:

```python
>>> list_to_tuple = tuple([1, 2, 3, 4])
>>> list_to_tuple
(1, 2, 3, 4)

>>> str_to_tuple = tuple("Python")
>>> str_to_tuple
('P', 'y', 't', 'h', 'o', 'n')

>>> set_to_tuple = tuple({1, 2, 3, 4})
>>> set_to_tuple
(1, 2, 3, 4)

>>> range_to_tuple = tuple(range(5))
>>> range_to_tuple
(0, 1, 2, 3, 4)
```

## عملیات روی تاپل‌ها

### ترکیب تاپل‌ها (Concatenation)

```python
>>> tuple_a = (1, 2, 3)
>>> tuple_b = (4, 5, 6)
>>> tuple_a + tuple_b
(1, 2, 3, 4, 5, 6)
```

### تکرار تاپل (Repetition)

```python
>>> etc_tuple = (1, 2, 3)
>>> etc_tuple * 3
(1, 2, 3, 1, 2, 3, 1, 2, 3)
```

### بررسی وجود عنصر در تاپل

```python
>>> etc_tuple = (10, 20, 30, 40)
>>> 20 in etc_tuple
True
>>> 50 in etc_tuple
False
>>> 50 not in etc_tuple
True
```

### unpacking - باز کردن اعضای تاپل

```python
>>> point = (10, 20)
>>> x, y = point
>>> x
10
>>> y
20

>>> person = ('Ali', 25, 'Tehran')
>>> name, age, city = person
>>> name
'Ali'
>>> age
25
>>> city
'Tehran'

>>> numbers = (1, 2, 3, 4, 5)
>>> first, *middle, last = numbers
>>> first
1
>>> middle
[2, 3, 4]
>>> last
5
```

### مقایسه تاپل‌ها

```python
>>> (1, 2, 3) < (1, 2, 4)
True
>>> (1, 2, 3) == (1, 2, 3)
True
>>> (1, 2, 3) > (1, 2, 2)
True
```

## کاربردهای خاص تاپل

### استفاده از تاپل به عنوان کلید در دیکشنری

```python
>>> locations = {}
>>> locations[(35.6892, 51.3890)] = 'Tehran'
>>> locations[(40.7128, 74.0060)] = 'New York'
>>> locations
{(35.6892, 51.389): 'Tehran', (40.7128, 74.006): 'New York'}
```

### بازگرداندن چند مقدار از تابع

```python
>>> def get_min_max(numbers):
...     return min(numbers), max(numbers)
...
>>> result = get_min_max([10, 30, 5, 40, 15])
>>> result
(5, 40)
>>> min_val, max_val = result
>>> min_val
5
>>> max_val
40
```

## جمع‌بندی سریع متدها و توابع `tuple`

| متد/تابع   | کاربرد                             |
|------------|------------------------------------|
| count      | شمارش تعداد تکرار یک مقدار         |
| index      | پیدا کردن اندیس اولین رخداد        |
| len()      | تعداد عناصر تاپل                    |
| min()      | کوچکترین عنصر                      |
| max()      | بزرگترین عنصر                       |
| sum()      | جمع عناصر عددی                      |
| sorted()   | ایجاد لیست مرتب‌شده از عناصر        |
| tuple()    | تبدیل به تاپل                       |
| +          | ترکیب دو تاپل                       |
| *          | تکرار تاپل                          |
| in         | بررسی وجود عنصر                     |