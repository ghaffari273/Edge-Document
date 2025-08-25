# دریافت گزارشات ارسال

با این API می‌توانید گزارش کلی از درخواست‌های ارسال پیامک خود را دریافت کنید. این گزارش اطلاعاتی در مورد پیام‌های ارسالی
ارائه می‌دهد اما جزئیات پیام‌ها را شامل نمی‌شود. برای دسترسی به داده‌های سطح پیام، لطفاً به APIهای تفصیلی که در ادامه
این مستندات توضیح داده شده‌اند، مراجعه کنید.

می‌توانید از پارامترهای page و limit برای صفحه‌بندی نتایج استفاده کنید.

## 📍 لینک دسترسی

```
POST {base_url}/api/report/new_list
```

## 🧾 هدرهای درخواست

| کلید          | مقدار               |
|---------------|---------------------|
| Authorization | توکن یا کلید دسترسی |
| Content-Type  | application/json    |

## 📤 بدنه درخواست

```json
{
  "page": 1,
  "limit": 10,
  "filters": {
    "username": "*",
    "number": "+98217000070",
    "messages_outbox_id": "1100972179",
    "create_from_date": "1744102007",
    "create_to_date": "1744102007",
    "send_from_date": "1744102007",
    "send_to_date": "1744102007",
    "from_exit_count": 1,
    "to_exit_count": 100,
    "message": "تست",
    "state_id": "6"
  }
}
```

## 📝 پارامترها

| پارامتر                    | نوع     | الزامی | توضیحات                                                    |
|----------------------------|---------|--------|------------------------------------------------------------|
| page                       | integer | خیر    | شماره صفحه برای صفحه‌بندی. پیش‌فرض ۱.                      |
| limit                      | integer | خیر    | تعداد رکورد در هر صفحه. پیش‌فرض ۱۰.                        |
| filters                    | object  | خیر    | شیئی حاوی فیلترهای مختلف برای اعمال بر گزارش.              |
| filters.username           | string  | خیر    | فیلتر بر اساس نام کاربری (پشتیبانی از wildcard `*`).       |
| filters.number             | string  | خیر    | فیلتر بر اساس شماره فرستنده در فرمت E.164.                 |
| filters.messages_outbox_id | string  | خیر    | فیلتر بر اساس شناسه خاص صندوق خروجی پیام.                  |
| filters.create_from_date   | string  | خیر    | فیلتر بر اساس تاریخ ایجاد از (timestamp).                  |
| filters.create_to_date     | string  | خیر    | فیلتر بر اساس تاریخ ایجاد تا (timestamp).                  |
| filters.send_from_date     | string  | خیر    | فیلتر بر اساس تاریخ ارسال از (timestamp).                  |
| filters.send_to_date       | string  | خیر    | فیلتر بر اساس تاریخ ارسال تا (timestamp).                  |
| filters.from_exit_count    | integer | خیر    | فیلتر بر اساس حداقل تعداد خروجی.                           |
| filters.to_exit_count      | integer | خیر    | فیلتر بر اساس حداکثر تعداد خروجی.                          |
| filters.message            | string  | خیر    | فیلتر بر اساس محتوای پیام.                                 |
| filters.state_id           | string  | خیر    | فیلتر بر اساس شناسه وضعیت پیام (مثلاً `6` برای ارسال شده). |

## 📝 نکات

- شیء `filters` به شما امکان تعیین معیارهای متعدد برای محدود کردن نتایج گزارش را می‌دهد.
- `state_id` می‌تواند برای فیلتر کردن پیام‌ها بر اساس وضعیت آن‌ها مانند ارسال شده، ناموفق، یا در انتظار استفاده شود.
    - `0`: پیام در حال ایجاد است.
    - `1`: پیام با موفقیت ایجاد شده و در صف نظارت قرار دارد.
    - `2`: پیام در حال ارسال است.
    - `3`: پیام توسط سیستم نظارت رد شده.
    - `4`: گیرندگان این پیام به اشتباه وارد شده‌اند یا معتبر نیستند.
    - `5`: پیام در صف ارسال است.
    - `6`: پیام با موفقیت ارسال شده.
    - `7`: ارسال پیام لغو شده.
    - `8`: اعتبار ناکافی برای ارسال.
    - `9`: پیام به دلیل خطای سیستم ارسال نشده.

## ✅ پاسخ موفق

```json
{
  "data": [
    {
      "username": "*****",
      "number_color": "#95E871",
      "number": "+981000",
      "number_id": "123654",
      "messages_outbox_id": "12545856",
      "state": "finish",
      "type": "pattern_transactional",
      "time_send": "1745409418",
      "time": "1745409418",
      "rcpts_count": "1",
      "exit_count": "1",
      "status": "پایان یافته",
      "partner_id": null,
      "in_delivery_line": 0,
      "valid": "approve",
      "message": "متن پیام",
      "part": null,
      "cost": 3990.2,
      "summary": null,
      "user_ip": null,
      "user_id": null,
      "files_path": null,
      "parent_id": null,
      "state_id": 6
    },
    {
      "username": "******",
      "number_color": "#95E871",
      "number": "+981000",
      "number_id": "1236587",
      "messages_outbox_id": "588459562",
      "state": "finish",
      "type": "pattern",
      "time_send": "1745409418",
      "time": "1745409418",
      "rcpts_count": "1",
      "exit_count": "1",
      "status": "پایان یافته",
      "partner_id": null,
      "in_delivery_line": 0,
      "valid": "approve",
      "message": "متن پیام",
      "part": null,
      "cost": 6144.9,
      "summary": null,
      "user_ip": null,
      "user_id": null,
      "files_path": null,
      "parent_id": null,
      "state_id": 6
    }
  ],
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 32282040,
    "path": "/api/report/new_list",
    "per_page": 2,
    "to": 2,
    "total": 64564080,
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

## ❌ پاسخ خطا — درخواست نامعتبر (422)

```json
{
  "data": null,
  "meta": {
    "status": false,
    "message": "invalid state",
    "message_parameters": [],
    "message_code": "400-31",
    "errors": {}
  }
}
```

## 🧪 مثال درخواست

```bash
curl --location '{base_url}/api/report/new_list' \
--header 'Content-Type: application/json' \
--header 'Authorization: Your Apikey/Token' \
--data '{
    "page": 1,
    "limit": 10,
    "filters": {
        "username": "*",
        "number": "+98217000070",
        "messages_outbox_id": "1100972179",
        "create_from_date": "1744102007",
        "create_to_date": "1744102007",
        "send_from_date": "1744102007",
        "send_to_date": "1744102007",
        "from_exit_count": 1,
        "to_exit_count": 100,
        "message": "تست",
        "state_id":"6"
    }
}'
```
