---
title: Добавление кода в отчет | Документация Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
helpviewer_keywords:
- code [Reporting Services]
- custom code [Reporting Services]
- expressions [Reporting Services], code
- adding code
- reports [Reporting Services], code
ms.assetid: 00ef8fc6-99fe-49b2-8a22-7eb475881dc4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bd2f5d60bacc29a5b7efcf1abb8c1d44429d93f6
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "77081668"
---
# <a name="add-code-to-a-report-ssrs"></a>Добавление кода в отчет (службы SSRS)
  В любом выражении можно вызвать собственный пользовательский код. Данный код можно предоставить следующими способами.  
  
-   Напрямую внедрить в отчет код, написанный на [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] . Если код ссылается на классы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], не принадлежащие пространству имен <xref:System.Math> или <xref:System.Convert>, то в отчет нужно добавить ссылку. Дополнительные сведения см. в разделе [Добавление в отчет ссылки на сборку (службы SSRS)](../../reporting-services/report-design/add-an-assembly-reference-to-a-report-ssrs.md). Дополнительные сведения о других ссылках, которые можно выполнить из кода, см. в разделе [Пользовательский код и ссылки на сборки в выражениях в конструкторе отчетов (службы SSRS)](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
-   Предоставить сборку пользовательского кода, использующего платформу [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Если предоставляется пользовательская сборка, ее следует установить как на компьютере, на котором создается отчет, так и на сервере отчетов, где выполняется просмотр отчета. Дополнительные сведения см. в статье [Using Custom Assemblies with Reports](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md).  
  
### <a name="to-add-embedded-code-to-a-report"></a>Добавление в отчет внедренного кода  
  
1.  В режиме **конструктора** щелкните правой кнопкой мыши в области конструктора за границей отчета и выберите команду **Свойства отчета**.  
  
2.  Щелкните **Код**.  
  
3.  В поле **Пользовательский код**введите код. Если при выполнении отчета в коде возникают ошибки, то выводятся предупреждения. В следующем примере создается пользовательская функция с именем `ChangeWord` , заменяющая слово «`Bike`» словом «`Bicycle`».  
  
    ```  
    Public Function ChangeWord(ByVal s As String) As String  
       Dim strBuilder As New System.Text.StringBuilder(s)  
       If s.Contains("Bike") Then  
          strBuilder.Replace("Bike", "Bicycle")  
          Return strBuilder.ToString()  
          Else : Return s  
       End If  
    End Function  
    ```  
  
4.  В следующем примере показывается, как с помощью выражения передать этой функции поле набора данных с именем «Категория».  
  
    ```  
    =Code.ChangeWord(Fields!Category.Value)  
    ```  
  
     Если поместить такое выражение в ячейку таблицы, отображающую значения категории, то при возникновении в поле набора данных для данной строки слова «Bike», в качестве значения ячейки таблицы будет отображено слово «Bicycle».  
  
## <a name="see-also"></a>См. также:  
 [Диалоговое окно «Свойства отчета» — «Код»](https://msdn.microsoft.com/library/955d4b11-17b4-4f1c-9690-6e7af54caea7)   
 [Примеры выражений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Ссылки на коллекцию параметров (построитель отчетов и службы SSRS)](../../reporting-services/report-design/built-in-collections-parameters-collection-references-report-builder.md)  
  
  
