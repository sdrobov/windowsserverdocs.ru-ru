---
title: AD FS Устранение неполадок — подключение к SQL
description: В этом документе описываются способы устранения различных аспектов службы федерации Active Directory
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 01/12/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 4b09094b6e305bc85b38e94d11fbc8845d555437
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66443936"
---
# <a name="ad-fs-troubleshooting---sql-connectivity"></a>AD FS Устранение неполадок — подключение к SQL
Службы федерации Active Directory предоставляет возможность использовать удаленный SQL Server для данных фермы AD FS.  Вы увидите проблемы, если серверы AD FS в ферме не может обмениваться данными с внутренними серверами SQL.  Следующий документ предоставит некоторых основных шага по тестированию обмен данными с внутренними серверами.

## <a name="acquire-the-sql-database-connection-string"></a>Получить строку подключения базы данных SQL
— В первую очередь необходимо проверить, когда идет проверка возможности подключения SQL, если службы федерации Active Directory содержат правильные данные подключения SQL.  Это можно сделать с помощью PowerShell.

### <a name="to-acquire-the-sql-connection-string"></a>Чтобы получить строку подключения SQL
1.  Откройте Windows PowerShell
2. Введите следующее: `$adfs = gwmi -Namespace root/ADFS -Class SecurityTokenService` и нажмите клавишу ВВОД
3. Введите следующее: `$adfs.ConfigurationDatabaseConnectionString` и нажмите клавишу ВВОД.
4. Вы увидите данные строки подключения.
![](media/ad-fs-tshoot-sql/sql2.png)

## <a name="create-a-universal-data-link-udl-file-to-test-connectivity"></a>Создайте файл универсальной Data Link (UDL) для проверки подключения
Универсальная связь данных файла или UDL-файл, по сути, является текстовый файл, содержащий строку подключения базы данных.  С помощью сведений, которые были получены выше мы тестируем ли SQL server отвечает на подключения.

### <a name="to-create-a-udl-file-to-test-connectivity"></a>Для создания UDL-файл, чтобы проверить возможность подключения

1. Откройте Блокнот и сохраните файл как test.udl.  Убедитесь, что у вас есть **все файлы** выбрать из раскрывающегося списка для **тип**.
2. Дважды щелкните test.udl
3. Укажите следующие сведения:. **Выберите или введите имя сервера:**  Используйте источник данных из строки подключения выше b. **Введите данные для входа сервер:**  Используйте учетную запись службы AD FS или учетную запись, имеющую разрешения на удаленный вход.  Если учетная запись использует учетную запись windows встроенную проверку подлинности в противном случае введите имя пользователя и пароль.
    В. **Выберите базу данных на сервере:** Используйте исходный каталог в строке выше.  Пример.  AdfsConfigurationV3.
   ![Проверка подключения](media/ad-fs-tshoot-sql/sql4.png)
1. Нажмите кнопку **Проверка соединения**.</br>
![Успех](media/ad-fs-tshoot-sql/sql3.png)

## <a name="use-sql-server-management-studio-to-test-connectivity"></a>Использовать для проверки подключения к SQL Server Management Studio
Вы также можете [загрузить](https://go.microsoft.com/fwlink/?linkid=864329) и установите SSMS, чтобы проверить подключение к базе данных.

### <a name="to-test-connectivity-with-ssms"></a>Чтобы проверить возможность подключения с помощью SSMS
1. Скачайте и установите SQL Server Management Studio.
![Установить](media/ad-fs-tshoot-sql/sql5.png)
1. Откройте среду SSMS, введите имя сервера.  Источник данных выше.
2. Используйте учетную запись службы AD FS или учетную запись, имеющую разрешения на удаленный вход.  Если учетная запись использует учетную запись windows встроенную проверку подлинности в противном случае введите имя пользователя и пароль.
![Подключение](media/ad-fs-tshoot-sql/sql6.png)
1. Вы должны увидеть левой заполнен.  Разверните узел базы данных и убедитесь, что вы видите баз данных AD FS.
![Базы данных AD FS](media/ad-fs-tshoot-sql/sql7.png)

## <a name="next-steps"></a>Следующие шаги

- [Устранение неполадок в AD FS](ad-fs-tshoot-overview.md)