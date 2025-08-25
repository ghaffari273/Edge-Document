# تخصیص شماره به کاربر زیرمجوعه

این API به شما امکان تخصیص شماره به کاربر زیرمجموعه خود را می‌دهد.

دقت داشته باشید که این API صرفا برای ریسلرهای سامانه در دسترس بوده و کاربران عادی به آن دسترسی ندارند.

## 📍 لینک دسترسی

```
POST {base_url}/api/numbers/assign
```

## 🧾 هدرها

| کلید          | مقدار               |
|---------------|---------------------|
| Authorization | توکن یا کلید دسترسی |
| Content-Type  | application/json    |

## 📤 بدنه درخواست

```json
{
  "number_id": 10,
  "target_user_id": 123,
  "number": "+983000505",
  "target_user": "testuser",
  "send": true,
  "gets": false
}
```

## 📝 پارامترها

| پارامتر        | نوع     | اجباری | توضیحات                                                       |
|----------------|---------|--------|---------------------------------------------------------------|
| number_id      | integer | بله    | شناسه شماره‌ای که قرار است به کاربر تخصیص داده شود.           |
| target_user_id | integer | بله    | شناسه کاربری که شماره به او تخصیص داده خواهد شد.              |
| number         | string  | خیر    | شماره در فرمت E.164 که قرار است تخصیص داده شود.               |
| target_user    | string  | خیر    | نام کاربری  که شماره به او تخصیص داده خواهد شد.               |
| send           | boolean | بله    | اگر `true` باشد، کاربر می‌تواند با این شماره پیام ارسال کند.  |
| gets           | boolean | بله    | اگر `true` باشد، کاربر می‌تواند با این شماره پیام دریافت کند. |

## 📝 نکات

- `number_id` در صورتی که `number` ارائه نشده باشد اجباری است.
- `target_user_id` در صورتی که `target_user` ارائه نشده باشد اجباری است.
- `number` در صورتی که `number_id` ارائه نشده باشد اجباری است.
- `target_user` در صورتی که `target_user_id` ارائه نشده باشد اجباری است.
- `gets` کاربر قادر خواهد بود پیام‌های ورودی این شماره را دریافت/مشاهده کند. معمولاً برای شماره‌های اختصاصی `true` است.

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

## ❌ پاسخ خطا — درخواست نامعتبر (422)

```json
{
  "data": null,
  "meta": {
    "status": false,
    "message": "تکمیل گزینه number id الزامی است (و 1 خطای دیگر)",
    "message_parameters": [],
    "message_code": "400-2",
    "errors": {
      "number_id": [
        "تکمیل گزینه number id الزامی است"
      ],
      "number": [
        "تکمیل گزینه number الزامی است"
      ]
    }
  }
}
```

## ❌ پاسخ خطا — درخواست نامعتبر (400)

```json
{
  "data": null,
  "meta": {
    "status": false,
    "message": "number already assigned to user",
    "message_parameters": [],
    "message_code": "400-1",
    "errors": {}
  }
}
```

## 🧪 نمونه درخواست

```bash
curl --location '{base_url}/api/numbers/assign' \
--header 'Content-Type: application/json' \
--header 'Authorization: Your Apikey/Token' \
--data '{
    "number": "+983000505",
    "target_user": "testuser",
    "send": true,
    "gets": false
}'
```
