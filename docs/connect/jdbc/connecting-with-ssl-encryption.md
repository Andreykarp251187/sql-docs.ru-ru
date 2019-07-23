---
title: Подключение с помощью SSL-шифрования | Документация Майкрософт
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ec91fa8a-ab7e-4c1e-a05a-d7951ddf33b1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 209ced9fbf6d1ceb21ed4e5b6d686dd87eec0de2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67956806"
---
# <a name="connecting-with-ssl-encryption"></a>Соединение с помощью SSL-шифрования
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В примерах из этой статьи описывается использование свойств строки соединения, которые разрешают приложениям использовать шифрование SSL в приложении Java. Дополнительные сведения об этих новых свойствах строки соединения, например **encrypt**, **trustServerCertificate**, **trustStore**, **trustStorePassword** и **hostNameInCertificate**, см. в разделе [Задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Если свойство **encrypt** установлено в значение **true**, а свойство **trustServerCertificate** — в значение **true**, то драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] не будет проверять SSL-сертификат [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это обычно необходимо для того, чтобы разрешить соединения в тестовой среде, например когда у экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] есть лишь самозаверяющий сертификат.  
  
 В следующем примере кода показано, как можно задать свойство **trustServerCertificate** в строке подключения:  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true;trustServerCertificate=true";  
```  
  
 Если свойство **encrypt** установлено в значение **true**, а свойство **trustServerCertificate** — в значение **false**, то драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] будет проверять SSL-сертификат [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Проверка сертификата сервера является частью SSL-подтверждения и гарантирует, что для подключения выбран правильный сервер. Чтобы проверить сертификат сервера, при подключении необходимо явно предоставить доверенный материал с помощью свойств подключения **trustStore** и **trustStorePassword** или неявно, с помощью базового доверенного хранилища JVM по умолчанию.  
  
 Свойство **trustStore** указывает путь (включая имя файла) к файлу сертификата trustStore, который содержит список сертификатов, которым доверяет клиент. Свойство **trustStorePassword** задает пароль, используемый для проверки целостности данных trustStore. Дополнительные сведения об использовании хранилища доверия ВИРТУАЛЬНОЙ машины Java по умолчанию см. в разделе [Настройка клиента для шифрования SSL](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md).  
  
 В следующем примере кода показано, как в строке подключения можно задать свойства **trustStore** и **trustStorePassword**:  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword";  
```  
  
 Драйвер JDBC предоставляет дополнительное свойство, **hostNameInCertificate**, которое задает имя узла сервера. Значение этого свойства должно совпадать со значением свойства subject сертификата.  
  
 В следующем примере кода показано, как в строке подключения можно использовать свойство **hostNameInCertificate**:  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword" +  
     "hostNameInCertificate=hostName";  
```  
  
> [!NOTE]  
>  Кроме того, можно задать значение свойству подключения с помощью соответствующих методов **задания**, предоставляемых классом [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
 Если свойство **Encrypt** имеет значение **true** , а свойству **trustServerCertificate** присвоено значение **false** и если имя сервера в строке подключения не совпадает с именем сервера в SSL-сертификате, будет выдаваться следующая ошибка: Дата выпуска `The driver couldn't establish a secure connection to SQL Server by using Secure Sockets Layer (SSL) encryption. Error: "java.security.cert.CertificateException: Failed to validate the server name in a certificate during Secure Sockets Layer (SSL) initialization."`:. Начиная с версии 7,2, драйвер поддерживает сопоставление шаблонов с подстановочными знаками в крайней левой части имени сервера в SSL-сертификате.
## <a name="see-also"></a>См. также:  
 [Использование SSL-шифрования](../../connect/jdbc/using-ssl-encryption.md)   
 [Защита приложений драйвера JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
