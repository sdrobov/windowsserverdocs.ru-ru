---
title: "Создание файла Oobe.xml, включая эмблему и лицензионное соглашение"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8a7b3cc1-21bb-4344-8110-f5d5959b370d
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: f8f99a2051e114b3c890f1cdac23aebf58689980
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="create-the-oobexml-file-including-logo-and-eula"></a>Создание файла Oobe.xml, включая эмблему и лицензионное соглашение

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

С помощью файла Oobe.xml начальной настройки можно добавить собственные конечного пользователя условия лицензионного соглашения (EULA). Oobe.xml — это файл, для предоставления текст и изображения для начальной настройки, экрана приветствия Windows и других страниц, которые отображаются для конечного пользователя. Можно добавить несколько файлов Oobe.xml для настройки содержимого в соответствии с языком и страной или регионом, выбираемыми конечным пользователем. Дополнительные сведения см. в разделе [комплект средств для развертывания Windows 8 и оценки Windows](https://go.microsoft.com/fwlink/?LinkId=248694) документации.  
  
 Лицензионное соглашение компании отображается вместе с лицензионным СОГЛАШЕНИЕМ Майкрософт. Лицензионное соглашение Майкрософт сначала отображается во время начальной настройки взаимодействия с пользователем, а затем вашего лицензионного соглашения, будет отображаться. Лицензионное соглашение компании можно разместить в любом месте на сервере и указать расположение в файле Oobe.xml.  
  
#### <a name="to-add-your-company-eula-and-logo"></a>Чтобы добавить логотип и лицензионное соглашение компании  
  
1.  Откройте файл Oobe.xml в текстовом редакторе, например в блокноте.  
  
2.  В < logopath\ >< или logopath\ > теги, введите абсолютный путь к файлу эмблемы. Этот файл должен содержать 32-битовый графики (.png) файл размером 240 x 100 пикселей.  
  
3.  В < eulafilename\ >< или eulafilename\ > теги, введите абсолютный путь к файлу лицензионного соглашения. Файл лицензионного соглашения должен быть (.rtf) RTF-файл.  
  
4.  В < имя >< или имя > теги, введите название компании.  
  
     В следующем примере показаны теги в файле Oobe.xml.  
  
    ```  
  
    <FirstExperience>  
       <oobe>  
          <oem>  
             <name>Fabrikam</name>  
             <logopath>c:\fabrikam\fabrikam.png</logopath>  
             <eulafilename>c:\fabrikam\fabrikam_eula.rtf</eulafilename>  
          </oem>  
       </oobe>  
    </FirstExperience>  
  
    ```  
  
5.  Сохраните файл.  
  
6.  Поместите файл Oobe.xml в одной из следующих расположений:  
  
    |Расположение Oobe.xml|Условие для определения расположения|  
    |-----------------------|----------------------------------------|  
    |%windir%\system32\oobe\info\|Сервер продается в одной стране или регионе и в одной языковой системе.|  
    |%windir%\system32\oobe\info\default\\ < правильного >|Сервер продается в одной стране или регионе и в нескольких языковых системах.|  
    |%windir%\system32\oobe\info\\ < страны или региона > \ и %windir%\system32\oobe\info\\ < страны или региона > \ < правильного > \|Сервер продается в несколько стран или регионов и параметры требуют настройки отдельно для каждой страны или региона, каждый из которых соответствует один язык. Где < country/region > представляет десятичную версию идентификатора географического расположения (GeoID) страны или региона, где сервер развернут, а < правильного > — это десятичная версия языкового стандарта (LCID).|  
  
 Если эмблема компании содержит белый текст, его может быть лучше видно в ходе установки благодаря синему фону.  Можно дополнительно указать эту эмблему, установив раздел реестра и значение.  
  
#### <a name="to-specify-a-company-logo-by-setting-the-oem-registry-key"></a>Указание эмблемы компании путем установки раздела реестра OEM  
  
1.  На сервере, переместите указатель мыши в правый верхний угол экрана, а затем нажмите кнопку **поиска**.  
  
2.  В поле поиска введите **regedit**, а затем щелкните приложение Regedit.  
  
3.  В области навигации перейдите в раздел **HKEY_LOCAL_MACHINE**, разверните **программного обеспечения**, разверните **Microsoft**, разверните **Windows Server**. Если раздел OEM не существует, создайте раздел следующим образом:  
  
    1.  Щелкните правой кнопкой мыши **Windows Server**, нажмите кнопку **New**, а затем нажмите кнопку **ключ**.  
  
    2.  Имя ключа, введите **OEM**.  
  
4.  (Необязательно) Если вы создаете запись для логотипа, можно создать отдельные разделы для ее различных языковых версий логотипа. Например, если у вас есть версии на английском и немецком логотипа, можно создать en-us ключа и ключ, de-de. Так как все файлы логотип хранятся в той же папке, необходимо предоставить экземпляров файла с изображением эмблемы уникальное имя для каждого языка. Например можно создать файл с именем LogoWithWhiteText_en.png и LogoWithWhiteText_de.png.  
  
5.  Либо щелкните правой кнопкой мыши **OEM** или щелкните правой кнопкой мыши раздел соответствующий язык, щелкните, чтобы **New**, а затем нажмите кнопку **строковое значение**.  
  
6.  Введите LogoWithWhiteText в качестве строки и нажмите клавишу ВВОД.  
  
7.  Щелкните правой кнопкой мыши новую строку и выберите **изменить**.  
  
8.  Введите путь к изображению эмблемы и нажмите кнопку ОК.  
  
## <a name="see-also"></a>См. также:  
 [Начало работы с ADK Windows Server Essentials](Getting-Started-with-the-Windows-Server-Essentials-ADK.md)   
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)