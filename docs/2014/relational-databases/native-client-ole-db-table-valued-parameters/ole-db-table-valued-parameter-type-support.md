---
title: Поддержка типов параметров OLE DB, возвращающих табличные значения | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
ms.assetid: 147036a0-260e-4f81-8b3b-89209e023a32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 27ae90e05784c18d85f84daa9955818d3133ad07
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63046508"
---
# <a name="ole-db-table-valued-parameter-type-support"></a>Поддержка типа возвращающего табличное значение параметра OLE DB
  Этот раздел содержит описание поддержки типа параметра OLE DB для параметров, возвращающих табличное значение.  
  
## <a name="table-valued-parameter-rowset-object"></a>Объект набора строк параметра, возвращающего табличное значение  
 Можно создать специальный объект набора строк для параметров, возвращающих табличное значение. Объект набора строк возвращающего табличное значение параметра создается с помощью Итабледефинитионвисконстраинтс:: Креатетаблевисконстраинтс или IOpenRowset:: OpenRowset. Для этого установите элемент *eKind* параметра *pTableID* в значение DBKIND_GUID_NAME и укажите CLSID_ROWSET_INMEMORY как элемент *guid*. Имя типа сервера для возвращающего табличное значение параметра должно быть указано в *pwszName* члене *PTableID* при использовании IOpenRowset:: OPENROWSET. Объект набора строк параметра, возвращающего табличное значение, действует так же, как объект поставщика OLE DB собственного клиента для SQL Server.  
  
```  
const GUID CLSID_ROWSET_TVP =   
{0xc7ef28d5, 0x7bee, 0x443f, {0x86, 0xda, 0xe3, 0x98, 0x4f, 0xcd, 0x4d, 0xf9}};  
  
CoType RowsetTVP  
{  
[mandatory] interface IAccessor;  
[mandatory] interface IColumnsInfo;  
[mandatory] interface IConvertType;  
[mandatory] interface IRowset;  
[mandatory] interface IRowsetInfo;  
[optional]  interface IColumnsRowset;  
[optional]  interface IRowsetChange;  
[optional]  interface ISupportErrorInfo;  
};  
```  
  
## <a name="dbtype_table"></a>DBTYPE_TABLE  
 Новый тип, DBTYPE_TABLE, представляет собой табличный тип. Этот тип описывает возвращающие табличное значение параметры в различных интерфейсах OLE DB, где требуется тип DBTYPE.  
  
```  
#define DBTYPE_TABLE (143)  
```  
  
 DBTYPE_TABLE имеет такой же формат, что и DBTYPE_IUNKNOWN. Представляет собой указатель на объект в буфере данных. Чтобы определить полную спецификацию в привязках, потребитель заполняет буфер DBOBJECT, задавая для параметра *iid* один из интерфейсов объекта набора строк (IID_IRowset). Если объект DBOBJECT в привязках не указан, то предполагается использование объекта IID_IRowset.  
  
 Прямые и обратные преобразования в тип DBTYPE_TABLE для каких-либо других типов не поддерживаются. Метод IConvertType::CanConvert возвращает значение S_FALSE для неподдерживаемого преобразования применительно к любому запросу, отличному от преобразования DBTYPE_TABLE в DBTYPE_TABLE. При этом предполагается использование параметра DBCONVERTFLAGS_PARAMETER объекта Command.  
  
## <a name="methods"></a>Методы  
 Дополнительные сведения о методах OLE DB, которые поддерживают возвращающие табличное значение параметры, см. в разделе [OLE DB тип возвращающего табличное значение параметра поддержка &#40;методов&#41;](ole-db-table-valued-parameter-type-support-methods.md).  
  
## <a name="properties"></a>Свойства  
 Дополнительные сведения о OLE DB свойствах, поддерживающих возвращающие табличное значение параметры, OLE DB см. в разделе [Поддержка типа возвращающего табличное значение параметра &#40;свойств&#41;](ole-db-table-valued-parameter-type-support-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Возвращающие табличные значения параметры &#40;OLE DB&#41;](table-valued-parameters-ole-db.md)   
 [Использование возвращающих табличные значения параметров &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
