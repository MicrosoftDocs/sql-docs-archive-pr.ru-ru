---
title: Использование групповой загрузки SQLXML в среде .NET | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, XML Bulk Load
- XML Bulk Load [SQLXML], .NET environment
- .NET Framework [SQLXML], XML Bulk Load
- bulk load [SQLXML], .NET environment
ms.assetid: b85df83b-ba56-43bf-bcdf-b2a6fca43276
author: rothja
ms.author: jroth
ms.openlocfilehash: 6bd1c44a8b56bc5129aeb9843ed9ba814d45742a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738174"
---
# <a name="using-sqlxml-bulk-load-in-the-net-environment"></a>Использование массовой загрузки SQLXML в среде .NET
  В этом разделе объясняется, как можно использовать функциональность массовой загрузки XML в среде .NET. Подробные сведения о групповой загрузке XML см. в разделе [выполнение групповой загрузки XML-данных &#40;SQLXML 4,0&#41;](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md).  
  
 Для использования объекта COM массовой загрузки SQLXML в управляемой среде необходимо добавить в этот объект ссылку на проект. Это сформирует управляемый интерфейс оболочки объекта массовой загрузки COM.  
  
> [!NOTE]  
>  Управляемая массовая загрузка XML не работает с управляемыми потоками и требует оболочки собственных потоков. Компонент массовой загрузки SQLXML не будет запущен в многопоточной среде (атрибут '[MTAThread]'). При попытке запустить компонент с массовыми загрузками в многопотоковой среде возникает исключение InvalidCastException со следующими дополнительными сведениями: "QueryInterface для интерфейса SQLXMLBULKLOADLib. Исклксмлбулклоад Failed". Обходной путь состоит в том, чтобы сделать объект, содержащий объект групповой загрузки, доступный для одного потока (например, с помощью атрибута **[STAThread]** , как показано в примере).  
  
 Этот раздел содержит образец реализации приложения на языке C# для массовой загрузки XML-данных в базу данных. Чтобы создать образец реализации, выполните следующие шаги.  
  
1.  Создайте следующие таблицы:  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int identity(1,1)  PRIMARY KEY,  
             CustomerID  varchar(5))  
    GO  
    CREATE TABLE Product (  
             ProductID   int identity(1,1) PRIMARY KEY,  
             ProductName varchar(20))  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID))  
    GO  
    ```  
  
2.  Сохраните в файле (schema.xml) следующую схему:  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
    <xsd:annotation>  
      <xsd:appinfo>  
        <sql:relationship name="OrderOD"  
              parent="Ord"  
              parent-key="OrderID"  
              child="OrderDetail"  
              child-key="OrderID" />  
  
        <sql:relationship name="ODProduct"  
              parent="OrderDetail"  
              parent-key="ProductID"  
              child="Product"  
              child-key="ProductID"   
              inverse="true"/>  
      </xsd:appinfo>  
    </xsd:annotation>  
  
      <xsd:element name="Order" sql:relation="Ord"   
                                sql:key-fields="OrderID" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="Product" sql:relation="Product"   
                         sql:key-fields="ProductID"  
                         sql:relationship="OrderOD ODProduct">  
              <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
              </xsd:complexType>  
            </xsd:element>  
         </xsd:sequence>  
            <xsd:attribute name="OrderID"   type="xsd:integer" />   
            <xsd:attribute name="CustomerID"   type="xsd:string" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  Сохраните в файле (data.xml) следующий образец XML-документа:  
  
    ```  
    <ROOT>    
      <Order OrderID="11" CustomerID="ALFKI">  
        <Product ProductID="11" ProductName="Chai" />  
        <Product ProductID="22" ProductName="Chang" />  
      </Order>  
      <Order OrderID="22" CustomerID="ANATR">  
         <Product ProductID="33" ProductName="Aniseed Syrup" />  
        <Product ProductID="44" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  Запустите среду Visual Studio.  
  
5.  Создайте консольное приложение C#.  
  
6.  В меню **проект** выберите команду **Добавить ссылку**.  
  
7.  На вкладке **com** выберите **БИБЛИОТЕКУ типов Microsoft SQLXML Bulkload 4,0** (xblkld4.dll) и нажмите кнопку **ОК**. Вы увидите сборку **Interop. SQLXMLBULKLOADLib** , созданную в проекте.  
  
8.  Замените метод Main() на следующий код. Обновите свойство **ConnectionString** и путь к файлу схемы и файлов данных.  
  
    ```  
    [STAThread]  
       static void Main(string[] args)  
       {     
             try  
             {  
                SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class objBL = new SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class();  
                objBL.ConnectionString = "Provider=sqloledb;server=server;database=databaseName;integrated security=SSPI";  
                objBL.ErrorLogFile = "error.xml";  
                objBL.KeepIdentity = false;  
                objBL.Execute ("schema.xml","data.xml");  
             }  
             catch(Exception e)  
             {  
             Console.WriteLine(e.ToString());  
             }  
       }  
    ```  
  
9. Для загрузки XML в создаваемую таблицу постройте и запустите проект.  
  
    > [!NOTE]  
    >  Ссылку на компонент массовой загрузки (xblkld4.dll) можно также добавить при помощи средства tlbimp.exe, которое доступно как часть платформы .NET Framework. Это средство создает управляемую оболочку для собственной DLL-библиотеки (xblkld4.dll), которую затем можно использовать в любом проекте .NET. Пример:  
  
    ```  
    c:\>tlbimp xblkld4.dll  
    ```  
  
     Это средство создает DLL-библиотеку управляемой оболочки (SQLXMLBULKLOADLib.dll), которую можно использовать в проекте платформы .NET Framework. В .NET Framework ссылка на проект добавляется к вновь созданной DLL-библиотеке.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение массовой загрузки XML-данных &#40;SQLXML 4.0&#41;](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
  
  
