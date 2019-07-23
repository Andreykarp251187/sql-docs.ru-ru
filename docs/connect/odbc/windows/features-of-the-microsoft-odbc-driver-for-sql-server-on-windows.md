---
title: Функции Microsoft ODBC Driver for SQL Server в Windows | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8088334f4bc9cfd03c23af654fbef9eb478aa9a3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989449"
---
# <a name="features-of-the-microsoft-odbc-driver-for-sql-server-on-windows"></a>Функции Microsoft ODBC Driver for SQL Server в Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

    
## <a name="microsoft-odbc-driver-131-for-sql-server-on-windows"></a>Драйвер Microsoft ODBC Driver 13.1 for SQL Server в Windows

Драйвер ODBC 13,1 для SQL Server содержит все функции предыдущей версии (11) и добавляет поддержку проверки подлинности Always Encrypted и Azure Active Directory при использовании в сочетании с Microsoft SQL Server 2016.  
  
Функция Always Encrypted позволяет клиентам шифровать конфиденциальные данные в клиентских приложениях, не раскрывая ключи шифрования для SQL Server. Драйвер с поддержкой Always Encrypted, установленный на клиентском компьютере, реализует это за счет автоматического шифрования и расшифровки конфиденциальных данных в клиентском приложении SQL Server. Драйвер шифрует данные из конфиденциальных столбцов перед их передачей в SQL Server и автоматически переписывает запросы, чтобы сохранить семантику приложения. Аналогичным образом драйвер прозрачно расшифровывает данные, хранящиеся в столбцах зашифрованной базы данных, которые содержатся в результатах запроса. Дополнительные сведения см. в статье [Использование функции Always Encrypted с драйвером ODBC](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md).
 
Azure Active Directory позволяет пользователям, администраторам баз данных и приложениям использовать проверку подлинности Azure Active Directory в качестве механизма подключения к База данных SQL Microsoft Azure и Microsoft SQL Server 2016 с помощью удостоверений в Azure Active Directory (Azure AD ). Дополнительные сведения см. в статьях [использование Azure Active Directory с драйвером ODBC](../../../connect/odbc/using-azure-active-directory.md)и [Подключение к базе данных SQL или ХРАНИЛИЩу данных SQL с помощью проверки подлинности Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).   
  
## <a name="microsoft-odbc-driver-11-for-sql-server-on-windows"></a>Драйвер Microsoft ODBC 11 для SQL Server в Windows  

Драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] содержит все функциональные возможности драйвера ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, который входит в состав [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]. Дополнительные сведения см. в статье [Программирование SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md). Драйвер ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client основан на драйвере ODBC, который входит в состав операционной системы Windows. Дополнительные сведения см. в статье [Пакет SDK компонентов доступа к данным Windows DAC](https://msdn.microsoft.com/library/aa968814(VS.85).aspx).  
  
Этот выпуск драйвера ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] содержит следующие новые функции:  
  
### <a name="bcpexe--l-option-for-specifying-a-login-timeout"></a>параметр bcp. exe-l для указания времени ожидания входа
 
Параметр -l задает время ожидания (в секундах) для входа `bcp.exe` в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при попытке соединения с сервером. Время ожидания входа по умолчанию — 15 секунд. Время ожидания входа должно быть числом в диапазоне от 0 до 65 534. Если указанное значение не является числом или выходит за пределы указанного диапазона, программа `bcp.exe` выдает сообщение об ошибке. Значение 0 указывает бесконечное время ожидания. Время ожидания входа, которое меньше 10 секунд (приблизительно), не является надежным.  
  
### <a name="driver-aware-connection-pooling"></a>Организация пулов соединений с учетом драйвера  
Драйвер ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает [организацию пулов соединений с учетом драйвера](https://msdn.microsoft.com/library/hh405031(VS.85).aspx). Дополнительные сведения см. в статье [Организация пулов соединений с учетом драйвера в ODBC Driver for SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md).  
  
### <a name="asynchronous-execution-notification-method"></a>Асинхронное выполнение (метод уведомления)  
Драйвер ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает [асинхронное выполнение (метод уведомления)](https://msdn.microsoft.com/library/hh405038(VS.85).aspx). Пример использования см. в [примере асинхронного выполнения &#40;метод уведомления&#41;](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md).  
  
### <a name="connection-resiliency"></a>Устойчивость подключений
Чтобы обеспечить сохранение подключения приложений к Базе данных SQL Microsoft Azure, драйвер ODBC в Windows может восстанавливать неактивные соединения. Дополнительные сведения см. в статье [Устойчивость подключения в драйвере ODBC в Windows](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md).  
  
## <a name="behavior-changes"></a>Изменения в работе

В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственном клиенте `-y0` параметр для `sqlcmd.exe` привел к усечению выходных данных в 1 МБ, если ширина экрана равна 0.
  
Начиная с ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ограничение на объем данных, извлекаемых в одном столбце, при указанном `-y0` отсутствует. Теперь `sqlcmd.exe` осуществляет потоковую передачу столбцов размером до 2 ГБ (максимальное значение для типа данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]).  
  
Другое различие заключается в том, `-h` что `-y0` при указании обоих параметров и теперь создается сообщение об ошибке, сообщающее о том, что параметры несовместимы. Параметр `-h`, который указывает количество выводимых строк между заголовками столбцов, никогда не был совместим с `-y0` и игнорировался, хотя заголовки не выводились.
  
Обратите внимание на то, что `-y0` может значительно снизить производительность сервера и сети в зависимости от объема возвращаемых данных.

## <a name="see-also"></a>См. также:  
[Драйвер Microsoft ODBC для SQL Server в Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
