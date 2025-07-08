# Send Keyword Phonebook SMS

This API allows you to send messages using a keyword to a phonebook.

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
  "sending_type": "keyword_phonebook",
  "from_number": "+983000505",
  "message": "تاریخ {ex_50856}\nبدهی {ex_50858}",
  "send_time": "2025-03-25 10:10:10",
  "params": [
    {
      "phonebook_id": 123654
    }
  ]
}
```

## 📝 Parameters

| Parameter | Type | Required | Description                                                                            |
| --------- | ---- | -------- |----------------------------------------------------------------------------------------|
| sending_type | string | Yes | Type of sending, must be "keyword_phonebook" for this endpoint                         |
| from_number | string | Yes | Sender's phone number in E.164 format (e.g., +983000505)                               |
| message | string | Yes | Message content to be sent, can include placeholders for phonebook fields              |
| send_time | string | No | Scheduled time for sending the message in YYYY-MM-DD HH:MM:SS format (timezone is UTC) |
| params | array | Yes | Array of objects containing phonebook id                                               |
| phonebook_id | integer | Yes | ID of the phonebook to send messages to                                                |

## 📝 Notes
- The `from_number` must be a valid sender number assigned to your account.
- The `send_time` is optional; if not provided, the message will be sent immediately.


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
The response returns an array of message_outbox_ids – one ID per message sent (regardless of how many recipients it had).
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
    "sending_type": "keyword_phonebook",
    "from_number": "+983000505",
    "message": "تاریخ {ex_50856}\nبدهی {ex_50858}",
    "send_time": "2025-03-25 10:10:10",
    "params": [
        {
            "phonebook_id": 123654
        }
    ]
}'
```
