---
title: Развертывание рабочих папок с помощью AD FS и прокси-службы веб-приложения. Шаг 2. Действия после настройки AD FS
ms.prod: windows-server
ms.technology: storage-work-folders
ms.topic: article
manager: klaasl
ms.author: jeffpatt
author: JeffPatt24
ms.date: 06/06/2019
ms.assetid: 0a48852e-48cc-4047-ae58-99f11c273942
ms.openlocfilehash: 42e7477c168b0b7c1230fd37b5fb26d77590ef1c
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86965776"
---
# <a name="deploy-work-folders-with-ad-fs-and-web-application-proxy-step-2-ad-fs-post-configuration-work"></a>Развертывание рабочих папок с помощью AD FS и прокси-службы веб-приложения. Шаг 2. Действия после настройки AD FS

>Применяется к: Windows Server (Semi-Annual Channel), Windows Server 2016

В этой статье описывается второй шаг процесса развертывания рабочих папок с помощью службы федерации Active Directory (AD FS) и прокси-службы веб-приложения. Другие шаги этого процесса можно найти в следующих статьях:  
  
-   [Развертывание рабочих папок с помощью AD FS и прокси веб-приложения: обзор](deploy-work-folders-adfs-overview.md)  
  
-   [Развертывание рабочих папок с помощью AD FS и прокси-службы веб-приложения. Шаг 1. Настройка AD FS](deploy-work-folders-adfs-step1.md)  
  
-   [Развертывание рабочих папок с помощью AD FS и прокси-службы веб-приложения. Шаг 3. Настройка рабочих папок](deploy-work-folders-adfs-step3.md)  
  
-   [Развертывание рабочих папок с помощью AD FS и прокси-службы веб-приложения. Шаг 4. Настройка прокси-службы веб-приложения](deploy-work-folders-adfs-step4.md)  
  
-   [Развертывание рабочих папок с помощью AD FS и прокси-службы веб-приложения. Шаг 5. Настройка клиентов](deploy-work-folders-adfs-step5.md)  
  
> [!NOTE]
> Инструкции, описанные в этом разделе, предназначены для среды Windows Server 2019 или Windows Server 2016. Если вы используете Windows Server 2012 R2, следуйте [инструкциями для Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn747208(v=ws.11)).

На шаге 1 вы установили и настроили AD FS. Теперь необходимо выполнить следующие действия после настройки для AD FS.  
  
## <a name="configure-dns-entries"></a>Настройка записей DNS

Вам необходимо создать две записи DNS для AD FS. Эти две записи уже использовались на шагах по подготовке к установке при создании сертификата с альтернативным именем субъекта (SAN).  
  
Записи DNS имеют следующий вид:  
  
-   имя службы AD FS.домен  
  
-   enterpriseregistration.домен  
  
-   имя сервера AD FS.domain   (Запись DNS уже должна существовать. Например, 2016-ADFS.contoso.com)
  
В тестовом примере используются следующие значения:  
  
-   **blueadfs.contoso.com**  
  
-   **enterpriseregistration.contoso.com**  
  
## <a name="create-the-a-and-cname-records-for-ad-fs"></a>Создание записей A и CNAME для AD FS

Чтобы создать записи A и CNAME для AD FS, выполните следующие действия.  
  
1.  На контроллере домена откройте раздел "Диспетчер DNS".  
  
2.  Разверните папку "Зоны прямого просмотра", щелкните правой кнопкой мыши домен и выберите **Новый узел (A)**.  
  
3.  Откроется окно **Новый узел**. В поле **Имя** введите псевдоним для имени службы AD FS. В тестовом примере используется имя **blueadfs**.  
  
    Псевдоним должен совпадать с субъектом в сертификате, использованным для AD FS. Например, если субъектом был adfs.contoso.com, для псевдонима здесь было бы введено значение **adfs**.  
  
    > [!IMPORTANT]  
    > При настройке AD FS с помощью пользовательского интерфейса Windows Server, а не Windows PowerShell, необходимо создать запись A вместо CNAME для AD FS. Причина этого в том, что имя субъекта-службы, созданное с помощью пользовательского интерфейса, содержит только псевдоним, используемый для настройки службы AD FS в качестве узла.  

