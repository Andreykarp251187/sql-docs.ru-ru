---
title: SQLDriverConnect | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDriverConnect function
ms.assetid: a1e38e2c-3a97-42d1-9c45-a0ca3282ffd1
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1e8b52f4940a60e464f9ea4405ddd421bb9b48d4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68035639"
---
# <a name="sqldriverconnect"></a>SQLDriverConnect
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определяет атрибуты соединения, которые заменяют или расширяют ключевые слова строки соединения. Некоторые ключевые слова строки соединения имеют значения по умолчанию, заданные в драйвере ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Список слов, доступных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента, см. в разделе [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] атрибуты соединения и поведении драйвера по умолчанию, см. в разделе [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
 Описание ключевых слов строки подключения, которые являются допустимыми для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, см. в разделе [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Когда **SQLDriverConnect**_DriverCompletion_ значение параметра является SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE или SQL_DRIVER_COMPLETE_REQUIRED, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента Получает значения ключевых слов из отображенного диалогового. Если значение ключевого слова передается в строке соединения и пользователь не изменил значение в диалоговом окне, драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует значение из строки соединения. Если значение не определено в строке соединения, а пользователь не присваивает его в диалоговом окне, драйвер использует значение по умолчанию.  
  
 **SQLDriverConnect** должен быть задан допустимый *WindowHandle* при любой *DriverCompletion* значение требует (или, может потребовать) отображения диалогового окна соединения драйвера. Недопустимый дескриптор возвращает ошибку SQL_ERROR.  
  
 Укажите ключевое слово DRIVER или DSN. Драйвер ODBC использует крайнее левое из этих ключевых слов и пропускает другое, если указаны оба. Если ДРАЙВЕР указан или является самым левым узлом из них и **SQLDriverConnect**_DriverCompletion_ имеет значение SQL_DRIVER_NOPROMPT, ключевое слово SERVER и соответствующее значение не требуются.  
  
 Если задано значение SQL_DRIVER_NOPROMPT, необходимо указать ключевые слова проверки подлинности пользователя вместе с их значениями. Драйвер обеспечивает наличие строки «Trusted_Connection=yes» или обоих ключевых слов UID и PWD.  
  
 Если *DriverCompletion* имеет значение SQL_DRIVER_NOPROMPT или SQL_DRIVER_COMPLETE_REQUIRED, а язык или база данных получен из строки подключения и недопустимы, **SQLDriverConnect**возвращает ошибку SQL_ERROR.  
  
 Если *DriverCompletion* имеет значение SQL_DRIVER_NOPROMPT или SQL_DRIVER_COMPLETE_REQUIRED, а язык или база данных поступают из определений источников данных ODBC и недопустимы, **SQLDriverConnect**  использует язык по умолчанию или базы данных для заданного идентификатора пользователя и возвращает значение SQL_SUCCESS_WITH_INFO.  
  
 Если *DriverCompletion* значение параметра является SQL_DRIVER_COMPLETE или SQL_DRIVER_PROMPT, а если язык или база данных является недопустимым, **SQLDriverConnect** повторно отображает диалоговое окно.  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a>Поддержка высокого уровня доступности и аварийного восстановления SQLDriverConnect  
 Дополнительные сведения об использовании **SQLDriverConnect** для подключения к [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] кластера, см. в разделе [SQL Server Native Client Support для высокого уровня доступности и аварийного восстановления](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a>Поддержка SQLDriverConnect для имен участников-служб (SPN)  
 SQLDDriverConnect будет использовать имя входа ODBC, включенном приглашении диалоговое окно. Это позволяет ввести имена участников-служб как для основного сервера, так и для его партнера по обеспечению отработки отказа.  
  
 SQLDriverConnect будет принимать новые ключевые слова строки подключения **ServerSPN** и **FailoverPartnerSPN**, а также распознает новые атрибуты соединения SQL_COPT_SS_SERVER_SPN и SQL_COPT_SS_ FAILOVER_PARTNER_SPN.  
  
 Если значение атрибута соединения задано более одного раза, приоритет получает программно установленное значение, а не значение в DSN или строке соединения. Значение DSN имеет приоритет над значением в строке соединения.  
  
 При открытии соединения собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задает SQL_COPT_SS_MUTUALLY_AUTHENTICATED и SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD метод проверки подлинности, используемый для открытия соединения.  
  
 Дополнительные сведения об именах SPN см. в разделе [имена участников-служб &#40;имена участников-служб&#41; в клиентских соединениях &#40;ODBC&#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="examples"></a>Примеры  
 В следующем вызове показан наименьшего объема данных, необходимых для **SQLDriverConnect**:  
  
```  
SQLDriverConnect(hdbc, hwnd,  
    (SQLTCHAR*) TEXT("DRIVER={SQL Server Native Client 10};"), SQL_NTS, szOutConn,  
    MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
```  
  
 Следующей строке соединения показан минимальный объем необходимых данных при *DriverCompletion* имеет значение SQL_DRIVER_NOPROMPT:  
  
```  
"DSN=Human Resources;Trusted_Connection=yes"  
  
"FILEDSN=HR_FDSN;Trusted_Connection=yes"  
  
"DRIVER={SQL Server Native Client 10};SERVER=(local);Trusted_Connection=yes"  
```  
  
## <a name="see-also"></a>См. также  
 [Функция SQLDriverConnect](https://go.microsoft.com/fwlink/?LinkId=59340)   
 [Сведения о реализации API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SET ANSI_NULLS (Transact-SQL)](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING (Transact-SQL)](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md)  
  
  
