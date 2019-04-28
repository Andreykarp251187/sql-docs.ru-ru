---
title: Управление паролями (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Managing Passwords in Oracle, Exporting or Importing Encrypted Password
- Managing passwords in Oracle, Securing Password
ms.assetid: 8c7d9f8e-06bb-476c-bbd2-15b61d5bba3c
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: c6b99dfd27655894456a1b0957c8c42f31819e1b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62795744"
---
# <a name="managing-passwords-oracletosql"></a>Управление паролями (OracleToSQL)
Этот раздел посвящен защита пароли к базам данных и процедуру для импорта или экспорта их на серверах:  
  
1.  Защита пароля  
  
2.  Экспорт или импорт зашифрованный пароль  
  
## <a name="securing-password"></a>Защита пароля  
SSMA позволяет защищать пароль базы данных.  
  
Используйте следующую процедуру для установления безопасного соединения:  
  
Укажите допустимый пароль с помощью одного из следующих трех методов:  
  
1.  **Открытый текст:** Введите пароль базы данных в атрибуте значение узла «пароль». Его можно найти в разделе Определение узел сервера в разделе сервера из файла сценария или файла соединения сервера.  
  
    Пароли в виде открытого текста не являются безопасными. Таким образом возникнет следующее предупреждающее сообщение в выходных данных консоли: *«Server &lt;идентификатор сервера&gt; пароль предоставляется в виде открытого текста, небезопасный, SSMA консольное приложение предоставляет возможность защитить пароль с помощью шифрования, см. параметр - securepassword в файле справки SSMA для получения дополнительных сведений информация».*  
  
    **Зашифрованные пароли:** В этом случае указанный пароль хранится в зашифрованном виде на локальном компьютере в ProtectedStorage.ssma.  
  
    -   **Защита паролей**  
  
        -   Выполнение `SSMAforOracleConsole.exe` с `-securepassword` и добавьте параметр командной строки, передав сервера соединение или скрипт файл, содержащий узел пароля в разделе "Определение" server.  
  
        -   В командной строке пользователю предлагается ввести пароль и подтвердите его.  
  
            Определения идентификаторов серверов и его соответствующие зашифрованные пароли хранятся в файле на локальном компьютере  
            
            Пример 1.  
            
                Specify password
                
                C:\SSMA\SSMAforOracleConsole.EXE -securepassword -add all -s "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx
            
            Пример 2.
            
                C:\SSMA\SSMAforOracleConsole.EXE -securepassword -add "source_1,target_1" -c "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ServersConnectionFileSample.xml" - v "D:\Program Files\Microsoft SQL Server Migration Assistant for Oracle\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx  
    
    -   **Удаление зашифрованных паролей**  
  
        Выполнение `SSMAforOracleConsole.exe` с`-securepassword` и `-remove` переключиться в командной строке, передав идентификаторов серверов, чтобы удалить зашифрованные пароли из защищенного хранилища файле присутствует на локальном компьютере.  
        
        Пример  
        
            C:\SSMA\SSMAforOracleConsole.EXE -securepassword -remove all
            C:\SSMA\SSMAforOracleConsole.EXE -securepassword -remove "source_1,target_1"  
  
    -   **Список идентификаторов серверов, чьи пароли шифруются**  
  
        Выполнение `SSMAforOracleConsole.exe` с `-securepassword` и `-list` переключиться в командной строке, чтобы получить список идентификаторов серверов, чьи пароли были зашифрованы.  
  
        Пример  
        
            C:\SSMA\SSMAforOracleConsole.EXE -securepassword -list  
  
    > [!NOTE]  
    > 1.  Пароль в виде открытого текста, упомянутые в файле подключения скрипт или сервера имеет приоритет над зашифрованный пароль в защищенный файл.  
    > 2.  Если пароль не существует в разделе сервера файле подключения сервера или файла скрипта или при отсутствии защиты на локальном компьютере, консоли появится запрос на ввод пароля.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Экспорт или импорт зашифрованных паролей  
SSMA консольного приложения позволяет экспортировать пароли зашифрованной базы данных представлен в файле на локальном компьютере для защищенного файла и наоборот. Он помогает в создании независимых машины зашифрованные пароли. Функция экспорта считывает идентификатор сервера и пароль из локального защищенное хранилище и сохраняет данные в зашифрованном файле. Пользователю предлагается ввести пароль для защищенного файла. Убедитесь, что введенный пароль имеет значение не менее 8 символов. Этот защищенный файл можно переносить на разных компьютерах. Функции импорта считывает значения сервера идентификатор и пароль из защищенного файла. Пользователю предлагается ввести пароль для защищенного файла и добавляет данные в локальном защищенном хранилище.  
  
Пример  

    Export password
    
    Enter password for protecting the exported file C:\SSMA\SSMAforOracleConsole.EXE -securepassword -export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforOracleConsole.EXE -p -e "OracleDB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
Пример  

    Import an encrypted password
    
    Enter password for protecting the imported file C:\SSMA\SSMAforOracleConsole.EXE -securepassword -import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforOracleConsole.EXE -p -i "OracleDB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
## <a name="see-also"></a>См. также  
[Выполнение команд консоли SSMA (Oracle)](https://msdn.microsoft.com/7228ccba-c69f-4b4c-8664-01a2750183c5)  
  
