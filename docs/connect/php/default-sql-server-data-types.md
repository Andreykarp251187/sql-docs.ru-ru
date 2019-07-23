---
title: Типы данных SQL Server по умолчанию | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: 65c7c211-96d3-4e65-a1de-1fe8d21348e7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 69c138e7eb5d2c4f6dbace0db59ce235e1c0a5f9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993657"
---
# <a name="default-sql-server-data-types"></a>Типы данных SQL Server по умолчанию
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

При отправке данных на сервер [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] преобразует данные из своего типа данных PHP в тип данных SQL Server, если пользователь не задал тип данных SQL Server. Следующая таблица содержит тип данных PHP (тип данных, отправляемых на сервер) и тип данных SQL Server по умолчанию тип (тип данных, в который преобразуются данные). Дополнительные сведения об указании типов данных при отправке данных на сервер см. в статье [Практическое руководство. Указание типов данных SQL Server при использовании драйвера SQLSRV](../../connect/php/how-to-specify-sql-server-data-types-when-using-the-sqlsrv-driver.md).  
  
|Тип данных PHP|Тип SQL Server по умолчанию в драйвере SQLSRV|Тип SQL Server по умолчанию в драйвере PDO_SQLSRV|  
|-----------------|------------------------------------------------|-----------------------------------------------------|  
|NULL|varchar(1)|не поддерживается|  
|Логическое значение|bit|bit|  
|Целочисленный|INT|INT|  
|float|float(24)|не поддерживается|  
|Строка (длина менее 8000 байт)|varchar(<string length>)|varchar(<string length>)|  
|Строка (длина более 8000 байт)|varchar(max)|varchar(max)|  
|Ресурс|Не поддерживается.|Не поддерживается.|  
|Поток (кодировка: не двоичная)|varchar(max)|varchar(max)|  
|Поток (кодировка: двоичная)|varbinary|varbinary|  
|Array|Не поддерживается.|Не поддерживается.|  
|Объект|Не поддерживается.|Не поддерживается.|  
|DateTime (1)|DATETIME|Не поддерживается.|  
  
## <a name="see-also"></a>См. также:  
[Константы (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[Преобразование типов данных](../../connect/php/converting-data-types.md)

[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)

[Типы PHP](https://php.net/manual/language.types.php)

[Типы данных (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/data-types/data-types-transact-sql)  
  
