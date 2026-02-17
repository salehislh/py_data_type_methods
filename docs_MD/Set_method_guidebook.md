# دفترچه راهنمای متدهای [Set - مجموعه](https://docs.python.org/3/library/stdtypes.html#set-types-set-frozenset) در پایتون

در پایتون نوع داده‌ی `set` یک مجموعه **نامرتب (unordered)**، **غیرقابل‌اندیس‌گذاری (unindexed)** و **قابل تغییر (mutable)** است.

یعنی:

* عناصر **منحصر به فرد (unique)** هستند (تکراری مجاز نیست)
* **ترتیب** عناصر حفظ نمی‌شود
* نمی‌توان با اندیس به عناصر دسترسی داشت
* عناصر باید **غیرقابل تغییر (immutable)** باشند (مثل int, str, tuple)

### تعریف مجموعه و نمایش آن

```python
>>> etc_set = {10, 'Apple', 3.5, (1, 2, 3)}
>>> etc_set
{3.5, 10, 'Apple', (1, 2, 3)}  # ترتیب ممکن است متفاوت باشد
```

### تعریف مجموعه با تابع set()

```python
>>> etc_set = set([1, 2, 3, 2, 1])  # تبدیل لیست به مجموعه (تکراری‌ها حذف می‌شوند)
>>> etc_set
{1, 2, 3}

>>> etc_set = set("hello")  # تبدیل رشته به مجموعه
>>> etc_set
{'h', 'e', 'l', 'o'}  # ترتیب و تکرارها حذف شده‌اند
```

### مجموعه خالی

⚠️ توجه: برای مجموعه خالی باید از `set()` استفاده کرد، `{}` یک دیکشنری خالی است.

```python
>>> empty_set = set()
>>> empty_set
set()

>>> type(empty_set)
<class 'set'>
```

# متد ها - Methods

> ### [set.add(element)](https://docs.python.org/3/library/stdtypes.html#frozenset.add)

#### عنصر جدید به مجموعه اضافه می‌کند (اگر وجود نداشته باشد):

```python
>>> etc_set = {1, 2, 3}
>>> etc_set.add(4)
>>> etc_set
{1, 2, 3, 4}

>>> etc_set.add(2)  # عنصر تکراری، تغییری ایجاد نمی‌کند
>>> etc_set
{1, 2, 3, 4}
```

> ### [set.update(iterable)](https://docs.python.org/3/library/stdtypes.html#frozenset.update)

#### چند عنصر جدید را به مجموعه اضافه می‌کند:

```python
>>> etc_set = {1, 2, 3}
>>> etc_set.update([3, 4, 5])
>>> etc_set
{1, 2, 3, 4, 5}

>>> etc_set.update({6, 7}, (8, 9))
>>> etc_set
{1, 2, 3, 4, 5, 6, 7, 8, 9}
```

> ### [set.remove(element)](https://docs.python.org/3/library/stdtypes.html#frozenset.remove)

#### عنصر مشخص را از مجموعه حذف می‌کند (در صورت عدم وجود خطا می‌دهد):

```python
>>> etc_set = {1, 2, 3, 4}
>>> etc_set.remove(3)
>>> etc_set
{1, 2, 4}

>>> etc_set.remove(10)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 10
```

> ### [set.discard(element)](https://docs.python.org/3/library/stdtypes.html#frozenset.discard)

#### عنصر مشخص را حذف می‌کند (اگر وجود نداشت، خطایی نمی‌دهد):

```python
>>> etc_set = {1, 2, 3, 4}
>>> etc_set.discard(3)
>>> etc_set
{1, 2, 4}

>>> etc_set.discard(10)  # هیچ خطایی رخ نمی‌دهد
>>> etc_set
{1, 2, 4}
```

> ### [set.pop()](https://docs.python.org/3/library/stdtypes.html#frozenset.pop)

#### یک عنصر تصادفی را از مجموعه حذف و برمی‌گرداند:

```python
>>> etc_set = {1, 2, 3, 4}
>>> etc_set.pop()  # عنصر تصادفی حذف می‌شود
1
>>> etc_set.pop()
2
>>> etc_set
{3, 4}
```

⚠️ اگر مجموعه خالی باشد، خطای `KeyError` می‌دهد.

> ### [set.clear()](https://docs.python.org/3/library/stdtypes.html#frozenset.clear)

#### تمام عناصر مجموعه را پاک می‌کند:

```python
>>> etc_set = {1, 2, 3, 4}
>>> etc_set.clear()
>>> etc_set
set()
```

> ### [set.copy()](https://docs.python.org/3/library/stdtypes.html#frozenset.copy)

#### یک کپی سطحی از مجموعه می‌سازد:

```python
>>> etc_set = {1, 2, 3}
>>> etc_set_copy = etc_set.copy()
>>> etc_set_copy
{1, 2, 3}
>>> etc_set is etc_set_copy
False
```

## عملیات مجموعه‌ها (Operations)

> ### [set.union(other_set)](https://docs.python.org/3/library/stdtypes.html#frozenset.union)

#### اجتماع دو مجموعه (همه عناصر هر دو مجموعه):

```python
>>> set_a = {1, 2, 3}
>>> set_b = {3, 4, 5}

>>> set_a.union(set_b)
{1, 2, 3, 4, 5}

>>> set_a | set_b  # عملگر | هم همین کار را می‌کند
{1, 2, 3, 4, 5}
```

> ### [set.intersection(other_set)](https://docs.python.org/3/library/stdtypes.html#frozenset.intersection)

#### اشتراک دو مجموعه (عناصر مشترک):

