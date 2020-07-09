---
title: Задание языка сеанса | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server], international considerations
- globalization [SQL Server], sessions
- time [SQL Server]
- sessions [SQL Server], languages
- international considerations [SQL Server], sessions
- dates [SQL Server], session languages
- global considerations [SQL Server], sessions
- client-side session language
- time [SQL Server], session languages
- messages [SQL Server], international considerations
- server-side session language
ms.assetid: de7f2c90-8f4f-4cfc-94cc-4933a7fd2bde
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d2acf936682a9c220d08df637778169e9a5b5840
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85719904"
---
# <a name="set-a-session-language"></a>Задание языка сеанса
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Язык сеанса можно применять для настройки отображения элементов на сервере в зависимости от языковых и культурных предпочтений.  
  
-   Язык, на котором будут отображаться сообщения об ошибках и другие системные сообщения. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает работу с несколькими копиями всех строк и сообщений о системных ошибках на всех языках, для которых произведена локализация [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Текст этих сообщений можно просмотреть в представлении каталога [sys.messages](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md) . При установке локализованной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]эти сообщения будут переведены на выбранный во время установки язык. По умолчанию устанавливается также набор системных сообщений для языка «Английский (США)». Кроме этого, существует процедура [sp_addmessage](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md), которая позволяет добавлять пользовательские сообщения на выбранном языке.  
  
-   Формат даты и времени.  
  
-   Названия дней и месяцев, включая сокращения.  
  
-   Первый день недели.  
  
-   Денежные единицы.  
  
 Доступно 33 языка сеансов. Список языков приведен в таблице [sys.syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md).  
  
## <a name="setting-the-session-language-from-the-server"></a>Настройка языка сеанса на стороне сервера  
 Язык сеанса задается с сервера с помощью команды [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md).  
  
## <a name="setting-the-session-language-from-the-client"></a>Настройка языка сеанса на стороне клиента  
 Язык сеанса на компьютере клиента настраивается с помощью OLE DB, ODBC или ADO.NET. Для OLE DB язык сеанса настраивается с помощью свойства SSPROP_INIT_CURRENTLANGUAGE. Дополнительные сведения см. в статье [Свойства инициализации и авторизации](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
 В ODBC используется ключевое слово Language. Дополнительные сведения см. в статье [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md).  
  
 В ADO.NET используется параметр **Текущий язык** объекта **ConnectionString** . Дополнительные сведения см. в документации пакета средств разработки программного обеспечения (SDK) для компонентов доступа к данным [!INCLUDE[msCoName](../../includes/msconame-md.md)] (MDAC).  
  
  
