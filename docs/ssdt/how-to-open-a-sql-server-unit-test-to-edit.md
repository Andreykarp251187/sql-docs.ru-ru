---
title: Руководство. Открытие модульного теста SQL Server для изменения | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: c6af1b12-54cd-42f9-b2ef-7164f8078323
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d464ba2cd7b3b5b3cb2ac687f9f9e1b3ae8023b0
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65098446"
---
# <a name="how-to-open-a-sql-server-unit-test-to-edit"></a>Руководство. открыть модульный тест SQL Server для изменения
После создания модульного теста SQL Server добавьте инструкции и условия тестов Transact**SQL с помощью** конструктора модульных тестов SQL Server\-. Тесты, создаваемые с помощью конструктора, формируют код Visual C# или Visual Basic. Код выполняется при запуске теста.  
  
Если тест соответствует требованиям, его можно запускать без изменений. Если в модульный тест требуется добавить дополнительные функции, его код можно изменить. Код находится в файле с расширением CS или VB в тестовом проекте. Дополнительные сведения см. в статье [Файлы модульного теста SQL Server](../ssdt/sql-server-unit-test-files.md). Тесты также можно настраивать путем создания новых тестовых условий. Дополнительные сведения см. в разделе [Как создавать условия теста для конструктора модульных тестов базы данных (Visual Studio 2010)](https://msdn.microsoft.com/library/aa833409(VS.100).aspx).  
  
> [!NOTE]  
> Если для удаления метода теста вносятся изменения в файл с расширением .cs или .vb, этот метод все равно будет отображаться в **конструкторе модульных тестов SQL Server**. Это происходит потому, что метод InitializeComponent класса тестов все еще содержит переменные этого теста. Несмотря на то что тест отображается в конструкторе, выполнить его невозможно, потому что его код удален. Чтобы повторно создать метод для этого теста, измените в редакторе код Transact\-SQL, а затем сохраните CS- или VB-файл либо перепостройте тестовый проект.  
  
### <a name="to-open-the-source-code-file-of-a-sql-server-unit-test-from-solution-explorer"></a>Открытие файла с исходным кодом модульного теста SQL Server из обозревателя решений  
  
-   В **обозревателе решений** щелкните правой кнопкой мыши файл с исходным кодом, содержащий модульный тест SQL Server, и выберите команду **Просмотр кода**.  
  
    При открытии файла метод модульного теста отображается в главном окне редактора Visual Studio.  
  
### <a name="to-open-the-source-code-file-of-a-sql-server-unit-test-from-the-test-view-window-visual-studio-2010"></a>Открытие файла с исходным кодом модульного теста SQL Server из окна представления теста (Visual Studio 2010)  
  
1.  Запустите модульный тест. Дополнительные сведения см. в разделе "Выполнение модульных тестов SQL Server" в статье [Пошаговое руководство. Создание и запуск модульного теста SQL Server](../ssdt/walkthrough-creating-and-running-a-sql-server-unit-test.md).  
  
2.  В окне "Представление теста" щелкните тест правой кнопкой мыши и выберите команду **Открыть тест**.  
  
    При открытии файла метод модульного теста отображается в главном окне редактора Visual Studio.  
  
### <a name="to-open-the-source-code-file-of-a-sql-server-unit-test-from-the-test-view-window-visual-studio-2012"></a>Открытие файла с исходным кодом модульного теста SQL Server из окна представления теста (Visual Studio 2012)  
  
1.  Запустите модульный тест. Дополнительные сведения см. в разделе "Выполнение модульных тестов SQL Server" в статье [Пошаговое руководство. Создание и запуск модульного теста SQL Server](../ssdt/walkthrough-creating-and-running-a-sql-server-unit-test.md).  
  
2.  В окне «Обозреватель тестов» щелкните имя файла с исходным кодом тестирования модулей.  
  
    При открытии файла метод модульного теста отображается в главном окне редактора Visual Studio.  
  
## <a name="see-also"></a>См. также:  
[Создание и определение модульных тестов SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
[Проверка кода базы данных с помощью модульных тестов SQL Server](../ssdt/verifying-database-code-by-using-sql-server-unit-tests.md)  
  
