---
title: Список ошибок, исправленных | Документация Майкрософт
ms.custom: ''
ms.date: 06/29/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
author: v-makouz
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: 9dba11c0130dc3b969a9fcec46b631abd7d62fe8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63198770"
---
# <a name="list-of-bugs-fixed"></a>Список ошибок, исправленных

Эта страница содержит список ошибок, исправленных в каждом выпуске, начиная с [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-173-for-includessnoversionincludesssnoversion-mdmd"></a>Исправления ошибок в [!INCLUDE[msCoName](../../includes/msconame_md.md)] 17.3 драйвер ODBC для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Фиксированный утечки памяти дескриптор события TCP отправки уведомлений
- Выпуск основных переопределение _SQL_FILESTREAM_DESIRED_ACCESS перечисления в файле заголовка msodbcsql.h
- Определение в файле заголовка msodbcsql.h для Linux, связанные с предопределенной отсутствует маркер доступа и проверки ПОДЛИННОСТИ

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-172-for-includessnoversionincludesssnoversion-mdmd"></a>Исправления ошибок в [!INCLUDE[msCoName](../../includes/msconame_md.md)] 17.2 драйвер ODBC для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Исправлено сообщение об ошибке об аутентификации Azure Active Directory
- Исправлено обнаружение кодировки, если языковой стандарт переменные среды задаются по-разному
- Фиксированный сбой после отключения с идет восстановление подключения
- Исправлено обнаружение из жизнеспособность подключения
- Исправлено неверное обнаружение закрытых сокетов
- Исправлена неограниченное время ожидания при попытке освобождения дескриптора инструкции во время восстановления, завершившееся сбоем
- Исправлено удаление неправильное поведение при установке версии 13 и 17 на Windows
- Поведение предопределенной расшифровки на более старых платформ Windows (Windows 7, 8 и Server 2012)
- Устранена проблема кэша при использовании проверки подлинности ADAL для Windows
- Исправлена проблема, которая блокировок и перезаписи трассировки входит в систему Windows

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversion-mdmd"></a>Исправления ошибок в [!INCLUDE[msCoName](../../includes/msconame_md.md)] 17.1 драйвер ODBC для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Исправлена 1-секундная задержка при вызове SQLFreeHandle с включенным режимом MARS и атрибут соединения «Encrypt = yes»
- Исправлена ошибка 22003 сбой в SQLGetData, когда размер буфера, переданного в меньше, а затем извлекаемых данных (Windows)
- Исправлены сообщения усеченное ADAL об ошибках
- Устранена ошибка, редко в 32-разрядной Windows, при преобразовании с плавающей запятой в целое число
- Исправлена проблема, при которой Вставка double в десятичное поле с постоянным шифрованием на возвратит ошибка усечения данных
- Исправлено предупреждение в MacOS установщика
- Исправлена отправкой Неправильное состояние в SQL Server во время попытки восстановления сеанса при устойчивость подключения организация пулов соединений, так и включены, вызывая сеанса для удаления сервера

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversion-mdmd"></a>Исправления ошибок в [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Исправлена ошибка, если при использовании проверки подлинности Kerberos, инструкции bulk insert может завершиться с ошибкой «отказано в доступе»
- Удален решение в версии ниже 2.3.1 unixODBC ошибки (драйвер вдвое размеры некоторых буферов, передаваемый unixODBC)
- Исправлена устойчивость подключений (повторное подключение) зависает при использовании ColumnEncryption = включено
- Исправлена ошибка создания имени DSN, где при с помощью «Интерактивной проверки подлинности Active Directory» параметра проверки подлинности Azure окно может стать не отвечает (Windows)
- Исправлена редкими сбоями во время завершения работы с ODBC, при включении асинхронное выполнение (произошло при удалении дескриптора соединения)
- Исправлена проблема, при котором драйвер SQL вызвал высоком потреблении ресурсов ЦП при выполнении долго хранимых процедур
- Фиксированный невозможность получения данных в столбце varbinary(max), зашифрованные без преобразования
- Устранена проблема, когда после null varchar(max) зашифрованного столбца является извлекаются с помощью SQLGetData() для статического курсора, следующий столбец является также обнулением даже если он содержит данные
- Устранена проблема с выборкой varbinary(max) поле с постоянным шифрованием на
- Устранена проблема, из setlocale() не работает с постоянным шифрованием
- Устранена проблема с SQLDescribeParam(), возвращая ошибку при вызове на параметр процедуры XML-типа, хранящегося с постоянным шифрованием
- Исправлена escape-символы подчеркивания, не работает в SQLTables
- Исправлена ошибка, где иврита данные (varchar) будут усечены при возврате в виде расширенных символов в Linux
- Устранена проблема с запроса char и varchar Shift-JIS в кодировке UTF-8 приложения
- Исправлена ошибка, когда вызов SQLGetInfo с параметром SQL_DRIVER_NAME возвращенный стиле Linux filename в Mac OS
- Устранена проблема, где файлы размером более 32 КБ байтов в столбцы типа VARCHAR, с помощью программы bcp бы привести к ошибкам загрузки Windows-1252 символьных данных, с помощью входных данных
