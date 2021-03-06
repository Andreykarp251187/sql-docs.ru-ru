---
title: Физические компоненты устройства
description: Имена и описания физических компонентов PDW и структуры устройств.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 5cbed66f53189668518e04848002ae69adb8c614
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "74400920"
---
# <a name="appliance-physical-components---analytics-platform-system"></a>Физические компоненты устройства — системная платформа аналитики
Имена и описания физических компонентов PDW и структуры устройств. 
  
<!-- MISSING LINKS See also [HDInsight Physical Components &#40;Analytics Platform System&#41;](hdinsight-physical-components.md).  -->  
  
## <a name="component-diagrams"></a><a name="diagrams"></a>Схемы компонентов  
Здесь отображаются имена физических компонентов и их расположение в первой стойке 6-расчетного устройства узла.  
  
![Имена компонентов региона PDW — HP](./media/pdw-and-appliance-fabric-physical-components/APS_HW_ComponentNames-HP.png "APS_HW_ComponentNames HP")  
  
Фактическим именем для компонентов PDW является имя региона PDW, затем дефис, за которым следует имя компонента. Например, если имя региона PDW — PDW123, фактические имена: **PDW123-CTL01**, **PDW123-CMP01**и т. д.  
  
Точно так же фактическим именем для компонентов структуры устройства является имя домена устройства, тире, за которым следует имя компонента. Например, если домен устройства — FSW123, виртуальные машины фабрики устройств — это **FSW123-WDS**, **FSW123-AD01**, **FSW123-VMM**и т. д.  
  
Ниже представлено объединенное представление области PDW с шестью вычисленными узлами.  
  
![Имена компонентов PDW](./media/pdw-and-appliance-fabric-physical-components/APS_HW_Names.png "APS_HW_Names")  
  
## <a name="pdw-components"></a><a name="pdw"></a>Компоненты PDW  
Виртуальные машины PDW входят в состав области PDW.  
  
*PDW_region*CTL01  
Виртуальная машина, на которой выполняется узел управления. Это выполняется на HST01 и может переключиться на HST02.  
  
> [!WARNING]  
> SQL Server PDW не поддерживает создание моментального снимка виртуальной машины CTL01 с помощью диспетчера Hyper-V. Моментальные снимки зависят от локального хранилища, что приведет к ошибкам, если виртуальная машина попытается выполнить отработку отказа в резервную копию. Создание моментального снимка также может вызвать проблемы с надежностью других виртуальных машин, отработка отказа на пассивный сервер.  
  
*PDW_region*-CMP01 с помощью *PDW_Region*-CMP06  
Виртуальная машина, на которой выполняется узел вычислений. На этой 6-кластерной диаграмме узлов узлы, HSA01 через HSA06, запускают виртуальные машины с виртуальными машинами CMP01 через CMP06 соответственно.  
  
## <a name="appliance-fabric-components"></a><a name="fabric"></a>Компоненты структуры устройств  
Эти компоненты являются частью структуры устройства.  
  
### <a name="virtual-machines"></a>Виртуальные машины  
*appliance_domain*-WDS  
На этой виртуальной машине размещаются службы развертывания Windows (WDS), в которых в системе аналитики используется платформа для развертывания операционных систем Windows по сети устройства. На нем также размещается служба DHCP, которая позволяет узлам устройства присоединяться к сети устройства без предварительно настроенного IP-адреса.  
  
*Appliance_domain*виртуальная машина WDS выполняется на HST01 и может выполнять отработку отказа на HST02. Виртуальная машина WDS и виртуальная машина VMM развертывают Windows на физических узлах во время установки устройства. Во время жизненного цикла устройства WDS и VMM выполняют такие операции, как замена узла.  
  
*appliance_domain*— VMM  
Virtual Machine Manager (VMM) выполняется на виртуальной машине и может переключиться на HST02. VMM размещает System Center для развертывания операционной системы на физических узлах. VMM также предоставляет Windows Server Update Services (WSUS) для применения или удаления обновлений Windows на всех узлах и виртуальных машинах.  
  
*appliance_domain*-AD01, *appliance_domain*-AD02  
Службы домен Active Directory, которые содержат службу доменных имен (DNS), выполняются на виртуальной машине как в HST01, так и в HST02. Для обеспечения высокой доступности устройства AD01 и AD02 являются реплицируемыми контроллерами домена и не выполняют отработку отказа. В случае сбоя одна из них уже будет доступна с правильными данными.  
  
*appliance_domain*ISCSI01  
Одна виртуальная машина ISCSI выполняется на каждом из узлов с подключенным хранилищем (HSA01-HSA06). Эта виртуальная машина не выполняет отработку отказа.  
  
### <a name="hosts"></a>Узлы  
*appliance_domain*-HST01 с помощью *appliance_domain*-HST06  
Узлы для узла элемента управления PDW и виртуальных машин структуры устройств. HST03 — необязательный пассивный узел.  
  
*appliance_domain*-HSA01 с помощью *appliance_domain*-HSA08  
Узлы с подключенным хранилищем (ХСА). На каждом узле выполняются одна виртуальная машина с одним и тем же виртуальным узлом ISCSI.  
  
### <a name="cluster-for-pdw"></a>Кластер для PDW  
*appliance_domain*WFOHST01  
Кластер PDW называется WFOHST01. Он управляет всеми физическими узлами и виртуальными машинами, принадлежащими PDW.  
  
### <a name="direct-attached-storage"></a>Непосредственно подключенное хранилище  
*appliance_domain*-DAS01 с помощью *appliance_domain*-DAS03  
Это непосредственно подключенное хранилище, подключенное к вычисленным узлам. Компания HP имеет один DAS для каждого из двух Вычисленийных узлов. В Dell и тактах имеется один DAS для каждого из трех вычислений.  
  
## <a name="see-also"></a>См. также  
<!-- MISSING LINKS [Hardware Configurations &#40;Analytics Platform System&#41;](../architecture/hardware-configurations.md)  -->  
[Конфигурация устройства &#40;&#41;платформа системы аналитики ](appliance-configuration.md)  
[Задачи управления устройством &#40;&#41;платформы аналитики ](appliance-management-tasks.md)  
  
