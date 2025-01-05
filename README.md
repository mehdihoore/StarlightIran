# ثبات: موتور جستجوی هوشمند با امکانات نجومی

ثبات یک برنامه قدرتمند بر پایه Cloudflare Worker است که به منظور ارائه یک تجربه جستجوی جامع و ارائه اطلاعات مفید در یک مکان واحد طراحی شده است.

## ویژگی‌ها

-   **جستجوی چند موتوره:** ثبات نتایج جستجو را از موتورهای مختلف جمع‌آوری می‌کند، از جمله:
    -   گوگل (جستجوی سفارشی)
    -   داک‌داک‌گو (وب و اخبار)
    -   ویکی‌پدیا
    -   دانشنامه فلسفه استنفورد (SEP)
    -   کوانت
    -   جستجوی مقالات نیویورک تایمز

-   **پاسخ‌های مبتنی بر هوش مصنوعی:**
    -   از مدل جمینای گوگل برای تولید پاسخ‌های جامع و دقیق به پرسش‌های کاربران استفاده می‌کند، و به طور مستقیم به نتایج جستجو ارجاع می‌دهد.
    -   حداقل یک لینک مرتبط با سوال کاربر در پاسخ اضافه می‌کند.
    -   بر ارائه اطلاعات دقیق تأکید دارد و از افشای ماهیت هوش مصنوعی خود در پاسخ‌ها خودداری می‌کند.

-   **اطلاعات تاریخ و زمان:**
    -   تاریخ و زمان فعلی را در تقویم‌های میلادی و شمسی (ایرانی) نمایش می‌دهد.
    -   رویدادهای امروز در تقویم ایرانی را نشان می‌دهد.

-   **تصویر نجومی روز ناسا (APOD):**
    -   تصویر نجومی روز ناسا را دریافت و نمایش می‌دهد.
    -   توضیحات تصویر را به دو زبان انگلیسی و فارسی ارائه می‌دهد (ترجمه با استفاده از جمینای).

-   **نمای سیارات:**
    -   نمای واقعی سیارات قابل مشاهده در آسمان تهران، ایران را با استفاده از داده‌های `api.visibleplanets.dev` ارائه می‌دهد.
    -   نام سیارات را به فارسی نمایش می‌دهد.

-   **تولید تصویر:**
    -   از مدل `@cf/runwayml/stable-diffusion-v1-5` برای تولید تصاویر بر اساس توضیحات متنی کاربران استفاده می‌کند.

-   **تغییر تم:**
    -   به کاربران اجازه می‌دهد بین تم‌های روشن و تاریک جابجا شوند.

-   **نوار ناوبری:**
    -   دسترسی سریع به سایر منابع مفید مانند لیست VPN، جداول اشتال، اخبار آب و هوا، چت‌بات هوش مصنوعی، چت‌بات فلسفی و نقشه آسمان شب را فراهم می‌کند.

-   **عملکرد پروکسی:**
    -   شامل یک نقطه پایانی پروکسی (`/proxy`) برای دور زدن محدودیت‌ها و دسترسی به وب‌سایت‌هایی است که ممکن است مسدود شده باشند.

## راه‌اندازی

1. **پیش‌نیازها:**
    -   حساب Cloudflare.
    -   نصب و پیکربندی `wrangler` CLI.

2. **کلون کردن مخزن:**

    ```bash
    git clone https://github.com/mehdihoore/StarlightIran.git
    cd StarlightIran
    ```

3. **متغیرهای محیطی:**
    -   یک فایل `.dev.vars` در ریشه پروژه خود ایجاد کنید.
    -   متغیرهای محیطی زیر را اضافه کنید (با کلیدهای واقعی خود جایگزین کنید):

    ```
    GOOGLE_API_KEY = "YOUR_GOOGLE_API_KEY"
    GOOGLE_CSE_ID = "YOUR_GOOGLE_CSE_ID"
    GEMINI_API_KEY = "YOUR_GEMINI_API_KEY"
    NASA_API_KEY = "YOUR_NASA_API_KEY"
    NYT_API_KEY = "YOUR_NYT_API_KEY"
    ```

    -   **مهم:** برای استفاده از سرویس‌های مربوطه، باید کلیدهای API را از گوگل، جمینای، ناسا و نیویورک تایمز دریافت کنید.

4. **نصب وابستگی‌ها:**

    ```bash
    npm install
    ```

5. **استقرار در Cloudflare:**

    ```bash
    wrangler deploy
    ```
6.  **پروکسی:** برای دسترسی به یک وب‌سایت از طریق پروکسی، از نقطه پایانی `/proxy` با پارامتر `url` استفاده کنید:

    ```
    https://your-worker-url.workers.dev/proxy?url=https://www.example.com
    ```

    `https://your-worker-url.workers.dev` را با URL  Cloudflare Worker خود و `https://www.example.com` را با وب‌سایتی که می‌خواهید به آن دسترسی داشته باشید، جایگزین کنید.
## نحوه استفاده

-   **جستجو:** عبارت مورد نظر خود را در نوار جستجو وارد کرده و روی "جستجو" کلیک کنید. نتایج از چندین موتور جستجو نمایش داده می‌شود و هوش مصنوعی یک پاسخ جامع تولید خواهد کرد.
-   **تاریخ و زمان:** تاریخ و زمان فعلی در تقویم‌های میلادی و شمسی به طور برجسته نمایش داده می‌شود، همراه با رویدادهای ایرانی آن روز.
-   **تصویر نجومی روز ناسا:** تصویر نجومی روز ناسا را مشاهده کنید، همراه با توضیحات به زبان‌های انگلیسی و فارسی. برای جابجایی بین زبان‌ها، روی زبان مورد نظر کلیک کنید.
-   **سیارات:** ببینید کدام سیارات در حال حاضر در آسمان تهران قابل مشاهده هستند. نمای سیارات هر 5 دقیقه به‌روزرسانی می‌شود.
-   **تولید تصویر:** یک توضیح متنی وارد کنید تا تصویری با استفاده از Stable Diffusion تولید شود.
-   **تم:** با استفاده از دکمه گوشه بالا سمت چپ، بین تم‌های روشن و تاریک جابجا شوید.
-   **ناوبری:** از نوار ناوبری در بالا برای دسترسی به سایر خدمات مانند لیست VPN، جداول اشتال، اخبار آب و هوا، چت‌بات هوش مصنوعی، چت‌بات فلسفی و نقشه آسمان شب استفاده کنید.
-   **پروکسی:** برای دسترسی به یک وب‌سایت از طریق پروکسی، از نقطه پایانی `/proxy` با پارامتر `url` استفاده کنید:

