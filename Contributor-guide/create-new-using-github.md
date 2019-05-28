---
title: Создание новой статьи о Windows Server, с помощью GitHub и Visual Studio Code
description: Как создать новые статьи, относящиеся к серверу Windows, с помощью GitHub и Visual Studio Code, как сотрудник Microsoft.
author: eross-msft
ms.author: lizross
ms.date: 05/02/2019
ms.openlocfilehash: d75bf135266a4783ab2617977b344782cea679ef
ms.sourcegitcommit: 29ad32b9dea298a7fe81dcc33d2a42d383018e82
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65624560"
---
# <a name="create-new-windows-server-articles-using-github-and-visual-studio-code"></a>Создание новой статьи о Windows Server, с помощью GitHub и Visual Studio Code

Существует два разных расположениях, где мы храним техническое содержимое Windows Server. Одно из расположений является общим (windowsserverdocs), а другой — частный (windowsserverdocs-pr). Кто вы определяет расположение, где вас есть доступ.

- **Я являюсь сотрудником корпорации Майкрософт.** Как сотрудник Microsoft у вас есть параметры, в зависимости от того, что вы пытаетесь сделать:

    - **Создание совершенно новой статьи.** Создание совершенно новой статьи, необходимо создать и настроить учетную запись GitHub и средства, разветвлять и клонировать репозиторий windowsserverdocs-pr, установки удаленной ветви, создать статью и наконец, создайте новый запрос на включение внесенных изменений для утверждения и публикации. Эти инструкции прочтите эту статью.

    - **Внести значительные изменения в существующую статью.** Чтобы внести существенные изменения в существующую статью, можно следуйте инструкциям в [изменение существующей статьи Windows Server с помощью GitHub и Visual Studio Code](edit-existing-using-github.md) статьи.

    - **Внести незначительные изменения в существующую статью.** Чтобы внести незначительные изменения в существующую статью, можно следуйте инструкциям в [обновления существующей статьи о Windows Server, с помощью веб-браузер и GitHub](github-browser-updates.md) статьи.

