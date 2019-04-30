---
title: Приложение 1 (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sybase Console,Appendix
ms.assetid: 6dcfd6d5-772c-4876-aa94-a7f43c4b9d59
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 4e9e3aabd08566d65cd09242dbaf8a2041cc4ef1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63132271"
---
# <a name="appendix---1-sybasetosql"></a>Приложение 1 (SybaseToSQL)
Краткий обзор команд консоли SSMA параметры командной строки:  
  
|SL. Нет.|Параметр|Обязательно?|Аргумент ключа|Допустимые значения|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s или сценарий|Да|scriptfile|Допустимое имя XML-файла.<br /><br />Файл определения скрипта консоли.|  
|2|-v или переменная|Нет|variablevaluefile|Допустимое имя XML-файла.<br /><br />Если в файле сценария используются переменные, должен быть указан этот файл.|  
|3|-c/serverconnection|Нет|serverconnectionfile|Допустимое имя XML-файла.<br /><br />Этот файл содержит сведения о подключении сервера.|  
|4|-x/xmloutput|Нет|xmloutputfile|Этот параметр указывает, выходные данные консоли в формате XML. Если этот параметр не указан, по умолчанию выводится в ТЕКСТОВОМ формате.<br /><br />Если xmloutputfile не указан, выходные данные XML направляется в STDOUT.<br /><br />Xmloutputfile — это имя файла, в который записывается в выходных данных консоли в формате XML.|  
|5|-l/log|Нет|logfile|Допустимое имя файла.|  
|6|-e/projectenvironment|Нет|projectenvironmentfolder|Допустимое имя папки с файлами среды проекта SSMA.|  
|7|-p/securepassword|Нет|-a/добавление {< server_id > [,... n] &#124; все} - c&#124;serverconnection < файл server соединения > [-v&#124;переменной < переменная значение file >] [-o или перезаписывать]<br /><br />или диспетчер конфигурации служб<br /><br />-a/добавление {< server_id > [,... n] &#124; все} -s&#124;скрипт < файл сценария > [-v&#124;переменной < переменная значение file >] [-o или перезаписывать]<br /><br />-r/remove {<server_id> [, ...n] &#124; all}<br /><br />-l/списка<br /><br />-e/export {<server-id> [, ...n] &#124; all} <encrypted-password -file><br /><br />-i/import {<server-id> [, ...n] &#124; all} <encrypted-password-file>|Если указано, этот параметр не должны объединяться с любыми другими параметрами.<br /><br />Идентификатор сервера: Уникальный идентификатор, предоставленный для сервера {строка}<br /><br />файл для подключения сервера: файл определения сервера (serverconnectionfile или scriptfile).<br /><br />переменная значение файл: Он представляет собой файл определения переменной и используется в файле для подключения сервера.<br /><br />пароль файл с шифрованием: Это файл паролей сервера, зашифрованные с помощью пользовательской парольную фразу.|  
|8|-?|Нет|Неприменимо|Неприменимо|  
  
## <a name="see-also"></a>См. также  
[Выполнение команд консоли SSMA (Sybase)](https://msdn.microsoft.com/ea8950b7-fabc-4aa4-89f8-9573a2617d70)  
  
