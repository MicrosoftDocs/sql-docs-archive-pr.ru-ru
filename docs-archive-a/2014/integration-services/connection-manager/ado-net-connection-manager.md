---
title: Диспетчер подключений ADO.NET | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], ADO.NET
- ADO.NET connection manager [Integration Services]
- connections [Integration Services], ADO.NET
ms.assetid: fc5daa2f-0159-4bda-9402-c87f1035a96f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9bdc25eeeae93fe0bd85deb55bfc86c55ab91ee5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664449"
---
# <a name="adonet-connection-manager"></a>Диспетчер соединений ADO.NET
  Диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] позволяет пакету обращаться к источникам данных с помощью поставщика .NET. Этот диспетчер соединений обычно используется для доступа к таким источникам данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , как, а также к источникам данных, предоставляемым с помощью OLE DB и XML в пользовательских задачах, написанных в управляемом коде с использованием языка, такого как C#.  
  
 При добавлении [!INCLUDE[vstecado](../../includes/vstecado-md.md)] к пакету диспетчера соединений служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создает диспетчер соединений, который разрешается как [!INCLUDE[vstecado](../../includes/vstecado-md.md)] соединение во время выполнения, устанавливает свойства диспетчера соединений и добавляет его в `Connections` коллекцию пакета.  
  
 Свойству `ConnectionManagerType` диспетчера соединений присваивается значение `ADO.NET`. Значение `ConnectionManagerType` уточняется: в него включается имя поставщика .NET, используемого диспетчером соединений.  
  
## <a name="adonet-connection-manager-troubleshooting"></a>Устранение неполадок, связанных с диспетчером соединений ADO.NET  
 В журнал можно записывать вызовы, сделанные диспетчером соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] к внешним источникам данных. Эта возможность протоколирования может быть использована для устранения неполадок соединений, которые устанавливаются диспетчером соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] с внешними источниками данных. Чтобы протоколировать вызовы, которые диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] совершает к внешним поставщикам данных, необходимо разрешить ведение журнала пакета и выбрать событие **Диагностика** на уровне пакета. Дополнительные сведения см. в разделе [Инструменты устранения неполадок при выполнении пакетов](../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
 При чтении данных диспетчером соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] данные определенных типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формируют результаты, показанные в следующей таблице.  
  
|Тип данных SQL Server|Результат|  
|--------------------------|------------|  
|`time`, `datetimeoffset`|Выполнение пакета завершается неудачей, если в пакете не используются параметризованные команды SQL. Чтобы применить параметризованные команды SQL, используйте в пакете задачу «Выполнение SQL». Дополнительные сведения см. в разделах [Задача "Выполнение SQL"](../control-flow/execute-sql-task.md) и [Параметры и коды возврата в задаче "Выполнение SQL"](../parameters-and-return-codes-in-the-execute-sql-task.md).|  
|`datetime2`|Диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] отбрасывает миллисекунды.|  
  
> [!NOTE]  
>  Дополнительные сведения о типах данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и их сопоставлении с типами данных [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] см. в разделе [Типы данных (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql) и [Типы данных службы Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="adonet-connection-manager-configuration"></a>Настройка диспетчера соединений ADO.NET  
 Диспетчер соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] можно настроить следующими способами:  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
-   Предоставьте специальную строку подключения, настроенную таким образом, чтобы удовлетворить требования выбранного поставщика .NET.  
  
-   В зависимости от поставщика предоставьте имя источника данных, к которому производится подключение.  
  
-   Предоставьте безопасные учетные данные, соответствующие выбранному поставщику.  
  
-   Обозначает, будет ли соединение, созданное из диспетчера соединений, сохранено во время выполнения.  
  
 Многие параметры конфигурации диспетчера соединений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] зависят от используемого им поставщика .NET.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , см. в одном из последующих разделов.  
  
-   [Настройка диспетчера подключений ADO.NET](../configure-ado-net-connection-manager.md)  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>См. также:  
 [Соединения в службах Integration Services (SSIS)](integration-services-ssis-connections.md)  
  
  
