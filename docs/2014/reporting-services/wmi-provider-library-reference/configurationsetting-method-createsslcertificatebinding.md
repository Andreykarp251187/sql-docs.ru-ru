---
title: Метод CreateSSLCertificateBinding (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- CreateSSLCertificateBinding
ms.assetid: 407d50e4-0a55-43cb-8ddf-2d82714071b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f16b86b1343d83c44819427b8ba6c43726798e93
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66098543"
---
# <a name="createsslcertificatebinding-method-wmi-msreportserver_configurationsetting"></a>Метод CreateSSLCertificateBinding (WMI MSReportServer_ConfigurationSetting)
  Создает привязку SSL-сертификата.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub CreateSSLCertificateBinding(ByVal Application As String, _  
    ByVal CertificateHash As String, ByVal IPAddress As String, _  
    ByVal Port As Int32, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void CreateSSLCertificateBinding(string application,   
    string certificateHash, string IPAddress, int Port,   
    int lcid, out string error, out int HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *Приложение*  
 Имя приложения, для которого следует создать привязку к сертификату.  
  
 *CertificateHash*  
 Хэш для сертификата.  
  
 *IPAddress*  
 IP-адрес для приложения.  
  
 *Порт*  
 Порт SSL, связанный с привязкой.  
  
 *Намного*  
 Локаль, используемая для возвращаемых сообщений об ошибке.  
  
 *Ошибка*  
 [out] Описание случившихся ошибок.  
  
 *СОСТАВ*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 означает, что вызов метода завершился успешно; код ошибки означает, что произошла ошибка.  
  
## <a name="remarks"></a>Remarks  
 Этот метод позволяет добавить привязку приложения в файл rsreportserver.config. Если привязка еще не существует в файле HTTP.SYS, то она в нем создается.  
  
 Перед созданием привязки при вызове метода происходит проверка зарезервированных URL-адресов для того, чтобы указанное приложение могло определить допустимость привязки сертификата SSL.  
  
 Выполняется проверка следующих условий, результатом которой могут стать ошибки.  
  
1.  Сертификат не существует.  
  
2.  Указанный сертификат не соответствует значению, указанному для параметра IPAddress для этого компьютера.  
  
3.  Указанное значение параметра IPAddress является адресом категории DHCP IPAddress (изменение которого происходит периодически). Рекомендуется вместо указанного адреса использовать IP-адрес с подстановочными символами (0.0.0.0).  
  
4.  Указанное значение параметра IPAddress не соответствует IP-адресу, указанному в списке зарезервированных URL-адресов и не является подстановочным символом или именем хоста для существующего зарезервированного URL-адреса.  
  
5.  Наличие зарезервированного URL-адреса, определяющего, что имя хоста не совпадает с именем, указанным в сертификате имени хоста.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
