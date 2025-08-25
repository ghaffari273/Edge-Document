# دریافت گزارشات دریافت

این API به شما امکان دریافت گزارش پیام‌های دریافتی را می‌دهد.

اگر می‌خواهید پیام‌های جدید دریافتی را بگیرید، می‌توانید از پارامتر from_id در بدنه درخواست استفاده کنید. این پارامتر
شناسه آخرین پیامی است که دریافت کرده‌اید. API تمام پیام‌های دریافتی بعد از این شناسه را برمی‌گرداند.

می‌توانید از پارامترهای page و per_page برای صفحه‌بندی نتایج استفاده کنید.

## 📍 لینک دسترسی

```
POST {base_url}/api/report/messages-inbox
```

## 🧾 هدرها

| کلید          | مقدار               |
|---------------|---------------------|
| Authorization | توکن یا کلید دسترسی |
| Content-Type  | application/json    |

## 📤 بدنه درخواست

```json
{
  "page": 1,
  "per_page": 10,
  "filters": {
    "from_id": 125
  }
}
```

## 📝 پارامترها

| پارامتر  | نوع     | الزامی | توضیحات                                                                                |
|----------|---------|--------|----------------------------------------------------------------------------------------|
| page     | integer | خیر    | شماره صفحه برای دریافت (پیش‌فرض ۱)                                                     |
| per_page | integer | خیر    | تعداد آیتم‌ها در هر صفحه (پیش‌فرض ۱۰)                                                  |
| filters  | object  | خیر    | شیئی حاوی فیلترهای مختلف برای اعمال بر نتایج گزارش                                     |
| from_id  | integer | خیر    | شناسه آخرین پیام دریافت شده، برای دریافت پیام‌های جدید بعد از این شناسه استفاده می‌شود |

## ✅ پاسخ موفق

```json
{
  "data": [
    {
      "messages_inbox_id": 123,
      "from": "+989122222222",
      "number": "+981000123",
      "message": "message text",
      "type": "normal",
      "time": 1747808125,
      "seen": "0"
    },
    {
      "messages_inbox_id": 122,
      "from": "+989122222222",
      "number": "+981000123",
      "message": "message text",
      "type": "normal",
      "time": 1747808120,
      "seen": "0"
    }
  ],
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 4066539,
    "path": "https://baseurl/api/report/messages-inbox",
    "per_page": 2,
    "to": 1,
    "total": 4066539,
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

## 🧪 نمونه درخواست

```bash
curl --location '{base_url}/api/report/messages-inbox' \
--header 'Content-Type: application/json' \
--header 'Authorization: Your Apikey/Token' \
--data '{
    "page": 1,
    "per_page": 10,
    "filters" : {
        "from_id":125
    }
}'
```
