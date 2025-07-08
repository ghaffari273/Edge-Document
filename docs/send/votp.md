# Send VOTP

This API allows you to send a VOTP (Voice One-Time Password) message.

## 📍 Endpoint

```
POST {base_url}/api/send
```

## 🧾 Headers

| Key | Value |
| --- | ----- |
| Authorization | YOUR_TOKEN_HERE |
| Content-Type | application/json |

## 📤 Request Body

```json
{
  "sending_type": "votp",
  "message": "45852",
  "params": {
    "recipients": [
      "+989120000000"
    ]
  }
}
```

## 📝 Parameters

| Parameter | Type | Required | Description |
| --------- | ---- | -------- | ----------- |
| sending_type | string | Yes | Type of sending, must be "votp" for this endpoint |
| message | string | Yes | Message content to be sent, typically a one-time password (OTP), such as "45852" |
| params | object | Yes | Object containing recipients and other optional parameters |
| recipients | array | Yes | List of recipient phone numbers in E.164 format (e.g., +989120000000), only one recipient is allowed for VOTP |

## 📝 Notes
- The `from_number` must be a valid sender number assigned to your account.
- The `recipients` array must contain valid phone number in E.164 format.



## ✅ Success Response

```json
{
  "data": {
    "message_outbox_ids": [
      1123594208
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

## ❌ Error Response — Invalid Request (422)

```json
{
  "data": null,
  "meta": {
    "status": false,
    "message": "تکمیل گزینه پیام الزامی است",
    "message_parameters": [],
    "message_code": "400-2",
    "errors": {
      "message": [
        "تکمیل گزینه پیام الزامی است"
      ]
    }
  }
}
```

## 🧪 Example Request

```bash
curl --location '{base_url}/api/send' \
--header 'Content-Type: application/json' \
--header 'Authorization: API TOKEN' \
--data '{
    "sending_type": "votp",
    "message": "45852",
    "params": {
        "recipients": [
            "+989120000000"
        ]
    }
}'
```
