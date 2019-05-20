---
title: Функции служб Integration Services, поддерживаемые различными выпусками SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e5018225-68bb-4f34-ae4a-ead79d8ad13a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5207da1170eea9cfbd90d9461776131f738cd3d9
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65723611"
---
# <a name="integration-services-features-supported-by-the-editions-of-sql-server"></a>Функции служб Integration Services, поддерживаемые различными выпусками SQL Server

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


 В этом разделе подробно описаны функции служб SQL Server Integration Services (SSIS), поддерживаемые различными выпусками [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)].  

В приведенных ниже таблицах функции, поддерживаемые выпусками Evaluation и Developer, в указаны в наборе функций для выпуска Enterprise.
  
Актуальные заметки о выпуске и сведения о новых возможностях содержатся в следующих статьях:
-   [Заметки о выпуске для SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
-   [Новые возможности служб Integration Services в SQL Server 2016](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)
-   [Новые возможности служб Integration Services в SQL Server 2017](../integration-services/what-s-new-in-integration-services-in-sql-server-2017.md)
    
**Оцените SQL Server 2016!**    

Выпуск SQL Server Evaluation доступен для ознакомления в течение 180 дней.  
    
> [![Скачать на странице центра оценки](../analysis-services/media/download.png)](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) **[Скачайте SQL Server 2016 на странице центра оценки](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)**    
    
## <a name="ISNew"></a> Новые функции служб Integration Services в SQL Server 2017
  
|Компонент|Enterprise|Standard|Web Edition|Express с дополнительными службами|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Мастер Scale Out|Да|||||
|Рабочая роль Scale Out|Да|Да <sup>1</sup>|TBD|TBD|TBD|
|Поддержка Microsoft Dynamics CRM и Microsoft Dynamics AX в компонентах OData <sup>2</sup>|Да|Да||||

<sup>1</sup> Если вы запускаете пакеты, которым в Scale Out требуются функции из выпуска Enterprise, рабочие роли Scale Out также должны выполняться на экземплярах SQL Server Enterprise.

<sup>2</sup> Эта функция также поддерживается в SQL Server 2016 с пакетом обновления 1 (SP1).

## <a name="IEWiz"></a> Мастер импорта и экспорта SQL Server

|Компонент|Enterprise|Standard|Web Edition|Express с дополнительными службами|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|мастер импорта и экспорта SQL Server|Да|Да|Да|Да|Да|  

## <a name="IS"></a> Службы Integration Services  
  
|Компонент|Enterprise|Standard|Web Edition|Express с дополнительными службами|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Встроенные соединители источника данных|Да|Да|||| 
|Встроенные задачи и преобразования|Да|Да||||  
|Источник и назначение ODBC |Да|Да|||| 
|Соединители источника данных Azure и задачи|Да|Да||||  
|Соединители и задачи Hadoop и HDFS|Да|Да||||  
|Средства профилирования основных данных|Да|Да|||| 

## <a name="ISAA"></a> Службы Integration Services — дополнительные источники и назначения  
  
|Компонент|Enterprise|Standard|Web Edition|Express с дополнительными службами|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Высокопроизводительные источник и назначение Oracle от Attunity|Да|||||  
|Высокопроизводительные источник и назначение Teradata от Attunity|Да|||||  
|Источник и назначение SAP BW|Да|||||  
|Назначение "Обучение модели интеллектуального анализа данных"|Да|||||  
|Назначение "Обработка измерений"|Да|||||  
|Назначение "Обработка секций"|Да|||||  
  
## <a name="ISAT"></a> Службы Integration Services — дополнительные задачи и преобразования  
  
|Компонент|Enterprise|Standard|Web Edition|Express с дополнительными службами|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Компоненты службы Change Data Capture от Attunity<sup>1</sup>|Да|||||  
|Преобразование «Запрос интеллектуального анализа данных»|Да|||||  
|Преобразования "Нечеткое группирование" и "Нечеткий уточняющий запрос"|Да|||||  
|Извлечение терминов и преобразование "Уточняющий запрос термина"|Да|||||  

<sup>1</sup> Компонентам службы Change Data Capture от Attunity требуется выпуск Enterprise. Однако службе Change Data Capture Service и конструктору отслеживания измененных данных выпуск Enterprise не требуется. Вы можете использовать службу и конструктор на компьютере, где не установлены службы SSIS.
