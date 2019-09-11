---
title: Создание новых статей по Windows Server с помощью GitHub и Visual Studio Code
description: Создание новых статей, связанных с Windows Server, с помощью GitHub и Visual Studio Code в качестве сотрудника Майкрософт.
author: eross-msft
ms.author: lizross
ms.date: 05/02/2019
ms.openlocfilehash: 3f09c36c1e3960728ff016f5801deb854e3d3c96
ms.sourcegitcommit: f6490192d686f0a1e0c2ebe471f98e30105c0844
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70865066"
---
# <a name="create-new-windows-server-articles-using-github-and-visual-studio-code"></a>Создание новых статей по Windows Server с помощью GitHub и Visual Studio Code

Существует два отдельных расположения, где мы будем размещать техническое содержимое Windows Server. Одно из расположений — Public (виндовссервердокс), а другое — частный (виндовссервердокс-PR). Кто определяет, в какое расположение вы вносите изменения:

- **Я являюсь сотрудником корпорации Майкрософт.** Как сотрудник корпорации Майкрософт, у вас есть варианты, основанные на том, что вы пытаетесь сделать:

    - **Создайте новую статью.** Чтобы создать новую статью, необходимо создать и настроить учетную запись GitHub и средства, вилку и клонировать репозиторий виндовссервердокс-PR, настроить удаленную ветвь, создать статью и, наконец, создать новый запрос на вытягивание для утверждения и публикации. Чтобы ознакомиться с этими инструкциями, продолжайте читать эту статью.

    - **Внести значительные изменения в существующую статью.** Чтобы внести существенные изменения в существующую статью, можно выполнить инструкции из [статьи изменение существующей системы Windows Server с помощью GitHub и Visual Studio Code](edit-existing-using-github.md) статьи.

    - **Внесение незначительных изменений в существующую статью.** Чтобы внести незначительные изменения в существующую статью, можно выполнить инструкции из статьи [обновление существующих статей о Windows Server с помощью веб-браузера и GitHub](github-browser-updates.md) .

