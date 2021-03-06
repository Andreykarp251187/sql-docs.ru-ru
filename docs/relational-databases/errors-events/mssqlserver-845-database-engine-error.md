---
description: MSSQLSERVER_845
title: MSSQLSERVER_845 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 845 (Database Engine error)
ms.assetid: 8fff6ad4-234c-44be-b123-e25d5e1cd63e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b4d474714579397d18e22f2c32cc540ff30d5ac0
ms.sourcegitcommit: a0245fdae1ff9045f587a3a67b72f34405d35a4f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2020
ms.locfileid: "88618073"
---
# <a name="mssqlserver_845"></a>MSSQLSERVER_845
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|845|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|BUFLATCH_TIMEOUT|  
|Текст сообщения|Истекло время ожидания кратковременной блокировки буфера — тип %d, страница %S_PGID, идентификатор базы данных %d.|  
  
## <a name="explanation"></a>Объяснение  
Процесс ожидал получения кратковременной блокировки, но время ожидания истекло, и блокировку не удалось получить. Это может произойти, если операциях ввода-вывода выполняется слишком долго. Обычно это происходит в результате блокировки системных процессов другими задачами. В некоторых случаях эта ошибка может возникать в результате сбоя оборудования.  
  
## <a name="cause"></a>Причина
Это сообщение об ошибке зависит от общей среды системы. Любое из следующих условий может привести к чрезмерной нагрузке на систему.

- Оборудование, не удовлетворяющее требованиям ввода-вывода и потребности в памяти
- Неправильно настроенные и проверенные параметры
- Неэффективная структура

 Когда ваша система сильно загружена и не может удовлетворить потребности рабочей нагрузки, может возникнуть ошибка 845. Вот некоторые из наиболее распространенных причин перегруженности среды.

- Проблемы с оборудованием
- Сжатые тома
- Нестандартные параметры конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
- Неэффективные запросы или проектирование индексов
- Частые операции автоматического увеличения или сжатия базы данных

## <a name="user-action"></a>Действие пользователя  
Для предотвращения этой ошибки попробуйте предпринять следующее.  
  
- Определите наличие узких мест в оборудовании. См. рекомендации в разделе [Выявление узких мест](../performance/identify-bottlenecks.md). При необходимости обновите оборудование, чтобы оно могло обслуживать потребности среды в конфигурации, запросах и нагрузке.

- Убедитесь, что оборудование работает правильно. Проверьте все зарегистрированные в журнале ошибки и запустите программу диагностики, предоставляемую поставщиком оборудования. В журнале ошибок или журнале событий проверьте соответствующие сбои операций ввода-вывода. Сбои операций ввода-вывода обычно указывают на неправильную работу диска.  
- Убедитесь, что тома на дисках не сжаты. Хранение файлов данных и журналов на сжатых дисках не поддерживается; см. [Файлы базы данных и файловые группы](../databases/database-files-and-filegroups.md). Дополнительные сведения о поддержке сжатых дисков см. в следующей статье. [Базы данных SQL Server не поддерживаются на сжатых томах](https://support.microsoft.com/EN-US/help/231347)

- Проверьте, исчезают ли сообщения об ошибках при отключении всех следующих параметров конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
   - [Параметр повышения приоритета](../../database-engine/configure-windows/configure-the-priority-boost-server-configuration-option.md)
   - [Параметр использования упрощенных пулов (в режиме волокон)](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)
   - [Параметр set working set size](../../database-engine/configure-windows/set-working-set-size-server-configuration-option.md)

    Дополнительные сведения см. в разделе [ПРАКТИЧЕСКОЕ РУКОВОДСТВО. Определение надлежащих параметров конфигурации SQL Server](https://support.microsoft.com/EN-US/help/319942).

- Настройте запросы таким образом, чтобы система потребляла меньший объем ресурсов. Настройка производительности поможет снизить нагрузку на систему и сократить время отклика отдельных запросов.
- Присвойте свойству AutoShrink значение OFF для снижения затрат на изменение размера базы данных.
- Убедитесь, что приращения, заданные с помощью свойства AutoGrow, имеют достаточный объем, чтобы их можно было редко выполнять. Запланируйте задание проверки доступного места на диске в базах данных, затем задайте увеличение размера базы данных в периоды наименьшей нагрузки.
- В журнале ошибок проверьте наличие невыполненных задач и других критических ошибок. Сначала устраните эти ошибки, так как они могут указывать на основную причину проблемы.
- Если критические ошибки встречаются часто, устраните их причину.
- Если сообщения об ошибке 845 возникают редко, их можно пропустить.