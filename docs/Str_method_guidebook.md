# دفترچه راهنمای متدهای [String - رشته](https://docs.python.org/3/library/stdtypes.html#string-methods) در پایتون

در پایتون نوع داده‌ی `str` مجموعه‌ای **غیرقابل تغییر (immutable)** و **دنباله‌ای (sequence)** از کاراکترها است.

یعنی:

* هر کاراکتر در رشته یک موقعیت (اندیس) دارد
* **نمی‌توان** پس از ساخته شدن، رشته را تغییر داد
* هر متدی که روی رشته اعمال می‌شود، یک **رشته جدید** برمی‌گرداند
* رشته‌ها مرتب (ordered) هستند

### تعریف رشته و نمایش آن

```python
>>> etc_str = "Python Programming"
>>> etc_str
'Python Programming'
```

### دسترسی به کاراکترها با استفاده از اندیس (index):

```python
>>> etc_str = "Python"
>>> etc_str[0]
'P'
>>> etc_str[-1]
'n'
```

### برش (Slicing):

```python
>>> etc_str = "Python Programming"

>>> etc_str[0:6]
'Python'

>>> etc_str[:6]
'Python'

>>> etc_str[7:]
'Programming'
```

# متد ها - Methods

> ### [str.upper()](https://docs.python.org/3/library/stdtypes.html#str.upper)

#### تمام حروف رشته را به حروف بزرگ تبدیل می‌کند:

```python
>>> etc_str = "Python"
>>> etc_str.upper()
'PYTHON'
>>> etc_str  # رشته اصلی تغییر نکرده
'Python'
```

> ### [str.lower()](https://docs.python.org/3/library/stdtypes.html#str.lower)

#### تمام حروف رشته را به حروف کوچک تبدیل می‌کند:

```python
>>> etc_str = "Python"
>>> etc_str.lower()
'python'
```

> ### [str.capitalize()](https://docs.python.org/3/library/stdtypes.html#str.capitalize)

#### اولین حرف رشته را بزرگ و بقیه را کوچک می‌کند:

```python
>>> etc_str = "python PROGRAMMING"
>>> etc_str.capitalize()
'Python programming'
```

> ### [str.title()](https://docs.python.org/3/library/stdtypes.html#str.title)

#### اولین حرف هر کلمه را بزرگ می‌کند:

```python
>>> etc_str = "python programming language"
>>> etc_str.title()
'Python Programming Language'
```

> ### [str.strip([chars])](https://docs.python.org/3/library/stdtypes.html#str.strip)

#### حذف فاصله‌ها یا کاراکترهای مشخص از ابتدا و انتهای رشته:

```python
>>> etc_str = "   Hello World   "
>>> etc_str.strip()
'Hello World'

>>> etc_str = "***Hello World***"
>>> etc_str.strip('*')
'Hello World'
```

> ### [str.lstrip()](https://docs.python.org/3/library/stdtypes.html#str.lstrip)

#### حذف فاصله‌ها از ابتدای رشته (سمت چپ):

```python
>>> etc_str = "   Hello World   "
>>> etc_str.lstrip()
'Hello World   '
```

> ### [str.rstrip()](https://docs.python.org/3/library/stdtypes.html#str.rstrip)

#### حذف فاصله‌ها از انتهای رشته (سمت راست):

```python
>>> etc_str = "   Hello World   "
>>> etc_str.rstrip()
'   Hello World'
```

> ### [str.split(sep=None)](https://docs.python.org/3/library/stdtypes.html#str.split)

#### رشته را بر اساس جداکننده مشخص، به لیستی از زیررشته‌ها تبدیل می‌کند:

```python
>>> etc_str = "apple,banana,orange"
>>> etc_str.split(',')
['apple', 'banana', 'orange']

>>> etc_str = "Hello World Python"
>>> etc_str.split()  # جداکننده پیش‌فرض: فاصله
['Hello', 'World', 'Python']
```

> ### [str.join(iterable)](https://docs.python.org/3/library/stdtypes.html#str.join)

#### اعضای یک مجموعه (مثل لیست) را با رشته فعلی به هم متصل می‌کند:

```python
>>> etc_list = ['apple', 'banana', 'orange']
>>> ', '.join(etc_list)
'apple, banana, orange'

>>> '-'.join(['2024', '01', '15'])
'2024-01-15'
```

> ### [str.replace(old, new)](https://docs.python.org/3/library/stdtypes.html#str.replace)

#### زیررشته مورد نظر را با رشته جدید جایگزین می‌کند:

```python
>>> etc_str = "Hello World, Hello Python"
>>> etc_str.replace('Hello', 'Hi')
'Hi World, Hi Python'

>>> etc_str.replace('Hello', 'Hi', 1)  # فقط اولین مورد
'Hi World, Hello Python'
```

> ### [str.find(sub)](https://docs.python.org/3/library/stdtypes.html#str.find)

#### اندیس اولین رخداد زیررشته را برمی‌گرداند (در صورت عدم وجود: 1-):

