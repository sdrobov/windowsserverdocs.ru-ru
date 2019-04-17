---
title: Устранение неполадок постоянно подключенного VPN-профиля
description: В этом разделе приведены инструкции по проверке и устранение неполадок развертывания VPN в Windows Server 2016.
ms.prod: windows-server-threshold
ms.technology: networking-ras
ms.topic: article
ms.assetid: 4d08164e-3cc8-44e5-a319-9671e1ac294a
ms.localizationpriority: medium
ms.date: 06/11/2018
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 47d22d566407f45fe6ac78931ffea7b5b2854a1c
ms.sourcegitcommit: 4893d79345cea85db427224bb106fc1bf88ffdbc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "6067513"
---
# Устранение неполадок постоянно подключенного VPN-профиля 

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows 10

Если настроек VPN несовпадение подключение клиентов к внутренней сети, причиной этого является скорее всего недопустимый сертификат VPN, неверно политики сервера политики сети или проблем с сценарии развертывания клиента или в Маршрутизация и удаленный доступ. Первым шагом по устранению неполадок и тестирования VPN-подключение — понять основные компоненты инфраструктуры VPN. 

Вы можете устранить проблемы подключения несколькими способами. Проблемы на стороне клиента и устранение общих неполадок журналы приложений на клиентских компьютерах очень полезным. Для проверки подлинности конкретной проблемы журнал сервера политики сети на сервер политики сети помогают определить источник проблемы.


## Коды ошибок


### Код ошибки: 800

-   **Описание ошибки.** Подключение к удаленному не была предпринята попытка Туннели VPN не удалось. VPN-сервер может быть недоступен. Если это подключение попытка использования туннеля L2TP/IPsec, параметры безопасности, необходимые для согласования не настроена надлежащим образом IPsec.


-   **Возможные причины.** Эта ошибка возникает, когда **Автоматическое** Тип туннеля VPN и происходит сбой попытки подключения для всех Туннели VPN.

-   **Возможные решения:**

    -   Если вы знаете, какой туннеля для развертывания, задайте тип VPN этим типом конкретного туннеля на стороне клиента VPN.

    -   Делая VPN-подключение с помощью туннеля конкретного типа, подключения по-прежнему завершится ошибкой, но это приведет к более туннеля определенной ошибки (например, «GRE заблокирован для PPTP»).

    -   Эта ошибка также возникает, когда VPN-сервер недоступен или сбое подключения через туннель.

-   **Удостоверься:**

    -   IKE-порты (UDP ports500 и 4500) не заблокирован.

    -   Правильные сертификаты для IKE присутствуют на клиенте и сервере.

### Код ошибки: 809

-   **Описание ошибки.**  Не удается установить сетевое подключение между компьютером и VPN-сервера, так как удаленный сервер не отвечает. Это может быть вызвано одно из устройств сети \ (например, брандмауэры, NAT, routers\) между компьютером и удаленным сервером не настроена на поддержку VPN-подключений. Обратитесь к администратору или поставщика услуг, чтобы определить, какое устройство может быть причиной проблемы.

-   **Возможные причины.** Эта ошибка вызвана заблокированных UDP 500 или 4500 порты на VPN-сервер или брандмауэр.

-   **Возможное решение.** Убедитесь, что UDP ports500 и 4500 разрешены через все брандмауэры между клиентом и сервером RRAS. 
    
    
### Код ошибки: 812

-   **Описание ошибки.** Не удается подключиться к VPN. Подключение не выполнено из-за политика, настроенная на сервере удаленного доступа или VPN. В частности метод проверки подлинности сервера позволяют проверить ваше имя пользователя и пароль, может не соответствовать метод проверки подлинности, настроенный в вашем профиле подключения. Обратитесь к администратору сервера удаленного доступа и уведомить его этой ошибки.

