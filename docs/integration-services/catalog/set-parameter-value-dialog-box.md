---
title: Диалоговое окно "Задание значения параметра" | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ce9c2201-4e9a-4495-948f-b68deeaa7955
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9a3e056e60eeab6dfdb79a448b4fc95bf1c01f50
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71298939"
---
# <a name="set-parameter-value-dialog-box"></a>Диалоговое окно «Задание значения параметра»

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Диалоговое окно **Задание значения параметра** используется для настройки параметров и свойств диспетчеров соединений для пакетов и проектов.  
  
 **Выбор действия**  
  
-   [Открыть диалоговое окно «Задание значения параметра»](#open_dialog)  
  
-   [Настройка параметров](#option)  
  
##  <a name="open_dialog"></a> Открыть диалоговое окно «Задание значения параметра»  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]установите соединение с сервером служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Устанавливается соединение с экземпляром [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], в котором размещена база данных SSISDB.  
  
2.  В обозревателе объектов разверните дерево для отображения узла **Каталоги служб Integration Services** .  
  
3.  Разверните узел **SSISDB** .  
  
4.  Щелкните правой кнопкой мыши пакет, выберите **Настроить**, а затем нажмите кнопку с многоточием на вкладке **Параметры** или **Диспетчеры соединений** .  
  
##  <a name="option"></a> Настройка параметров  
 **Параметр**  
 Выводит список имен параметра.  
  
 **Тип**  
 Перечисляет тип данных значения параметра.  
  
 **Описание**  
 Показывает дополнительное описание параметра.  
  
 **Изменить значение**  
 Выберите этот параметр, чтобы изменить значение параметра.  
  
 **Использовать значение по умолчанию из пакета**  
 Выберите этот параметр, чтобы использовать значение параметра по умолчанию, сохраненное в пакете.  
  
 **Использовать переменную среды**  
 Выберите этот параметр для использования значения переменной, сохраненного в среде, на которую ссылается проект или пакет. Чтобы добавить ссылку среды к проекту или пакету, используйте диалоговое окно **Настройка** . Дополнительные сведения см. в статье [Configure Dialog Box](../../integration-services/catalog/configure-dialog-box.md).  
  
  
