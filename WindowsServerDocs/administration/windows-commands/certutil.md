---
title: certutil
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c264ccf0-ba1e-412b-9dd3-d77dd9345ad9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8248f5ae540866394169229f0d7cf11497c9dcf2
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59834725"
---
# <a name="certutil"></a>certutil



Certutil.exe – это командной строки программа, которая устанавливается как часть служб сертификации. Можно использовать Certutil.exe дампа и отображение сведений о конфигурации центра сертификации (ЦС) сертификации, настроить службы сертификатов резервного копирования и восстановления компонентов ЦС и проверить сертификаты, пары ключей и цепочек сертификатов.

Если certutil запускается на компьютере центра сертификации без дополнительных параметров, он отображает текущую конфигурацию центра сертификации. Если cerutil запускается на компьютере без сертификации, по умолчанию используется под управлением certutil [-дампа](#BKMK_dump) команды.

> [!WARNING]
> Более ранние версии certutil может не предоставлять все параметры, описанные в этом документе. Можно просмотреть все параметры, которые предоставляет определенную версию certutil, выполнив команды, показанные в [нотации синтаксиса](#BKMK_notations) раздел.

## <a name="BKMK_menu"></a>Меню

Ниже приведены основных подразделов в этом документе.
-   [Команды](#BKMK_Verbs)
-   [Обозначения синтаксиса](#BKMK_notations)
-   [Параметры](#BKMK_Options)
-   [Примеры дополнительных certutil](#BKMK_AddedExamples)

## <a name="BKMK_Verbs"></a>Команды

В следующей таблице описаны команды, которые могут использоваться с помощью команды certutil.

|Команды|Описание|
|-----|-----------|
|[-дампа](#BKMK_dump)|Дамп данных или файлов конфигурации|
|[-asn](#BKMK_asn)|Синтаксический анализ файла ASN.1|
|[-decodehex](#BKMK_decodehex)|Расшифровать файл в шестнадцатеричной кодировке|
|[-декодирования](#BKMK_decode)|Декодировать файл с кодировкой Base64|
|[-кодирования](#BKMK_encode)|Закодировать файл в кодировке Base64|
|[— запретить](#BKMK_deny)|Запретить ожидаемого запроса сертификата|
|[-повторной отправки](#BKMK_resubmit)|Отправьте повторно ожидающий запрос сертификата|
|[-setattributes](#BKMK_setattributes)|Задание атрибутов для ожидаемого запроса сертификата|
|[-setextension](#BKMK_setextension)|Установить расширение для ожидаемого запроса сертификата|
|[-отозвать](#BKMK_revoke)|Отзыв сертификата|
|[-isvalid](#BKMK_isvalid)|Отображение метода обработки текущего сертификата|
|[-getconfig](#BKMK_getconfig)|Получить строку конфигурации по умолчанию|
|[-проверки связи](#BKMK_ping)|Запросить интерфейс Active Directory Certificate Services запрос|
|-pingadmin|Свяжется интерфейса администратора служб сертификатов Active Directory|
|[-CAInfo](#BKMK_CAInfo)|Отображение информации о центре сертификации|
|[-ca.cert](#BKMK_ca.cert)|Получить сертификат для центра сертификации|
|[-ca.chain](#BKMK_ca.chain)|Извлечь цепочку сертификатов центра сертификации|
|[-GetCRL](#BKMK_GetCRL)|Получить список отзыва сертификатов (CRL)|
|[-CRL](#BKMK_CRL)|Публикация новых списков отзыва сертификатов (CRL) [или только разностных списков отзыва сертификатов]|
|[— Завершение работы](#BKMK_shutdown)|Завершение служб сертификатов Active Directory|
|[-installCert](#BKMK_installcert)|Установить сертификат центра сертификации|
|[-renewCert](#BKMK_renewcert)|Продлить сертификат центра сертификации|
|[-схемы](#BKMK_schema)|Дамп схемы для сертификата|
|[-представление](#BKMK_view)|Дамп просмотра сертификата|
|[-db](#BKMK_db)|Дамп необработанной базы данных|
|[-deleterow](#BKMK_deleterow)|Удаление строки из базы данных сервера|
|[-резервного копирования](#BKMK_backup)|Службы сертификатов резервного копирования Active Directory|
|[-backupDB](#BKMK_backupDB)|Резервное копирование базы данных служб сертификатов Active Directory|
|[-backupKey](#BKMK_backupKey)|Службы сертификатов Active Directory сертификат и закрытый ключ для резервного копирования|
|[-Восстановление](#BKMK_restore)|Восстановление служб сертификатов Active Directory|
|[-restoreDB](#BKMK_restoreDB)|Восстановление базы данных служб сертификатов Active Directory|
|[-restoreKey](#BKMK_restorekey)|Восстановление служб сертификатов Active Directory сертификат и закрытый ключ|
|[-importPFX](#BKMK_importPFX)|Импорт сертификата и закрытого ключа|
|[-dynamicfilelist](#BKMK_dynamicfilelist)|Отобразить список динамических файлов|
|[-databaselocations](#BKMK_databaselocations)|Отображения расположения базы данных|
|[-hashfile](#BKMK_hashfile)|Создать и отобразить криптографический хэш над файлом|
|[-хранения](#BKMK_Store)|Дамп хранилища сертификатов|
|[-addstore](#BKMK_addstore)|Добавление сертификата в хранилище|
|[-delstore](#BKMK_delstore)|Удаление сертификата из хранилища|
|[-verifystore](#BKMK_verifystore)|Проверить сертификат в хранилище|
|[-repairstore](#BKMK_repairstore)|Восстановить сопоставления на основе ключа либо обновление свойств сертификата или дескриптор ключа безопасности|
|[-viewstore](#BKMK_viewstore)|Дамп в хранилище сертификатов|
|[-viewdelstore](#BKMK_viewdelstore)|Удаление сертификата из хранилища|
|[-dsPublish](#BKMK_dsPublish)|Опубликовать сертификат или список отзыва сертификатов (CRL) в Active Directory|
|[-ADTemplate](#BKMK_ADTemplate)|Шаблоны отображения AD|
|[-Шаблона](#BKMK_template)|Отображение шаблонов сертификатов|
|[-TemplateCAs](#BKMK_TemplateCAs)|Отобразить центров сертификации (ЦС) для шаблона сертификата|
|[-CATemplates](#BKMK_CATemplates)|Отображение шаблонов для ЦС|
|[-SetCASites](#BKMK_SetCASites)|Управление именами сайт для ЦС|
|[-enrollmentServerURL](#BKMK_enrollmentServerURL)|Отображения, добавить или удалить URL-адреса сервера регистрации, связанные с ЦС|
|[-ADCA](#BKMK_ADCA)|Отобразить центров сертификации AD|
|[-CA](#BKMK_CA)|Отображение ЦС политики регистрации|
|[-Policy](#BKMK_Policy)|Отображение политики регистрации|
|[-PolicyCache](#BKMK_PolicyCache)|Отображение или удаление записей кэша политики регистрации|
|[-CredStore](#BKMK_Credstore)|Отображения, добавить или удалить записи учетных данных Store|
|[-InstallDefaultTemplates](#BKMK_InstallDefaultTemplates)|Установите шаблоны сертификатов по умолчанию|
|[-URLCache](#BKMK_URLCache)|Отображение или удаление записей кэша URL-адрес|
|[-pulse](#BKMK_pulse)|Pulse автоматической регистрации событий|
|[-MachineInfo](#BKMK_MachineInfo)|Отобразить сведения об объекте машины Active Directory|
|[-DCInfo](#BKMK_DCInfo)|Отображение информации о контроллере домена|
|[-EntInfo](#BKMK_EntInfo)|Отображение сведений об ЦС предприятия|
|[-TCAInfo](#BKMK_TCAInfo)|Отображение информации о ЦС|
|[-SCInfo](#BKMK_SCInfo)|Отображение информации о смарт-карты|
|[-SCRoots](#BKMK_SCRoots)|Управление корневые сертификаты смарт-карты|
|[-verifykeys](#BKMK_verifykeys)|Проверить набор общедоступных или частных ключей|
|[— Проверка](#BKMK_verify)|Проверка сертификата и списка отзыва сертификатов (CRL) или цепочки сертификатов|
|[-verifyCTL](#BKMK_verifyCTL)|Проверка AuthRoot или запрещенных сертификатов списка доверия Сертификатов|
|[-входа](#BKMK_sign)|Повторно подписать список отзыва сертификатов (CRL) или сертификат|
|[-vroot](#BKMK_vroot)|Создание или удаление виртуальных корней Веба и общих папок|
|[-vocsproot](#BKMK_vocsproot)|Создание или удаление виртуальных корней Веба для веб-прокси OCSP|
|[-addEnrollmentServer](#BKMK_addEnrollmentServer)|Добавление сервера регистрации приложения|
|[-deleteEnrollmentServer](#BKMK_deleteEnrollmentServer)|Удалить приложение сервера регистрации|
|[-addPolicyServer](#BKMK_addPolicyServer)|Добавление политики серверного приложения|
|[-deletePolicyServer](#BKMK_deletePolicyServer)|Удаление политики серверного приложения|
|[-oid](#BKMK_oid)|Отобразить идентификатор объекта или задать отображаемое имя|
|[-Ошибка](#BKMK_error)|Отобразить текст сообщения, связанного с кодом ошибки|
|[-getreg](#BKMK_getreg)|Отобразить значение реестра|
|[-setreg](#BKMK_setreg)|Задание значения реестра|
|[-delreg](#BKMK_delreg)|Удалить значение реестра|
|[-ImportKMS](#BKMK_ImportKMS)|Импорт пользовательских ключей и сертификатов в базе данных сервера для архивации ключа|
|[-ImportCert](#BKMK_ImportCert)|Импорт файла сертификата в базу данных|
|[-GetKey](#BKMK_GetKey)|Получить большой двоичный объект восстановления заархивированного закрытого ключа|
|[-RecoverKey](#BKMK_RecoverKey)|Восстановление архивированного закрытого ключа|
|[-MergePFX](#BKMK_MergePFX)|Слияние файлов PFX|
|[-ConvertEPF](#BKMK_ConvertEPF)|Преобразовать в PFX-файл в файл EPF|
|-?|Отображает список команд|
|-*\<Команда >* -?|Отображает справку по указанная команда.|
|-? -v|Отображает полный список команд и|

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_notations"></a>Обозначения синтаксиса

-   Базовый синтаксис командной строки запустите `certutil -?`
-   Синтаксис, об использовании определенной команды certutil, выполните **certutil**  *\<глагол >* **-?**
-   Чтобы отправить certutil синтаксиса, в текстовый файл, выполните следующие команды:  
    -   `certutil -v -? > certutilhelp.txt`
    -   `notepad certutilhelp.txt`

В следующей таблице описаны представления, используемые в синтаксисе командной строки.

|Нотация|Описание|
|--------|-----------|
|Текст без квадратных или фигурных скобок|Элементы, которые необходимо указать, как показано|
|\<Текст в угловых скобках >|Заполнитель, для которого необходимо указать значение|
|[Текст в квадратных скобках]|Необязательные элементы|
|{Текст в фигурных скобках}|Набор обязательных элементов Выберите один|
|Вертикальная черта ()|)|Разделитель для элементов взаимно исключают друг друга. Выберите один|
|Кнопку с многоточием (...)|Элементы, которые могут быть повторены|

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_dump"></a>-дампа

CertUtil [параметры] [-дампа]

CertUtil [параметры] [-дампа] файл

Дамп данных или файлов конфигурации

[-f]. [-silent] [-разделить] [-p пароль] [-t время ожидания]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_asn"></a>-asn

CertUtil [параметры] - asn файл [тип]

Синтаксический анализ файла ASN.1

Тип: числовой тип декодирование CRYPT_STRING_ *

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_decodehex"></a>-decodehex

CertUtil [параметры] - decodehex InFile OutFile [тип]

Тип: числовой тип кодировки CRYPT_STRING_ *

[-f].

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_decode"></a>-декодирования

CertUtil [параметры] - декодирования InFile OutFile

Расшифровать файл в кодировке base 64

[-f].

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_encode"></a>-кодирования

CertUtil [параметры] - кодирования InFile OutFile

Закодировать файл в кодировке Base64

[-f]. [-UnicodeText]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_deny"></a>— запретить

CertUtil [параметры] - запретить RequestId

Отклонение запросов, ожидающих запросов

[-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_resubmit"></a>-повторной отправки

CertUtil [параметры] - повторно отправить RequestId

Отправьте повторно ожидающий запрос

[-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_setattributes"></a>-setattributes

CertUtil [параметры] - setattributes RequestId AttributeString

Задать атрибуты для ожидающего выполнения запроса

RequestId - числовой ИД ожидающего выполнения запроса

AttributeString - Запрашивать пары имен и значений атрибутов
-   Имена и значения разделяются двоеточием.
-   Несколько имя пары "значение", разделяются символом новой строки.
-   Пример: "CertificateTemplate:User\nEMail:User@Domain.com"
-   Каждая последовательность «\n» преобразуется в символ новой строки разделителя.

[-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_setextension"></a>-setextension

CertUtil [параметры] - setextension флаги RequestId ExtensionName {Long | Дата | Строка | @InFile}

Установить расширение для ожидающего запроса

RequestId - числовой ИД ожидающего запроса

ExtensionName--Строка ObjectId расширения

Флаги--рекомендуется 0.  1 делает Критическое расширение, выключает 2, 3 выполняет обе.

Если последний параметр является числовым, оно рассматривается как Long.

Если он может быть проанализировано как дата, оно рассматривается как дату.

Если он начинается с "@", остальная часть маркера — имя файла, содержащего двоичные данные или шестнадцатеричный дамп текста ascii.

Что-нибудь еще рассматривается как строка.

[-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_revoke"></a>-отозвать

CertUtil [параметры] - отозвать SerialNumber [Reason]

Отзыв сертификата

Серийный номер: Разделенный запятыми список серийных номеров сертификатов для отзыва

Причина: причиной отзыва числовому или символическому
-   0: CRL_REASON_UNSPECIFIED: Этот атрибут не задан (по умолчанию)
-   1. CRL_REASON_KEY_COMPROMISE: Компрометация ключа
-   2. CRL_REASON_CA_COMPROMISE: Компрометация ЦС
-   3. CRL_REASON_AFFILIATION_CHANGED: Изменение принадлежности
-   4: CRL_REASON_SUPERSEDED: Заменено
-   5: CRL_REASON_CESSATION_OF_OPERATION: Прекращение действия
-   6: CRL_REASON_CERTIFICATE_HOLD: Приостановка
-   8: CRL_REASON_REMOVE_FROM_CRL: Удалить из списка отзыва Сертификатов
-   -1: Отмена отзыва: Отмена отзыва

[-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_isvalid"></a>-isvalid

CertUtil [параметры] - isvalid SerialNumber | CertHash

Отображение текущего расположения сертификата

[-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_getconfig"></a>-getconfig

CertUtil [параметры] - getconfig

Получение строки конфигурации по умолчанию

[-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_ping"></a>-проверки связи

CertUtil [параметры] - ping [MaxSecondsToWait | CAMachineList]

Интерфейс ping Active Directory Services запрос сертификата

CAMachineList--Список имен машин ЦС с разделителями запятыми
1.  Для одного компьютера используйте запятую завершающий
2.  Для каждого компьютера ЦС стоимость сайта

[-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_CAInfo"></a>-CAInfo

CertUtil [параметры] - CAInfo [ИмяИнфо [индекс | Код ошибки]]

Сведения о ЦС

InfoName - указывает свойство ЦС для отображения (см. ниже). Используйте «*» для всех свойств.

Индекс — необязательное свойство, отсчитываемый от нуля индекс

Код ошибки — числовой код ошибки

[-f]. [-разделить] [-config Machine\CAName]

Синтаксис аргумента ИмяИнфо:
-   Файл: Версия файла
-   продукт: Версия продукта
-   exitcount: Число модулей выхода
-   Exit [Index]: Описание модуля выхода.
-   Политика: Описание модуля политики
-   Имя: Имя ЦС
-   sanitizedname: Исключенное имя ЦС
-   dsname: Исключенное ЦС короткое имя (DS)
-   общая_папка: Общую папку
-   код ошибки error1: Текст сообщения об ошибке
-   код ошибки error2: Текст сообщения об ошибке и кодом ошибки
-   Тип: Тип ЦС
-   информация: Сведения о ЦС
-   Родитель: Родительский ЦС
-   certcount: Счетчик сертификатов ЦС
-   xchgcount: Счетчик сертификатов ЦС exchange
-   kracount: Счетчик сертификатов KRA
-   kraused: Число используемых сертификатов KRA
-   propidmax: PropId максимальное ЦС
-   certstate [Index]: Сертификат ЦС
-   certversion [Index]: Версия сертификата ЦС
-   certstatuscode [Index]: Состояние проверки сертификата ЦС
-   crlstate [Index]: CRL
-   krastate [Index]: Сертификатов KRA
-   crossstate + [Index]: Прямой перекрестный сертификат
-   crossstate-[Index]: Обратный перекрестный сертификат
-   сертификат [Index]: Сертификат ЦС
-   certchain [Index]: Цепочка сертификатов ЦС
-   certcrlchain [Index]: Цепочка сертификатов ЦС с помощью списков отзыва сертификатов
-   xchg [Index]: Сертификат ЦС exchange
-   xchgchain [Index]: Цепочка сертификатов ЦС exchange
-   xchgcrlchain [Index]: Цепочка сертификатов ЦС exchange со списком отзыва сертификатов
-   KRA [Index]: Сертификатов KRA
-   между + [Index]: Прямой перекрестный сертификат
-   кросс-[Index]: Обратный перекрестный сертификат
-   Список отзыва Сертификатов [Index]: Базовый CRL
-   deltacrl [Index]: Разностный список отзыва Сертификатов
-   crlstatus [Index]: Состояние публикации списка отзыва Сертификатов
-   deltacrlstatus [Index]: Состояние публикации разностного списка отзыва Сертификатов
-   DNS-сервер: DNS-имя
-   Роль: Разделение ролей
-   Реклама: Advanced Server
-   шаблоны: Шаблоны
-   OCSP [Index]: URL-адреса OCSP
-   AIA [Index]: URL-адресов AIA
-   cdp [Index]: URL-адреса CDP
-   localename: Имя языкового стандарта ЦС
-   subjecttemplateoids: OID шаблон субъекта

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_ca.cert"></a>-ca.cert

CertUtil [параметры] - ca.cert ВыхФайлСертифЦС [индекс]

Получить сертификат ЦС

ВыхФайлСертифЦС: выходной файл

Индекс: Индекс обновления сертификата ЦС (по умолчанию — самой последней)

[-f]. [-разделить] [-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_ca.chain"></a>-ca.chain

CertUtil [параметры] - ca.chain ВыхФайлЦепСертифЦС [индекс]

Извлечь цепочку сертификатов ЦС

ВыхФайлЦепСертифЦС: выходной файл

Индекс: Индекс обновления сертификата ЦС (по умолчанию — самой последней)

[-f]. [-разделить] [-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_GetCRL"></a>-GetCRL

CertUtil [параметры] - GetCRL OutFile [Index] [разностных]

Получение списка отзыва Сертификатов

Индекс: Список отзыва Сертификатов индекса или ключа индекса (по умолчанию для списка отзыва Сертификатов для самого нового ключа)

дельта: разностный список отзыва Сертификатов (значение по умолчанию — базовый список отзыва Сертификатов)

[-f]. [-разделить] [-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_CRL"></a>-CRL

CertUtil [параметры] - CRL [dd:hh | повторно опубликовать] [разностных]

Опубликовать новый CRL [или только разностный CRL]

dd:hh — новый срок действия списка отзыва Сертификатов в дни и часы

Повторная публикация — повторная публикация последних CRL

дельта - только разностный CRL (по умолчанию — базового и разностного списков отзыва сертификатов)

[-разделить] [-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_shutdown"></a>— Завершение работы

CertUtil [параметры] - завершение работы

Завершение служб сертификатов Active Directory

[-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_installcert"></a>-installCert

CertUtil [параметры] - installCert [CACertFile]

Установка сертификата центра сертификации

[-f]. [-silent] [-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_renewcert"></a>-renewCert

CertUtil [параметры] - renewCert [ReuseKeys] [Machine\ParentCAName]

Обновление сертификата центра сертификации

Используйте -f, чтобы игнорировать отложенного запроса обновления и создания нового запроса.

[-f]. [-silent] [-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_schema"></a>-схемы

CertUtil [параметры] - схемы [Ext | Attrib | СПИСОК ОТЗЫВА СЕРТИФИКАТОВ]

Дамп схемы сертификатов

Значения по умолчанию для запроса и сертификат таблицы

Ext: Таблицу расширения

Атрибуты: Таблица атрибутов

СПИСОК ОТЗЫВА СЕРТИФИКАТОВ: Таблица списка отзыва Сертификатов

[-разделить] [-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_view"></a>-представление

CertUtil [параметры] - представление [очередь | Журнал | LogFail | Отменить | Ext | Attrib | Список отзыва Сертификатов] [csv]

Дамп просмотра сертификата

Очередь. Очередь запросов

Журнал: Выданный или отозванные сертификаты, а также неудачные запросы

LogFail: Неудачных запросов

Отменить: Отозванные сертификаты

Ext: Таблицу расширения

Атрибуты: Таблица атрибутов

СПИСОК ОТЗЫВА СЕРТИФИКАТОВ: Таблица списка отзыва Сертификатов

CSV-файл: Выходные, так как значения, разделенные запятыми

Для отображения столбца код состояния для всех записей:-out StatusCode

Для отображения всех столбцов для последней операции:-ограничение «RequestId == $»

Для отображения ИД запроса и метода обработки для трех запросов:-ограничение «RequestId > = 37, RequestId\<40»-out «RequestId, расположения»

Для отображения идентификаторы строк и чисел списка отзыва Сертификатов для всех базовый CRL:-ограничить «CRLMinBase = 0»-out «CRLRowId CRLNumber» списка отзыва Сертификатов

Для отображения базового CRL номер 3: - v-ограничение «CRLMinBase = 0, CRLNumber = 3»-out «CRLRawCRL» списка отзыва Сертификатов

Для отображения всей таблицы списка отзыва Сертификатов: CRL

Используйте «Дата [+ |-dd:hh]» для ограничения даты

Используйте «now + dd:hh» для даты, относительно текущего времени

[-silent] [-разделить] [-config Machine\CAName] [-ограничить RestrictionList] [-out ColumnList]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_db"></a>-db

CertUtil [параметры] - db

Необработанный дамп базы данных

[-config Machine\CAName] [-ограничить RestrictionList] [-out ColumnList]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_deleterow"></a>-deleterow

CertUtil [параметры] - deleterow RowId | Даты [запрос | CERT | Ext | Attrib | СПИСОК ОТЗЫВА СЕРТИФИКАТОВ]

Удалить строку базы данных сервера

Запрос: Не удалось и ожидающих запросов (Дата отправки)

Cert: Просроченные и отозванных сертификатов (Дата окончания срока действия)

Ext: Таблицу расширения

Атрибуты: Таблица атрибутов

СПИСОК ОТЗЫВА СЕРТИФИКАТОВ: Таблица списка отзыва Сертификатов (Дата окончания срока действия)

Чтобы удалить невыполненные запросы, отправленные от 22 января 2001 г. и: 1/22/2001 запроса

Чтобы удалить все сертификаты, срок действия истек 22 января 2001 года: 1/22/2001 cert

Удаление сертификата строк, атрибуты и расширения для 37 ИД запроса: 37

Чтобы удалить списки отзыва сертификатов, срок действия истек 22 января 2001 года: 1/22/2001 СПИСКА ОТЗЫВА СЕРТИФИКАТОВ

[-f]. [-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_backup"></a>-резервного копирования

CertUtil [параметры] - создать резервную копию BackupDirectory [добавочные] [KeepLog]

Службы сертификатов резервного копирования Active Directory

BackupDirectory: каталог для хранения резервных копий данных

INCREMENTAL: выполнять добавочное резервное копирование (значение по умолчанию — полное резервное копирование)

KeepLog: сохранить файлы журнала базы данных (по умолчанию — выполнить усечение файлов журнала)

[-f]. [-config Machine\CAName] [-p пароль]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_backupDB"></a>-backupDB

CertUtil [параметры] - backupDB BackupDirectory [добавочные] [KeepLog]

Резервное копирование базы данных служб сертификатов Active Directory

BackupDirectory: каталог для хранения резервных копий фалов базы данных

INCREMENTAL: выполнять добавочное резервное копирование (значение по умолчанию — полное резервное копирование)

KeepLog: сохранить файлы журнала базы данных (по умолчанию — выполнить усечение файлов журнала)

[-f]. [-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_backupKey"></a>-backupKey

BackupDirectory - backupKey CertUtil [параметры]

Резервного копирования службы сертификатов Active Directory сертификат и закрытый ключ

BackupDirectory: каталог для хранения резервное копирование PFX-файла

[-f]. [-config Machine\CAName] [-p пароль] [-t время ожидания]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_restore"></a>-Восстановление

CertUtil [параметры] - восстановление BackupDirectory

Восстановление служб сертификатов Active Directory

BackupDirectory: каталог, содержащий данные для восстановления

[-f]. [-config Machine\CAName] [-p пароль]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_restoreDB"></a>-restoreDB

BackupDirectory - restoreDB CertUtil [параметры]

Восстановление базы данных служб сертификатов Active Directory

BackupDirectory: каталог, содержащий восстановить файлы базы данных

[-f]. [-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_restorekey"></a>-restoreKey

CertUtil [параметры] - restoreKey BackupDirectory | PFXFile

Восстановление служб сертификатов Active Directory сертификат и закрытый ключ

BackupDirectory: каталог, содержащий PFX-файл для восстановления

PFXFile: PFX-файл для восстановления

[-f]. [-config Machine\CAName] [-p пароль]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_importPFX"></a>-importPFX

CertUtil [параметры] - importPFX [Имяхранилищасертификатов] PFXFile [модификаторы]

Импорт сертификата и закрытого ключа

Имяхранилищасертификатов: Имя хранилища сертификатов.  См. в разделе [-хранить](#BKMK_Store).

PFXFile: PFX-файл для импорта

Модификаторы: Разделенный запятыми список из одного или нескольких из следующих:
1.  AT_SIGNATURE, КОТОРОЕ: Изменение KeySpec подписи
2.  AT_KEYEXCHANGE: Изменение KeySpec для обмена ключами
3.  NoExport: Сделать закрытый ключ недоступен для экспорта
4.  NoCert: Не импортировать сертификат
5.  NoChain: Не импортируйте цепочку сертификатов
6.  NoRoot: Не импортируйте корневой сертификат
7.  Защита: Защита ключей с помощью пароля
8.  NoProtect: Не паролем защиты ключей

По умолчанию в личном хранилище.

[-f]. [-пользователь] [-p пароль] [-csp поставщик]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_dynamicfilelist"></a>-dynamicfilelist

CertUtil [параметры] - dynamicfilelist

Отображение динамического списка файлов

[-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_databaselocations"></a>-databaselocations

CertUtil [параметры] - databaselocations

Отображения расположения базы данных

[-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_hashfile"></a>-hashfile

InFile - hashfile CertUtil [параметры] [HashAlgorithm]

Создать и отобразить криптографический хэш над файлом

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_Store"></a>-хранения

CertUtil [параметры] - хранения [Имяхранилищасертификатов [CertId [ВыходнойФайл]]]

Хранилище сертификатов дампа

Имяхранилищасертификатов: Имя хранилища сертификатов. Примеры
-   «My», «CA» (по умолчанию), «Root»,
-   «ldap: / / / CN центров сертификации, CN = = Public Key Services, CN = Services, CN = Configuration, DC = cpandl, DC = com? сертификат ЦС? один? objectClass = certificationAuthority» (представление корневые сертификаты)
-   «ldap: / / / CN Имя_цс, CN = центров сертификации, CN = = Public Key Services, CN = Services, CN = Configuration, DC = cpandl, DC = com? сертификат ЦС? базовый? objectClass = certificationAuthority» (изменение корневых сертификатов)
-   «ldap: / / / CN Имя_цс, CN = MachineName, CN = CDP, CN = = Public Key Services, CN = Services, CN = Configuration, DC = cpandl, DC = com? certificateRevocationList? базовый? objectClass = cRLDistributionPoint» (представления списков отзыва сертификатов)
-   «ldap: / / / CN = NTAuthCertificates, CN = Public Key Services, CN = Services, CN = Configuration, DC = cpandl, DC = com? сертификат ЦС? базовый? objectClass = certificationAuthority» (сертификаты ЦС предприятия)
-   LDAP: (Сертификаты объекта компьютера AD)
-   — пользователь ldap: (Сертификаты объект пользователя AD)

CertId: Сертификат или маркер совпадение списка отзыва Сертификатов.  Это может быть серийный номер, SHA-1 сертификата, списка отзыва Сертификатов, CTL или хэш открытого ключа, индекс cert числовые (0, 1 и т. д.), числовой индекс списка отзыва Сертификатов (. 0,.1 и т. д.), числовой индекс списка доверия Сертификатов (.. 0... 1 и т. д.), открытый ключ подписи или расширение ObjectId, общее имя, адрес электронной почты субъекта сертификата имя участника-пользователя или DNS-имя, имя контейнера ключей или имя поставщика служб Шифрования, имя шаблона или ObjectId, EKU или ObjectId политики приложения и имени поставщика CRL общее имя. Многие из них может привести к несколько совпадений.

OutputFile: файл, чтобы сохранить сопоставления сертификата

Используйте параметр - пользователю доступ к хранилище пользователя, а не хранилище компьютера.

Используйте параметр - enterprise, чтобы получить доступ к enterprise хранилище на компьютере.

Используйте параметр - службы для доступа к службе хранилище на компьютере.

Получить доступ к хранилище групповой политики на компьютере - grouppolicy.

Примеры
-   -enterprise NTAuth
-   -Корпоративный корневой 37
-   — пользователь моей 26e0aaaf000000000004
-   ЦС.11

[-f]. [-enterprise] [-пользователь] [-GroupPolicy] [-silent] [-разделить] [-dc DCName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_addstore"></a>-addstore

CertUtil [параметры] - addstore Имяхранилищасертификатов InFile

Добавление сертификата в хранилище

Имяхранилищасертификатов: Имя хранилища сертификатов.  См. в разделе [-хранить](#BKMK_Store).

InFile: Файл сертификата или списка отзыва Сертификатов для добавления для хранения.

[-f]. [-enterprise] [-пользователь] [-GroupPolicy] [-dc DCName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_delstore"></a>-delstore

CertUtil [параметры] - delstore Имяхранилищасертификатов CertId

Удалить сертификат из хранилища

Имяхранилищасертификатов: Имя хранилища сертификатов.  См. в разделе [-хранить](#BKMK_Store).

CertId: Сертификат или маркер совпадение списка отзыва Сертификатов.  См. в разделе [-хранить](#BKMK_Store).

[-enterprise] [-пользователь] [-GroupPolicy] [-dc DCName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_verifystore"></a>-verifystore

Имяхранилищасертификатов - verifystore CertUtil [параметры] [CertId]

Проверка сертификата в хранилище

Имяхранилищасертификатов: Имя хранилища сертификатов.  См. в разделе [-хранить](#BKMK_Store).

CertId: Сертификат или маркер совпадение списка отзыва Сертификатов.  См. в разделе [-хранить](#BKMK_Store).

[-enterprise] [-пользователь] [-GroupPolicy] [-silent] [-разделить] [-dc DCName] [-t время ожидания]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_repairstore"></a>-repairstore

CertUtil [параметры] - repairstore Имяхранилищасертификатов CertIdList [PropertyInfFile | SDDLSecurityDescriptor]

Восстановление сопоставления ключа или обновить дескриптор безопасности свойства или ключа сертификата

Имяхранилищасертификатов: Имя хранилища сертификатов.  См. в разделе [-хранить](#BKMK_Store).

CertIdList: разделенный запятыми список сертификатов или CRL маркеры совпадения. См. в разделе [-хранить](#BKMK_Store) CertId описание.

PropertyInfFile--INF файл, содержащий свойства внешнего:
```
[Properties]
     19 = Empty ; Add archived property, OR:
     19 =       ; Remove archived property

     11 = "{text}Friendly Name" ; Add friendly name property

     127 = "{hex}" ; Add custom hexadecimal property
         _continue_ = "00 01 02 03 04 05 06 07 08 09 0a 0b 0c 0d 0e 0f"
         _continue_ = "10 11 12 13 14 15 16 17 18 19 1a 1b 1c 1d 1e 1f"

     2 = "{text}" ; Add Key Provider Information property
       _continue_ = "Container=Container Name&"
       _continue_ = "Provider=Microsoft Strong Cryptographic Provider&"
       _continue_ = "ProviderType=1&"
       _continue_ = "Flags=0&"
       _continue_ = "KeySpec=2"

     9 = "{text}" ; Add Enhanced Key Usage property
       _continue_ = "1.3.6.1.5.5.7.3.2,"
       _continue_ = "1.3.6.1.5.5.7.3.1,"
```
[-f]. [-enterprise] [-пользователь] [-GroupPolicy] [-silent] [-разделить] [-csp поставщик]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_viewstore"></a>-viewstore

CertUtil [параметры] - viewstore [Имяхранилищасертификатов [CertId [ВыходнойФайл]]]

Хранилище сертификатов дампа

Имяхранилищасертификатов: Имя хранилища сертификатов.  Примеры
-   «My», «CA» (по умолчанию), «Root»,
-   «ldap: / / / CN центров сертификации, CN = = Public Key Services, CN = Services, CN = Configuration, DC = cpandl, DC = com? сертификат ЦС? один? objectClass = certificationAuthority» (представление корневые сертификаты)
-   «ldap: / / / CN Имя_цс, CN = центров сертификации, CN = = Public Key Services, CN = Services, CN = Configuration, DC = cpandl, DC = com? сертификат ЦС? базовый? objectClass = certificationAuthority» (изменение корневых сертификатов)
-   «ldap: / / / CN Имя_цс, CN = MachineName, CN = CDP, CN = = Public Key Services, CN = Services, CN = Configuration, DC = cpandl, DC = com? certificateRevocationList? базовый? objectClass = cRLDistributionPoint» (представления списков отзыва сертификатов)
-   «ldap: / / / CN = NTAuthCertificates, CN = Public Key Services, CN = Services, CN = Configuration, DC = cpandl, DC = com? сертификат ЦС? базовый? objectClass = certificationAuthority» (сертификаты ЦС предприятия)
-   LDAP: (Сертификаты объекта компьютера AD)
-   — пользователь ldap: (Сертификаты объект пользователя AD)

CertId: Сертификат или маркер совпадение списка отзыва Сертификатов. Это может быть серийный номер, SHA-1 сертификата, списка отзыва Сертификатов, CTL или хэш открытого ключа, индекс cert числовые (0, 1 и т. д.), числовой индекс списка отзыва Сертификатов (. 0,.1 и т. д.), числовой индекс списка доверия Сертификатов (.. 0... 1 и т. д.), открытый ключ подписи или расширение ObjectId, общее имя, адрес электронной почты субъекта сертификата имя участника-пользователя или DNS-имя, имя контейнера ключей или имя поставщика служб Шифрования, имя шаблона или ObjectId, EKU или ObjectId политики приложения и имени поставщика CRL общее имя. Многие из них может привести к несколько совпадений.

OutputFile: файл, чтобы сохранить сопоставления сертификата

Используйте параметр - пользователю доступ к хранилище пользователя, а не хранилище компьютера.

Используйте параметр - enterprise, чтобы получить доступ к enterprise хранилище на компьютере.

Используйте параметр - службы для доступа к службе хранилище на компьютере.

Получить доступ к хранилище групповой политики на компьютере - grouppolicy.

Примеры
1.  -enterprise NTAuth
2.  -Корпоративный корневой 37
3.  — пользователь моей 26e0aaaf000000000004
4.  ЦС.11

[-f]. [-enterprise] [-пользователь] [-GroupPolicy] [-dc DCName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_viewdelstore"></a>-viewdelstore

CertUtil [параметры] - viewdelstore [Имяхранилищасертификатов [CertId [ВыходнойФайл]]]

Удалить сертификат из хранилища

Имяхранилищасертификатов: Имя хранилища сертификатов.  Примеры
-   «My», «CA» (по умолчанию), «Root»,
-   «ldap: / / / CN центров сертификации, CN = = Public Key Services, CN = Services, CN = Configuration, DC = cpandl, DC = com? сертификат ЦС? один? objectClass = certificationAuthority» (представление корневые сертификаты)
-   «ldap: / / / CN Имя_цс, CN = центров сертификации, CN = = Public Key Services, CN = Services, CN = Configuration, DC = cpandl, DC = com? сертификат ЦС? базовый? objectClass = certificationAuthority» (изменение корневых сертификатов)
-   «ldap: / / / CN Имя_цс, CN = MachineName, CN = CDP, CN = = Public Key Services, CN = Services, CN = Configuration, DC = cpandl, DC = com? certificateRevocationList? базовый? objectClass = cRLDistributionPoint» (представления списков отзыва сертификатов)
-   «ldap: / / / CN = NTAuthCertificates, CN = Public Key Services, CN = Services, CN = Configuration, DC = cpandl, DC = com? сертификат ЦС? базовый? objectClass = certificationAuthority» (сертификаты ЦС предприятия)
-   LDAP: (Сертификаты объекта компьютера AD)
-   — пользователь ldap: (Сертификаты объект пользователя AD)

CertId: Сертификат или маркер совпадение списка отзыва Сертификатов. Это может быть серийный номер, SHA-1 сертификата, списка отзыва Сертификатов, CTL или хэш открытого ключа, индекс cert числовые (0, 1 и т. д.), числовой индекс списка отзыва Сертификатов (. 0,.1 и т. д.), числовой индекс списка доверия Сертификатов (.. 0... 1 и т. д.), открытый ключ подписи или расширение ObjectId, общее имя, адрес электронной почты субъекта сертификата имя участника-пользователя или DNS-имя, имя контейнера ключей или имя поставщика служб Шифрования, имя шаблона или ObjectId, EKU или ObjectId политики приложения и имени поставщика CRL общее имя. Многие из них может привести к несколько совпадений.

OutputFile: файл, чтобы сохранить сопоставления сертификата

Используйте параметр - пользователю доступ к хранилище пользователя, а не хранилище компьютера.

Используйте параметр - enterprise, чтобы получить доступ к enterprise хранилище на компьютере.

Используйте параметр - службы для доступа к службе хранилище на компьютере.

Получить доступ к хранилище групповой политики на компьютере - grouppolicy.

Примеры
1.  -enterprise NTAuth
2.  -Корпоративный корневой 37
3.  — пользователь моей 26e0aaaf000000000004
4.  ЦС.11

[-f]. [-enterprise] [-пользователь] [-GroupPolicy] [-dc DCName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_dsPublish"></a>-dsPublish

CertUtil [параметры] - dsPublish CertFile [NTAuthCA | RootCA | Вы можете | Перекрестный ЦС | KRA | Пользователя | Машины]

CRLFile - dsPublish CertUtil [параметры] [DSCDPContainer [DSCDPCN]]

Публикацию сертификатов или списка отзыва Сертификатов в Active Directory

CertFile: файл сертификата для публикации

NTAuthCA: Опубликовать сертификат в хранилище доменных служб Active Directory предприятия

RootCA: Публикация в доменных служб Active Directory доверенное корневое хранилище сертификатов

SubCA: Опубликовать сертификат ЦС для объекта доменных служб Active Directory ЦС

CrossCA: Публикация кросс-cert объекту доменных служб Active Directory ЦС

KRA: Публикация сертификата агента восстановления ключей доменных служб Active Directory объект

Пользователь: Опубликовать сертификат к объекту пользователя доменных служб Active Directory

Компьютер: Публикация cert объекту машины доменных служб Active Directory

CRLFile: Файл списка отзыва Сертификатов для публикации

DSCDPContainer: Контейнер ТРС DS CN, обычно имя компьютера ЦС

DSCDPCN: DS CDP объекта CN, обычно на основе исключенного короткого имени ЦС и индекс ключа

Используйте -f для создания объекта доменных служб Active Directory.

[-f]. [-пользователь] [-dc DCName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_ADTemplate"></a>-ADTemplate

CertUtil [параметры] - ADTemplate [шаблона]

Шаблоны отображения AD

[-f]. [-пользователь] [-ut] [-mt] [-dc DCName]

## <a name="BKMK_template"></a>-Шаблона

CertUtil [параметры] - шаблон [шаблон]

Отображать шаблоны политики регистрации

[-f]. [-пользователь] [-silent] [-PolicyServer URLOrId] [-Анонимный] [-Kerberos] [-ClientCertId на ClientCertificate] [-Имя пользователя имя пользователя] [-p пароль]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_TemplateCAs"></a>-TemplateCAs

CertUtil [параметры] - TemplateCAs шаблона

Отображение ЦС для шаблона

[-f]. [-пользователь] [-dc DCName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_CATemplates"></a>-CATemplates

CertUtil [параметры] - CATemplates [шаблона]

Отображение шаблонов для ЦС

[-f]. [-пользователь] [-ut] [-mt] [-config Machine\CAName] [-dc DCName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_SetCASites"></a>-SetCASites

CertUtil [параметры] - SetCASites [набора] [имя_узла]

CertUtil [параметры] - SetCASites проверить [имя_узла]

Delete - SetCASites CertUtil [параметры]

Имена сайтов набора, проверить или удалить ЦС
-   Используйте параметр - config целевых один центр сертификации (значение по умолчанию — все ЦС)
-   *SiteName* допускается только при ориентации один центр сертификации
-   Используйте -f, чтобы переопределить ошибок проверки для указанного *SiteName*
-   Используйте -f, чтобы удалить все имена сайтов ЦС

[-f]. [-config Machine\CAName] [-dc DCName]

> [!NOTE]
> Дополнительные сведения о настройке центров сертификации для доменных служб Active Directory (AD DS) о сайтах, см. в разделе [AD DS о сайтах для клиентов AD CS и PKI](https://social.technet.microsoft.com/wiki/contents/articles/14106.ad-ds-site-awareness-for-ad-cs-and-pki-clients.aspx).

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_enrollmentServerURL"></a>-enrollmentServerURL

CertUtil [параметры] - enrollmentServerURL [AuthenticationType URL-адрес [приоритет] [модификаторы]]

Удаление URL-адрес - enrollmentServerURL CertUtil [параметры]

Отображения, добавить или удалить URL-адреса сервера регистрации, связанные с ЦС

AuthenticationType: Укажите один из следующих методов проверки подлинности клиента при добавлении URL-адрес
1.  Kerberos: Использовать учетные данные Kerberos SSL
2.  Имя пользователя: Использование с именем учетной записи для учетных данных SSL
3.  ClientCertificate: Использовать учетные данные сертификата X.509 SSL
4.  Anonymous: Использование анонимных учетных данных SSL

удалить: Удаляет указанный URL-адрес, связанный с центром сертификации

Приоритет: значение по умолчанию — "1", если не указано, при добавлении URL-адрес

Модификаторы — Разделенный запятыми список из одного или нескольких из следующих:
1.  AllowRenewalsOnly: Только запросы обновления могут передаваться в ЦС через этот URL-адрес
2.  AllowKeyBasedRenewal: Позволяет использовать сертификат, который имеет нет связанной учетной записи в AD. Это относится только с ClientCertificate и режимом AllowRenewalsOnly

[-config Machine\CAName] [-dc DCName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_ADCA"></a>-ADCA

CertUtil [параметры] - ADCA [CAName]

Отобразить центров сертификации AD

[-f]. [-разделить] [-dc DCName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_CA"></a>-CA

CertUtil [параметры] -CA [Имя_цс | TemplateName]

Отображение ЦС политики регистрации

[-f]. [-пользователь] [-silent] [-разделить] [-PolicyServer URLOrId] [-Анонимный] [-Kerberos] [-ClientCertId на ClientCertificate] [-Имя пользователя имя пользователя] [-p пароль]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_Policy"></a>-Policy

Отображение политики регистрации

[-f]. [-пользователь] [-silent] [-разделить] [-PolicyServer URLOrId] [-Анонимный] [-Kerberos] [-ClientCertId на ClientCertificate] [-Имя пользователя имя пользователя] [-p пароль]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_PolicyCache"></a>-PolicyCache

CertUtil [параметры] - PolicyCache [delete]

Отображение или удаление записей кэша политики регистрации

удаление: удаление записей кэша сервера политики

-f: используйте -f, чтобы удалить все записи кэша

[-f]. [-пользователь] [-PolicyServer URLOrId]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_Credstore"></a>-CredStore

CertUtil [параметры] - CredStore [URL]

CertUtil [параметры] - CredStore добавьте URL-адрес

CertUtil [параметры] - CredStore удалить URL-адрес

Отображения, добавить или удалить записи учетных данных Store

URL-адрес: целевой URL-адрес.  Используйте * для сопоставления всех записей. Используйте https://machine* в соответствии с префикс URL-адреса.

Добавление: добавить запись учетных данных Store. Также необходимо указать учетные данные SSL.

удаление: удаление записей Store учетных данных

-f: используйте -f для перезаписи запись или удалить несколько записей.

[-f]. [-пользователь] [-silent] [-Анонимный] [-Kerberos] [-ClientCertId на ClientCertificate] [-Имя пользователя имя пользователя] [-p пароль]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_InstallDefaultTemplates"></a>-InstallDefaultTemplates

CertUtil [параметры] - InstallDefaultTemplates

Установите шаблоны сертификатов по умолчанию

[-dc DCName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_URLCache"></a>-URLCache

CertUtil [параметры] - URLCache [URL-адрес | СПИСОК ОТЗЫВА СЕРТИФИКАТОВ | * [удалить]]

Отображение или удаление записей кэша URL-адрес

URL-адрес: кэшированный URL-адрес

Список отзыва Сертификатов: оперируют все кэшированного списка отзыва Сертификатов URL-адреса только

*: оперируют все кэшированные URL-адреса

удалить: удалить соответствующие URL-адреса из локального кэша для текущего пользователя

Используйте -f для принудительного получения определенного URL-адреса и обновления кэша.

[-f]. [-разделить]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_pulse"></a>-pulse

CertUtil [параметры] - pulse

Pulse автоматической регистрации событий

[-пользователь]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_MachineInfo"></a>-MachineInfo

CertUtil [параметры] - MachineInfo DomainName\MachineName$

Отобразить сведения о объекта компьютера Active Directory

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_DCInfo"></a>-DCInfo

CertUtil [параметры] - DCInfo [домен] [Проверьте | DeleteBad | DeleteAll]

Отобразить сведения о контроллере домена

Значение по умолчанию — для отображения сертификатов контроллера домена без проверки

[-f]. [-пользователь] [-urlfetch] [-dc DCName] [-t время ожидания]

> [!TIP]
> Возможность указать домен доменных служб Active Directory (AD DS) **[домен]** и указать контроллер домена (**-dc**) был добавлен в Windows Server 2012. Для успешного выполнения команды, необходимо использовать учетную запись, которая является членом **"Администраторы домена"** или **"Администраторы предприятия"**. Ниже приведены изменения поведения этой команды.</br>> 1.  Если домен не указан и определенным контроллером домена не указан, этот параметр Возвращает список контроллеров домена для обработки из контроллера домена по умолчанию.</br>> 2.  Если домен не указан, но контроллер домена указан, создается отчет сертификатов на указанный контроллер домена.</br>> 3.  Если домен указан, но контроллер домена не указан, список контроллеров домена создается вместе с отчетами на сертификаты для каждого контроллера домена в списке.</br>> 4.  Если указаны домена и контроллером домена, список контроллеров домена создается с контроллера домена. Также создается отчет для каждого контроллера домена в списке сертификатов.

Например предположим, имеется домен с именем CPANDL с контроллером домена с именем CPANDL DC1. Вы может выполните следующую команду для извлечения списка контроллеров домена и их сертификатах, от CPANDL DC1: certutil - контроллер домена cpandl dc1 - dcinfo cpandl

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_EntInfo"></a>-EntInfo

CertUtil [параметры] - EntInfo DomainName\MachineName$

[-f]. [-пользователь]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_TCAInfo"></a>-TCAInfo

CertUtil [параметры] - TCAInfo [DomainDN |-]

Сведения о ЦС

[-f]. [-enterprise] [-пользователь] [-urlfetch] [-dc DCName] [-t время ожидания]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_SCInfo"></a>-SCInfo

CertUtil [параметры] - SCInfo [ReaderName [CRYPT_DELETEKEYSET]]

Отображать сведения о смарт-карты

CRYPT_DELETEKEYSET: Удалить все ключи в смарт-карты

[-silent] [-разделить] [-urlfetch] [-t время ожидания]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_SCRoots"></a>-SCRoots

CertUtil [параметры] - SCRoots обновления [+] [InputRootFile] [ReaderName]

CertUtil [параметры] - SCRoots Сохранить @OutputRootFile [ReaderName]

Представление - SCRoots CertUtil [параметры] [InputRootFile | ReaderName]

CertUtil [параметры] - SCRoots удалить [ReaderName]

Управление корневые сертификаты смарт-карты

[-f]. [-разделить] [-p пароль]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_verifykeys"></a>-verifykeys

CertUtil [параметры] - verifykeys [КонтейнерКлючей ФайлСертификатаЦС]

Проверка открытого и закрытого ключа набора

КонтейнерКлючей: имя контейнера ключей ключа для проверки. По умолчанию ключи компьютера.  Используйте параметр - пользователя для ключей пользователя.

CACertFile: файл сертификата подписи или шифрования

Если аргументы не указаны, каждый сертификат подписи ЦС сверяется с его закрытым ключом.

Эта операция может выполняться только для локального ЦС или локальных ключей.

[-f]. [-пользователь] [-silent] [-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_verify"></a>— Проверка

CertUtil [параметры] - CertFile проверить [ApplicationPolicyList |-[IssuancePolicyList]]

CertUtil [параметры] - Проверьте CertFile [CACertFile [CrossedCACertFile]]

CertUtil [параметры] - Проверьте CRLFile CACertFile [IssuedCertFile]

CertUtil [параметры] - Проверьте CRLFile CACertFile [DeltaCRLFile]

Проверка CRL, сертификата или цепочки

CertFile: Сертификат для проверки

ApplicationPolicyList: Необязательный разделенный запятыми список требуется идентификаторы objectid для политики приложения

IssuancePolicyList: Необязательный разделенный запятыми список требуется идентификаторы objectid для политики выдачи

CACertFile: необязательный сертификат ЦС для проверки

CrossedCACertFile: необязательный сертификат перекрестно сертифицированным по CertFile

CRLFile: Список отзыва Сертификатов для проверки

IssuedCertFile: выданный сертификат с необязательным охваченных CRLFile

DeltaCRLFile: необязательно разностный список отзыва Сертификатов

Если указан ApplicationPolicyList, построение цепочки ограничено цепочками, допустимыми для указанных политик приложения.

Если указан IssuancePolicyList, построение цепочки ограничено цепочками, допустимыми для указанных политик выдачи.

Если указан CACertFile полей в CACertFile сверяются с CertFile или CRLFile.

Если CACertFile не указан, CertFile используется для создания и проверки всей цепочки.

Если CACertFile и CrossedCACertFile указан, поля в CACertFile и CrossedCACertFile сверяются с CertFile.

Если указан IssuedCertFile полей в IssuedCertFile сверяются с CRLFile.

Если указан DeltaCRLFile полей в DeltaCRLFile сверяются с CRLFile.

[-f]. [-enterprise] [-пользователь] [-silent] [-разделить] [-urlfetch] [-t время ожидания]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_verifyCTL"></a>-verifyCTL

CTLObject - verifyCTL CertUtil [параметры] [CertDir] [CertFile]

Проверка AuthRoot или запрещенных сертификатов списка доверия Сертификатов

CTLObject: Определяет список доверия Сертификатов для проверки:
-   AuthRootWU: чтение AuthRoot CAB и соответствующие сертификаты из кэша URL-адрес. Для загрузки из центра обновления Windows вместо этого, используйте -f.
-   DisallowedWU: чтение запрещено CAB-файлов сертификатов и запрещенных хранилища файл сертификата из кэша URL-адрес.  Для загрузки из центра обновления Windows вместо этого, используйте -f.
-   AuthRoot: чтения реестра кэшированные AuthRoot списка доверия Сертификатов.  Использовать с -f и CertFile, который не уже является доверенным для принудительного обновления реестра кэшированных AuthRoot и запрещенные списков доверия сертификатов сертификат.
-   Запрещено: чтения реестра кэшированные CTL сертификатов запрещено. -f действует так же, как и в случае с AuthRoot.
-   CTLFileName: файл "или" http: путь к CTL или CAB-файла

CertDir: папка, содержащая сертификаты совпадающих записей списка доверия Сертификатов. Http: путь к папке должен заканчиваться разделителем пути. Если не указана папка с AuthRoot или не разрешено, нескольких местах будет производиться поиск сопоставления сертификатов: локальный сертификат хранит crypt32.dll ресурсы и локальный кэш URL-адрес. Для загрузки из центра обновления Windows при необходимости используйте -f. В противном случае по умолчанию же папку или веб-сайта как CTLObject.

CertFile: файл, содержащий сертификаты для проверки. Сертификаты будет сопоставлена с записи списка доверия Сертификатов и соответствует результаты отображаются. Подавляет большая часть выходных данных по умолчанию.

[-f]. [-пользователь] [-разделить]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_sign"></a>-входа

CertUtil [параметры] - входить InFileList | SerialNumber | Список отзыва Сертификатов OutFileList [StartDate + dd:hh] [+ SerialNumberList | - SerialNumberList | - указывает | @ExtensionFile]

CertUtil [параметры] - входить InFileList | SerialNumber | Список отзыва Сертификатов OutFileList [#HashAlgorithm] [+ AlternateSignatureAlgorithm | - AlternateSignatureAlgorithm]

Повторной подписи сертификата или списка отзыва Сертификатов

InFileList: разделенный запятыми список сертификатов или CRL файлы для изменения и повторно подписать

Серийный номер: Серийный номер сертификата для создания. Срок действия и другие параметры должны отсутствовать.

СПИСОК ОТЗЫВА СЕРТИФИКАТОВ: Создайте пустой список отзыва Сертификатов. Срок действия и другие параметры должны отсутствовать.

OutFileList: разделенный запятыми список измененных файлов выходных данных сертификатов или CRL. Число файлов, должно соответствовать InFileList.

StartDate + dd:hh: новый период: необязательно дата плюс; необязательное количество дней и часов срок действия; Если указаны оба, используйте разделитель плюс (+). Используйте «now [+ dd:hh]» для запуска в настоящее время. Используйте «никогда», чтобы без даты окончания срока действия (для списков отзыва сертификатов только).

SerialNumberList: разделенный запятыми список серийный номер для добавления или удаления

Указывает: расширение ObjectId через запятую для удаления

@ExtensionFile: INF-файл, содержащий расширения, чтобы обновить или удалить:
```
[Extensions]
     2.5.29.31 = ; Remove CRL Distribution Points extension
     2.5.29.15 = "{hex}" ; Update Key Usage extension
     _continue_="03 02 01 86"
```
HashAlgorithm: Имя хэш-алгоритма, предшествует знак #

AlternateSignatureAlgorithm: альтернативный описатель алгоритм подписи

Знак «минус» вызывает серийные номера и расширения для удаления. Значок «плюс» вызывает серийных номеров для добавления списка отзыва Сертификатов. При удалении элементов из списка отзыва Сертификатов, список может содержать серийные номера и идентификаторы objectid. Знак минус перед AlternateSignatureAlgorithm вызывает формат подписи прежних версий для использования. Знак плюс, прежде чем AlternateSignatureAlgorithm вызвано alternature формата подписи для использования. Если AlternateSignatureAlgorithm не указан, используется формат подписи в сертификат или списка отзыва Сертификатов.

[-nullsign] [-f]. [-silent] [-Cert CertId]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_vroot"></a>-vroot

CertUtil [параметры] - vroot [delete]

Создание и удаление виртуальных корней Веба и общим папкам

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_vocsproot"></a>-vocsproot

CertUtil [параметры] - vocsproot [delete]

Создание и удаление виртуальных корней Веба для веб-прокси OCSP

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_addEnrollmentServer"></a>-addEnrollmentServer

CertUtil [параметры] - addEnrollmentServer Kerberos | Имя пользователя | ClientCertificate [AllowRenewalsOnly] [AllowKeyBasedRenewal]

Добавление сервера регистрации приложения

Добавление сервера регистрации приложения и пул приложений, при необходимости, для указанного ЦС. Эта команда не производится установка двоичных файлов или пакетов. Одно из следующих методов проверки подлинности, с которыми клиент подключается к серверу регистрации сертификата.
-   Kerberos: Использовать учетные данные Kerberos SSL
-   Имя пользователя: Использование с именем учетной записи для учетных данных SSL
-   ClientCertificate: Использовать учетные данные сертификата X.509 SSL
-   AllowRenewalsOnly: Только запросы обновления могут передаваться в ЦС через этот URL-адрес
-   AllowKeyBasedRenewal — Позволяет использовать сертификат, который имеет нет связанной учетной записи в AD. Это относится только с режимом на ClientCertificate и AllowRenewalsOnly.

[-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_deleteEnrollmentServer"></a>-deleteEnrollmentServer

CertUtil [параметры] - deleteEnrollmentServer Kerberos | Имя пользователя | ClientCertificate

Удалить приложение сервера регистрации

Удаление сервера регистрации приложения и пул приложений, при необходимости, для указанного ЦС. Эта команда не удаляет двоичные файлы и пакеты. Одно из следующих методов проверки подлинности, с которыми клиент подключается к серверу регистрации сертификата.
1.  Kerberos: Использовать учетные данные Kerberos SSL
2.  Имя пользователя: Использование с именем учетной записи для учетных данных SSL
3.  ClientCertificate: Использовать учетные данные сертификата X.509 SSL

[-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_addPolicyServer"></a>-addPolicyServer

CertUtil [параметры] - addPolicyServer Kerberos | Имя пользователя | ClientCertificate [KeyBasedRenewal]

Добавление политики серверного приложения

При необходимости можно добавьте политики серверное приложение и пул приложений. Эта команда не производится установка двоичных файлов или пакетов. Один из следующих методов проверки подлинности, с которыми клиент подключается к серверу политики сертификата:
-   Kerberos: Использовать учетные данные Kerberos SSL
-   Имя пользователя: Использование с именем учетной записи для учетных данных SSL
-   ClientCertificate: Использовать учетные данные сертификата X.509 SSL
-   KeyBasedRenewal: Только политики, которые содержат шаблоны KeyBasedRenewal возвращаются клиенту. Этот флаг применяется только для проверки подлинности имя пользователя и на ClientCertificate.

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_deletePolicyServer"></a>-deletePolicyServer

CertUtil [параметры] - deletePolicyServer Kerberos | Имя пользователя | ClientCertificate [KeyBasedRenewal]

Удаление политики серверного приложения

При необходимости удалите политику серверное приложение и пул приложений. Эта команда не удаляет двоичные файлы и пакеты. Один из следующих методов проверки подлинности, с которыми клиент подключается к серверу политики сертификата:
1.  Kerberos: Использовать учетные данные Kerberos SSL
2.  Имя пользователя: Использование с именем учетной записи для учетных данных SSL
3.  ClientCertificate: Использовать учетные данные сертификата X.509 SSL
4.  KeyBasedRenewal: Сервер политики KeyBasedRenewal

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_oid"></a>-oid

CertUtil [параметры] - oid ObjectId [DisplayName | удаление [LanguageId [Type]]]

GroupId — идентификатор объекта CertUtil [параметры]

CertUtil [параметры] - oid AlgId | AlgorithmName [GroupId]

Отобразить ObjectId или задать отображаемое имя
-   ObjectId – ObjectId для отображения или добавить отображаемое имя
-   GroupId — десятичное число GroupId для идентификаторы objectid для перечисления
-   AlgId--шестнадцатеричное AlgId для ObjectId для поиска
-   AlgorithmName--Имя алгоритма для ObjectId для поиска
-   DisplayName — Отображаемое имя для хранения в доменных служб Active Directory
-   удалить – удалить отображаемое имя
-   LanguageId--Идентификатор языка (значение по умолчанию — текущий: 1033)
-   Тип "—" тип создаваемого доменных служб Active Directory объекта: 1 для шаблона (по умолчанию), 2 для политики выдачи, 3 для политики приложения
-   Используйте -f для создания объекта доменных служб Active Directory.

[-f].

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_error"></a>-Ошибка

CertUtil [параметры] - Ошибка ErrorCode

Отобразить текст сообщения об ошибке код

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_getreg"></a>-getreg

CertUtil [параметры] - getreg [{ЦС | Восстановление | политики | выйти из | шаблон | регистрации | цепочки | PolicyServers}\[ProgId\]] [Имя_значения_реестра]

Отображение параметра реестра

ЦС: Раздел реестра используйте ЦС

Восстановление: Раздел реестра ЦС используйте восстановления

Политика: Использовать раздел реестра модуля политики

Выход: Используйте сначала следует выйти из раздела реестра модуля

Шаблон: Используйте шаблон раздела реестра (используйте параметр-пользователя для пользовательских шаблонов)

зарегистрировать: Использовать раздел реестра регистрации (используйте параметр-пользователя для контекста пользователя)

Цепочка: Использовать раздел реестра конфигурации цепочки

PolicyServers: Использовать раздел реестра на серверах политики

Идентификатор progId: С помощью политики или выхода из модуля ProgId (имя подраздела реестра)

Имя_значения_реестра: имя значения реестра (используйте «Имя *», в качестве префикса сопоставления)

Значение: новый числовой, строка или дата значение реестра или имя файла. Если числовое значение начинается с «+» или «-», задания и в существующее значение реестра битов, указанное в новое значение.

Если строковое значение начинается с «+» или «-» и существующее значение имеет тип REG_MULTI_SZ, строка добавляется к или удаляется из существующее значение реестра. Чтобы принудительно создать значения REG_MULTI_SZ, добавьте в конец значения строки «\n».

Если значение начинается с «@», остальные значения — имя файла, содержащего шестнадцатеричное текстовое представление двоичного значения. Если он не ссылается на допустимый файл, вместо этого он анализируется как [Date] [+ |-] [dd:hh]--необязательно даты, плюс или минус необязательно дни и часы. Если указаны оба, используйте знак плюс (+) или минус (-)-разделитель. Используйте «now + dd:hh» для даты, относительно текущего времени.

Используйте «chain\ChainCacheResyncFiletime @now"эффективно очистить кэшированные списки отзыва сертификатов.

[-f]. [-пользователь] [-GroupPolicy] [-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_setreg"></a>-setreg

CertUtil [параметры] - setreg [{ЦС | Восстановление | политики | выйти из | шаблон | регистрации | цепочки | PolicyServers}\[ProgId\]] Имя_значения_реестра значение

Установка параметра реестра

ЦС: Раздел реестра используйте ЦС

Восстановление: Раздел реестра ЦС используйте восстановления

Политика: Использовать раздел реестра модуля политики

Выход: Используйте сначала следует выйти из раздела реестра модуля

Шаблон: Используйте шаблон раздела реестра (используйте параметр-пользователя для пользовательских шаблонов)

зарегистрировать: Использовать раздел реестра регистрации (используйте параметр-пользователя для контекста пользователя)

Цепочка: Использовать раздел реестра конфигурации цепочки

PolicyServers: Использовать раздел реестра на серверах политики

Идентификатор progId: С помощью политики или выхода из модуля ProgId (имя подраздела реестра)

Имя_значения_реестра: имя значения реестра (используйте «Имя *», в качестве префикса сопоставления)

Значение: новый числовой, строка или дата значение реестра или имя файла. Если числовое значение начинается с «+» или «-», задания и в существующее значение реестра битов, указанное в новое значение.

Если строковое значение начинается с «+» или «-» и существующее значение имеет тип REG_MULTI_SZ, строка добавляется к или удаляется из существующее значение реестра. Чтобы принудительно создать значения REG_MULTI_SZ, добавьте в конец значения строки «\n».

Если значение начинается с «@», остальные значения — имя файла, содержащего шестнадцатеричное текстовое представление двоичного значения. Если он не ссылается на допустимый файл, вместо этого он анализируется как [Date] [+ |-] [dd:hh]--необязательно даты, плюс или минус необязательно дни и часы. Если указаны оба, используйте знак плюс (+) или минус (-)-разделитель. Используйте «now + dd:hh» для даты, относительно текущего времени.

Используйте «chain\ChainCacheResyncFiletime @now"эффективно очистить кэшированные списки отзыва сертификатов.

[-f]. [-пользователь] [-GroupPolicy] [-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_delreg"></a>-delreg

CertUtil [параметры] - delreg [{ЦС | Восстановление | политики | выйти из | шаблон | регистрации | цепочки | PolicyServers}\[ProgId\]] [Имя_значения_реестра]

Удалить значение реестра

ЦС: Раздел реестра используйте ЦС

Восстановление: Раздел реестра ЦС используйте восстановления

Политика: Использовать раздел реестра модуля политики

Выход: Используйте сначала следует выйти из раздела реестра модуля

Шаблон: Используйте шаблон раздела реестра (используйте параметр-пользователя для пользовательских шаблонов)

зарегистрировать: Использовать раздел реестра регистрации (используйте параметр-пользователя для контекста пользователя)

Цепочка: Использовать раздел реестра конфигурации цепочки

PolicyServers: Использовать раздел реестра на серверах политики

Идентификатор progId: С помощью политики или выхода из модуля ProgId (имя подраздела реестра)

Имя_значения_реестра: имя значения реестра (используйте «Имя *», в качестве префикса сопоставления)

Значение: новый числовой, строка или дата значение реестра или имя файла. Если числовое значение начинается с «+» или «-», задания и в существующее значение реестра битов, указанное в новое значение.

Если строковое значение начинается с «+» или «-» и существующее значение имеет тип REG_MULTI_SZ, строка добавляется к или удаляется из существующее значение реестра. Чтобы принудительно создать значения REG_MULTI_SZ, добавьте в конец значения строки «\n».

Если значение начинается с «@», остальные значения — имя файла, содержащего шестнадцатеричное текстовое представление двоичного значения. Если он не ссылается на допустимый файл, вместо этого он анализируется как [Date] [+ |-] [dd:hh]--необязательно даты, плюс или минус необязательно дни и часы. Если указаны оба, используйте знак плюс (+) или минус (-)-разделитель. Используйте «now + dd:hh» для даты, относительно текущего времени.

Используйте «chain\ChainCacheResyncFiletime @now"эффективно очистить кэшированные списки отзыва сертификатов.

[-f]. [-пользователь] [-GroupPolicy] [-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_ImportKMS"></a>-ImportKMS

UserKeyAndCertFile - ImportKMS CertUtil [параметры] [CertId]

Импорт ключей и сертификатов пользователей в базу данных сервера для архивации ключа

UserKeyAndCertFile - Файл данных содержащего закрытые ключи пользователей и сертификаты для архивирования.  Это может быть одним из следующих:
-   Файл экспорта Exchange сервера управления ключами (KMS)
-   PFX-файла

CertId: KMS экспортировать маркер соответствия сертификата расшифровки файла.  См. в разделе [-хранить](#BKMK_Store).

Импорт сертификатов не выдан центром сертификации, используйте -f.

[-f]. [-silent] [-разделить] [-config Machine\CAName] [-p пароль] [-symkeyalg SymmetricKeyAlgorithm [, KeyLength]]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_ImportCert"></a>-ImportCert

CertUtil [параметры] - ImportCert Certfile [ExistingRow]

Импорт файла сертификата в базу данных

Используйте ExistingRow для импорта сертификата вместо ожидающего запроса тем же ключом.

Импорт сертификатов не выдан центром сертификации, используйте -f.

Центр сертификации также может потребоваться настроить для поддержки внешнего сертификата импорта: certutil - setreg ca\KRAFlags + KRAF_ENABLEFOREIGN

[-f]. [-config Machine\CAName]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_GetKey"></a>-GetKey

SearchToken - GetKey CertUtil [параметры] [RecoveryBlobOutFile]

CertUtil [параметры] - GetKey скрипт SearchToken OutputScriptFile

CertUtil [параметры] - GetKey SearchToken получения | восстановить OutputFileBaseName

Получить большой двоичный объект восстановления заархивированного закрытого ключа, создается скрипт восстановления или восстановление архивированных ключей

сценарий: Создание скрипта для извлечения и восстановления ключей (поведение по умолчанию при обнаружении соответствия множественное восстановления, или в том случае, если выходной файл не указан).

получить: получить один или несколько ключей восстановления большие двоичные объекты (поведение по умолчанию при обнаружении ровно один соответствующий кандидата восстановления, и в том случае, если указан выходной файл)

Восстановление: и восстановления закрытых ключей за один шаг (требуется агент восстановления ключей сертификатов и закрытых ключей)

SearchToken: Позволяет выбрать ключи и сертификаты для восстановления.

может быть одним из следующих:
1.  Общее имя сертификата
2.  Серийный номер сертификата
3.  Хэш сертификата SHA-1 (отпечаток)
4.  Хэш сертификата KeyId SHA-1 (идентификатор ключа субъекта)
5.  Имя запросившего (домен\пользователь)
6.  ИМЯ УЧАСТНИКА-ПОЛЬЗОВАТЕЛЯ (user@domain)

RecoveryBlobOutFile: выходной файл, содержащий цепочку сертификатов и связанный закрытый ключ, зашифрованный для одного или нескольких сертификатов агента восстановления ключей.

OutputScriptFile: выходной файл, содержащий пакетного скрипта для извлечения и восстановить закрытые ключи.

OutputFileBaseName: имя выходного файла базовой. Для поиска любое расширение усекается и строки, зависящей от сертификата и модуль .rec добавляются для каждого большого двоичного объекта ключа восстановления.  Каждый файл содержит цепочку сертификатов и связанный закрытый ключ, зашифрованный для одного или нескольких сертификатов агента восстановления ключей. Для восстановления любое расширение усекается и расширение .p12 добавляется.  Содержит цепочек сертификатов восстановленные и связанные закрытые ключи, хранящиеся в виде PFX-файла.

[-f]. [-UnicodeText] [-silent] [-config Machine\CAName] [-p пароль] [-ProtectTo SAMNameAndSIDList] [-csp поставщик]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_RecoverKey"></a>-RecoverKey

RecoveryBlobInFile - RecoverKey CertUtil [параметры] [PFXOutFile [RecipientIndex]]

Восстановить архивные закрытый ключ

[-f] [-user] [-silent] [-split] [-p Password] [-ProtectTo SAMNameAndSIDList] [-csp Provider] [-t Timeout]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_MergePFX"></a>-MergePFX

CertUtil [параметры] - MergePFX PFXInFileList PFXOutFile [ExtendedProperties]

PFXInFileList: Разделенный запятыми список входной файл PFX

PFXOutFile: Выходной файл PFX

ExtendedProperties: Включить расширенные свойства

Пароль, указанный в командной строке представляет собой список пароль, разделенных запятыми.  Если указано несколько паролей, для выходного файла используется последний пароль.  Если только один пароль указан или является последний пароль «*», пользователь будет запрашиваться пароль файла выходных данных.

[-f]. [-пользователь] [-разделить] [-p пароль] [-ProtectTo SAMNameAndSIDList] [-csp поставщик]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_ConvertEPF"></a>-ConvertEPF

CertUtil [параметры] - ConvertEPF PFXInFileList EPFOutFile [приведения | cast-] [V3CACertId] [, случайных данных]

Преобразовать PFX-файлы в файл EPF

PFXInFileList: Разделенный запятыми список входной файл PFX

EPF: Выходной файл EPF

приведение типов: Использование шифрования CAST 64

CAST-: Использование шифрования CAST 64 (Экспорт)

V3CACertId: Токен соответствия сертификата ЦС v3.  См. в разделе [-хранить](#BKMK_Store) CertId описание.

SALT: EPF выходной файл salt-строку

Пароль, указанный в командной строке представляет собой список пароль, разделенных запятыми. Если указано несколько паролей, для выходного файла используется последний пароль.  Если только один пароль указан или является последний пароль «*», пользователь будет запрашиваться пароль файла выходных данных.

[-f]. [-silent] [-разделить] [-dc DCName] [-p пароль] [-csp поставщик]

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_Options"></a>Параметры

Этот раздел определяет параметры, которые можно задать с помощью команды.

|Параметры|Описание|
|-------|-----------|
|-nullsign|Использовать хэш данных в качестве подписи|
|-f|Принудительная перезапись|
|— enterprise|Используйте хранилище сертификатов локального компьютера предприятия реестра|
|-пользователя|Использовать ключи HKEY_CURRENT_USER или хранилище сертификатов|
|-GroupPolicy|Хранилище сертификатов с помощью групповой политики|
|-ut|Отображение шаблонов пользователя|
|-mt|Отображение шаблонов компьютера|
|-Юникода|Запись перенаправленного вывода в формате Юникод|
|-UnicodeText|Записать выходной файл в кодировке Юникод|
|-gmt|Вывод времени по Гринвичу|
|-секунд|Время отображения с секундами и миллисекундами|
|-silent|Используйте автоматическую флаг, чтобы получить контекст шифрования|
|-разбиение|Разбиение внедренные элементы ASN.1 и сохранить в файлы|
|-v|Verbose операции|
|-privatekey|Отображение пароль и данные закрытого ключа|
|-Закрепить ПИН-код|Смарт-карты с ПИН-код|
|-urlfetch|Извлечь и проверить сертификаты AIA и CDP CRL|
|-config Machine\CAName|Строка имени ЦС и компьютера|
|-PolicyServer URLOrId|URL-адрес сервера политики или идентификатор. Для выбора U / I, используйте - PolicyServer. Для всех серверов политики, используйте - PolicyServer *|
|-Анонимный|Использование анонимных учетных данных SSL|
|-Kerberos|Использовать учетные данные Kerberos SSL|
|-ClientCertificate ClientCertId|Используйте учетные данные сертификата X.509 SSL. Для выбора U / I, используйте - clientCertificate.|
|Имя пользователя - UserName|Использование с именем учетной записи для учетных данных SSL. Для выбора U / I, используйте - UserName.|
|-Cert CertId|Сертификат для подписи|
|-dc DCName|Целевой конкретный контроллер домена|
|-ограничение RestrictionList|Список ограничений, разделенные запятыми. Каждое ограничение состоит в том, имя столбца, оператор сравнения и постоянное целое число, строка или дата. Одно имя столбца может быть перед знаком плюс или минус, чтобы указать порядок сортировки. Примеры</br>"RequestId = 47"</br>«+ RequesterName > =, RequesterName < b»</br>"-RequesterName > DOMAIN, Disposition = 21"|
|-out ColumnList|Разделенный запятыми список столбцов|
|-p пароль|Пароль|
|-ProtectTo SAMNameAndSIDList|Разделенный запятыми список имя или ИД безопасности SAM|
|-Поставщик csp|Поставщик|
|-t время ожидания|Время ожидания выборки URL-адрес в миллисекундах|
|-symkeyalg SymmetricKeyAlgorithm [, KeyLength]|Имя алгоритма симметричного ключа с необязательным длина ключа, пример: AES, 128 или 3DES|

Вернитесь к [меню](#BKMK_menu)

## <a name="BKMK_AddedExamples"></a>Примеры дополнительных certutil

Некоторые примеры использования этой команды см. в разделе
1.  [Примеры Certutil для управления службы сертификатов Active Directory (AD CS) из командной строки](https://social.technet.microsoft.com/wiki/contents/articles/3063.certutil-examples-for-managing-active-directory-certificate-services-ad-cs-from-the-command-line.aspx)
2.  [Задачи Certutil для управления сертификатами](https://technet.microsoft.com/library/cc772898.aspx)
3.  [Двоичный запрос экспорта, с помощью средства командной строки CertUtil.exe пошагового руководства](https://social.technet.microsoft.com/wiki/contents/articles/7573.active-directory-certificate-services-pki-key-archival-and-management.aspx)
4.  [Продление сертификата корневого ЦС](https://social.technet.microsoft.com/wiki/contents/articles/2016.root-ca-certificate-renewal.aspx)
5.  [Certutil](https://msdn.microsoft.com/subscriptions/cc773087.aspx)

Вернитесь к [меню](#BKMK_menu)
