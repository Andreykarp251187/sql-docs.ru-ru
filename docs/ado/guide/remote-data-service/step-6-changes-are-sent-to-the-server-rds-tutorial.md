---
title: Шаг 6. Изменения отправляются на сервер (учебник по RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], changes sent to server
ms.assetid: b1e927d6-7d50-4978-9eef-045043cdce7a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8bfeb9ad607fc35c055e025fcc67435323d3143e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955721"
---
# <a name="step-6-changes-are-sent-to-the-server-rds-tutorial"></a>Шаг 6. Изменения отправлены на сервер (учебник по RDS)
Если **записей** редактирования объекта, любые изменения (то есть строк, которые добавлены, изменены или удалены) могут отправляться на сервер.  
  
> [!NOTE]
>  По умолчанию служб удаленных рабочих СТОЛОВ могут вызываться неявно с объектами ADO и поставщик Microsoft OLE DB удаленного взаимодействия. Запросы могут возвращать **записей**s и измененный **записей**s может обновить источник данных. Этот учебник не вызывает RDS с объектами ADO, но это, как она будет выглядеть при как:  
  
```vb
Dim rs as New ADODB.Recordset  
rs. "SELECT * FROM Authors","=MS Remote;=Pubs;" & _  
=https://yourServer;=SQLOLEDB;"  
...              ' Edit the Recordset.  
rs.   ' The equivalent of   
...  
```  
  
 **Часть** Предположим, что для этого случая, который вы использовали только [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) и что **записей** объекта теперь связан с **RDS. DataControl**. [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) метод обновляет источник данных изменений, вносимых в **записей** Если [Server](../../../ado/reference/rds-api/server-property-rds.md) и [Connect](../../../ado/reference/rds-api/connect-property-rds.md) свойства по-прежнему устанавливаются.  
  
```vb
Sub RDSTutorial6A()  
Dim DC as New RDS.DataControl  
Dim RS as ADODB.Recordset  
DC. = "https://yourServer"  
DC. = "DSN=Pubs"  
DC. = "SELECT * FROM Authors"  
DC.  
...  
Set RS = DC.  
   ' Edit the Recordset.  
...  
DC.  
...  
```  
  
 **Часть Б** в качестве альтернативы Вы можете обновить сервер с [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) объекта, указание соединения и **записей** объекта.  
  
```vb
Sub RDSTutorial6B()  
Dim DS As New RDS.DataSpace  
Dim RS As ADODB.Recordset  
Dim DC As New RDS.DataControl  
Dim DF As Object  
Dim blnStatus As Boolean  
Set DF = DS.("RDSServer.DataFactory", "https://yourServer")  
Set RS = DF. ("DSN=Pubs", "SELECT * FROM Authors")  
DC. = RS    ' Visual controls can now bind to DC.  
    ' Edit the Recordset.  
blnStatus = DF."DSN=Pubs", RS  
End Sub  
```  
  
 **Это происходит в конце этого руководства.**  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>См. также  
 [Поставщик Microsoft OLE DB удаленного взаимодействия (поставщик услуг ADO)](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)   
 [Учебник по RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Учебник по RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
