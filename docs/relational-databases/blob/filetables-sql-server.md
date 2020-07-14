---
title: Таблицы FileTable (SQL Server) | Документация Майкрософт
description: Изучите преимущества и функциональные возможности таблиц FileTable — функции SQL Server, которая использует структуру каталогов для хранения файлов. Обучение работе с таблицами FileTable
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], overview
- FileTables [SQL Server]
- FileTable [SQL Server], see FileTables [SQL Server]
- FileTable [SQL Server]
ms.assetid: a57b629c-e9ed-48fd-9a48-ed3787d80c8f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8f694511c2f79bcaf86d7756410a2cbc286b968a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767960"
---
# <a name="filetables-sql-server"></a>Таблицы FileTable (SQL Server)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Функция FileTable обеспечивает поддержку пространства имен файлов Windows и совместимость с приложениями Windows для файлов данных, хранящихся в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Таблица FileTable позволяет приложению интегрировать свои компоненты хранения и управления данными, а также обеспечивает работу интегрированных служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , включая полнотекстовый и семантический поиск, с неструктурированными данными и метаданными.  
  
 Иными словами, появляется возможность хранить файлы и документы в специальных таблицах на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , называемых таблицами FileTable, но при этом доступ к ним возможен из приложений Windows без внесения каких-либо изменений в эти приложения, как если бы они хранились в файловой системе.  
  
 Функция FileTable построена на основе технологии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] FILESTREAM. Дополнительные сведения о FILESTREAM см. в разделе [FILESTREAM (SQL Server)](../../relational-databases/blob/filestream-sql-server.md).  
  
##  <a name="benefits-of-the-filetable-feature"></a><a name="Goals"></a> Преимущества функции FileTable  
 Таблицы FileTable имеют следующее назначение.  
  
-   Совместимость с API-интерфейсами Windows для файлов данных, хранящихся в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Совместимость с API-интерфейсами Windows включает следующее.  
  
    -   Потоковый доступ без транзакций и обновление на месте с заменой данных FILESTREAM.  
  
    -   Иерархическое пространство имен для каталогов и файлов.  
  
    -   Хранение атрибутов файлов, таких как дата создания и дата изменения.  
  
    -   Поддержка API-интерфейсов Windows для управления файлами и каталогами.  
  
