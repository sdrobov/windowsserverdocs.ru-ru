---
title: Настройка узлов для динамической миграции без отказоустойчивой кластеризации
description: Инструкции по настройке динамической миграции в некластеризованной среде
ms.prod: windows-server-threshold
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b5e3c405-cb76-4ff2-8042-c2284448c435
author: KBDAzure
ms.author: kathydav
ms.date: 9/30/2016
ms.openlocfilehash: 49e36d7fae5eec07772fd6f82c5a5d69838351d8
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59821995"
---
# <a name="set-up-hosts-for-live-migration-without-failover-clustering"></a>Настройка узлов для динамической миграции без отказоустойчивой кластеризации

>Область применения. Windows Server 2016, Microsoft Hyper-V Server 2016, Windows Server 2019 г., Microsoft Hyper-V Server 2019 г.

В этой статье показано, как настроить узлы, которые не clustered, поэтому можно, динамическая миграция между ними. Используйте эти инструкции, если вы не настроили динамической миграции, при установке Hyper-V, или если вы хотите изменить параметры. Для настройки узлов кластера, используйте средства отказоустойчивой кластеризации.  
  
## <a name="requirements-for-setting-up-live-migration"></a>Требования к настройке динамической миграции  
  
Чтобы настроить некластеризованных узлов для динамической миграции, вам потребуется:   
  
-  Учетная запись пользователя с разрешением для выполнения следующих шагов. Членство в локальной группе администраторов Hyper-V или в группу администраторов на исходном и конечном компьютерах соответствует этому требованию, если вы настраиваете ограниченного делегирования. Членство в группе администраторов домена является обязательным для настройки ограниченного делегирования.  
  
- Роль Hyper-V в Windows Server 2016 или Windows Server 2012 R2, установлены на исходном и конечном серверах. Можно выполнить динамическую миграцию между узлами под управлением Windows Server 2016 и Windows Server 2012 R2, если виртуальная машина по крайней мере версии 5. <br>Инструкции по обновлению версии, см. в разделе [обновление версии виртуальной машины в Hyper-V в Windows 10 или Windows Server 2016](Upgrade-virtual-machine-version-in-Hyper-V-on-Windows-or-Windows-Server.md). Инструкции по установке см. в разделе [установить роль Hyper-V в Windows Server](../get-started/Install-the-Hyper-V-role-on-Windows-Server.md).  
  
- Исходный и конечный компьютеры, которые принадлежат к тому же домену Active Directory, либо к доменам, доверяющим друг другу.    
- Средства управления Hyper-V, установленных на компьютере под управлением Windows Server 2016 или Windows 10, если средства устанавливаются на сервере источника или назначения и вы будете запускать средства с сервера.  
  
## <a name="consider-options-for-authentication-and-networking"></a>Рассмотрите варианты для проверки подлинности и сети  
  
Рассмотрим, как вы хотите настроить следующее:  
  
-  **Проверка подлинности**: Протокол, который будет использоваться для проверки подлинности трафика динамической миграции между исходный и конечный серверы? Выбор определяет ли вам потребуется выполнить вход на исходный сервер перед началом динамической миграции:   
   - Kerberos позволяет избежать необходимости входа на сервер, но требует ограниченное делегирование, которое необходимо настроить. Ниже приведены инструкции.  
   - CredSSP позволяет избежать Настройка ограниченного делегирования, но требует, чтобы войти на исходный сервер. Это можно сделать через локальный сеанс консоли, сеанс удаленного рабочего стола или удаленный сеанс Windows PowerShell.  
  
      CredSPP требуется вход в ситуациях, где могут возникнуть затруднения. Например если вход на TestServer01 для перемещения виртуальной машины на testserver02 вы, а затем хотите переместить виртуальную машину обратно на TestServer01 необходимо войдете на TestServer02 перед попыткой перемещения виртуальной машины обратно на TestServer01. Если этого не сделать, попытки проверки подлинности завершается ошибкой, возникает ошибка, и отображается следующее сообщение:  
    
      «Сбой операции миграции виртуальной машины в исходном расположении миграции.  
      Не удалось установить соединение с узлом *имя_компьютера*: Учетные данные не доступны в пакете безопасности данные 0x8009030E.»
  
