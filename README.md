# Bug Reports

## Environment
- Base URL: https://api.example.com
- Endpoint: POST /login

---

## BUG-001 Login succeeds with empty password

### Steps to reproduce:
1. Send POST /login request
2. Body:
```json
{
  "email": "test@test.com",
  "password": ""
}
```

### Expected result:
Status: 400 Bad Request  
Error message about empty password

### Actual result:
Status: 200 OK  
User is authenticated successfully and receives access token

### Severity:
High

---

## BUG-002 Login succeeds with empty email

### Steps to reproduce:
1. Send POST /login request
2. Body:
```json
{
  "email": "",
  "password": "123456"
}
```

### Expected result:
Status: 400 Bad Request  
Error message about empty email

### Actual result:
Status: 200 OK  
User is authenticated successfully and receives access token

### Severity:
High

---

## BUG-003 No validation for missing fields

### Steps to reproduce:
1. Send POST /login request
2. Body:
```json
{
}
```

### Expected result:
Status: 400 Bad Request  
Validation error

### Actual result:
Status: 500 Internal Server Error  
Server crashes

### Severity:
Critical

### Impact:
Critical issue: server instability and potential crash under invalid input
