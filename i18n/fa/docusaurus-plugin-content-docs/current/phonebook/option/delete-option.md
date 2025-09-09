# حذف گزینه دفترچه تلفن
این API به شما امکان حذف فهرستی از گزینه‌ها را می‌دهد. می‌توانید چندین گزینه را برای حذف در یک درخواست مشخص کنید.

## 📍 نقطه پایانی

```
POST {base_url}/api/phonebooks/options/delete-list
```

## 🧾 هدرها

| کلید | مقدار |
| --- | ----- |
| Authorization | YOUR_TOKEN_HERE |
| Content-Type | application/json |

## 📤 بدنه درخواست

```json
{
  "listOptions": [
    1234
  ]
}
```

## 📝 پارامترها

| پارامتر | نوع | الزامی | توضیحات                                                                 |
| --------- | ---- |----------|-----------------------------------------------------------------------------|
| listOptions | array | بله      | آرایه‌ای از گزینه‌ها که باید حذف شوند. شماره‌ها باید در فرمت عدد صحیح باشند. |


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
curl --location --globoff '{base_url}/api/phonebooks/options/delete-list' \
--header 'Authorization: API TOKEN' \
--header 'Accept: application/json' \
--data '{
  "listOptions": [
    1234
  ]
}'
```