```python
>>> etc_str = "Python Programming"
>>> etc_str.find('Prog')
7
>>> etc_str.find('Java')
-1
```

> ### [str.index(sub)](https://docs.python.org/3/library/stdtypes.html#str.index)

#### مشابه find اما در صورت عدم وجود خطا می‌دهد:

```python
>>> etc_str = "Python Programming"
>>> etc_str.index('Prog')
7
>>> etc_str.index('Java')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: substring not found
```

> ### [str.count(sub)](https://docs.python.org/3/library/stdtypes.html#str.count)

#### تعداد رخدادهای زیررشته را شمارش می‌کند:

```python
>>> etc_str = "Hello Hello World"
>>> etc_str.count('Hello')
2
>>> etc_str.count('l')
5
```

> ### [str.startswith(prefix)](https://docs.python.org/3/library/stdtypes.html#str.startswith)

#### بررسی می‌کند که رشته با پیشوند مشخص شروع می‌شود یا خیر:

```python
>>> etc_str = "Python Programming"
>>> etc_str.startswith('Python')
True
>>> etc_str.startswith('Java')
False
```

> ### [str.endswith(suffix)](https://docs.python.org/3/library/stdtypes.html#str.endswith)

#### بررسی می‌کند که رشته با پسوند مشخص پایان می‌یابد یا خیر:

```python
>>> etc_str = "document.pdf"
>>> etc_str.endswith('.pdf')
True
>>> etc_str.endswith('.txt')
False
```

> ### [str.isdigit()](https://docs.python.org/3/library/stdtypes.html#str.isdigit)

#### بررسی می‌کند که آیا همه کاراکترها عدد هستند یا خیر:

```python
>>> etc_str = "12345"
>>> etc_str.isdigit()
True

>>> etc_str = "123abc"
>>> etc_str.isdigit()
False
```

> ### [str.isalpha()](https://docs.python.org/3/library/stdtypes.html#str.isalpha)

#### بررسی می‌کند که آیا همه کاراکترها حرف هستند یا خیر:

```python
>>> etc_str = "Python"
>>> etc_str.isalpha()
True

>>> etc_str = "Python3"
>>> etc_str.isalpha()
False
```

> ### [str.isalnum()](https://docs.python.org/3/library/stdtypes.html#str.isalnum)

#### بررسی می‌کند که آیا همه کاراکترها حرف یا عدد هستند:

```python
>>> etc_str = "Python3"
>>> etc_str.isalnum()
True

>>> etc_str = "Python 3"
>>> etc_str.isalnum()  # فاصله مجاز نیست
False
```

> ### [str.center(width)](https://docs.python.org/3/library/stdtypes.html#str.center)

#### رشته را در مرکز با عرض مشخص قرار می‌دهد:

```python
>>> etc_str = "Python"
>>> etc_str.center(20)
'       Python       '

>>> etc_str.center(20, '*')
'*******Python*******'
```

> ### [str.zfill(width)](https://docs.python.org/3/library/stdtypes.html#str.zfill)

#### رشته را با صفر از سمت چپ پر می‌کند تا به عرض مشخص برسد:

```python
>>> etc_str = "42"
>>> etc_str.zfill(5)
'00042'

>>> etc_str = "-42"
>>> etc_str.zfill(5)
'-0042'  # علامت منفی حفظ می‌شود
```

> ### [str.swapcase()](https://docs.python.org/3/library/stdtypes.html#str.swapcase)

#### حروف بزرگ را کوچک و حروف کوچک را بزرگ می‌کند:

```python
>>> etc_str = "Python Programming"
>>> etc_str.swapcase()
'pYTHON pROGRAMMING'
```

### بررسی وجود زیررشته در رشته

```python
>>> etc_str = "Python Programming"
>>> 'Python' in etc_str
True
>>> 'Java' in etc_str
False
```

### طول رشته

```python
>>> etc_str = "Python"
>>> len(etc_str)
6
```

## جمع‌بندی سریع متدهای `str`

| متد        | کاربرد                               |
|------------|--------------------------------------|
| upper      | تبدیل به حروف بزرگ                   |
| lower      | تبدیل به حروف کوچک                   |
| capitalize | بزرگ کردن حرف اول                    |
| title      | بزرگ کردن حرف اول هر کلمه            |
| strip      | حذف فاصله از ابتدا و انتها           |
| split      | تبدیل رشته به لیست                   |
| join       | تبدیل لیست به رشته                   |
| replace    | جایگزینی زیررشته                     |
| find       | پیدا کردن اندیس (یا 1-)              |
| count      | شمارش تعداد تکرار                    |
| startswith | بررسی شروع با پیشوند                 |
| endswith   | بررسی پایان با پسوند                 |
| isdigit    | بررسی عدد بودن                       |
| isalpha    | بررسی حرف بودن                       |
| isalnum    | بررسی حرف یا عدد بودن                |
| center     | مرکزچین کردن                         |
| zfill      | پر کردن با صفر از چپ                 |
| swapcase   | جابجایی بزرگی و کوچکی حروف           |