---
title: tsecimp
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d7488ec6-0eff-45ff-89ee-9cbe752416bf
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a5ed2ef8b1d0238a3608dabdd165a255855a304d
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66440872"
---
# <a name="tsecimp"></a>tsecimp



Импортирует сведения о назначении из файла расширяемого языка разметки (XML) в защищенный файл сервера TAPI (Tsec.ini). Можно также использовать эту команду для отображения списка поставщиков TAPI и устройств, связанных с каждым из них, проверки структуры XML-файла без импорта содержимого и проверять членство в домене.

## <a name="syntax"></a>Синтаксис

```
tsecimp /f <Filename> [{/v | /u}]
tsecimp /d
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/f \<имя файла >|Обязательный. Указывает имя XML-файл, содержащий сведения о назначении, который требуется импортировать.|
|/v|Проверяет структуру XML-файла, не импортируя данные в файл Tsec.ini.|
|/u|Проверяет, является ли каждый пользователь является членом домена, указанного в XML-файле. Компьютер, на котором используется этот параметр должен быть подключен к сети. Этот параметр может существенно снизить производительность при обработке большого объема о назначении пользователей.|
|/d|Отображение списка установленных поставщиков услуг телефонии. Для каждого поставщика услуг перечисляются соответствующие устройства, а также адресов и пользователей, связанных с каждым устройством.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

-   XML-файл, из которого требуется импортировать сведения о назначении должен иметь структуру, описанных ниже.  
    -   **UserList** элемент

        **UserList** является верхним элементом XML-файла.
    -   **Пользователь** элемент

        Каждый **пользователя** элемент содержит сведения о пользователе, который является членом домена. Каждый пользователь может назначить один или несколько устройств.

        Кроме того, каждое **пользователя** элемент может иметь атрибут с именем **NoMerge**. Если этот атрибут указан, все текущие назначения устройств для пользователя, удаляются прежде, чем создаются новые. Этот атрибут можно использовать для быстрого удаления ненужных назначений пользователя. По умолчанию этот атрибут не задано.

        **Пользователя** элемент должен содержать один **DomainUserName** элемент, который указывает домен и имя пользователя. **Пользователя** элемент также может содержать один **FriendlyName** элемент, который указывает понятное имя для пользователя.

        **Пользователя** элемент может содержать один **LineList** элемент. Если **LineList** элемент отсутствует, удаляются все строки устройства для этого пользователя.
    -   **LineList** элемент

        **LineList** элемент содержит сведения о каждой строки или устройство, которое могут быть назначены пользователю. Каждый **LineList** элемент может содержать более одного **строки** элемент.
    -   **Строки** элемент

        Каждый **строки** элемент определяет устройство линии. Необходимо определить каждого устройства, добавив **адрес** элемент или **PermanentID** элемента под **строки** элемент.

        Для каждого **строки** элемент, можно задать **удалить** атрибута. Если присвоить этому атрибуту, пользователь больше не назначается этого устройства. Если этот атрибут не задан, пользователь получает доступ к данному устройству линии. Ошибка не выдается в том случае, если устройство линии недоступен пользователю.

## <a name="examples"></a>Примеры
- Следующие сегменты кода примера XML показано правильное использование элементов, определенных выше.  
  - Следующий код удаляет все строки устройства, назначенные пользователю User1.  
    ```
    <UserList>
      <User NoMerge="1">
        <DomainUser>domain1\user1</DomainUser>
      </User>
    </UserList>
    ```  
  - Следующий код удаляет все строки устройства, назначенные пользователю User1, перед назначением одну строку с адресом 99999. Пользователь USER1 получит другие устройства линии независимо от того, какие-то устройства были назначены ранее.  
    ```
    <UserList>
      <User NoMerge="1">
        <DomainUser>domain1\user1</DomainUser>
        <FriendlyName>User1</FriendlyName>
        <LineList>
          <Line>
            <Address>99999</Address>
          </Line>
        </LineList>
      </User>
    </UserList>
    ```  
  - Следующий код добавляет одно устройство строки для пользователя User1 без удаления ранее назначенных устройств.  
    ```
    <UserList>
      <User>
        <DomainUser>domain1\user1</DomainUser>
        <FriendlyName>User1</FriendlyName>
        <LineList>
          <Line>
            <Address>99999</Address>
          </Line>
        </LineList>
      </User>
    </UserList>
    ```  
  - Следующий код добавляет адресом 99999 и удаляет адресом 88888 из доступа пользователя User1.  
    ```
    <UserList>
      <User>
        <DomainUser>domain1\user1</DomainUser>
        <FriendlyName>User1</FriendlyName>
        <LineList>
          <Line>
            <Address>99999</Address>
          </Line>
          <Line Remove="1">
            <Address>88888</Address>
          </Line>
        </LineList>
      </User>
    </UserList>
    ```  
  - Следующий код добавляет устройство с постоянным 1000 и удаляет строки 88888 из доступа пользователя User1.  
    ```
    <UserList>
      <User>
        <DomainUser>domain1\user1</DomainUser>
        <FriendlyName>User1</FriendlyName>
        <LineList>
          <Line>
            <PermanentID>1000</PermanentID>
          </Line>
          <Line Remove="1">
            <Address>88888</Address>
          </Line>
        </LineList>
      </User>
    </UserList>


~~~
    ```  
~~~
-   The following sample output appears after the **/d** command-line option is specified to display the current TAPI configuration. For each telephony provider, the associated line devices are listed, as well as the addresses and users associated with each line device.  
    ```
    NDIS Proxy TAPI Service Provider
            Line: "WAN Miniport (L2TP)"
                    Permanent ID: 12345678910

    NDIS Proxy TAPI Service Provider
            Line: "LPT1DOMAIN1\User1"
                    Permanent ID: 12345678910

    Microsoft H.323 Telephony Service Provider
            Line: "H323 Line"
                    Permanent ID: 123456
                    Addresses:
                            BLDG1-TAPI32

    ```

#### Additional references

[Command-Line Syntax Key](command-line-syntax-key.md)

[Command shell overview](https://technet.microsoft.com/library/cc737438(v=ws.10).aspx)