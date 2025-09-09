# نمونه وارد کردن شماره دفترچه تلفن
این API به شما امکان دریافت نمونه‌ای برای وارد کردن شماره در یک دفترچه تلفن خاص را می‌دهد. این برای درک فرمت مورد نیاز برای وارد کردن شماره‌ها مفید است.

## 📍 نقطه پایانی

```
GET {base_url}/api/phonebooks/{phonebook_id}/import/get-sample
```

## 🧾 هدرها

| کلید | مقدار |
| --- | ----- |
| Authorization | YOUR_TOKEN_HERE |
| Content-Type | application/json |

## 📝 پارامترها

| پارامتر | نوع | الزامی | توضیحات                                                          |
| --------- | ---- | -------- |----------------------------------------------------------------------|
| phonebook_id | string | بله | شناسه دفترچه تلفن |

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
curl --location '{base_url}/api/phonebooks/12345/import/get-sample' \
--header 'Content-Type: application/json' \
--header 'Authorization: API TOKEN'
```
