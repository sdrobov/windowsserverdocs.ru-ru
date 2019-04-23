Во-первых получите сертификат SSL для HGS из центра сертификации. Каждый хост-компьютере необходимо доверять сертификату SSL, поэтому мы рекомендуем выпускать SSL-сертификат от компании открытого ключа инфраструктуры или третьей стороны ЦС. SSL-сертификат, поддерживаемых службами IIS поддерживается HGS, тем не менее **имя субъекта сертификата должно соответствовать имени службы полное HGS** (имя распределенной сети кластера). Например если домен HGS — «bastion.local» и «hgs» — имя службы HGS, SSL-сертификат должен быть выдан «hgs.bastion.local». В поле альтернативного имени субъекта сертификата при необходимости можно добавить дополнительные DNS-имена.

После того как у вас есть SSL сертификатов, откройте сеанс с повышенными правами PowerShelll и укажите путь к сертификату при запуске [HgsServer набора](https://technet.microsoft.com/itpro/powershell/windows/host-guardian-service/server/set-hgsserver):


```powershell
$sslPassword = Read-Host -AsSecureString -Prompt "SSL Certificate Password"
Set-HgsServer -Http -Https -HttpsCertificatePath 'C:\temp\HgsSSLCertificate.pfx' -HttpsCertificatePassword $sslPassword
```

Или, если вы уже установили сертификат в локальном хранилище сертификатов, можно создать ссылку по отпечатку:

```powershell
Set-HgsServer -Http -Https -HttpsCertificateThumbprint 'A1B2C3D4E5F6...'
```

> [!IMPORTANT]
> Настройка HGS с помощью SSL-сертификат не отключает конечную точку HTTP.
> Если вы хотите только разрешает использовать конечную точку HTTPS, настройте брандмауэр Windows, чтобы блокировать входящие соединения на порт 80.
> **Не изменяйте привязки IIS** для веб-сайтов HGS удалить конечную точку HTTP; он не поддерживается для этого.
