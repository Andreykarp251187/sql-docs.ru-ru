---
title: Свойства псевдонима (вкладка "Псевдоним")
description: Использование вкладки "Псевдоним" диалогового окна "Свойства", чтобы настроить псевдоним, чтобы можно было использовать альтернативное имя при соединении с экземпляром SQL Server.
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 2d1498e2-129c-4ce7-88e5-408e4037243c
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 098da595a57c82e4d0ff68713880f38fe6acb6d2
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85902190"
---
# <a name="ltaliasgt-properties-alias-tab"></a>Свойства &lt;псевдонима&gt; (вкладка "Псевдоним")

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

Псевдоним является альтернативным именем, которое можно использовать для создания соединения. Псевдоним инкапсулирует необходимые элементы строки соединения и представляет их с помощью имени, выбранного пользователем. Используйте страницу **Псевдоним** в диалоговом окне **Свойства \<**Alias name**>** , чтобы просматривать или указывать элементы строки подключения псевдонима.

## <a name="options"></a>Параметры

**Имя псевдонима**

Имя (псевдоним), которое будет использоваться для ссылки на это соединение.  

**Имя канала** / **Номер порта**  

Дополнительные элементы строки подключения. Имя этого поля зависит от выбранного протокола. Примеры см. в перечисленных ниже разделах.  

**протокол**;

Протокол, используемый для соединения.

**Server**

Имя экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], к которому выполняется подключение.  

## <a name="see-also"></a>См. также:

- [Создание допустимой строки соединения с использованием протокола общей памяти](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)
- [Создание допустимой строки подключения с использованием протокола TCP/IP](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)
- [Создание допустимой строки подключения, использующей протокол именованных каналов](https://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)