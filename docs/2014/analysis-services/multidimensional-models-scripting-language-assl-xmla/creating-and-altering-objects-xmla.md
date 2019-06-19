---
title: Создание и изменение объектов (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [XML for Analysis]
- subordinate objects [XML for Analysis]
- XML for Analysis, objects
- modifying objects
- removing objects
- deleting objects
- XMLA, objects
ms.assetid: a2080867-e130-440c-92eb-f768869f34a8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3dcc6eedc97b3d476d79420b4e067883e17f03d2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62702301"
---
# <a name="creating-and-altering-objects-xmla"></a>Создание и изменение объектов (XMLA)
  Основные объекты можно создавать, изменять и удалять независимо. Основные объекты включают следующие объекты:  
  
-   Серверы  
  
-   Базы данных  
  
-   Измерения  
  
-   Кубы  
  
-   Группы мер  
  
-   Секции  
  
-   перспективами  
  
-   Модели интеллектуального анализа данных  
  
-   Роли  
  
-   Команды, связанные с сервером или базой данных  
  
-   Источники данных  
  
 Использовании [создать](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) команду для создания основного объекта на экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]и [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) команду, чтобы изменить существующий основной объект в экземпляре. Обе команды запускаются с помощью [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) метод.  
  
## <a name="creating-objects"></a>Создание объектов  
 Объекты можно создавать при помощи метода `Create`; для этого сначала необходимо определить родительский объект, содержащий объект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], который должен быть создан. Определить родительский объект, указав ссылку на объект в [ParentObject](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) свойство `Create` команды. Каждая ссылка объекта содержит идентификаторы объекта, необходимые, чтобы идентифицировать родительский объект для команды `Create` уникальным образом. Дополнительные сведения о ссылках на объекты, см. в разделе [определение и идентификация объектов &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).  
  
 Например, следует указать ссылку объекта на куб, чтобы создать новую группу мер для этого куба. Ссылка на объект для куба в свойстве `ParentObject` содержит идентификатор базы данных и идентификатор куба, поскольку тот же идентификатор куба может использоваться в другой базе данных.  
  
 [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) элемент содержит элементы языка сценариев служб Analysis Services (ASSL), которые определяют создаваемый основной объект должен быть создан. Дополнительные сведения о ASSL см. в разделе [разработка с использованием язык сценариев служб Analysis Services &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 Если атрибуту `AllowOverwrite` команды `Create` задать значение TRUE, можно переписать существующий основной объект, имеющий указанный идентификатор. В противном случае, если основной объект с указанным идентификатором уже существует в родительском объекте, возникает ошибка.  
  
 Дополнительные сведения о `Create` команды, см. в разделе [Создание элемента &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla).  
  
### <a name="creating-session-objects"></a>Создание объектов сеанса  
 Объекты сеанса — это временные объекты, доступные только для явных или неявных сеансов, которые используются клиентским приложением и удаляются по завершении сеанса. Объект сеанса можно создать, задав `Scope` атрибут `Create` команды *сеанса*.  
  
> [!NOTE]  
>  При использовании *сеанса* параметр `ObjectDefinition` элемент может содержать только [измерения](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [куба](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl), или [MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL элементы.  
  
## <a name="altering-objects"></a>Изменение объектов  
 При изменении объектов с помощью `Alter` метод, сначала нужно определить объект для изменения, указав ссылку на объект в [объект](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) свойство `Alter` команды. Каждая ссылка объекта содержит идентификаторы объекта, необходимые, чтобы уникальным образом идентифицировать объект для команды `Alter`. Дополнительные сведения о ссылках на объекты, см. в разделе [определение и идентификация объектов &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).  
  
 Например, чтобы изменить структуру куба, необходимо указать ссылку объекта на куб. Ссылка на объект для куба в свойстве `Object` содержит идентификатор базы данных и идентификатор куба, поскольку тот же идентификатор куба может использоваться в другой базе данных.  
  
 Элемент `ObjectDefinition` содержит элементы языка ASSL, определяющие основной объект, которые должен быть изменен. Дополнительные сведения о ASSL см. в разделе [разработка с использованием язык сценариев служб Analysis Services &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 Если атрибуту `AllowCreate` команды `Alter` задать значение TRUE, можно создать указанный основной объект, если он не существует. В противном случае, если указанный основной объект еще не существует, возникает ошибка.  
  
### <a name="using-the-objectexpansion-attribute"></a>Использование атрибута ObjectExpansion  
 Если вы изменяете только свойства основного объекта и без переопределения второстепенных объектов, которые содержатся в основном объекте, можно задать `ObjectExpansion` атрибут `Alter` команды *ObjectProperties*. В этом случае свойство `ObjectDefinition` должно содержать только элементы для свойств основного объекта, а команда `Alter` оставляет второстепенные объекты, ассоциированные с основным объектом, без изменений.  
  
 Чтобы переопределить второстепенные объекты для основного объекта, необходимо задать `ObjectExpansion` атрибут *ExpandFull* и определение объекта должен включать все второстепенные объекты, которые содержатся в основном объекте. Если в свойство `ObjectDefinition` команды `Alter` явно не включен второстепенный объект, содержащийся в основном объекте, то не указанный в нем второстепенный объект удаляется.  
  
### <a name="altering-session-objects"></a>Изменение объектов сеанса  
 Чтобы изменить объекты сеанса, созданные `Create` команды, задайте `Scope` атрибут `Alter` команды *сеанса*.  
  
> [!NOTE]  
>  При использовании *сеанса* параметр `ObjectDefinition` элемент может содержать только [измерения](https://docs.microsoft.com/bi-reference/assl/objects/dimension-element-assl), [куба](https://docs.microsoft.com/bi-reference/assl/objects/cube-element-assl), или [MiningModel](https://docs.microsoft.com/bi-reference/assl/objects/miningmodel-element-assl) ASSL элементы.  
  
## <a name="creating-or-altering-subordinate-objects"></a>Создание или изменение подчиненных объектов  
 Хотя команда `Create` или `Alter` создает или изменяет только один самый верхний основной объект, создаваемый или изменяемый основной объект может содержать во включающем свойстве `ObjectDefinition` определения для других основных или второстепенных объектов, которые ему подчинены. Например, при определении куба родительская база данных указывается в свойстве `ParentObject`, тогда как в рамках определения куба в свойстве `ObjectDefinition` можно определить группы мер для куба, а в рамках групп мер — определить секции для каждой группы мер. Второстепенный объект можно определить только в содержащем его основном объекте. Дополнительные сведения об основных и второстепенных объектах см. в разделе [объектов базы данных &#40;службы Analysis Services — многомерные данные&#41;](../multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="description"></a>Описание  
 В следующем примере создается реляционный источник данных, ссылающийся на [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] пример [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных.  
  
### <a name="code"></a>Код  
  
```  
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    </ParentObject>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=localhost;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ImpersonationInfo>  
                <ImpersonationMode>ImpersonateServiceAccount</ImpersonationMode>  
            </ImpersonationInfo>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT0S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Create>  
```  
  
### <a name="description"></a>Описание  
 В следующем примере реляционный источник данных, созданный в предыдущем примере, изменяется путем задания времени ожидания запроса для источника данных, равного 30 секундам.  
  
### <a name="code"></a>Код  
  
```  
<Alter ObjectExpansion="ObjectProperties" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DataSourceID>AdventureWorksDW2012</DataSourceID>  
    </Object>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=fr-dwk-02;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT30S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Alter>  
```  
  
### <a name="comments"></a>Комментарии  
 `ObjectExpansion` Атрибут `Alter` команды было присвоено *ObjectProperties*. Этот параметр позволяет [ImpersonationInfo](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl) элемент, второстепенный объект, который необходимо исключить из источника данных, определенного в `ObjectDefinition`. Поэтому в качестве данных об олицетворении для этого источника данных остается заданной учетная запись службы, как указано в первом примере.  
  
## <a name="see-also"></a>См. также  
 [Метод Execute &#40;XML для Аналитики&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)   
 [Разработка на языке ASSL (язык ASSL)](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Разработка с использованием XMLA в службах Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
