# دفترچه راهنمای متدهای [Dictionary - دیکشنری](https://docs.python.org/3/library/stdtypes.html#mapping-types-dict) در پایتون

در پایتون نوع داده‌ی `dict` یک مجموعه **مرتب 'ordered' (از پایتون نسخه 3.7 به بعد)** از زوج‌های **{ key: value }** است.

* هر کلید **منحصر به فرد (unique)** و **غیر قابل تغییر (immutable)** است
* کلید ها باید مقادیر immutable مثل str , tuple , float , int باشند
* مقادیر می‌توانند تکراری باشند
* قابل تغییر (mutable)

### تعریف دیکشنری و نمایش مقادیر آن

```python
>>> etc_dict = {'a': 1, 'b': 2}
>>> etc_dict
{'a': 1, 'b': 2}
```

### دسترسی به مقادیر با استفاده از کلید

```python
>>> etc_dict = {'a': 1, 'b': 2}
>>> etc_dict['a']
1
>>> etc_dict['b']
2
```

### افزودن یا تغییر مقدار کلید

```python
>>> etc_dict = {'a': 1, 'b': 2}
>>> etc_dict['c'] = 3
>>> etc_dict['b'] = 20
>>> etc_dict
{'a': 1, 'b': 20, 'c': 3}
```

⚠️ درصورت عدم وجود کلید، خطا رخ میدهد.

# متد ها - Methods

> ### [dict.get(key, defult=None)](https://docs.python.org/3/library/stdtypes.html#dict.get)

#### دسترسی به مقادیر - در صورت عدم وجود کلید، مقدار پیش‌فرض را برمی‌گرداند:

```python
>>> etc_dict = {'a': 1, 'b': 2}
>>> etc_dict.get('c', 0)
0
>>> etc_dict.get('c', 'NULL')
'NULL'
```

> ### [dict.update(**kwargs)](https://docs.python.org/3/library/stdtypes.html#dict.update)

#### امکان افزودن چند کلید-مقدار جدید به دیکشنری یا ویرایش کلید-مقدار های قبلی:

```python
>>> etc_dict = {'a': 1, 'b': 2}
>>> etc_dict.update({'b': 20, 'c': 3})
>>> etc_dict
{'a': 1, 'b': 20, 'c': 3}
```

> ### [dict.pop(key)](https://docs.python.org/3/library/stdtypes.html#dict.pop)

#### آیتم مد نظر خود را با استفاده از کلید آن از دیکشنری بردارید و در متغیر قرار دهید:

```python
>>> etc_dict = {'a': 1, 'b': 2}
>>> value = etc_dict.pop('b')
>>> value
2
>>> etc_dict
{'a': 1}
```

```python
>>> etc_dict = {'a': 1, 'b': 2}
>>> value = etc_dict.pop('a')
>>> value
1
>>> etc_dict
{'b': 2}
```

> ### [dict.popitem()](https://docs.python.org/3/library/stdtypes.html#dict.popitem)

#### آخرین آیتم در دیکشنری را بردارید و در متغیر قرار دهید:

```python
>>> etc_dict = {'a': 1, 'b': 2}
>>> etc_dict.popitem()
{'b': 2}
>>> etc_dict
{'a': 1}
```

```python
>>> etc_dict = {'a': 1}
>>> etc_dict.popitem()
{'a': 1}
>>> etc_dict
{}
```

> ### [dict.clear()](https://docs.python.org/3/library/stdtypes.html#dict.clear)

#### تمام عناصر دیکشنری را به طوری کامل پاک کنید:

```python
>>> etc_dict = {'a': 1, 'b': 2}
>>> etc_dict.clear()
>>> etc_dict
{}
``` 

> ### [dict.copy()](https://docs.python.org/3/library/stdtypes.html#dict.copy)

#### یک کپی سطحی از دیکشنری بسازید:

```python
>>> etc_dict = {'a': 1, 'b': 2}
>>> etc_dict_copy = etc_dict.copy()
>>> etc_dict
{'a': 1, 'b': 2}
>>> etc_dict_copy
{'a': 1, 'b': 2}
```

> ### [dict.keys()](https://docs.python.org/3/library/stdtypes.html#dict.keys)

#### تمام کلید های دیکشنری را برگردانید:

```python
>>> etc_dict = {'a': 1, 'b': 2}
>>> etc_dict.keys()
dict_keys(['a', 'b'])
```

> ### [dict.values()](https://docs.python.org/3/library/stdtypes.html#dict.values)

#### تمام مقادیر کلید های دیکشنری را برگردانید:

```python
>>> etc_dict = {'a': 1, 'b': 2}
>>> etc_dict.values()
dict_values([1, 2])
```

> ### [dict.items()](https://docs.python.org/3/library/stdtypes.html#dict.items)

#### تمام مقادیر و کلید ها را به صورت های زوج های tuple برگردانید:

```python
>>> etc_dict = {'a': 1, 'b': 2}
>>> etc_dict.items()
dict_items([('a', 1), ('b', 2)])
```

---

### 📌 به خاطر داشته باشید! شما میتوانید خروجی هر 3 متد بالا را به ساختار داده های زیر تبدیل کنید.

* [tuple](https://docs.python.org/3/library/stdtypes.html#tuple)
* [list](https://docs.python.org/3/library/stdtypes.html#list)
* [set](https://docs.python.org/3/library/stdtypes.html#set)

#### به مثال های زیر توجه کنید:

```python
>>> etc_dict = {'a': 1, 'b': 2}

>>> list(etc_dict.items())
[('a', 1), ('b', 2)]

>>> tuple(etc_dict.items())
(('a', 1), ('b', 2))

>>> set(etc_dict.items())
{('a', 1), ('b', 2)}
```

```python
>>> etc_dict = {'a': 1, 'b': 2}

>>> list(etc_dict.values())
[1, 2]

>>> tuple(etc_dict.values())
(1, 2)

>>> set(etc_dict.values())
{1, 2}
```

```python
>>> etc_dict = {'a': 1, 'b': 2}

>>> list(etc_dict.keys())
['a', 'b']

>>> tuple(etc_dict.keys())
('a', 'b')

>>> set(etc_dict.keys())
{'a', 'b'}
```

### بررسی وجود کلید در دیکشنری

```python
>>> etc_dict = {'a': 1, 'b': 2}
>>> 'a' in etc_dict
True
>>> 'z' in etc_dict
False
```

### بررسی وجود مقدار در دیکشنری

```python
>>> etc_dict = {'a': 1, 'b': 2}
>>> 1 in etc_dict.values()
True
>>> 3 in etc_dict.values()
False

```

# جمع بندی سریع

| متد     | کاربرد                             |
|---------|------------------------------------|
| d[key]  | دسترسی یا تغییر مقدار بر اساس کلید |
| get     | دسترسی امن با مقدار پیش‌فرض        |
| update  | اضافه یا تغییر چند کلید:مقدار      |
| pop     | حذف کلید و دریافت مقدار            |
| popitem | حذف آخرین جفت کلید:مقدار           |
| clear   | پاک کردن کل دیکشنری                |
| keys    | مشاهده کلیدها                      |
| values  | مشاهده مقادیر                      |
| items   | مشاهده جفت کلید:مقدارها            |
| copy    | کپی سطحی گرفتن                     |


