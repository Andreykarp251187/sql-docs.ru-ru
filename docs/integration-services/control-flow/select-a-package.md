---
title: Выбор пакета | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.selectapackage.f1
helpviewer_keywords:
- Select a Package dialog box
ms.assetid: 92b47a2b-21b5-460a-885d-6cc4bb567249
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8cc976451c29c6d0b1656fec456b2a46b1f4f5f1
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65727483"
---
# <a name="select-a-package"></a>Выбор пакета

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Используйте диалоговое окно **Выбор пакета** , чтобы указать пакет, из которого задача «Очередь сообщений» может получать сообщения.  
  
## <a name="static-options"></a>Статические параметры  
 **Местоположение**  
 Определяет местонахождение пакета. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Установите местонахождение экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При выборе данного значения отображаются динамические параметры, **Сервер**, **Использовать проверку подлинности Windows**, **Использовать проверку подлинности SQL Server**, **Имя пользователя**и **Пароль**.|  
|Файл DTSX|Установите местонахождение для файла DTSX. При выборе этого значения отображается динамический параметр **Имя файла**.|  
  
## <a name="location-dynamic-options"></a>Динамические параметры местоположения  
  
### <a name="location--sql-server"></a>Местонахождение = SQL Server  
 **Имя пакета**  
 Выберите пакет, хранимый на указанном сервере.  
  
 **Server**  
 Введите имя сервера или выберите его из списка.  
  
 **Использовать проверку подлинности Windows**  
 Выберите для использования проверки подлинности Windows.  
  
 **Использовать проверку подлинности SQL Server**  
 Выберите для использования проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **User name**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] введите имя пользователя, которое необходимо использовать для входа на сервер.  
  
 **Пароль**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] укажите пароль.  
  
### <a name="location--dtsx-file"></a>Местонахождение = файл DTSX  
 **Имя файла**  
 Укажите путь к пакету или нажмите кнопку обзора **(...)** и определите его расположение.  
  
## <a name="see-also"></a>См. также:  
 [Задача «Очередь сообщений»](../../integration-services/control-flow/message-queue-task.md)  
  
  
