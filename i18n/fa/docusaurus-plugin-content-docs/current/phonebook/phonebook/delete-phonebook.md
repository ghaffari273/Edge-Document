# حذف دفترچه تلفن
این API به شما امکان حذف فهرستی از مدخل‌های دفترچه تلفن با استفاده از شناسه‌هایشان را می‌دهد.

## 📍 نقطه پایانی

```
POST {base_url}/api/phonebooks/delete-list
```

## 🧾 هدرها

| کلید | مقدار |
| --- | ----- |
| Authorization | YOUR_TOKEN_HERE |
| Content-Type | application/json |

## 📤 بدنه درخواست

```json
{
  "listPhonebooks": [
    860108
  ]
}
```

## 📝 پارامترها

| پارامتر | نوع | الزامی | توضیحات                                                           |
| --------- | ---- | -------- |-----------------------------------------------------------------------|
| listPhonebooks | array | بله      | آرایه‌ای از شناسه‌های دفترچه تلفن که باید حذف شوند. هر شناسه باید یک عدد صحیح معتبر باشد. |


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
curl --location '{base_url}/api/phonebooks/delete-list' \
--header 'Authorization: Your Apikey/Token' \
--header 'Content-Type: application/json' \
--data '{
    "listPhonebooks": [
        860108
    ]
}'
```
