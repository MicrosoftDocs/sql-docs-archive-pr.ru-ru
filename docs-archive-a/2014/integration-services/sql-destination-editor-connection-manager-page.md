---
title: Редактор назначения «SQL» (страница «Диспетчер соединений») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.connection.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 423e1654-54af-47c6-ab6f-98670534557d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f3a552968cb297de337e1f0c406b444d95dc5a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658308"
---
# <a name="sql-destination-editor-connection-manager-page"></a>Редактор назначения «SQL» (страница «Диспетчер соединений»)
  Страница **Диспетчер соединений** диалогового окна **Редактор назначения «SQL»** используется для задания сведений об источнике данных и для предварительного просмотра результатов. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Назначение загружает данные в таблицы или представления в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] базе данных.  
  
 Дополнительные сведения о назначении «SQL Server» см. в разделе [SQL Server Destination](data-flow/sql-server-destination.md).  
  
## <a name="options"></a>Параметры  
 **Диспетчер соединений OLE DB**  
 Выберите существующий диспетчер подключений из списка или создайте новое соединение, выбрав пункт **Создать**.  
  
 **Создать**  
 Создайте новое соединение с помощью диалогового окна **Настройка диспетчера соединений OLE DB** .  
  
 **Использовать таблицу или представление**  
 Выберите существующую таблицу или представление из списка или создайте новое соединение, нажав кнопку **Создать**.  
  
 **Создать**  
 Создайте новую таблицу с помощью диалогового окна **Создание таблицы** .  
  
> [!NOTE]  
>  При нажатии кнопки **Создать**службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] по умолчанию формируют инструкцию CREATE TABLE на основе подключенного источника данных. Эта инструкция CREATE TABLE не включает атрибут FILESTREAM, даже если исходная таблица содержит столбец, для которого объявлен атрибут FILESTREAM. Чтобы запустить компонент служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] с атрибутом FILESTREAM, сначала следует создать хранилище FILESTREAM в целевой базе данных. Затем добавьте атрибут FILESTREAM к инструкции CREATE TABLE в диалоговом окне **Создание таблицы** . Дополнительные сведения см. в разделе [Данные большого двоичного объекта (SQL Server)](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 **Предварительный просмотр**  
 Просмотрите предварительные результаты, используя диалоговое окно **Предварительный просмотр результатов запроса** . В окне «Предварительный просмотр» может отображаться до 200 строк.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор назначения "SQL &#40;страниц сопоставления"&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md)   
 [Редактор назначения "SQL" &#40;страница "Дополнительно"&#41;](../../2014/integration-services/sql-destination-editor-advanced-page.md)   
 [Выполнение массовой загрузки данных с помощью назначения «SQL Server»](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
