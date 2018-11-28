# CS.Center-Api
CS.Center Api Dökümantasyon

# Api endpoint
https://cs.center/api/ **APIKEY** / **URUNID** / **SERVIS**

# Ön bilgi
**APIKEY** inize şifre değiştirme ekranının en altında bulabilirsiniz(her şifre değişimi sonrası api key değişir).
**URUNID** Hizmetlerim kısmında yer alan ürün id


# Servisler

Metod | SERVIS | Açıklama
------------- | -------------
GET | GetAdminGroups | Aktif admin gruplarını(tip : json)
GET | GetAdmins | Aktif Adminlikleri listeler(tip : json)
GET | GetChatColors | Aktif Renkli yazıları listeler(tip : json)
GET | GetOverrides | Aktif komut üstünlüklerini listeler(tip : json)
GET | ReloadAdmins | Adminlikleri yeniler(adminlik yazım sonrası için map değişmeden adminliğin aktif olmasında kullanılmalıdır)
POST | AddAdmin | Adminlik yazım servisi
POST | AddChatColors | Renkli yazı ekleme servisi
POST | AdminSales | Adminlik ve renkli yazı ekleme servisi, adminlik satışı sonrası çağırmanız gereken servistir(eğer renkli yazı yazmayacaksanız sade addadmin i kullanabilirsiniz).

# Service Post Fields

## AddAdmin Servisi

Input | Durum | Açıklama
------------- | -------------
steamid | Gerekli | Kullanıcı Steam ID
immunity | Gerekli | Dokunulmazlık seviyesi
flags | Gerekli | Yetki bayrakları
aciklama | Opsiyonel | Açıklama

## AddChatColors Servisi

Input | Durum | Açıklama
------------- | -------------
steamid | Gerekli | Steam id
tag | Gerekli | Tag
tagkiskacstart | Gerekli | Tag başlangıç karakteri örn : [TAG] da ki [
tagkiskacend | Gerekli | Tag sonlanma karakteri örn : [TAG] da ki ]
textcolor | Gerekli | Yazı rengi
namecolor | Gerekli | İsim rengi
tagcolor | Gerekli | Tag Rengi

## AdminSales Servisi

Input | Durum | Açıklama
------------- | -------------
steamid | Gerekli | Kullanıcı Steam ID
immunity | Gerekli | Dokunulmazlık seviyesi
flags | Gerekli | Yetki bayrakları
aciklama | Opsiyonel | Açıklama
tag | Gerekli | Tag
tagkiskacstart | Gerekli | Tag başlangıç karakteri örn : [TAG] da ki [
tagkiskacend | Gerekli | Tag sonlanma karakteri örn : [TAG] da ki ]
textcolor | Gerekli | Yazı rengi
namecolor | Gerekli | İsim rengi
tagcolor | Gerekli | Tag Rengi

# Renk listesi

Kod| Renk adı
------------- | -------------
{01}|Beyaz
{02}|Koyu Kırmızı
{03}|Mor
{04}|Koyu yeşil
{05}|Açık yeşil
{06}|Yeşil
{07}|Kırmızı
{08}|Gri
{09}|Sarı
{0A}|Açık mavi
{0B}|Mavi
{0C}|Koyu mavi
{0D}|Açık gri
{0E}|Pembe
{0F}|Açık kırmızı
{10}|Turuncu
