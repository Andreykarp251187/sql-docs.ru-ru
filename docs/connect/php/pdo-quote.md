---
title: 'PDO:: quote | Документация Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ab9ddc48-42f8-4edf-aa8b-b0fc66706161
author: MightyPen
ms.author: genemi
ms.openlocfilehash: eeb83be9d9414d0d9380ca1771bf50985e283b98
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993175"
---
# <a name="pdoquote"></a>PDO::quote
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Обрабатывает строку для использования в запросе, заключая входную строку в кавычки, как того требует основная база данных SQL Server. PDO::quote будет экранировать специальные символы во входной строке с помощью стиля кавычек, подходящего для SQL Server.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
string PDO::quote( $string[, $parameter_type ] )  
```  
  
#### <a name="parameters"></a>Параметры  
$*string*: строка для заключения в кавычки.  
  
$*parameter_type*: необязательный символ (целое число), указывающий тип данных.  Значение по умолчанию — PDO::PARAM_STR.  
  
## <a name="return-value"></a>Возвращаемое значение  
Строка в кавычках, которую можно передать в инструкцию SQL, или значение false в случае ошибки.  
  
## <a name="remarks"></a>Remarks  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
  
```  
<?php  
$database = "test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$param = 'a \' g';  
$param2 = $conn->quote( $param );  
  
$query = "INSERT INTO Table1 VALUES( ?, '1' )";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param));  
  
$query = "INSERT INTO Table1 VALUES( ?, ? )";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param, $param2));  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
