---
title: Ролей, служб ролей и компонентов, включенных в Windows Server - основных серверных компонентов
description: Какие роли и компоненты входят в вариант установки Server Core из Windows Server?
ms.prod: windows-server-threshold
ms.mktglfcycl: manage
ms.sitesec: library
author: lizap
ms.localizationpriority: medium
ms.date: 02/23/2018
ms.openlocfilehash: 65729eb68c9590fd6316f5650be48f33c19c926d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59859295"
---
# <a name="roles-role-services-and-features-included-in-windows-server---server-core"></a>Ролей, служб ролей и компонентов, включенных в Windows Server - основных серверных компонентов

> Относится к: Windows Server (полугодовой канал) и Windows Server 2016

Обычно мы говорим о [что элемента *не* в Server Core](server-core-removed-roles.md) — теперь мы собираемся попробовать другой подход и говорить, что в *включены* и является ли что-то *устанавливается по умолчанию*. Следующие роли, службы ролей и компоненты являются *в* с вариантом установки основных серверных компонентов Windows Server. Используйте эти сведения помогут понять, если параметр Server Core работает для вашей среды. Так как это большой список, рассмотрите возможность поиска для конкретных ролей и компонентов, вас интересует - Если поиск не возвращает, что вы искали, оно не указано в Server Core.

Например при поиске «Remote Desktop Session Host» - вы не найдет на этой странице. Том, что узла сеансов удаленных рабочих Столов не включен в образ основных серверных компонентов.

Помните, что вы можете [всегда производят](server-core-removed-roles.md) на каком элемента *не* включены. Это просто другой способ рассмотреть еще такие аспекты.

## <a name="roles-included-in-server-core"></a>Роли, включенные в основных серверных компонентов
Вариант установки Server Core включает в себя следующие роли сервера.

| Роль                                            | Имя                           | Устанавливается по умолчанию? |
|-------------------------------------------------|--------------------------------|-----------------------|
| Службы сертификатов Active Directory           | Сертификат AD                 | N                     |
| Доменные службы Active Directory                | AD-Domain-Services             | N                     |
| Службы федерации Active Directory (AD FS)            | Федерации ADFS                | N                     |
| Службы Active Directory облегченного доступа к каталогам (AD LDS) | ADLDS                          | N                     |
| Службы управления правами Active Directory (AD RMS)     | ADRMS                          | N                     |
| Аттестация работоспособности устройства                       | DeviceHealthAttestationService | N                     |
| DHCP-сервер                                     | DHCP                           | N                     |
| DNS-сервер                                      | DNS                            | N                     |
| Файловые службы и службы хранилища                       | FileAndStorage-Services        | Y                     |
| Служба защиты узла                           | HostGuardianServiceRole        | N                     |
| Hyper-V                                         | Hyper-V                        | N                     |
| Службы печати и документов                     | Службы печати                 | N                     |
| Удаленный доступ                                   | Удаленного доступа                   | N                     |
| Службы удаленных рабочих столов                         | Службы удаленной рабочего стола        | N                     |
| Службы активации корпоративных лицензий                      | VolumeActivation               | N                     |
| Веб-сервер IIS                                  | Веб сервера                     | N                     |
| Режим Windows Server Essentials            | ServerEssentialsRole           | N                     |
| Службы Windows Server Update Services                  | UpdateServices                 | N                     |

## <a name="role-services-included-in-server-core"></a>Службы ролей, включенные в основных серверных компонентов
Вариант установки Server Core включает в себя следующие службы ролей.

