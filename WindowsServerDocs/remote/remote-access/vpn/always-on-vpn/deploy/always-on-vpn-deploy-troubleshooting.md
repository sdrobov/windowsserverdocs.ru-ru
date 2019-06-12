---
title: Устранение неполадок постоянно подключенного VPN-профиля
description: Этот раздел содержит инструкции для проверки и устранение неполадок при развертывании AlwaysOn VPN в Windows Server 2016.
ms.prod: windows-server-threshold
ms.technology: networking-ras
ms.topic: article
ms.assetid: 4d08164e-3cc8-44e5-a319-9671e1ac294a
ms.localizationpriority: medium
ms.date: 06/11/2018
ms.author: pashort
author: shortpatti
ms.openlocfilehash: d9e0efede39f5a8189dbb3d62033210c393c424d
ms.sourcegitcommit: 0948a1abff1c1be506216eeb51ffc6f752a9fe7e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66749649"
---
# <a name="troubleshoot-always-on-vpn"></a>Устранение неполадок постоянно подключенного VPN-профиля 

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows 10

Если произошел сбой установки AlwaysOn VPN для подключения клиентов к внутренней сети, причиной является скорее всего, недопустимый сертификат VPN, неверные политики NPS или проблемы с помощью скриптов развертывания клиента или службы маршрутизации и удаленного доступа. Первым шагом устранения неполадок и тестирования VPN-подключение является понимание того, основные компоненты инфраструктуры AlwaysOn VPN. 

Устранения неполадок подключения несколькими способами. Для проблем на стороне клиента и устранения общих неполадок журналы приложений на клиентских компьютерах являются очень полезными. Для проблемы проверки подлинности журнала NPS на сервере политики сети может помочь определить источник проблемы.

## <a name="error-codes"></a>Коды ошибок

### <a name="error-code-800"></a>Код ошибки: 800

- **Описание ошибки.** Удаленное подключение не находится в из-за сбоя попытки VPN-туннели. VPN-сервер может быть недоступен. Если это подключение пытается использовать туннель L2TP/IPsec, параметры безопасности, необходимые для IPsec, согласование не настроен должным образом.

- **Возможная причина.** Эта ошибка возникает, если выбран тип туннеля VPN **автоматического** и попытка подключения завершается ошибкой для всех VPN-туннелей.

- **Возможные решения:**

    - Если вы знаете туннель, который будет использоваться для вашего развертывания, присвоения значения тип VPN туннель определенного типа на стороне клиента VPN.

    - За счет подключения VPN с типом конкретного туннель, подключение по-прежнему завершится ошибкой, но это приведет к более туннель ошибки (например, «GRE заблокирован на PPTP»).

    - Эта ошибка также возникает при VPN-сервер недоступен, или происходит сбой подключения через туннель.

- **Удостоверься:**

    - IKE-порты (порты UDP 500 и 4500) не блокируются.

    - Правильные сертификаты для IKE присутствуют на клиенте и сервере.

### <a name="error-code-809"></a>Код ошибки: 809

- **Описание ошибки.**  Не удалось установить сетевое подключение между вашим компьютером и VPN-сервера, так как удаленный сервер не отвечает. Возможно, один из сетевых устройств (например, брандмауэры, NAT, маршрутизаторы) между вашим компьютером и удаленный сервер не настроен для подключений VPN. Обратитесь к администратору или поставщиком услуг, чтобы определить, какие устройства могут быть причиной проблемы.

- **Возможная причина.** Эта ошибка вызвана заблокированных UDP 500 и 4500 порты на VPN-сервер или брандмауэр.

- **Возможное решение.** Убедитесь, что порты UDP 500 и 4500 разрешены через все брандмауэры между клиентом и RRAS-сервере.

### <a name="error-code-812"></a>Код ошибки: 812

- **Описание ошибки.** Не удается подключиться к AlwaysOn VPN. Подключение не выполнено из-за политики, настроенный на сервере удаленного доступа или VPN. В частности метод проверки подлинности сервера, используемый для проверки имени пользователя и пароля может не соответствовать метод проверки подлинности, настроены в вашем профиле подключения. Обратитесь к администратору сервера удаленного доступа и уведомить его этой ошибки.

- **Возможные причины:**

    - Эта ошибка может быть вызвано том, что сервер NPS указал условие проверки подлинности, который клиент не отвечает. Например сервер политики сети может задать использование сертификата для обеспечения безопасного подключения PEAP, но клиент пытается использовать EAP-MSCHAPv2.

    - Журнал событий 20276 регистрируется в средство просмотра событий, когда параметр протокола проверки подлинности VPN на основе RRAS сервера отлична от компьютера VPN-клиента.

