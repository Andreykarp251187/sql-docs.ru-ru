---
title: Метод SetServiceAccount (класс SqlService) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetServiceAccount Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetServiceAccount method
ms.assetid: d5782892-e9d8-4d48-92af-b3afe9610f84
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cbd2e80a4d5484368a63e0d3c92c638e1a6294c2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119927"
---
# <a name="setserviceaccount-method-sqlservice-class"></a>Метод SetServiceAccount (класс SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Пытается изменить имя пользователя и пароль, с которыми выполняется экземпляр службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetServiceAccount(ServiceStartName , ServiceStartPassword)  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , представляющий службу.  
  
#### <a name="parameters"></a>Параметры  
 *ServiceStartName*  
 Строковое значение, указывающее имя учетной записи, под которым выполняется служба. В зависимости от типа службы имя учетной записи может иметь формат ИмяДомена\ИмяПользователя. При запуске процесс службы входит в систему, используя один из следующих двух форматов:  
  
-   если учетная запись принадлежит встроенному домену, можно указать \ИмяПользователя;  
  
-   Если задано значение NULL, служба входит в систему как **LocalSystem** учетной записи.  
  
 Для ядра или драйверов системного уровня *StartName* содержит имя объекта драйвера \FileSystem\Rdr или \Driver\Xns, которое система ввода-вывода использует для загрузки драйвера устройства. Если задано значение NULL, драйвер выполняется с именем объекта «значение по умолчанию», созданным системой ввода-вывода на основе имени службы, например DWDOM\Admin.  
  
 *ServiceStartPassword*  
 Строковое значение, указывающее пароль для имени учетной записи в *StartName* параметра. Если пароль не меняется, указывается значение NULL. Если служба не имеет пароля, указывается пустая строка.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
