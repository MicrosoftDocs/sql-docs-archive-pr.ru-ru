---
title: Роли безопасности (Analysis Services-многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], roles
- Analysis Services objects, roles
- security [Analysis Services], roles
- roles [Analysis Services], about roles
- server roles [Analysis Services]
- database roles [Analysis Services]
- roles [Analysis Services]
- storing data [Analysis Services], roles
- access rights [Analysis Services], roles
ms.assetid: 5b7e9cef-ff68-4d8e-99bc-e0094ced1baa
author: minewiskan
ms.author: owend
ms.openlocfilehash: e62abaab5a8f74dfee7d51962f2fb243dc6eb20a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736977"
---
# <a name="security-roles--analysis-services---multidimensional-data"></a>Роли безопасности (службы Analysis Services — многомерные данные)
  Роли используются в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] для управления безопасностью [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] объектов и данных. Роли связывают идентификаторы безопасности (SID) пользователей и групп Microsoft Windows, имеющих определенные права доступа и разрешения, определенные для объектов, управляемых экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. В службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]имеет два типа ролей:  
  
-   Роль сервера — фиксированная роль, предоставляющая права администратора для доступа к экземпляру служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
-   Роли базы данных — роли, определенные администраторами для контроля доступа к объектам и данным пользователям, которые не являются администраторами.  
  
 Безопасность в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] системе безопасности управляется с помощью ролей и разрешений. Роли — это группы пользователей. Пользователи, называемые также членами, могут быть добавлены или удалены из состава ролей. Разрешения для объектов регламентируются с помощью ролей, и все члены, относящиеся к некоторой роли, могут использовать объекты, на которые в этой роли имеются разрешения. Все члены одной и той же роли имеют одинаковые разрешения на объекты. Разрешения связаны с конкретными объектами. Для каждого объекта предусмотрена коллекция разрешений, в которой указаны предоставленные разрешения на этот объект, причем на каждый объект могут быть предоставлены разные наборы разрешений. Для каждого разрешения из коллекции разрешений объекта назначена отдельная роль.  
  
## <a name="role-and-role-member-objects"></a>Объекты ролей и членов ролей  
 Роль — это объект, который предназначен для использования в качестве контейнера для коллекции пользователей (членов). В определении роли регламентируется членство пользователей в службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Таким образом, разрешения присваиваются с учетом роли, поэтому пользователь должен стать членом роли, прежде чем получить доступ к какому-либо объекту.  
  
 Объект <xref:Microsoft.AnalysisServices.Role> состоит из значений параметров Name, Id и Members. Значение Members — это коллекция строк. Каждый член роли содержит имя пользователя в форме «домен\имя_пользователя». Значение Name — это строка, которая содержит имя роли. Значение ID — это строка, которая содержит уникальный идентификатор роли.  
  
### <a name="server-role"></a>Роль сервера  
 Роль сервера служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] определяет административный доступ пользователей и групп Windows к экземпляру служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Члены этой роли имеют доступ ко всем базам данных и объектам служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]и могут выполнять следующие задачи:  
  
-   Выполнение административных функций на уровне сервера в среде SQL Server Management Studio или [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], включая создание баз данных и настройку свойств на уровне сервера.  
  
-   Выполнение административных функций программным методом с помощью объектов AMO.  
  
-   Обслуживание ролей базы данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
-   Запуск трассировок (отличных от обработки событий, которые могут выполняться ролью базы данных с правом доступа Process).  
  
 Каждый экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] имеет роль сервера, которая определяет пользователей с функциями администрирования этого экземпляра. Имя и идентификатор этой роли — «Администраторы»; в отличие от ролей базы данных, роль сервера удалить нельзя, в нее также нельзя добавлять разрешения или удалять их. Другими словами, пользователь является или не является администратором экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]в зависимости от того, включен он или нет в роль сервера этого экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
### <a name="database-roles"></a>Роли базы данных  
 Роль базы данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] определяет доступ пользователей к объектам и данным в базе данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . Роль базы данных создается как отдельный объект в базе данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и применяется только к той базе данных, в которой эта роль создана. Пользователи и группы Windows включаются в эту роль администратором. Он же определяет разрешения этой роли.  
  
 Разрешения роли, помимо доступа к объектам и данным в базе данных, позволяют членам роли получить доступ и права администрирования базы данных. Каждое разрешение имеет одно или несколько связанных прав доступа, которые, в свою очередь, позволяют точно контролировать доступ к отдельным объектам в базе данных.  
  
## <a name="permission-objects"></a>Объекты разрешений  
 Разрешения связаны с объектом (куб, измерение и др.) для конкретной роли. Разрешения указывают на то, какие операции может выполнять над этим объектом член этой роли.  
  
 Класс <xref:Microsoft.AnalysisServices.Permission> представляет собой абстрактный класс. Поэтому необходимо использовать производные классы для определения разрешений на соответствующие объекты. Для каждого объекта определяется производный класс разрешения.  
  
