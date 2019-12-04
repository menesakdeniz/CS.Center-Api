# CS.Center-Api
CS.Center Api Dökümantasyon

Hazır PHP Api için https://github.com/emrezorlu/cs.center adresine bakabilirsiniz.

# Api endpoint
https://cs.center/api/ **APIKEY** / **URUNID** / **SERVIS**

# Ön bilgi
**APIKEY** inize şifre değiştirme ekranının en altında bulabilirsiniz(her şifre değişimi sonrası api key değişir). 
**URUNID** Hizmetlerim kısmında yer alan ürün id 
 
Auth gerekmeyen servislerde, ip adresini APIKEY, portu ise URUNID olarak yazabilirsiniz. 
 
örneğin : 
https://cs.center/api/ 45.10.56.1 / 27015 / GetServerInfo 

https://cs.center/api/ 45.10.56.1 / 27015 / GetPlayerInfo 


# Servisler

Metod | SERVIS | Açıklama | Rate(Limit) | Auth
------------- | ------------- | ------------- | ------------- | ------------- 
GET | GetDonationHistory | Sisteme gelen bağışları listele(tip : json) | 60 Req/min | Gerekli 
GET | GetAdminGroups | Aktif admin gruplarını(tip : json) | 60 Req/min | Gerekli 
GET | GetAdmins | Aktif Adminlikleri listeler(tip : json) | 60 Req/min | Gerekli 
GET | GetChatColors | Aktif Renkli yazıları listeler(tip : json) | 60 Req/min | Gerekli 
GET | GetOverrides | Aktif komut üstünlüklerini listeler(tip : json) | 60 Req/min | Gerekli 
GET | ReloadAdmins | Adminlikleri yeniler(adminlik yazım sonrası için map değişmeden adminliğin aktif olmasında kullanılmalıdır) | 60 Req/min | Gerekli 
POST | AddAdmin | Adminlik yazım servisi | 60 Req/min | Gerekli 
POST | DeleteAdmin | Adminlik silme servisi | 60 Req/min | Gerekli 
POST | AddChatColors | Renkli yazı ekleme servisi | 60 Req/min | Gerekli 
POST | AdminSales | Adminlik ve renkli yazı ekleme servisi, adminlik satışı sonrası çağırmanız gereken servistir(eğer renkli yazı yazmayacaksanız sade addadmin i kullanabilirsiniz). | 60 Req/min | Gerekli 
POST | SendRcon | Rcon komutu servisi | 60 Req/min | Gerekli 
GET | GetServerInfo | Server adını, oyuncu sayısını ve max kapasiteyi döndüren servis(A2S_Query) | 60 Req/min | Gereksiz 
GET | GetPlayerInfo | Server player bilgilerini döndüren servis(A2S_Player) | 60 Req/min | Gereksiz

# Service Post Fields

## AddAdmin Servisi

Input | Durum | Açıklama
------------- | ------------- | -------------
steamid | Gerekli | Kullanıcı Steam ID
immunity | Gerekli | Dokunulmazlık seviyesi
flags | Gerekli | Yetki bayrakları
aciklama | Opsiyonel | Açıklama
bitistarihi | Gerekli | Bitiş tarihi(unix timestamp)(0 => süresiz)

## DeleteAdmin Servisi

Input | Durum | Açıklama
------------- | ------------- | -------------
steamid | Gerekli | Silinecek Admin Steam ID

## AddChatColors Servisi

Input | Durum | Açıklama
------------- | ------------- | -------------
steamid | Gerekli | Steam id
tag | Gerekli | Tag
tagkiskacstart | Gerekli | Tag başlangıç karakteri örn : [TAG] da ki [
tagkiskacend | Gerekli | Tag sonlanma karakteri örn : [TAG] da ki ]
textcolor | Gerekli | Yazı rengi
namecolor | Gerekli | İsim rengi
tagcolor | Gerekli | Tag Rengi

## AdminSales Servisi

Input | Durum | Açıklama
------------- | ------------- | -------------
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
customerapi | Gerekli | Panelde ki adminlik gruplarını kullanma(0 => Kendi datalarımı kullan, 1=> Panelde ki taslakları kullan)
bitistarihi | Gerekli | Bitiş tarihi(unix timestamp)(0 => süresiz)

## SendRcon Servisi

Input | Durum | Açıklama
------------- | ------------- | -------------
cmd | Gerekli | Yollanacak komut

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
