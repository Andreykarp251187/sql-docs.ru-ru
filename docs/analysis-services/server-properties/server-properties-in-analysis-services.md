---
title: Свойства сервера в службах Analysis Services | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ce74bb210e3d5d3cd01120b0bd406672db6dd5ed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207962"
---
# <a name="server-properties-in-analysis-services"></a>Свойства сервера в службах Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Администратор служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может изменить по умолчанию свойства конфигурации сервера для экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . У всех экземпляров имеются собственные свойства конфигурации, которые можно задать независимо от других экземпляров на том же сервере.  
  
 Для настройки сервера, используйте SQL Server Management Studio или измените файл msmdsrv.ini соответствующего экземпляра SQL Server Analysis Services.  
 
На страницах свойств в среде SQL Server Management Studio отображается подмножество свойств, которые, скорее всего, будут изменены. Полный список свойств содержится в файле msmdsrv.ini.   
  
> [!NOTE]  
>  При установке SQL Server Analysis Services по умолчанию можно найти в \Program Files\Microsoft SQL Server\MSAS13 msmdsrv.ini. Папка MSSQLSERVER\OLAP\Config.
> 
> В число других свойств, влияющих на конфигурацию сервера, входят свойства конфигурации развертывания в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения об этих свойствах см. в разделе [Указание настроек конфигурации для развертывания решения](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md).
 
## <a name="configure-properties-in-management-studio"></a>Настройка свойств в среде Management Studio 
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]подключитесь к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2. В обозревателе объектов щелкните правой кнопкой мыши экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и выберите пункт **Свойства**. Отображается страница «Общие», содержащая основные свойства.  

3.  Для просмотра дополнительных свойств установите флажок **Показать дополнительные (все) свойства** в нижней части страницы.  
  
     Изменение свойств сервера поддерживается только для серверов в табличном и многомерном режимах. Если установлен [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], всегда используйте значения по умолчанию, если только сотрудник службы технической поддержки Майкрософт не даст другие указания.  
  
  
## <a name="configure-properties-in-msmdsrvini"></a>Настройка свойств в файле msmdsrv.ini
  
Определенные свойства можно задать только в файле msmdrsrv.ini. Эти свойства неприменимы к службам Azure Analysis Services.
Если свойство, которое необходимо задать, не отображается даже после включения дополнительных свойств, может потребоваться внести изменения непосредственно в файл msmdsrv.ini. 
  
1.  Проверьте свойство **DataDir** на странице свойств "Общие" в среде Management Studio, чтобы проверить, где находятся программные файлы служб Analysis Services, в том числе файл msmdsrv.ini.

     Если на сервере установлено несколько экземпляров, это позволит убедиться, что изменениям подвергается верный файл.  
  
2.  Найдите папку **config** в каталоге, где находится папка Program Files.

3. Создайте резервную копию файла на случай необходимости использования исходного файла.  
  
4.  Используйте текстовый редактор для просмотра и изменения файла msmdsrv.ini.  
  
5.  Сохраните файл и перезапустите службу.  
  
##  <a name="server-property-reference"></a>Справочник по свойствам сервера  
  
 Следующие подразделы содержат описание различных свойств конфигурации служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] :  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Общие свойства](../../analysis-services/server-properties/general-properties.md)|К общим свойствам относятся основные и расширенные свойства, а так же свойства, которые определяют каталог данных, каталог резервного копирования и другие характеристики сервера.|  
|[Свойства интеллектуального анализа данных](../../analysis-services/server-properties/data-mining-properties.md)|Свойства интеллектуального анализа данных позволяют включать или отключать различные алгоритмы интеллектуального анализа. По умолчанию все алгоритмы включены.| 
|[Свойства DAX](../../analysis-services/server-properties/dax-properties.md)|В этом разделе описаны свойства, связанные с запросами DAX.|
|объекты DSO|Объекты DSO теперь не поддерживаются. Свойства DSO не обрабатываются.|  
|[Свойства функций](../../analysis-services/server-properties/feature-properties.md)|Свойства функций служат для настройки возможностей продуктов, большинство из которых являются расширенными, включая свойства, управляющие связями между экземплярами сервера.|  
|[Свойства хранилища файлов](../../analysis-services/server-properties/filestore-properties.md)|Свойства файлового хранилища предназначены только для расширенного использования. К этим свойствам относятся расширенные параметры управления памятью.|  
|[Свойства диспетчера блокировок](../../analysis-services/server-properties/lock-manager-properties.md)|Свойства диспетчера блокировок управляют блокировками и временем ожидания сервера. Большинство из них предназначены только для расширенного использования.|  
|[Свойства журнала](../../analysis-services/server-properties/log-properties.md)|Свойства журналов управляют регистрацией событий на сервере, если она используется. Они позволяют настроить регистрацию ошибок и исключений, «черный ящик», регистрацию запросов и трассировку.|  
|[Свойства памяти](../../analysis-services/server-properties/memory-properties.md)|Свойства памяти управляют использованием памяти сервером. Они предназначены, главным образом, для расширенного использования.|  
|[Свойства сети](../../analysis-services/server-properties/network-properties.md)|Сетевые свойства контролируют работу сервера в сети, к ним относятся свойства, управляющие сжатием и двоичными файлами XML. Большинство из них предназначены только для расширенного использования.|  
|[Свойства OLAP](../../analysis-services/server-properties/olap-properties.md)|Свойства OLAP управляют обработкой кубов и измерений, отложенной обработкой, кэшированием данных и поведением запросов. К ним относятся и основные, и расширенные свойства.|  
|[Свойства безопасности](../../analysis-services/server-properties/security-properties.md)|Раздел безопасности содержит основные и расширенные свойства, определяющие разрешения доступа. К ним относятся параметры, управляющие действиями администраторов и пользователей.|  
|[Свойства пула потоков](../../analysis-services/server-properties/thread-pool-properties.md)|Свойства пула потоков управляют количеством потоков, которые создает сервер. Они предназначены, главным образом, для расширенного использования.|  
  
## <a name="see-also"></a>См. также  
 [Управление экземплярами служб Analysis Services](../../analysis-services/instances/analysis-services-instance-management.md)   
 [Указание настроек конфигурации для развертывания решения](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
  
