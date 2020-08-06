---
title: Создание, изменение и удаление триггеров | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- triggers [SMO]
ms.assetid: 8ddbe23b-6e31-4f8e-8a70-17bd5072413e
author: stevestein
ms.author: sstein
ms.openlocfilehash: c2cdd1573c488fbe7b2309f656cd6bf42e82a527
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668199"
---
# <a name="creating-altering-and-removing-triggers"></a>Создание, изменение и удаление триггеров
  В SMO триггеры представлены объектом <xref:Microsoft.SqlServer.Management.Smo.Trigger>. [!INCLUDE[tsql](../../../includes/tsql-md.md)]Код, выполняемый при срабатывании триггера, задается <xref:Microsoft.SqlServer.Management.Smo.Trigger.TextBody%2A> свойством объекта триггера. Тип триггера определяется другими свойствами объекта <xref:Microsoft.SqlServer.Management.Smo.Trigger>, например свойством <xref:Microsoft.SqlServer.Management.Smo.Trigger.Update%2A>. Это логическое свойство, которое указывает, срабатывает ли триггер при выполнении инструкции `UPDATE` для записей в родительской таблице.  
  
 Объект <xref:Microsoft.SqlServer.Management.Smo.Trigger> представляет обычные триггеры языка обработки данных DML. В [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] и более поздних версиях также поддерживаются триггеры языка определения данных DDL. Триггеры DDL представлены объектом <xref:Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger> и объектом <xref:Microsoft.SqlServer.Management.Smo.ServerDdlTrigger>.  
  
## <a name="example"></a>Пример  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-basic"></a>Создание, изменение и удаление триггера на языке Visual Basic  
 В этом примере кода показано, как создать и вставить триггер Update в существующую таблицу с именем `Sales`в базе данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . Триггер отправляет сообщение с напоминанием при обновлении таблицы или вставке новой записи.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBTriggers1](SMO How to#SMO_VBTriggers1)]  -->  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-c"></a>Создание, изменение и удаление триггера на языке Visual C#  
 В этом примере кода показано, как создать и вставить триггер Update в существующую таблицу с именем `Sales`в базе данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . Триггер отправляет сообщение с напоминанием при обновлении таблицы или вставке новой записи.  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server mysrv;  
            mysrv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database mydb;  
            mydb = mysrv.Databases["AdventureWorks2012"];  
            //Declare a Table object variable and reference the Customer table.   
            Table mytab;  
            mytab = mydb.Tables["Customer", "Sales"];  
            //Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.   
            Trigger tr;  
            tr = new Trigger(mytab, "Sales");  
            //Set TextMode property to False, then set other properties to define the trigger.   
            tr.TextMode = false;  
            tr.Insert = true;  
            tr.Update = true;  
            tr.InsertOrder = ActivationOrder.First;  
            string stmt;  
            stmt = " RAISERROR('Notify Customer Relations',16,10) ";  
            tr.TextBody = stmt;  
            tr.ImplementationType = ImplementationType.TransactSql;  
            //Create the trigger on the instance of SQL Server.   
            tr.Create();  
            //Remove the trigger.   
            tr.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-trigger-in-powershell"></a>Создание, изменение и удаление триггера в PowerShell  
 В этом примере кода показано, как создать и вставить триггер Update в существующую таблицу с именем `Sales`в базе данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . Триггер отправляет сообщение с напоминанием при обновлении таблицы или вставке новой записи.  
  
```powershell
# Set the path context to the local, default instance of SQL Server and to the  
#database tables in Adventureworks2012  
CD \sql\localhost\default\databases\AdventureWorks2012\Tables\  
  
#Get reference to the trigger's target table  
$mytab = Get-Item Sales.Customer  
  
# Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.  
$tr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Trigger -argumentlist $mytab, "Sales"  
  
# Set TextMode property to False, then set other properties to define the trigger.
$tr.TextMode = $false  
$tr.Insert = $true  
$tr.Update = $true  
$tr.InsertOrder = [Microsoft.SqlServer.Management.SMO.Agent.ActivationOrder]::First  
$tr.TextBody = " RAISERROR('Notify Customer Relations',16,10) "  
$tr.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Create the trigger on the instance of SQL Server.
$tr.Create()  
  
#Remove the trigger.
$tr.Drop()  
```  
