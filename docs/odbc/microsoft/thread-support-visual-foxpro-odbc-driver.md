---
title: Поддержка (драйвер ODBC для Visual FoxPro) потока | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- thread support [ODBC]
- Visual FoxPro ODBC driver [ODBC], thread support
- FoxPro ODBC driver [ODBC], thread support
- multithreaded applications [ODBC]
ms.assetid: 0c6abbbc-012b-41aa-bded-5e7e362d015b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 72672cfc20b5d363229fd1ba49278d11e6d6793d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67912414"
---
# <a name="thread-support-visual-foxpro-odbc-driver"></a>Поддержка потоков (драйвер ODBC для Visual FoxPro)
Драйвер ODBC для Visual FoxPro является поточно ориентированной. Доступ к дескрипторы среды (*ри*), дескрипторов соединений (*hdbc*) и дескрипторы инструкций (*hstmt*) упаковывается в соответствующие семафоры, чтобы другие процессы доступ к и потенциально изменяя драйвера внутренних структур данных.  
  
 В многопоточном приложении, вы можете отменить функции, на котором выполняется синхронно на *hstmt* путем вызова [SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md) в отдельном потоке.  
  
 Драйвер использует отдельный поток для выборки данных при использовании последовательной выборки. Чтобы использовать последовательной выборки для источника данных, выберите **выборки данных в фоновом режиме** флажок на [диалоговое окно настройки ODBC для Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) или использовать ключевое слово атрибута BackgroundFetch при подключении Строка. Старайтесь не использовать выборку в фоновом режиме, при вызове драйвер из многопоточных приложений. Сведения о ключевых словах атрибут строки подключения, см. в разделе [с помощью строки подключения](../../odbc/microsoft/using-connection-strings.md).  
  
 Дополнительные сведения о потоках и **SQLCancel**, см. в разделе [SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md) в *Справочник по программированию ODBC*.
