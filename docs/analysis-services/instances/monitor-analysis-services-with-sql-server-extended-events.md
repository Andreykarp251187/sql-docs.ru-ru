---
title: Мониторинг служб Analysis Services с помощью расширенных событий SQL Server | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dc51c444483dc9a89cf0b9edbd557c3dce11a054
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62709261"
---
# <a name="monitor-analysis-services-with-sql-server-extended-events"></a>Мониторинг служб Analysis Services с помощью расширенных событий SQL Server
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas-all-aas.md)]
  Расширенные события (*xEvents*) — это упрощенная система трассировки и мониторинга производительности, которая использует очень небольшое количество системных ресурсов. Это делает систему идеальным средством для диагностики проблем как на производственных, так и на тестовых серверах. Система также характеризуется высокой масштабируемостью и возможностями настройки. В SQL Server 2016 ее использование упрощено благодаря поддержке новых встроенных средств. В SQL Server Management Studio для подключений к экземплярам служб Analysis Services можно настроить, запустить и отслеживать динамическую трассировку так же, как и при использовании приложения SQL Server Profiler. Добавление улучшенных средств не только делает xEvents более рациональной заменой SQL Server Profiler, но и позволяет упорядочить диагностику проблем в ядре СУБД и рабочих нагрузках служб Analysis Services.  
  
 Кроме использования [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]вы также можете настроить сеансы расширенных событий  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] традиционным способом — с помощью скриптов XMLA, поддерживаемых в предыдущих выпусках.  
  
 Все события служб Analysis Services можно регистрировать и направлять конкретным получателям, как определено в [расширенных событиях](../../relational-databases/extended-events/extended-events.md).  
  
