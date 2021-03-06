---
title: Что такое Azure Data Studio
description: Azure Data Studio — это бесплатное упрощенное средство, которое работает в Windows, macOS и Linux и предназначено для управления SQL Server, базой данных SQL Azure и хранилищем данных SQL Azure.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: overview
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, maghan, sstein
ms.custom: seodec18, sqlfreshmay19
ms.date: 01/15/2020
ms.openlocfilehash: b58a54e99c269db113bdd1e1821ba55ce3d83ff5
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88765513"
---
# <a name="what-is-azure-data-studio"></a>Что такое Azure Data Studio?

Azure Data Studio — это кроссплатформенное решение для специалистов по работе с данными, использующих семейство локальных и облачных платформ данных Майкрософт в Windows, MacOS и Linux.

Azure Data Studio предлагает современный редактор с технологией IntelliSense, возможностью использования фрагментов кода, интеграцией системы управления версиями и интегрированным терминалом. Он создан с учетом потребностей пользователей платформы данных и включает в себя встроенную возможность построения диаграмм на основе результирующих наборов запросов и настраиваемые панели мониторинга.

Исходный код Azure Data Studio и используемых поставщиков данных доступен на сайте GitHub на условиях лицензионного соглашения в отношении исходного кода. Это соглашение предоставляет права на изменение и использование программного обеспечения, но не на его распространение или размещение в облачной службе. Дополнительные сведения см. в статье [Вопросы и ответы по Azure Data Studio](faq.md).

**[Скачивание и установка Azure Data Studio](./download-azure-data-studio.md?view=sql-server-ver15)**

## <a name="sql-code-editor-with-intellisense"></a>Редактор кода SQL с технологией IntelliSense

Azure Data Studio предлагает современную среду создания кода SQL с активным использованием клавиатуры, которая упрощает выполнение повседневных задач благодаря таким встроенным функциям, как несколько окон вкладок, полнофункциональный редактор SQL, технология IntelliSense, завершение ключевых слов, фрагменты кода, навигация по коду и интеграция системы управления версиями (Git). Выполняйте запросы SQL по требованию, а затем анализируйте и сохраняйте результаты в виде текста, а также в форматах JSON или Excel. Редактируйте данные, упорядочивайте избранные подключения к базам данных и просматривайте объекты базы данных в знакомом интерфейсе. Сведения об использовании редактора SQL см. в статье о [создании объектов базы данных с помощью редактора SQL](tutorial-sql-editor.md).

## <a name="smart-sql-code-snippets"></a>Интеллектуальные фрагменты кода SQL

Фрагменты кода SQL позволяют формировать правильный синтаксис SQL для создания баз данных, таблиц, представлений, хранимых процедур, пользователей, имен входа, ролей, а также для обновления существующих объектов базы данных. С помощью интеллектуальных фрагментов кода можно быстро создавать копии базы данных для разработки или тестирования, а также генерировать и выполнять сценарии CREATE и INSERT.

Azure Data Studio также предоставляет возможности для создания пользовательских фрагментов кода SQL. Дополнительные сведения см. в статье о [создании и использовании фрагментов кода](code-snippets.md).

## <a name="customizable-server-and-database-dashboards"></a>Настраиваемые панели мониторинга сервера и базы данных

Создавайте многофункциональные настраиваемые панели мониторинга для отслеживания и быстрого устранения проблем, препятствующих высокой производительности баз данных. Сведения об аналитических мини-приложениях и панелях мониторинга баз данных и серверов см. в статье об [управлении серверами и базами данных с помощью аналитических мини-приложений](insight-widgets.md).

## <a name="connection-management-server-groups"></a>Управление подключением (группы серверов)

Группы серверов позволяют упорядочивать сведения о подключениях к рабочим серверам и базам данных. Дополнительные сведения см. в статье [Группы серверов в Azure Data Studio](server-groups.md).

## <a name="integrated-terminal"></a>Встроенный терминал

Используйте популярные программы и средства командной строки (например, Bash, PowerShell, sqlcmd, bcp и SSH) в окне встроенного терминала непосредственно в пользовательском интерфейсе Azure Data Studio. Дополнительные сведения об интегрированном терминале см. в [этой статье](integrated-terminal.md).

## <a name="extensibility-and-extension-authoring"></a>Расширяемость и создание расширений

Повышайте эффективность разработки в Azure Data Studio, расширяя функциональные возможности базовой установки. Azure Data Studio предоставляет точки расширения для действий по управлению данными, а также поддержку для создания расширений.

Сведения о расширяемости Azure Data Studio см. в [Расширяемость](extensibility.md).
Дополнительные сведения о создании расширений см. в [этой статье](extension-authoring.md).

