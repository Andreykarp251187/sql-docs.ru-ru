---
title: PDOStatement::setFetchMode | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f132b2af-0433-4fbe-b03f-69a7d631093a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 75082b50eeb6298173d41e70ed3020247896c164
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921150"
---
# <a name="pdostatementsetfetchmode"></a>PDOStatement::setFetchMode
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Указывает режим извлечения для дескриптора PDOStatement.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
bool PDOStatement::setFetchMode( $mode );  
```  
  
#### <a name="parameters"></a>Параметры  
$*mode*: любые параметры, допустимые для передачи в [PDOStatement::fetch](../../connect/php/pdostatement-fetch.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
Значение true в случае успеха, в противном случае — значение false.  
  
## <a name="remarks"></a>Remarks  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   $stmt1 = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   while ( $row = $stmt1->fetch()) {   
      print($row['Name'] . "\n");   
   }  
   print( "\n---------- PDO::FETCH_ASSOC -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $stmt->setFetchMode(PDO::FETCH_ASSOC);  
   $result = $stmt->fetch();  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_NUM -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $stmt->setFetchMode(PDO::FETCH_NUM);  
   $result = $stmt->fetch();  
   print_r ($result );  
  
   print( "\n---------- PDO::FETCH_BOTH -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $stmt->setFetchMode(PDO::FETCH_BOTH);  
   $result = $stmt->fetch();  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_LAZY -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $stmt->setFetchMode(PDO::FETCH_LAZY);  
   $result = $stmt->fetch();  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_OBJ -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $stmt->setFetchMode(PDO::FETCH_OBJ);  
   $result = $stmt->fetch();  
   print $result->Name;  
   print( "\n \n" );  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
