# Phonebook Option Delete
This API allows you to delete a list of options. You can specify multiple options to be deleted in a single request.

## 📍 Endpoint

```
POST {base_url}/api/phonebooks/options/delete-list
```

## 🧾 Headers

| Key | Value |
| --- | ----- |
| Authorization | YOUR_TOKEN_HERE |
| Content-Type | application/json |

## 📤 Request Body

```json
{
  "listOptions": [
    1234
  ]
}
```

## 📝 Parameters

| Parameter | Type | Required | Description                                                                 |
| --------- | ---- |----------|-----------------------------------------------------------------------------|
| listNumbers | array | Yes      | An array of options to be deleted. The numbers should be in integer format. |


## ✅ Success Response

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

## ❌ Error Response — Invalid or Expired Token (401)

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

## 🧪 Example Request

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
