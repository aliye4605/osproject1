مراحل انجام پروژه:
1.	نصب VMware برای پشتیبانی از لینوکس
2.	نصب VScode و Google Chrome در ماشین مجازی
3.	نصب یکسری Extention ها در Visual Studio Code برای اجرای کد به زبان C
4.	شروع کد زنی

نحوه پیاده سازی:
توابع processFolder() و process()از نظر عملکرد مشابه هستند. آنها هر دو ساختار دایرکتوری را به صورت بازگشتی طی می کنند و فایل ها و دایرکتوری ها را پردازش می کنند. آنها داده های مانیتورینگ m1 را با اطلاعات مربوط به هر فایلی که با آنها مواجه می شوند به روز می کنند.
در processFolder() داریم:
DIR *dir;: اشاره گر را به جریان دایرکتوری اعلام می کند.
struct dirent *entry;: یک اشاره گر به ساختاری که نشان دهنده ورودی دایرکتوری است را اعلام می کند.
struct stat fileStat;: ساختاری را برای نگهداری اطلاعات وضعیت فایل اعلام می کند.
char *folderPath = (char *)path;: مسیر آرگومان void* را به یک char* که نشان دهنده مسیر پوشه است ارسال می کند.
dir = opendir(folderPath): دایرکتوری مشخص شده توسط folderPath را باز می کند و جریان آن را به نشانگر dir اختصاص می دهد. این تابع در صورت موفقیت یک اشاره گر به جریان دایرکتوری یا در صورت شکست NULL برمی گرداند.
………..
 pid_t pid: یک متغیر pid از نوع pid_t را اعلام می کند که یک نوع داده برای شناسه های فرآیند است.
fork(): یک فرآیند جدید با کپی کردن فرآیند فراخوانی ایجاد می کند. پس از یک fork() موفق، دو پردازش (والد و فرزند) ایجاد می‌شود و هر دو از نقطه فراخوانی fork() به اجرا ادامه می‌دهند. پردازش فرزند یک کپی از حافظه پردازش والد دریافت می کند.

نحوه اجرای کد:
ابتدا به برنامه مسیری را میدهیم سپس کد چک می کند اگر فولدری باشد، آن را باز می کند با کمک نخ ها و بعد از آنها برای جستجو فایل ها استفاده می کند. لایه اول بررسی با فرآیند و لایه های داخلی با نخ چک می شود. 




