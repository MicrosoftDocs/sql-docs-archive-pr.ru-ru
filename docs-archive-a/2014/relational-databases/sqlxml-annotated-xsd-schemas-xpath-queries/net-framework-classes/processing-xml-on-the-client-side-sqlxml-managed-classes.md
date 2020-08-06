---
title: Обработка XML на стороне клиента (управляемые классы SQLXML) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- processing XML on client side [SQLXML]
- client-side XML formatting
- Managed Classes [SQLXML], client-side XML formatting
- SQLXML Managed Classes, client-side XML formatting
- ClientSideXml property
ms.assetid: 5e7ecf18-66fc-49ff-bc50-83635cd7ac0b
author: rothja
ms.author: jroth
ms.openlocfilehash: fb90f7c5c823c750b64f47d0c9df9551b9f857b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655015"
---
# <a name="processing-xml-on-the-client-side-sqlxml-managed-classes"></a>Обработка XML-кода на стороне клиента (управляемые классы SQLXML)
  В этом примере показано использование свойства Клиентсидексмл. Приложение выполняет хранимую процедуру на сервере. Результат хранимой процедуры (набор строк из двух столбцов) обрабатывается на стороне клиента для создания XML-документа.  
  
 Следующая хранимая процедура "связи" возвращает " **FirstName** " и " **LastName** " сотрудников в таблице Person. Contact в базе данных AdventureWorks.  
  
```  
USE AdventureWorks  
CREATE PROCEDURE GetContacts @LastName varchar(20)  
AS  
SELECT FirstName, LastName  
FROM   Person.Contact  
WHERE LastName = @LastName  
Go  
```  
  
 Это приложение C# выполняет хранимую процедуру и задает параметр FOR XML AUTO в указании значения CommandText. В приложении свойству Клиентсидексмл объекта SqlXmlCommand присваивается значение true. Это позволяет выполнять существующие хранимые процедуры, возвращающие наборы строк, и применить к ним преобразование XML на стороне клиента.  
  
> [!NOTE]  
>  В коде необходимо задать имя экземпляра Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в строке соединения.  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
    static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         //Stream strm;  
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.ClientSideXml = true;  
         cmd.CommandText = "EXEC GetContacts ? FOR XML NESTED";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         using (Stream strm = cmd.ExecuteStream())   
         {  
            using (StreamReader sr = new StreamReader(strm))  
                  {  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;  
      }  
  
public static int Main(String[] args)  
{  
    testParams();  
    return 0;  
}  
}  
```  
  
 Чтобы проверить этот пример, необходимо установить на компьютер платформу [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework.  
  
### <a name="to-test-the-application"></a>Тестирование приложения  
  
1.  Создайте хранимую процедуру.  
  
2.  Сохраните в папке код C# (файл DocSample.cs), приведенный в этом примере. Измените этот код, указав нужные имя входа и пароль.  
  
3.  Скомпилируйте код. Чтобы скомпилировать код из командной строки, введите следующую команду.  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Будет создан исполняемый файл (DocSample.exe).  
  
4.  Запустите файл DocSample.exe из командной строки.  
  
  
