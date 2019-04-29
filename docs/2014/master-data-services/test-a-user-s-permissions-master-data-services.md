---
title: Проверка разрешений пользователя (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 83a03b85-ea7f-4b4a-b19b-f7eca534ffae
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 0160628621049db7c9498ca931c675c080e78b8d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923233"
---
# <a name="test-a-user39s-permissions-master-data-services"></a>Проверка разрешений пользователя (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно создать тестовую учетную запись и войти в веб-приложение для проверки разрешений. При попытке пользователя получить доступ к URL-адресу [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выполняется проверка учетных данных пользователя. В Internet Explorer в зависимости от параметров безопасности проверка подлинности будет выполнена автоматически либо пользователю придется ввести имя и пароль. Чтобы изменить эти настройки, выполните следующие действия.  
  
### <a name="to-test-a-users-security"></a>Проверка безопасности пользователя  
  
1.  В Internet Explorer версии 7 и выше выберите в меню **Сервис**пункт **Свойства обозревателя**и перейдите на вкладку **Безопасность** .  
  
2.  Нажмите **Местная интрасеть** , затем нажмите кнопку **Другой** .  
  
3.  В разделе **Проверка подлинности пользователя** выберите **Запрос имени пользователя и пароля**.  
  
4.  При следующем открытии окна браузера будет предложено указать имя пользователя и пароль.  
  
## <a name="see-also"></a>См. также:  
 [Безопасность (службы Master Data Services)](security-master-data-services.md)  
  
  
