# دریافت درخت والدین

درخت کامل سلسله مراتب (درخت فروشنده) یک کاربر خاص را برمی‌گرداند.

## 📍 لینک دسترسی

```
GET {base_url}/api/user/parents_tree?user_id={user_id}
```

## 🧾 هدرهای درخواست

| کلید          | مقدار               |
|---------------|---------------------|
| Authorization | توکن یا کلید دسترسی |
| Content-Type  | application/json    |

## 📝 پارامترها

| پارامتر | نوع     | الزامی | توضیحات                                                  |
|---------|---------|--------|----------------------------------------------------------|
| user_id | integer | بله    | شناسه کاربری که می‌خواهید درخت والدین آن را دریافت کنید. |

## ✅ پاسخ موفق

```json
{
  "data": {
    "selected_user": {
      "id": 123,
      "username": "user",
      "is_reseller": true
    },
    "main_parent": {
      "id": 584,
      "username": "mainparent",
      "is_reseller": true
    },
    "tree": [
      {
        "id": 1,
        "username": "ippanel",
        "is_reseller": "yes"
      },
      {
        "id": 464,
        "username": "res1",
        "is_reseller": "yes"
      },
      {
        "id": 8555,
        "username": "res2",
        "is_reseller": "yes"
      },
      {
        "id": 98798,
        "username": "res3",
        "is_reseller": "yes"
      }
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
    "message": "تکمیل گزینه user id الزامی است",
    "message_parameters": [],
    "message_code": "400-2",
    "errors": {
      "user_id": [
        "تکمیل گزینه user id الزامی است"
      ]
    }
  }
}
```

## 🧪 مثال درخواست

```bash
curl --location '{base_url}/api/user/parents_tree?user_id={user_id}' \
--header 'Content-Type: application/json' \
--header 'Authorization: Your Apikey/Token' 
```
