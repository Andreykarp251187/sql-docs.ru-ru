---
title: Использование пользовательских сборок со строгими именами | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-assemblies
ms.topic: reference
helpviewer_keywords:
- AllowPartiallyTrustedCallersAttribute attribute
- strong-named custom assemblies [Reporting Services]
- strong names [Reporting Services]
- assemblies [Reporting Services], strong names
- custom assemblies [Reporting Services], strong-named
ms.assetid: ca9f19d7-6e86-46f2-b9ad-9bf807eaa52e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 31479ae9b460b6a660ec865e68e46afd912f49b6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63194084"
---
# <a name="using-strong-named-custom-assemblies"></a>Использование пользовательских сборок со строгими именами
  Строгое имя идентифицирует сборку и включает текстовое имя сборки, четырехкомпонентный номер версии, сведения о культуре (если они указаны), открытый ключ и цифровую подпись, хранящуюся в манифесте сборки. Строгое имя уникальным образом определяет сборку в среде CLR и гарантирует целостность двоичных файлов.  
  
## <a name="using-allowpartiallytrustedcallersattribute"></a>Использование атрибута AllowPartiallyTrustedCallersAttribute  
 Чтобы использовать с отчетами сборки со строгими именами, необходимо разрешить вызов сборки со строгим именем из частично доверенного кода. Для этого используется атрибут **AllowPartiallyTrustedCallers** сборки. С помощью атрибута **AllowPartiallyTrustedCallersAttribute** можно разрешить вызов сборок со строгими именами в выражениях отчетов из конструктора отчетов или с сервера отчетов. Чтобы разрешить вызов сборок со строгими именами из частично доверенного кода, добавьте в файл атрибутов сборки следующий атрибут уровня сборки.  
  
```vb  
<assembly:AllowPartiallyTrustedCallers>  
```  
  
```csharp  
[assembly:AllowPartiallyTrustedCallers]  
```  
  
 Атрибут **AllowPartiallyTrustedCallersAttribute** действует только при применении сборкой со строгим именем на уровне сборки. Дополнительные сведения о применении атрибутов на уровне сборки см. в разделе "Применение атрибутов" документации по пакету SDK [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
> [!CAUTION]  
>  Если присутствует атрибут **AllowPartiallyTrustedCallersAttribute**, то стандартная проверка безопасности **FullTrustLinkDemand** блокируется, что позволяет вызывать сборку из любой другой частично доверенной сборки. Все виды проверки безопасности, в том числе декларативные атрибуты безопасности уровня класса или уровня метода, необходимо указывать явно.  
  
## <a name="see-also"></a>См. также:  
 [Использование пользовательских сборок с отчетами](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
