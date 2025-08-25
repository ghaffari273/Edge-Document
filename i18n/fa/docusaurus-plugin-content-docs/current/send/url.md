# ارسال پیامک با لینک (URL)

این سند نحوه ارسال پیامک با استفاده از درخواست URL به API را شرح می‌دهد. درخواست می‌تواند با استفاده از کلید API یا
ترکیب نام کاربری/رمز عبور برای احراز هویت انجام شود.

## 📍 لینک دسترسی

```
GET-POST {base_url}/api/send/webservice'
```

## 📤 پارامترهای درخواست

```json
{
  "apikey": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "from": "+983000505",
  "message": "متن پیام",
  "to": "+989120000000",
  "username": "username",
  "password": "password"
}
```

## 📝 پارامترها

| پارامتر    | نوع    | ضروری | توضیحات                                         |
|------------|--------|-------|-------------------------------------------------|
| `apikey`   | string | شاید  | کلید API شما برای احراز هویت                    |
| `from`     | string | بله   | شماره فرستنده در فرمت E.164                     |
| `message`  | string | بله   | محتوای پیامک برای ارسال                         |
| `to`       | string | بله   | شماره گیرنده در فرمت E.164                      |
| `username` | string | شاید  | نام کاربری برای احراز هویت اضافی (در صورت نیاز) |
| `password` | string | شاید  | رمز عبور برای احراز هویت اضافی (در صورت نیاز)   |

## 📝 نام‌های جایگزین پارامترها

در هر درخواست، می‌توانید از یکی از کلیدهای جایگزین زیر برای هر پارامتر استفاده کنید:

- برای پارامتر `apikey`، می‌توانید استفاده کنید از:
  `api_key`, `apikey`, `apiKey`, `x-api-key`, `ApiKey`, `api-key`, `ApiKey`, `key`, `access_key`,
  `accessKey`, `auth_key`, `authorization`, `token`, `secret`, `api_token`

- برای پارامتر `from`، می‌توانید استفاده کنید از:
  `From`, `from`, `sender`, `src`, `source`, `from_number`, `sender_number`, `origin`, `originator`, `caller`,
  `caller_id`, `sms_from`, `fromNum`

- برای پارامتر `message`، می‌توانید استفاده کنید از:
  `Message`, `message`, `msg`, `text`, `txt`, `body`, `content`, `sms`, `message_body`, `messageText`

- برای پارامتر `to`، می‌توانید استفاده کنید از:
  `To`, `to`, `recipient`, `dest`, `destination`, `to_number`, `recipient_number`, `target`, `receiver`,
  `mobile`, `phone`, `sms_to`, `toNum`

- برای پارامتر `username`، می‌توانید استفاده کنید از:
  `Username`, `username`, `user`, `login`, `account`, `userId`, `user_id`

- برای پارامتر `password`، می‌توانید استفاده کنید از:
  `Password`, `password`, `pass`, `pwd`, `secret_key`, `auth_password`

## 📝 نکات

- شماره فرستنده باید سرشماره معتبری باشد که به حساب شما اختصاص یافته است.
- می‌توانید از کلید API یا ترکیب نام کاربری/رمز عبور برای احراز هویت استفاده کنید.
- این روش برای ارسال سریع پیامک در نرم افزارها یا محیط هایی که امکان تنظیمات پیچیده وجود ندارد مناسب است.
- همه پارامترها باید به صورت URL encoded ارسال شوند.
- این لینک فراخوانی با هر دو متد `POST` و `GET` را پشتیبانی می کند

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

## ❌ پاسخ خطا — احراز هویت ناموفق (401)

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
با استفاده از کلید دسترسی:
```bash
curl --location '{base_url}/api/send/webservice?apikey=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx&from=+983000505&message=متن پیام&to=+989120000000'
```

یا با استفاده از نام کاربری و رمز عبور:

```bash
curl --location '{base_url}/api/send/webservice?username=username&password=password&from=+983000505&message=متن پیام&to=+989120000000'
```