## <a name="feature-comparison-with-sql-server-management-studio-ssms"></a>Сравнение функций с SQL Server Management Studio (SSMS)

**Используйте Azure Data Studio, если вы...**

- будете работать в macOS или Linux;
- выполняете подключение к кластеру больших данных SQL Server 2019;
- тратите большую часть времени на изменение или выполнение запросов;
- хотите быстро создавать диаграммы и визуализировать результирующие наборы;
- можете выполнять большинство задач администрирования через встроенный терминал с помощью sqlcmd или PowerShell;
- имеете незначительную потребность в использовании мастера;
- не будете выполнять детализированную административную конфигурацию.

**Используйте SQL Server Management Studio, если вы...**

- тратите большую часть времени на выполнение задач администрирования базы данных;
- выполняете детализированную административную конфигурацию;
- управляете вопросами безопасности, включая управление пользователями, оценку уязвимостей и настройку функций безопасности;
- используете отчеты для хранилища запросов SQL Server;
- будете использовать помощники по настройке производительности и панели мониторинга;
- импортируете и экспортируете пакеты DACPAC;
- хотите получить доступ к зарегистрированным серверам и управлять службами SQL Server в Windows.

### <a name="shell"></a>Оболочка

|Компонент|Azure Data Studio|SSMS|
|:---|:---|:---|
|Вход в Azure|Да|Да|
|Панель мониторинга|Да||
|Модули|Да||
|Встроенный терминал|Да||
|Обозреватель объектов|Да|Да|
|Скрипты объектов|Да|Да|
|Система проектов|Да||
|Выбор из таблицы|Да|Да|
|Управление исходным кодом|Да||
|Панель задач|Да||
|Темы|Да||
|Темный режим|Да||
|Обозреватель ресурсов Azure|Preview (Предварительный просмотр)||
|Мастер создания скриптов||Preview (Предварительный просмотр)|
|Импорт и экспорт DACPAC||Да|
|Свойства объекта||Preview (Предварительный просмотр)|
|конструктор таблиц||Да|

### <a name="query-editor"></a>Редактор запросов

|Компонент|Azure Data Studio|SSMS|
|:---|:---|:---|
|Средство просмотра диаграмм|Да||
|Экспорт результатов в CSV-, JSON-, XLSX-файлы|Да||
|технология IntelliSense|Да|Да|
|Фрагменты кода|Да|Да|
|Показ плана|Preview (Предварительный просмотр)|Да|
|Статистика клиента||Да|
|Статистика активных запросов||Да|
|Параметры запроса||Да|
|В файл||Да|
|В виде текста||Да|
|Средство просмотра пространственных данных||Да|
|SQLCMD||Да|
|Записные книжки|Да||
|Сохранение запроса в виде фрагмента кода|Да||

### <a name="operating-system-support"></a>Поддержка операционных систем

|Компонент|Azure Data Studio|SSMS|
|:---|:---|:---|
|Linux|Да||
|macOS|Да||
|Windows|Да|Да|

### <a name="data-engineering"></a>Инжиниринг данных

|Компонент|Azure Data Studio|SSMS|
|:---|:---|:---|
|Мастер создания внешних таблиц|Да||
|Интеграция HDFS|Да||
|Записные книжки|Да||

### <a name="database-administration"></a>Администрирование базы данных

|Компонент|Azure Data Studio|SSMS|
|:---|:---|:---|
|Резервное копирование и восстановление|Да|Да|
|Поддержка кластеров больших данных|Да||
|Импорт неструктурированных файлов|Preview (Предварительный просмотр)|Да|
|Агент SQL|Preview (Предварительный просмотр)|Да|
|SQL Profiler|Preview (Предварительный просмотр)|Да|
|Всегда включено||Да|
|Always Encrypted||Да|
|Мастер копирования данных||Да|
|Database Engine Tuning Advisor||Да|
|Средство просмотра журнала ошибок||Да|
|Планы обслуживания||Да|
|Многосерверный запрос||Да|
|управление на основе политик||Да|
|PolyBase||Да|
|Хранилище запросов||Да|
|зарегистрированные серверы||Да|
|Репликация||Да|
|Управление безопасностью||Да|
|Компонент Service Broker||Да|
|Служба SQL Mail||Да|
|Template Explorer||Да|
|Оценка уязвимости||Да|
|Управление XEvent||Да|
|Интеграция с API оценки SQL||Да|

## <a name="next-steps"></a>Дальнейшие действия

- [Скачивание и установка Azure Data Studio](./download-azure-data-studio.md?view=sql-server-ver15)
- [Подключение и отправка запроса к SQL Server](quickstart-sql-server.md)
- [Подключение и отправка запроса к базе данных SQL Azure](quickstart-sql-database.md)

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]