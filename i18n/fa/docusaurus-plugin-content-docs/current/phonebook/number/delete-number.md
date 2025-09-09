# حذف شماره دفترچه تلفن
این API به شما امکان حذف فهرستی از شماره تلفن‌ها از دفترچه تلفن شما را می‌دهد. می‌توانید چندین شماره را برای حذف در یک درخواست مشخص کنید.

## 📍 نقطه پایانی

```
POST {base_url}/api/phonebooks/numbers/delete-list
```

## 🧾 هدرها

| کلید | مقدار |
| --- | ----- |
| Authorization | YOUR_TOKEN_HERE |
| Content-Type | application/json |

## 📤 بدنه درخواست

```json
{
  "listNumbers": [
    1234
  ]
}
```

## 📝 پارامترها

| پارامتر | نوع | الزامی | توضیحات                                                           |
| --------- | ---- |----------|-----------------------------------------------------------------------|
| listNumbers | array | بله      | آرایه‌ای از شماره تلفن‌ها که باید از دفترچه تلفن حذف شوند. شماره‌ها باید در فرمت عدد صحیح باشند. |




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
curl --location '{base_url}/api/phonebooks/numbers/delete-list' \
--header 'Content-Type: application/json' \
--header 'Authorization: API TOKEN' \
--data '{
    "listNumbers": [
       1234
    ]
}'
```
