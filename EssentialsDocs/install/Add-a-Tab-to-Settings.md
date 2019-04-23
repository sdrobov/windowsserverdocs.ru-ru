---
title: Добавление вкладки в раздел "Параметры"
description: Описывает способ использования Windows Server Essentials
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
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59854985"
---
# <a name="add-a-tab-to-settings"></a>Добавление вкладки в раздел "Параметры"

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Для добавления вкладки в раздел Параметры на панели мониторинга нужно создать и установить сборку кода, используемую диспетчером параметров операционной системы.  
  
## <a name="add-a-tab-to-settings"></a>Добавить вкладку в Параметры  
 Чтобы добавить вкладку в параметры, нужно выполнить следующие действия:  
  
-   [Добавление в сборку реализации интерфейса ISettingsData](Add-a-Tab-to-Settings.md#BKMK_ISettingsData).  
  
-   [Sign the assembly with an Authenticode signature](Add-a-Tab-to-Settings.md#BKMK_SignAssembly).  
  
-   [Установка сборки на компьютере-образце](Add-a-Tab-to-Settings.md#BKMK_InstallAssembly).  
  
###  <a name="BKMK_ISettingsData"></a> Добавление в сборку реализации интерфейса ISettingsData  
 Интерфейс ISettingsData включен в пространство имен Microsoft.WindowsServerSolutions.Settings сборки AdminCommon.dll, которая расположена в папке \Program Files\Windows Server\Bin.  
  
##### <a name="to-add-the-isettingsdata-code-to-the-assembly"></a>Добавление в сборку реализации интерфейса ISettingsData  
  
1.  Откройте Visual Studio 2010 с правами администратора, щелкнув эту программу правой кнопкой мыши в меню **Пуск** и выбрав команду **Запуск от имени администратора**.  
  
2.  В меню **Файл**выберите команду **Создать**и щелкните пункт **Проект**.  
  
3.  В диалоговом окне **Новый проект** последовательно щелкните **Visual C#**, затем **Библиотека классов**, введите **DashboardSettingsPage** в качестве имени решения и нажмите кнопку **OK**.  
  
    > [!IMPORTANT]
    >  Сборку, устанавливаемую на сервер, необходимо назвать DashboardSettingsPage.dll и затем скопировать DLL в папку %ProgramFiles%\Windows Server\Bin\OEM.  
  
4.  Создайте элемент управления, который требуется использовать на вкладке. В этом примере используется элемент управления параметрами с именем MySettingsControl.  
  
5.  Присвойте файлу Class1.cs другое имя, например MySettingTab.cs.  
  
6.  Добавьте ссылку на файл AdminCommon.dll.  
  
7.  Добавьте следующий оператор using:  
  
    ```c#  
    using Microsoft.WindowsServerSolutions.Settings;  
    ```  
  
8.  Измените пространство имен и заголовок класса аналогично следующему примеру:  
  
    ```  
  
    namespace DashboardSettingsPage  
    {  
        public class MySettingTab : ISettingsData  
        {  
        }  
    }  
  
    ```  
  
9. Создайте экземпляр элемента управления, созданного для вкладки. Пример:  
  
    ```c#  
    private MySettingsControl tab;  
    ```  
  
10. Добавьте конструктор для класса. Подобный конструктор показан в следующем примере кода:  
  
    ```  
  
    public MySettingTab()  
    {  
       tab = new MySettingsControl();  
    }  
    ```  
  
11. Добавьте метод Commit, который отправляет изменения параметров. Метод Commit показан в следующем примере кода:  
  
    ```  
  
    void ISettingsData.Commit(bool dismissed)  
    {  
       // Implement the code that is required to submit your setting changes  
    }  
    ```  
  
12. Добавьте метод TabControl, который определяет элемент управления для вкладки. Метод TabControl показан в следующем примере кода:  
  
    ```  
  
    System.Windows.Forms.Control ISettingsData.TabControl  
    {  
       get { return tab; }  
    }  
    ```  
  
13. Добавьте метод TabId, который предоставляет уникальный идентификатор для вкладки. Метод TabId показан в следующем примере кода:  
  
    ```  
  
    private Guid id = Guid.NewGuid();  
  
    Guid ISettingsData.TabId  
    {  
       get { return id; }  
    }  
    ```  
  
14. Добавьте метод TabOrder, который возвращает порядковый номер вкладки. Метод TabOrder показан в следующем примере кода:  
  
    ```  
  
    int ISettingsData.TabOrder  
    {  
       get { return 0; }  
    }  
    ```  
  
    > [!NOTE]
    >  Порядковый номер вкладки отсчитывается от 0. Сначала отображаются встроенные вкладки параметров Майкрософт, а пользовательские вкладки отображаются в соответствии с указанными для них порядковыми номерами. Например, при наличии трех вкладок параметров для них указываются порядковые номера 0, 1 и 2 в соответствии с порядком отображения вкладок.  
  
15. Добавьте метод TabTitle, предоставляющий Заголовок вкладки. Метод TabTitle показан в следующем примере кода:  
  
    ```  
  
    string ISettingsData.TabTitle  
    {  
      get { return "My Settings Tab"; }  
    }  
    ```  
  
    > [!NOTE]
    >  При необходимости локализации программного обеспечения для предоставления заголовка вкладки можно также использовать файл ресурсов.  
  
16. Сохраните решение и выполните его построение.  
  
###  <a name="BKMK_SignAssembly"></a> Поставьте на сборке подпись Authenticode  
 Чтобы сборку можно было использовать в операционной системе, на ней должна быть подпись Authenticode. Дополнительные сведения о подписи сборки см. в разделе [Подпись и проверка кода с помощью Authenticode](https://msdn.microsoft.com/library/ms537364\(VS.85\).aspx#SignCode).  
  
###  <a name="BKMK_InstallAssembly"></a> Установка сборки на компьютере-образце  
 В случае успешного построения решения поместите копию файла DashboardSettingsPage.dll в следующую папку на компьютере-образце:  
  
 **%Programfiles%\Windows Server\Bin\OEM**  
  
## <a name="see-also"></a>См. также  
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)