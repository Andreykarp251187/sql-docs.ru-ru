---
description: Характеристики курсора и блокировки
title: Параметры курсора и блокировки | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- locks [ADO], characteristics
- adOpenDynamic [ADO]
- cursors [ADO], characteristics
ms.assetid: 459c29cb-4230-42bf-8cc2-f3132ccc7aba
author: rothja
ms.author: jroth
ms.openlocfilehash: 4bd8b88ab3a90669982a752023d8a983c188dcbf
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991465"
---
# <a name="cursor-and-lock-characteristics"></a>Характеристики курсора и блокировки
Хотя характеристики курсора зависят от возможностей поставщика, следующие преимущества и недостатки обычно применяются к различным типам курсоров и блокировок.  
  
|Тип курсора или блокировки|Преимущества|Недостатки|  
|-------------------------|----------------|-------------------|  
|**адопенфорвардонли**|-Низкие требования к ресурсам|-Невозможно прокрутить назад<br />-Нет параллелизма данных|  
|**adOpenStatic**|— Прокручиваемый|-Нет параллелизма данных|  
|**adOpenKeyset**|— Некоторый параллелизм данных<br />— Прокручиваемый|-Более высокие требования к ресурсам<br />— Недоступно в сценарии отключения|  
|**adOpenDynamic**|— Высокая степень параллелизма данных<br />— Прокручиваемый|— Максимальные требования к ресурсам<br />— Недоступно в сценарии отключения|  
|**адлоккреадонли**|-Низкие требования к ресурсам<br />— Высокая масштабируемость|— Данные не обновляются с помощью курсора.|  
|**адлоккбатчоптимистик**|-Пакетные обновления<br />— Разрешает сценарии отключения.<br />— Другие пользователи могут получать доступ к данным|— Данные могут быть изменены несколькими пользователями одновременно|  
|**адлоккпессимистик**|-Данные не могут быть изменены другими пользователями, если они заблокированы|— Запрещает другим пользователям доступ к данным во время блокировки|  
|**adLockOptimistic**|— Другие пользователи могут получать доступ к данным|— Данные могут быть изменены несколькими пользователями одновременно|
