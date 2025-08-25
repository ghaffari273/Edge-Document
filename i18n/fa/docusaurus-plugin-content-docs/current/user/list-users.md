# لیست کاربران

این API به شما اجازه می‌دهد تا تمام کاربران زیرمجموعه خود را لیست کنید.

## 📍 لینک دسترسی

```
GET {base_url}/api/user/list?page=1&per_page=10
```

## 🧾 هدرهای درخواست

| کلید          | مقدار               |
|---------------|---------------------|
| Authorization | توکن یا کلید دسترسی |
| Content-Type  | application/json    |

## 📝 پارامترها

| پارامتر         | نوع     | الزامی | توضیحات                                                                                                                                                                                                                                                                                              |
|-----------------|---------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| page            | integer | خیر    | شماره صفحه برای صفحه‌بندی (پیش‌فرض 1)                                                                                                                                                                                                                                                                |
| per_page        | integer | خیر    | تعداد کاربران در هر صفحه (پیش‌فرض 10)                                                                                                                                                                                                                                                                |
| username        | string  | خیر    | فیلتر بر اساس نام کاربری (اختیاری)                                                                                                                                                                                                                                                                   |
| name            | string  | خیر    | فیلتر بر اساس نام (اختیاری)                                                                                                                                                                                                                                                                          |
| add_status      | string  | خیر    | فیلتر بر اساس وضعیت ایجاد کاربر. می‌تواند یکی از این مقادیر باشد: `status`,`normal`,`online`,`webservice` (اختیاری)                                                                                                                                                                                  |
| national_id     | string  | خیر    | فیلتر بر اساس شناسه ملی (اختیاری)                                                                                                                                                                                                                                                                    |
| acl_role_id     | integer | خیر    | فیلتر بر اساس شناسه نقش ACL (اختیاری)                                                                                                                                                                                                                                                                |
| tell            | string  | خیر    | فیلتر بر اساس شماره تلفن (اختیاری)                                                                                                                                                                                                                                                                   |
| mobile          | string  | خیر    | فیلتر بر اساس شماره موبایل (اختیاری)                                                                                                                                                                                                                                                                 |
| is_reseller     | string  | خیر    | فیلتر بر اساس وضعیت فروشنده (`yes` یا `no`) (اختیاری)                                                                                                                                                                                                                                                |
| document_block  | string  | خیر    | فیلتر بر اساس وضعیت بلوک سند (`yes` یا `no`) (اختیاری)                                                                                                                                                                                                                                               |
| created_from    | string  | خیر    | فیلتر بر اساس تاریخ ایجاد از (فرمت: timestamp UTC) (اختیاری)                                                                                                                                                                                                                                         |
| created_to      | string  | خیر    | فیلتر بر اساس تاریخ ایجاد تا (فرمت: timestamp UTC) (اختیاری)                                                                                                                                                                                                                                         |
| expire_from     | string  | خیر    | فیلتر بر اساس تاریخ انقضا از (فرمت: timestamp UTC) (اختیاری)                                                                                                                                                                                                                                         |
| expire_to       | string  | خیر    | فیلتر بر اساس تاریخ انقضا تا (فرمت: timestamp UTC) (اختیاری)                                                                                                                                                                                                                                         |
| is_bought_panel | string  | خیر    | فیلتر بر اساس وضعیت خرید پنل (`1` یا `0`) (اختیاری)                                                                                                                                                                                                                                                  |
| login_status    | integer | خیر    | نشان‌دهنده این است که آیا کاربر وارد شده است یا خیر. می‌تواند یکی از این وضعیت‌ها باشد: `0` و به معنای عدم ورود است (اختیاری)                                                                                                                                                                        |
| sub_reseller    | integer | خیر    | پذیرای `0` یا `1` است. `0` نشان‌دهنده این است که کاربر یک زیر فروشنده مستقیم است و `1` نشان‌دهنده این است که کاربر یک زیر فروشنده غیرمستقیم است (یعنی بخشی از خط پایین اما مستقیماً زیر درخواست‌دهنده نیست). در صورت عدم ذکر، تمام کاربران (هم مستقیم و هم غیرمستقیم) بازگردانده خواهند شد (اختیاری) |

⚠️ مهم: برای حذف فیلتر از کوئری، آن را اصلاً در درخواست قرار ندهید. از ارسال آن با رشته خالی یا مقدار null خودداری کنید.

## ✅ پاسخ موفق

```json
{
  "data": [
    {
      "status": "active",
      "time": 1747570721,
      "uname": "user1",
      "document_block": "yes",
      "special_disc": 0,
      "parent": 123654,
      "user_id": 123654,
      "accounting_id": null,
      "is_reseller": "yes",
      "name": "name and family",
      "national_id": "1587459321",
      "certificate_id": "1587459321",
      "tell": null,
      "mobile": "+989122222222",
      "address": "adress",
      "company": "test",
      "postalcode": 4758896654,
      "send_block": "yes",
      "email": "",
      "add_status": "webservice",
      "acl_role_id": 123,
      "last_login": 1747573019,
      "confirm": "0",
      "user_create": "no",
      "show_status": "active",
      "expire_time": null,
      "user_description": null,
      "description": null,
      "is_bought_panel": "1",
      "main_parent": "main_parent_name",
      "credit": {
        "credit": 0,
        "user_id": 123654
      },
      "acl_role": {
        "acl_role_id": 123,
        "acl_role_name": "package_name"
      }
    },
    {
      "status": "active",
      "time": 1747570721,
      "uname": "user1",
      "document_block": "yes",
      "special_disc": 0,
      "parent": 123654,
      "user_id": 123654,
      "accounting_id": null,
      "is_reseller": "yes",
      "name": "name and family",
      "national_id": "1587459321",
      "certificate_id": "1587459321",
      "tell": null,
      "mobile": "+989122222222",
      "address": "adress",
      "company": "test",
      "postalcode": 4758896654,
      "send_block": "yes",
      "email": "",
      "add_status": "webservice",
      "acl_role_id": 123,
      "last_login": 1747573019,
      "confirm": "0",
      "user_create": "no",
      "show_status": "active",
      "expire_time": null,
      "user_description": null,
      "description": null,
      "is_bought_panel": "1",
      "main_parent": "main_parent_name",
      "credit": {
        "credit": 0,
        "user_id": 123654
      },
      "acl_role": {
        "acl_role_id": 123,
        "acl_role_name": "package_name"
      }
    }
  ],
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 46,
    "path": "https://baseurl/api/user/list",
    "per_page": 1,
    "to": 1,
    "total": 46,
    "status": true,
    "message": "انجام شد",
    "message_code": "200-1"
  }
}
```

## ❌ پاسخ خطا — توکن نامعتبر یا منقضی شده (401)

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
curl --location '{base_url}/api/user/list?page=1&per_page=10' \
--header 'Content-Type: application/json' \
--header 'Authorization: Your Apikey/Token' 
```
