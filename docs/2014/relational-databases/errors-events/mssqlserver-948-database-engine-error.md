---
title: MSSQLSERVER_948 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "948"
helpviewer_keywords:
- 948 (Database Engine error)
ms.assetid: 95c4ad45-a518-4165-a5c4-6e6b932b0570
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b3d55dca978b4383a1a28b0103750b42a294095f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62912577"
---
# <a name="mssqlserver_948"></a>MSSQLSERVER_948
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|948|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|Н/Д|  
|Текст сообщения|Не удалось открыть базу данных «%.*ls», поскольку она имеет версию %d. Данный сервер поддерживает версию %d и более ранние. Переход на предыдущую версию не поддерживается.|  
  
## <a name="explanation"></a>Объяснение  
 Некоторые особенности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] влияют на структуру файлов базы данных. При добавлении базы данных на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файл форматирования может оказаться несовместимым с другой версией компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Например, эта ошибка может возникнуть при использовании формата хранения vardecimal в более поздней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и при последующей попытке добавить файлы базы данных в версию более раннюю, чем [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] с пакетом обновления 2 (SP2).  
  
## <a name="user-action"></a>Действие пользователя  
 Определите версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], запущенную на исходном сервере. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]либо щелкните правой кнопкой мыши сервер, а затем выберите пункт **свойства** или `SELECT @@VERSION` введите в окне запроса. Откройте базу данных с помощью исходной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Изучите функции, которые включены в исходной базе данных экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Измените параметры для работы с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в которой будет выполняться добавление базы данных.  
  
  
