---
title: Транзакции служб Integration Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], transactions
- transactions [Integration Services], about transactions in packages
- tasks [Integration Services], transactions
- transactions [Integration Services]
ms.assetid: 3c78bb26-ddce-4831-a5f8-09d4f4fd53cc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5c0ee195bbcb7b9779111add4c1f2349816d5441
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664372"
---
# <a name="integration-services-transactions"></a>Транзакции служб Integration Services
  Пакеты используют транзакции для связывания выполняемых в базе данных задачами операций в атомарные объекты, и, таким образом, сохраняют целостность данных. Все типы контейнеров служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (пакеты, контейнеры циклов по элементам и по каждому элементу, контейнеры последовательности, а также серверы задач, которые содержат каждую задачу) могут быть настроены для использования транзакций. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] предоставляют три параметра для настройки транзакций: **NotSupported**, **Supported**и **Required**.  
  
-   **Required** указывает, что контейнер запускает транзакцию, если она еще не запущена родительским контейнером. Если транзакция уже существует, контейнер с ней соединяется. Например, если пакет, не настроенный для поддержки транзакций, содержит контейнер последовательности, использующий параметр **Required** , то контейнер последовательности начнет свою собственную транзакцию. Если бы пакет был настроен для использования параметра **Required** , контейнер последовательности соединился бы с транзакцией пакета.  
  
-   **Supported** указывает, что контейнер не запускает транзакцию, но соединяется с любой транзакцией, запущенной родительским контейнером. Например, если пакет с четырьмя задачами «Выполнение SQL» запускает транзакцию и все четыре задачи используют параметр **Supported** , то обновления базы данных, выполненные задачами «Выполнение SQL», откатываются при ошибке обновления любой из этих задач. Если пакет не начинает транзакцию, четыре задачи «Выполнение SQL» не связаны транзакцией и в случае ошибки обновления базы данных одной из задач отменяются только обновления этой задачи.  
  
-   **NotSupported** указывает, что контейнер не начинает транзакцию и не соединяется с существующей транзакцией. Транзакция, запущенная родительским контейнером, не влияет на дочерние контейнеры, которые не были настроены на поддержку транзакций. Например, если пакет был настроен на запуск транзакции, а контейнер «цикл по элементам» в пакете использует параметр **NotSupported** , то в случае неудачи откат каких-либо задач в контейнере «цикл по элементам» невозможен.  
  
 Настройка транзакций происходит с помощью свойства контейнера TransactionOption. Установить это свойство можно в окне **Свойства** в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]или программным путем.  
  
> [!NOTE]  
>  Cвойствo `TransactionOption` влияет на то, применяется ли значение свойства `IsolationLevel`, запрашиваемого контейнером. Дополнительные сведения см. в описании `IsolationLevel` свойства в разделе [Установка свойств пакета](set-package-properties.md).  
  
### <a name="to-configure-a-package-to-use-transactions"></a>Настройка пакета на использование транзакций  
  
-   [Настройка пакета для использования транзакций](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
-   Запись в блоге, [Как использовать транзакции в службах SQL Server Integration Services SSIS](https://go.microsoft.com/fwlink/?LinkId=157783), на сайте www.mssqltips.com  
  
## <a name="see-also"></a>См. также:  
 [Унаследованные транзакции](../../2014/integration-services/inherited-transactions.md)   
 [Множественные транзакции](../../2014/integration-services/multiple-transactions.md)  
  
  
