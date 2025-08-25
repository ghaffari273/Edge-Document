# دریافت شهرها

این API به شما امکان دریافت فهرست شهرهای یک شهرستان خاص را می‌دهد که می‌تواند برای فیلتر کردن گیرندگان در ارسال شهر و
استان از
آن‌ها استفاده شود.

## 📍 لینک دسترسی

```
GET {base_url}/api/send/banks/cities?county_id={county_id}
```

## 🧾 هدرهای درخواست

| کلید          | مقدار               |
|---------------|---------------------|
| Authorization | توکن یا کلید دسترسی |
| Content-Type  | application/json    |

## 📝 پارامترها

| پارامتر   | نوع     | ضروری | توضیحات                             |
|-----------|---------|-------|-------------------------------------|
| county_id | integer | بله   | شناسه شهرستان برای دریافت شهرهای آن |

## ✅ پاسخ موفق

```json
{
  "data": [
    {
      "id": 12,
      "name": "بیرجند"
    }
  ],
  "meta": {
    "status": true,
    "message": "انجام شد",
    "message_parameters": [],
    "message_code": "200-1"
  }
}
```

## 📝 نکات

- پارامتر `county_id` اجباری است و باید شناسه معتبر شهرستان باشد.
- فهرست شهرهای شهرستان انتخابی بازگردانده می‌شود.
- شناسه شهرها برای استفاده در API ارسال پیامک شهر و استان مورد نیاز است.

## ❌ پاسخ خطا — توکن نامعتبر یا منقضی شده (401)

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

## ❌ پاسخ خطا — شهرستان یافت نشد (404)

```json
{
  "data": null,
  "meta": {
    "status": false,
    "message": "شهرستان یافت نشد",
    "message_parameters": [],
    "message_code": "404-1",
    "errors": {}
  }
}
```

## 🧪 نمونه درخواست

```bash
curl --location '{base_url}/api/send/banks/cities?county_id=147' \
--header 'Authorization: API TOKEN'
```
