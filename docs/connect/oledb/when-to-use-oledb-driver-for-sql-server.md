---
title: Случаи использования драйвера OLE DB для SQL Server | Документация Майкрософт
description: Когда использовать драйвер OLE DB для SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], about OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 210a15d827cb8f0a828c11c1c8fe87586cd79028
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66795874"
---
# <a name="when-to-use-ole-db-driver-for-sql-server"></a>Когда использовать драйвер OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server — одна из технологий, который можно использовать для доступа к данным в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных.  Обсуждение других технологий доступа к данным см. в разделе [Схема технологий доступа к данным](https://go.microsoft.com/fwlink/?LinkID=179186).  
  
 В принятии решения о необходимости использования в качестве технологии доступа к данным драйвера OLE DB для SQL Server необходимо принимать во внимание ряд факторов.  
  
 Если используется язык программирования с управляемым кодом, например Microsoft Visual C# или Visual Basic, и необходимо обращаться к новым функциям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то для новых приложений следует пользоваться поставщиком данных .NET Framework для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который является частью платформы .NET Framework.  
  
 Если разрабатывается приложение на основе COM и необходим доступ к новым функциям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], следует использовать драйвер OLE DB для SQL Server. Если доступ к новым возможностям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не требуется, то можно продолжать использовать компоненты WDAC.  
  
 Для существующих приложений OLE DB самый важный вопрос — необходим ли доступ к новым функциям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если имеется отлаженное приложение, не требующее новых возможностей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то можно продолжать использование компонентов WDAC. Но если требуется доступ к новым возможностям, например к новому [типу данных xml](../../t-sql/xml/xml-transact-sql.md), то необходимо использовать драйвер OLE DB для SQL Server.  
  
 Оба драйвер OLE DB для SQL Server и MDAC поддерживают изоляции транзакций read committed с использованием управления версиями строк, но только драйвер OLE DB для изоляции транзакции моментальных снимков поддерживает SQL Server. С точки зрения программирования уровень изоляции транзакции READ COMMITTED с управлением версиями строк — то же самое, что и транзакция READ COMMITTED.  
  
 Сведения о различиях между драйвер OLE DB для SQL Server и MDAC см. в разделе [обновление приложения для драйвера OLE DB для SQL Server с компонентами MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  
  
## <a name="see-also"></a>См. также:  
 [Драйвер OLE DB для SQL Server](../oledb/oledb-driver-for-sql-server.md)     
 [Инструкции по OLE DB](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
