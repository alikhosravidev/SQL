# محدودیت‌های CONSTRAINT در SQL: 🚀

**راهی برای حفظ یکپارچگی داده‌ها**

اگر با پایگاه داده‌ها و SQL کار کرده باشید، حتماً بارها با کلمه‌ی CONSTRAINT برخورد کرده‌اید. این کلمه که به معنای “محدودیت” است، نقش بسیار مهمی در طراحی و مدیریت جداول پایگاه داده دارد.

این مفهوم شاید کمی گنگ و پیچیده به نظر برسه، اما در اینجا تصمیم گرفتم آنچه در این مورد یاد گرفته‌ام را با شما به اشتراک بگذارم. 😊

به زبان ساده، CONSTRAINT قوانینی است که برای حفظ یکپارچگی و کیفیت داده‌ها در جداول پایگاه داده تعریف می‌شود. این قوانین تضمین می‌کنند که داده‌های وارد شده به جدول معتبر باشند و از ورود داده‌های نامعتبر جلوگیری می‌کنند.

## انواع CONSTRAINT در SQL 📌

### ✅ NOT NULL

این محدودیت تضمین می‌کند که یک ستون نمی‌تواند مقدار خالی (NULL) داشته باشد. این به شما کمک می‌کند تا اطمینان حاصل کنید که اطلاعات حیاتی همیشه در دسترس هستند.

```sql
CREATE TABLE Users (
    ID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    Email VARCHAR(100) NOT NULL
);
```


### ✅ UNIQUE

این محدودیت تضمین می‌کند که تمام مقادیر موجود در یک ستون (یا ترکیبی از چند ستون) یکتا باشند. این به جلوگیری از ورود داده‌های تکراری کمک می‌کند.

```sql
CREATE TABLE Users (
    ID INT PRIMARY KEY,
    Email VARCHAR(100) UNIQUE,
    Username VARCHAR(50) UNIQUE
);
```


### ✅ PRIMARY KEY

این محدودیت ترکیبی از NOT NULL و UNIQUE است و تضمین می‌کند که هر رکورد در جدول دارای یک شناسه‌ی یکتا باشد. هر جدول باید یک PRIMARY KEY داشته باشد.

```sql
CREATE TABLE Products (
    ID INT PRIMARY KEY,
    ProductName VARCHAR(100) NOT NULL,
    Price DECIMAL(10, 2) NOT NULL
);
```


### ✅ FOREIGN KEY

این محدودیت برای ایجاد ارتباط بین دو جدول استفاده می‌شود. FOREIGN KEY به یک PRIMARY KEY یا UNIQUE در جدول دیگر اشاره می‌کند و تضمین می‌کند که داده‌های مرتبط معتبر باشند.

```sql 
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    FOREIGN KEY (CustomerID) REFERENCES Customers(ID)
);
```


### ✅ CHECK

این محدودیت به شما اجازه می‌دهد یک شرط خاص برای مقدار ستون تعریف کنید. این به شما کمک می‌کند تا اطمینان حاصل کنید که داده‌های وارد شده با شرایط خاصی سازگار هستند.

```sql
CREATE TABLE Products (
    ID INT PRIMARY KEY,
    Price DECIMAL(10, 2) CHECK (Price > 0)
);
```


### ✅ DEFAULT

این محدودیت به شما اجازه می‌دهد یک مقدار پیش‌فرض برای یک ستون تعریف کنید. اگر کاربر مقداری برای آن ستون وارد نکند، مقدار پیش‌فرض استفاده می‌شود.

```sql
CREATE TABLE Users (
    ID INT PRIMARY KEY,
    CreatedAt DATETIME DEFAULT GETDATE()
);
```


### ✅ ON DELETE / ON UPDATE CASCADE

این محدودیت‌ها در ارتباط با FOREIGN KEY استفاده می‌شوند و مشخص می‌کنند که هنگام حذف یا به‌روزرسانی رکورد مرتبط در جدول اصلی، چه اتفاقی برای رکوردهای مرتبط در جدول فرعی بیفتد.

```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    FOREIGN KEY (CustomerID) REFERENCES Customers(ID) ON DELETE CASCADE
);
```


### چرا CONSTRAINT مهم است؟ 🤔

به‌طور کلی، استفاده از CONSTRAINT‌ها به شما کمک می‌کند:

- یکپارچگی داده‌ها را حفظ کنید.
- از ورود داده‌های نامعتبر جلوگیری کنید.
- کیفیت داده‌ها را تضمین کنید.
- روابط بین جداول را مدیریت کنید.
  در نهایت، این محدودیت‌ها نقش کلیدی در طراحی پایگاه داده‌های حرفه‌ای ایفا می‌کنند و به شما کمک می‌کنند تا سیستمی پایدار و قابل‌اعتماد داشته باشید. 💪

