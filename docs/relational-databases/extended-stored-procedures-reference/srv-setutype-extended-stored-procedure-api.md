---
title: srv_setutype (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_setutype
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_setutype
ms.assetid: 6160f15d-1b68-411e-ab6d-491ec288f264
author: rothja
ms.author: jroth
ms.openlocfilehash: cfd81188f0e751fb57c2d4a29ce61d574cfe3486
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119621"
---
# <a name="srvsetutype-extended-stored-procedure-api"></a>srv_setutype (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Устанавливает определяемый пользователем тип данных для столбца строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_setutype (  
SRV_PROC *  
srvproc  
,  
int   
column  
,   
DBINT  
user_type   
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, который представляет собой дескриптор соединения с клиентом. Эта структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *column*  
 Указывает, какой столбец устанавливать. Нумерация столбцов начинается с 1.  
  
 *user_type*  
 Указывает код определяемого пользователем типа данных.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL. Если столбец не существует, возвращает значение FAIL.  
  
## <a name="remarks"></a>Remarks  
 Столбец имеет два типа данных: фактический и определяемый пользователем. Определяемый пользователем тип данных используется [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для хранения действительного определяемого пользователем типа данных столбца, и сведения об описании столбца, например допустимость значения NULL и возможность обновления (если таковые существуют).  
  
 Функцию **srv_setutype** можно вызвать в любое время после определения *column* с помощью функции **srv_describe** и до передачи последней строки.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://www.microsoft.com/en-us/msrc?rtc=1).  
  
## <a name="see-also"></a>См. также:  
 [srv_describe (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/srv-describe-extended-stored-procedure-api.md)  
  
  
