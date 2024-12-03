# Optimize-search-time 
## پیش‌نیازها
- نیاز به کتابخانه `time`

## خلاصه ای درباره پروژه
این پروژه شامل پیاده‌سازی و مقایسه چندین الگوریتم جستجو برای پیدا کردن نام کاربری در یک پایگاه داده است. در این پروژه از سه الگوریتم جستجو استفاده شده است: جستجوی خطی، جستجوی دودویی و جستجو با جدول هش (Hash Table). 

هدف این است که عملکرد هر الگوریتم را از نظر زمان اجرا و کارایی بررسی کنیم.

 فایل ها:
 - main.py
 - Hash.py
 - Chart.py

## main.py
حاوی سه تابع که جستجو خطی و دودویی و خواندن دیتابیس در آنها پیاده سازی شده است 
1. **def linear_search:**

2. **def binary_search:**

3. **def read_database_from_file:**

## نحوه کار توابع

## 1. **def linear_search**:

تابع `linear_search` یک الگوریتم جستجوی خطی (Linear Search) است که برای پیدا کردن یک نام کاربری خاص در یک لیست از نام‌های کاربری استفاده می‌شود. نحوه کار این تابع به شرح زیر است:
### پارامترها:

- database:.یک لیست از نام‌های کاربری (مجموعه‌ای از داده‌ها که در آن جستجو انجام می‌شود)
- target: .نام کاربری مورد نظر برای جستجو

### توضیح عملکرد تابع:
یک تابع for ساده است که از تابع `enumerate` در ان استفاده شده تا علاوه بر مقدار هر آیتم (که در اینجا نام کاربری است)، اندیس (شماره موقعیت) آن را نیز فراهم می‌کند.
 اگر پیدا شد آن را برمیگرداند و اگر پیدا نشد -1 بر میگرداند

## 2. **def binary_search**:
تابع `binary_search` یک الگوریتم جستجوی دودویی (Binary Search) است که برای پیدا کردن یک نام کاربری در یک لیست از نام‌های کاربری مرتب شده استفاده می‌شود. در این الگوریتم، جستجو به طور کارآمد در میانه لیست انجام می‌شود و بسته به مقایسه با مقدار میانه، نصف لیست را کنار می‌گذارد تا جستجو سریع‌تر انجام شود.

### پارامترها:
- database:.لیستی از نام‌های کاربری مرتب‌شده.
- target: نام کاربری مورد نظر برای جستجو.

### توضیح عملکرد تابع:
1. مقداردهی اولیه: در ابتدا دو متغیر `left` و `right` به ترتیب برابر با ابتدا و انتهای لیست (یعنی ۰ و طول لیست - ۱) تنظیم می‌شوند. این دو متغیر مرزهای جستجو را تعیین می‌کنند.
2. حلقه جستجو: تابع وارد یک حلقه `while` می‌شود که تا زمانی که `left` از `right` کوچکتر یا مساوی باشد ادامه می‌یابد. این به این معنی است که هنوز بخشی از لیست برای جستجو باقی مانده است.
3. : در هر تکرار حلقه، ابتدا موقعیت میانه (اندیس mid) لیست محاسبه می‌شود با فرمول:
#### **mid = (left + right) // 2**
این موقعیت نشان‌دهنده میانه بخش فعلی لیست است.
4. مقایسه میانه با target:
* اگر مقدار در میانه `(database[mid])` برابر با `target` باشد، نام کاربری پیدا شده و اندیس آن `(مقدار mid)` برگردانده می‌شود.
* اگر مقدار میانه کوچک‌تر از `target` باشد، یعنی `target` باید در نیمی از لیست که در سمت راست میانه قرار دارد، باشد. بنابراین، مقدار `left` به` mid + 1` تغییر می‌کند تا جستجو در نیمه راست ادامه یابد.
* اگر مقدار میانه بزرگ‌تر از `target` باشد، یعنی `target` باید در نیمی از لیست که در سمت چپ میانه قرار دارد، باشد. بنابراین، مقدار `right` به `mid - 1` تغییر می‌کند تا جستجو در نیمه چپ ادامه یابد.

## 3. **def read_database_from_file**:
نام های کاربری را از یک فایل میخواند و آنها را به صورت لیست برمیگرداند.
##  نحوه استفاده از توابع 
برای استفاده از این توابع در خود فایل بعد از توابع مقادیر(متغیر) مورد نیاز نوشته شده است که برای هر خط، کامنت مورد نظر برای توضیح مختصر گذاشته شده است

فقط کافی است نام کاربری مورد نظر خودتون رو داخل مقدار `target_username` قرار دهید
```python
target_username = "admin"
```