- **Я не являюсь сотрудником корпорации Майкрософт.** В качестве сотрудника, не относящегося к корпорации Майкрософт, необходимо участвовать в общедоступном расположении. Сведения о том, как это сделать, см. в [технической документации «участие в программе Windows Server](https://github.com/MicrosoftDocs/windowsserverdocs/blob/master/CONTRIBUTING.md) ».

## <a name="prerequisites"></a>Предварительные требования

Прежде чем начать работу в репозитории, необходимо создать и настроить учетную запись GitHub, настроить двухфакторную проверку, а также установить и настроить все необходимые средства. Если вы уже сделали это, можно перейти к [разделу разветвления репозитория](#fork-the-repository) этой статьи.

1. [Создание учетной записи и профиля GitHub](https://review.docs.microsoft.com/help/contribute/contribute-get-started-setup-github?branch=master#create-a-github-account-and-set-up-your-profile)

2. [Свяжите свою учетную запись с учетная запись Майкрософт и с организациями Майкрософт и MicrosoftDocs](https://review.docs.microsoft.com/help/contribute/contribute-get-started-setup-github?branch=master#link-your-github-and-microsoft-accounts)

3. [Включить двухфакторную проверку](https://review.docs.microsoft.com/help/contribute/contribute-get-started-setup-github?branch=master#enable-two-factor-authentication-and-create-an-access-token)

4. [Авторизация системы сборки для доступа к учетной записи GitHub](https://review.docs.microsoft.com/help/contribute/contribute-get-started-setup-github?branch=master#authorize-the-ops-build-system-to-access-your-github-account)

5. [Установка Visual Studio Code](https://review.docs.microsoft.com/help/contribute/contribute-get-started-setup-tools?branch=master#install-visual-studio-code)

6. [Установка GitHub и его инструментов](https://review.docs.microsoft.com/help/contribute/contribute-get-started-setup-tools?branch=master#install-git-client-tools)

7. [Установка пакета создания документов](https://review.docs.microsoft.com/help/contribute/contribute-get-started-setup-tools?branch=master#install-the-docs-authoring-pack)

## <a name="set-up-your-own-version-of-the-repo"></a>Настройка собственной версии репозитория

После создания и настройки учетной записи GitHub и средств можно создать личную версию вашего репозитория. Здесь вы создадите ветви и внесете все изменения.

### <a name="fork-the-repository"></a>Выполните разветвление репозитория.

Вам потребуется локальная копия исходных файлов, чтобы можно было создавать запросы на вытягивание из вилки в рабочий репозиторий.

#### <a name="to-fork-the-repository"></a>Ветвление репозитория

1. Войдите в свою учетную запись GitHub и перейдите https://github.com/microsoftdocs/windowsserverdocs-pr по адресу.

2. Выберите **вилку**.

    ![Кнопка ветвления, выделенная на странице](media/create-new-using-github/fork-button.png)

3. Выберите свою учетную запись GitHub в качестве расположения разветвления.

    ![Кнопка ветвления, выделенная на странице](media/create-new-using-github/fork-location.png)

### <a name="clone-the-repository"></a>Клонируйте репозиторий.

Необходимо клонировать репозиторий, чтобы получить локальную копию репозитория на локальном устройстве.

#### <a name="to-clone-the-repository"></a>Клонирование репозитория

1. Перейдите в https://github.com/settings/developers , а затем выберите **Личные маркеры доступа** в левой области.

2. Выберите **создать новый токен**, присвойте токену осмысленное и уникальное имя, выберите все доступные области, а затем выберите **создать токен**.

3. Скопируйте маркер и вставьте его в безопасном месте. Это будет необходимо для оставшейся части процесса, и после выхода из этой страницы вы не сможете вернуться к ней.

4. Откройте команду git Bash и перейдите в каталог, где вы хотите сохранить репозиторий. Мы рекомендуем использовать, `C:\users\<your_name>\GitHub`.

5. Введите следующие команды, используя сведения по одной, чтобы клонировать репозиторий и настроить удаленные ветви:

    ```markdown

    git clone https://<your_github_username>:<your_personal_access_token>@github.com/<your_github_username>/windowsserverdocs-pr.git

    cd windowsserverdocs-pr

    git remote add upstream https://<your_github_username>:<your_personal_access_token>@github.com/MicrosoftDocs/windowsserverdocs-pr.git

    git fetch upstream master
    ```

6. Выполните следующую команду, чтобы убедиться, что удаленная настройка выполнена правильно:

    `git remote -v`

7. Вы должны увидеть примерно такие выходные данные:

    ```markdown
    $ git remote -v

    origin https://github.com/<your_github_username>/windowsserverdocs-pr.git (fetch)
    origin https://github.com/<your_github_username>/windowsserverdocs-pr.git (push)
    upstream https://github.com/MicrosoftDocs/windowsserverdocs-pr.git (fetch)
    upstream https://github.com/MicrosoftDocs/windowsserverdocs-pr.git (push)
    ```

    Если удаленный выход не выглядит так, можно повторить попытку при первом запуске `git remote remove upstream`.

## <a name="create-a-branch-and-a-new-article"></a>Создание ветви и новой статьи

Чтобы создать статью, выполните следующие действия.

### <a name="create-a-new-branch-and-a-new-file"></a>Создание новой ветви и нового файла

Перед началом работы с содержимым необходимо создать новую ветвь в локальном репозитории.

#### <a name="to-create-a-new-branch-in-git-bash"></a>Создание новой ветви в Git bash

- Откройте Git Bash и введите команды (по одной за раз):

    ```markdown
    cd windowsserverdocs-pr

    git checkout –B <name_of_your_new_branch>

    git push origin <name_of_your_new_branch>
    ```

    >[!Note]
    >Мы настоятельно рекомендуем назвать ветвь как очевидную и уникальную, чтобы ее можно было найти позже.

    После выполнения команд вы будете находиться в новой ветви и готовы к созданию нового файла. Необходимо только изменить в репозиторий виндовссервердокс-PR один раз для каждого экземпляра Git bash. Если вы закроете Git bash, необходимо будет снова изменить каталоги после его открытия.

#### <a name="to-create-a-new-file-in-your-branch"></a>Создание нового файла в ветви

1. Откройте проводник Windows, перейдите в каталог GitHub и создайте новый текстовый файл в структуре папок. Имя файла должно содержать все символы нижнего регистра и разделяться дефисами. Например, _What-is-Windows-Server.md_.

     Также необходимо изменить расширение файла с txt на. md. В появившемся сообщении об ошибке выберите **Да** , чтобы сохранить файл с новым расширением.

2. Откройте Visual Studio Code и перейдите в **файл**, выберите **Открыть папку**, а затем перейдите к расположению GitHub файла, созданного на шаге 1.

3. В области **Обозреватель** выберите новый файл.

4. Добавьте текст на страницу. Если вы создаете новую статью, убедитесь, что вы [добавили необходимые теги метаданных в соответствующую статью по Windows Server](metadata-requirements-for-articles.md).

5. Выберите **файл** > **сохранить**.

### <a name="preview-your-text"></a>Предварительный просмотр текста

После добавления текста в новый файл необходимо предварительно просмотреть изменения, чтобы убедиться, что они отображаются правильно.

#### <a name="to-preview-your-text"></a>Предварительный просмотр текста

1. В Visual Studio Code выберите любую из кнопок **предварительного просмотра** в правом верхнем углу.

    ![значок кнопки предварительного просмотра](media/create-new-using-github/preview-button-full-page.png): Переключиться на полноэкранный просмотр содержимого.

    ![значок кнопки предварительного просмотра](media/create-new-using-github/preview-button-side-by-side.png): Открывает страницу предварительный просмотр рядом с рабочей страницей рядом с ней.

2. Убедитесь, что ваша статья будет выглядеть так, как вы предполагаете.

    Убедившись, что все выглядит правильно, можно зафиксировать изменения и создать запрос на вытягивание для публикации.

### <a name="commit-your-changes"></a>Фиксация изменений

После того как текст будет выглядеть правильно, можно зафиксировать изменения в локальной версии репозитория.

#### <a name="to-commit-your-changes"></a>Фиксация изменений

- Откройте Git Bash и введите команды (по одной за раз, удалив необязательные теги):

    ```markdown
    OPTIONAL: git status

    git add .

    git commit -m “public comment about what change is”

    OPTIONAL: git pull upstream master

    git push origin <name_of_your_new_branch>

    ```

    Необязательная команда состояния Git показывает, какие файлы были изменены в рамках этой фиксации. Необязательный образец вышестоящего сводного сервера Git извлекает последние изменения содержимого из главной ветви MicrosoftDocs, синхронизируя локальное содержимое с основным главным содержимым. Это позволяет показывать любые потенциальные конфликты слияния заранее, чтобы их можно было исправить перед переходом на этап запроса на вытягивание.

### <a name="submit-a-pull-request-for-review-and-publication"></a>Отправка запроса на вытягивание для проверки и публикации

Завершив работу с этой статьей, вы должны получить утверждение от вашего модуля записи (подождите некоторое время) для публикации.

#### <a name="to-submit-your-pull-request"></a>Отправка запроса на вытягивание

1. Перейдите к https://github.com/MicrosoftDocs/windowsserverdocs-pr и выберите вкладку **запросы на вытягивание** .

2. В области **рецензенты** правой панели щелкните значок шестеренки, а затем введите псевдоним _виндовссерверконтент_ для проверки.

    Член псевдонима _виндовссерверконтент_ просматривает изменения или добавляет комментарии о том, что необходимо изменить, прежде чем можно будет выполнить слияние.

3. В комментарии введите **#sign-off** , чтобы рецензенты знали, что вы используете для просмотра и публикации. **#Sign** комментарий:

    - Обновляет метку для запроса на вытягивание от **Do-un-Merge** до **готового к слиянию**.

    - Позволяет псевдонимам и модулям записи узнавать, что вы готовы к рецензированию содержимого.

    - Позволяет администраторам понять, что после утверждения ваше содержимое готово к работе.

    >[!Important]
    >После добавления #sign комментария участник команды виндовссерверконтент будет просматривать текст и отправлять его в главную базу данных, чтобы он выйдет следующую запланированную публикацию в реальном времени (10:10:30 и 3:30 Weekday).
    >
    >Если вы не добавите #sign в качестве окончательного комментария к вашему запросу на вытягивание, содержимое останется в очереди без отправки в базу данных master и в конечном итоге в режим реального времени.

## <a name="related-information"></a>Связанные сведения

Дополнительные сведения о GitHub и языке Markdown см. в следующих статьях:

### <a name="git-concepts"></a>Основные понятия Git

- [Руководства по GitHub — введение в руководство по Git](https://guides.github.com/introduction/git-handbook/)

- [Руководства по GitHub — разветвление проектов](https://guides.github.com/activities/forking/)

- [Руководства GitHub — общие сведения о потоке GitHub](https://guides.github.com/introduction/flow/)

- [Изучение ветвления Git] (https://learngitbranching.js.org/ (Отлично подходит для визуальных ознакомлений!))

### <a name="markdown"></a>Markdown

- [Наши внутренние markdownные рекомендации](https://review.docs.microsoft.com/help/contribute/markdown-reference?branch=master)

- [Внешние, руководство по GitHub](https://www.markdowntutorial.com/)
