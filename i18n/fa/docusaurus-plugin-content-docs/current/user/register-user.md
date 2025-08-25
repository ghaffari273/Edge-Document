# ثبت کاربر

این API به شما اجازه می‌دهد تا کاربر جدیدی را به عنوان زیرمجموعه خود ثبت کنید.

## 📍 لینک دسترسی

```
POST {base_url}/api/user/create
```

## 🧾 هدرها

| کلید          | مقدار               |
|---------------|---------------------|
| Authorization | توکن یا کلید دسترسی |
| Content-Type  | application/json    |

## 📤 بدنه درخواست

```json
{
  "user_name": "newuser",
  "password": "StrongPassword123!",
  "national_code": "1234567890",
  "mobile_number": "09120000000",
  "birth_date": "1990-01-01",
  "acl_id": 12345
}
```

## 📝 پارامترها

| پارامتر       | نوع     | الزامی | توضیحات                 |
|---------------|---------|--------|-------------------------|
| username      | string  | بله    | نام کاربری منحصر به فرد |
| password      | string  | بله    | کلمه عبور کاربر         |
| national_code | string  | بله    | کد ملی کاربر            |
| mobile_number | string  | بله    | شماره موبایل کاربر      |
| birth_date    | string  | بله    | تاریخ تولد کاربر        |
| acl_id        | integer | بله    | شناسه نقش ACL           |

⚠️ نکته:

- در صورتی که شماره موبایل وارد شده متعلق به کد ملی وارد شده نباشد، حساب کاربری فعال نخواهد شد.

- تغییر کد ملی کاربر بعد از ثبت نام به هیچ عنوان امکانپذیر نبوده و درصورت اشتباه وارد نمودن آن، مستلزم ساخت حساب کاربری جدید است

## ✅ پاسخ موفق

```json
{
  "data": null,
  "meta": {
    "status": true,
    "message": "انجام شد",
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

## 🧪 مثال درخواست

```bash
curl --location '{base_url}/api/user/create' \
--header 'Authorization: Your Apikey' \
--header 'Content-Type: application/json' \
--data '{
    "user_name": "username",
    "password": "q8?6Man96Q]%U|q",
    "national_code": "1111111111",
    "mobile_number": "0912000000",
    "birth_date": "1990-01-01",
    "acl_id": 12345
}'
```
