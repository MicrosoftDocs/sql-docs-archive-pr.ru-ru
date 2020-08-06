---
title: Объект SqlDataRecord | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlDataRecord object
- custom result sets [CLR integration]
ms.assetid: 2ed667fb-749c-4280-a8fb-650643683c8f
author: rothja
ms.author: jroth
ms.openlocfilehash: 87a26f5a2ff5fc6af73a30a7ca28d78c2b5ee52b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658836"
---
# <a name="sqldatarecord-object"></a><span data-ttu-id="b31e7-102">Объект SqlDataRecord</span><span class="sxs-lookup"><span data-stu-id="b31e7-102">SqlDataRecord Object</span></span>
  <span data-ttu-id="b31e7-103">Объект `SqlDataRecord` представляет одну строку данных и связанные с ними метаданные.</span><span class="sxs-lookup"><span data-stu-id="b31e7-103">The `SqlDataRecord` object represents a single row of data, along with its related metadata.</span></span>  
  
 <span data-ttu-id="b31e7-104">Управляемые хранимые процедуры могут отправлять результирующие наборы, которые не относятся к `SqlDataReader`.</span><span class="sxs-lookup"><span data-stu-id="b31e7-104">Managed stored procedures may send to the client result sets that are not from a `SqlDataReader`.</span></span> <span data-ttu-id="b31e7-105">Класс `SqlDataRecord` вместе с методами `SendResultsStart`, `SendResultsRow` и `SendResultsEnd` объекта `SqlPipe` позволяет хранимым процедурам отправлять клиенту пользовательские результирующие наборы.</span><span class="sxs-lookup"><span data-stu-id="b31e7-105">The `SqlDataRecord` class, along with `SendResultsStart`, `SendResultsRow`, and `SendResultsEnd` methods of the `SqlPipe` object, allows stored procedures to send custom result sets to the client.</span></span>  
  
 <span data-ttu-id="b31e7-106">Дополнительные сведения см. в справочной документации по классу `Microsoft.SqlServer.Server.SqlDataRecord` в документации по пакету .NET Framework SDK.</span><span class="sxs-lookup"><span data-stu-id="b31e7-106">For more information, see the `Microsoft.SqlServer.Server.SqlDataRecord` class reference documentation in the .NET Framework SDK documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b31e7-107">Пример</span><span class="sxs-lookup"><span data-stu-id="b31e7-107">Example</span></span>  
 <span data-ttu-id="b31e7-108">В следующем примере создается новая запись сотрудника, которая возвращается вызывающему.</span><span class="sxs-lookup"><span data-stu-id="b31e7-108">The following example creates a new employee record and returns it to the caller.</span></span>  
  
 <span data-ttu-id="b31e7-109">C#</span><span class="sxs-lookup"><span data-stu-id="b31e7-109">C#</span></span>  
  
```  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void CreateNewRecordProc()  
{  
    // Variables.         
    SqlDataRecord record;  
  
    // Create a new record with the column metadata.  The constructor   
    // is able to accept a variable number of parameters.  
    record = new SqlDataRecord(new SqlMetaData("EmployeeID", SqlDbType.Int),  
                               new SqlMetaData("Surname", SqlDbType.NVarChar, 20),  
                               new SqlMetaData("GivenName", SqlDbType.NVarChar, 20),  
                               new SqlMetaData("StartDate", SqlDbType.DateTime) );  
  
    // Set the record fields.  
    record.SetInt32(0, 0042);  
    record.SetString(1, "Funk");  
    record.SetString(2, "Don");  
    record.SetDateTime(3, new DateTime(2005, 7, 17));  
  
    // Send the record to the calling program.  
    SqlContext.Pipe.Send(record);  
  
}  
```  
  
 <span data-ttu-id="b31e7-110">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b31e7-110">Visual Basic</span></span>  
  
```  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  CreateNewRecordVBProc ()  
    ' Variables.  
    Dim record As SqlDataRecord  
  
    ' Create a new record with the column metadata. The constructor is   
    ' able to accept a variable number of parameters  
  
    record = New SqlDataRecord(New SqlMetaData("EmployeeID", SqlDbType.Int), _  
                           New SqlMetaData("Surname", SqlDbType.NVarChar, 20), _  
                           New SqlMetaData("GivenName", SqlDbType.NVarChar, 20), _  
                           New SqlMetaData("StartDate", SqlDbType.DateTime))  
  
    ' Set the record fields.  
    record.SetInt32(0, 42)  
    record.SetString(1, "Funk")  
    record.SetString(2, "Don")  
    record.SetDateTime(3, New DateTime(2005, 7, 17))  
  
    ' Send the record to the calling program.  
    SqlContext.Pipe.Send(record)  
  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="b31e7-111">См. также:</span><span class="sxs-lookup"><span data-stu-id="b31e7-111">See Also</span></span>  
 [<span data-ttu-id="b31e7-112">Объект SqlPipe</span><span class="sxs-lookup"><span data-stu-id="b31e7-112">SqlPipe Object</span></span>](sqlpipe-object.md)  
  
  
