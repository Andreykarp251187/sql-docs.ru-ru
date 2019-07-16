---
title: xp_msver (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_msver_TSQL
- xp_msver
dev_langs:
- TSQL
helpviewer_keywords:
- xp_msver
ms.assetid: 9264cf8c-92ba-45ad-b2d6-15d26d805a16
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b936f00f449bd57a7a00fa825910a809a1baf225
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67898368"
---
# <a name="xpmsver-transact-sql"></a>xp_msver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **xp_msver** также возвращает сведения о номере действительной компоновки сервера и сведения о среде сервера. Сведения, **xp_msver** возвращает могут использоваться в [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций, пакетов, хранимых процедур и т. д., чтобы усовершенствовать логику не зависящего от платформы кода.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
xp_msver [ optname ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *optname*  
 Имя параметра может иметь одно из следующих значений.  
  
|Имя параметра/столбца|Описание|  
|-------------------------|-----------------|  
|**ProductName**|Название продукта; например [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ProductVersion**|Номер версии продукта.|  
|**Язык**|Языковая версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Платформа**|Имя операционной системы, имя производителя и имя семейства чипов для компьютера, на котором работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Комментарии**|Различные сведения об [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Название организации**|Имя компании, производящей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; например [!INCLUDE[msCoName](../../includes/msconame-md.md)] Corporation.|  
|**FileDescription**|Операционная система.|  
|**Необязательный параметр**|Версия исполняемого файла [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Внутреннееимя**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] внутреннее имя для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например SQLSERVR.|  
|**LegalCopyright**|Юридические сведения об авторских правах, необходимых для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; например Copyright © [!INCLUDE[msCoName](../../includes/msconame-md.md)] Corp. 1988-2005.|  
|**LegalTrademarks**|Сведения о зарегистрированном товарном знаке, требуемые для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Например [!INCLUDE[msCoName](../../includes/msconame-md.md)] является охраняемым товарным знаком [!INCLUDE[msCoName](../../includes/msconame-md.md)] Corporation.|  
|**OriginalFilename**|Имя файла, выполняемого при запуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; например Sqlservr.exe.|  
|**PrivateBuild**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**SpecialBuild**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**WindowsVersion**|Версия [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, установленная на компьютере, где работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ProcessorCount**|Количество процессоров в компьютере, где работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ProcessorActiveMask**|Показывает запущенные и пригодные к использованию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows процессоры, установленные в компьютере, на котором работает [!INCLUDE[msCoName](../../includes/msconame-md.md)].|  
|**ProcessorType**|Тип процессора. Аналогичную **платформы**.|  
|**PhysicalMemory**|Количество памяти RAM в мегабайтах (МБ), установленной на компьютере, где работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Идентификатор продукта**|Идентификационный номер продукта (PID). Указывается в процессе установки. Этот номер расположен на наклейке на подлинной коробке с дисками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 1 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 **xp_msver**, без параметров возвращает четыре столбца результирующего набора, перечислены все значения параметров. **xp_msver**, для любого параметра возвращает четыре столбца результирующего набора со значениями для этого параметра.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="see-also"></a>См. также  
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Общие расширенные хранимые процедуры &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [@@VERSION &#40;Transact-SQL&#41;](../../t-sql/functions/version-transact-sql-configuration-functions.md)  
  
  
