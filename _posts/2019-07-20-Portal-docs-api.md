---
date: 2019-07-20
title: Tài liệu API của portal
categories:
  - docs-api
description: Tài liệu API dành cho User của portal cloud365
type: Document
---

# Docs API portal dành cho User.

## 1. API xác thực

### 1. Tạo mới Token.

- Phương thức: POST
- Đường dẫn: http://portalurl/api/v1/auth/tokens
- Tham số:

![scr1](/images/img-api/scr1.png)

- Request mẫu:

```sh
{
    "email": "string",
    "password": "string",
    "expired": 0,
    "project_id": "string"
}
```

- Respone mẫu:

```sh
{
    "message": "Xác thực thành công",
    "token": "string"
}
```

### 2. Lấy thông tin chi tiết Token.

- Phương thức: GET
- Đường dẫn: http://portalurl/api/v1/auth/tokens
- Respone mẫu:

```sh
{
    "project_id": "string",
    "token_created": "YYYY-MM-DDTh:i:s+07:00",
    "token_expired": "YYYY-MM-DDTh:i:s+07:00",
    "token_key": "string",
    "user_owner": "user@example.com"
}
```

### 3. Xóa Token.

- Phương thức: DEL
- Đường dẫn: http://portalurl/api/v1/auth/tokens

## 2. API phục vụ cho thao tác và điều khiển máy chủ ảo.

### 1. Liệt kê các máy chủ ảo đang sở hữu.

- Phương thức: GET
- Đường dẫn: http://portalurl/api/v1/server/
- Tham số:

![scr2](/images/img-api/scr2.png)

- Respone mẫu:

```sh
{
  "count": 0,
  "next": "http://example.com",
  "previous": "http://example.com",
  "results": [
    {
      "instance_id": "string",
      "status": "string",
      "addresses": "string",
      "name": "string",
      "created": "2019-07-18T06:41:10Z",
      "expired": "2019-07-18T06:41:10Z",
      "ip_addresses": [
        "string"
      ],
      "region": "string"
    }
  ]
}
```

### 2. Thông tin chi tiết máy chủ ảo.

- Phương thức: GET
- Đường dẫn: http://portalurl/api/v1/server/{instance_id}/
- Tham số:

![scr3](/images/img-api/scr3.png)

- Respone mẫu:

```sh
{
  "instance_id": "string",
  "status": "string",
  "addresses": "string",
  "name": "string",
  "created": "2019-07-18T06:41:10Z",
  "expired": "2019-07-18T06:41:10Z",
  "ip_addresses": [
    "string"
  ],
  "region": "string"
}
```

### 3. Thay đổi mật khẩu máy chủ ảo.

- Phương thức: POST
- Đường dẫn: http://portalurl/api/v1/server/{instance_id}/change_password/
- Tham số:

![scr4](/images/img-api/scr4.png)

- Request mẫu:

```sh
{
  "password": "string",
  "re_password": "string"
}
```

- Respone mẫu:

```sh
{
  "message": "string"
}
```

### 4. lấy đường dẫn console của server.

- Phương thức: GET
- Đường dẫn: http://portalurl/api/v1/server/{instance_id}/console/
- Tham số:

![scr5](/images/img-api/scr5.png)

- Respone mẫu:

```sh
[
  {
    "message": "string",
    "url": "example.com"
  }
]
```

### 5. Lấy thông tin nhật ký boot của máy chủ ảo.

- Phương thức: GET
- Đường dẫn: http://portalurl/api/v1/server/{instance_id}/get_console_log/
- Tham số:

![scr6](/images/img-api/scr6.png)

- Respone mẫu:

```sh
{
  "console_log": "string"
}
```

### 6. Lấy thông tin các volume gắn vào máy chủ ảo.

- Phương thức: GET
- Đường dẫn: http://portalurl/api/v1/server/{instance_id}/list_volume_attached/
- Tham số:

![scr7](/images/img-api/scr7.png)

- Respone mẫu:

```sh
[
  {
    "bootable": "true",
    "name": "string",
    "size": 0,
    "volume_id": "string"
  },
  {}
]
```

