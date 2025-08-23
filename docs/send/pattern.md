# Send Pattern SMS

This API allows you to send messages using a pattern.

## 📍 Endpoint

```
POST {base_url}/api/send
```

## 🧾 Headers

| Key           | Value            |
|---------------|------------------|
| Authorization | YOUR_TOKEN_HERE  |
| Content-Type  | application/json |

## 📤 Request Body

```json
{
  "sending_type": "pattern",
  "from_number": "+983000505",
  "code": "xxxxxxxxxxxxxxx",
  "recipients": [
    "+989120000000"
  ],
  "params": {
    "code": "متن جایگذاری"
  },
  "phonebook": {
    "id": 1234,
    "name": "سعید محمدی",
    "pre": "mr",
    "email": "saeed@gmail.com",
    "options": {
      "456": "1970/01/01"
    }
  }
}
```

## 📝 Parameters

| Parameter         | Type   | Required | Description                                                                                                            |
|-------------------|--------|----------|------------------------------------------------------------------------------------------------------------------------|
| sending_type      | string | Yes      | Type of sending, must be "pattern" for this endpoint                                                                   |
| from_number       | string | Yes      | Sender's phone number in E.164 format (e.g., +983000505)                                                               |
| code              | string | Yes      | The pattern code to be used for sending the message                                                                    |
| recipients        | array  | Yes      | List of recipient phone number in E.164 format (e.g., +989120000000). Only one recipient is allowed for this endpoint. |
| params            | object | Yes      | Object containing parameters to replace in the pattern code. The keys must match the placeholders in the pattern.      |
| phonebook         | object | No       | Optional object containing phonebook details. If provided, it will save the recipient to the specified phonebook.      |
| phonebook.id      | int    | Yes      | ID of the phonebook to which the recipient will be added.                                                              |
| phonebook.name    | string | No       | Name of the contact to be saved in the phonebook.                                                                      |   
| phonebook.pre     | string | No       | Prefix for the contact (e.g., mr, ms).                                                                                 |
| phonebook.email   | string | No       | Email of the contact to be saved in the phonebook.                                                                     |
| phonebook.options | object | No       | Additional options for the contact. The keys are custom field IDs and the values are the corresponding data.           |

## 📝 Notes

- The `from_number` must be a valid sender number assigned to your account.
- The `recipients` array must contain valid phone numbers in E.164 format.
- The `params` object must contain key-value pairs where keys match the placeholders in the pattern code.
- If the `phonebook` object is provided, the recipient will be added to the specified phonebook with the given details.
- Only one recipient is allowed for this endpoint.
- If phonebook recipient limit is reached, only the message will be sent and the recipient will not be added to the phonebook.

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
    "sending_type": "pattern",
    "from_number": "+983000505",
    "code": "xxxxxxxxxxxxxxx",
    "recipients": [
        "+989120000000"
    ],
    "params": {
        "code": "متن جایگذاری"
    },
    "phonebook": {
      "id": 1234,
      "name": "سعید محمدی",
      "pre": "mr",
      "email": "saeed@gmail.com",
      "options": {
        "456": "1970/01/01"
      }
    }
}'
```