4.  В поле **IP-адрес** введите IP-адрес сервера AD FS. В тестовом примере используется адрес **192.168.0.160**. Нажмите кнопку **Добавить узел**.  
  
5.  В папке "Зоны прямого просмотра" щелкните правой кнопкой мыши домен и выберите **Новый псевдоним (CNAME)**.  
  
6.  В окне **Новая запись ресурса** добавьте имя псевдонима **enterpriseregistration** и введите FQDN для сервера AD FS. Этот псевдоним используется для присоединения устройств и должен иметь имя **enterpriseregistration**.
  
7.  Нажмите кнопку **ОК**.  
  
Чтобы выполнить те же действия через Windows PowerShell, используйте следующую команду. Команду необходимо выполнить на контроллере домена.  
  
```Powershell  
Add-DnsServerResourceRecord  -ZoneName "contoso.com" -Name blueadfs -A -IPv4Address 192.168.0.160   
Add-DnsServerResourceRecord  -ZoneName "contoso.com" -Name enterpriseregistration -CName  -HostNameAlias 2016-ADFS.contoso.com
```  
  
## <a name="set-up-the-ad-fs-relying-party-trust-for-work-folders"></a>Настройка отношений доверия с проверяющей стороной AD FS для рабочих папок

Вы можете настроить отношения доверия с проверяющей стороной для рабочих папок, несмотря на то что рабочие папки еще не настроены. Необходимо настроить отношения доверия с проверяющей стороной, чтобы рабочие папки могли использовать AD FS. Так как вы настраиваете AD FS, самое время выполнить этот шаг.  
  
Настройка отношений доверия с проверяющей стороной:  
  
1.  Откройте **Диспетчер сервера** и в меню **Средства** выберите **Управление AD FS**.  
  
2.  На панели справа в разделе **Действия** нажмите **Добавить отношения доверия с проверяющей стороной**.  
  
3.  На странице **Приветствие** выберите **Поддержка утверждений** и нажмите **Пуск**.  
  
4.  На странице **Выбор источника данных** выберите **Ввод данных о проверяющей стороне вручную** и нажмите кнопку **Далее**.  
  
5.  В поле **Отображаемое имя** введите **WorkFolders** и нажмите **Далее**.  
  
6.  На странице **Настройка сертификата** нажмите кнопку **Далее**. Сертификаты шифрования маркеров необязательны и не требуются для тестовой конфигурации.  
  
7.  На странице **Настройка URL-адреса** нажмите кнопку **Далее**.  
  
8. На странице **Настройка идентификаторов** добавьте следующий идентификатор: `https://windows-server-work-folders/V1` . Этот идентификатор представляет собой жестко заданное значение, используемое рабочими папками, и отправляется службой рабочих папок при обмене данными с AD FS. Щелкните **Далее**.  
  
9. На странице "Выбор политики контроля доступа" выберите **Разрешить всем** и нажмите кнопку **Далее**.  
  
10. На странице **Готово к добавлению отношений доверия** щелкните **Далее**.  
  
11. После завершения настройки на последней странице мастера будет указано, что настройка прошла успешно. Выберите флажок для изменения правил утверждений и нажмите **Закрыть**.  
  
12. В оснастке AD FS выберите отношения доверия с проверяющей стороной **WorkFolders** и нажмите **Изменить политику выдачи утверждений**.

13. Откроется окно **Изменение политики выдачи утверждений**. Нажмите кнопку **Добавить правило**.  
  
14. В раскрывающемся списке **Шаблон правила утверждений** выберите **Отправлять атрибуты LDAP в виде утверждений** и нажмите **Далее**.  
  
