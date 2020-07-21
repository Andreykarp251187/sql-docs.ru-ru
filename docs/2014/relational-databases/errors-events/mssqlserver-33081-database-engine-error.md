---
title: MSSQLSERVER_33081 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33081 (Database Engine error)
ms.assetid: 839705e7-fa37-4c0d-9f3f-95a9eab98bcf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 325ade571d62177bd702b791113753ccac890768
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551689"
---
# <a name="mssqlserver_33081"></a>MSSQLSERVER_33081
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|33081|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SEC_DLL_TRUST_VERIFICATION_FAILED|  
|Текст сообщения|Не удалось загрузить поставщик служб шифрования "%.*ls" из-за недействительной подписи Authenticode или недействительного пути к файлу.  Проверьте наличие других ошибок в предыдущих сообщениях.|  
  
## <a name="explanation"></a>Объяснение  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не смог загрузить поставщик служб шифрования, указанный в сообщении об ошибке. Существует несколько ошибок Win API, которые могут вызвать эту ошибку. Кольцевой буфер содержит имя ошибочного API и код ошибки Windows, возвращенный API. Чтобы получить дополнительные сведения, выполните следующий запрос к представлению sys.dm_os_ring_buffers.  
  
```  
SELECT * FROM sys.dm_os_ring_buffers   
WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
```  
  
## <a name="user-action"></a>Действие пользователя  
 Чтобы исследовать эту проблему, выполните поиск кода ошибки Windows в MSDN (https://msdn.microsoft.com/). Устраните ошибку или обратитесь к службу поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] за дополнительными сведениями. Перед обращением в службу поддержки пользователей соберите следующие данные.  
  
-   Журнал ошибок, отображающий ошибку загрузки поставщика служб шифрования.  
  
-   Выход из следующей инструкции:  
  
    ```  
    SELECT * FROM sys.dm_os_ring_buffers   
    WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
    ```  
  
> [!NOTE]  
>  Попробуйте сразу собрать данные кольцевого буфера, поскольку они могут быть потеряны при перезагрузке.  
  
  
