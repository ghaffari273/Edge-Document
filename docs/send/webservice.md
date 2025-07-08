# Send Webservice SMS

This endpoint is used to send SMS messages using a web service.

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
  "sending_type": "webservice",
  "from_number": "+983000505",
  "message": "متن پیام",
  "params": {
    "recipients": [
      "+989120000000",
      "+989350000000"
    ]
  },
  "send_time": "2025-03-12 21:20:02"
}
```

## 📝 Parameters

| Parameter | Type | Required | Description                                                         |
| --------- | ---- | -------- |---------------------------------------------------------------------|
| sending_type | string | Yes | Type of sending, must be "webservice" for this endpoint             |
| from_number | string | Yes | Sender's phone number in E.164 format (e.g., +983000505)            |
| message | string | Yes | Message content to be sent |
| params | object | Yes | Parameters for sending the message, including recipients |
| recipients | array | Yes | List of recipient phone numbers in E.164 format (e.g., +989120000000) |
| send_time | string | No | Scheduled time for sending the message in YYYY-MM-DD HH:MM:SS.timezone is UTC. |

## 📝 Notes
- The `from_number` must be a valid sender number assigned to your account.
- The `recipients` array must contain valid phone numbers in E.164 format.
- The `send_time` is optional; if not provided, the message will be sent immediately.

## ✅ Success Response

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
    "sending_type": "webservice",
    "from_number": "+983000505",
    "message": "متن پیام",
    "params": {
        "recipients": [
            "+989120000000",
            "+989350000000"
        ]
    },
    "send_time": "2025-03-12 21:20:02"
}'
```
