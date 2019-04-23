Существует много способов настроить разрешение имен для домена fabric. Один простой способ — настроить сервер условной пересылки зоны в DNS для структуры. Чтобы настроить эту зону, выполните следующие команды в консоль Windows PowerShell с повышенными привилегиями на сервере DNS fabric. Замените имена и адреса в синтаксисе Windows PowerShell ниже, при необходимости для вашей среды. Добавление главных серверов для дополнительных узлов HGS.

```
Add-DnsServerConditionalForwarderZone -Name 'bastion.local' -ReplicationScope "Forest" -MasterServers <IP addresses of HGS server>
```

<!-- Appears in guarded-fabric-configuring-fabric-dns-ad.md and guarded-fabric-configuring-fabric-dns.md and set-up-hgs-for-always-encrypted-in-sql-server.md
-->    