| Роль                                  | Служба роли                                                   | Имя                    | Устанавливается по умолчанию? |
|---------------------------------------|----------------------------------------------------------------|-------------------------|-----------------------|
| Службы сертификатов Active Directory | Центр сертификации                                        | ADCS-Cert центра     | N                     |
|                                       | Веб-служба политик регистрации сертификатов                      | ADCS-регистрация Web-Pol     | N                     |
|                                       | Веб-служба регистрации сертификатов                             | ADCS-регистрация Web-Svc     | N                     |
|                                       | Служба регистрации в центре сертификации через Интернет                         | ADCS подача заявок через Интернет     | N                     |
|                                       | Служба подачи заявок на сетевые устройства                              | Регистрация для устройств ADCS  | N                     |
|                                       | Сетевой ответчик                                               | ADCS-Online-Cert        | N                     |
| Active Directory Rights Management    | Сервер управления правами Active Directory                      | ADRMS-сервер            | N                     |
|                                       | Поддержка федерации удостоверений                                    | ADRMS-Identity          | N                     |
| Файловые службы и службы хранилища             | Файловые службы и службы iSCSI                                        | Файловые службы           | N                     |
|                                       | Файловый сервер                                                    | Файловый сервер федерации Active Directory           | N                     |
|                                       | Служба BranchCache для сетевых файлов                                  | FS BranchCache          | N                     |
|                                       | Дедупликация данных                                             | FS-дедупликации данных   | N                     |
|                                       | Пространства имен DFS                                                 | Пространство имен DFS FS        | N                     |
|                                       | Репликация DFS                                                | FS-DFS-Replication      | N                     |
|                                       | Диспетчер ресурсов файлового сервера                                   | FS-Resource-Manager     | N                     |
|                                       | Служба агента VSS файлового сервера                                  | FS-VSS-Agent            | N                     |
|                                       | Целевой сервер iSCSI                                            | iSCSITarget-Server      | N                     |
|                                       | Поставщик хранилища цели (поставщиков оборудования VDS и VSS) iSCSI | iSCSITarget VSS службы виртуальных ДИСКОВ     | N                     |
|                                       | Сервер для NFS                                                 | Служба федерации Active Directory NFS          | N                     |
|                                       | рабочие папки                                                   | FS SyncShareService     | N                     |
|                                       | Службы хранения                                               | Службы хранилища        | Y                     |
| Службы печати и документов           | Сервер печати                                                   | Сервер печати            | N                     |
|                                       | Служба LPD                                                    | Служба печати LPD       | N                     |
| Удаленный доступ                         | DirectAccess и VPN (RAS)                                     | DirectAccess-VPN        | N                     |
|                                       | Маршрутизация                                                        | Маршрутизация                 | N                     |
|                                       | Прокси-сервер веб-приложения                                          | Прокси веб-приложения   | N                     |
| Службы удаленных рабочих столов               | Посредник подключений к удаленному рабочему столу                               | Посредник для подключений служб удаленных рабочих СТОЛОВ   | N                     |
|                                       | Лицензирование удаленных рабочих столов                                       | Лицензирование служб удаленных рабочих СТОЛОВ           | N                     |
|                                       | Узел виртуализации удаленных рабочих столов                             | Виртуализация служб удаленных рабочих СТОЛОВ      | N                     |
| Веб-сервер (IIS)                      | Веб-сервер                                                     | Web-WebServer           | N                     |
|                                       | Общие компоненты HTTP                                           | Web-Common-Http         | N                     |
|                                       | Документ по умолчанию                                               | Web-Default-Doc         | N                     |
|                                       | Просмотр каталогов                                             | Web-Dir-Browsing        | N                     |
|                                       | Ошибки HTTP                                                    | Web-Http-Errors         | N                     |
|                                       | Статическое содержимое                                                 | Web-Static-Content      | N                     |
|                                       | Перенаправление HTTP                                               | Web-Http-Redirect       | N                     |
|                                       | Публикация WebDAV                                              | Веб DAV-публикации      | N                     |
|                                       | Работоспособность и диагностика                                         | Web-Health              | N                     |
|                                       | Ведение журнала HTTP                                                   | Ведение журнала Http Web        | N                     |
|                                       | Настраиваемое протоколирование                                                 | Веб Custom-ведения журнала      | N                     |
|                                       | Средства ведения журнала                                                  | Веб Log-Libraries       | N                     |
|                                       | Ведение журнала ODBC                                                   | Ведение журнала ODBC Web        | N                     |
|                                       | Монитор запросов                                              | Web-Request-Monitor     | N                     |
|                                       | Трассировка                                                        | Web-Http трассировка        | N                     |
|                                       | Производительность                                                    | Веб-тестами производительности         | N                     |
|                                       | Сжатие статического содержимого                                     | Web-Stat-Compression    | N                     |
|                                       | Сжатие динамического содержимого                                    | Веб Dyn сжатие     | N                     |
|                                       | Безопасность                                                       | Веб безопасности            | N                     |
|                                       | Request Filtering                                              | Веб-фильтр           | N                     |
|                                       | Обычная проверка подлинности                                           | Web обычной проверки подлинности.          | N                     |
|                                       | Поддержка централизованного SSL-сертификатов                            | Веб CertProvider        | N                     |
|                                       | Проверка подлинности с сопоставлением сертификата клиента                      | Веб клиента Auth         | N                     |
|                                       | Дайджест-проверка подлинности                                          | Веб дайджест-проверки подлинности         | N                     |
|                                       | Проверка подлинности с сопоставлением сертификата клиента IIS                  | Веб Cert-Auth           | N                     |
|                                       | IP-адрес и ограничения домена                                     | Веб IP-безопасности         | N                     |
|                                       | Авторизация URL-адреса                                              | Веб-URL-адрес Auth            | N                     |
|                                       | Проверка подлинности Windows                                         | Веб Windows-Auth        | N                     |
|                                       | Разработка приложений                                        | Web-App-Dev             | N                     |
|                                       | Расширяемость .NET 3.5                                         | Web-Net-Ext             | N                     |
|                                       | Расширяемость .NET 4.6                                         | Web-Net-Ext45           | N                     |
|                                       | Инициализация приложения                                     | Инициализации веб приложений             | N                     |
|                                       | ASP                                                            | Веб ASP                 | N                     |
|                                       | ASP.NET 3.5                                                    | Веб Asp-Net             | N                     |
|                                       | ASP.NET 4.6                                                    | Web-Asp-Net45           | N                     |
|                                       | CGI                                                            | Web CGI                 | N                     |
|                                       | Расширения ISAPI                                               | Web-ISAPI-Ext           | N                     |
|                                       | ISAPI Filters                                                  | Web-ISAPI-фильтра        | N                     |
|                                       | Включения на стороне сервера                                           | Включает в себя Web            | N                     |
|                                       | Протокол WebSocket                                             | Веб WebSockets          | N                     |
|                                       | FTP-сервер                                                     | Веб Ftp сервера          | N                     |
|                                       | Служба FTP                                                    | Веб Ftp службы         | N                     |
|                                       | Расширяемость FTP                                              | Web-Ftp-Ext             | N                     |
|                                       | Средства управления                                               | Web-Mgmt-Tools          | N                     |
|                                       | Совместимость управления IIS 6                                 | Web-Mgmt совместимости         | N                     |
|                                       | Совместимость метабазы IIS 6                                   | Веб метабазы            | N                     |
|                                       | IIS 6 сценариев средства                                          | Веб-Lgcy сценарии      | N                     |
|                                       | Совместимость WMI IIS 6                                        | Веб WMI                 | N                     |
|                                       | Сценарии и средства управления IIS                               | Веб средств работы со сценариями     | N                     |
|                                       | Служба управления                                             | Веб Mgmt службы        | N                     |
| Службы Windows Server Update Services        | Подключение WID                                               | UpdateServices-WidDB    | N                     |
|                                       | Службы WSUS                                                  | UpdateServices-Services | N                     |
|                                       | Подключение к SQL Server                                        | UpdateServices-DB       | N                     |