-   **Возможные причины:**

    -  Обычно такой ошибки это том, что NPS указал условие проверки подлинности, клиент не отвечают. Например NPS может задать использование сертификатов для защиты подключения PEAP, но клиент пытается использовать протокол EAP-MSCHAP версии 2.

    -  Журнал событий 20276 регистрируется в средстве просмотра событий при параметра протокол проверки подлинности сервера VPN на основе RRAS не совпадают с соответствующими версиями на клиентском компьютере VPN.

-   **Возможное решение.** Убедитесь, что ваша конфигурация клиента совпадает условия, приведенные на сервер политики сети.


### Код ошибки: 13806

-   **Описание ошибки.** IKE не удалось найти действительный сертификат компьютера. Обратитесь к администратору безопасности сети об установке действительного сертификата в соответствующее хранилище сертификатов.

-   **Возможные причины.** Эта ошибка обычно возникает, когда нет сертификат компьютера или корневой сертификат компьютера на VPN-сервер.

-   **Возможное решение.** Убедитесь, что сертификаты, описанные в этом развертывания устанавливаются на клиентском компьютере и VPN-сервер.

### Код ошибки: 13801

-   **Описание ошибки.** Неприемлемые учетные данные проверки подлинности IKE.

-   **Возможные причины.** Эта ошибка обычно возникает в одном из следующих случаев:

    -   Сертификат компьютера, используемый для проверки IKEv2 на сервере удаленного доступа не имеет **Проверки подлинности сервера** в группе **Улучшенного ключа**.

    -   Сертификат компьютера на сервере удаленного доступа истек.

    -   Корневой сертификат для проверки сертификата сервера удаленного доступа отсутствует на клиентском компьютере.

    -   Имя VPN-сервера, используемый на клиентском компьютере не соответствует **имя субъекта** сертификата сервера.

-   **Возможное решение.** Убедитесь, что сертификат сервера включает в себя **Проверки подлинности сервера** в группе **Улучшенного ключа**. Убедитесь, что по-прежнему действительный сертификат сервера. Убедитесь, что используется ЦС находится в списке **Доверенных корневых центров сертификации** на сервере RRAS. Убедитесь, что VPN-клиент подключается, используя полное доменное имя VPN-сервера, представленную в сертификате VPN-сервер.


### Код ошибки: 0x80070040

-   **Описание ошибки.** Сертификат сервера не имеет **Проверки подлинности сервера** как одно из его операции использования сертификата.

-   **Возможные причины.** Эта ошибка может возникать, если нет сертификата проверки подлинности сервера установлен на сервере удаленного доступа.

-   **Возможное решение.** Проверьте правильность сертификат компьютера, который использует сервер удаленного доступа для **IKEv2** **Проверки подлинности сервера** как одна из операций использования сертификата.

### Код ошибки: 0x800B0109

Как правило на клиентском компьютере VPN к домену Active Directory на основе. При использовании учетных данных домена для входа на VPN-сервер, сертификат автоматически устанавливается в доверенных корневых центров сертификации хранения. Тем не менее если компьютер не присоединен к домену или использовать цепи альтернативных сертификата, могут возникнуть проблемы.

-   **Описание ошибки.** Цепочка сертификатов обработана, но не завершается в корневой сертификат, который не доверяет поставщик доверия.

-   **Возможные причины.** Эта ошибка может возникнуть, если не установлен соответствующий доверенного корневого Центра сертификации в доверенных корневых центров сертификации хранить на клиентском компьютере.

-   **Возможное решение.** Убедитесь, что корневой сертификат установлен на клиентском компьютере в хранилище доверенных корневых центров сертификации.

## Журналы

### Журналы приложений

Журналы приложений на клиентских компьютерах запишите большая часть более высокого уровня подробные сведения о событиях подключения VPN.

