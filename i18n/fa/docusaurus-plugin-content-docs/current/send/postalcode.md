# ارسال پیامک با کد پستی

این API به شما امکان ارسال پیام با استفاده از کدهای پستی را می‌دهد.

## 📍 لینک دسترسی

```
POST {base_url}/api/send
```

## 🧾 هدرهای درخواست

| کلید          | مقدار               |
|---------------|---------------------|
| Authorization | توکن یا کلید دسترسی |
| Content-Type  | application/json    |

## 📤 بدنه درخواست

```json
{
  "sending_type": "postal_code",
  "from_number": "+98BANK",
  "message": "متن پیام",
  "params": [
    {
      "bank": "all",
      "postal_code": 131,
      "gender": 0,
      "age_from": 1330,
      "age_to": 1402,
      "mci": {
        "start": 0,
        "size": 1
      },
      "irancell": {
        "start": 0,
        "size": 0
      },
      "other": {
        "start": 0,
        "size": 0
      }
    },
    {
      "bank": "all",
      "postal_code": 141,
      "gender": 0,
      "age_from": 1330,
      "age_to": 1402,
      "mci": {
        "start": 0,
        "size": 1
      },
      "irancell": {
        "start": 0,
        "size": 0
      },
      "other": {
        "start": 0,
        "size": 0
      }
    }
  ],
  "other_recipients": [
    "+989120000000",
    "+989350000000"
  ],
  "send_time": "2025-02-28 10:52:02"
}
```

## 📝 پارامترها

| پارامتر      | نوع     | ضروری | توضیحات                                                                              |
|--------------|---------|-------|--------------------------------------------------------------------------------------|
| sending_type | string  | بله   | نوع ارسال، باید "postal_code" باشد                                                   |
| from_number  | string  | بله   | شماره فرستنده در فرمت E.164 (مثال: +983000505)                                       |
| message      | string  | بله   | متن پیامی که میخواهید ارسال نمایید. این متن نباید بیش از 1400 کارکتر یا 20 پارت باشد |
| params       | array   | بله   | آرایه‌ای از اشیاء شامل تنظیمات کد پستی                                               |
| bank         | string  | بله   | نوع بانک اطلاعاتی: "all" برای همه                                                    |
| postal_code  | integer | بله   | کد پستی مورد نظر                                                                     |
| gender       | integer | خیر   | جنسیت: 0 برای همه، 1 برای مرد، 2 برای زن                                             |
| age_from     | integer | خیر   | سال تولد شروع (شمسی)                                                                 |
| age_to       | integer | خیر   | سال تولد پایان (شمسی)                                                                |
| mci          | object  | خیر   | تنظیمات اپراتور همراه اول شامل از چه ردیف و به چه تعداد                              |
| irancell     | object  | خیر   | تنظیمات اپراتور ایرانسل شامل از چه ردیف و به چه تعداد                                |
| other        | object  | خیر   | تنظیمات سایر اپراتورها شامل از چه ردیف و به چه تعداد                                 |
| start        | integer | خیر   | شماره ردیف شروع                                                                      |
| size         | integer | خیر   | تعداد شماره‌های مورد نظر                                                             |
| send_time    | string  | خیر   | زمان مورد نظر برای ارسال پیام در فرمت YYYY-MM-DD HH:MM:SS. منطقه زمانی UTC است.      |

## 📝 تنظیمات اپراتور

هر اپراتور شامل دو پارامتر است:

- `start`: شماره ردیف شروع (پیش‌فرض: 0)
- `size`: تعداد شماره‌های مورد نظر (پیش‌فرض: 0)

## 📝 نکات

- `from_number` باید سرشماره معتبری باشد که به حساب شما اختصاص یافته است.
- کد پستی باید معتبر و در سیستم موجود باشد.
- می‌توانید با تنظیم پارامترهای جنسیت و سن، مخاطبین را فیلتر کنید.
- اگر پارامترهای اپراتور تنظیم نشوند، به همه شماره‌ها ارسال می‌شود.

## ✅ پاسخ موفق

```json
{
  "data": {
    "message_outbox_ids": [
      1123544244
    ]
  },
  "meta": {
    "status": true,
    "message": "انجام شد",
    "message_parameters": [],
    "message_code": "200-1"
  }
}
```

## ❌ پاسخ خطا — کد پستی نامعتبر (422)

```json
{
  "data": null,
  "meta": {
    "status": false,
    "message": "کد پستی نامعتبر است",
    "message_parameters": [],
    "message_code": "400-2",
    "errors": {
      "postal_code": [
        "کد پستی نامعتبر است"
      ]
    }
  }
}
```

## 🧪 نمونه درخواست

```bash
curl --location '{base_url}/api/send' \
--header 'Content-Type: application/json' \
--header 'Authorization: API TOKEN' \
--data '{
    "sending_type": "postal_code",
    "from_number": "+98BANK",
    "message": "متن پیام",
    "params": [
        {
            "bank": "all",
            "postal_code": 131,
            "gender": 0,
            "age_from": 1330,
            "age_to": 1402,
            "mci": {
                "start": 0,
                "size": 1
            },
            "irancell": {
                "start": 0,
                "size": 0
            },
            "other": {
                "start": 0,
                "size": 0
            }
        },
        {
            "bank": "all",
            "postal_code": 141,
            "gender": 0,
            "age_from": 1330,
            "age_to": 1402,
            "mci": {
                "start": 0,
                "size": 1
            },
            "irancell": {
                "start": 0,
                "size": 0
            },
            "other": {
                "start": 0,
                "size": 0
            }
        }
    ],
    "other_recipients": [
        "+989120000000",
        "+989350000000"
    ],
    "send_time": "2025-02-28 10:52:02"
}'
```
