---
title: "Подготовка образа для развертывания"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 681c6cad-7fde-494f-86a5-f4c7c15d23f9
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 16411ab073e9417c52592aa9a6b13707dd461537
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="preparing-the-image-for-deployment"></a>Подготовка образа для развертывания

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Обычное средство для подготовки образа — sysprep.exe. Запуск этого средства сделать образ универсальным и выключить сервер, чтобы после перезагрузки сервера, содержащий образ будет запущен в начальной конфигурации. Все изменения в образ должен быть завершен, перед запуском sysprep.exe.  
  
> [!NOTE]
>  Не более трех раз активацию Windows можно сбросить с помощью sysprep.exe.  
  
#### <a name="to-prepare-the-image"></a>Чтобы подготовить образ  
  
1.  Удалите добавленный SkipIC.txt?  
  
2.  Откройте окно командной строки с повышенными. Нажмите кнопку **запустить**, щелкните правой кнопкой мыши **командной строки**, а затем выберите **Запуск от имени администратора**.  
  
3.  Выполните следующую команду, чтобы сбросить раздел реестра, чтобы пользователь будет иметь полный льготный период, прежде чем сервер станет несоответствующим.  
  
    ```  
    %systemroot%\system32\reg.exe add HKLM\Software\Microsoft\ServerInfrastructureLicensing /v Rearm /t REG_DWORD /d 1 /f  
    ```  
  
4.  Выполните следующую команду, чтобы добавить раздел реестра для отображения ключа, страницы языка, страницы языкового стандарта и страницы лицензионного соглашения. По умолчанию эти страницы во время начальной настройки не отображаются. Следовательно случае выпуска предустановленного пакета необходимо добавить данный раздел реестра. Тем не менее если вы выпускаете DVD-диска, не следует добавлять этот ключ, как эти страницы будут отображены в ходе WinPE и начальной настройки.  
  
    ```  
    %systemroot%\system32\reg.exe add "HKLM\Software\microsoft\windows server\setup" /v ShowPreinstallPages /t REG_SZ /d true /f  
    ```  
  
5.  Если пакет содержит предварительно созданные разделы, отключите страницу раздела начальной настройки. Страница раздела будет отображаться только при ShowPreinstallPages = true и KeyPreInstalled! = true.  
  
    ```  
    %systemroot%\system32\reg.exe add "HKLM\Software\microsoft\windows server\setup" /v KeyPreInstalled /t REG_SZ /d true /f  
    ```  
  
6.  Выполните следующую команду, чтобы добавить раздел реестра, если вы хотите отключить проверки требований к оборудованию. Это относится только к предустановленному пакету, который не отвечает требованиям к оборудованию. Если вы выпускаете DVD-диска или коробки с вашим требованиям к оборудованию, рекомендуется не добавлять этот раздел.  
  
    ```  
    %systemroot%\system32\reg.exe add "HKLM\Software\microsoft\windows server\setup" /v HWRequirementChecks /t REG_DWORD /d 0 /f  
    ```  
  
7.  (Необязательно) Удалите журналы **%programdata%\Microsoft\Windows Server\Logs**.  
  
8.  Подготовьте автоматической XML-файл для sysprep, как показано в следующем формате.  
  
    ```  
    <unattend xmlns="urn:schemas-microsoft-com:unattend" xmlns:ms="urn:schemas-microsoft-com:asm.v3">  
  
      <settings pass="oobeSystem">  
        <component name="Microsoft-Windows-Shell-Setup" processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="https://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  
          <!-- Must have -->  
          <OOBE>  
             <HideEULAPage>true</HideEULAPage>  
          </OOBE>  
          <!-- Must have -->  
          <AutoLogon>   
            <Enabled>true</Enabled>   
            <Username>Administrator</Username>   
            <Domain>.</Domain>   
            <Password>   
              <!--You can set any password you like, but keep it consistent with password settings -->       
              <Value>Admin@123</Value>   
              <PlainText>true</PlainText>   
            </Password>   
          </AutoLogon>   
          <UserAccounts>   
           <AdministratorPassword>   
             <!--You can set any password you like, but keep it consistent with auto logon settings -->       
             <Value>Admin@123</Value>   
             <PlainText>true</PlainText>   
           </AdministratorPassword>   
          </UserAccounts>  
  
          <!-- Optional -->  
          <OEMInformation>  
             <HelpCustomized>true</HelpCustomized>  
             <Manufacturer>OEM name</Manufacturer>  
             <Model>model name</Model>  
             <SupportHours>hours</SupportHours>  
             <SupportPhone>123-456-7890</SupportPhone>  
             <SupportURL>http://www.contoso.com</SupportURL>  
          </OEMInformation>  
  
        </component>  
  
      </settings>  
  
      <settings pass="specialize">  
        <component name="Microsoft-Windows-Shell-Setup" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" processorArchitecture="amd64">  
          <!-- Must have -->  
          <ComputerName>Server</ComputerName>          
          <!-- Optional -->  
          <ProductKey>XXXXX-XXXXX-XXXXX-XXXXX-XXXXX</ProductKey>  
        </component>  
      </settings>  
    </unattend>  
    ```  
  
9. Выполните следующую команду в программе Sysprep.  
  
    ```  
    %systemroot%\system32\sysprep\sysprep.exe /generalize /OOBE /unattend:xxx.xml /Quit  
    ```  
  
    > [!IMPORTANT]
    >  Также можно добавить файл unattend.xml на % systemdrive %, а не в качестве параметра sysprep. Если файл находится в разделе c:\, он будет распространяться настройки пользователя s, если используется в качестве параметра sysprep, он не будут рассмотрены в s параметры пользователя. Файл unattend.xml на % systemdrive %, будут удалены при каждом перезапуске сервера. Следовательно убедитесь, что после создания unattend.xml на % systemdrive %, сервер не перезапускался.  
  
10. Выполните следующую команду, чтобы добавить раздел реестра и пропустить страницу ключа Windows OOBE.  
  
    ```  
    %systemroot%\system32\reg.exe add "HKLM\Software\microsoft\Windows\CurrentVersion\Setup\OOBE" /v SetupDisplayedProductKey /t REG_DWORD /d 1 /f  
    ```  
  
11. Выполните следующую команду, чтобы добавить раздел реестра и пропустить страницу выбора языка Windows.  
  
    ```  
    %systemroot%\system32\reg.exe add "HKLM\Software\microsoft\Windows\CurrentVersion\Setup\OOBE" /v SetupDisplayedLanguageSelection /t REG_DWORD /d 1 /f  
    ```  
  
    > [!IMPORTANT]
    >  Необходимо выполнить последние 2 шага, в противном случае появится страница запуска Windows при ПЕРВОМ связанная с начальной настройки страницы и нарушит сценарий удаленно администрируемого сервера.  
  
12. Выключите сервер после выполнения sysprep, можно создать образ или перезапустить сервер, чтобы продолжить начальную настройку с клиентского компьютера.  
  
> [!IMPORTANT]
>  Партнерам, планирующим создать носитель для восстановления сервера необходимо записать образ и создать носитель для восстановления перед переходом к следующему шагу.