### 7. Khởi động lại máy chủ ảo.

- Phương thức: POST
- Đường dẫn: http://portalurl/api/v1/server/{instance_id}/reboot/
- Tham số:

![scr8](/images/img-api/scr8.png)

- Respone mẫu:

```sh
{
  "message": "string"
}
```

### 8. Khởi động máy chủ ảo.

- Phương thức: POST
- Đường dẫn: http://portalurl/api/v1/server/{instance_id}/start/
- Tham số:

![scr9](/images/img-api/scr9.png)

- Respone mẫu:

```sh
{
  "message": "string"
}
```

### 9. Tắt máy chủ ảo.

- Phương thức: POST
- Đường dẫn: http://portalurl/api/v1/server/{instance_id}/stop/
- Tham số:

![scr10](/images/img-api/scr10.png)

- Respone mẫu:

```sh
{
  "message": "string"
}
```

### 10. Đổi tên máy chủ ảo.

- Phương thức: POST
- Đường dẫn: http://portalurl/api/v1/server/{instance_id}/rename/
- Tham số:

![scr11](/images/img-api/scr11.png)

- Request mẫu:

```sh
{
  "server_name": "string"
}
```

- Respone mẫu:

```sh
{
  "message": "string"
}
```

### 11. Rebuild máy ảo => Thay đổi hệ điều hành của máy chủ ảo.

- Phương thức: POST
- Đường dẫn: http://portalurl/api/v1/server/{instance_id}/rebuild/
- Tham số:

![scr12](/images/img-api/scr12.png)
- Request mẫu:

```sh
{
  "os_image": 0
}
```

- Respone mẫu:

```sh
{
  "message": "string"
}
```

## 3. API phục vụ cho việc quản lý thông tin cá nhân của User.

### 1. Lấy thông tin cá nhân.

- Phương thức: GET
- Đường dẫn: http://portalurl/api/v1/user/detail_user/
- Respone mẫu:

```sh
{
    "address": "string",
    "birthday": "YYYY-MM-DD",
    "company": "string",
    "date_joined": "YYYY-MM-DDTh:i:s+07:00",
    "email": "user@example.com",
    "first_name": "string",
    "gender": "gender",
    "last_login": "YYYY-MM-DDTh:i:s+07:00",
    "last_name": "string",
    "phone_number": "00000000"
}
```

### 2. Cập nhật, thay đổi thông tin cá nhân.

- Phương thức: PATCH
- Đường dẫn: http://portalurl/api/v1/user/update_profile/
- Tham số:

![scr13](/images/img-api/scr13.png)

- Request mẫu:

```sh
{
    "first_name": "string",
    "last_name": "string",
    "gender": 0,
    "phone_number": "string",
    "address": "string",
    "company": "string"
}
```

- Respone mẫu:

```sh
{
    "message": "string"
}
```

### 3. Thay đổi mật khẩu của người dùng.

- Phương thức: POST
- Đường dẫn: http://portalurl/api/v1/user/change_password/
- Tham số:

![scr14](/images/img-api/scr14.png)

- Request mẫu:

```sh
{
    "old_password": "string",
    "new_password": "string",
    "re_password": "string"
}
```

- Respone mẫu:

```sh
{
    "message": "string"
}
```

### 4. Liệt kê các project mà tài khoản sở hữu.

- Phương thức: GET
- Đường dẫn: http://portalurl/api/v1/user/list_project/
- Respone mẫu:

```sh
{
    "is_available": true,
    "project": "string",
    "project_user_name": "string"
}
```

---
<a href="https://cloud365.vn/" target="_blank">cloud365.vn</a>

Khi cần hỗ trợ xin liên hệ với chúng tôi:

**Công ty phần mềm Nhân Hòa**
- Trụ sở Hà Nội: 32 Võ Văn Dũng, Đống Đa, Hà Nội
- Chi nhánh HCM: 270 Cao Thắng (nối dài), Phường 12,Quận 10, TP HCM
- Hotline: `19006680`