-   **Производительность**: Имеет смысл настроить параметры производительности? Эти параметры можно сократить, сеть и ЦП, а также сделать динамической миграции работать все быстрее. Рассмотрим требований и инфраструктуры и проверить различные конфигурации, которые помогут решить. Параметры описаны в конце шаг 2.  
  
-  **Сетевые настройки**: Разрешите ли вы прохождение трафика динамической миграции через любую доступную сеть или ограничите его определенными сетями? В качестве рекомендации по безопасности мы советуем вам ограничить прохождение трафика доверенными частными сетями, потому что трафик динамической миграции не шифруется при отправке по сети. Для обеспечения сетевой изоляции можно воспользоваться физически изолированной сетью или другой доверенной сетевой технологией, например VLAN.  
  
## <a name="BKMK_Step1"></a>Шаг 1. Настройка ограниченного делегирования (необязательно)  
Если вы решили использовать Kerberos для проверки подлинности трафика динамической миграции, настройте ограниченное делегирование, с помощью учетной записи, которая является членом группы администраторов домена.  
  
### <a name="use-the-users-and-computers-snap-in-to-configure-constrained-delegation"></a>Используйте оснастку «Пользователи и компьютеры», чтобы настроить ограниченное делегирование  
  
1.  Откройте оснастку "Active Directory - пользователи и компьютеры". (В диспетчере серверов выберите сервер, если он не выбран, щелкните **средства** >> **Active Directory — пользователи и компьютеры**).  
  
2.  В области навигации **Active Directory — пользователи и компьютеры**, выберите домен и дважды щелкните **компьютеров** папки.  
  
3.  Из **компьютеров** папку, щелкните правой кнопкой мыши учетная запись компьютера исходного сервера, а затем нажмите кнопку **свойства**.  
  
4.  Из **свойства**, нажмите кнопку **делегирования** вкладки.  
  
5.  На вкладке «делегирование» выберите **доверять компьютеру делегирование только указанных служб** , а затем выберите **использовать любой протокол проверки подлинности**.  
  
6.  Нажмите кнопку **Добавить**.  
  
7.  Из **Добавление служб**, нажмите кнопку **пользователей или компьютеров**.  
  
8.  Из **Выбор пользователей или компьютеров**, введите имя конечного сервера. Нажмите кнопку **проверить имена** проверить его, а затем нажмите кнопку **ОК**.  
  
9. Из **Добавление служб**, в списке доступных служб выполните следующие действия и нажмите кнопку **ОК**:  
  
    -   Для перемещения хранилищ виртуальной машины выберите **cifs**. Это необходимо, если вы хотите переместить хранилище вместе с виртуальной машины, а также как, если вы хотите переместить только хранилище виртуальной машины. Если сервер настроен для использования хранилища SMB для Hyper-V, этот параметр уже должен быть выбран.  
  
    -   Для перемещения виртуальных машин выберите **Службу миграции виртуальной системы Майкрософт**.  
  
10. На вкладке **Делегирование** диалогового окна "Свойства" убедитесь, что службы, выбранные на предыдущем шаге, указаны как службы, которым конечный компьютер может представлять делегированные учетные данные. Нажмите кнопку **ОК**.  
  
11. В папке **Компьютеры** выберите учетную запись компьютера конечного сервера и повторите процесс. Убедитесь, что в диалоговом окне **Выбор пользователей или компьютеров** указано имя исходного сервера.  
  
Изменения конфигурации вступят в силу после внесения оба из следующих:  
  
  -  Изменения реплицируются на контроллеры домена, которые были зарегистрированы серверы с Hyper-V в.  
  -  Контроллер домена выдает новый билет Kerberos.  
  
## <a name="BKMK_Step2"></a>Шаг 2. Настройте исходный и конечный компьютеры для динамической миграции  
Этот этап включает в себя Выбор параметров для проверки подлинности и сети. По соображениям безопасности рекомендуется выбирать определенные сети для трафика динамической миграции, как описано выше. Этот шаг также показано, как выбрать вариант производительности.   
  
### <a name="use-hyper-v-manager-to-set-up-the-source-and-destination-computers-for-live-migration"></a>Настройте исходный и конечный компьютеры для динамической миграции с помощью диспетчера Hyper-V  
  
1.  Откройте диспетчер Hyper-V. (В диспетчере сервера щелкните **средства** >>**диспетчера Hyper-V**.)  
  