## نحوه محاسبه زمان اجرا
برای محاسبه زمان اجرا ما از کتابخانه `time` استفاده میکنیم. نمونه کد نحوه محاسبه:
```python
# Measure execution time
start_time_linear_search = time.time()
result_linear_search = linear_search(database, target_username)
end_time_linear_search = time.time()
print(f"Username in linear_search '{target_username}' found at index {result_linear_search}.")
```
به این صورت میتوانیم زمانی که شروع و پایان این کد صرف شده را پیدا کنیم

## جمع بندی
الگوریتم جستجوی دودویی (Binary Search) به طور مؤثر با تقسیم مرتب لیست به دو نیمه، جستجو را سریع‌تر انجام می‌دهد. این الگوریتم به طور خاص فقط بر روی لیست‌های مرتب شده قابل استفاده است. در هر مرحله، نیمی از لیست که نام کاربری هدف در آن قرار ندارد، کنار گذاشته می‌شود و جستجو در نیمه باقی‌مانده ادامه می‌یابد. این باعث می‌شود که زمان اجرای آن بسیار سریع‌تر از جستجوی خطی باشد (زمان اجرای
O(logn) به جای
O(n)).

<br><br><br><br><br><br>
## Hash.py
دارای سه تابع مختلف دارد که همگی به طور مرتبط با جستجو و پردازش نام‌های کاربری در یک پایگاه داده عمل می‌کنند. در ادامه هر تابع به تفصیل توضیح داده می‌شود:

### 1. تابع create_hash_table

این تابع یک جدول هش (hash table) ایجاد می‌کند که از لیستی از نام‌های کاربری (username) به عنوان ورودی استفاده می‌کند. در این جدول هش، نام‌های کاربری به اندیس‌های خود در لیست مرتبط هستند.

### پارامترها:
* database: لیستی از نام‌های کاربری

### توضیح عملکرد:
* یک دیکشنری (hash_table) خالی ایجاد می‌شود.

* سپس با استفاده از حلقه for، هر نام کاربری در لیست database با اندیس آن به جدول هش اضافه می‌شود.

* در پایان، دیکشنری حاوی نام‌های کاربری به همراه اندیس‌هایشان باز می‌گردد.
<br><br>
### 2. تابع read_database_from_file

این تابع نام‌های کاربری را از یک فایل متنی می‌خواند و آن‌ها را به صورت یک لیست باز می‌گرداند.

### پارامترها:
* `file_path:` مسیر فایل متنی که نام‌های کاربری در آن ذخیره شده است.
### توضیح عملکرد:
* فایل به صورت خواندنی (`'r'`) باز می‌شود.

* سپس تمام خطوط فایل خوانده می‌شود و برای هر خط، فاصله‌های اضافی (مانند فاصله‌های قبل و بعد از هر نام کاربری) حذف می‌شود.

* در نهایت یک لیست از نام‌های کاربری تولید و باز می‌گردد.

### 3. تابع search_in_hash_table

این تابع برای جستجو در جدول هش ایجاد شده است تا نام کاربری خاصی را پیدا کند و اندیس آن را برگرداند.

### پارامترها::
* `hash_table` جدول هش (دیکشنری) که نام‌های کاربری و اندیس‌هایشان را در خود دارد.

* `target:` نام کاربری مورد نظر برای جستجو.
### توضیح عملکرد:
* تابع از متد `.get()` استفاده می‌کند که به صورت امن در دیکشنری جستجو می‌کند.

* اگر `target` در جدول هش موجود باشد، اندیس آن برمی‌گردد.

* اگر `target` یافت نشود، مقدار پیش‌فرض `-1` باز می‌گردد که نشان‌دهنده عدم یافتن نام کاربری است.

## **مزایا و معایب هش تیبل**

### **مزایا:**:

1. `سرعت بالا:`
دسترسی به داده‌ها در حالت ایده‌آل زمان ثابتی 
O(1) دارد.
2. `ساختار ساده و منعطف:`
استفاده از کلید برای جستجو باعث می‌شود هش تیبل برای داده‌هایی با کلیدهای منحصر به فرد مناسب باشد.
3. `پشتیبانی پیش‌فرض در پایتون:`
ساختار داده `dict` در پایتون بهینه و سریع است.

### **معایب:**
1. `مصرف حافظه بالا:`
به دلیل استفاده از فضای اضافی برای جلوگیری از برخورد کلیدها، حافظه بیشتری نسبت به سایر ساختارها مصرف می‌شود.
2. `برخورد کلیدها (Collisions):`
اگر تابع هش کلیدهای مختلف را به یک مکان نگاشت دهد، زمان جستجو ممکن است از
O(1) به
O(n) افزایش یابد.
3. `عدم ترتیب:`
هش تیبل ترتیب عناصر را حفظ نمی‌کند (مگر در نسخه‌های جدیدتر پایتون که dict ترتیب درج را حفظ می‌کند).
<br><br><br><br>

