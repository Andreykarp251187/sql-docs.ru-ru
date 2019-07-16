---
title: Допустимость значений NULL и трехзначная логика сравнения | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- precision [CLR integration]
- overflow detections [CLR integration]
- null values [CLR integration]
- three-value logic comparisons [CLR integration]
- data types [CLR integration]
- SqlBoolean data type
ms.assetid: 13da4c7f-1010-4b2d-a63c-c69b6bfd96f1
author: rothja
ms.author: jroth
ms.openlocfilehash: e5dbdf757038abbf2c98d3987ee14a9cb9184a61
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68081320"
---
# <a name="nullability-and-three-value-logic-comparisons"></a>Допустимость значений NULL и трехзначная логика сравнения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Если вы знакомы с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных, вы найдете сходную семантику и точность в **System.Data.SqlTypes** пространства имен в [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Однако существуют определенные различия. В этом разделе описаны самые важные из них.  
  
## <a name="null-values"></a>Значения NULL  
 Главное различие между типами данных среды CLR и типами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] заключается в том, что первые не допускают значений NULL, а вторые реализуют полную семантику NULL.  
  
 Значения NULL влияют на результаты сравнений. При сравнении двух значений x и y, если x или y имеет значение NULL, то результатом некоторых логических сравнений будет значение UNKNOWN, а не TRUE или FALSE.  
  
## <a name="sqlboolean-data-type"></a>Тип данных SqlBoolean  
 **System.Data.SqlTypes** представляет пространство имен **SqlBoolean** тип для представления этого трехзначной логики. Сравнения каких-либо **SqlTypes** возвращают **SqlBoolean** тип значения. Неизвестное значение, представленное значение null **SqlBoolean** типа. Свойства **IsTrue**, **IsFalse**, и **IsNull** обеспечивают возможность проверки значение **SqlBoolean** типа.  
  
## <a name="operations-functions-and-null-values"></a>Операции, функции и значения NULL  
 Все арифметические операторы (+, -, \*, /, %), битовые операторы (~ &, и |), и большинство функций возвращают NULL, если какой-либо из операндов или аргументов **SqlTypes** равны NULL. **IsNull** свойство всегда возвращает значение true или false.  
  
## <a name="precision"></a>Точность  
 Максимальные значения типов данных decimal в среде CLR платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] отличаются от максимальных значений числовых типов и типов decimal в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Кроме того, типы данных decimal в среде CLR платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] предполагают использование максимальной точности. В среде CLR для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но при этом **SqlDecimal** предоставляет такую же максимальную точность и масштаб, а также ту же семантику, что тип данных decimal в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="overflow-detection"></a>Обнаружение переполнений  
 В среде CLR платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] сложение двух очень больших чисел не может вызвать исключение. При этом если не использовался оператор проверки, возвращенный результат может «обернуться по кругу» и превратиться в отрицательное целое число. В **System.Data.SqlTypes**, исключения возникают для всех переполнения и потери значимости ошибки и ошибки деления на ноль.  
  
## <a name="see-also"></a>См. также  
 [Типы данных SQL Server в платформе .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
