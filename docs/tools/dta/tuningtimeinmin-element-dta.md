---
title: Элемент TuningTimeInMin (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningTimeInMin element
ms.assetid: 4973d9ac-20fd-4ac3-bc9f-5d60e39fdb7d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b1b5c836f3c318429757d1d4786876275edcf03c
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67729510"
---
# <a name="tuningtimeinmin-element-dta"></a>Элемент TuningTimeInMin (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Позволяет задать максимальную длительность сеанса настройки в минутах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <TuningTimeInMin>...</TuningTimeInMin>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**unsignedInt**, неограниченная длина|  
|**Значение по умолчанию**|480 минут (8 часов)|  
|**Наличие**|Требуется в случае, если не задано значение элемента **NumberOfEvents** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент TuningOptions (DTA)](../../tools/dta/tuningoptions-element-dta.md)|  
|**Дочерние элементы**|None|  
  
## <a name="example"></a>Пример  
  
## <a name="description"></a>Описание  
 В следующем примере кода показано, как установить максимальное время настройки — 12 часов:  
  
## <a name="code"></a>Код  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <TuningTimeInMin>720</TuningTimeInMin>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
