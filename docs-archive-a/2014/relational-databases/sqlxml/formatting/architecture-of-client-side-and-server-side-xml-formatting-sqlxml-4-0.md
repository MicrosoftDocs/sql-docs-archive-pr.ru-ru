---
title: Архитектура форматирования XML на стороне клиента и на стороне сервера (SQLXML 4,0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], XML formatting architecture
- SQLOLEDB provider
- client-side XML formatting
- data providers [SQLXML], XML formatting architecture
- SQLNCLI, XML
- server-side XML formatting
- SQL Server Native Client, XML
- SQLXMLOLEDB Provider, XML formatting architecture
ms.assetid: 52440d9e-89fd-4c15-a008-a1ea99f41387
author: rothja
ms.author: jroth
ms.openlocfilehash: ae1a9c60a7a7966f4eff2a08b4557487f5aec58c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665934"
---
# <a name="architecture-of-client-side-and-server-side-xml-formatting-sqlxml-40"></a>Архитектура форматирования XML на стороне клиента и сервера (SQLXML 4.0)
  На следующей иллюстрации показана архитектура форматирования XML на стороне сервера.  
  
 ![Архитектура форматирования XML-кода на стороне сервера.](../../../database-engine/dev-guide/media/serversidexml.gif "Архитектура форматирования XML-кода на стороне сервера.")  
  
 В этом примере команда, указанная на стороне клиента, передается на сервер. Сервер создает XML-документ и возвращает его клиенту. В этом случае сервер имеет экземпляр [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Чтобы форматировать XML-документ на стороне сервера, можно применять либо поставщик SQLXMLOLEDB, либо SQLOLEDB.  Поставщик SQLXMLOLEDB использует библиотеку Sqlxml4.dll, входящую в SQLXML 4.0. Если используется поставщик SQLOLEDB, по умолчанию получаем функциональность SQLXML, предоставляемую библиотекой Sqlxmlx.dll, входящей в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, или компоненты доступа к данным MDAC 2.6 или более поздней версии. Чтобы использовать Sqlxml4.dll с SQLOLEDB, необходимо задать для свойства версия SQLXML значение SQLXML. 4.0 в объекте подключения SQLOLEDB. В любом случае сервер создает XML-документ и передает его клиенту.  
  
> [!NOTE]  
>  Запросы XPath и диаграммы обновления анализируются на клиенте. Чтобы вернуть шаблон XPath или диаграмму обновления в SQLXML 4.0, используйте библиотеку Sqlxml4.dll.  
  
 На следующей иллюстрации показана архитектура форматирования XML на стороне клиента.  
  
 ![Архитектура форматирования XML-кода на стороне клиента.](../../../database-engine/dev-guide/media/clientsidexml.gif "Архитектура форматирования XML-кода на стороне клиента.")  
  
 В этом примере клиент использует поставщик SQLXMLOLEDB. В строке подключения для свойства поставщика данных необходимо задать значение SQLOLEDB. (Это единственное значение, допустимое в SQLXML 4,0.) Команда, выполняемая на клиенте, отправляется на сервер. Созданный на сервере набор строк отправляется клиенту. Форматирование XML-документа на основе набора строк выполняется на стороне клиента.  
  
 В SQLXML 4.0 в качестве поставщика данных может использоваться собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (SQLNCLI11) или поставщик SQLOLEDB. Теоретически можно получить доступ к любому источнику данных. Если запрос возвращает единственный набор строк, преобразование XML может применяться на клиенте.  
  
  