- **Возможное решение.** Убедитесь, что конфигурацию клиента соответствует условиям, заданные на сервере политики сети.

### <a name="error-code-13806"></a>Код ошибки: 13806

- **Описание ошибки.** Не удалось найти сертификат компьютера IKE. Обратитесь к администратору безопасности сети, об установке действительный сертификат в соответствующее хранилище сертификатов.

- **Возможная причина.** Эта ошибка обычно возникает, когда нет сертификата компьютера или корневой сертификат компьютера присутствует на сервере VPN.

- **Возможное решение.** Убедитесь в том, что на клиентском компьютере и VPN-сервер установлены сертификаты, описанные в этом развертывании.

### <a name="error-code-13801"></a>Код ошибки: 13801

- **Описание ошибки.** Неприемлемые учетные данные проверки подлинности IKE.

- **Возможные причины.** Эта ошибка обычно возникает в одном из следующих случаев:

    - Сертификат компьютера, используемый для проверки IKEv2 на сервере удаленного доступа не имеет **аутентификация** под **расширенное использование ключа**.

    - Истек срок действия сертификата компьютера на сервере удаленного доступа.

    - Корневой сертификат, чтобы проверить сертификат сервера удаленного доступа отсутствует на клиентском компьютере.

    - Имя сервера VPN, используемое на клиентском компьютере не соответствует **subjectName** сертификата сервера.

- **Возможное решение.** Убедитесь, что сертификат сервера содержит **аутентификация** под **расширенное использование ключа**. Убедитесь, что сертификат сервера по-прежнему действителен. Убедитесь, что ЦС, который используется в разделе **доверенные корневые центры сертификации** на RRAS-сервере. Убедитесь, что VPN-клиент подключается, используя полное ДОМЕННОЕ имя VPN-сервера, представленный на сертификат VPN-сервера.

### <a name="error-code-0x80070040"></a>Код ошибки: 0x80070040

- **Описание ошибки.** Сертификат сервера не поддерживает **аутентификация** как одну из записей об использовании его сертификата.

- **Возможная причина.** Эта ошибка может возникать, если ни один сертификат проверки подлинности сервера устанавливается на сервере удаленного доступа.

- **Возможное решение.** Убедитесь, что сертификат компьютера RAS-сервер использует для **IKEv2** имеет **аутентификация** как одну из записей об использовании сертификата.

### <a name="error-code-0x800b0109"></a>Код ошибки: 0x800B0109

Как правило VPN клиентский компьютер присоединен к домену на основе Active Directory. Если вы используете учетные данные домена для входа на VPN-сервер, сертификат автоматически устанавливается в доверенных корневых центров сертификации хранения. Тем не менее если компьютер не присоединен к домену или если вы используете в цепочке альтернативный сертификат, эта проблема может возникнуть.

- **Описание ошибки.** Цепочка сертификатов обработана, но обработка прервана на корневом сертификате, который не доверяет поставщик доверия.

- **Возможная причина.** Эта ошибка может возникать, если соответствующий сертификат доверенного корневого ЦС не установлен в доверенные корневые центры сертификации хранить на клиентском компьютере.

- **Возможное решение.** Убедитесь, что корневой сертификат установлен на клиентском компьютере в хранилище доверенных корневых центров сертификации.

## <a name="logs"></a>Журналы

### <a name="application-logs"></a>Журналы приложений

Журналы приложений на клиентских компьютерах записать большинство различными аспектами более высокого уровня события подключения VPN.

