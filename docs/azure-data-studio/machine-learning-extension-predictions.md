---
title: Создание прогнозов с помощью расширения машинного обучения
titleSuffix: Azure Data Studio
description: Узнайте, как использовать расширение «Машинное обучение» для Azure Data Studio, чтобы создавать прогнозы с помощью модели ONNX в базе данных.
ms.date: 06/09/2020
ms.reviewer: sstein
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 5472f4ff32a807b58091fd56f3382aa73ead142e
ms.sourcegitcommit: dc8a30a4a27e15fc6671ca2674da9b7c637ec255
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2020
ms.locfileid: "88745494"
---
# <a name="make-predictions-with-machine-learning-extension-preview-for-azure-data-studio"></a>Создание прогнозов с помощью расширения машинного обучения для Azure Data Studio (предварительная версия)

Узнайте, как использовать [расширение «Машинное обучение» для Azure Data Studio](machine-learning-extension.md), чтобы создавать прогнозы с помощью модели ONNX в базе данных. Расширение создаст сценарий T-SQL, используя [PREDICT](../t-sql/queries/predict-transact-sql.md), чтобы сделать прогнозы для набора данных, хранящегося в таблице, с ранее импортированной моделью, расположенной в локальном файле или в Машинном обучении Azure.

> [!IMPORTANT]
> Прогнозирование с помощью расширения "Машинное обучение" в настоящее время поддерживает только [Службы машинного обучения в управляемом экземпляре SQL Azure](/azure/azure-sql/managed-instance/machine-learning-services-overview) и [Azure SQL для пограничных вычислений с ONNX](/azure/azure-sql-edge/onnx-overview).

## <a name="prerequisites"></a>Предварительные требования

- Установите и настройте [расширение «Машинное обучение» для Azure Data Studio](machine-learning-extension.md). Укажите [пути установки Python в параметрах расширения](machine-learning-extension.md#settings).

- Установите пакеты Python **onnxruntime**, **mlflow** и **mlflow-dbstore**. Если пакеты еще не установлены, расширение «Машинное обучение» предложит вам установить их.

## <a name="make-predictions-from-onnx-model"></a>Создание прогнозов на основе модели ONNX

Выполните приведенные ниже действия, чтобы использовать модель ONNX для составления прогнозов.

1. Щелкните **Составление прогнозов**.

1. Если будет предложено установить пакеты **onnxruntime**, **mlflow** и **mlflow-dbstore**, выберите **Да**.

1. Выберите место расположения модели и нажмите кнопку **Далее**. Вы можете использовать:
    - **Импортированные модели**. Выберите, чтобы использовать модель, которая уже хранится в базе данных. Выберите **Шаблон базы данных** и **Шаблон таблицы**, в которых находится модель, выберите нужную модель и нажмите **Далее**.
    - **Отправка файлов**. Выберите этот вариант, чтобы использовать модель из файла. Выберите файл модели в разделе **Исходные файлы** и нажмите кнопку **Далее**.
    - **Машинное обучение Azure**. Выберите этот вариант, чтобы использовать модель из Машинного обучения Azure. Сначала **войдите в Azure**. Затем выберите значения для параметров **Учетная запись Azure**, **Подписка Azure**, **Группа ресурсов Azure** и **Рабочая область Azure ML**. Выберите нужную модель и нажмите кнопку **Далее**.

1. Сопоставьте исходные данные с моделью.
    - Выберите **Исходную базу данных**  и **Исходную таблицу**, содержащую набор данных, для которого необходимо применить прогноз.
    - Сопоставьте столбцы в разделе **Сопоставление входных данных модели** и **Выходные данные модели**. Расширение будет автоматически сопоставлять столбцы с одинаковыми именами и типами данных.

1. Нажмите **Выполнить прогноз**.

Azure Data Studio создаст новый запрос T-SQL с [PREDICT](../t-sql/queries/predict-transact-sql.md), который можно использовать для составления прогнозов по данным.

## <a name="next-steps"></a>Дальнейшие действия

- [Расширение "Машинное обучение" для Azure Data Studio](machine-learning-extension.md)
- [Управление пакетами в базе данных](machine-learning-extension-manage-packages.md)
- [Импорт или просмотр моделей](machine-learning-extension-import-view-models.md)
- [Записные книжки в Azure Data Studio](notebooks-guidance.md)
- [Документация по машинному обучению на SQL](../machine-learning/index.yml)
- [Службы машинного обучения в управляемом экземпляре SQL Azure](/azure/azure-sql/managed-instance/machine-learning-services-overview)
- [Машинное обучение и ИИ с применением ONNX в SQL для пограничных вычислений (предварительная версия)](/azure/azure-sql-edge/onnx-overview)
