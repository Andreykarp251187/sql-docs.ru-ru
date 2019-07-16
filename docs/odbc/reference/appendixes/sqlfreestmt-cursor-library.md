---
title: SQLFreeStmt (библиотека курсоров) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeStmt function [ODBC], Cursor Library
ms.assetid: 47bfbd4d-9453-4609-958d-1e05794cb223
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4bfe5c91a90f874b514abb661ea06631be87e69c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086415"
---
# <a name="sqlfreestmt-cursor-library"></a>SQLFreeStmt (библиотека курсоров)
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Корпорация Майкрософт рекомендует использовать функциональные возможности драйвера курсора.  
  
 В этом разделе рассматривается использование **SQLFreeStmt** функции в библиотеку курсоров. Общие сведения о **SQLFreeStmt**, см. в разделе [SQLFreeStmt, функция](../../../odbc/reference/syntax/sqlfreestmt-function.md).  
  
 Если приложение вызывает **SQLFreeStmt** с параметром SQL_UNBIND, после вызова **SQLExtendedFetch**, **SQLFetch**, или **SQLFetchScroll**, библиотека курсоров возвращает сообщение об ошибке. Прежде чем его можно отменить привязку столбцы результирующего набора, приложение должно вызвать **SQLCloseCursor** или **SQLFreeStmt** с параметром SQL_CLOSE.
