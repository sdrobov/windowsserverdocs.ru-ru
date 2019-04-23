Кроме того можно указать отпечаток, если вы хотите использовать собственный сертификат. Это может быть полезно в том случае, если вы хотите совместно использовать сертификат на нескольких компьютерах, или используйте сертификат, связанный с доверенным платформенным Модулем или аппаратный модуль безопасности. Ниже приведен пример создания сертификата привязкой доверенный платформенный модуль (который предотвращает его закрытый ключ украден и использован на другом компьютере и требуется только TPM 1.2):

```powersehll
$tpmBoundCert = New-SelfSignedCertificate -Subject “Host Key Attestation ($env:computername)” -Provider “Microsoft Platform Crypto Provider”
Set-HgsClientHostKey -Thumbprint $tpmBoundCert.Thumbprint
```


<!-- Appears in set-up-hgs-for-always-encrypted-in-sql-server.md and guarded-fabric-create-host-key.md
-->