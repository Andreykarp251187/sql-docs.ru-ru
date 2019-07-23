---
title: Настройка ключей постоянного шифрования с помощью PowerShell | Документация Майкрософт
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
ms.assetid: 3bdf8629-738c-489f-959b-2f5afdaf7d61
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a488f0b9255464573be68b03a73f837a77cd1db5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68050162"
---
# <a name="configure-always-encrypted-keys-using-powershell"></a>Настройка ключей постоянного шифрования с помощью PowerShell
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

    
В этой статье описаны действия по подготовке ключей постоянного шифрования с помощью [модуля SqlServer PowerShell](../../../relational-databases/scripting/sql-server-powershell-provider.md). PowerShell можно использовать для подготовки ключей постоянного шифрования [с разделением ролей и без разделения ролей](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md#KeyManagementRoles)с управлением пользователями, имеющими доступ к фактическим ключам шифрования в хранилище ключей и доступ к базе данных. 

Обзор процесса управления ключами постоянного шифрования, включая некоторые общие рекомендации, см. в разделе [Overview of Key Management for Always Encrypted (Общие сведения об управлении ключами для постоянного шифрования)](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md).
Сведения о начале работы с модулем SqlServer PowerShell для постоянного шифрования см. в разделе [Configure Always Encrypted using PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md)(Настройка постоянного шифрования с помощью PowerShell).


## <a name="KeyProvisionWithoutRoles"></a> Подготовка ключей без разделения ролей

В описанном здесь способе подготовки ключей не поддерживается разделение ролей между администраторами безопасности и администраторами баз данных. В некоторых шагах операции с физическими ключами объединены с операциями с метаданными ключей. Таким образом, этот метод подготовки ключей рекомендуется для организаций, использующих модель разработки и операций, или если база данных размещается в облаке и основная цель заключается в ограничении доступа администраторов облака (но не локальных администраторов баз данных) к конфиденциальным данным. Этот метод не рекомендуется использовать, если администраторы баз данных являются потенциальными злоумышленниками или если они не должны иметь доступ к конфиденциальным данным.

Перед выполнением действий, связанных с доступом к ключам с открытым текстом или хранилищу ключей (определены в столбце **Доступ к ключам с открытым текстом или хранилищу ключей** в таблице ниже), убедитесь, что среда PowerShell запущена на защищенном компьютере, отличном от компьютера с базой данных. Дополнительные сведения см. в разделе ***Security Considerations for Key Management***(Вопросы безопасности для управления ключами).


Задача  |Статья  |Доступ к ключам с открытым текстом или хранилищу ключей  |Доступ к базе данных   
---------|---------|---------|---------
Шаг 1. Создание главного ключа столбца в хранилище ключей.<br><br>**Примечание.** Этот шаг не поддерживается в модуле SqlServer PowerShell. Для выполнения этой задачи из командной строки используйте средства, поддерживаемые выбранным хранилищем ключей. |[Создание и хранение главных ключей столбцов (постоянное шифрование)](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md) | Да | нет     
Шаг 2.  Запуск среды PowerShell и импорт модуля SqlServer.  |   [Configure Always Encrypted using PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md)   |    нет    | нет         
Шаг 3.  Соединение с сервером и базой данных.     |     [Connect to a Database (Соединение с базой данных)](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md#connectingtodatabase)    |    нет     | Да         
Шаг 4.  Создание объекта *SqlColumnMasterKeySettings* , содержащего сведения о расположении главного ключа столбца. SqlColumnMasterKeySettings — это объект, который существует в памяти (PowerShell). Используйте командлет, поддерживаемый хранилищем ключей.   |     [New-SqlAzureKeyVaultColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlazurekeyvaultcolumnmasterkeysettings)<br><br>[New-SqlCertificateStoreColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcertificatestorecolumnmasterkeysettings)<br><br>[New-SqlCngColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcngcolumnmasterkeysettings)<br><br>[New-SqlCspColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcspcolumnmasterkeysettings)        |   нет      | нет         
Шаг 5.  Создание метаданных о главном ключе столбца в базе данных.      |    [New-SqlColumnMasterKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnmasterkey)<br><br>**Примечание.** На самом деле для создания метаданных ключа командлет выполняет инструкцию [CREATE COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-column-master-key-transact-sql.md) .|    нет     |    Да
Шаг 6.  Проверка подлинности в Azure, если главный ключ столбца хранится в хранилище ключей Azure. | [Add-SqlAzureAuthenticationContext](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/add-sqlazureauthenticationcontext)    |  Да   | нет         
Шаг 7.  Создание ключа шифрования столбца, его шифрование с помощью главного ключа столбца и создание метаданных ключа шифрования столбца в базе данных.     |    [New-SqlColumnEncryptionKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnencryptionkey)<br><br>**Примечание.** Используйте командлет, который внутренним образом создает и шифрует ключ шифрования столбца.<br><br>**Примечание.** На самом деле для создания метаданных ключа командлет выполняет инструкцию [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/create-column-encryption-key-transact-sql.md).  | Да | Да
  

## <a name="windows-certificate-store-without-role-separation-example"></a>Хранилище сертификатов Windows без разделения ролей (пример)

Этот скрипт — законченный пример создания главного ключа столбца, который является сертификатом в хранилище сертификатов Windows, создания и шифрования ключа шифрования столбца и создания метаданных ключа в базе данных SQL Server.


```
# Create a column master key in Windows Certificate Store.
$cert1 = New-SelfSignedCertificate -Subject "AlwaysEncryptedCert" -CertStoreLocation Cert:CurrentUser\My -KeyExportPolicy Exportable -Type DocumentEncryptionCert -KeyUsage DataEncipherment -KeySpec KeyExchange

# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Integrated Security = True"
$connection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection
$connection.ConnectionString = $connStr
$connection.Connect()
$server = New-Object Microsoft.SqlServer.Management.Smo.Server($connection)
$database = $server.Databases[$databaseName]

# Create a SqlColumnMasterKeySettings object for your column master key. 
$cmkSettings = New-SqlCertificateStoreColumnMasterKeySettings -CertificateStoreLocation "CurrentUser" -Thumbprint $cert1.Thumbprint

# Create column master key metadata in the database.
$cmkName = "CMK1"
New-SqlColumnMasterKey -Name $cmkName -InputObject $database -ColumnMasterKeySettings $cmkSettings


# Generate a column encryption key, encrypt it with the column master key and create column encryption key metadata in the database. 
$cekName = "CEK1"
New-SqlColumnEncryptionKey -Name $cekName  -InputObject $database -ColumnMasterKey $cmkName
```

## <a name="azure-key-vault-without-role-separation-example"></a>Хранилище ключей Azure без разделения ролей (пример)

Этот скрипт является законченным примером подготовки и настройки хранилища ключей Azure, создания главного ключа столбца в хранилище, создания и шифрования ключа шифрования столбца и создания метаданных ключа в базе данных Azure SQL.


```
# Create a column master key in Azure Key Vault.
Connect-AzAccount
$SubscriptionId = "<Azure SubscriptionId>"
$resourceGroup = "<resource group name>"
$azureLocation = "<datacenter location>"
$akvName = "<key vault name>"
$akvKeyName = "<key name>"
$azureCtx = Set-AzConteXt -SubscriptionId $SubscriptionId # Sets the context for the below cmdlets to the specified subscription.
New-AzResourceGroup -Name $resourceGroup -Location $azureLocation # Creates a new resource group - skip, if you desire group already exists.
New-AzKeyVault -VaultName $akvName -ResourceGroupName $resourceGroup -Location $azureLocation # Creates a new key vault - skip if your vault already exists.
Set-AzKeyVaultAccessPolicy -VaultName $akvName -ResourceGroupName $resourceGroup -PermissionsToKeys get, create, delete, list, update, import, backup, restore, wrapKey,unwrapKey, sign, verify -UserPrincipalName $azureCtx.Account
$akvKey = Add-AzureKeyVaultKey -VaultName $akvName -Name $akvKeyName -Destination "Software"

# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database (Azure SQL database).
$serverName = "<Azure SQL server name>.database.windows.net"
$databaseName = "<database name>"
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Authentication = Active Directory Integrated"
$connection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection
$connection.ConnectionString = $connStr
$connection.Connect()
$server = New-Object Microsoft.SqlServer.Management.Smo.Server($connection)
$database = $server.Databases[$databaseName] 

# Create a SqlColumnMasterKeySettings object for your column master key. 
$cmkSettings = New-SqlAzureKeyVaultColumnMasterKeySettings -KeyURL $akvKey.ID

# Create column master key metadata in the database.
$cmkName = "CMK1"
New-SqlColumnMasterKey -Name $cmkName -InputObject $database -ColumnMasterKeySettings $cmkSettings

# Authenticate to Azure
Add-SqlAzureAuthenticationContext -Interactive

# Generate a column encryption key, encrypt it with the column master key and create column encryption key metadata in the database. 
$cekName = "CEK1"
New-SqlColumnEncryptionKey -Name $cekName -InputObject $database -ColumnMasterKey $cmkName
```

## <a name="cngksp-without-role-separation-example"></a>CNG/KSP без разделения ролей (пример)

Этот скрипт является законченным примером создания главного ключа столбца в хранилище ключей, реализующем API CNG, создания и шифрования ключа шифрования столбца и создания метаданных ключа в базе данных SQL Server.

В примере используется хранилище ключей с ПО поставщика хранилища ключей Microsoft Software Key Storage Provider. Этот пример можно изменить для использования другого хранилища, например аппаратного модуля безопасности. Для этого необходимо надлежащим образом установить и запустить на компьютере поставщик хранилища ключей (KSP), реализующий CNG. Строку "Microsoft Software Key Storage Provider" нужно будет изменить на имя KSP устройства.


```
# Create a column master key in a key store that has a CNG provider, a.k.a key store provider (KSP).
$cngProviderName = "Microsoft Software Key Storage Provider" # If you have an HSM, you can use a KSP for your HSM instead of a Microsoft KSP
$cngAlgorithmName = "RSA"
$cngKeySize = 2048 # Recommended key size for Always Encrypted column master keys
$cngKeyName = "AlwaysEncryptedKey" # Name identifying your new key in the KSP
$cngProvider = New-Object System.Security.Cryptography.CngProvider($cngProviderName)
$cngKeyParams = New-Object System.Security.Cryptography.CngKeyCreationParameters
$cngKeyParams.provider = $cngProvider
$cngKeyParams.KeyCreationOptions = [System.Security.Cryptography.CngKeyCreationOptions]::OverwriteExistingKey
$keySizeProperty = New-Object System.Security.Cryptography.CngProperty("Length", [System.BitConverter]::GetBytes($cngKeySize), [System.Security.Cryptography.CngPropertyOptions]::None);
$cngKeyParams.Parameters.Add($keySizeProperty)
$cngAlgorithm = New-Object System.Security.Cryptography.CngAlgorithm($cngAlgorithmName)
$cngKey = [System.Security.Cryptography.CngKey]::Create($cngAlgorithm, $cngKeyName, $cngKeyParams)

# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Integrated Security = True"
$connection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection
$connection.ConnectionString = $connStr
$connection.Connect()
$server = New-Object Microsoft.SqlServer.Management.Smo.Server($connection)
$database = $server.Databases[$databaseName]

# Create a SqlColumnMasterKeySettings object for your column master key. 
$cmkSettings = New-SqlCngColumnMasterKeySettings -CngProviderName $cngProviderName -KeyName $cngKeyName

# Create column master key metadata in the database.
$cmkName = "CMK1"
New-SqlColumnMasterKey -Name $cmkName -InputObject $database -ColumnMasterKeySettings $cmkSettings

# Generate a column encryption key, encrypt it with the column master key and create column encryption key metadata in the database. 
$cekName = "CEK1"
New-SqlColumnEncryptionKey -Name $cekName -InputObject $database -ColumnMasterKey $cmkName
```

## <a name="KeyProvisionWithRoles"></a> Подготовка ключей с разделением ролей

В этом разделе описано, как настроить шифрование, когда у администраторов безопасности нет доступа к базе данных, а у администраторов баз данных — доступа к хранилищу ключей или ключам с обычным текстом.


### <a name="security-administrator"></a>Администратор безопасности

Перед выполнением действий, предполагающих доступ к ключам с открытым текстом или хранилищу ключей (определены в столбце **Доступ к ключам с открытым текстом или хранилищу ключей** в таблице ниже), убедитесь, что выполнены указанные далее условия.
1.  Среда PowerShell используется на защищенном компьютере (и не на компьютере с базой данных).
2.  Администраторы баз данных в вашей организации не имеют доступа к компьютеру (что противоречило бы концепции разделения ролей).

Дополнительные сведения см. в разделе [Security Considerations for Key Management](overview-of-key-management-for-always-encrypted.md#security-considerations-for-key-management)(Вопросы безопасности для управления ключами).


Задача  |Статья  |Доступ к ключам с открытым текстом или хранилищу ключей  |Доступ к базе данных  
---------|---------|---------|---------
Шаг 1. Создание главного ключа столбца в хранилище ключей.<br><br>**Примечание.** Этот шаг не поддерживается в модуле SqlServer. Для выполнения этой задачи из командной строки используйте средства, поддерживаемые выбранным хранилищем ключей.     | [Создание и хранение главных ключей столбцов (постоянное шифрование)](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md)  |    Да    | нет 
Шаг 2.  Запуск сеанса PowerShell и импорт модуля SqlServer.      |     [Импорт модуля SqlServer](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md#importsqlservermodule)     | нет | нет         
Шаг 3.  Создание объекта *SqlColumnMasterKeySettings* , содержащего сведения о расположении главного ключа столбца. *SqlColumnMasterKeySettings* — это объект, который существует в памяти (PowerShell). Используйте командлет, поддерживаемый хранилищем ключей. |      [New-SqlAzureKeyVaultColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlazurekeyvaultcolumnmasterkeysettings)<br><br>[New-SqlCertificateStoreColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcertificatestorecolumnmasterkeysettings)<br><br>[New-SqlCngColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcngcolumnmasterkeysettings)<br><br>[New-SqlCspColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcspcolumnmasterkeysettings)   | нет         | нет         
Шаг 4.  Проверка подлинности в Azure, если главный ключ столбца хранится в хранилище ключей Azure. |    [Add-SqlAzureAuthenticationContext](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/add-sqlazureauthenticationcontext)    |Да|нет         
Шаг 5.  Создание ключа шифрования столбца, его шифрование с помощью главного ключа столбца для формирования зашифрованного значения ключа шифрования столбца.     |   [New-SqlColumnEncryptionKeyEncryptedValue](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnencryptionkeyencryptedvalue)     |    Да    | нет        
Шаг 6.  Предоставление администратору баз данных информации о расположении главного ключа столбца (имени поставщика и пути к главному ключу столбца) и зашифрованного значения ключа шифрования.  | См. примеры ниже.        |   нет      | нет         

### <a name="dba"></a>Администратор баз данных 

Администраторы баз данных используют сведения, полученные от администратора безопасности (см. шаг 6 выше), для создания метаданных ключей постоянного шифрования в базе данных и управления ими.

Задача  |Статья  |Доступ к ключам с открытым текстом  |Доступ к базе данных   
---------|---------|---------|---------
Шаг 1.  Получение расположения главного ключа столбца и зашифрованного значения ключа шифрования столбца от администратора безопасности. |См. примеры ниже. | нет | нет
Шаг 2.  Запуск среды PowerShell и импорт модуля SqlServer.  | [Configure Always Encrypted using PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md)  | нет | нет
Шаг 3.  Соединение с сервером и базой данных. | [Соединение с базой данных](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md#connectingtodatabase) | нет | Да
Шаг 4.  Создание объекта SqlColumnMasterKeySettings, содержащего сведения о расположении главного ключа столбца. SqlColumnMasterKeySettings — это объект, который существует в памяти. | New-SqlColumnMasterKeySettings | нет | нет
Шаг 5. Создание метаданных о главном ключе столбца в базе данных. | [New-SqlColumnMasterKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnmasterkey)<br>**Примечание.** На самом деле для создания метаданных главного ключа столбца командлет выполняет инструкцию [CREATE COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-column-master-key-transact-sql.md) . | нет | Да
Шаг 6. Создание метаданных ключа шифрования столбца в базе данных. | New-SqlColumnEncryptionKey<br>**Примечание.** Администраторы баз данных используют командлет, который создает только метаданные ключа шифрования столбца.<br>На самом деле для создания метаданных ключа шифрования столбца командлет выполняет инструкцию [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/create-column-encryption-key-transact-sql.md) . | нет | Да
  
## <a name="windows-certificate-store-with-role-separation-example"></a>Хранилище сертификатов Windows с разделением ролей (пример)

### <a name="security-administrator"></a>Администратор безопасности


```
# Create a column master key in Windows Certificate Store.
$storeLocation = "CurrentUser"
$certPath = "Cert:" + $storeLocation + "\My"
$cert = New-SelfSignedCertificate -Subject "AlwaysEncryptedCert" -CertStoreLocation $certPath -KeyExportPolicy Exportable -Type DocumentEncryptionCert -KeyUsage DataEncipherment -KeySpec KeyExchange

# Import the SqlServer module
Import-Module "SqlServer"

# Create a SqlColumnMasterKeySettings object for your column master key. 
$cmkSettings = New-SqlCertificateStoreColumnMasterKeySettings -CertificateStoreLocation "CurrentUser" -Thumbprint $cert.Thumbprint

# Generate a column encryption key, encrypt it with the column master key to produce an encrypted value of the column encryption key.
$encryptedValue = New-SqlColumnEncryptionKeyEncryptedValue -TargetColumnMasterKeySettings $cmkSettings

# Share the location of the column master key and an encrypted value of the column encryption key with a DBA, via a CSV file on a share drive
$keyDataFile = "Z:\keydata.txt"
"KeyStoreProviderName, KeyPath, EncryptedValue" > $keyDataFile
$cmkSettings.KeyStoreProviderName + ", " + $cmkSettings.KeyPath + ", " + $encryptedValue >> $keyDataFile

# Read the key data back to verify
$keyData = Import-Csv $keyDataFile
$keyData.KeyStoreProviderName
$keyData.KeyPath
$keyData.EncryptedValue 
```

### <a name="dba"></a>Администратор баз данных

```
# Obtain the location of the column master key and the encrypted value of the column encryption key from your Security Administrator, via a CSV file on a share drive.
$keyDataFile = "Z:\keydata.txt"
$keyData = Import-Csv $keyDataFile

# Import the SqlServer module
Import-Module "SqlServer"

# Connect to your database.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Integrated Security = True"
$connection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection
$connection.ConnectionString = $connStr
$connection.Connect()
$server = New-Object Microsoft.SqlServer.Management.Smo.Server($connection)
$database = $server.Databases[$databaseName]

# Create a SqlColumnMasterKeySettings object for your column master key. 
$cmkSettings = New-SqlColumnMasterKeySettings -KeyStoreProviderName $keyData.KeyStoreProviderName -KeyPath $keyData.KeyPath

# Create column master key metadata in the database.
$cmkName = "CMK1"
New-SqlColumnMasterKey -Name $cmkName -InputObject $database -ColumnMasterKeySettings $cmkSettings

# Generate a  column encryption key, encrypt it with the column master key and create column encryption key metadata in the database. 
$cekName = "CEK1"
New-SqlColumnEncryptionKey -Name $cekName -InputObject $database -ColumnMasterKey $cmkName -EncryptedValue $keyData.EncryptedValue
```  
 
## <a name="next-steps"></a>Next Steps    

- [Настройка шифрования столбцов с помощью PowerShell](../../../relational-databases/security/encryption/configure-column-encryption-using-powershell.md)    
- [Смена ключей постоянного шифрования с помощью PowerShell](../../../relational-databases/security/encryption/rotate-always-encrypted-keys-using-powershell.md)
    
## <a name="additional-resources"></a>Дополнительные ресурсы    
    
- [Общие сведения об управлении ключами для постоянного шифрования](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
- [Настройка постоянного шифрования с помощью PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md)
- [Always Encrypted (ядро СУБД)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Постоянное шифрование (разработка клиентских приложений)](../../../relational-databases/security/encryption/always-encrypted-client-development.md)
- [Блог о постоянном шифровании](https://blogs.msdn.microsoft.com/sqlsecurity/tag/always-encrypted/)