```python
>>> set_a = {1, 2, 3}
>>> set_b = {3, 4, 5}

>>> set_a.intersection(set_b)
{3}

>>> set_a & set_b  # عملگر & هم همین کار را می‌کند
{3}
```

> ### [set.difference(other_set)](https://docs.python.org/3/library/stdtypes.html#frozenset.difference)

#### تفاضل دو مجموعه (عناصر set_a که در set_b نیستند):

```python
>>> set_a = {1, 2, 3, 4}
>>> set_b = {3, 4, 5}

>>> set_a.difference(set_b)
{1, 2}

>>> set_a - set_b  # عملگر - هم همین کار را می‌کند
{1, 2}
```

> ### [set.symmetric_difference(other_set)](https://docs.python.org/3/library/stdtypes.html#frozenset.symmetric_difference)

#### اختلاف متقارن (عناصری که فقط در یکی از مجموعه‌ها هستند):

```python
>>> set_a = {1, 2, 3, 4}
>>> set_b = {3, 4, 5, 6}

>>> set_a.symmetric_difference(set_b)
{1, 2, 5, 6}

>>> set_a ^ set_b  # عملگر ^ هم همین کار را می‌کند
{1, 2, 5, 6}
```

## متدهای بررسی روابط مجموعه‌ها

> ### [set.issubset(other_set)](https://docs.python.org/3/library/stdtypes.html#frozenset.issubset)

#### بررسی می‌کند که آیا مجموعه، زیرمجموعه مجموعه دیگر است:

```python
>>> set_a = {1, 2, 3}
>>> set_b = {1, 2, 3, 4, 5}

>>> set_a.issubset(set_b)
True

>>> set_a <= set_b  # عملگر <= هم همین کار را می‌کند
True
```

> ### [set.issuperset(other_set)](https://docs.python.org/3/library/stdtypes.html#frozenset.issuperset)

#### بررسی می‌کند که آیا مجموعه، ابرمجموعه مجموعه دیگر است:

```python
>>> set_a = {1, 2, 3, 4, 5}
>>> set_b = {2, 3, 4}

>>> set_a.issuperset(set_b)
True

>>> set_a >= set_b  # عملگر >= هم همین کار را می‌کند
True
```

> ### [set.isdisjoint(other_set)](https://docs.python.org/3/library/stdtypes.html#frozenset.isdisjoint)

#### بررسی می‌کند که آیا دو مجموعه هیچ عنصر مشترکی ندارند:

```python
>>> set_a = {1, 2, 3}
>>> set_b = {4, 5, 6}

>>> set_a.isdisjoint(set_b)
True

>>> set_c = {3, 4, 5}
>>> set_a.isdisjoint(set_c)
False  # عدد 3 مشترک است
```

## متدهای به‌روزرسانی درجا

> ### [set.intersection_update(other_set)](https://docs.python.org/3/library/stdtypes.html#frozenset.intersection_update)

#### مجموعه اصلی را با اشتراک خودش و مجموعه دیگر جایگزین می‌کند:

```python
>>> set_a = {1, 2, 3, 4}
>>> set_b = {3, 4, 5}

>>> set_a.intersection_update(set_b)
>>> set_a
{3, 4}
```

> ### [set.difference_update(other_set)](https://docs.python.org/3/library/stdtypes.html#frozenset.difference_update)

#### مجموعه اصلی را با تفاضل خودش و مجموعه دیگر جایگزین می‌کند:

```python
>>> set_a = {1, 2, 3, 4}
>>> set_b = {3, 4, 5}

>>> set_a.difference_update(set_b)
>>> set_a
{1, 2}
```

> ### [set.symmetric_difference_update(other_set)](https://docs.python.org/3/library/stdtypes.html#frozenset.symmetric_difference_update)

#### مجموعه اصلی را با اختلاف متقارن خودش و مجموعه دیگر جایگزین می‌کند:

```python
>>> set_a = {1, 2, 3, 4}
>>> set_b = {3, 4, 5, 6}

>>> set_a.symmetric_difference_update(set_b)
>>> set_a
{1, 2, 5, 6}
```

### بررسی وجود عنصر در مجموعه

```python
>>> etc_set = {1, 2, 3, 4}
>>> 2 in etc_set
True
>>> 5 in etc_set
False
```

### طول مجموعه

```python
>>> etc_set = {1, 2, 3, 4}
>>> len(etc_set)
4
```

## جمع‌بندی سریع متدهای `set`

| متد                      | کاربرد                                   |
|--------------------------|------------------------------------------|
| add                      | اضافه کردن یک عنصر                       |
| update                   | اضافه کردن چند عنصر                       |
| remove                   | حذف عنصر (در صورت عدم وجود خطا)          |
| discard                  | حذف عنصر (در صورت عدم وجود، نادیده می‌گیرد) |
| pop                      | حذف و برگرداندن یک عنصر تصادفی            |
| clear                    | پاک کردن کل مجموعه                        |
| copy                     | کپی سطحی گرفتن                            |
| union (`\|`)             | اجتماع دو مجموعه                          |
| intersection (`&`)       | اشتراک دو مجموعه                          |
| difference (`-`)         | تفاضل دو مجموعه                           |
| symmetric_difference (`^`)| اختلاف متقارن                            |
| issubset (`<=`)          | بررسی زیرمجموعه بودن                      |
| issuperset (`>=`)        | بررسی ابرمجموعه بودن                      |
| isdisjoint               | بررسی عدم اشتراک                          |
| intersection_update      | به‌روزرسانی با اشتراک                      |
| difference_update        | به‌روزرسانی با تفاضل                       |
| symmetric_difference_update | به‌روزرسانی با اختلاف متقارن              |