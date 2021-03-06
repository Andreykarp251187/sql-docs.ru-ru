---
description: Запуск бизнес-объектов в службах компонентов
title: Запуск бизнес-объектов в службах компонентов | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- component services in RDS [ADO]
ms.assetid: 3077d0b6-42d6-4f10-8e5d-42e6204f1109
author: rothja
ms.author: jroth
ms.openlocfilehash: 4343d8e1bd04d7e8044fa7f3f1b5de6184466d3f
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88977725"
---
# <a name="running-business-objects-in-component-services"></a>Запуск бизнес-объектов в службах компонентов
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Бизнес-объекты могут быть исполняемыми файлами (exe) или библиотеками динамической компоновки (. dll). Конфигурация, используемая для запуска бизнес-объекта, зависит от того, является ли объект файлом DLL или exe:  
  
-   Бизнес-объекты, созданные как файлы exe, можно вызывать через DCOM. Если эти бизнес-объекты используются в службы IIS (IIS), они подчиняются дополнительной упаковке данных, что приведет к снижению производительности клиента.  
  
-   Бизнес-объекты, созданные как файлы DLL, можно использовать через IIS, а значит, и по протоколу HTTP. Их также можно использовать через DCOM только через службы компонентов или с помощью Microsoft Transaction Server, если используется Windows NT. Для доступа к ним с помощью IIS на компьютере сервера IIS необходимо зарегистрировать библиотеки бизнес-объектов. Сведения о настройке библиотеки DLL для работы на DCOM см. в разделе [Включение библиотеки DLL для запуска на DCOM](./enabling-a-dll-to-run-on-dcom.md).  
  
> [!NOTE]
>  Если бизнес-объекты на среднем уровне реализуются как компоненты служб компонентов **с помощью функций** **сеткомплете**, а также **SetAbort**, то бизнес-объекты могут использовать службы компонентов (или MTS, если используются контекстные объекты Windows NT) для поддержания состояния между несколькими клиентскими вызовами. Такая ситуация возможна при использовании DCOM, который обычно реализуется между доверенными клиентами и серверами в интрасети. В этом случае [RDS. Объект пространства](../../reference/rds-api/dataspace-object-rds.md) и метод [CreateObject](../../reference/rds-api/createobject-method-rds.md) на стороне клиента заменяются объектом контекста транзакции и методом **CreateInstance** , которые предоставляются интерфейсом **итрансактионконтекст** и реализуются службами компонентов.  
  
## <a name="see-also"></a>См. также  
 [Основные принципы RDS](./rds-fundamentals.md)