---
title: Основные сведения о модели COM скриптов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], object model
ms.assetid: 2a0aae82-39cc-4423-b09a-72d2f61033bd
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e2bfa3fdf09dea1b088fb519b9782999bd20296b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62768440"
---
# <a name="understanding-the-script-component-object-model"></a>Основные сведения о модели объектов компонента скрипта
  Как описано в разделе [написание кода и отладка компонента скрипта] (.. /екстендинг-паккажес-скриптинг/Дата-Флов-скрипт-компонент/кодинг-Анд-дебуггинг-СЕ-скрипт-компонент.МД, проект компонента скрипта содержит три элемента проекта:  
  
1.  Элемент `ScriptMain`, который содержит класс `ScriptMain` для создания кода. Класс `ScriptMain` наследуется от класса `UserComponent`.  
  
2.  Элемент `ComponentWrapper`, который содержит класс `UserComponent`, экземпляр объекта <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>, который содержит методы и свойства для обработки данных и взаимодействия с пакетом. Элемент `ComponentWrapper` содержит также классы коллекций `Connections` и `Variables`.  
  
3.  Элемент `BufferWrapper`, который содержит классы, унаследованные от класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> для каждого входа и выхода и типизированные свойства для каждого столбца.  
  
 При создании кода для элемента `ScriptMain` используются объекты, методы и свойства, обсуждаемые в данном разделе. Компонент может использовать не все перечисленные здесь методы. Однако если они используются, то используются в указанной последовательности.  
  
 Базовый класс <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> не содержит кода, реализующего методы, которые обсуждаются в данном разделе. Поэтому вызов базового класса в вашей собственной реализации этого метода не обязателен, но безопасен.  
  
 Сведения об использовании методов и свойств этих классов в компоненте скрипта определенного типа см. в разделе [Дополнительные примеры компонента скрипта](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md). В разделах примеров также приведен полный образец кода.  
  
## <a name="acquireconnections-method"></a>Метод AcquireConnections  
 Источники и назначения обычно должны быть соединены с внешним источником данных. Переопределите метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> базового класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>, чтобы получить соединение или сведения о соединении из соответствующего диспетчера соединений.  
  
 Следующий пример возвращает соединение `System.Data.SqlClient.SqlConnection` из диспетчера соединений ADO.NET.  
  
```vb  
Dim connMgr As IDTSConnectionManager100  
Dim sqlConn As SqlConnection  
  
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
    connMgr = Me.Connections.MyADONETConnection  
    sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)  
  
End Sub  
```  
  
 Следующий пример возвращает полный путь и имя файла из диспетчера соединений с неструктурированными файлами, после чего открывает соответствующий файл с помощью объекта `System.IO.StreamReader`.  
  
```vb  
Private textReader As StreamReader  
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
    Dim connMgr As IDTSConnectionManager100 = _  
        Me.Connections.MyFlatFileSrcConnectionManager  
    Dim exportedAddressFile As String = _  
        CType(connMgr.AcquireConnection(Nothing), String)  
    textReader = New StreamReader(exportedAddressFile)  
  
End Sub  
```  
  
## <a name="preexecute-method"></a>Метод PreExecute  
 Переопределите метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PreExecute%2A> базового класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>, если необходимо однократно выполнить некоторые действия перед началом обработки строк данных. Например, в назначении может потребоваться настроить параметризованную команду, которая будет использоваться назначением для вставки строк данных в источник данных.  
  
```vb  
    Dim sqlConn As SqlConnection  
    Dim sqlCmd As SqlCommand  
    Dim sqlParam As SqlParameter  
...  
    Public Overrides Sub PreExecute()  
  
        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
            "VALUES(@addressid, @city)", sqlConn)  
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)  
        sqlCmd.Parameters.Add(sqlParam)  
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)  
        sqlCmd.Parameters.Add(sqlParam)  
  
    End Sub  
```  
  
```csharp  
SqlConnection sqlConn;   
SqlCommand sqlCmd;   
SqlParameter sqlParam;   
  
public override void PreExecute()   
{   
  
    sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " + "VALUES(@addressid, @city)", sqlConn);   
    sqlParam = new SqlParameter("@addressid", SqlDbType.Int);   
    sqlCmd.Parameters.Add(sqlParam);   
    sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30);   
    sqlCmd.Parameters.Add(sqlParam);   
  
}  
```  
  
## <a name="processing-inputs-and-outputs"></a>Обработка входов и выходов  
  
### <a name="processing-inputs"></a>Обработка входов  
 Компоненты скрипта, настроенные как преобразования или назначения, имеют один вход.  
  
#### <a name="what-the-bufferwrapper-project-item-provides"></a>Содержимое элемента проекта BufferWrapper  
 Для каждого настроенного входа элемент проекта `BufferWrapper` содержит класс, порожденный от класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> и совпадающий по имени с входом. Каждый класс входного буфера содержит перечисленные далее свойства, функции и методы.  
  
-   Именованные и типизированные свойства метода доступа для каждого выбранного входного столбца. Эти свойства доступны только для чтения или для чтения и записи в зависимости от **типа применения**, указанного для столбца на странице **Входные столбцы** диалогового окна **Редактор преобразования "скрипт"** .  
  
-   Свойство **\<столбец>_IsNull** для каждого выбранного входного столбца. Это свойство также доступно только для чтения или для чтения и записи в зависимости от **типа применения**, указанного для этого столбца.  
  
-   Метод **DirectRowTo\<выходной_буфер>** для каждого настроенного выхода. Эти методы используются при фильтрации строк в один или несколько выходов одной и той же группы `ExclusionGroup`.  
  
-   Функция `NextRow` для получения следующей входной строки и функция `EndOfRowset` для определения того, был ли обработан последний буфер данных. Обычно эти функции не нужны, если используются методы обработки ввода, реализованные в базовом классе `UserComponent`. В следующем разделе приводится более подробная информация о базовом классе `UserComponent`.  
  
#### <a name="what-the-componentwrapper-project-item-provides"></a>Содержимое элемента проекта ComponentWrapper  
 Элемент проекта ComponentWrapper содержит класс с именем `UserComponent`, производный от класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>. Класс `ScriptMain`, в котором создается пользовательский код, в свою очередь, является производным от класса `UserComponent`. Класс `UserComponent` содержит следующие методы.  
  
-   Переопределенная реализация метода `ProcessInput`. Этот метод вызывается подсистемой обработки потока данных во время выполнения сразу за методом `PreExecute`. Он может быть вызван более одного раза. `ProcessInput`передает обработку методу ** \<>_ProcessInput INPUTBUFFER** . После этого метод `ProcessInput` проверяет, достигнут ли конец входного буфера, и в этом случае вызывает переопределяемый метод `FinishOutputs`, а также частный метод `MarkOutputsAsFinished`. Затем метод `MarkOutputsAsFinished` вызывает метод `SetEndOfRowset` для последнего выходного буфера.  
  
-   Перегружаемая реализация метода **\<входной_буфер>_ProcessInput**. Эта реализация по умолчанию просто перебирает входящие строки и вызывает метод **\<входной_буфер>_ProcessInputRow**.  
  
-   Перегружаемая реализация метода **\<входной_буфер>_ProcessInputRow**. Реализация по умолчанию пуста. Этот метод обычно переопределяется, чтобы написать пользовательский код обработки данных.  
  
#### <a name="what-your-custom-code-should-do"></a>Задачи, выполняемые в пользовательском коде  
 Для обработки входа в классе `ScriptMain` можно использовать перечисленные далее методы.  
  
-   Переопределите метод **\<входной_буфер>_ProcessInputRow** для обработки данных в каждой входной строке по мере ее прохождения.  
  
-   Переопределите метод **\<входной_буфер>_ProcessInput**, только если необходимо выполнять дополнительные действия по мере перебора входных строк. (Например, необходимо протестировать `EndOfRowset` , чтобы выполнить какое-либо другое действие после обработки всех строк.) Вызовите ** \<INPUTBUFFER>_ProcessInputRow** для выполнения обработки строк.  
  
-   Переопределите метод `FinishOutputs`, если нужно выполнять действия с выходами перед их закрытием.  
  
 Метод `ProcessInput` обеспечивает, что эти методы будут вызываться в нужное время.  
  
### <a name="processing-outputs"></a>Обработка выходов  
 Компоненты скрипта, настроенные в качестве источников или преобразований, имеют один или несколько выходов.  
  
#### <a name="what-the-bufferwrapper-project-item-provides"></a>Содержимое элемента проекта BufferWrapper  
 Для каждого настроенного выхода элемент проекта BufferWrapper содержит класс, порожденный от класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> и совпадающий по имени с выходом. Каждый класс входного буфера содержит перечисленные далее свойства и методы.  
  
-   Именованные и типизированные свойства метода доступа только для записи для каждого выходного столбца.  
  
-   ** \<Столбец** , доступный только для записи,>_IsNull свойство для каждого выбранного выходного столбца, который можно использовать для задания значения `null`столбца.  
  
-   Метод `AddRow` для добавления новой пустой строки в выходной буфер.  
  
-   Метод `SetEndOfRowset` для оповещения подсистемы обработки потока данных о том, что буферов данных больше не ожидается. Имеется также функция `EndOfRowset` для определения того, является ли текущий буфер данных последним. Обычно эти функции не нужны, если используются методы обработки ввода, реализованные в базовом классе `UserComponent`.  
  
#### <a name="what-the-componentwrapper-project-item-provides"></a>Содержимое элемента проекта ComponentWrapper  
 Элемент проекта ComponentWrapper содержит класс с именем `UserComponent`, производный от класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>. Класс `ScriptMain`, в котором создается пользовательский код, в свою очередь, является производным от класса `UserComponent`. Класс `UserComponent` содержит следующие методы.  
  
-   Переопределенная реализация метода `PrimeOutput`. Подсистема обработки потока данных вызывает этот метод перед методом `ProcessInput` во время выполнения. Он вызывается только один раз. 
  `PrimeOutput` передает обработку методу `CreateNewOutputRows`. Затем, если компонент является источником (то есть не имеет входов), `PrimeOutput` вызывает переопределяемый метод `FinishOutputs` и частный метод `MarkOutputsAsFinished`. Метод `MarkOutputsAsFinished` вызывает метод `SetEndOfRowset` для последнего выходного буфера.  
  
-   Реализация метода `CreateNewOutputRows`, доступная для переопределения. Реализация по умолчанию пуста. Этот метод обычно переопределяется, чтобы написать пользовательский код обработки данных.  
  
#### <a name="what-your-custom-code-should-do"></a>Задачи, выполняемые в пользовательском коде  
 Для обработки выходов в классе `ScriptMain` можно использовать следующие методы.  
  
-   Переопределите метод `CreateNewOutputRows`, только если возможно добавление и заполнение выходных строк перед обработкой входных строк. Например, метод `CreateNewOutputRows` можно использовать на источнике, но при преобразовании с использованием асинхронных выходов необходимо вызывать метод `AddRow` во время или после обработки входных данных.  
  
-   Переопределите метод `FinishOutputs`, если нужно выполнять действия с выходами перед их закрытием.  
  
 Метод `PrimeOutput` обеспечивает, что эти методы будут вызываться в нужное время.  
  
## <a name="postexecute-method"></a>Метод PostExecute  
 Переопределите метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PostExecute%2A> базового класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>, если необходимо однократно выполнить некоторые действия после обработки всех строк данных. Например, можно закрыть на источнике объект `System.Data.SqlClient.SqlDataReader`, который используется для загрузки данных в поток данных.  
  
> [!IMPORTANT]  
>  Коллекция `ReadWriteVariables` доступна только в методе `PostExecute`. Поэтому нельзя непосредственно увеличивать значение переменной пакета после обработки каждой строки данных. Вместо этого увеличьте значение локальной переменной и задайте это же значение переменной пакета в методе `PostExecute` после того, как все данные обработаны.  
  
## <a name="releaseconnections-method"></a>Метод ReleaseConnections  
 Источники и назначения обычно должны быть соединены с внешним источником данных. Переопределите метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReleaseConnections%2A> базового класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>, чтобы закрыть и освободить соединение, ранее открытое в методе <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A>.  
  
```vb  
    Dim connMgr As IDTSConnectionManager100  
...  
    Public Overrides Sub ReleaseConnections()  
  
        connMgr.ReleaseConnection(sqlConn)  
  
    End Sub  
```  
  
```csharp  
IDTSConnectionManager100 connMgr;  
  
public override void ReleaseConnections()  
{  
  
    connMgr.ReleaseConnection(sqlConn);  
  
}  
```  
  
![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Настройка компонента скрипта в редакторе компонента скрипта](configuring-the-script-component-in-the-script-component-editor.md)   
 [Написание кода и отладка компонента скрипта] (.. /екстендинг-паккажес-скриптинг/дата-флов-скрипт-компонент/кодинг-анд-дебуггинг-се-скрипт-компонент.мд  
  
  
