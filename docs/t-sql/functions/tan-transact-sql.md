---
title: TAN (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- TAN_TSQL
- TAN
dev_langs:
- TSQL
helpviewer_keywords:
- TAN function
- tangent
ms.assetid: f679fa6a-5739-484b-9450-fb3400d4f30c
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c451192a96dc2fdf4e8e5e619237527139b4f2f6
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68117453"
---
# <a name="tan-transact-sql"></a>TAN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает тангенс входного аргумента.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
TAN ( float_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *float_expression*  
 [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) типа **float** или типа, который может быть неявно преобразован в тип **float**, воспринимаемый как количество радиан.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **float**  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается тангенс `PI()/2`.  
  
```  
SELECT TAN(PI()/2);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------------  
1.6331778728383844E+16  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В приведенном ниже примере возвращается тангенс 0,45.  
  
```  
SELECT TAN(.45);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
--------  
0.48
```  
  
## <a name="see-also"></a>См. также:  
 [Математические функции (Transact-SQL)](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  

