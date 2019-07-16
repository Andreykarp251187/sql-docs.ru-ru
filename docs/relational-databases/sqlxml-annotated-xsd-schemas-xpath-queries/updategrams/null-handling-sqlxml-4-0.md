---
title: NULL (SQLXML 4.0) обработка | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updg:nullvalue attribute
- updategrams [SQLXML], null values
- nullvalue attribute
- null values [SQLXML]
ms.assetid: 5e11eebb-d94e-4ce6-a6d0-870225706bc1
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 43d5235d8e82ff674abcaa00da8c20bdbedffa60
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68018509"
---
# <a name="null-handling-sqlxml-40"></a>Обработка значений NULL (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Синтаксис XML определяет значение NULL как отсутствие. (Например, если значение атрибута или элемента имеет значение NULL, этот атрибут или элемент отсутствует в XML-документе.) В [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML, **updg: nullValue** атрибут позволяет задать значение NULL для значения элемента или атрибута.  
  
 Например, следующая диаграмма обновления гарантирует, что **Title** значение для контакта с **ContactID** равным 64, равно NULL, а затем обновляет **Title** значение «Mr.» для этого контакта.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync updg:nullvalue="IsNULL"  >  
    <updg:before>  
       <Person.Contact ContactID="64" Title="IsNULL" />  
    </updg:before>  
    <updg:after>  
       <Person.Contact ContactID="64" Title="Mr." />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Когда параметры передаются диаграмме обновления, значение NULL может передаваться как значение параметра. Это делается путем указания **nullvalue** атрибут в  **\<updg:header >** блока. Например, см. в разделе [передача параметров в диаграммы обновления &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/passing-parameters-to-updategrams-sqlxml-4-0.md).  
  
## <a name="see-also"></a>См. также  
 [Вопросы безопасности диаграмм обновления &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
