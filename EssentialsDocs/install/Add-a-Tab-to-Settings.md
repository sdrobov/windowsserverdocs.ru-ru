---
title: "Добавить вкладку в параметры"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aac6b7f3-9020-46c3-a83f-b81542300385
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 9eaa1aa5a9c5e8d4c2e36f2000e0adecc83245d9
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="add-a-tab-to-settings"></a>Добавить вкладку в параметры

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Можно добавить вкладку в параметры на панели мониторинга, необходимо создать и установить сборку кода, которая используется диспетчером параметров в операционной системе.  
  
## <a name="add-a-tab-to-settings"></a>Добавить вкладку в параметры  
 Добавить вкладку в параметры, выполнив следующие задачи:  
  
-   [Добавьте реализацию интерфейса ISettingsData сборки](Add-a-Tab-to-Settings.md#BKMK_ISettingsData).  
  
-   [Подпишите сборку подпись Authenticode](Add-a-Tab-to-Settings.md#BKMK_SignAssembly).  
  
-   [Установить сборку на компьютере-образце](Add-a-Tab-to-Settings.md#BKMK_InstallAssembly).  
  
###  <a name="BKMK_ISettingsData"></a>Добавьте реализацию интерфейса ISettingsData сборки  
 Интерфейс ISettingsData входит в пространство имен Microsoft.WindowsServerSolutions.Settings AdminCommon.dll сборки, который находится в \Program Files\Windows Server\Bin.  
  
##### <a name="to-add-the-isettingsdata-code-to-the-assembly"></a>Добавление кода ISettingsData сборки  
  
1.  Откройте Visual Studio 2010 с правами администратора, щелкнув правой кнопкой мыши программы в **запустить** меню и выбрав **Запуск от имени администратора**.  
  
2.  Нажмите кнопку **файл**, нажмите кнопку **New**, а затем нажмите кнопку **проекта**.  
  
3.  В **новый проект** диалоговом нажмите кнопку **Visual C#**, нажмите кнопку **библиотека классов**, введите **DashboardSettingsPage** для имени решения, а затем нажмите кнопку **ОК**.  
  
    > [!IMPORTANT]
    >  Сборки, которая устанавливается на сервере должен быть назван DashboardSettingsPage.dll, а затем скопируйте библиотеку dll для %ProgramFiles%\Windows Server\Bin\OEM.  
  
4.  Создайте элемент управления, который будет использоваться на вкладке. В этом примере параметры управления с именем MySettingsControl.  
  
5.  Переименуйте файл Class1.cs. Например, MySettingTab.cs.  
  
6.  Добавьте ссылку на файл AdminCommon.dll.  
  
7.  Добавьте следующий оператор:  
  
    ```c#  
    using Microsoft.WindowsServerSolutions.Settings;  
    ```  
  
8.  Измените пространство имен и класс заголовок, чтобы следующим образом:  
  
    ```  
  
    namespace DashboardSettingsPage  
    {  
        public class MySettingTab : ISettingsData  
        {  
        }  
    }  
  
    ```  
  
9. Создайте экземпляр элемента управления, который вы создали для требуемой вкладки. Например:  
  
    ```c#  
    private MySettingsControl tab;  
    ```  
  
10. Добавьте конструктор для класса. В следующем примере кода показан конструктор:  
  
    ```  
  
    public MySettingTab()  
    {  
       tab = new MySettingsControl();  
    }  
    ```  
  
11. Добавьте метод фиксации, который отправляет измененные параметры. В следующем примере показан метод фиксации:  
  
    ```  
  
    void ISettingsData.Commit(bool dismissed)  
    {  
       // Implement the code that is required to submit your setting changes  
    }  
    ```  
  
12. Добавьте метод TabControl, который определяет элемент управления для вкладки. В следующем примере показан метод TabControl:  
  
    ```  
  
    System.Windows.Forms.Control ISettingsData.TabControl  
    {  
       get { return tab; }  
    }  
    ```  
  
13. Добавьте метод TabId, который предоставляет уникальный идентификатор для требуемой вкладки. В следующем примере показан метод TabId:  
  
    ```  
  
    private Guid id = Guid.NewGuid();  
  
    Guid ISettingsData.TabId  
    {  
       get { return id; }  
    }  
    ```  
  
14. Добавьте метод TabOrder, который возвращает заказа на вкладке. В следующем примере показан метод TabOrder:  
  
    ```  
  
    int ISettingsData.TabOrder  
    {  
       get { return 0; }  
    }  
    ```  
  
    > [!NOTE]
    >  Табуляции определяется с помощью номера, начиная с 0. Вкладки отображаются на основе последовательности перехода, который вы определяете и параметры встроенных вкладок Майкрософт отображаются первыми. Например если у вас есть три вкладки Параметры, укажите табуляции как 0, 1 и 2, в порядке, что требуется вкладки для отображения.  
  
15. Добавьте метод TabTitle, который содержит название вкладки. В следующем примере показан метод TabTitle:  
  
    ```  
  
    string ISettingsData.TabTitle  
    {  
      get { return "My Settings Tab"; }  
    }  
    ```  
  
    > [!NOTE]
    >  Текст названия, также могут поступать из файла ресурса для удовлетворения потребностей локализации.  
  
16. Сохраните и построение решения.  
  
###  <a name="BKMK_SignAssembly"></a>Подпишите сборку подпись Authenticode  
 Вы должны будете подпись Authenticode сборки, он должен использоваться в операционной системе. Дополнительные сведения о подписи сборки см. в разделе [подпись и проверка кода с помощью Authenticode](https://msdn.microsoft.com/library/ms537364\(VS.85\).aspx#SignCode).  
  
###  <a name="BKMK_InstallAssembly"></a>Установить сборку на компьютере-образце  
 После успешного построения решения, поместите копию файла DashboardSettingsPage.dll в следующей папке на компьютере-образце.  
  
 **%ProgramFiles%\Windows Server\Bin\OEM**  
  
## <a name="see-also"></a>См. также:  
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)