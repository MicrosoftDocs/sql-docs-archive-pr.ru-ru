---
title: Работа с путями SQL Server PowerShell | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: f31d8e2c-8d59-4fee-ac2a-324668e54262
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6d2647251eb1c8843d4ab7a95d2c439e47f5bb6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731773"
---
# <a name="work-with-sql-server-powershell-paths"></a>Работа с  путями SQL Server PowerShell
  После перехода к узлу в пути поставщика компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] можно выполнять действия или с помощью методов и свойств извлекать информацию из управляющих объектов компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] , связанных с этим узлом.  
  
1.  [Перед началом](#BeforeYouBegin)  
  
2.  **To work on a path node:**  [Listing Methods and Properties](#ListPropMeth), [Using Methods and Properties](#UsePropMeth)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
 После того как выбран узел в пути поставщика компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] , можно выполнять действия двух типов.  
  
-   Можно запускать командлеты Windows PowerShell, работающие с узлами, такие как **Rename-Item**.  
  
-   Можно вызывать методы из соответствующей модели управляющих объектов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , например SMO. Например, если перейти в пути к узлу Databases, то можно использовать методы и свойства класса <xref:Microsoft.SqlServer.Management.Smo.Database> .  
  
 Поставщик [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] используется для управления объектами в экземпляре компонента [!INCLUDE[ssDE](../includes/ssde-md.md)]. Он не предназначен для работы с данными в базах данных. Если выбрана таблица или представление, нельзя использовать поставщик для выбора, вставки, обновления или удаления данных. Чтобы запросить или изменить данные в таблицах и представлениях из среды Windows PowerShell, воспользуйтесь командлетом **Invoke-Sqlcmd** . Дополнительные сведения см. в разделе [Invoke-Sqlcmd, командлет](../database-engine/invoke-sqlcmd-cmdlet.md).  
  
##  <a name="listing-methods-and-properties"></a><a name="ListPropMeth"></a>Вывод списка методов и свойств
  
 Командлет **Get-Member** используется для просмотра методов и свойств, доступных для определенных объектов или классов объектов.  
  
### <a name="examples-listing-methods-and-properties"></a>Примеры: список методов и свойств  
 В этом примере задается переменная Windows PowerShell для класса <xref:Microsoft.SqlServer.Management.Smo.Database> модели SMO и перечисляются методы и свойства:  
  
```powershell
$MyDBVar = New-Object Microsoft.SqlServer.Management.SMO.Database  
$MyDBVar | Get-Member -Type Methods  
$MyDBVar | Get-Member -Type Properties  
```  
  
 Командлет **Get-Member** также можно использовать для вывода методов и свойств, связанных с конечным узлом пути Windows PowerShell.  
  
 В этом примере выполняется переход к узлу Databases на диске SQLSERVER и перечисление свойства коллекции.  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
Get-Item . | Get-Member -Type Properties  
```  
  
 В этом примере выполняется переход к узлу AdventureWorks2012 по пути SQLSERVER: и перечисление свойства объектов.  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012  
Get-Item . | Get-Member -Type Properties  
```  
  
##  <a name="using-smo-methods-and-properties"></a><a name="UsePropMeth"></a>Использование методов и свойств объектов SMO  
  
 Для выполнения действий с объектами из пути поставщика компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] можно использовать методы и свойства объектов SMO.  
  
### <a name="examples-using-methods-and-properties"></a>Примеры: использование методов и свойств  
 В этом примере свойство **Schema** объекта SMO служит для получения списка таблиц из схемы Sales в базе данных AdventureWorks2012:  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012\Tables  
Get-ChildItem | Where {$_.Schema -eq "Sales"}  
```  
  
 В этом примере используется метод **скрипта** SMO для создания скрипта, содержащего инструкции, которые необходимо `CREATE VIEW` выполнить для повторного создания представлений в AdventureWorks2012:  
  
```powershell
Remove-Item C:\PowerShell\CreateViews.sql  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012\Views  
foreach ($Item in Get-ChildItem) { $Item.Script() | Out-File -Filepath C:\PowerShell\CreateViews.sql -append }  
```  
  
 В этом примере используется метод **Create** модели SMO, чтобы создать базу данных, а затем используется свойство **State** , чтобы показать, существует ли эта база данных:  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
$MyDBVar = New-Object Microsoft.SqlServer.Management.SMO.Database  
$MyDBVar.Parent = (Get-Item ..)  
$MyDBVar.Name = "NewDB"  
$MyDBVar.Create()  
$MyDBVar.State  
```  
  
## <a name="see-also"></a>См. также:  
 [Поставщик SQL Server PowerShell](sql-server-powershell-provider.md)   
 [Навигация по путям SQL Server PowerShell](navigate-sql-server-powershell-paths.md)   
 [Преобразование URN в пути поставщика SQL Server](../database-engine/convert-urns-to-sql-server-provider-paths.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
