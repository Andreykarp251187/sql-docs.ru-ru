---
title: Метод stat | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Stat
helpviewer_keywords:
- Stat method [ADO]
ms.assetid: 99a2b2d4-e6b1-4205-b011-72d024ea7240
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 127aab5e00247ce5550f25e2a281e190472b0186
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62740344"
---
# <a name="stat-method"></a>Метод Stat
Извлекает сведения о [Stream](../../../ado/reference/ado-api/stream-object-ado.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Long stream.Stat(StatStg, StatFlag)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **Long** значение, указывающее состояние операции.  
  
#### <a name="parameters"></a>Параметры  
 *StatStg*  
 Структура STATSTG, будут заполнены сведения о потоке. Реализация **Stat** метод, используемый в объекте ADO Stream не заполните все поля структуры.  
  
 *StatFlag*  
 Указывает, что этот метод не возвращает некоторые члены в структуре STATSTG, что экономит операция выделения памяти. Значения берутся из перечисления STATFLAG. Перечисление STATFLAG имеет два значения  
  
|Константа|Значение|  
|--------------|-----------|  
|STATFLAG_DEFAULT|0|  
|STATFLAG_NONAME|1|  
  
## <a name="remarks"></a>Примечания  
 В следующих полях структуры STATSTG заполняет версию Stat метод, реализованный в объекте ADO Stream:  
  
 *pwcsName*  
 Строка, содержащая имя потока, если он доступен и STATFLAG_NONAME StatFlag значение не указано.  
  
 *cbSize*  
 Указывает размер в байтах для потока или массива байтов.  
  
 *mtime*  
 Указывает время последнего изменения для этого хранилища, потока или массива байтов.  
  
 *CTime*  
 Указывает время создания для этого хранилища, потока или массива байтов.  
  
 *atime*  
 Указывает время последнего обращения для данного хранилища, потока или массива байтов.  
  
 Если STATFLAG_NONAME указан в параметре StatFlag, имя потока не возвращается.  
  
 Если STATFLAG_NONAME не указан в параметре StatFlag отсутствует имя для текущего потока, это значение будет E_NOTIMPL.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
