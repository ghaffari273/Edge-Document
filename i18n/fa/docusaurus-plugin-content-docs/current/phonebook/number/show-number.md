# نمایش شماره دفترچه تلفن
این API به شما امکان دریافت جزئیات یک مخاطب خاص دفترچه تلفن با استفاده از شناسه منحصر به فرد آن را می‌دهد. می‌توانید از این نقطه پایانی برای دریافت اطلاعاتی مانند نام، شماره، ایمیل و برچسب‌های مرتبط با مخاطب استفاده کنید.

## 📍 نقطه پایانی

```
GET {base_url}/api/phonebooks/numbers/contact-list/{contact_id}
```

## 🧾 هدرها

| کلید | مقدار |
| --- | ----- |
| Authorization | YOUR_TOKEN_HERE |
| Content-Type | application/json |

## 📝 پارامترها

| پارامتر | نوع | الزامی | توضیحات |
| --------- | ---- |----------|-------------|
| contact_id | string | بله      | شناسه منحصر به فرد مخاطبی که می‌خواهید جزئیات آن را دریافت کنید. |

## ✅ پاسخ موفق

```json
{
  "data": {
    "id": 1234,
    "phonebook_id": 12345,
    "pre": "آقای",
    "name": "حسن",
    "email": "",
    "number": "+98912000000",
    "created_at": "2025-05-18T10:40:47+00:00",
    "updated_at": "2025-05-18T10:40:47+00:00",
    "phonebook_title": "title",
    "is_send_blacklist": true,
    "is_receive_blacklist": false,
    "tags": [
      {
        "id": 10,
        "number_id": "123",
        "phonebook_id": "12345",
        "tag": "tag test",
        "created_at": "2025-05-19T11:51:07.687000Z",
        "updated_at": "2025-05-19T11:51:07.687000Z"
      }
    ]
  },
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
curl --location '{base_url}/api/phonebooks/numbers/contact-list/{contact_id}' \
--header 'Content-Type: application/json' \
--header 'Authorization: API TOKEN'
```
