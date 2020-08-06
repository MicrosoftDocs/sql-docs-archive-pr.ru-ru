---
title: Запуск DiffGram с помощью ADO (SQLXML 4,0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], SQLOLEDB Provider
- ADO [SQLXML]
- SQLXMLOLEDB Provider, DiffGrams
- data providers [SQLXML], SQLOLEDB Provider
- DiffGrams [SQLXML], ADO
ms.assetid: 741fce82-de83-4923-86eb-30acb5b9a5e6
author: rothja
ms.author: jroth
ms.openlocfilehash: b96db25fd46b1ecbbc15c8acd912743e5560f178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664814"
---
# <a name="executing-a-diffgram-by-using-ado-sqlxml-40"></a>Выполнение дельты с использованием ADO (SQLXML 4.0)
  Следующее приложение на языке [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic использует ADO для установки соединения с экземпляром Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и выполняет DiffGram. В этом приложении дельты и схема XSD хранятся в файле. Приложение загружает DiffGram из заданного файла. Вы можете использовать любую из дельтами (и связанную с ней схему XSD), описанную в разделе [примеры DiffGram](diffgram-examples-sqlxml-4-0.md).  
  
 Ниже приводится последовательность действий в образце приложения.  
  
-   Объект **conn** (**ADODB. Соединение**) устанавливает соединение с выполняющимся экземпляром SQL Server на определенном сервере.  
  
-   Объект **cmd** (**ADODB. Command**) выполняется для установленного соединения.  
  
-   В качестве диалекта команды задано значение DBGUID_MSSQLXML.  
  
-   Объект DiffGram копируется в поток команд (**strmIn**) из файла.  
  
-   Поток вывода команды задается как объект **стрмаут** (**ADODB. Stream**) для получения возвращенных данных.  
  
-   При использовании поставщика SQLOLEDB вы по умолчанию получаете функциональность Microsoft SQLXML, предоставляемую библиотекой Sqlxmlx.dll. Чтобы использовать Sqlxml4.dll с поставщиком SQLOLEDB, свойство **версии SQLXML** должно иметь значение **SQLXML. 4.0** для объекта **соединения** поставщика SQLOLEDB.  
  
-   Команда (дельта) будет выполнена.  
  
 Следующий код представляет собой образец приложения.  
  
> [!NOTE]  
>  В коде необходимо задать имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в строке соединения.  
  
```  
Private Sub Command1_Click()  
  Dim cmd As New ADODB.Command  
  Dim conn As New ADODB.Connection  
  Dim strmOut As New ADODB.Stream  
  Dim strmIn As New ADODB.Stream  
  
  'Open a connection to SQL Server.  
  conn.Provider = "SQLOLEDB"  
  conn.Open "server=SqlServerName; database=tempdb; Integrated Security=SSPI; "  
  conn.Properties("SQLXML Version") = "SQLXML.4.0"  
  Set cmd.ActiveConnection = conn  
  strmIn.Open  
  strmIn.Charset = "UTF-8"  
  strmIn.LoadFromFile "C:\SomeFilePath\SampleDiffGram.xml"  
  strmIn.Position = 0  
  Set cmd.CommandStream = strmIn  
  
  strmOut.Open  
  cmd.Properties("Output Stream").Value = strmOut  
  cmd.Properties("Output Encoding").Value = "UTF-8"  
  
  cmd.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  cmd.Properties("Mapping Schema") = "C:\SomeFilePath\SampleDiffGram.xml"  
  cmd.Execute , , adExecuteStream  
  strmOut.Position = 0  
  Set cmd = Nothing  
  strmOut.Charset = "UTF-8"  
  strmOut.SaveToFile "C:\DropIt.txt", adSaveCreateOverWrite  
  strmOut.Close  
  Set strmOut = Nothing  
  
End Sub  
```  
  
### <a name="to-test-the-diffgram"></a>Проверка дельты  
  
1.  В папку на компьютере скопируйте любую из дельтами и соответствующую схему XSD из одного из примеров в [примерах DiffGram](diffgram-examples-sqlxml-4-0.md).  
  
2.  Откройте Visual Basic и создайте проект стандартного исполняемого файла.  
  
3.  Добавьте эти ссылки в проект:  
  
    ```  
    Microsoft ActiveX Data Objects 2.8 Library  
    ```  
  
4.  На панели элементов щелкните **CommandButton**, а затем нарисуйте кнопку в форме.  
  
5.  Дважды нажмите кнопку, чтобы изменить ее код, и добавьте код приложения из раздела.  
  
6.  Отредактируйте код, чтобы в нем указывались имена файлов DiffGram и XSD. Также отредактируйте строку соединения.  
  
7.  Запустите приложение. Результат выполнения зависит от типа DiffGram.  
  
  
