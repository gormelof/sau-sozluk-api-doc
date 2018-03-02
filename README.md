# SAÜ SÖZLÜK API DÖKÜMANTASYONU  

Saü sözlüğün andorid uygulamasını geliştirilirken böyle bir dökümantasyona ihtiyaç duydum. Tarayıcımın geliştirici araçlarından takip edebildiğim kadarını dökümante ediyorum. 
(bkz. [saü sözlük android uygulaması](https://github.com/gormelof/sau-sozluk-android))

## User - Login User (Kullanıcı Giriş)

**Post**

> /v1/sessions

**Parametreler**

|Alan            |Tip      |Açıklama                     |
|----------------|---------|-----------------------------|
|`email`	     |String   |kullanıcı e-posta adresi     |
|`password`      |String   |kullanıcı parolası           |

**Başarılı Sonuç**

```json
{
    "success":true,
    "data":{
        "user_id":"695d8a6572229a111fbb1fa0",
        "token":"IrZgwOzFpWcQR1wWC7LUdSqgQwYPUfi1",
        "email":"test@test.com",
        "username":"test test",
        "slug":"test-test",
        "authority":0,
        "unread":0
    }
}
```

**Başarısız Sonuç**

```json
{
    "success":false,
    "message":"hata mesajı"
}
```