## <a name="features-included-in-server-core"></a>Компоненты, включенные в основных серверных компонентов
Вариант установки Server Core включает в себя следующие компоненты.

| Компонент                                                | Имя                               | Устанавливается по умолчанию? |
|--------------------------------------------------------|------------------------------------|-----------------------|
| Компоненты .NET framework 3.5                            | NET-Framework функции             | N                     |
| .NET framework 3.5 (включает .NET 2.0 и 3.0)       | NET-Framework-Core                 | (Удалить)             |
| Активация по протоколам HTTP                                        | NET-HTTP-Activation                | N                     |
| Активация по отличным от HTTP протоколам                                    | NET-не HTTP-активные                 | N                     |
| Компоненты .NET framework 4.6                            | NET-Framework-45-функции          | Y                     |
| .NET Framework 4.6                                     | NET-Framework-45-Core              | Y                     |
| ASP.NET 4.6                                            | NET-Framework-45-ASPNET            | N                     |
| Службы WCF                                           | NET-WCF-Services45                 | Y                     |
| Активация по протоколам HTTP                                        | NET-WCF-HTTP-Activation45          | N                     |
| Активация (MSMQ) очереди сообщений                      | NET-WCF-MSMQ-Activation45          | N                     |
| Активация именованного канала                                  | NET-WCF-Pipe-Activation45          | N                     |
| Активация TCP                                         | NET-WCF-TCP-Activation45           | N                     |
| Совместное использование порта TCP                                       | NET-WCF-TCP-PortSharing45          | Y                     |
| Фоновая интеллектуальная служба передачи (BITS)         | BITS                               | N                     |
| Облегченный сервер загрузки                                         | BITS-компакт Server                | N                     |
| Шифрование диска BitLocker                             | BitLocker                          | N                     |
| BranchCache                                            | BranchCache                        | N                     |
| Клиент для NFS                                         | NFS-клиента                         | N                     |
| Контейнеры                                             | Контейнеры                         | N                     |
| Мост для центра обработки данных                                   | Мост центра данных               | N                     |
| Enhanced Storage                                       | EnhancedStorage                    | N                     |
| Отказоустойчивая кластеризация                                    | Отказоустойчивая кластеризация                | N                     |
| Управление групповой политикой                                | Консоль управления групповыми политиками                               | N                     |
| Качество обслуживания ввода-вывода                                 | Дисковый ввод-вывод QoS                         | N                     |
| Внедряемое веб-ядро служб IIS                                  | Веб WHC                            | N                     |
| Сервер управления IP-адресами (IPAM)                    | IPAM                               | N                     |
| Службы iSNS-сервера                                    | ISNS                               | N                     |
| Расширение IIS OData для управления                         | ManagementOdata                    | N                     |
| Media Foundation                                       | Сервер мультимедиа            | N                     |
| служба очередей сообщений                                        | MSMQ                               | N                     |
| Службы очереди сообщений                               | Служба MSMQ                      | N                     |
| Сервер очереди сообщений                                 | MSMQ-Server                        | N                     |
| Интеграция служб каталогов                          | MSMQ-Directory                     | N                     |
| Поддержка HTTP                                           | MSMQ-HTTP-Support                  | N                     |
| Триггеры очереди сообщений                               | Триггеры MSMQ                      | N                     |
| Служба маршрутизации                                        | MSMQ-маршрутизации                       | N                     |
| DCOM-прокси очереди сообщений                             | MSMQ DCOM                          | N                     |
| Multipath I/O;                                          | Multipath IO                       | N                     |
| Соединитель MultiPoint                                   | Соединитель multiPoint               | N                     |
| Соединитель multiPoint Services                          | Служб multiPoint соединителей      | N                     |
| Диспетчер multiPoint и MultiPoint Dashboard            | MultiPoint-Tools                   | N                     |
| Балансировка сетевой нагрузки                                 | NLB                                | N                     |
| Протокол однорангового разрешения имен (PNRP)                          | PNRP                               | N                     |
| Quality Windows Audio Video Experience (qWave)                 | qWave                              | N                     |
| удаленное разностное сжатие;                        | RDC                                | N                     |
| Средства удаленного администрирования сервера                     | RSAT                               | N                     |
| Средства администрирования компонентов                           | RSAT-Feature-Tools                 | N                     |
| Служебные программы администрирования шифрования диска BitLocker  | Средства удаленного администрирования сервера компонента средства BitLocker       | N                     |
| Инструменты LLDP DataCenterBridging                          | RSAT-DataCenterBridging-LLDP-Tools | N                     |
| Средства отказоустойчивости кластеров                              | RSAT-Clustering                    | N                     |
| Модуль отказоустойчивого кластера для Windows PowerShell         | PowerShell для кластеризации RSAT         | N                     |
| Сервер автоматизации отказоустойчивого кластера                     | Кластеризация AutomationServer средства удаленного администрирования сервера   | N                     |
| Интерфейс командной отказоустойчивого кластера                     | Кластеризация CmdInterface средства удаленного администрирования сервера       | N                     |
| Клиент Management (IPAM) адрес IP-адрес                    | Компонент IPAM-клиента                | N                     |
| Средства для экранированной виртуальной Машины                                      | RSAT-экранированных VM-Tools             | N                     |
| Модуль реплики хранилища для Windows PowerShell          | Средства удаленного администрирования сервера реплики хранилища               | N                     |
| Средства администрирования ролей                              | RSAT-Role-Tools                    | N                     |
| Средства AD DS и AD LDS                                 | Средства RSAT-AD                      | N                     |
| Модуль Active Directory для Windows PowerShell         | RSAT-AD-PowerShell                 | N                     |
| Средства AD DS                                            | ДОБАВЛЯЕТ СРЕДСТВА УДАЛЕННОГО АДМИНИСТРИРОВАНИЯ СЕРВЕРА                          | N                     |
| Центр администрирования Active Directory                 | RSAT-AD-AdminCenter                | N                     |
| Оснастки и программы командной строки доменных служб Active Directory                  | ДОБАВЛЯЕТ средства RSAT                    | N                     |
| AD LDS оснастки и программы командной строки                 | СРЕДСТВА УДАЛЕННОГО АДМИНИСТРИРОВАНИЯ СЕРВЕРА ADLDS                         | N                     |
| Средства управления Hyper-V                               | RSAT-Hyper-V-Tools                 | N                     |
| Модуль Hyper-V для Windows PowerShell                  | PowerShell для Hyper-V                 | N                     |
| Windows Server Update Services, средства                   | UpdateServices-RSAT                | N                     |
| API и командлеты PowerShell                             | UpdateServices-API                 | N                     |
| Средства DHCP-сервера                                      | RSAT-DHCP                          | N                     |
| DNS Server Tools                                       | RSAT-DNS-сервер                    | N                     |
| Средства управления удаленным доступом                         | RSAT-RemoteAccess                  | N                     |
| модуль удаленного доступа для Windows PowerShell.            | RSAT-RemoteAccess-PowerShell       | N                     |
| RPC-через-HTTP-прокси                                    | RPC-over-HTTP-Proxy                | N                     |
| Коллекция событий установки и загрузки                        | Программа установки и Boot сбора событий    | N                     |
| простые службы TCP/IP;                                 | Simple-TCPIP                       | N                     |
| Поддержка протоколов общего доступа к файлам SMB 1.0 и CIFS                      | FS-SMB1                            | Y                     |
| Ограничение пропускной способности SMB                                    | FS SMBBW                           | N                     |
| Служба SNMP                                           | Служба SNMP                       | N                     |
| WMI-поставщик SNMP                                      | WMI-поставщик SNMP                  | N                     |
| Клиент Telnet                                          | Клиент Telnet                      | N                     |
| Средства экранирования виртуальных машин для управления структурой               | FabricShieldedTools                | N                     |
| Компоненты Защитника Windows                              | Компоненты для Защитника Windows          | Y                     |
| Защитник Windows                                       | Защитник Windows                   | Y                     |
| Внутренняя база данных Windows                              | Windows внутренней-базы данных          | N                     |
| Windows PowerShell                                     | PowerShellRoot                     | Y                     |
| Windows PowerShell 5.1                                 | PowerShell                         | Y                     |
| Подсистемы Windows PowerShell 2.0                          | PowerShell V2                      | (Удалить)             |
| Windows PowerShell Desired State Configuration службы | Служба DSC                        | N                     |
| Windows PowerShell Web Access                          | WindowsPowerShellWebAccess         | N                     |
| Служба активации процессов Windows                     | БЫЛО                                | N                     |
| Модель процессов                                          | БЫЛ Process-Model                  | N                     |
| Платформа .NET 3.5                                   | БЫЛ NET-Environment                | N                     |
| API-интерфейсы конфигурации                                     | БЫЛ Config-APIs                    | N                     |
| Система архивации данных Windows Server                                  | Архивации данных Windows Server              | N                     |
| Средства миграции Windows Server                         | Миграция                          | N                     |
| Стандартизированное управление хранилищами Windows             | WindowsStorageManagementService    | N                     |
| Расширение IIS WinRM                                    | WinRM-IIS-Ext                      | N                     |
| WINS-сервер                                            | WINS                               | N                     |
| Поддержка WoW64                                          | Поддержка WoW64                      | Y                     |
|                                                        |                                    |                       |
