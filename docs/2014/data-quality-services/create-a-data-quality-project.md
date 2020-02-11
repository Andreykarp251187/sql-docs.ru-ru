---
title: Создание проекта служб DQS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dqproject.newdqproject.f1
helpviewer_keywords:
- create,data quality project
- data quality project,create
ms.assetid: 19c52d2b-d28e-4449-ab59-5fe0dc326cd9
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: f341d13995cd7a13a06e0ad7b9b380ebd0184f7d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65480956"
---
# <a name="create-a-data-quality-project"></a>Создание проекта служб DQS
  В этом разделе описывается создание проекта служб DQS с помощью программы [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Проект качества данных используется для выполнения очистки или сопоставления данных в службах [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
 Необходимо иметь соответствующие базы знаний для использования в проекте качества данных для выполнения очистки или сопоставления данных.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для создания проекта служб DQS необходимо иметь роль dqs_kb_editor или dqs_kb_operator в базе данных DQS_MAIN.  
  
##  <a name="Create"></a>Создание проекта качества данных  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Запустите приложение Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На главном экране [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] щелкните **Создать проект служб DQS**.  
  
3.  На экране **Новый проект служб DQS**  
  
    1.  в поле **Имя** введите имя нового проекта служб DQS.  
  
    2.  В текстовом поле **Описание** введите описание нового проекта служб DQS (необязательно).  
  
    3.  В списке **Использовать базу знаний** выберите базу знаний для использования в проекте служб DQS. Область **Сведения о базе знаний: <имя_базы_знаний>** в правой части содержит доступные в выбранной базе знаний доменные имена.  
  
    4.  В области **Выбор действия** выберите действие, которое требуется выполнить с помощью этого проекта служб DQS:  
  
        -   **Очистка**: выберите это действие, чтобы очистить исходные данные.  
  
        -   **Сопоставление**. Выберите это действие, чтобы выполнить сопоставление. Это действие доступно только в том случае, если база знаний, выбранная для проекта служб DQS, содержит политику сопоставления.  
  
4.  Нажмите **Создать** , чтобы создать проект служб DQS.  
  
##  <a name="FollowUp"></a>Дальнейшие действия. После создания проекта качества данных  
 После того как проект качества данных создан, откроется мастер для выполнения выбранного действия: очистки или сопоставления. Дополнительные сведения о действиях по очистке и сопоставлению см. в разделах [Очистка данных](../../2014/data-quality-services/data-cleansing.md) и [Сопоставление данных](../../2014/data-quality-services/data-matching.md).  
  
  
