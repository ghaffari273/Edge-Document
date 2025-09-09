# بروزرسانی دفترچه تلفن
این API به شما امکان بروزرسانی یک مدخل موجود در دفترچه تلفن با استفاده از شناسه آن را می‌دهد.

## 📍 نقطه پایانی

```
PUT {base_url}/api/phonebooks/{phonebook_id}
```

## 🧾 هدرها

| کلید | مقدار |
| --- | ----- |
| Authorization | YOUR_TOKEN_HERE |
| Content-Type | application/json |

## 📤 بدنه درخواست

```json
{
  "title": "title",
  "options": [
    "123"
  ]
}
```

## 📝 پارامترها

| پارامتر | نوع | الزامی | توضیحات                                                         |
| --------- | ---- |----------|---------------------------------------------------------------------|
| phonebook_id | string | بله      | شناسه منحصر به فرد مدخل دفترچه تلفنی که می‌خواهید بروزرسانی کنید.    |
| title     | string | خیر       | عنوان مدخل دفترچه تلفن. حداکثر طول 200 کاراکتر. |
| options   | array  | خیر       | آرایه‌ای از شناسه‌های گزینه‌ها که به مدخل دفترچه تلفن مرتبط می‌شوند.   |

## ✅ پاسخ موفق

```json
{
  "data": null,
  "meta": {
    "status": true,
    "message": "انجام شد",
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
curl --location --globoff --request PUT '{base_url}/api/phonebooks/{phonebook_id}' \
--header 'Authorization: Your Apikey/Token' \
--header 'Content-Type: application/json' \
--data '{
    "title": "title",
    "options": [
        "123"
    ]
}'
```