15. На странице **Настройка правил утверждений** в поле **Имя правила утверждений** введите **WorkFolders**.  
  
16. В раскрывающемся списке **Хранилище атрибутов** выберите **Active Directory**.  
  
17. В таблице сопоставлений введите следующие значения:  
  
    -   Имя участника-пользователя: имя участника пользователя  
  
    -   Отображаемое имя: имя  
  
    -   Фамилия: фамилия  
  
    -   Заданное имя: заданное имя  
  
18. Нажмите кнопку **Готово**. На вкладке "Правила преобразования выдачи" будет указано правило WorkFolders. Нажмите кнопку **ОК**.  
  
### <a name="set-relying-part-trust-options"></a>Настройка параметров отношений доверия с проверяющей стороной

После настройки отношений доверия с проверяющей стороной для AD FS необходимо завершить настройку путем выполнения пяти команд в Windows PowerShell. Эти команды настраивают параметры, которые нужны рабочим папкам для успешного обмена данными с AD FS и не могут быть настроены через пользовательский интерфейс. Доступны следующие параметры:  
  
-   включение использования веб-маркеров JSON (JWT);  
  
-   отключение зашифрованных утверждений;  
  
-   включение автоматического обновления;  
  
-   установка выдачи маркеров обновления Oauth для всех устройств.  

-   Предоставление клиентам доступа к отношениями доверия с проверяющей стороной

Для настройки этих параметров используйте следующие команды:  
  
```powershell  
Set-ADFSRelyingPartyTrust -TargetIdentifier "https://windows-server-work-folders/V1" -EnableJWT $true   
Set-ADFSRelyingPartyTrust -TargetIdentifier "https://windows-server-work-folders/V1" -Encryptclaims $false   
Set-ADFSRelyingPartyTrust -TargetIdentifier "https://windows-server-work-folders/V1" -AutoupdateEnabled $true   
Set-ADFSRelyingPartyTrust -TargetIdentifier "https://windows-server-work-folders/V1" -IssueOAuthRefreshTokensTo AllDevices
Grant-AdfsApplicationPermission -ServerRoleIdentifier "https://windows-server-work-folders/V1" -AllowAllRegisteredClients -ScopeNames openid,profile  
```  
  
## <a name="enable-workplace-join"></a>Включение Workplace Join

Включать Workplace Join не обязательно, но это может быть полезным, если вам требуется предоставить пользователям возможность использовать их персональные устройства для доступа к рабочим ресурсам.  
  
Чтобы включить регистрацию устройств для Workplace Join, необходимо выполнить следующие команды Windows PowerShell, которые настроят регистрацию устройств и установят глобальную политику проверки подлинности:  
  
```powershell  
Initialize-ADDeviceRegistration -ServiceAccountName <your AD FS service account>
    Example: Initialize-ADDeviceRegistration -ServiceAccountName contoso\adfsservice$
Set-ADFSGlobalAuthenticationPolicy -DeviceAuthenticationEnabled $true   
```  
  
## <a name="export-the-ad-fs-certificate"></a>Экспорт сертификата AD FS

Далее экспортируйте самозаверяющий сертификат AD FS, чтобы установить его на следующие компьютеры в тестовой среде:  
  
-   сервер, используемый для рабочих папок;  
  
-   сервер, используемый для прокси-службы веб-приложения;  
  
-   присоединенный к домену клиент Windows;  
  
-   не присоединенный к домену клиент Windows.  
  
Для экспорта сертификата выполните следующие действия:  
  
1.  Нажмите кнопку **Пуск**, затем щелкните **Выполнить**.  
  
2.  Введите **MMC**.  
  
3.  В меню **Файл** выберите **Добавить или удалить оснастку**.  
  
4.  В списке **Доступные оснастки** выберите пункт **Сертификаты** и нажмите кнопку **Добавить**. Запустится мастер оснастки сертификатов.  
  
