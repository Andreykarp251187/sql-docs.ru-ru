---
title: Ошибка ядра СУБД MSSQLSERVER_802 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 802 (Database Engine error)
ms.assetid: 5892ed24-4dcb-4bf9-a8a4-a7ca898832d5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3e15b2614b64b6c5161e8648574f88700d4fd6d8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62797042"
---
# <a name="mssqlserver802---database-engine-error"></a>Ошибка ядра СУБД MSSQLSERVER_802
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|802|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|NO_BUFS|  
|Текст сообщения|Недостаточно свободной памяти в буферном пуле.|  
  
## <a name="explanation"></a>Объяснение  
Это происходит, если буферный пул заполнен и не может больше увеличиваться.  
  
## <a name="user-action"></a>Действие пользователя  
Далее представлены общие шаги, которые помогут при устранении неполадок с памятью.  
  
1.  Проверьте, не используют ли память данного сервера другие приложения или службы. Измените настройки таким образом, чтобы менее важные приложения или службы использовали меньший объем памяти.  
  
2.  Начните сбор счетчиков системного монитора для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **: Buffer Manager**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **: Memory Manager**.  
  
3.  Проверьте следующие параметры конфигурации памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    -   **max server memory**  
  
    -   **min server memory**  
  
    -   **min memory per query**  
  
    Обратите внимание на любые необычные параметры и исправьте их при необходимости. Принимайте во внимание тот факт, что в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предъявляются повышенные требования к доступному объему памяти. Настройки по умолчанию приведены в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в разделе «Настройка параметров конфигурации сервера».  
  
4.  Обратите внимание на сообщения инструкции DBCC MEMORYSTATUS и способ их изменения при появлении сообщений об ошибках.  
  
5.  Проверьте рабочую нагрузку (число параллельных сеансов, выполняющихся запросов).  
  
Следующие действия могут позволить использовать больший объем памяти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Если ресурсы потребляют приложения, выполняющиеся вместе с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], попробуйте остановить эти приложения или выполнить их на отдельном сервере.  
  
-   Если установлен параметр **max server memory**, увеличьте его значение.  
  
Выполните следующие команды DBCC для освобождения нескольких кэшей памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
Если проблема не исчезла, необходимо продолжить ее исследование и, возможно, снизить рабочую нагрузку.  
  
