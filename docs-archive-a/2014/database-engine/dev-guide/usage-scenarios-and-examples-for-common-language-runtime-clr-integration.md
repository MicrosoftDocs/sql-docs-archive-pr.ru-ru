---
title: Сценарии использования и примеры интеграции со средой CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- scenarios [CLR integration]
- common language runtime [SQL Server], samples
- examples [CLR integration]
- sample applications [CLR integration]
- database objects [CLR integration], samples
- managed code [SQL Server], samples
ms.assetid: 33aac25f-abb4-4f29-af88-4a0dacd80ae7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 30a54064d398ec6db09a9ccd54eed9411a7f905a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732998"
---
# <a name="usage-scenarios-and-examples-for-common-language-runtime-clr-integration"></a>Сценарии использования и примеры интеграции со средой CLR
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] включает примеры приложений, образцы пакетов и многочисленные образцы кода, которые можно использовать для изучения возможностей программирования в условиях интеграции со средой CLR.  
  
 Для завершения проектов Visual Studio, реализующих эти примеры и дополнительные материалы, посетите [Microsoft SQL Server проекты сообщества & примеров на сайте CodePlex](https://go.microsoft.com/fwlink/?LinkID=193935).  
  
|name|Описание|  
|----------|-----------------|  
|[доступ к машинному коду из определяемой пользователем функции CLR](../../../2014/database-engine/dev-guide/accessing-native-code-from-a-clr-udf.md)|Показывает способ вызова в базе данных функции в собственном (неуправляемом) коде C++ из определяемых пользователем функции в сборке.|  
|[Образец параметра массива](../../../2014/database-engine/dev-guide/array-parameter-sample.md)|Демонстрирует создание, обновление или удаление набора строк в базе данных путем передачи массива сведений от клиента хранимой процедуре интеграции со средой CLR на сервере. Делается это с помощью определяемого пользователем типа данных.|  
|[Пример определяемого пользователем типа даты и времени с учетом календаря](../../../2014/database-engine/dev-guide/calendar-aware-date-and-time-udt-sample.md)|Определяет два определяемых пользователем типа данных, обеспечивающих обработку даты и времени с учетом календаря.|  
|[Образец транзакции среды CLR](../../../2014/database-engine/dev-guide/clr-transactions-sample.md)|Демонстрирует управление транзакциями с использованием управляемых интерфейсов API, расположенных в пространстве имен System.Transactions.|  
|[Создание контакта с использованием среды CLR и XML-кода](../../../2014/database-engine/dev-guide/contact-creation-using-clr-and-xml.md)|Образец Contact для SQL Server содержит ряд полезных программ, образующих дополнительный функциональный слой поверх базового образца базы данных AdventureWorks2012. Первая программа создает контактные записи для разных групп людей, включенных в базу данных AdventureWorks2012. Контактные данные описываются в формате XML и передаются хранимой процедуре на языке C# или VB, которая создает XML-код и помещает его в нужные таблицы базы данных.|  
|[Тип денежной единицы и функция конвертации](../../../2014/database-engine/dev-guide/currency-type-and-conversion-function.md)|Описывает на языке C# определяемый пользователем тип данных Currency.|  
|[Обработка больших объектов в среде CLR](../../../2014/database-engine/dev-guide/handling-large-objects-using-clr.md)|Демонстрирует передачу больших двоичных объектов между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и файловой системой, которая доступна серверу, с использованием хранимых процедур CLR.|  
|[Образец Hello World Ready](../../../2014/database-engine/dev-guide/hello-world-ready-sample.md)|Демонстрирует базовые операции для создания, развертывания и проверки простой общедоступной хранимой процедуры на основе использования интеграции со средой CLR.|  
|[Пример кода Hello World](../../../2014/database-engine/dev-guide/hello-world-sample.md)|Демонстрирует базовые операции для создания, развертывания и проверки простой хранимой процедуры, основанной на использовании интеграции со средой CLR.|  
|[Образец внутрипроцессного доступа к данным](../../../2014/database-engine/dev-guide/in-process-data-access-sample.md)|Содержит несколько простых функций, демонстрирующих различные характеристики внутрипроцессного доступа к данным для среды CLR.|  
|[Образец результирующего набора](../../../2014/database-engine/dev-guide/result-set-sample.md)|Демонстрирует выполнение команд во время чтения результатов запроса без открытия нового соединения и считывания всех результатов в память.|  
|[Образец отправки DataSet](../../../2014/database-engine/dev-guide/send-dataset-sample.md)|Демонстрирует возвращение клиенту в качестве результирующего набора DataSet на основе ADO.NET в рамках хранимой процедуры CLR на стороне сервера.|  
|[Пример функций программы работы со строками](../../../2014/database-engine/dev-guide/string-utility-functions-sample.md)|Содержит потоковую возвращающую функцию с табличным значением, написанную на языках Visual C# и Visual Basic, которая разбивает строку с разделителями-запятыми в таблицу, содержащую один столбец.|  
|[Образец операций над строками с учетом дополнений](../../../2014/database-engine/dev-guide/supplementary-aware-string-manipulation-sample.md)|Показывает реализацию пяти строковых функций [!INCLUDE[tsql](../../includes/tsql-md.md)] с учетом дополнений, которые могут управлять как строками в Юникоде, так и суррогатными строками.|  
|[Программы определяемых пользователем типов](../../../2014/database-engine/dev-guide/udt-utilities.md)|Содержит несколько функций для работы с определяемыми пользователем типами данных.|  
|[Очистка неиспользуемой сборки](../../../2014/database-engine/dev-guide/unused-assembly-cleanup.md)|Содержит хранимую процедуру .NET, которая удаляет неиспользуемые сборки из текущей базы данных, выполняя запрос к каталогам метаданных.|  
|[Определяемый пользователем тип](../../../2014/database-engine/dev-guide/user-defined-type.md)|Показывает создание и использование простого, определяемого пользователем типа данных как из [!INCLUDE[tsql](../../includes/tsql-md.md)], так и из клиентского приложения, использующего пространство имен System.Data.SqlClient.|  
|[Символьный определяемый пользователем тип данных UTF8 &#40;&#41;UDT](../../../2014/database-engine/dev-guide/utf8-string-user-defined-data-type-udt.md)|Демонстрирует реализацию определяемого пользователем типа данных, который расширяет систему типов базы данных для хранения значений в кодировке UTF8.|  
  
  
