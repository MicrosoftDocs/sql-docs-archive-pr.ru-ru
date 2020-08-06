---
title: Использование ADO для выполнения запросов SQLXML 4.0
ms.custom: ''
ms.date: 12/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- query testers [SQLXML]
- test scripts
- ADO [SQLXML]
- queries [SQLXML], ADO
- SQLXML, ADO
ms.assetid: 3d54e3bb-7c5f-427e-82f8-1403a54c4f53
author: rothja
ms.author: jroth
ms.openlocfilehash: 169d20b4192e4a5b8e7b32839f2da255fc58d89c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729346"
---
# <a name="using-ado-to-execute-sqlxml-40-queries"></a>Использование ADO для выполнения запросов SQLXML 4.0
  В предыдущих версиях SQLXML выполнение запросов по HTTP поддерживалось с помощью виртуальных каталогов SQLXML в IIS и ISAPI-фильтра SQLXML. В SQLXML 4.0 эти компоненты были удалены, так как похожая и перекрывающаяся функциональность предоставляется собственными веб-службами с поддержкой XML, начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 В качестве альтернативы можно выполнять запросы и использовать SQLXML 4.0 с приложениями на основе COM, используя расширения SQLXML для объектов данных ActiveX (ADO), которые появились в компонентах доступа к данным (MDAC) версии 2.6 и более поздних.  
  
 В этом разделе демонстрируется использование SQLXML и ADO как части приложения Visual Basic Scripting Edition (VBScript) (скрипта с расширением файла VBS). Обеспечивает начальную процедуру установки, которая помогает создать повторно и тестировать образцы запросов в документации SQLXML 4.0.  
  
## <a name="creating-the-sqlxml-40-test-script"></a>Создание тестового скрипта SQLXML 4.0  
 В этой процедуре создается файл VBScript (.vbs), Sqlxml4test.vbs, который можно использовать для выполнения запросов SQLXML с использованием ADO-расширений SQLXML в ADO 2.6 и более поздних версий.  
  
#### <a name="to-create-the-sqlxml-40-query-tester-using-ado-vbscript"></a>Создание испытателя запросов SQLXML 4.0 с использованием ADO (VBScript)  
  
1.  Скопируйте приведенный ниже код VBScript и вставьте его в текстовый файл. Сохраните файл с именем Sqlxml4test.xml.  
  
    ```vb
    WScript.Echo "Query process may take a few seconds to complete. Please be patient."  
  
    ' Note that for SQL Server Native Client to be used as the data provider,  
    ' it needs to be installed on the client computer first. Also, SQLXML extensions   
    ' for ADO are used and available in MDAC 2.6 or later.  
  
    'Set script variables.  
    inputFile = "@@FILE_NAME@@"  
    strServer = "@@SERVER_NAME@@"  
    strDatabase = "@@DATABASE_NAME@@"  
    dbGuid = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  
    ' Establish ADO connection to SQL Server and   
    ' create an instance of the ADO Command object.  
    Set conn = CreateObject("ADODB.Connection")  
    Set cmd = CreateObject("ADODB.Command")  
    conn.Open "Provider=SQLXMLOLEDB.4.0;Data Provider=SQLNCLI11;Server=" & strServer & _  
              ";Database=" & strDatabase & ";Integrated Security=SSPI"  
    Set cmd.ActiveConnection = conn  
  
    ' Create the input stream as an instance of the ADO Stream object.  
    Set inStream = CreateObject("ADODB.Stream")  
    inStream.Open  
    inStream.Charset = "utf-8"  
    inStream.LoadFromFile inputFile  
  
    ' Set ADO Command instance to use input stream.  
    Set cmd.CommandStream = inStream  
  
    ' Set the command dialect.  
    cmd.Dialect = dbGuid  
  
    ' Set a second ADO Stream instance for use as a results stream.   
    Set outStream = CreateObject("ADODB.Stream")  
    outStream.Open  
  
    ' Set dynamic properties used by the SQLXML ADO command instance.   
    cmd.Properties("XML Root").Value = "ROOT"  
    cmd.Properties("Output Encoding").Value = "UTF-8"  
  
    ' Connect the results stream to the command instance and execute the command.  
    cmd.Properties("Output Stream").Value = outStream  
    cmd.Execute , , 1024  
  
    ' Echo cropped/partial results to console.  
    WScript.Echo Left(outStream.ReadText, 1023)  
  
    inStream.Close  
    outStream.Close  
    ```  
  
2.  Обновите следующие значения скриптов для образца, который предстоит протестировать, и тестовой среды.  
  
    -   Найдите «`@@FILE_NAME@@`» и замените его именем файла шаблона.  
  
    -   Найдите «`@@SERVER_NAME@@`» и замените его именем экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (например, «`(local)`», если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется локально).  
  
    -   Найдите «`@@DATABASE_NAME@@`» и замените его именем базы данных (например, «`AdventureWorks2012`» или «`tempdb`»).  
  
     Обновите любые другие значения, упомянутые в конкретных инструкциях для примера, который нужно создать повторно локально на компьютере.  
  
3.  Сохраните файл и закройте его.  
  
4.  Проверьте, что созданы все дополнительные файлы, такие как XML-шаблоны или схемы, которые являются частью образца, который нужно локально создать повторно на компьютере. Эти файлы должны находиться в том же каталоге, в котором сохранен файл тестового скрипта (Sqlxml4test.vbs).  
  
5.  Следуйте инструкциям следующего раздела по использованию тестового скрипта SQLXML 4.0.  
  
## <a name="using-the-sqlxml-40-test-script"></a>Использование тестового скрипта SQLXML 4.0  
 Следующая процедура описывает способ использования файлов Sqlxml4test.vbs для тестирования примеров запросов, предоставленных в этой документации.  
  
#### <a name="to-use-the-sqlxml-40-query-tester"></a>Использование испытателя запросов SQLXML 4.0  
  
1.  Проверьте, что установлен собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    1.  В меню " **Пуск** " выберите пункт " **Параметры**", а затем " **Панель управления**".  
  
    2.  В панели управления откройте окно **Установка и удаление программ** .  
  
    3.  В списке установленных программ убедитесь, что в списке присутствует **Microsoft SQL Server Native Client** .  
  
        > [!NOTE]  
        >  Если необходимо установить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент, см. статью [Установка SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md).  
  
2.  Проверьте, что на клиентском компьютере установлена версия MDAC 2.6 или более поздняя. Если необходимо проверить сведения о версии MDAC, можно использовать средство проверки компонентов MDAC, которое предоставляется бесплатно для загрузки с веб-сайта корпорации Майкрософт [https://www.microsoft.com/](https://www.microsoft.com/) . Для получения дополнительных сведений выполните поиск по фразе "средство проверки компонентов MDAC" на веб-сайте Майкрософт.  
  
3.  Выполните скрипт.  
  
     Файл VBScript можно выполнить из командной строки с использованием Cscript.exe или дважды щелкнув файл Sqlxml4test.vbs, чтобы вызвать сервер скриптов Windows (WScript.exe).  
  
     При выполнении скрипт должен вывести сообщение, предупреждая, что выполнение скрипта может занять некоторое время перед возвратом и отображением результатов запроса как вывода скрипта. После того как данные будут выведены, сравните их с ожидаемыми результатами запроса.  
  
  
