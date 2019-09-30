---
title: Разработка пользовательского интерфейса для пользовательского перечислителя по каждому элементу | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services], custom foreach enumerators
- custom foreach enumerators [Integration Services], developing custom user interface
ms.assetid: 8aa4aa80-c9ba-42b3-ba87-ae5ea5d3cac3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 07bd14be05b07fab0ba383da928e2fd384bbdfe5
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71297170"
---
# <a name="developing-a-user-interface-for-a-custom-foreach-enumerator"></a>Разработка пользовательского интерфейса для пользовательского перечислителя по каждому элементу

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  После переопределения реализации свойств и методов базового класса для выполнения пользовательских функций может понадобиться создать настраиваемый пользовательский интерфейс для пользовательского перечислителя по каждому элементу. Если нестандартный пользовательский интерфейс не создается, пользователи могут настраивать новые пользовательские перечислители по каждому элементу только с помощью окна «Свойства».  
  
 В проекте или сборке собственного пользовательского интерфейса создается класс, реализующий интерфейс <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI>. Этот класс является производным от класса System.Windows.Forms.UserControl, который обычно используется для создания составного элемента управления для размещения других элементов управления Windows Forms. Создаваемый элемент управления отображается в области **Конфигурация перечислителя** на вкладке **Коллекция** окна **Редактор циклов по каждому элементу**.  
  
> [!IMPORTANT]  
>  После подписи и сборки собственного пользовательского интерфейса и его установки в глобальный кэш сборок, как описано в разделе [Сборка, развертывание и отладка пользовательских объектов](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md), нужно указать полное имя этого класса в свойстве <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> атрибута <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>.  
  
## <a name="coding-the-user-interface-control-class"></a>Написание кода для класса элемента управления пользовательского интерфейса  
  
### <a name="initializing-the-user-interface"></a>Инициализация пользовательского интерфейса  
 Метод <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.Initialize%2A> переопределяется для кэширования ссылок на базовый объект, а также коллекции диспетчеров соединения и переменные, определенные в пакете.  
  
### <a name="setting-properties-on-the-user-interface-control"></a>Установка свойств элемента управления пользовательского интерфейса  
 Класс UserControl, от которого наследуется класс пользовательского интерфейса, предназначен для использования в качестве составного элемента управления для размещения других элементов управления Windows Forms. Поскольку этот класс размещает другие элементы управления, собственный пользовательский интерфейс можно создавать, перетаскивая и упорядочивая элементы управления, устанавливая их свойства и реагируя во время выполнения на формируемые ими события, как в любом другом приложении Windows Forms.  
  
### <a name="saving-settings"></a>Сохранение настроек  
 Метод <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.SaveSettings%2A> переопределяется для копирования выбранных пользователем значений при закрытии редактора — от элементов управления до свойств перечислителя.  
  
## <a name="see-also"></a>См. также:  
 [Создание пользовательского перечислителя по каждому элементу](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/creating-a-custom-foreach-enumerator.md)   
 [Написание кода пользовательского перечислителя по каждому элементу](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/coding-a-custom-foreach-enumerator.md)  
  
  