> [!NOTE]  
>  Просмотрите это [краткое вводное видео](https://www.youtube.com/watch?v=ja2mOHWRVC0&index=1&list=PLv2BtOtLblH1YvzQ5YnjfQFr_oKEvMk19) или прочитайте [публикацию в блоге службы поддержки](http://blogs.msdn.com/b/analysisservices/archive/2015/09/22/using-extended-events-with-sql-server-analysis-services-2016-cpt-2-3.aspx) , чтобы узнать больше о расширенных событиях xEvents для служб Analysis Services в SQL Server 2016.  
  
  
##  <a name="bkmk_ssas_extended_events_ssms"></a> Настройка служб Analysis Services с помощью Management Studio  
 Как для табличных, так и для многомерных экземпляров Management Studio предусматривает новую папку "Управление", содержащую инициированные пользователем сеансы xEvent. Одновременно можно запускать несколько сеансов. Однако в текущей реализации пользовательский интерфейс расширенных событий [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не поддерживает обновление или воспроизведение существующего сеанса.  
  
 ![ssas_extended_events_ssms_start](../../analysis-services/instances/media/ssas-extended-events-ssms-start.png "ssas_extended_events_ssms_start")  
  
 **Выбор событий**  
  
 Если вы уже знаете, какие события нужно зарегистрировать, проще всего добавить их в трассировку, выполнив поиск. В противном случае для мониторинга операций обычно используются следующие события:  
  
-   **CommandBegin** и **CommandEnd**.  
  
-   **QueryBegin**, **QueryEnd**и **QuerySubcubeVerbose** (показывает весь запрос MDX или DAX, отправляемый на сервер), а также **ResourceUsage** для статистики по ресурсам, потребленным запросом, и количеству возвращенных строк.  
  
-   **ProgressReportBegin** и **ProgressReportEnd** (для операций обработки).  
  
-   **AuditLogin** и **AuditLogout** (фиксирует идентификатор пользователя, под которым клиентское приложение подключается к службам Analysis Services).  
  
 **Выбор хранилища данных**  
  
 Сеанс может передаваться в виде потока в окно Management Studio или сохраняться в файл для последующего анализа с помощью Power Query или Excel.  
  
-   **event_file** сохраняет данные сеанса в XEL-файле.  
  
-   **event_stream** включает параметр **Просмотр данных, передаваемых в режиме реального времени** в среде Management Studio.  
  
-   **ring_buffer** сохраняет данные сеанса в памяти, пока работает сервер. При перезапуске сервера данные сеанса теряются.  
  
 **Добавление полей событий**  
  
 Не забудьте при настройке сеанса включить поля событий, чтобы можно было легко просматривать сведения, представляющие интерес.  
  
 Параметр**Настроить** находится в удаленной области диалогового окна.  
  
 ![ssas-xevents-configure](../../analysis-services/instances/media/ssas-xevents-configure.PNG "ssas-xevents-configure")  
  
 В конфигурации на вкладке "Поля событий" выберите поле **TextData** , чтобы оно отображалось рядом с событием и показывало возвращаемые значения, включая запросы, которые выполняются на сервере.  
  
 После настройки сеанса для нужных событий и хранения данных можно, нажав кнопку сценария, отправить конфигурацию в одно из поддерживаемых целевых расположений: файл, новый запрос в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]и буфер обмена.  
  
 **Обновление сеансов**  
  
 После создания сеанса не забудьте обновить папку "Сеансы" в Management Studio для просмотра сеанса, который вы только что создали. Если вы настроили event_stream, можно щелкнуть правой кнопкой мыши имя сеанса и выбрать **Просмотр динамических данных** для мониторинга активности сервера в режиме реального времени.  
  
##  <a name="bkmk_script_start"></a> Скрипт XMLA для запуска расширенных событий в службах Analysis Services  
 Расширенная трассировка событий включается с помощью команды скрипта создания объекта, аналогичной команде XML для аналитики, как показано ниже.  
  
```  
<Execute ...>  
   <Command>  
      <Batch ...>  
         <Create ...>  
            <ObjectDefinition>  
               <Trace>  
                  <ID>trace_id</ID>  
                  <Name>trace_name</Name>  
                  <ddl300_300:XEvent>  
                     <event_session ...>  
                        <event package="AS" name="AS_event">  
                           <action package="PACKAGE0" .../>  
                        </event>  
                        <target package="PACKAGE0" name="asynchronous_file_target">  
                           <parameter name="filename" value="data_filename.xel"/>  
                           <parameter name="metadatafile" value="metadata_filename.xem"/>  
                        </target>  
                     </event_session>  
                  </ddl300_300:XEvent>  
               </Trace>  
            </ObjectDefinition>  
         </Create>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 Следующие элементы должны быть определены пользователем с учетом потребностей трассировки:  
  
 *trace_id*  
 Определяет уникальный идентификатор для данной трассировки.  
  
 *trace_name*  
 Имя, присвоенное данной трассировке. Как правило, понятное определение трассировки. Обычно принято использовать в качестве имени значение *trace_id* .  
  
 *AS_event*  
 Событие служб Analysis Services, к которому должен быть предоставлен доступ. Имена событий см. в разделе [События трассировки служб Analysis Services](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events) .  
  
 *data_filename*  
 Имя файла данных, который содержит данные события. Это имя имеет в качестве суффикса отметку времени, что позволяет предотвратить перезапись данных, если одно и то же сообщение трассировки передается снова и снова.  
  
 *metadata_filename*  
 Имя файла данных, который содержит метаданные события. Это имя имеет в качестве суффикса отметку времени, что позволяет предотвратить перезапись данных, если одно и то же сообщение трассировки передается снова и снова.  
  
  
##  <a name="bkmk_script_stop"></a> Скрипт XMLA для остановки расширенных событий в службах Analysis Services  
 Чтобы остановить объект расширенных событий трассировки, необходимо удалить этот объект с помощью команды скрипта удаления объекта, аналогичной применяемой в XML для аналитики, как показано ниже.  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Batch ...>  
         <Delete ...>  
            <Object>  
               <TraceID>trace_id</TraceID>  
            </Object>  
         </Delete>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 Следующие элементы должны быть определены пользователем с учетом потребностей трассировки:  
  
 *trace_id*  
 Определяет уникальный идентификатор удаляемой трассировки.  
  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
  
