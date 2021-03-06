---
description: Сводка объектной модели RDS
title: Сводка объектной модели RDS | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS objects [ADO], object model summary
- RDS object model [ADO]
ms.assetid: 909f9af7-31db-4eec-ad52-650ce74dac2f
author: rothja
ms.author: jroth
ms.openlocfilehash: e2650f9a80c56856133d1e694a5ea0eb807251f0
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88977985"
---
# <a name="rds-object-model-summary"></a>Сводка объектной модели RDS
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
|Объект|Описание|  
|------------|-----------------|  
|[Клиент. Пространство данных](../../reference/rds-api/dataspace-object-rds.md)|Этот объект содержит метод для получения прокси сервера. Может использоваться прокси-сервер по умолчанию или пользовательская программа (бизнес-объект). Серверная программа может быть вызвана в Интернете, интрасети, локальной сети или в виде локальной библиотеки динамической компоновки.<br /><br /> Объект **Space** является надежным для скриптов.|  
|[RDSServer. факт.](../../reference/rds-api/datafactory-object-rdsserver.md)|Этот объект представляет программу сервера по умолчанию. Он выполняет получение данных RDS по умолчанию и поведение обновления.<br /><br /> Объект **фактов** не является надежным для сценариев.|  
|[Клиент. DataControl](../../reference/rds-api/datacontrol-object-rds.md)|Этот объект может автоматически вызывать **RDS. Объекты Space** и **RDSServer. объект фактов** .<br /><br /> Используйте этот объект, чтобы вызвать получение данных RDS по умолчанию или поведение обновления.<br /><br /> Этот объект также предоставляет средства визуальных элементов управления для доступа к возвращенному объекту **набора записей** .<br /><br /> Объект " **элемент управления** " является надежным для сценариев.|  
  
## <a name="see-also"></a>См. также  
 [Основы RDS](./rds-fundamentals.md)   
 [Сценарий RDS](./rds-scenario.md)   
 [Руководство по RDS](./rds-tutorial.md)   
 [Использование RDS и безопасность](./rds-usage-and-security.md)