---
title: Свойство EOS | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EOS
- Stream::EOS
helpviewer_keywords:
- EOS property
ms.assetid: 57e08c5f-f3ed-4ecd-8c66-50b83b1031d1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47b3e48e612e0ee5595ada33127f016ee6b986f1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63180998"
---
# <a name="eos-property"></a>Свойство EOS
Указывает, является ли текущая позиция в конце [поток](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="return-values"></a>Возвращаемые значения  
 Возвращает **логическое** значение, указывающее, является ли текущая позиция в конце потока. **EOS** возвращает **True** при наличии байты в поток; он возвращает **False** при наличии большее число байтов после текущего положения.  
  
 Чтобы обозначить конец позицию в потоке, используйте [SetEOS](../../../ado/reference/ado-api/seteos-method.md) метод. Чтобы определить текущую позицию, используйте [позиции](../../../ado/reference/ado-api/position-property-ado.md) свойство.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [EOS и LineSeparator свойства и метод SkipLine (Visual Basic)](../../../ado/reference/ado-api/eos-and-lineseparator-properties-and-skipline-method-example-vb.md)   
 [Объект Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
