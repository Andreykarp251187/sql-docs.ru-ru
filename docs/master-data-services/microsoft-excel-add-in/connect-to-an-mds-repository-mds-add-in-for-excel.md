---
title: Соединение с репозиторием MDS (надстройка MDS для Excel) | Документы Майкрософт
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 8f427312-4c09-4c8b-b9f9-8b235557a74b
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 5dcfad83ed20960402f26d2af71b845db044597b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65488886"
---
# <a name="connect-to-an-mds-repository-mds-add-in-for-excel"></a>Соединение с репозиторием MDS (надстройка MDS для Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]необходимо установить соединение с репозиторием MDS, прежде чем можно будет загружать или публиковать данные.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
### <a name="to-connect-to-an-mds-repository"></a>Соединение с репозиторием MDS  
  
1.  В MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]на вкладке **Основные данные** в группе **Соединение и загрузка** нажмите стрелку под кнопкой **Соединение** и выберите команду **Управление соединениями**.  
  
2.  В диалоговом окне **Управление соединениями** в разделе **Новое соединение** нажмите кнопку **Создать новое соединение**.  
  
3.  Нажмите кнопку **Создать**.  
  
4.  В диалоговом окне **Добавление нового соединения** в поле **Описание** введите описание соединения. Это соединение будет отображаться при нажатии стрелки кнопки **Соединение** на панели инструментов.  
  
5.  В поле **Адрес сервера MDS** введите URL-адрес веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], например `https://contoso/mds`.  
  
    > [!NOTE]  
    >  Следует использовать имя компьютера, а не localhost.  
  
6.  Нажмите кнопку **ОК**. Это имя появится в разделе **Существующие соединения** .  
  
7.  Можно нажать кнопку **Проверка** , чтобы проверить соединение. Будет выдано диалоговое окно подтверждения или сообщение об ошибке. Чтобы закрыть его, нажмите кнопку **ОК** .  
  
8.  Нажмите кнопку **Соединить**. Отображается панель **Службы Master Data Services** .  
  
## <a name="next-steps"></a>Next Steps  
  
-   [Экспорт данных в Excel из Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)  
  
-   [Фильтрация данных перед их экспортом (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>См. также:  
 [Соединения (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/connections-mds-add-in-for-excel.md)  
  
  
