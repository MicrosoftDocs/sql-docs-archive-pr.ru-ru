---
title: Форматирование XML на стороне клиента (SQLXML 4,0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- FOR XML clause, formatting
- middle tier XML formatting [SQLXML]
- client-side XML formatting
- client-side-xml attribute
ms.assetid: 9630a21d-a93b-4d3b-8a25-c4b32399f993
author: rothja
ms.author: jroth
ms.openlocfilehash: bf4a680d79a25d24ebdf779b41fd3be5a5d6a605
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665928"
---
# <a name="client-side-xml-formatting-sqlxml-40"></a>Форматирование XML на стороне клиента (SQLXML 4.0)
  В этом разделе содержатся сведения о форматировании XML на стороне клиента. Форматирование на стороне означает форматирование XML на среднем уровне.  
  
> [!NOTE]  
>  В этом разделе содержатся дополнительные сведения об использовании предложения FOR XML на стороне клиента и предполагается предварительное знакомство с предложением FOR XML. Дополнительные сведения о XML см. в разделе [Создание XML с помощью for XML](../../xml/for-xml-sql-server.md).  
  
 **Важно!** Чтобы использовать функциональность XML на стороне клиента с новым `xml` типом данных, клиенты всегда должны использовать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поставщик данных Native Client (SQLNCLI11) вместо поставщика SQLOLEDB. SQLNCLI11 является самой последней версией поставщика SQL Server, поддерживающей все типы данных, появившиеся в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. FOR XML на стороне клиента с поставщиком SQLOLEDB воспринимает типы данных `xml` как строки.  
  
## <a name="formatting-xml-documents-on-the-client-side"></a>Форматирование XML-документов на стороне клиента  
 Предположим, клиентское приложение выполняет следующий запрос.  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
FOR XML RAW  
```  
  
 Только этот фрагмент запроса будет отправлен на сервер.  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
```  
  
 Сервер выполняет запрос и возвращает клиенту набор строк (который содержит FirstName и Ластнамеколумнс). Затем средний уровень применяет к набору строк преобразование FOR XML и возвращает XML-форматирование клиенту.  
  
 Аналогичным образом, при выполнении запроса XPath сервер возвращает клиенту набор строк, а затем к набору строк на стороне клиента применяется преобразование FOR XML EXPLICIT, создавая нужное XML-форматирование.  
  
 В следующей таблице приведены режимы, которые могут быть заданы для FOR XML на стороне клиента.  
  
|Режим FOR XML на стороне клиента|Комментировать|  
|-------------------------------|-------------|  
|RAW|Выдает одинаковый результат при указании в FOR XML на стороне клиента или сервера.|  
|NESTED|Похож на режим FOR XML AUTO на стороне сервера.|  
|EXPLICIT|Похож на режим FOR XML EXPLICIT на стороне сервера.|  
  
> [!NOTE]  
>  Если указать режим AUTO и запросить XML-форматирование на стороне клиента, то запрос будет целиком отправлен на сервер, то есть XML-форматирование будет выполняться на сервере. Это сделано для удобства, но обратите внимание, что режим NESTED возвращает имена базовых таблиц в созданном в XML-документе как имена элементов. Для некоторых создаваемых пользователем приложений могут потребоваться имена базовых таблиц. Например, можно выполнить хранимую процедуру и загрузить результирующие данные в Dataset (на платформе [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework), а затем создать дельту для обновления данных в таблицах. В таком случае потребуются сведения о базовой таблице, и поэтому придется использовать режим NESTED.  
  
## <a name="benefits-of-client-side-xml-formatting"></a>Преимущества форматирования XML-кода на стороне клиента  
 Ниже приведены некоторые преимущества форматирования XML-кода на стороне клиента.  
  
### <a name="if-you-have-stored-procedures-on-the-server-that-return-a-single-rowset-you-can-request-client-side-for-xml-transformation-to-generate-an-xml"></a>При наличии на сервере хранимых процедур, которые возвращают единственный набор строк, можно для создания XML запросить преобразование FOR XML на стороне клиента.  
 Например, рассмотрим следующую хранимую процедуру. Она возвращает имена и фамилии сотрудников из таблицы Person.Contact в базе AdventureWorks.  
  
```  
IF EXISTS (SELECT name FROM sysobjects  
   WHERE name = 'GetContacts' AND type = 'P')  
   DROP PROCEDURE GetContacts  
GO  
CREATE PROCEDURE GetContacts  
AS  
    SELECT   FirstName, LastName  
    FROM     Person.Contact  
```  
  
 Следующий образец XML-шаблона выполняет хранимую процедуру. Предложение FOR XML указывается после имени хранимой процедуры.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    EXEC GetContacts FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 Поскольку атрибут **Client-Side-XML** имеет значение 1 (true) в шаблоне, хранимая процедура выполняется на сервере, а набор строк с двумя столбцами, возвращаемый сервером, преобразуется в XML на среднем уровне и возвращается клиенту. (здесь показан только фрагмент результата).  
  
```  
 <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact FirstName="Catherine" LastName="Abel" />  
</ROOT>  
```  
  
> [!NOTE]  
>  При использовании поставщика SQLXMLOLEDB или управляемых классов SQLXML можно при помощи свойства `ClientSideXml` задать форматирование XML на стороне клиента.  
  
### <a name="the-workload-is-more-balanced"></a>Рабочая нагрузка лучше сбалансирована  
 Поскольку клиент выполняет XML-форматирование, рабочая нагрузка будет балансироваться между сервером и клиентом, высвобождая серверные ресурсы для выполнения других задач.  
  
## <a name="supporting-client-side-xml-formatting"></a>Поддержка форматирования XML-кода на стороне клиента  
 Поддержку форматирования XML-кода на стороне клиента обеспечивают следующие компоненты SQLXML:  
  
-   SQLXMLOLEDB, поставщик  
  
-   управляемые классы SQLXML  
  
-   Улучшенная поддержка XML-шаблонов  
  
-   SqlXmlCommand. Клиентсидексмл, свойство  
  
     Установив это свойство управляемых классов SQLXML в значение true, можно задать форматирование на стороне клиента.  
  
## <a name="enhanced-xml-template-support"></a>Улучшенная поддержка XML-шаблонов  
 Начиная с версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] , XML-шаблон в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] был дополнен добавлением атрибута на **стороне клиента XML** . Если значение этого атрибута установлено в значение true, то XML-форматирование выполняется на стороне клиента. Обратите внимание, что этот атрибут шаблона идентичен свойству Клиентсидексмл, зависящему от поставщика SQLXMLOLEDB, в функциональных возможностях.  
  
> [!NOTE]  
>  Если вы выполняете XML-шаблон в приложении ADO, использующем поставщик SQLXMLOLEDB, и задаете атрибут **Client-Side-XML** в шаблоне и свойстве клиентсидексмл поставщика, приоритет получает значение, заданное в шаблоне.  
  
## <a name="see-also"></a>См. также:  
 [Архитектура форматирования XML на стороне клиента и на стороне сервера &#40;SQLXML 4,0&#41;](server-side-xml-formatting-sqlxml-4-0.md)   
 [ДЛЯ SQL Server &#40;XML&#41;](../../xml/for-xml-sql-server.md)   
 [Рекомендации по безопасности XML &#40;SQLXML 4,0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md)   
 [Поддержка типов данных XML в SQLXML 4,0](../xml-data-type-support-in-sqlxml-4-0.md)   
 [Управляемые классы SQLXML](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md)   
 [Клиентское и серверное форматирование XML &#40;SQLXML 4,0&#41;](client-side-vs-server-side-xml-formatting-sqlxml-4-0.md)   
 [Объект SqlXmlCommand &#40;управляемые классы SQLXML&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlcommand-object.md)   
 [Данные XML (SQL Server)](../../xml/xml-data-sql-server.md)  
  
  
