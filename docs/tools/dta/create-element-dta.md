---
title: элемент Create (DTA)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Create element (DTA)
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: c12803dc07617012a6da22b130c2cd954a82c04e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75307991"
---
# <a name="create-element-dta"></a>элемент Create (DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Содержит сведения об индексах, статистике или структурах кучи в указанной пользователем конфигурации.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Recommendation>  
    <Create>  
    ...code removed here...  
    </Create>  
</Recommendation>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|**Тип данных и длина**|Нет.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Данный элемент должен быть указан один раз для каждого типа структур физического проектирования (индексов, статистики или структур кучи).|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Recommendation (DTA)](../../tools/dta/recommendation-element-dta.md)|  
|**Дочерние элементы**|[Элемент Index (DTA)](../../tools/dta/index-element-dta.md)<br /><br /> Элемент**Statistics** (см. раздел [XML-схема помощника по настройке ядра СУБД](https://schemas.microsoft.com/sqlserver/) )<br /><br /> Элемент**Heap** (см. раздел [XML-схема помощника по настройке ядра СУБД](https://schemas.microsoft.com/sqlserver/) )|  
  
## <a name="remarks"></a>Remarks  
 Этот элемент с именем **CreateTypecomplexType** определен в схеме XML помощника по настройке ядра СУБД. Он используется для создания индексов, статистики и структур кучи для указанной пользователем конфигурации. Не путайте этот элемент **Create** с другими типами, которые можно использовать для создания представлений (**CreateViewType**) или секционирования (**CreatePType**). Дополнительные сведения об этих и других типах элемента [Create](https://schemas.microsoft.com/sqlserver/) см. в разделе **XML-схема помощника по настройке ядра СУБД** .  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
