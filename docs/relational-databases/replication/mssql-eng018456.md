---
title: MSSQL_ENG018456 | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG018456 error
ms.assetid: 3daa8144-d81f-445a-b6c3-4bb3e9fd1526
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 86c8934c0fec7b653e96590d2bce5d862e7dd817
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85721757"
---
# <a name="mssql_eng018456"></a>MSSQL_ENG018456
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|18456|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Ошибка входа пользователя '%.*ls'.%.\*ls|  
  
## <a name="explanation"></a>Объяснение  
 Ошибка MSSQL_ENG018456 возникает при неудачной попытке входа в систему. Если сообщение об ошибке включает учетную запись **distributor_admin** (Ошибка входа пользователя 'distributor_admin'.), проблема заключается в учетной записи, которая используется репликацией. Репликация создает удаленный сервер **repl_distributor**, предоставляющий возможность обмена данными между распространителем и издателем. Имя входа **distributor_admin** связано с этим удаленным сервером и должно иметь правильный пароль.  
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь в том, что для учетной записи указан пароль. Дополнительные сведения см. в разделе [Организация безопасности распространителя](../../relational-databases/replication/security/secure-the-distributor.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
