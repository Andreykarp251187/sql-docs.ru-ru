---
title: Привязка столбцов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: c4407694-c8e1-4b0b-a39d-b007e6c3b54d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a634a553672b83931091056dd489f7559c4269b4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106208"
---
# <a name="binding-columns"></a>Привязка столбцов
Данные, полученные из источника данных возвращается в приложение в переменных, которые приложение, выделенной для этой цели. Прежде чем это можно сделать, необходимо связать приложение, или *привязать*, эти переменные к столбцам результирующего набора; по сути, этот процесс — так же, как привязка переменных приложения для параметров инструкции. Если приложение связывает столбец результирующего набора переменной, в нем описаны эту переменную - адрес, тип данных и т. д. — к драйверу. Драйвер сохраняет эту информацию в структуре, он поддерживает для этой инструкции и использует сведения для возврата значения из столбца при выборке строки.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Привязка столбцов результирующего набора](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Использование SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
