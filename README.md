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

**Örnek Başarılı Sonuç**

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

**Örnek Başarısız Sonuç**

```json
{
    "success":false,
    "message":"hata mesajı"
}
```

## User - Register User (Kullanıcı Kaydı)

**Post**

> /v1/users

**Parametreler**

|Alan            |Tip      |Açıklama                     |
|----------------|---------|-----------------------------|
|`email`	     |String   |kullanıcı e-posta adresi     |
|`password`      |String   |kullanıcı parolası           |
|`username`      |String   |kullanıcı adı (nick)         |

**Örnek Başarılı Sonuç**

```json
{
    "success":true
}
```

**Örnek Başarısız Sonuç**

```json
{
    "success":false,
    "message":"hata mesajı"
}
```

## User - User Profile (Kullanıcı Profili)

**Post**

> /v1/users/profile/{username}

**Örnek Başarılı Sonuç**

```json
{
    {
    "success":true,
    "data":{
        "entry_count":1550,
        "last_entries":[
            {
                "id":8117,
                "title":"iyi yürekli"
            }
        ],
        "most_liked":[
            {
                "id":5540,
                "title":"kullanım şartlarını okudum kabul ediyorum"
            }
        ],
        "most_hated":[
            {
                "id":5469,
                "title":"entry girerken lafın lafı açması"
            }
        ],
        "liked":[
            {
                "id":8025,
                "title":"boston dynamics"
            }
        ],
        "username":"test",
        "last_activities":[
            {
                "_id":"5a991c4989c136777ff60efd",
                "data":{

                },
                "action":"logout",
                "date":"2018-03-02T09:41:29.060Z"
            },
            {
                "_id":"5a991c4989c136777ff60efd",
                "data":{

                },
                "action":"login",
                "date":"2018-03-02T10:47:25.618Z"
            }
        ],
        "generation":"1",
        "status":"mod",
        "online":false
    }
}
```

**Örnek Başarısız Sonuç**

```json
{
    "success":false,
    "message":"hata mesajı"
}
```