5.  Выберите **Учетная запись компьютера** и нажмите кнопку **Далее**.  
  
6.  Выберите **Локальный компьютер: (компьютер, на котором запущена эта консоль)** и нажмите кнопку **Готово**.  
  
7.  Нажмите кнопку **ОК**.  
  
8.  Раскройте **консоль папки Рут\цертификатес \( локальный компьютер) \персонал\цертификатес**.  
  
9.  Щелкните правой кнопкой мыши **Сертификат AD FS**, нажмите **Все задачи**, а затем — **Экспорт...**.  
  
10. Откроется мастер экспорта сертификатов. Выберите **Да, экспортировать закрытый ключ**.  
  
11. На странице **Формат экспортируемого файла** оставьте параметры по умолчанию и нажмите кнопку **Далее**.  
  
12. Создайте пароль для сертификата. Этот пароль вам пригодится позднее при импорте сертификата на другие устройства. Щелкните **Далее**.  
  
13. Введите расположение и имя для сертификата и нажмите кнопку **Готово**.  
  
Процесс установки сертификата описан далее в рамках процедуры развертывания.  
  
## <a name="manage-the-private-key-setting"></a>Управление настройкой закрытого ключа

Вам необходимо предоставить учетной записи службы AD FS разрешение на доступ к закрытому ключу нового сертификата. Вам снова потребуется предоставить это разрешение при замене сертификата обмена данными после истечения срока его действия. Чтобы предоставить разрешение, сделайте следующее:  
  
1.  Нажмите кнопку **Пуск**, затем щелкните **Выполнить**.  
  
2.  Введите **MMC**.  
  
3.  В меню **Файл** выберите **Добавить или удалить оснастку**.  
  
4.  В списке **Доступные оснастки** выберите пункт **Сертификаты** и нажмите кнопку **Добавить**. Запустится мастер оснастки сертификатов.  
  
5.  Выберите **Учетная запись компьютера** и нажмите кнопку **Далее**.  
  
6.  Выберите **Локальный компьютер: (компьютер, на котором запущена эта консоль)** и нажмите кнопку **Готово**.  
  
7.  Нажмите кнопку **ОК**.  
  
8.  Раскройте **консоль папки Рут\цертификатес \( локальный компьютер) \персонал\цертификатес**.  
  
9.  Щелкните правой кнопкой мыши **Сертификат AD FS**, нажмите **Все задачи**, а затем — **Управление закрытыми ключами**.  
  
10. В окне **Разрешения** нажмите **Добавить**.  
  
11. В окне **Типы объектов** выберите **Учетные записи служб** и нажмите кнопку **ОК**.  
  
12. Введите имя учетной записи, под которой выполняется AD FS. В тестовом примере используется имя ADFSService. Нажмите кнопку **ОК**.  
  
13. В окне **Разрешения** предоставьте учетной записи хотя бы разрешения на чтение и нажмите кнопку **ОК**.  
  
Если у вас нет возможности управлять закрытыми ключами, может потребоваться выполнить следующую команду:`certutil -repairstore my *`  
  
## <a name="verify-that-ad-fs-is-operational"></a>Проверка работоспособности AD FS

Чтобы убедиться, что AD FS работает, откройте окно браузера и перейдите к `https://blueadfs.contoso.com/federationmetadata/2007-06/federationmetadata.xml` , изменив URL-адрес в соответствии с вашей средой.
  
В окне браузера отобразятся метаданные сервера федерации без форматирования. Если вы видите данные без ошибок или предупреждений SSL, ваш сервер федерации работает.  
  
Следующий шаг: [Развертывание рабочих папок с помощью AD FS и прокси-службы веб-приложения. Шаг 3. Настройка рабочих папок](deploy-work-folders-adfs-step3.md)  
  
## <a name="see-also"></a>См. также  
[Обзор рабочих папок](Work-Folders-Overview.md)