- **Я не являюсь сотрудником корпорации Майкрософт.** Как сотрудник сторонних разработчиков вы должны внести свой вклад к общедоступному расположению. Сведения о том, как это сделать, см. в разделе [участвующая в технической документации Windows Server](https://github.com/MicrosoftDocs/windowsserverdocs/blob/master/CONTRIBUTING.md) статьи.

## <a name="prerequisites"></a>Предварительные требования

Перед началом работы в репозитории, необходимо создать и настроить учетную запись GitHub, Настройка двухфакторной проверки подлинности, установить и настроить все необходимые средства. Если вы сделали это, можно перейти вниз к [разветвление в репозитории разделе](#fork-the-repository) этой статьи.

1. [Создание профиля и учетной записи GitHub](https://review.docs.microsoft.com/help/contribute/contribute-get-started-setup-github?branch=master#create-a-github-account-and-set-up-your-profile)

2. [Привяжите свою учетную запись для учетной записи Майкрософт и организаций Microsoft или MicrosoftDocs](https://review.docs.microsoft.com/help/contribute/contribute-get-started-setup-github?branch=master#link-your-github-and-microsoft-accounts)

3. [Включить двухфакторную проверку](https://review.docs.microsoft.com/help/contribute/contribute-get-started-setup-github?branch=master#enable-two-factor-authentication-and-create-an-access-token)

4. [Авторизация системы сборки для доступа к учетной записи GitHub](https://review.docs.microsoft.com/help/contribute/contribute-get-started-setup-github?branch=master#authorize-the-ops-build-system-to-access-your-github-account)

5. [Установка Visual Studio Code](https://review.docs.microsoft.com/help/contribute/contribute-get-started-setup-tools?branch=master#install-visual-studio-code)

6. [Установите GitHub и его средства](https://review.docs.microsoft.com/help/contribute/contribute-get-started-setup-tools?branch=master#install-git-client-tools)

7. [Установка пакета создания документации](https://review.docs.microsoft.com/help/contribute/contribute-get-started-setup-tools?branch=master#install-the-docs-authoring-pack)

## <a name="set-up-your-own-version-of-the-repo"></a>Настроить собственную версию репозитория

После создания и настройки учетной записи GitHub и средства, можно создать личную версию репозитория. Это, где вы создадите ветвей и внесите необходимые изменения.

### <a name="fork-the-repository"></a>Выполните разветвление репозитория.

Требуется локальной копии исходных файлов, чтобы вы могли создавать запросы на Вытягивание из вилки в репозитории рабочей.

#### <a name="to-fork-the-repository"></a>Чтобы создать разветвление репозитория

1. Войдите свою учетную запись GitHub и перейти к https://github.com/microsoftdocs/windowsserverdocs-pr.

2. Выберите **вилки**.

    ![Кнопка вилки, выделенным на странице](media/create-new-using-github/fork-button.png)

3. Выберите свою учетную запись GitHub как расположение вилки.

    ![Кнопка вилки, выделенным на странице](media/create-new-using-github/fork-location.png)

### <a name="clone-the-repository"></a>Клонируйте репозиторий.

Вам необходимо клонировать репозиторий get локальную копию репозитория на локальном устройстве.

#### <a name="to-clone-the-repository"></a>Чтобы клонировать репозиторий

1. Перейдите к https://github.com/settings/developers, а затем выберите **личные маркеры доступа** в левой области.

2. Выберите **создать новый токен**, назовите срок действия токена, понятным и уникальным, выберите все доступные области и выберите **создать токен**.

3. Скопируйте маркер и поместите его в безопасном месте. Он потребуется для остальной части процесса, и после выхода из страницы, вы не сможете вернуться к нему.

4. Откройте Git Bash команды и измените каталоги на место для хранения репозитория. Мы рекомендуем использовать, `C:\users\<your_name>\GitHub`.

5. Введите следующие команды, с помощью соответствующей информацией, поочередно, клонирование репозитория и настроить ваши Удаленные ветви:

    ```markdown

    git clone https://<your_github_username>:<your_personal_access_token>@github.com/<your_github_username>/windowsserverdocs-pr.git

    cd windowsserverdocs-pr

    git remote add upstream https://<your_github_username>:<your_personal_access_token>@github.com/MicrosoftDocs/windowsserverdocs-pr.git

    git fetch upstream master
    ```

6. Выполните следующую команду, чтобы убедиться в правильной настройке удаленного репозитория:

    `git remote -v`

7. Вы увидите нечто вроде эти выходные данные:

    ```markdown
    $ git remote -v

    origin https://github.com/<your_github_username>/windowsserverdocs-pr.git (fetch)
    origin https://github.com/<your_github_username>/windowsserverdocs-pr.git (push)
    upstream https://github.com/MicrosoftDocs/windowsserverdocs-pr.git (fetch)
    upstream https://github.com/MicrosoftDocs/windowsserverdocs-pr.git (push)
    ```

    Если удаленный выходных данных выглядит следующим образом, вы можете повторить попытку, запустив первый `git remote remove upstream`.

## <a name="create-a-branch-and-a-new-article"></a>Создание ветви и новая статья

Выполните следующие действия для создания статьи.

### <a name="create-a-new-branch-and-a-new-file"></a>Создайте новую ветвь и новый файл

Перед началом работы на содержимое, необходимо создать новую ветвь в локальном репозитории.

#### <a name="to-create-a-new-branch-in-git-bash"></a>Чтобы создать новую ветвь в Git Bash

- Откройте Git Bash и введите команды (по одному за раз):

    ```markdown
    cd windowsserverdocs-pr

    git checkout –B <name_of_your_new_branch>

    git push origin <name_of_your_new_branch>
    ```

    >[!Note]
    >Мы настоятельно рекомендуем именования ветви, что-то очевидным и уникальным, его можно найти попытку позже.

    После завершения команды, которую вы в новой ветви и Готово для создания нового файла. Необходимо изменить в репозиторий windowsserverdocs-pr один раз для каждого экземпляра Git Bash. Если вы закроете Git Bash, необходимо будет снова измените каталоги, открыв его.

#### <a name="to-create-a-new-file-in-your-branch"></a>Чтобы создать новый файл в ветви

1. Откройте проводник Windows, перейдите в каталог GitHub и создать новый текстовый файл в структуре папок. Имя файла должен быть все строчные и разделенные дефисами. Например _what — windows-server.md_.

     Необходимо также изменить расширение файла из .txt. md. В сообщении об ошибке, которое отображается, выберите **Да** для сохранения файла с новым расширением.

2. Откройте Visual Studio Code и перейдите к **файл**выберите **открыть папку**, а затем перейдите в расположение GitHub файла, созданного на шаге 1.

3. Из **Explorer** области, выберите новый файл.

4. Добавление текста на страницу, а затем выберите **файл** > **Сохранить**.

### <a name="preview-your-text"></a>Предварительный просмотр текста

После добавления текста в новый файл, необходимо предварительным просмотром изменений, чтобы убедиться в правильности их отображения.

#### <a name="to-preview-your-text"></a>Для предварительного просмотра текста

1. В Visual Studio Code, выберите один из **предварительной версии** кнопки в правом верхнем углу.

    ![значок кнопки предварительного просмотра](media/create-new-using-github/preview-button-full-page.png): Переключение в режиме полностраничного Предварительный просмотр содержимого.

    ![значок кнопки предварительного просмотра](media/create-new-using-github/preview-button-side-by-side.png): Откроется страница предварительного просмотра рядом со страницей вашей работы, side-by-side.

2. Убедитесь, что статья выглядит, как предполагается, что для поиска.

    После вы точно знаете, что оно установлено правильно, можно зафиксировать изменения и создать запрос на Вытягивание для публикации.

### <a name="commit-your-changes"></a>Фиксация изменений

После внесения правильно ли текст, можно зафиксировать изменения в локальную версию репозитория.

#### <a name="to-commit-your-changes"></a>Чтобы зафиксировать изменения

- Откройте Git Bash и введите команды (по одному за раз, удаление НЕОБЯЗАТЕЛЬНЫХ тегов):

    ```markdown
    OPTIONAL: git status

    git add .

    git commit -m “public comment about what change is”

    OPTIONAL: git pull upstream master

    git push origin <name_of_your_new_branch>

    ```

    Команда состояния необязательно git рассказывается о том, какие файлы были изменены в ходе этой фиксации. Необязательный git pull вышестоящего master переносит вниз содержимого последние изменения из главной ветви MicrosoftDocs, синхронизация локального содержимого с помощью основного содержимого главной. Это помогает Показать возможные конфликты слияния заранее, поэтому вы можете исправить их, прежде чем перейти к этапу запроса на Вытягивание.

### <a name="submit-a-pull-request-for-review-and-publication"></a>Отправить запрос на Вытягивание для просмотра и публикации

После завершения вашу статью, необходимо получить утверждение из записи (Разрешить некоторое время) для публикации.

#### <a name="to-submit-your-pull-request"></a>Чтобы отправить запрос на включение внесенных изменений

1. Перейдите к https://github.com/MicrosoftDocs/windowsserverdocs-pr и выберите **запросы на Вытягивание** вкладки.

2. В **рецензенты** части области справа щелкните значок шестеренки, а затем введите _windowsservercontent_ псевдоним для проверки.

    Является членом _windowsservercontent_ псевдоним будет просмотреть изменения или добавлять комментарии о том, что, которые должны быть изменены, прежде чем слияние может произойти.

3. Тип **#sign-off** в комментарии, чтобы рецензенты хорошо знакомы вы передаете для просмотра и публикации. **#Sign-off** комментарий:

    - Обновляет метку для запроса на Вытягивание из **not слияния** для **все готово для объединения**.

    - Позволяет псевдоним и понять, что теперь, чтобы просмотреть содержимое записи.

    - Позволяет администраторам знать, что после утверждения содержимого Готово go live.

    >[!Important]
    >Добавив комментарий #sign-off, член группы windowsservercontent прочтите текст и передаст его освоить, поэтому он будет передан с следующего запланированного публикации в реальном времени (10:30 по и 3:30 по будням).
    >
    >Если вы не добавите #sign-off как окончательный комментарий в запрос на Вытягивание, содержимое будет оставаться в очереди без отправляется в главную ветвь и в конечном счете жизни.

## <a name="related-information"></a>Связанные сведения

Дополнительные сведения о GitHub и языке разметки markdown см. в разделе:

### <a name="git-concepts"></a>Основные понятия Git

- [Общие сведения о руководстве руководства по GitHub-Git](https://guides.github.com/introduction/git-handbook/)

- [Руководства по разветвление GitHub проектов](https://guides.github.com/activities/forking/)

- [Руководства по GitHub-понимание поток GitHub](https://guides.github.com/introduction/flow/)

- [Узнайте, ветвление Git](https://learngitbranching.js.org/ (отлично подходят для визуального учеников!))

### <a name="markdown"></a>Markdown

- [Наше руководство внутреннего markdown](https://review.docs.microsoft.com/help/contribute/markdown-reference?branch=master)

- [Внешний, учебник по GitHub](https://www.markdowntutorial.com/)