2.  В области навигации выберите один из серверов. (Если его нет в списке, щелкните правой кнопкой мыши **диспетчера Hyper-V**, нажмите кнопку **соединение с сервером**, введите имя сервера и нажмите кнопку **ОК**. Повторите эти шаги для добавления дополнительных серверов.)  
  
3.  В **действие** панели щелкните **параметры Hyper-V** >>**динамические миграции**.  
  
4.  На панели **Динамические миграции** проверьте, включен ли параметр **Разрешить входящие и исходящие динамические миграции**.  
  
5.  В разделе **одновременных операций динамической миграции**, укажите другую цифру, если вы не хотите использовать значение по умолчанию 2.  
  
6.  Для параметра **Входящие динамические миграции**, если вы хотите использовать определенные сетевые соединения для принятия трафика динамической миграции, выберите **Добавить** , чтобы ввести информацию об IP-адресе. В обратном случае щелкните **Использовать любую доступную сеть для динамической миграции**. Нажмите кнопку **ОК**.  
  
7.  Чтобы выбрать параметры Kerberos и производительности, разверните **динамические миграции** , а затем выберите **дополнительные функции**.  
  
    - Если вы настроили ограниченное делегирование в разделе **протокол проверки подлинности**выберите **Kerberos**.  
    - В разделе **параметры производительности**, просмотрите сведения и выбрать другой параметр, если это требуется для вашей среды.   
  
8. Нажмите кнопку **ОК**.  
  
9. Выберите другой сервер в диспетчере Hyper-V и повторите шаги.  
  
### <a name="use-windows-powershell-to-set-up-the-source-and-destination-computers-for-live-migration"></a>Настройте исходный и конечный компьютеры для динамической миграции с помощью Windows PowerShell  
  
Для настройки динамической миграции на некластеризованных узлов доступны три командлета: [Enable-VMMigration](https://technet.microsoft.com/library/hh848544.aspx), [Set-VMMigrationNetwork](https://technet.microsoft.com/library/hh848467.aspx), и [Set-VMHost](https://technet.microsoft.com/library/hh848524.aspx). В этом примере используются все три и выполняет следующие функции:   
  - Настраивает динамической миграции на локальном узле  
  - Разрешает трафик входящей миграции только в конкретной сети  
  - Выбирает в качестве протокола проверки подлинности Kerberos   
  
Каждая строка представляет собой отдельную команду.  
  
```  
PS C:\> Enable-VMMigration  
  
PS C:\> Set-VMMigrationNetwork 192.168.10.1  
  
PS C:\> Set-VMHost -VirtualMachineMigrationAuthenticationType Kerberos  
  
```  
SET-VMHost позволяет также выбрать параметр производительности (и многие другие параметры узла). Например чтобы выбрать SMB, но оставьте значение по умолчанию CredSSP протокол проверки подлинности, введите следующую команду:  
  
```  
PS C:\> Set-VMHost -VirtualMachineMigrationPerformanceOption SMBTransport  
  
```  
  
Эта таблица описывает, как работают параметры быстродействия.  
  
|Параметр|Описание|  
|----------|---------------|  
    |TCP/IP|Копирует память виртуальной машины на целевой сервер через подключение TCP/IP.|  
    |сжатие;|Сжимает содержимое памяти виртуальной машины перед копированием на конечный сервер через подключение TCP/IP. **Примечание.** Это **по умолчанию** параметр.|  
    |SMB|Копирует память виртуальной машины на целевой сервер через подключение SMB 3.0.<br /><br />-SMB Direct используется при сетевых адаптеров на исходном и конечном серверах имеют возможностей удаленный доступ к памяти (RDMA).<br />-SMB Multichannel автоматически обнаруживает и использует несколько подключений, если определена соответствующая конфигурация SMB Multichannel.<br /><br />Дополнительные сведения см. в статье [Увеличение производительности файлового сервера с помощью SMB Direct](https://technet.microsoft.com/library/jj134210(WS.11).aspx).|  
      
 ## <a name="next-steps"></a>Следующие шаги
 
 После настройки узлов, вы готовы выполнить динамическую миграцию. Инструкции см. в разделе [использование динамической миграции без отказоустойчивой кластеризации для перемещения виртуальной машины](../manage/Use-live-migration-without-Failover-Clustering-to-move-a-virtual-machine.md). 
    