Найдите события от источника RasClient. Все сообщения об ошибках возвращает код ошибки в конце сообщения. Ниже приведены некоторые наиболее распространенные коды ошибок, но полный список доступен в [Маршрутизация и удаленный доступ коды ошибок](https://msdn.microsoft.com/library/windows/desktop/bb530704.aspx).

## Журналы сервера политики сети
Сервер политики сети создает и хранит журналы учета сервера политики сети. По умолчанию они хранятся в %SYSTEMROOT%\\System32\\Logfiles\\ в файле с именем в*XXXX.* txt, где *XXXX* — это дата создания файла.

По умолчанию эти журналы размещаются в формате с разделителями-запятыми, но они не включают строкой заголовка. Является строкой заголовка:

```
ComputerName,ServiceName,Record-Date,Record-Time,Packet-Type,User-Name,Fully-Qualified-Distinguished-Name,Called-Station-ID,Calling-Station-ID,Callback-Number,Framed-IP-Address,NAS-Identifier,NAS-IP-Address,NAS-Port,Client-Vendor,Client-IP-Address,Client-Friendly-Name,Event-Timestamp,Port-Limit,NAS-Port-Type,Connect-Info,Framed-Protocol,Service-Type,Authentication-Type,Policy-Name,Reason-Code,Class,Session-Timeout,Idle-Timeout,Termination-Action,EAP-Friendly-Name,Acct-Status-Type,Acct-Delay-Time,Acct-Input-Octets,Acct-Output-Octets,Acct-Session-Id,Acct-Authentic,Acct-Session-Time,Acct-Input-Packets,Acct-Output-Packets,Acct-Terminate-Cause,Acct-Multi-Ssn-ID,Acct-Link-Count,Acct-Interim-Interval,Tunnel-Type,Tunnel-Medium-Type,Tunnel-Client-Endpt,Tunnel-Server-Endpt,Acct-Tunnel-Conn,Tunnel-Pvt-Group-ID,Tunnel-Assignment-ID,Tunnel-Preference,MS-Acct-Auth-Type,MS-Acct-EAP-Type,MS-RAS-Version,MS-RAS-Vendor,MS-CHAP-Error,MS-CHAP-Domain,MS-MPPE-Encryption-Types,MS-MPPE-Encryption-Policy,Proxy-Policy-Name,Provider-Type,Provider-Name,Remote-Server-Address,MS-RAS-Client-Name,MS-RAS-Client-Version
```

Если вставить эту строку заголовка как первую строку файла журнала, затем импортируйте файл в Microsoft Excel, столбцы будет называться правильно.

Журналы сервера политики сети могут быть полезны для диагностики проблем, связанных с политикой. Дополнительные сведения о журналах сервера политики сети см. в разделе [Интерпретировать NPS журналов базы данных формата](https://technet.microsoft.com/library/cc771748.aspx).

## Проблемы VPN_Profile.ps1 сценария
Наиболее распространенные проблемы при выполнении сценария VPN_ Profile.ps1 вручную включают:

- Использовать средство удаленного подключения?  Убедитесь, что не следует использовать протокола удаленного рабочего СТОЛА или другого метода удаленное подключение, как messes обнаружения входа пользователя.

- Является пользователь администратором, локальный компьютер?  Убедитесь, что при выполнении сценария VPN_Profile.ps1, у пользователя есть права администратора.

- У вас есть дополнительные функции безопасности PowerShell включено? Убедитесь, что политику выполнения PowerShell не блокирует сценария. Вы можете рассмотреть выключение режима ограниченного языка, если параметр включен, перед запуском сценария. Вы можете активировать режим ограниченного языка после сценарий выполнен успешно.

## Проблем с подключением клиент VPN
Небольшой неправильная конфигурация может привести к клиентского подключения может завершиться сбоем и может оказаться сложной задачей для поиска причины.  Клиент VPN проходит через несколько шагов, прежде чем устанавливать подключение. При устранении проблем с подключением клиента, пройти процедуру исключения следующим:


1. Подключен компьютер шаблона извне Проверка **whatismyip** необходимо показать общий IP-адрес, который не принадлежит вам.

2. Может указывать имя сервера удаленного доступа или VPN на IP-адрес? На **Панели управления** \> **сеть** и **Интернет** \> **Сетевые подключения**, откройте свойства для профиля VPN. Значения на вкладке " **Общие** " должно быть открыто разрешимым через DNS.

3. Получить доступ к VPN-сервер из внешней сети? Рассмотрите возможность открытия во внешний интерфейс управления сообщение ICMP (Internet Protocol) и вызовы имя от удаленного клиента. После успешного завершения ping, вы можете удалить ICMP разрешить правила.

4. У вас есть внутренние и внешние сетевые адаптеры на VPN-сервера настроены правильно Они в разных подсетях? Внешний сетевой Адаптер подключиться нужный интерфейс в брандмауэре?

5. Открыты UDP 500 и порты 4500 от клиента для внешнего интерфейса VPN-сервера? Проверьте клиентский брандмауэр, брандмауэр сервера и все аппаратные брандмауэры. IPSEC использует UDP порт 500, поэтому убедитесь что, у вас нет IPEC отключен или блокируется в любом месте.

7. Проверки сертификата сбой? Убедитесь, что сервер политики сети есть сертификат проверки подлинности сервера, который может обслуживать запросы IKE. Убедитесь, что у вас есть IP-адрес сервера правильный VPN указан как клиент сервера политики сети. Убедитесь, что вход выполняется с помощью протокола PEAP и свойства защищенного EAP следует разрешить только проверки подлинности с помощью сертификата. Можно проверить журналы событий сервера политики сети для ошибок проверки подлинности. Дополнительные сведения см. в разделе [Установка и настройка сервера политики сети](vpn-deploy-nps.md)

8. Вы подключение, но не имеют доступа к сети Интернет/local? Проверьте пулов IP-адрес сервера DHCP или VPN для проблемы с конфигурацией.

9.  Такое подключение и иметь допустимый внутренний IP-адрес но не имеет доступа к локальным ресурсам?  Убедитесь, что клиенты знать, как получить доступ к этим ресурсам. Можно использовать VPN-сервера на запросы маршрута.


## Проблем с подключением Azure AD условного доступа

### Внесите - вам не удается получить образом еще

-   **Описание ошибки.** Когда политики условного доступа не выполняется, блокировать подключение VPN, но подключается после пользователь щелкает **X** , чтобы закрыть окно сообщения.  При нажатии кнопки **ОК** приводит к другой прохождение проверки подлинности, который заканчивается в другое _Oops_ сообщение. Эти события записываются в журнал событий рабочее AAD клиента. 

-   **Возможные причины.** 

    - Пользователь имеет действительный сертификат проверки подлинности клиента в своих личных сертификатов хранения, не выданный Azure AD.

    - VPN-профиль \ < TLSExtensions\ > раздел — это отсутствует или не не содержат **\ < EKUName\ > условного Access\ AAD < / EKUName\ > \ < EKUOID\ > 1.3.6.1.4.1.311.87 < / EKUOID\ > \ < EKUName > AAD условного доступа < / EKUName\ > \ < EKUOID\ > 1.3.6.1.4.1.311.87 < / EKUOID\ >** записей. \ < EKUName > и \ < EKUOID > записей сообщить VPN-клиент какие сертификат, чтобы получить из хранилища сертификатов пользователя при передаче сертификат на VPN-сервер. Без этого VPN-клиент использует любой действительный сертификат проверки подлинности клиента находится в хранилище сертификатов пользователя и успешной проверки подлинности. 

    - RADIUS-сервера (NPS) не был настроен на прием только сертификаты клиентов, которые содержат **Условного доступа в AAD** OID.

-   **Возможное решение.** Для выхода этого цикла, сделайте следующее:

    1. В Windows PowerShell выполните командлет **Get-WmiObject** создать дамп конфигурации профиля VPN. 
    2. Убедитесь, что **\ < TLSExtensions >**, **\ < EKUName >**, и **\ < EKUOID >** разделы существует и отображает его правильное имя и идентификатор Объекта. 
        ```
        PS C:\> Get-WmiObject -Class MDM_VPNv2_01 -Namespace root\cimv2\mdm\dmmap

        __GENUS                 : 2
        __CLASS                 : MDM_VPNv2_01
        __SUPERCLASS            :
        __DYNASTY               : MDM_VPNv2_01
        __RELPATH               : MDM_VPNv2_01.InstanceID="AlwaysOnVPN",ParentID="./Vendor/MSFT/VPNv2"
        __PROPERTY_COUNT        : 10
        __DERIVATION            : {}
        __SERVER                : DERS2
        __NAMESPACE             : root\cimv2\mdm\dmmap
        __PATH                  : \\DERS2\root\cimv2\mdm\dmmap:MDM_VPNv2_01.InstanceID="AlwaysOnVPN",ParentID="./Vendor/MSFT/VP
                                    Nv2"
        AlwaysOn                :
        ByPassForLocal          :
        DnsSuffix               :
        EdpModeId               :
        InstanceID              : AlwaysOnVPN
        LockDown                :
        ParentID                : ./Vendor/MSFT/VPNv2
        ProfileXML              : <VPNProfile><RememberCredentials>false</RememberCredentials><DeviceCompliance><Enabled>true</
                                    Enabled><Sso><Enabled>true</Enabled></Sso></DeviceCompliance><NativeProfile><Servers>derras2.
                                    corp.deverett.info;derras2.corp.deverett.info</Servers><RoutingPolicyType>ForceTunnel</Routin
                                    gPolicyType><NativeProtocolType>Ikev2</NativeProtocolType><Authentication><UserMethod>Eap</Us
                                    erMethod><MachineMethod>Eap</MachineMethod><Eap><Configuration><EapHostConfig
                                    xmlns="https://www.microsoft.com/provisioning/EapHostConfig"><EapMethod><Type
                                    xmlns="https://www.microsoft.com/provisioning/EapCommon">25</Type><VendorId
                                    xmlns="https://www.microsoft.com/provisioning/EapCommon">0</VendorId><VendorType
                                    xmlns="https://www.microsoft.com/provisioning/EapCommon">0</VendorType><AuthorId
                                    xmlns="https://www.microsoft.com/provisioning/EapCommon">0</AuthorId></EapMethod><Config
                                    xmlns="https://www.microsoft.com/provisioning/EapHostConfig"><Eap xmlns="https://www.microsoft.
                                    com/provisioning/BaseEapConnectionPropertiesV1"><Type>25</Type><EapType xmlns="https://www.mic
                                    rosoft.com/provisioning/MsPeapConnectionPropertiesV1"><ServerValidation><DisableUserPromptFor
                                    ServerValidation>true</DisableUserPromptForServerValidation><ServerNames></ServerNames></Serv
                                    erValidation><FastReconnect>true</FastReconnect><InnerEapOptional>false</InnerEapOptional><Ea
                                    p xmlns="https://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"><Type>13</Type>
                                    <EapType xmlns="https://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1"><Credenti
                                    alsSource><CertificateStore><SimpleCertSelection>true</SimpleCertSelection></CertificateStore
                                    ></CredentialsSource><ServerValidation><DisableUserPromptForServerValidation>true</DisableUse
                                    rPromptForServerValidation><ServerNames></ServerNames><TrustedRootCA>5a 89 fe cb 5b 49 a7 0b
                                    1a 52 63 b7 35 ee d7 1c c2 68 be 4b </TrustedRootCA></ServerValidation><DifferentUsername>fal
                                    se</DifferentUsername><PerformServerValidation xmlns="https://www.microsoft.com/provisioning/E
                                    apTlsConnectionPropertiesV2">true</PerformServerValidation><AcceptServerName xmlns="https://ww
                                    w.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName><TLSExtens
                                    ions
                                    xmlns="https://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"><FilteringInfo xml
                                    ns="https://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3"><EKUMapping><EKUMap><
                                    EKUName>AAD Conditional
                                    Access</EKUName><EKUOID>1.3.6.1.4.1.311.87</EKUOID></EKUMap></EKUMapping><ClientAuthEKUList
                                    Enabled="true"><EKUMapInList><EKUName>AAD Conditional Access</EKUName></EKUMapInList></Client
                                    AuthEKUList></FilteringInfo></TLSExtensions></EapType></Eap><EnableQuarantineChecks>false</En
                                    ableQuarantineChecks><RequireCryptoBinding>false</RequireCryptoBinding><PeapExtensions><Perfo
                                    rmServerValidation xmlns="https://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2"
                                    >false</PerformServerValidation><AcceptServerName xmlns="https://www.microsoft.com/provisionin
                                    g/MsPeapConnectionPropertiesV2">false</AcceptServerName></PeapExtensions></EapType></Eap></Co
                                    nfig></EapHostConfig></Configuration></Eap></Authentication></NativeProfile></VPNProfile>
        RememberCredentials     : False
        TrustedNetworkDetection :
        PSComputerName          : DERS2
        ```

    3. Чтобы определить, ли действительных сертификатов в хранилище сертификатов пользователя, выполните команду **Certutil** :

       ```
       C:\>certutil -store -user My

        My "Personal"
        ================ Certificate 0 ================
        Serial Number: 32000000265259d0069fa6f205000000000026
        Issuer: CN=corp-DEDC0-CA, DC=corp, DC=deverett, DC=info
         NotBefore: 12/8/2017 8:07 PM
         NotAfter: 12/8/2018 8:07 PM
        Subject: E=winfed@deverett.info, CN=WinFed, OU=Users, OU=Corp, DC=corp, DC=deverett, DC=info
        Certificate Template Name (Certificate Type): User
        Non-root Certificate
        Template: User
        Cert Hash(sha1): a50337ab015d5612b7dc4c1e759d201e74cc2a93
          Key Container = a890fd7fbbfc072f8fe045e680c501cf_5834bfa9-1c4a-44a8-a128-c2267f712336
          Simple container name: te-User-c7bcc4bd-0498-4411-af44-da2257f54387
          Provider = Microsoft Enhanced Cryptographic Provider v1.0
        Encryption test passed
        
        ================ Certificate 1 ================
        Serial Number: 367fbdd7e6e4103dec9b91f93959ac56
        Issuer: CN=Microsoft VPN root CA gen 1
         NotBefore: 12/8/2017 6:24 PM
         NotAfter: 12/8/2017 7:29 PM
        Subject: CN=WinFed@deverett.info
        Non-root Certificate
        Cert Hash(sha1): 37378a1b06dcef1b4d4753f7d21e4f20b18fbfec
          Key Container = 31685cae-af6f-48fb-ac37-845c69b4c097
          Unique container name: bf4097e20d4480b8d6ebc139c9360f02_5834bfa9-1c4a-44a8-a128-c2267f712336
          Provider = Microsoft Software Key Storage Provider
        Private key is NOT exportable
        Encryption test passed
       ```
       >[!NOTE]
       >Если сертификат от поставщика **CN = корневого центра сертификации Майкрософт VPN поколения 1** присутствует в личное хранилище пользователя, но пользователь, получивший доступ, щелкнув **X** , чтобы закрыть окно сообщения Oops, собирать журналы событий CAPI2 для проверки было сертификат, используемый для проверки подлинности действительный сертификат проверки подлинности клиента, не был выпущен из корневого центра сертификации Майкрософт VPN.

   4. Если действительный сертификат проверки подлинности клиента существует в личном хранилище пользователя, установить подключение не удастся (как надо) после нажатия пользователем **X** и, если **\ < TLSExtensions >**, **\ < EKUName >**, и **\ < EKUOID >** разделы существуют и содержат правильные значения.<p>_Не удалось найти сертификат, можно использовать с расширяемый протокол проверки подлинности._ Появится сообщение об ошибке.

### Не удалось удалить сертификат из колонке подключения VPN

-   **Описание ошибки.** Невозможно удалить сертификаты в колонке подключения к VPN.

-   **Возможные причины.** Сертификат задается в **основной**.

-   **Возможное решение.** 

    1. В колонке подключения VPN выберите сертификат.
    2. В разделе **основной**выберите " **Нет** " и нажмите кнопку **Сохранить**.
    3. В колонке подключения VPN выберите сертификат еще раз.
    4. Нажмите кнопку **Удалить**.


---