-   Совместимость с другими функциями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , включая средства управления, службы и возможности реляционных запросов через FILESTREAM и данные атрибутов файлов.  
  
 Таким образом, таблицы FileTable позволяют перешагнуть барьер, препятствовавший использованию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для хранения неструктурированных данных и управления данными, которые в настоящее время размещаются в виде файлов на файловом сервере. Предприятия получили возможность перенести данные с файловых серверов в таблицы FileTable, чтобы пользоваться и преимуществами интегрированного администрирования, и преимуществами служб, предоставляемыми [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В то же время сохраняется совместимость с существующими приложениями Windows, рассматривающими данные как файлы в файловой системе.  
 
  
##  <a name="what-is-a-filetable"></a><a name="Description"></a> Что такое таблица FileTable?  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет специальные **таблицы файлов**, которые также называются таблицами **FileTable**, для приложений, требующих хранения файлов и каталогов в базе данных, совместимости с API-интерфейсами Windows и нетранзакционного доступа к данным. Таблицы FileTable являются специализированными пользовательскими таблицами с предварительно определенной схемой для хранения данных FILESTREAM, а также сведений об иерархии файлов и каталогов и атрибутах файлов.  
  
 Таблицы FileTable обеспечивают следующие функциональные возможности.  
  
-   Таблица FileTable представляет иерархию файлов и каталогов. Она содержит данные, относящиеся ко всем узлам в иерархии для папок и файлов, содержащихся в них. Эта иерархия начинается с корневого каталога, указанного при создании FileTable.  
  
-   Каждая строка в таблице FileTable представляет файл или каталог.  
  
-   Каждая строка содержит следующие элементы. Дополнительные сведения о схеме таблиц FileTable см. в разделе [FileTable Schema](../../relational-databases/blob/filetable-schema.md).  
  
    -   Столбец **file_stream** для данных потока и идентификатор **stream_id** (GUID). (Для каталога значение в столбце **file_stream** равно NULL.)  
  
    -   Столбцы **path_locator** и **parent_path_locator** для представления и обслуживания текущего элемента (файла или каталога) и иерархии каталогов.  
  
    -   10 атрибутов файлов, таких как дата создания и дата изменения, которые требуются для API-интерфейсов файлового ввода-вывода.  
  
    -   Столбец типа, который поддерживает полнотекстовый поиск и семантический поиск по файлам и документам.  
  
-   В таблицах FileTable применяются определенные системные ограничения и триггеры, поддерживающие семантику пространства имен файлов.  
  
-   Если база данных настроена для нетранзакционного доступа, то иерархия файлов и каталогов, представленная в таблице FileTable, отображается с помощью общего ресурса FILESTREAM, настроенного для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Это обеспечивает доступ приложениям Windows к файловой системе.  
  
 Ниже перечислены некоторые дополнительные характеристики таблиц FileTable.  
  
-   Данные файлов и каталогов, хранящиеся в таблице FileTable, отображаются с помощью общего ресурса Windows для нетранзакционного доступа к файлам из приложений на основе API-интерфейсов Windows. Для приложения Windows это выглядит как обычная общая папка с файлами и каталогами. Приложения могут использовать богатый набор API-интерфейсов Windows для управления файлами и каталогами, находящимися в этой общей папке.  
  
-   Иерархия каталогов, отображаемая в общем хранилище, является просто логической структурой каталога, сохраняемой в таблице FileTable.  
  
-   Вызовы для создания или изменения файла или каталога через общий ресурс Windows перехватываются компонентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и отражаются в соответствующих реляционных данных в таблице FileTable.  
  
-   Операции API-интерфейсов Windows являются по своей природе нетранзакционными и не связаны с пользовательскими транзакциями. Тем не менее транзакционный доступ к данным FILESTREAM, хранящимся в таблице FileTable, полностью поддерживается, как это происходит для любого столбца FILESTREAM в обычной таблице.  
  
-   Кроме того, таблицы FileTable можно запрашивать и обновлять с помощью обычного доступа [!INCLUDE[tsql](../../includes/tsql-md.md)] . Они интегрируются со средствами управления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и такими компонентами, как средство резервного копирования.  

-   Нельзя отправить запрос по электронной почте через компонент dbmail и вложить файл, расположенный в каталоге filestream (и filetable соответственно). Драйвер фильтра файловой системы RsFx0420 проверяет запросы ввода-вывода, входящие в папку filestream и исходящие из нее. Запросы, которые не исходят из исполняемого файла SQL Server и кода Filestream, будут прямо запрещены.
  
##  <a name="additional-considerations-for-using-filetables"></a><a name="additional"></a> Дополнительные замечания об использовании таблиц FileTable  
  
###  <a name="administrative-considerations"></a><a name="DBA"></a> Вопросы управления  
 **О функции FILESTREAM и таблицах FileTable**  
  
-   Можно настроить таблицы FileTable отдельно от FILESTREAM. Таким образом, можно продолжать пользоваться функцией FILESTREAM, не включая нетранзакционный доступ и не создавая таблицы FileTable.  
  
-   Нетранзакционный доступ к данным FILESTREAM возможен исключительно с помощью таблиц FileTable. Таким образом, при включении нетранзакционного доступа поведение существующих столбцов FILESTREAM и приложений не изменяется.  
  
 **О таблицах FileTable и нетранзакционном доступе**  
  
-   Можно включить или отключить нетранзакционный доступ на уровне базы данных.  
  
-   Можно настроить или отрегулировать нетранзакционный доступ на уровне базы данных, отключив или включив доступ только для чтения или полный доступ для чтения и записи.  
   
###  <a name="filetables-do-not-support-memory-mapped-files"></a><a name="memory"></a> Таблицы FileTable не поддерживают файлы, отображенные на память  
 Таблицы FileTable не поддерживают файлы, отображенные на память. Двумя распространенными примерами приложений, в которых используются файлы, отображаемые на память, являются Notepad и Paint. Эти приложения нельзя использовать на том же компьютере, что и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для открытия файлов, которые хранятся в FileTable. Но можно использовать эти приложения с удаленного компьютера для открытия файлов, хранящихся в FileTable, поскольку в этих обстоятельствах средство отображения на память не используется.  
   
##  <a name="related-tasks"></a><a name="reltasks"></a> Связанные задачи  
 [Включение необходимых компонентов для таблицы FileTable](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)  
 Описывает способ включения компонентов, обязательных для создания и использования таблиц FileTable.  
  
 [Создание, изменение и удаление таблиц FileTable](../../relational-databases/blob/create-alter-and-drop-filetables.md)  
 Описывает способы создания новых таблиц FileTable и изменения или удаления существующих таблиц FileTable.  
  
 [Загрузка файлов в таблицы FileTable](../../relational-databases/blob/load-files-into-filetables.md)  
 Описывает процедуру загрузки или переноса файлов в таблицы FileTable.  
  
 [Работа с каталогами и путями в таблицах FileTable](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)  
 Описывает структуру каталогов, в которой файлы хранятся в таблицах FileTable.  
  
 [Доступ к таблицам FileTable с помощью Transact-SQL](../../relational-databases/blob/access-filetables-with-transact-sql.md)  
 Описывает, как команды DML языка обработки данных Transact-SQL работают с таблицами FileTable.  
  
 [Доступ к таблицам FileTable с помощью API-интерфейсов ввода-вывода файлов](../../relational-databases/blob/access-filetables-with-file-input-output-apis.md)  
 Описание работы файловой системы ввода-вывода с таблицами FileTable.  
  
 [Управление таблицами FileTable](../../relational-databases/blob/manage-filetables.md)  
 Описывает стандартные административные задачи по управлению таблицами FileTables.  
  
##  <a name="related-content"></a><a name="relcontent"></a> См. также  
 [Схема FileTable](../../relational-databases/blob/filetable-schema.md)  
 Описывает стандартные и фиксированные схемы таблицы FileTable.  
  
 [Совместимость FileTable с другими компонентами SQL Server](../../relational-databases/blob/filetable-compatibility-with-other-sql-server-features.md)  
 Описывает работу таблиц FileTable совместно с другими компонентами SQL Server.  
  
 [Инструкции FileTable языка DDL, функции, хранимые процедуры и представления](../../relational-databases/blob/filetable-ddl-functions-stored-procedures-and-views.md)  
 Приведен список инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] и объектов базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , добавленных или измененных для поддержки функциональности FileTable.  

## <a name="see-also"></a>См. также:
[Динамические административные представления Filestream и FileTable (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
<br>[Представления каталога Filestream и FileTable (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
<br>[Системные хранимые процедуры Filestream и FileTable (Transact-SQL)](../system-stored-procedures/filestream-and-filetable-system-stored-procedures.md)


  
  
