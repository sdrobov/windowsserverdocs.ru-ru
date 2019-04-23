1.  Запустите [установки HgsServer](https://technet.microsoft.com/itpro/powershell/windows/hgsserver/install-hgsserver) для присоединения к домену и повысить уровень узла до контроллера домена.

    ```powershell
    $adSafeModePassword = ConvertTo-SecureString -AsPlainText '<password>' -Force

    $cred = Get-Credential 'relecloud\Administrator'

    Install-HgsServer -HgsDomainName 'bastion.local' -HgsDomainCredential $cred -SafeModeAdministratorPassword $adSafeModePassword -Restart
    ```

2.  Когда после перезагрузки сервера войдите в учетную запись администратора домена.

<!-- Appears twice in guarded-fabric-configure-additional-hgs-nodes.md 
-->