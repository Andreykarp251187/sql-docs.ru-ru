---
title: PDO::exec | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 359a87c6-c13a-4518-8f23-a922e7f3b171
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4ac158f9005f66e49082b6be288c35f96b527f39
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993275"
---
# <a name="pdoexec"></a>PDO::exec
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Подготавливает и выполняет инструкцию SQL в одном вызове функции, возвращая количество строк, затронутых этой инструкцией.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int PDO::exec ($statement)  
```  
  
#### <a name="parameters"></a>Параметры  
*$statement*: строка, содержащая инструкцию SQL для выполнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
Целое число, обозначающее количество затронутых строк.  
  
## <a name="remarks"></a>Remarks  
Если *$statement* содержит несколько инструкций SQL, количество затронутых строк указывается только для последней инструкции.  
  
PDO::exec не возвращает результаты для инструкции SELECT.  
  
Следующие атрибуты влияют на поведение PDO::exec:  
  
-   PDO::ATTR_DEFAULT_FETCH_MODE  
  
-   PDO::SQLSRV_ATTR_ENCODING  
  
-   PDO::SQLSRV_ATTR_QUERY_TIMEOUT  
  
Дополнительные сведения см. в статье [PDO::setAttribute](../../connect/php/pdo-setattribute.md). 
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
Этот пример удаляет строки таблицы Table1, содержащие "xxxyy" в столбце col1. Затем пример сообщает, сколько строк было удалено.  
  
```  
<?php  
   $c = new PDO( "sqlsrv:server=(local)");  
  
   $c->exec("use Test");  
   $ret = $c->exec("delete from Table1 where col1 = 'xxxyy'");  
   echo $ret;  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
