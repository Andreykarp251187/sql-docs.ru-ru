---
title: Справочник по API драйвера SQLSRV | Документация Майкрософт
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0b55da26-ddeb-4e89-872a-91e0aba57103
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d3d5a6afaa4580623bade5ac6d7dd5b13a4cbdc6
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67992779"
---
# <a name="sqlsrv-driver-api-reference"></a>Справочник по API для драйвера SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

API для драйвера SQLSRV в [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] имеет имя **sqlsrv**. Все функции **sqlsrv** начинаются с элемента **sqlsrv_** , после которого следует глагол или существительное. Функции с глаголом выполняют определенное действие, а функции с существительным возвращают определенные виды метаданных.  
  
## <a name="in-this-section"></a>в этом разделе  
Драйвер SQLSRV содержит следующие функции:  
  
|Компонент|Описание|  
|------------|---------------|  
|[sqlsrv_begin_transaction](../../connect/php/sqlsrv-begin-transaction.md)|Начинает транзакцию.|  
|[sqlsrv_cancel](../../connect/php/sqlsrv-cancel.md)|Отменяет инструкцию, удаляет все ожидающие результаты для инструкции.|  
|[sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md)|Предоставляет сведения о клиенте.|  
|[sqlsrv_close](../../connect/php/sqlsrv-close.md)|Закрывает соединение. Освобождает все ресурсы, связанные с соединением.|  
|[sqlsrv_commit](../../connect/php/sqlsrv-commit.md)|Фиксирует транзакцию.|  
|[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)|Изменяет конфигурации обработки ошибок и ведения журнала.|  
|[sqlsrv_connect](../../connect/php/sqlsrv-connect.md)|Создает и открывает соединение.|  
|[sqlsrv_errors](../../connect/php/sqlsrv-errors.md)|Возвращает сведения об ошибке и (или) предупреждении для последней операции.|  
|[sqlsrv_execute](../../connect/php/sqlsrv-execute.md)|Выполняет подготовленную инструкцию.|  
|[sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md)|Делает следующую строку данных доступной для чтения.|  
|[sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)|Извлекает следующую строку данных в виде массива с числовым индексом и (или) ассоциативного массива.|  
|[sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md)|Извлекает следующую строку в качестве объекта.|  
|[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)|Возвращает метаданные поля.|  
|[sqlsrv_free_stmt](../../connect/php/sqlsrv-free-stmt.md)|Закрывает инструкцию. Освобождает все ресурсы, связанные с инструкцией.|  
|[sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md)|Возвращает значение указанного параметра конфигурации.|  
|[sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md)|Извлекает поле в текущей строке по индексу. Можно указать тип возвращаемого значения PHP.|  
|[sqlsrv_has_rows](../../connect/php/sqlsrv-has-rows.md)|Определяет, имеет ли результирующий набор одну или несколько строк.|  
|[sqlsrv_next_result](../../connect/php/sqlsrv-next-result.md)|Делает следующий результат доступным для обработки.|  
|[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md)|Сообщает число строк в результирующем наборе.|  
|[sqlsrv_num_fields](../../connect/php/sqlsrv-num-fields.md)|Извлекает количество полей в активном результирующем наборе.|  
|[sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)|Подготавливает запрос Transact-SQL без его выполнения. Выполняет неявную привязку параметров.|  
|[sqlsrv_query](../../connect/php/sqlsrv-query.md)|Подготавливает и выполняет запрос Transact-SQL.|  
|[sqlsrv_rollback](../../connect/php/sqlsrv-rollback.md)|Выполняет откат транзакции.|  
|[sqlsrv_rows_affected](../../connect/php/sqlsrv-rows-affected.md)|Возвращает количество измененных строк.|  
|[sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md)|Отправляет до 8 килобайт (8 КБ) данных на сервер с каждым вызовом функции.|  
|[sqlsrv_server_info](../../connect/php/sqlsrv-server-info.md)|Предоставляет сведения о сервере.|  
  
## <a name="reference"></a>Справочник  
[Руководство по PHP](https://php.net/manual)  
  
## <a name="see-also"></a>См. также:  
[Обзор драйверов Майкрософт для PHP для SQL Server](../../connect/php/overview-of-the-php-sql-driver.md)

[Константы (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[Руководство по программированию драйверов Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Getting Started with the Microsoft Drivers for PHP for SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md) (Начало работы с драйверами Майкрософт для PHP для SQL Server)
  
