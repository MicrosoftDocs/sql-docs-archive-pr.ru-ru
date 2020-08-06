---
title: Диспетчер подключения кэша | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Cache connection manager
ms.assetid: bdc92038-3720-4795-8a5c-79b963f2c952
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b8a7cc8bbe9e93c385fca6257e0be2e79bd3148a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664434"
---
# <a name="cache-connection-manager"></a>диспетчер соединений с кэшем
  Диспетчер соединений с кэшем считывает данные из преобразования кэша или из файла кэша (CAW) и может сохранить эти данные в файле кэша. Данные всегда будут храниться в памяти, вне зависимости от того, был ли настроен диспетчер соединений с кэшем для использования файла кэша.  
  
 Преобразование «Преобразование кэша» записывает данные из подключенного источника данных в потоке данных в диспетчер соединений с кэшем. Преобразование «Уточняющий запрос» в пакете выполняет уточняющие запросы по данным.  
  
> [!NOTE]  
>  Диспетчер соединений с кэшем не поддерживает типы данных больших двоичных объектов: DT_TEXT, DT_NTEXT и DT_IMAGE. Если ссылочный набор данных содержит данные типа BLOB, то при попытке выполнения пакета компонент завершится сбоем. **Редактор диспетчера соединений с кэшем** можно использовать для изменения типов данных столбцов. Дополнительные сведения см. в разделе [Cache Connection Manager Editor](../cache-connection-manager-editor.md).  
  
> [!NOTE]  
>  Уровень защиты пакета не применяется к кэшируемому файлу. Если кэшируемый файл содержит важные данные, используйте список управления доступом (ACL), чтобы запретить доступ к расположению или папке, в которой хранится файл. Доступ следует разрешать только определенным учетным записям. Дополнительные сведения см. в разделе [Доступ к файлам, используемым пакетами](../access-to-files-used-by-packages.md).  
  
## <a name="configuration-of-the-cache-connection-manager"></a>Настройка диспетчера соединений с кэшем  
 Диспетчер соединений с кэшем можно настроить следующими способами.  
  
-   Указать, следует ли использовать файл кэша.  
  
     Если выполнена настройка диспетчера соединений с кэшем для использования файла кэша, то диспетчер соединений выполняет одно из следующих действий.  
  
    -   Сохранить данные в файле, если преобразование «Конвертация данных кэш» настроено на запись данных из источника данных в потоке данных в диспетчер соединений с кэшем.  
  
    -   Считать данные из файла кэша.  
  
     Дополнительные сведения см. в разделе [Cache Transform](../data-flow/transformations/cache-transform.md).  
  
-   Изменить метаданные столбцов, хранящихся в кэше.  
  
-   Обновить имя файла кэша во время выполнения с помощью выражения для установки свойства ConnectionString. Дополнительные сведения см. в разделе [Использование выражений свойств в пакетах](../expressions/use-property-expressions-in-packages.md).  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , см. в разделе [Редактор диспетчера соединений с кэшем](../cache-connection-manager-editor.md).  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Реализация преобразования "Уточняющий запрос" в режиме полного кэширования с помощью преобразования диспетчера соединений с кэшем](lookup-transformation-full-cache-mode-ole-db-connection-manager.md)  
  
  