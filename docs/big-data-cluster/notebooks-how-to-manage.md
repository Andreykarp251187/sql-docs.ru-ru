---
title: Управление записных книжек в Azure Data Studio
titleSuffix: SQL Server big data clusters
description: Сведения об управлении записных книжек в Azure Data Studio. Это включает в себя Открытие записных книжек, их сохранение и изменение подключения кластера больших данных.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cf0041ee2beecb0864f196c4d13c7be309b40d17
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727568"
---
# <a name="how-to-manage-notebooks-in-azure-data-studio"></a>Как управлять записных книжек в Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этой статье показано, как открывать и сохранять файлы записной книжки в Azure Data Studio с предварительной версией SQL Server 2019. Также показано, как изменить подключение к кластеру больших данных SQL Server.

## <a name="prerequisites"></a>предварительные требования

В этой статье предполагается, что уже записную книжку, который вы хотите использовать в Azure Data Studio. Если вы хотите создать записную книжку, см. в разделе [использованию записных книжек в предварительной версии SQL Server 2019](notebooks-guidance.md). Чтобы использовать записные книжки в Azure Data Studio, необходимо выполнить следующие условия:

- [Развертывание кластера больших данных](quickstart-big-data-cluster-deploy.md).
- [Средства SQL Server 2019 больших данных](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
   - **kubectl**

## <a name="open-a-notebook"></a>Откройте записную книжку

Существует несколько способов, чтобы открыть **откройте записную книжку** диалоговое окно. Можно использовать меню "файл", панели мониторинга и палитру команд. В следующих разделах каждый метод.

### <a name="file-menu"></a>Меню "файл"

Выберите **Открытие файла** меню "файл" Ctrl + O (в Windows) и Cmd + O (в Mac).

![Открытие диалогового окна открытия файла, выбрав Открытие файла](./media/notebooks-how-to-manage/open-file-1.png) 

### <a name="dashboard"></a>Панель мониторинга

Нажмите кнопку **откройте записную книжку** на панели мониторинга, чтобы открыть диалоговое окно открытия файла.

![Открытие диалогового окна открытия файла, выбрав открыть записную книжку в панели мониторинга](./media/notebooks-how-to-manage/open-file-2.png) 

### <a name="command-palette"></a>Палитра команд

Используйте команду **файла: Откройте** палитре команд введите сочетание клавиш Ctrl + Shift + P (в Windows) и Cmd + Shift + P (в Mac).

![Открытие диалогового окна открытия файла, введя File:Open в палитре команд](./media/notebooks-how-to-manage/open-file-3.png)

## <a name="save-a-notebook"></a>Сохранить записной книжки

В настоящее время является одним из способов сохранить записную книжку. Необходимо выбрать **Сохранить** на панели инструментов записной книжки.

![Сохраните файл, нажав кнопку "Сохранить" на панели инструментов записной книжки](./media/notebooks-how-to-manage/save-file-1.png)

> [!NOTE]
> Следующие методы в настоящее время не сохранять изменения для записных книжек:
>
> - **Файл: Сохранить**, **файл: Сохранить как...**  и **файл сохранить все** команды из меню "файл".
> - **Файл: Сохранить** команд, введенных в палитре команд.

## <a name="change-the-big-data-cluster"></a>Изменение кластера больших данных

Изменение кластера больших данных SQL Server для записной книжки.

1. Нажмите кнопку **присоединить к** меню на панели инструментов записной книжки.

   ![Нажмите кнопку присоединиться к меню на панели инструментов записной книжки](./media/notebooks-how-to-manage/select-attach-to-1.png)

2. Выберите сервер из **присоединить к** меню.

   ![Выберите сервер из присоединение к меню](./media/notebooks-how-to-manage/select-attach-to-2.png)

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о записных книжек в Azure Data Studio, см. в разделе [использованию записных книжек в предварительной версии SQL Server 2019](notebooks-guidance.md).