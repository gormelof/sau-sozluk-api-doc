# SAÜ SÖZLÜK API DÖKÜMANTASYONU  

Saü sözlüğün andorid uygulamasını geliştirilirken böyle bir dökümantasyona ihtiyaç duydum. Tarayıcımın geliştirici araçlarından takip edebildiğim kadarını dökümante ediyorum. 
(bkz. [saü sözlük android uygulaması](https://github.com/gormelof/sau-sozluk-android))

## Sessions - Login User (Kullanıcı Girişi)

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

## Users - Register User (Kullanıcı Kaydı)

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

## Users - User Profile (Kullanıcı Profili)

**Get**

> /v1/users/profile/{username}

**Örnek Başarılı Sonuç**

```json
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
            }
        ],
        "generation":"1",
        "status":"mod",
        "online":false
    }
}
```

## Random - Random Entries (Ortaya karışık beş entry getirir)

**Get**

> /v1/topics/i/random

**Örnek Başarılı Sonuç**

```json
{
    "success": true,
    "data": [
        {
            "entry": {
                "id": 485,
                "user": {
                    "id": "596ef4332f371a000f086e96",
                    "slug": "hamlet",
                    "username": "hamlet"
                },
                "text": "tebrik de değildir.",
                "upvotes_count": 2,
                "downvotes_count": 0,
                "created_at": "2017-07-19T13:17:12.247Z",
                "updated_at": "2017-07-24T08:32:07.016Z"
            },
            "topic": {
                "id": 223,
                "slug": "ersan-kuneri",
                "title": "erşan kuneri"
            }
        }
    ]
}
```

## Topics - Topics (Konular)

**Get**

> /v1/topics

**Parametreler**

|Alan            |Tip      |Açıklama                                                               |
|----------------|---------|-----------------------------------------------------------------------|
|`count`	     |Int      |Konu sayısı (zorunlu değildir, varsayılan olarak 20 tane getirir)      |

**Örnek Başarılı Sonuç**

```json
{
    "success": true,
    "data": {
        "entries_count": 2,
        "topics": [
            {
                "id": 4007,
                "slug": "dilsiz-usak",
                "title": "dilsiz uşak",
                "count": 1,
                "updated_at": "2018-03-03T10:23:08.683Z",
                "created_at": "2018-03-03T10:23:08.683Z",
                "page": 1
            }
        ],
        "topics_count": 1
    }
}
```


