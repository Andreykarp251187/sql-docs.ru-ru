---
description: Модель программирования RDS с объектами
title: Модель программирования RDS с объектами | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS programming model [ADO]
- RDS objects [ADO]
ms.assetid: 07ce0ef0-72f1-48f4-823d-1b65d28c0926
author: rothja
ms.author: jroth
ms.openlocfilehash: 2658b8b7591284f1624f3649e3980db6e2022726
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88977955"
---
# <a name="rds-programming-model-with-objects"></a>Модель программирования RDS с объектами
Целью RDS является получение доступа к источникам данных и их обновление через промежуточные носители, такие как IIS. Модель программирования указывает последовательность действий, необходимых для выполнения этой цели. Объектная модель определяет объекты, методы и свойства которых влияют на модель программирования.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 RDS предоставляет средства для выполнения следующей последовательности действий:  
  
-   Укажите программу, которая будет вызываться на сервере, и получите способ (прокси) для ссылки на него из клиента ([RDS. Пространство](../../reference/rds-api/dataspace-object-rds.md).  
  
-   Вызов серверной программы. Передайте в серверную программу параметры, определяющие источник данных, и выдаваемый командой (прокси-сервер или [RDS). Элемент управления](../../reference/rds-api/datacontrol-object-rds.md).  
  
-   Серверная программа получает объект [набора записей](../../reference/ado-api/recordset-object-ado.md) из источника данных, обычно с помощью ADO. При необходимости объект **набора записей** обрабатывается на сервере ([RDSServer.](../../reference/rds-api/datafactory-object-rdsserver.md)DataObject).  
  
-   Серверная программа возвращает последний объект **набора записей** в клиентское приложение (прокси).  
  
-   На клиенте объект **набора записей** помещается в форму, которая может быть легко использована визуальными элементами управления (визуальным элементом управления и **RDS). Элемент управления**.  
  
-   Изменения объекта **набора записей** отправляются обратно на сервер и используются для обновления источника данных (**RDS. Элемент управления** или **RDSServer. факт**.  
  
## <a name="see-also"></a>См. также  
 [Сводка объектной модели RDS](./rds-object-model-summary.md)   
 [Объект элемента управления (RDS)](../../reference/rds-api/datacontrol-object-rds.md)   
 [Объект фактического объекта (RDSServer)](../../reference/rds-api/datafactory-object-rdsserver.md)   
 [Объект Space (RDS)](../../reference/rds-api/dataspace-object-rds.md)   
 [Сценарий RDS](./rds-scenario.md)   
 [Руководство по RDS](./rds-tutorial.md)   
 [Объект Recordset (ADO)](../../reference/ado-api/recordset-object-ado.md)   
 [Использование RDS и безопасность](./rds-usage-and-security.md)