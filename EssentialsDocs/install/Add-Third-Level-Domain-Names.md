---
title: "Добавление имен доменов третьего уровня"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5b4a362-1881-4024-ae4e-cc3b05e50103
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 64bf24e45155fdd981e2061b3de7ebce1c53b36c
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="add-third-level-domain-names"></a>Добавление имен доменов третьего уровня

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Вы можете добавить возможность пользователям возможность запрашивать имена доменов третьего уровня в мастера настройки доменного имени. Для этого необходимо создать и установить сборку кода, которая используется диспетчером доменов в операционной системе.  
  
## <a name="create-a-provider-of-third-level-domain-names"></a>Создание поставщика имена доменов третьего уровня  
 Можно сделать доступными имена доменов третьего уровня необходимо создать и установить сборку кода, которая предоставляет мастеру имена доменов. Для этого необходимо выполнить следующие задачи:  
  
-   [Добавьте реализацию интерфейса IDomainSignupProvider сборки](Add-Third-Level-Domain-Names.md#BKMK_DomainSignup)  
  
-   [Добавьте реализацию интерфейса IDomainMaintenanceProvider сборки](Add-Third-Level-Domain-Names.md#BKMK_DomainMaintenance)  
  
-   [Подпишите сборку подпись Authenticode](Add-Third-Level-Domain-Names.md#BKMK_SignAssembly)  
  
-   [Установить сборку на компьютере-образце](Add-Third-Level-Domain-Names.md#BKMK_InstallAssembly)  
  
-   [Перезапустите службу управление доменными именами Windows Server](Add-Third-Level-Domain-Names.md#BKMK_RestartService)  
  
###  <a name="BKMK_DomainSignup"></a>Добавьте реализацию интерфейса IDomainSignupProvider сборки  
 Интерфейс IDomainSignupProvider используется для добавления предложений домена мастер.  
  
##### <a name="to-add-the-idomainsignupprovider-code-to-the-assembly"></a>Добавление кода IDomainSignupProvider сборки  
  
1.  Откройте Visual Studio 2008 с правами администратора, щелкните правой кнопкой мыши программы в **запустить** меню и выбрав **Запуск от имени администратора**.  
  
2.  Нажмите кнопку **файл**, нажмите кнопку **New**, а затем нажмите кнопку **проекта**.  
  
3.  В **новый проект** диалоговом нажмите кнопку **Visual C#**, нажмите кнопку **библиотека классов**, введите имя для решения и нажмите кнопку **ОК**.  
  
4.  Переименуйте файл Class1.cs. Например MyDomainNameProvider.cs  
  
5.  Добавьте ссылки на файлы Wssg.Web.DomainManagerObjectModel.dll, CertManaged.dll, WssgCertMgmt.dll и WssgCommon.dll.  
  
6.  Добавьте следующие операторы using.  
  
    ```c#  
  
    using System.Collections.ObjectModel;  
    using System.Net;  
    using System.Net.Sockets;  
    using Microsoft.WindowsServerSolutions.Certificates;  
    using Microsoft.WindowsServerSolutions.CertificateManagement;  
    using Microsoft.WindowsServerSolutions.Common;  
    using Microsoft.Win32;  
    ```  
  
7.  Измените пространство имен и класс заголовок, чтобы следующим образом.  
  
    ```c#  
    namespace Microsoft.WindowsServerSolutions.RemoteAccess.Domains  
    {  
        public class MyDomainNameProvider : IDomainSignupProvider  
        {  
        }  
    }  
    ```  
  
8.  Добавьте метод Initialize и необходимые переменные на уровне класса, который определяет предложения, которые представлены в мастере.  
  
    > [!NOTE]
    >  Метод Initialize определяет идентификатор для поставщика домена, которое должно быть уникальным. Типичный способ сделать это является определение как идентификатор GUID. Дополнительные сведения о создании GUID см. в разделе [(guidgen.exe) создать Guid](https://go.microsoft.com/fwlink/?LinkId=116098).  
  
     В следующем примере показан метод Initialize.  
  
    ```c#  
  
    static readonly Guid MyID = new Guid("8C999DF5-696A-47af-822D-94F1673D3397");  
    public Guid ID { get { return MyID; } }  
    public string Name { get { return "My Provider"; } }  
    List<Offering> offerings = new List<Offering>();  
  
    public void Initialize(DomainProviderSettings config)  
    {  
       var offer1 = new Offering()  
       {  
          Description = "My Domain Provider",  
          Name = "Offering 1",  
          ProviderID = ID,  
          MoreInfoUrl = new Uri("http://www.contoso.com"),  
          MembershipServiceName = "My Membership",  
          EulaUrl = new Uri("http://www.contoso.com"),  
       };  
  
       this.offerings.Add(offer1);  
       RegistryKey key =   
          Registry.LocalMachine.CreateSubKey(@"Software\Microsoft\Windows Server\Domain Manager\Settings");  
       key.Close();  
    }  
    ```  
  
9. Добавьте метод GetOfferings, который возвращает список предложений, инициализированных на предыдущем шаге. В следующем примере показан метод GetOfferings.  
  
    ```c#  
  
    public ReadOnlyCollection<Offering> GetOfferings()  
    {  
       return this.offerings.AsReadOnly();  
    }  
    ```  
  
10. Добавьте метод FindOfferingForDomain, который возвращает предложения из списка. В следующем примере показан метод FindOfferingForDomain.  
  
    ```  
  
    public Offering FindOfferingForDomain(string domain)  
    {  
       // Return the offering that has the domain name.  
       return offerings[0];  
    }  
  
    ```  
  
11. Добавьте метод SetCredentials, который определяет учетные данные, которые требуются для доступа к предложений. В следующем примере показан метод SetCredentials.  
  
    ```c#  
  
    private string currentUser { get; set; }  
    private string currentPassword { get; set; }  
  
    public bool SetCredentials(DomainNameRequest request,   
       DomainProviderCredentials credentials, bool validate)  
    {  
       currentUser = credentials.UserName;  
       currentPassword = credentials.Password;  
       if (validate)  
       {  
          return ValidateCredentials();  
       }  
  
       return true;  
    }  
    ```  
  
12. Добавьте метод ValidateCredentials, которая проверяет учетные данные, определяемые SetCredentials. В следующем примере показан метод ValidateCredentials.  
  
    ```c#  
  
    public static readonly string offerUser = "user1@contoso.com";  
    public static readonly string offerPassword = "password1";  
  
    public bool ValidateCredentials()  
    {  
       if (IsUser())  
          return string.Equals(currentPassword, offerPassword);  
       else  
          return false;  
    }   
  
    private bool IsUser()  
    {  
       return string.Equals(currentUser, offerUser, StringComparison.OrdinalIgnoreCase);  
    }  
    ```  
  
13. Добавьте метод GetAvailableDomainRoots, который возвращает список имен корневого домена, поддерживаемые предложения, указанный в запросе. Этот список имен корневого домена, не должно быть пустым. В следующем примере показан метод GetAvailableDomainRoots.  
  
    ```c#  
  
    public ReadOnlyCollection<string> GetAvailableDomainRoots(DomainNameRequest request)  
    {  
       List<string> list = new List<string>();  
       list.Add("domain1.com");  
       list.Add("domain1.org");  
  
       return list.AsReadOnly();  
    }  
    ```  
  
14. Добавьте метод GetUserDomainNames, который возвращает список доменных имен, текущий пользователь купил, относительно текущее предложение. Этот список может быть пустым. В следующем примере показан метод GetUserDomainNames.  
  
    ```c#  
  
    public static readonly string AvailableDomain1 = "available.domain1.com",  
       AvailableDomain2 = "available.domain2.com";  
    public static readonly string OccupiedDomain1 = "occupied.domain1.com",  
       OccupiedDomain2 = "occupied.domain2.com";  
  
    public ReadOnlyCollection<string> GetUserDomainNames(DomainNameRequest request)  
    {  
       var userDomains = new List<string>();  
       userDomains.Add(OccupiedDomain1);  
       userDomains.Add(AvailableDomain1);  
  
       return userDomains.AsReadOnly();  
    }  
    ```  
  
15. Добавьте метод GetUserDomainQuota, который возвращает максимальное количество доменов, которые позволяет указанного предложения. Если более не применимо, этот метод должен возвращать 0. В следующем примере показан метод GetUserDomainQuota.  
  
    ```c#  
  
    public int GetUserDomainQuota(DomainNameRequest request)  
    {  
       return 0;  
    }  
    ```  
  
16. Добавьте метод CheckDomainAvailability, который проверяет наличие имени запрошенного домена и может возвращать список вариантов. В следующем примере показан метод CheckDomainAvailability.  
  
    ```c#  
  
    public bool CheckDomainAvailability(DomainNameRequest request,   
       out ReadOnlyCollection<string> suggestions)  
    {  
       suggestions = null;  
  
       return true;  
    }  
    ```  
  
17. Добавьте метод CommitDomain, который вносит запрошенного доменного имени. Успешное завершение этого метода означает, что имя домена, связанного с учетной записью пользователя, поставщик обслуживания будет вызван немедленно, чтобы получить сертификат, если состояние является полностью работоспособным и поставщика и предложения становятся активными. В следующем примере показан метод CommitDomain.  
  
    ```c#  
  
    public DomainStatus CommitDomain(DomainNameRequest request)  
    {              
       ReadOnlyCollection<string> suggestions;  
       if (!CheckDomainAvailability(request, out suggestions))  
       {  
          throw new DomainException(FailureReason.InvalidDomainName, null, null);  
       }  
  
       return DomainStatus.Ready;  
    }  
    ```  
  
18. Добавьте метод ReleaseDomain, который сообщает, пользователю необходимо освободить доменное имя поставщика. В следующем примере показан метод ReleaseDomain.  
  
    ```c#  
  
    public bool ReleaseDomain(DomainNameRequest request)  
    {  
       return true;  
    }  
    ```  
  
19. Добавьте метод GetProviderLandingUrl, который возвращает URL-адрес для целевой страницы в рабочем процессе регистрации домена. В следующем примере показан метод GetProviderLandingUrl.  
  
    ```c#  
  
    public Url GetProviderLandingUrl(DomainNameRequest request)  
    {  
       return new Url("www.contoso.com");  
    }  
    ```  
  
20. Добавьте метод GetDomainMaintenanceProvider, который возвращает экземпляр IDomainMaintenanceProvider, который используется для выполнения задач обслуживания домена. Этот метод вызывается после успешного метод CommitDomain и при запуске диспетчера домена. В следующем примере показан метод GetDomainMaintenanceProvider.  
  
    ```c#  
  
    public IDomainMaintenanceProvider GetDomainMaintenanceProvider()  
    {  
       return new MyDomainMaintenanceProvider();  
    }  
    ```  
  
21. Сохраните проект, но не закрывайте его так, как вы добавите к нему с помощью следующей процедуры. Вы не сможете до завершения этой процедуры построение проекта.  
  
###  <a name="BKMK_DomainMaintenance"></a>Добавьте реализацию интерфейса IDomainMaintenanceProvider сборки  
 IDomainMaintenanceProvider используется для поддержания домена после его создания.  
  
##### <a name="to-add-the-idomainmaintenanceprovider-code-to-the-assembly"></a>Добавление кода IDomainMaintenanceProvider сборки  
  
1.  Добавьте заголовок класса поставщика обслуживания домена. Убедитесь, что имя, задаваемое для поставщика совпадает с именем в методе GetDomainMaintenanceProvider, которую вы указали ранее.  
  
    ```c#  
  
    public class MyDomainMaintenanceProvider : IDomainMaintenanceProvider  
    {  
    }  
    ```  
  
2.  Добавьте метод Activate, который задает активного поставщика. В следующем примере показан метод активации.  
  
    ```c#  
  
    string DomainName { get; set; }  
    protected DomainProviderSettings Settings { get; set; }  
  
    public void Activate(DomainProviderSettings settings,   
       DomainNameConfiguration config, DomainProviderCredentials credentials)  
    {  
       Settings = settings;  
       SetCredentials(credentials);  
       DomainName = config.AutoConfiguredAnywhereAccessFullName.Punycode;  
    }  
    ```  
  
3.  Добавьте метод деактивировать, который используется для отключения всех действий. В следующем примере показан метод деактивировать.  
  
    ```  
  
    public void Deactivate()  
    {  
       //Deactivate all actions  
    }  
  
    ```  
  
4.  Добавьте метод SetCredentials, который обновляет учетные данные пользователя. Например этот метод может вызывать обновить учетные данные, которые больше не являются допустимыми. В следующем примере показан метод SetCredentials.  
  
    ```c#  
  
    protected DomainProviderCredentials Credentials { get; set; }  
  
    public bool SetCredentials(DomainProviderCredentials credentials)  
    {  
       this.Credentials = credentials;  
  
       return true;  
    }  
    ```  
  
5.  Добавьте метод ValidateCredentials, которая проверяет указанные учетные данные. В следующем примере показан метод ValidateCredentials.  
  
    ```c#  
  
    public static readonly string offerUser = "user1@contoso.com";  
    public static readonly string offerPassword = "password1";  
  
    public bool ValidateCredentials()  
    {  
       if (string.Equals(this.Credentials.UserName,   
          offerUser,   
          StringComparison.OrdinalIgnoreCase) &&   
             string.Equals(this.Credentials.Password, offerPassword))  
          return true;  
  
       return false;  
    }  
    ```  
  
6.  Добавьте метод GetPublicAddress, который возвращает внешний IP-адрес сервера. В следующем примере показан метод GetPublicAddress.  
  
    ```c#  
  
    public IPAddress GetPublicIPAddress()  
    {  
       string PublicIP = "0.0.0.0";  
       using (RegistryKey key = ProductInfo.RegKey.OpenSubKey("Domain Manager\\Settings", true))  
       {  
          PublicIP = (key == null) ? "0.0.0.0" : key.GetValue("PublicIP", "0.0.0.0").ToString();  
       }  
       IPAddress ip = IPAddress.Parse(PublicIP);  
  
       if (PublicIP == "0.0.0.0")  
       {  
          string strHostName = Dns.GetHostName();  
          IPHostEntry ipEntry = Dns.GetHostEntry(strHostName);  
  
          IPAddress[] addr = ipEntry.AddressList;  
          foreach (IPAddress add in addr)  
          {  
             if (add.AddressFamily == AddressFamily.InterNetwork)  
             {  
                return add;  
             }  
          }  
       }  
       else  
       {  
          return IPAddress.Parse(PublicIP);  
       }  
  
       return null;    
    }  
    ```  
  
7.  Добавьте метод SubmitCertificateRequest, который отправляет запрос на сертификат для имени домена в текущий момент.  
  
    ```c#  
  
    string cert=null;  
  
    public void SubmitCertificateRequest(string certificateRequest)  
    {  
       cert = CertManaged.SubmitRequest(certificateRequest, CertCommon.CAServerFQDN + "\\" +      
          CertCommon.CAName,   
          Microsoft.WindowsServerSolutions.CertificateManagement.CRFlags.Base64Header,   
          CertCommon.CATemplate,   
          EncodingFlags.Base64);  
    }  
    ```  
  
8.  Добавьте метод GetCertificateResponse, который возвращает ответ сертификата, если домен имеет состояние полностью работоспособным. Этот метод вызывается для обоих новые запросы на сертификаты и запросы на обновление сертификата. В следующем примере показан метод GetCertificateResponse.  
  
    ```c#  
  
    public string GetCertificateResponse(bool renew)  
    {  
       return cert;  
    }  
    ```  
  
9. Добавьте метод SubmitRenewCertificateRequest, который обрабатывает продления сертификата. В следующем примере показан метод SubmitRenewCertificateRequest.  
  
    ```c#  
  
    public void SubmitRenewCertificateRequest()  
    {  
       // Add certificate renewal code   
    }  
    ```  
  
10. Добавьте метод UpdateDNSRecords, который обновляет DNS-записи, хранящийся в определителе. В следующем примере показан метод UpdateDNS.  
  
    ```c#  
  
    public bool UpdateDnsRecords(IList<DnsRecord> records)  
    {  
       string UpdateDNS = "true";  
       using (RegistryKey key = ProductInfo.RegKey.OpenSubKey("Domain Manager\\Settings", true))  
       {  
          UpdateDNS = (key == null) ? "true" : key.GetValue("UpdateDNS", "true").ToString();  
       }  
  
       return UpdateDNS == "true";  
    }  
  
    ```  
  
11. Добавьте метод TestConnection, который пытается установить подключение к внутренней службы. Если этот метод требует проверки подлинности, должны быть соответствующие исключение. В следующем примере показан метод TestConnection.  
  
    ```c#  
  
    public bool TestConnection()  
    {  
       // Add code to test connection  
  
       return true;  
    }  
    ```  
  
12. Добавьте метод GetDomainState, который возвращает текущее состояние домена. В следующем примере показан метод GetDomainState.  
  
    ```c#  
  
    public DomainState GetDomainState()  
    {  
       string domainstatus = "FullyOperational";  
       long expirationDate = 365;  
       using (RegistryKey key = ProductInfo.RegKey.OpenSubKey("Domain Manager\\Settings", true))  
       {  
          domainstatus = (key == null) ? "Ready" : key.GetValue("DomainStatus", "Ready").ToString();  
          expirationDate = Int64.Parse(key.GetValue("ExpirationDate", "365").ToString());  
       }  
  
       switch (domainstatus)  
       {  
          case "Failed":  
             return new DomainState(DomainStatus.Failed,   
                null,   
                DateTime.Now.AddDays(expirationDate));  
          case "Ready":  
             return new DomainState(DomainStatus.Ready,   
                null,   
                DateTime.Now.AddDays(expirationDate));  
          case "InRenewal":  
             return new DomainState(DomainStatus.InRenewal,   
                null,   
                DateTime.Now.AddDays(expirationDate));  
          case "InRenewalCustomerInterventionRequired":  
             return new DomainState(DomainStatus.InRenewalCustomerInterventionRequired,   
                null,   
                DateTime.Now.AddDays(expirationDate));  
          case "Pending":  
             return new DomainState(DomainStatus.Pending,   
                null,   
                DateTime.Now.AddDays(expirationDate));  
          case "PendingCustomerInterventionRequired":  
             return new DomainState(DomainStatus.PendingCustomerInterventionRequired,   
                null,   
                DateTime.Now.AddDays(expirationDate));  
          case "RenewalFailed":  
             return new DomainState(DomainStatus.RenewalFailed,   
                null,   
                DateTime.Now.AddDays(expirationDate));  
          default:  
             return new DomainState(DomainStatus.Unknown,   
                null,   
                DateTime.Now.AddDays(expirationDate));                   
          }  
    }  
    ```  
  
13. Добавьте метод GetCertificateState, который возвращает текущее состояние сертификата. В следующем примере показан метод GetCertificateState.  
  
    ```c#  
  
    public CertificateState GetCertificateState(bool renew)  
    {  
       return new CertificateState(CertificateStatus.Ready, string.Empty);  
    }  
    ```  
  
14. Сохраните и построение решения.  
  
###  <a name="BKMK_SignAssembly"></a>Подпишите сборку подпись Authenticode  
 Вы должны будете подпись Authenticode сборки, он должен использоваться в операционной системе. Дополнительные сведения о подписи сборки см. в разделе [подпись и проверка кода с помощью Authenticode](https://msdn.microsoft.com/library/ms537364\(VS.85\).aspx#SignCode).  
  
###  <a name="BKMK_InstallAssembly"></a>Установить сборку на компьютере-образце  
 Установите сборки в папку на компьютере-образце. Запишите путь к папке, так как он перейдет в реестре в следующем шаге.  
  
### <a name="add-a-key-to-the-registry"></a>Добавить раздел в реестр  
 Добавьте запись реестра, чтобы определить характеристики и расположение сборки.  
  
##### <a name="to-add-a-key-to-the-registry"></a>Чтобы добавить раздел в реестр  
  
1.  На компьютере-образце нажмите кнопку **запустить**, введите **regedit**, а затем нажмите клавишу **ввод**.  
  
2.  В левой области разверните **HKEY_LOCAL_MACHINE**, разверните **программного обеспечения**, разверните **Microsoft**, разверните **Windows Server**, разверните **диспетчеров доменов**и затем разверните **поставщики**.  
  
3.  Щелкните правой кнопкой мыши **поставщики**, наведите курсор на **New**, а затем нажмите кнопку **ключ**.  
  
4.  Введите идентификатор для поставщика в качестве имени раздела. Идентификатор — это GUID, определенный для поставщика на шаге 8 процедуры [добавьте реализацию интерфейса IDomainSignupProvider сборки](Add-Third-Level-Domain-Names.md#BKMK_DomainSignup).  
  
5.  Щелкните правой кнопкой мыши только что создан, а затем нажмите кнопку **строковое значение**.  
  
6.  Тип **сборки** имя строки, а затем нажмите клавишу **ввод**.  
  
7.  Щелкните правой кнопкой мыши новый **сборки** строка в правой области и нажмите кнопку **изменить**.  
  
8.  Введите полный путь к файлу сборки, который вы создали ранее и нажмите кнопку **ОК**.  
  
9. Щелкните правой кнопкой мыши раздел, а затем нажмите кнопку **строковое значение**.  
  
10. Тип **включено** имя строки, а затем нажмите клавишу **ввод**.  
  
11. Щелкните правой кнопкой мыши новый **включено** строка в правой области и нажмите кнопку **изменить**.  
  
12. Тип **True**, а затем нажмите кнопку **ОК**.  
  
13. Щелкните правой кнопкой мыши раздел, а затем нажмите кнопку **строковое значение**.  
  
14. Тип **тип** имя строки, а затем нажмите клавишу **ввод**.  
  
15. Щелкните правой кнопкой мыши новый **тип** строка в правой области и нажмите кнопку **изменить**.  
  
16. Введите полное имя класса поставщика, определенные в сборке, а затем нажмите кнопку **ОК**.  
  
###  <a name="BKMK_RestartService"></a>Перезапустите службу управление доменными именами Windows Server  
 Необходимо перезапустить службу управления домена Windows Server для поставщика станет доступна для операционной системы.  
  
##### <a name="restart-the-service"></a>Перезапустите службу  
  
1.  Нажмите кнопку **запустить**, тип **mmc**, а затем нажмите клавишу **ввод**.  
  
2.  Если оснастку «службы» не отображается в консоли, добавьте его, выполнив следующие действия:  
  
    1.  Нажмите кнопку **файл**, а затем нажмите кнопку **добавить или удалить оснастку**.  
  
    2.  В **Доступные оснастки** выберите **службы**, а затем нажмите кнопку **добавить**.  
  
    3.  В **службы** диалогового окна убедитесь, что **локального компьютера** установлен, а затем нажмите кнопку **Готово**.  
  
    4.  Нажмите кнопку **ОК** закрыть **Добавление или удаление оснастки** диалоговое окно.  
  
3.  Дважды щелкните **службы**, прокрутите список вниз и выберите **управления домена Windows Server**, а затем нажмите кнопку **перезапустите службу**.  
  
## <a name="see-also"></a>См. также:  
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)