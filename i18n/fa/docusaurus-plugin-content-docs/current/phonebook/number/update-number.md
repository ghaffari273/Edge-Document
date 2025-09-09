# بروزرسانی شماره دفترچه تلفن

این API به شما امکان بروزرسانی یک مخاطب موجود در دفترچه تلفن با استفاده از شناسه آن را می‌دهد. می‌توانید نام، شماره، ایمیل و گزینه‌های اضافی مخاطب را تغییر دهید.

## 📍 نقطه پایانی

```
PUT {base_url}/api/phonebooks/numbers/update-new/{contact_id}
```

## 🧾 هدرها

| کلید           | مقدار            |
|---------------|------------------|
| Authorization | YOUR_TOKEN_HERE  |
| Content-Type  | application/json |

## 📤 بدنه درخواست

```json
{
  "pre": "Mr.",
  "name": "name",
  "number": "+989121236547",
  "options": {
    "124": "2025-05-20"
  },
  "phonebook_id": "12345"
}
```

## 📝 پارامترها

| پارامتر    | نوع   | الزامی | توضیحات                                           |
|--------------|--------|----------|-------------------------------------------------------|
| number       | string | بله      | شماره تلفن در فرمت E.164.                     |
| pre          | string | خیر       | پیشوند نام (مثل آقای، خانم).             |
| name         | string | خیر       | نام مخاطب.                              |
| email        | string | خیر       | آدرس ایمیل مخاطب.                     |
| options      | object | خیر       | گزینه‌های اضافی به عنوان جفت کلید-مقدار.                |
| phonebook_id | string | بله      | شناسه دفترچه تلفنی که مخاطب به آن تعلق دارد. |

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
curl --location --globoff --request PUT '{base_url}/api/phonebooks/numbers/update-new/234235' \
--header 'Authorization: Your Apikey/Token' \
--header 'Content-Type: application/json' \
--data '{
    "pre": "Mr.",
    "name": "name",
    "number": "+989121236547",
    "options": {
      "124": "2025-05-20"
    },
    "phonebook_id": "12345"
}'
```