<br><br><br><br>
# اندازه گیری زمان اجرا

## Linear_search
```python
target_username = "zigzag" 

# Measure execution time
start_time_linear_search = time.time()
result_linear_search = linear_search(database, target_username)
end_time_linear_search = time.time()

print(f"Username in linear_search '{target_username}' found at index {result_linear_search}.")
print(f"Execution time in linear_search: {end_time_linear_search - start_time_linear_search:.6f} seconds")
```

## خروجی:

![Screenshot 2024-12-04 004655.png](img%2FScreenshot%202024-12-04%20004655.png)
## Binary_search
```python
target_username = "zigzag" 

# Measure execution time
start_time_binary_search = time.time()
result_binary_search = binary_search(database, target_username)
end_time_binary_search = time.time()

print(f"Username in binary_search '{target_username}' found at index {result_binary_search }.")
print(f"Execution time in binary_search: {end_time_binary_search - start_time_binary_search:.20f} seconds")
```
## خروجی:
![Screenshot 2024-12-04 004858.png](img%2FScreenshot%202024-12-04%20004858.png)
## Hash
```python
target_username = "zigzag" 

# Create a hash table
start_time = time.time()
hash_table = create_hash_table(database)
end_time = time.time()

# Search for the target username
search_start_time = time.time()
result = search_in_hash_table(hash_table, target_username)
search_end_time = time.time()

print(f"Username '{target_username}' found at index {result}.")

print(f"Hash table creation time: {end_time - start_time:.6f} seconds")
print(f"Search execution time: {search_end_time - search_start_time:.9f} seconds")
```
## خروجی:
![Screenshot 2024-12-04 005353.png](img%2FScreenshot%202024-12-04%20005353.png)

# خلاصه و نتیجه‌گیری
## هش تیبل:

* **زمان ساخت:** 0.093 ثانیه
* **زمان جستجو:** عملاً صفر (خیلی سریع)
* **مزیت اصلی:** جستجوی بسیار سریع (تقریباً
O(1)).
* **هزینه:** زمان اولیه برای ساخت هش تیبل.

## جستجوی خطی:

* **زمان جستجو:** 0.012 ثانیه
* **مزیت:** ساده‌ترین الگوریتم؛ نیاز به پیش‌پردازش ندارد.
* **عیب:** کندترین روش، زمان اجرای
O(n).

## جستجوی دودویی:

* **زمان جستجو:** عملاً صفر (خیلی سریع).
* **مزیت اصلی:** بسیار سریع 
O(logn)) و نیازی به ساختار داده خاص ندارد.
* **هزینه:** نیازمند مرتب‌سازی اولیه.


# نتیجه‌گیری نهایی:

### اگر مرتب‌سازی یا ساختار اولیه داده امکان‌پذیر باشد، جستجوی دودویی و هش تیبل بهترین گزینه‌ها هستند.

### هش تیبل سریع‌ترین جستجو را دارد اما هزینه حافظه بیشتری دارد و به زمان ساخت اولیه نیازمند است.

### اگر پیش‌پردازش ممکن نیست یا داده‌ها کوچک هستند، جستجوی خطی ساده‌ترین گزینه است، هرچند برای داده‌های بزرگ کندتر است.


# پیشنهادات برای بهبود و بهینه‌سازی بیشتر

### بهبود زمان جستجوی خطی:
استفاده از موازی‌سازی: با استفاده از چندین رشته (threads) یا پردازش موازی (multiprocessing)، می‌توان لیست را به بخش‌های کوچک‌تر تقسیم و به صورت هم‌زمان جستجو کرد.

### بهبود جستجوی دودویی:
به‌روزرسانی داده‌ها: اگر داده‌ها مرتب نیستند یا تغییرات مکرر در آن‌ها رخ می‌دهد، استفاده از یک ساختار مرتب خودکار (مانند درخت جستجوی دودویی متوازن یا AVL Tree) می‌تواند به مرتب‌سازی مداوم کمک کند.

### بهبود هش تیبل:
تابع هش بهینه‌تر: استفاده از یک تابع هش مناسب برای داده‌ها (مثلاً hashlib برای کلیدهای پیچیده) می‌تواند برخورد کلیدها را کاهش داده و کارایی را افزایش دهد.

### ساختارهای داده پیشرفته‌تر:

### درخت B یا درخت B+:
برای پایگاه‌های داده یا فایل‌های بسیار بزرگ، استفاده از این درخت‌ها می‌تواند جستجوی سریع‌تری را روی دیسک فراهم کند.
