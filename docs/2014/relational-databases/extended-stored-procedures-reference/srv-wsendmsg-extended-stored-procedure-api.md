---
title: srv_wsendmsg (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_wsendmsg
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_wsendmsg
ms.assetid: f2153076-32c9-4a52-8e1b-fc9618153543
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 18b166472cff011b3766645dde61f562c766ff2c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63140451"
---
# <a name="srv_wsendmsg-extended-stored-procedure-api"></a>srv_wsendmsg (API-интерфейс расширенных хранимых процедур)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Вместо этого используйте интеграцию со средой CLR.  
  
 Отправляет клиенту сообщение в Юникоде.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_wsendmsg(SRV_PROC *   
srvproc  
, int   
msgnum  
, int   
severity  
, WCHAR *   
message  
, int   
msglen  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, который представляет собой дескриптор соединения с клиентом. Эта структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *Номерсообщения*  
 4-байтовый номер сообщения.  
  
 *Severity*  
 Указывает серьезность ошибки. Серьезность, меньше или равная 10, считается информационным сообщением, в противном случае — ошибкой.  
  
 *Сообщение*  
 Является указателем на строку в Юникоде, которая должна быть отправлена клиенту.  
  
 *msglen*  
 Указывает длину *message*в символах.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Remarks  
 Эта функция используется для отправки сообщения в Юникоде. Она сходна с функцией **srv_sendmsg**, но сообщение, которое она отправляет, является строкой типа WCHAR, а не строкой типа DBCHAR. Следует отметить, что длина сообщения считается в символах, а не в байтах, а также *msglen* никогда не будет равно SRV_NULLTERM.  
  
 Функция возвращает значение FAIL, если:  
  
-   значение *msglen* лежит вне диапазона 0-32242;  
  
-   значение *msglen* равно 0, но значение указателя сообщения равно NULL;  
  
-   при отправке сообщения об ошибке через сеть возникает ошибка.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>См. также:  
 [API srv_sendmsg &#40;расширенных хранимых процедур&#41;](srv-sendmsg-extended-stored-procedure-api.md)  
  
  
