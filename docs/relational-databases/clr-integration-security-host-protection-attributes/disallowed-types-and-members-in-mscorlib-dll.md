---
title: Недопустимые типы и элементы в mscorlib. dll | Документация Майкрософт
description: SQL Server программировании CLR не разрешает тип или член с некоторыми значениями перечисления Хостпротектионресаурце. В этой статье перечислены запрещенные значения mscorlib. dll.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: daf82d4b-2f6d-44ca-9148-75193321b6d5
author: rothja
ms.author: jroth
ms.openlocfilehash: 3c00877ce41cd15d27814bc67bf78bd32f6719ff
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81486883"
---
# <a name="disallowed-types-and-members-in-mscorlibdll"></a>Недопустимые типы и элементы в библиотеке mscorlib.dll
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Программирование в среде CLR запрещает использование типа или члена с **HostProtectionAttribute** , который указывает перечисление **System. Security. Permissions. Хостпротектионресаурце** со значением **екстерналпроцессмгмт**, **екстерналсреадинг**, **майлеаконаборт**, **секуритинфраструктуре**, **SelfAffectingProcessMgmnt**, **SelfAffectingThreading**, **SharedState**, **Synchronization**или **UI**. В следующей таблице перечислены типы и элементы сборки mscorlib.dll, значения атрибута защиты узла которых не допускаются.  
  
> [!NOTE]  
>  Этот список был создан из поддерживаемых сборок. Дополнительные сведения см. в разделе [supported .NET Framework librarys](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
|Тип или элемент|Значения атрибутов защиты узла|  
|--------------------|--------------------|  
|SyncStream.BeginRead()|ExternalThreading|  
|SyncStream.BeginWrite()|ExternalThreading|  
|System.Collections.ArrayList.Synchronized()|Синхронизация|  
|System.Collections.Hashtable.Synchronized()|Синхронизация|  
|System.Collections.Queue.Synchronized()|Синхронизация|  
|System.Collections.SortedList.Synchronized()|Синхронизация|  
|System.Collections.Stack.Synchronized()|Синхронизация|  
|System.Console.Beep()|UI|  
|System.Console.get_Error()|UI|  
|System.Console.get_In()|UI|  
|System.Console.get_KeyAvailable()|UI|  
|System.Console.get_Out()|UI|  
|System.Console.OpenStandardError()|UI|  
|System.Console.OpenStandardInput()|UI|  
|System.Console.OpenStandardOutput()|UI|  
|System.Console.Read()|UI|  
|System.Console.ReadKey()|UI|  
|System.Console.ReadLine()|UI|  
|System.Console.SetError()|UI|  
|System.Console.SetIn()|UI|  
|System.Console.SetOut()|UI|  
|System.Console.Write()|UI|  
|System.Console.WriteLine()|UI|  
|System.Diagnostics.LogMessageEventHandler|ExternalThreading, Synchronization|  
|System.IO.FileStream.BeginRead()|ExternalThreading|  
|System.IO.FileStream.BeginWrite()|ExternalThreading|  
|System.IO.Stream.Synchronized()|Синхронизация|  
|System.IO.TextReader.Synchronized()|Синхронизация|  
|System.IO.TextWriter.Synchronized()|Синхронизация|  
|System.Reflection.Emit.AssemblyBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.ConstructorBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.CustomAttributeBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.EnumBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.EventBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.FieldBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.MethodBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.MethodRental|MayLeakOnAbort|  
|System.Reflection.Emit.ModuleBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.PropertyBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.TypeBuilder|MayLeakOnAbort|  
|System.Reflection.Emit.UnmanagedMarshal|MayLeakOnAbort|  
|System.Security.Principal.WindowsPrincipal|SecurityInfrastructure|  
|System.Threading.AutoResetEvent|ExternalThreading, Synchronization|  
|System.Threading.EventWaitHandle|ExternalThreading, Synchronization|  
|System.Threading.ManualResetEvent|ExternalThreading, Synchronization|  
|System.Threading.Monitor|ExternalThreading, Synchronization|  
|System.Threading.Mutex|ExternalThreading, Synchronization|  
|System.Threading.ReaderWriterLock|ExternalThreading, Synchronization|  
|System.Threading.Thread.AllocateDataSlot()|ExternalThreading, SharedState|  
|System.Threading.Thread.AllocateNamedDataSlot()|ExternalThreading, SharedState|  
|System.Threading.Thread.BeginCriticalRegion()|ExternalThreading, Synchronization|  
|System.Threading.Thread.EndCriticalRegion()|ExternalThreading, Synchronization|  
|System.Threading.Thread.FreeNamedDataSlot()|ExternalThreading, SharedState|  
|System.Threading.Thread.GetData()|ExternalThreading, SharedState|  
|System.Threading.Thread.GetNamedDataSlot()|ExternalThreading, SharedState|  
|System.Threading.Thread.Join()|ExternalThreading, Synchronization|  
|System.Threading.Thread.set_ApartmentState()|Synchronization, SelfAffectingThreading|  
|System.Threading.Thread.set_CurrentUICulture()|ExternalThreading|  
|System.Threading.Thread.set_IsBackground()|SelfAffectingThreading|  
|System.Threading.Thread.set_Name()|ExternalThreading|  
|System.Threading.Thread.set_Priority()|SelfAffectingThreading|  
|System.Threading.Thread.SetApartmentState()|Synchronization, SelfAffectingThreading|  
|System.Threading.Thread.SetData()|ExternalThreading, SharedState|  
|System.Threading.Thread.SpinWait()|ExternalThreading, Synchronization|  
|System.Threading.Thread.Start()|ExternalThreading, Synchronization|  
|System.Threading.Thread.TrySetApartmentState()|Synchronization, SelfAffectingThreading|  
|System.Threading.ThreadPool|ExternalThreading, Synchronization|  
|System.Threading.Timer|ExternalThreading, Synchronization|  
|System.Threading.TimerBase|ExternalThreading, Synchronization|  
  
## <a name="see-also"></a>См. также:  
 [Атрибуты защиты узла и программирование интеграции со средой CLR](../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Недопустимые типы и члены в Microsoft. VisualBasic. dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [Недопустимые типы и члены в System. dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-dll.md)   
 [Недопустимые типы и члены в System. Data. dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-data-dll.md)   
 [Недопустимые типы и элементы в библиотеке System.Core.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-core-dll.md)  
  
  
