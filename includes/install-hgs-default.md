Служба защиты узла должен быть установлен в отдельном лесу Active Directory.
Убедитесь, что машина HGS **не** присоединен к домену, перед запуском и войдите в систему как локальный компьютер правами.

Выполните следующие команды для установки службы защиты узла и настройки своего домена.
Здесь пароль будет применяться только к пароль режима восстановления служб каталогов для Active Directory; он будет *не* изменить пароль для входа в учетную запись администратора.
Может предоставлять любое доменное имя по своему выбору - HgsDomainName.

```powershell
$adminPassword = ConvertTo-SecureString -AsPlainText '<password>' -Force

Install-HgsServer -HgsDomainName 'bastion.local' -SafeModeAdministratorPassword $adminPassword -Restart
```

<!-- Appears in guarded-fabric-install-hgs-default.md and set-up-hgs-for-always-encrypted-in-sql-server.md
-->
