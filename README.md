# SAÜ SÖZLÜK API DÖKÜMANTASYONU  

Saü sözlüğün andorid uygulamasını geliştirilirken böyle bir dökümantasyona ihtiyaç duydum. Tarayıcımın geliştirici araçlarından takip edebildiğim kadarını dökümante ediyorum. 
(bkz. [saü sözlük android uygulaması](https://github.com/gormelof/sau-sozluk-android))

# Başlangıç

**Base URL: http://sausozluk.net/service/proxy/api**

- [Giriş](#giriş)
- [Kayıt](#kayıt)
- [Profil](#profil)
- [Konular](#konular)
- [Ortaya Karışık](#ortaya-karışık)
- [Konuya Ait Entry](#konuya-ait-entry)
- [Entry Oluştur](#entry-oluştur)
- [Tek Entry](#tek-entry)
- [Entry Sil](#entry-sil)

## Giriş

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

## Kayıt

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

## Profil

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

## Konular

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

## Ortaya Karışık

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

## Konuya Ait Entry

**Get**

> /v1/topics/{topic_id}

**Parametreler**

|Alan            |Tip      |Açıklama                                                                          |
|----------------|---------|----------------------------------------------------------------------------------|
|`page`	         |Int      |İlgili sayfa (zorunlu değildir, varsayılan olarak sayfa 1 veriler getirilir)      |

**Örnek Başarılı Sonuç**

```json
{
    "success": true,
    "data": {
        "entries": [
            {
                "id": 2,
                "text": "sabancı üniversitesi interaktif sözlüğü. `:yersen`",
                "created_at": "2017-07-18T19:02:08.321Z",
                "updated_at": "2018-01-09T20:56:27.302Z",
                "upvotes_count": 0,
                "downvotes_count": 0,
                "user": {
                    "id": "596e57da7b8775000fc26beb",
                    "slug": "guguluk",
                    "username": "guguluk"
                }
            }
        ],
        "total_page": 6,
        "slug": "sau-sozluk",
        "title": "saü sözlük",
        "locked": false
    }
}
```

## Entry oluştur

**Post**

> /v1/entries

**Başlık (Header)**

|Alan            |Tip      |Açıklama                                        |
|----------------|---------|------------------------------------------------|
|`token`	     |String   | kullanıcıya özel oluşturulan ahahtar           |

**Parametreler (Params)**

|Alan            |Tip      |Açıklama                     |
|----------------|---------|-----------------------------|
|`text`	         |String   |entry içeriği                |
|`topic_id`      |Int      |ilgili konu                  |

**Örnek Başarılı Sonuç**

```json
{
    "success": true,
    "data": {
        "id": 8142
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

## Tek Entry

**Get**

> /v1/entries/{entry_id}

**Örnek Başarılı Sonuç**

```json
{
    "success": true,
    "data": {
        "id": 8139,
        "text": "Mimiklerine hayran olduğum [https://youtu.be/gq-WnnT74Fw?t=3145 komedyen]dir. Aynı sahnede korkudan, kardeşi rolündeki (bkz: gülse birsel)'in kucağına oturması beni benden alan bir kare olmuştur.",
        "upvotes_count": 0,
        "downvotes_count": 0,
        "created_at": "2018-03-03T01:59:51.551Z",
        "updated_at": "2018-03-03T01:59:51.551Z",
        "user": {
            "id": "598e2f25539ebb0014f525b3",
            "username": "wizard of oz",
            "slug": "wizard-of-oz"
        },
        "topic": {
            "id": 1299,
            "title": "ata demirer",
            "slug": "ata-demirer",
            "created_at": "2017-08-20T14:42:24.478Z",
            "updated_at": "2018-03-03T01:59:51.565Z"
        }
    }
}
```

## Entry Sil

**Delete**

> /v1/entries/{entry_id}

**Başlık (Header)**

|Alan            |Tip      |Açıklama                                        |
|----------------|---------|------------------------------------------------|
|`token`	     |String   | kullanıcıya özel oluşturulan ahahtar           |


**Örnek Başarılı Sonuç**

```json
{
    "success": true
}
```

**Örnek Başarısız Sonuç**

```json
{
    "success":false,
    "message":"hata mesajı"
}
```