Проверьте наличие событий из источника RasClient. Все сообщения об ошибках возвращают код ошибки в конце сообщения. Ниже приведены некоторые из наиболее распространенных кодов ошибок, но полный список можно найти в [маршрутизации и удаленного доступа коды](https://msdn.microsoft.com/library/windows/desktop/bb530704.aspx).

## <a name="nps-logs"></a>Журналы сервера политики сети

NPS создает и сохраняет журналы учета NPS. По умолчанию они хранятся в папке % SYSTEMROOT %\\System32\\Logfiles\\ в файл с именем в*XXXX*.txt, где *XXXX* — это дата создания файла.

По умолчанию в этих журналах используется формат значений с разделителями запятыми, но они не включают строку заголовка. Является строкой заголовка:

```
ComputerName,ServiceName,Record-Date,Record-Time,Packet-Type,User-Name,Fully-Qualified-Distinguished-Name,Called-Station-ID,Calling-Station-ID,Callback-Number,Framed-IP-Address,NAS-Identifier,NAS-IP-Address,NAS-Port,Client-Vendor,Client-IP-Address,Client-Friendly-Name,Event-Timestamp,Port-Limit,NAS-Port-Type,Connect-Info,Framed-Protocol,Service-Type,Authentication-Type,Policy-Name,Reason-Code,Class,Session-Timeout,Idle-Timeout,Termination-Action,EAP-Friendly-Name,Acct-Status-Type,Acct-Delay-Time,Acct-Input-Octets,Acct-Output-Octets,Acct-Session-Id,Acct-Authentic,Acct-Session-Time,Acct-Input-Packets,Acct-Output-Packets,Acct-Terminate-Cause,Acct-Multi-Ssn-ID,Acct-Link-Count,Acct-Interim-Interval,Tunnel-Type,Tunnel-Medium-Type,Tunnel-Client-Endpt,Tunnel-Server-Endpt,Acct-Tunnel-Conn,Tunnel-Pvt-Group-ID,Tunnel-Assignment-ID,Tunnel-Preference,MS-Acct-Auth-Type,MS-Acct-EAP-Type,MS-RAS-Version,MS-RAS-Vendor,MS-CHAP-Error,MS-CHAP-Domain,MS-MPPE-Encryption-Types,MS-MPPE-Encryption-Policy,Proxy-Policy-Name,Provider-Type,Provider-Name,Remote-Server-Address,MS-RAS-Client-Name,MS-RAS-Client-Version
```

При вставке этой строки заголовков в первой строке файла журнала, затем импортируйте файл в Microsoft Excel, столбцы будет называться должным образом.

Журналы сервера политики сети может быть полезно при диагностике проблем, связанных с политикой. Дополнительные сведения о журналах NPS см. в разделе [интерпретировать NPS базы данных файлы журнала в формате](https://technet.microsoft.com/library/cc771748.aspx).

## <a name="vpnprofileps1-script-issues"></a>Проблемы VPN_Profile.ps1 сценария

Наиболее распространенных проблем при ручного выполнения сценария VPN_ Profile.ps1 включают:

- Вы используете средства удаленного подключения?  Убедитесь в том, что не следует использовать RDP или другой способ удаленного подключения, как он трогает обнаружения имени входа пользователя.

- Является администратором этой локальной машине пользователя?  Убедитесь, что при выполнении сценария VPN_Profile.ps1, у пользователя есть права администратора.

- У вас есть включены дополнительные возможности безопасности PowerShell? Убедитесь, что политика выполнения PowerShell не блокирует скрипт. Может потребоваться, если выключить режим ограниченного языка, если параметр включен, перед выполнением скрипта. После успешного выполнения сценария, вы можете активировать режим ограниченного языка.

## <a name="always-on-vpn-client-connection-issues"></a>Проблемы с подключением клиента AlwaysOn VPN

Небольшой неправильной конфигурации может вызвать сбой подключения клиента и может оказаться сложной задачей для поиска причины.  Всегда на VPN-клиент проходит через несколько шагов перед установкой соединения. При устранении неполадок подключения клиента, пройти через процесс исключения со следующими:

1. Подключен ли компьютер шаблона извне? Объект **whatismyip** сканирование должно отображаться общедоступный IP-адрес, который не принадлежит вам.

2. Может разрешить имя удаленного доступа или VPN-сервера в IP-адрес. В **панели управления** > **сети** и **Internet** > **сетевых подключений**, откройте окно свойств для профиля VPN. Значение в **Общие** разрешимые через DNS должна быть вкладка.

3. Получить доступ к VPN-серверу из внешней сети? Рассмотрите возможность открытия сообщений протокола ICMP (Internet Control) внешнего интерфейса и проверив связь с именем из удаленного клиента. Можно удалить после успешной проверки связи ICMP разрешающее правило.

4. У вас есть внутренние и внешние сетевые адаптеры на VPN-сервер настроен правильно? Они в разных подсетях? Внешней сетевой платы, подключиться к требуемому интерфейсу в брандмауэре?

5. Открыты UDP 500 и 4500 порты от клиента для внешнего интерфейса VPN-сервера? Проверьте клиентский брандмауэр, брандмауэра для сервера и все брандмауэры оборудования. IPSEC использует UDP порт 500, поэтому создание Конечно, у вас нет IPEC отключена или заблокирована в любом месте.

6. Происходит сбой проверки сертификата? Убедитесь, что на NPS-сервер имеет сертификат проверки подлинности сервера, который может обслуживать запросы IKE. Убедитесь, что у вас есть правильный VPN IP-адрес сервера указан в качестве клиента NPS. Убедитесь, что вы выполняете проверку подлинности PEAP, и свойства защищенного EAP разрешать следует только проверки подлинности с помощью сертификата. Можно проверить журналы событий сервера политики сети для ошибок проверки подлинности. Дополнительные сведения см. в разделе [Установка и настройка сервера политики сети](vpn-deploy-nps.md)

7. Вы подключение, но не имеют доступа Интернета или локальной сети? Проверьте пулов IP-адрес сервера DHCP и VPN для проблемы с конфигурацией.

8. Такое подключение и допустимым внутренний IP-адрес но нет доступа к локальным ресурсам?  Убедитесь, что клиенты знаете, как получить доступ к этим ресурсам. Можно использовать VPN-сервер для перенаправления запросов.

## <a name="azure-ad-conditional-access-connection-issues"></a>Проблемы подключения Azure AD условного доступа

### <a name="oops---you-cant-get-to-this-yet"></a>Ой получить не удается это еще

- **Описание ошибки.** Если не удовлетворены, блокирует ли подключение VPN, политики условного доступа, но подключается после того как пользователь выберет **X** чтобы закрыть сообщение.  Выбрав **ОК** приводит к еще одна попытка проверки подлинности, который заканчивается на другое сообщение «Ошибка». Эти события записываются в журнал рабочих событий AAD клиента.

- **Возможная причина**

  - Пользователь имеет допустимый сертификат проверки подлинности клиента в своих личных сертификатов хранения, который не был выдан Azure AD.

  - Профиль VPN \<TLSExtensions\> раздел является отсутствует или не содержит **\<EKUName\>условного доступа AAD\</EKUName\> \< EKUOID\>1.3.6.1.4.1.311.87 < / EKUOID\>\<EKUName > AAD условного доступа < / EKUName\>\<EKUOID\>1.3.6.1.4.1.311.87 < / EKUOID\>** записей. \<EKUName > и \<EKUOID > записи сообщить VPN-клиента, какой сертификат необходимо получить из хранилища сертификатов пользователя, при передаче сертификат на VPN-сервере. Без этого VPN-клиент использует любой действительный сертификат проверки подлинности клиента находится в хранилище сертификатов пользователя и проверка подлинности завершается успешно. 

  - Сервер RADIUS (NPS) не настроен на прием сертификатов клиентов, которые содержат только **условного доступа AAD** OID.

- **Возможное решение.** Чтобы избежать этого цикла, сделайте следующее:

  1. В Windows PowerShell выполните **Get-WmiObject** командлет для помещения в дамп конфигурации профиля VPN. 
  2. Убедитесь, что  **\<TLSExtensions >** ,  **\<EKUName >** , и  **\<EKUOID >** разделы существуют и демонстрирует правильный имя и идентификатор Объекта.
      
      ```powershell
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

  3. Чтобы определить, существуют допустимые сертификаты в хранилище сертификатов пользователя, выполните **Certutil** команды:

     ```powershell
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
     >Если сертификат издателя **CN = корневой ЦС Microsoft VPN, gen 1** присутствует в личное хранилище пользователя, но пользователь, получивший доступ, выбрав **X** чтобы закрыть сообщение ой, сбор журналов событий CAPI2 для проверки сертификат, используемый для проверки подлинности был действительный сертификат проверки подлинности клиента, который не был выдан из корневого ЦС Майкрософт VPN.

  4. Если действительный сертификат проверки подлинности клиента в личное хранилище пользователя, подключение отсутствует (так же как и его), после того как пользователь выберет **X** и если  **\<TLSExtensions >** ,  **\<EKUName >** , и  **\<EKUOID >** разделы существуют и содержать некорректные сведения.
   
     Появится сообщение об ошибке с текстом «сертификат не найден, который может использоваться с помощью расширяемого протокола проверки подлинности».

### <a name="unable-to-delete-the-certificate-from-the-vpn-connectivity-blade"></a>Не удалось удалить сертификат из колонки подключения VPN

- **Описание ошибки.** Невозможно удалить сертификаты в колонке подключения VPN.

- **Возможная причина.** Сертификат имеет значение **основной**.

- **Возможное решение.**

    1. В колонке подключения VPN выберите сертификат.
    2. В разделе **основной**выберите **нет**, а затем выберите **Сохранить**.
    3. В колонке подключения VPN выберите сертификат, еще раз.
    4. Выберите **удалить**.
