---
title: Передача параметра отчета в URL-адресе | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], passing parameters
- passing parameters [Reporting Services]
ms.assetid: f93a94cc-27b5-435a-aa85-69e6ec6459ad
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 551fc19b3d39ef6cf12c5fdd4e77196b0abbb9fe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65580838"
---
# <a name="pass-a-report-parameter-within-a-url"></a>Pass a Report Parameter Within a URL
  Чтобы передать параметры в отчет, можно включить их в URL-адрес отчета. Такие параметры URL-адреса не снабжаются префиксами, поскольку они передаются непосредственно в подсистему обработки отчетов.  

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступна после выхода SQL Server 2016.
  
> [!IMPORTANT]  
>  Важно, чтобы URL-адрес содержал синтаксис прокси `_vti_bin` для отправки запроса с помощью центра администрирования SharePoint и прокси-сервера HTTP [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Прокси-сервер добавляет в HTTP-запрос контекст, необходимый для обеспечения правильного выполнения отчета для серверов отчетов в режиме интеграции с SharePoint.  
>   
>  Если не указывать синтаксис прокси, то нужно добавить к параметру префикс *rp:* .  
  
 Все параметры запроса могут иметь соответствующие параметры отчета. Параметр запроса можно передать в отчет. Дополнительные сведения см. в статье [Построение запроса в конструкторе реляционных запросов (построитель отчетов и службы SSRS)](../reporting-services/report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).  
  
> [!IMPORTANT]
>  В параметрах отчета учитывается регистр символов.  
> 
> [!NOTE]
>  Параметры отчета учитывают регистр символов и используют следующие специальные символы:  
> 
>  -   Все пробельные символы в строке URL-адресов заменяются символами «%20» в соответствии со стандартами кодировки URL-адресов.  
> -   Пробел в секции параметров URL-адреса заменяется символом плюса (+).  
> -   Точка с запятой в любой части строки заменяется символами «%3A».  
> -   Браузер должен автоматически выполнить необходимую кодировку URL-адреса. Пользователю нет необходимости выполнять кодировку символов вручную.  
  
 Чтобы задать параметр отчета в URL-адресе, используйте следующий синтаксис:  
  
```  
  
parameter=value  
```  
  
 Например, чтобы указать параметры ReportMonth и ReportYear, заданные в отчете, используйте следующий URL-адрес для сервера отчетов, работающего в собственном режиме:  
  
```  
https://myrshost/ReportServer?/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2&ReportMonth=3&ReportYear=2008  
```  
  
 Например, чтобы указать те же два параметра, заданные в отчете, используйте следующий URL-адрес для сервера отчетов, работающего в режиме интеграции c SharePoint. Обратите внимание на `/_vti_bin`!  
  
```  
https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2.rdl&ReportMonth=3&ReportYear=2008  
```  
  
 Чтобы задать параметру значение NULL, используйте следующий синтаксис:  
  
```  
  
parameter  
:isnull=true  
  
```  
  
 Например,  
  
```  
SalesOrderNumber:isnull=true  
```  
  
 Чтобы задать значение **Boolean** , используйте 0 для значения ложь и 1 для значения верно. Чтобы задать значение **Float** , включите десятичный разделитель для языкового стандарта сервера  
  
> [!NOTE]  
>  Если отчет содержит параметр отчета, имеющий значение по умолчанию, а свойство **Prompt** имеет значение **false** (то есть в диспетчере отчетов не выбрано свойство Подсказка пользователю), передать значение этого параметра отчета в URL-адресе невозможно. Это позволяет администраторам запретить пользователям добавлять и изменять значения определенных параметров отчета.  
  
##  <a name="bkmk_examples"></a> Дополнительные примеры  
 В следующем примере URL-адрес содержит пробелы и многозначные параметры.  
  
-   Имя папки "Группы образования пользователя SQL Server" содержит пробелы, которые заменяются знаком "+".  
  
-   Имя отчета "Отчет по командному проекту" содержит пробелы, которые заменяются знаком "+".  
  
-   Передает два параметра: teamgrouping2 со значением xgroup и teamgrouping1 со значением ygroup.  
  
```  
https://myserver/Reportserver?/SQL+Server+User+Education+Team/_ContentTeams/folder123/team+project+report&teamgrouping2=xgroup&teamgrouping1=ygroup  
```  
  
 В следующем примере URL-адрес содержит многозначный параметр OrderID. Формат многозначного параметра должен повторять имя параметра для каждого значения.  
  
```  
https://myserver/Reportserver?/SQL+Server+User+Education+Team/_ContentTeams/folder123/team+project+report&teamgrouping2=xgroup&teamgrouping1=ygroup&OrderID=747&OrderID=787&OrderID=12  
```  
  
 В следующем примере URL-адреса передается один параметр *SellStartDate* со значением 1.7.2005 для сервера отчетов, работающего в основном режиме.  
  
```  
https://myserver/ReportServer/Pages/ReportViewer.aspx?%2fProduct_and_Sales_Report_AdventureWorks&SellStartDate=7/1/2005  
```  
  
## <a name="see-also"></a>См. также:  
 [Доступ по URL-адресу (службы SSRS)](../reporting-services/url-access-ssrs.md)   
 [Ссылка на параметр доступа по URL-адресу](../reporting-services/url-access-parameter-reference.md)  
  
  