|Объект|Класс|  
|------------|-----------|  
|<xref:Microsoft.AnalysisServices.Database>|<xref:Microsoft.AnalysisServices.DatabasePermission>|  
|<xref:Microsoft.AnalysisServices.DataSource>|<xref:Microsoft.AnalysisServices.DataSourcePermission>|  
|<xref:Microsoft.AnalysisServices.Dimension>|<xref:Microsoft.AnalysisServices.DimensionPermission>|  
|<xref:Microsoft.AnalysisServices.Cube>|<xref:Microsoft.AnalysisServices.CubePermission>|  
|<xref:Microsoft.AnalysisServices.MiningStructure>|<xref:Microsoft.AnalysisServices.MiningStructurePermission>|  
|<xref:Microsoft.AnalysisServices.MiningModel>|<xref:Microsoft.AnalysisServices.MiningModelPermission>|  
  
 Возможные действия, допускаемые в соответствии с разрешениями, показаны в следующем списке.  
  
|Действие|Значения|Объяснение|  
|------------|------------|-----------------|  
|Процесс|{`true`, `false`}<br /><br /> Default=`false`|Если дано значение `true`, то члены роли могут обрабатывать и сам объект, и любые содержащиеся в нем объекты.<br /><br /> Разрешения на обработку не применяются к моделям интеллектуального анализа данных. Разрешения <xref:Microsoft.AnalysisServices.MiningModel> всегда наследуются от <xref:Microsoft.AnalysisServices.MiningStructure>.|  
|ReadDefinition|{`None`, `Basic`, `Allowed`}<br /><br /> Default=`None`|Определяет, могут ли члены читать определение данных (в коде ASSL), связанное с объектом.<br /><br /> Если дано значение `Allowed`, то члены могут читать код ASSL, связанный с объектом.<br /><br /> Разрешения `Basic` и `Allowed` наследуются объектами, которые содержатся в данном объекте. `Allowed` переопределяет `Basic` и `None`.<br /><br /> Разрешение `Allowed` необходимо для выполнения операции DISCOVER_XML_METADATA над объектом. Разрешение `Basic` необходимо для создания связанных объектов и локальных кубов.|  
|Чтение|{`None`, `Allowed`}<br /><br /> Default=`None` (за исключением DimensionPermission, где default=`Allowed`)|Указывает, имеют ли члены доступ для чтения к наборам строк схемы и содержимому данных.<br /><br /> `Allowed`предоставляет доступ для чтения к базе данных, которая позволяет обнаружить базу данных.<br /><br /> Значение `Allowed` применительно к кубу предоставляет доступ для чтения в наборах строк схемы и доступ к содержимому куба (при условии, что не введены в действие ограничения со стороны <xref:Microsoft.AnalysisServices.CellPermission> и <xref:Microsoft.AnalysisServices.CubeDimensionPermission>).<br /><br /> Значение `Allowed` применительно к измерению предоставляет разрешение на чтение для всех атрибутов в этом измерении (при условии, что не введены в действие ограничения со стороны <xref:Microsoft.AnalysisServices.CubeDimensionPermission>). Разрешение на чтение используется для статического наследования только для <xref:Microsoft.AnalysisServices.CubeDimensionPermission>. `None` применительно к измерению скрывает это измерение и предоставляет доступ к члену по умолчанию только для статистически обрабатываемых атрибутов. Если измерение содержит статистически необрабатываемый атрибут, возникает ошибка.<br /><br /> Значение `Allowed` применительно к разрешениям <xref:Microsoft.AnalysisServices.MiningModelPermission> предоставляет возможность просматривать объекты в наборах строк схемы и выполнять соединения в целях выработки прогноза.<br /><br /> **Нотеалловед** требуется для чтения или записи в любой объект базы данных.|  
|запись|{`None`, `Allowed`}<br /><br /> Default=`None`|Указывает, имеют ли члены доступ для записи к данным родительского объекта.<br /><br /> Права доступа относятся к подклассам <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.Cube> и <xref:Microsoft.AnalysisServices.MiningModel>. Они не применяются к подклассам базы данных <xref:Microsoft.AnalysisServices.MiningStructure>, которые создают сообщения ошибок проверки.<br /><br /> Значение `Allowed` применительно к <xref:Microsoft.AnalysisServices.Dimension> предоставляет разрешение на запись для всех атрибутов измерения.<br /><br /> Значение `Allowed` применительно к <xref:Microsoft.AnalysisServices.Cube> предоставляет разрешение на запись в ячейки куба для секций, определенных как Type=writeback.<br /><br /> Значение `Allowed` применительно к <xref:Microsoft.AnalysisServices.MiningModel> предоставляет разрешение на изменение содержимого модели.<br /><br /> Значение `Allowed` применительно к <xref:Microsoft.AnalysisServices.MiningStructure> не имеет конкретного смысла в службах [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. **Примечание.**  Невозможно задать параметр Write, `Allowed` Если для Read также задано значение`Allowed`|  
|Примечание по администрированию **:** только в разрешениях базы данных|{`true`, `false`}<br /><br /> Default=`false`|Указывает, могут ли члены выполнять административные функции по отношению к базе данных.<br /><br /> Значение `true` предоставляет членам роли разрешение для доступа ко всем объектам в базе данных.<br /><br /> Член роли может иметь разрешение на администрирование применительно к какой-то конкретной базе данных, но не к другим.|  
  
## <a name="see-also"></a>См. также:  
 [Предоставление доступа к объектам и операциям (службы Analysis Services)](../authorizing-access-to-objects-and-operations-analysis-services.md)  
  
  
