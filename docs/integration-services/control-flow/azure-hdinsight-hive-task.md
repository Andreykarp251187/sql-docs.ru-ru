---
title: Задача Hive для Azure HDInsight | Документы Майкрософт
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afphivetask.f1
- sql14.dts.designer.afphivetask.f1
ms.assetid: e1896c73-128a-4128-9814-3e01f7dfe19b
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 0d94c492504798095e01f20fbe78a023e8254c92
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67947279"
---
# <a name="azure-hdinsight-hive-task"></a>Задача Hive для Azure HDInsight

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


**Задача Hive для Azure HDInsight** позволяет выполнить скрипт Hive в кластере Azure HDInsight.
     
Чтобы добавить **задачу Hive для Azure HDInsight**, перетащите ее в конструктор SSIS, дважды щелкните или щелкните правой кнопкой мыши и выберите **Изменить** , чтобы открыть диалоговое окно **Редактор задач Hive для Azure HDInsight** .  
  
**Задача Hive для Azure HDInsight** входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
 В следующем списке описаны поля этого диалогового окна.  
  
1.  В поле **HDInsightConnection** выберите существующий диспетчер подключений Azure HDInsight (или создайте новый), который ссылается на кластер Azure HDInsight, используемый для выполнения скрипта.
  
2.  В поле **AzureStorageConnection** выберите существующий диспетчер подключений службы хранилища Azure (или создайте новый), который ссылается на учетную запись хранения Azure, связанную с кластером. Это необходимо только в том случае, если требуется скачать выходные данные выполнения скрипта и журналы ошибок.
 
3.  В поле **BlobContainer** укажите имя контейнера хранилища, связанного с кластером. Это необходимо только в том случае, если требуется скачать выходные данные выполнения скрипта и журналы ошибок.
  
4.  В поле **LocalLogFolder** укажите папку, в которую будут скачиваться выходные данные выполнения скрипта и журналы ошибок. Это необходимо только в том случае, если требуется скачать выходные данные выполнения скрипта и журналы ошибок.   
  
5.  Существует два способа указать выполняемый скрипт Hive.
  
    1.  **Встроенный скрипт.** Укажите значение в поле **Скрипт**, введя скрипт, который необходимо выполнить, в диалоговом окне **Введите сценарий**.
  
    2.  **Файл скрипта.** Отправьте файл скрипта в хранилище BLOB-объектов Azure и укажите значение в поле **BlobName**. Если BLOB-объект не находится в используемом по умолчанию хранилище или контейнере, связанном с кластером HDInsight, нужно указать значения в полях **ExternalStorageAccountName** и **ExternalBlobContainer**. Если используется внешний BLOB-объект, убедитесь в том, что он настроен как общедоступный.  
  
     Если использованы оба способа, будет задействован файл скрипта, а встроенный скрипт будет проигнорирован.
