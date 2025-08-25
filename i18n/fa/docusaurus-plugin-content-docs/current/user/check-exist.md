# بررسی وجود کاربر

این API به شما اجازه می‌دهد تا با نام کاربری، وجود یک کاربر را بررسی کنید. اگر نام کاربری برای ثبت‌نام در دسترس باشد،
پیام موفقیت و در صورت وجود نام کاربری یا مشکلات اعتبارسنجی، پیام خطا برمی‌گرداند.

## 📍 نقطه پایانی

```
POST {base_url}/api/user/check_exist
```

## 🧾 هدرهای درخواست

| کلید          | مقدار               |
|---------------|---------------------|
| Authorization | توکن یا کلید دسترسی |
| Content-Type  | application/json    |

## 📤 بدنه درخواست

```json
{
  "user_name": "username"
}
```

## 📝 پارامترها

| پارامتر  | نوع    | الزامی | توضیحات                                         |
|----------|--------|--------|-------------------------------------------------|
| username | string | بله    | نام کاربری  که می‌خواهید وجود آن را بررسی کنید. |

## ✅ پاسخ موفق

```json
{
  "data": null,
  "meta": {
    "status": true,
    "message": "این نام کاربری قابل ثبت می باشد",
    "message_parameters": [],
    "message_code": "200-1"
  }
}
```

## ❌ پاسخ خطا — توکن نامعتبر یا منقضی (401)

```json
{
  "data": null,
  "meta": {
    "status": false,
    "message": "اطلاعات وارد شده صحیح نمی باشد",
    "message_parameters": [],
    "message_code": "400-1",
    "errors": {}
  }
}
```

## ❌ پاسخ خطا — کاربر از قبل وجود دارد (409)

```json
{
  "data": null,
  "meta": {
    "status": false,
    "message": "نام کاربری وارد شده قبلا ثبت شده است",
    "message_parameters": [],
    "message_code": "400-1",
    "errors": {}
  }
}
```

## ❌ پاسخ خطا — فیلدهای الزامی ناموجود (422)

```json
{
  "data": null,
  "meta": {
    "status": false,
    "message": "نام کاربری باید شامل حروف انگلیسی بزرگ و کوچک و اعداد و - و . باشد",
    "message_parameters": [],
    "message_code": "400-1",
    "errors": {}
  }
}
```

## 🧪 نمونه درخواست

```bash
curl --location '{base_url}/api/user/check_exist' \
--header 'Authorization: Your Apikey' \
--header 'Content-Type: application/json' \
--data '{
    "user_name": "username"
}'
```
