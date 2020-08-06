---
title: Компоненты потока ODBC | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cf751f1e-2348-4a77-904c-bd92c0d7d0ae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c5c2ed8f5e77d8d9e96adb86bde6cf11d4208d26
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657199"
---
# <a name="odbc-flow-components"></a><span data-ttu-id="f8a28-102">Компоненты потока ODBC</span><span class="sxs-lookup"><span data-stu-id="f8a28-102">ODBC Flow Components</span></span>
  <span data-ttu-id="f8a28-103">Этот раздел содержит описание основных понятий, необходимых для создания потока данных ODBC с использованием [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8a28-103">This topic describes the concepts necessary for creating an ODBC data flow using [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]</span></span>  
  
 <span data-ttu-id="f8a28-104">Соединитель для ODBC компании Attunity для [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] позволяет разработчикам служб SSIS легко создавать пакеты, которые загружают и выгружают данные из баз данных с поддержкой ODBC.</span><span class="sxs-lookup"><span data-stu-id="f8a28-104">The Connector for Open Database Connectivity (ODBC) by Attunity for [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] helps SSIS developers easily create packages that load and unload data from ODBC-supported databases.</span></span>  
  
 <span data-ttu-id="f8a28-105">Соединитель ODBC предназначен для достижения оптимальной производительности при загрузке или выгрузке данных из базы данных с поддержкой ODBC в контексте [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8a28-105">The ODBC Connector is designed to achieve optimal performance when loading data into or unloading data from an ODBC-supported database in the context of [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].</span></span>  
  
## <a name="benefits"></a><span data-ttu-id="f8a28-106">Преимущества</span><span class="sxs-lookup"><span data-stu-id="f8a28-106">Benefits</span></span>  
 <span data-ttu-id="f8a28-107">Источник и назначение ODBC для [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] обеспечивают конкурентное превосходство для служб SSIS в проектах, связанных с загрузкой или выгрузкой данных из баз данных с поддержкой ODBC.</span><span class="sxs-lookup"><span data-stu-id="f8a28-107">The ODBC source and ODBC destination for [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] provides a competitive edge for SSIS in projects dealing with loading data into or unloading data from ODBC-supported databases.</span></span>  
  
 <span data-ttu-id="f8a28-108">Источник и назначение ODBC обеспечивают высокопроизводительную интеграцию данных с базами данных с поддержкой ODBC.</span><span class="sxs-lookup"><span data-stu-id="f8a28-108">Both the ODBC source and ODBC destination enable high performance data integration with ODBC-enabled databases.</span></span> <span data-ttu-id="f8a28-109">Оба компонента могут быть настроены для работы с привязками массива построчных параметров для высокопроизводительных поставщиков ODBC, которые поддерживают этот режим привязки, и привязками однострочных параметров для низкопроизводительных поставщиков ODBC.</span><span class="sxs-lookup"><span data-stu-id="f8a28-109">Both components can be configured to work with row-wise parameter array bindings for high-functioning ODBC providers that support this mode of binding and single-row parameter bindings for low-functioning ODBC providers.</span></span>  
  
## <a name="getting-started-with-the-odbc-source-and-destination"></a><span data-ttu-id="f8a28-110">Приступая к работе с источником и назначением ODBC</span><span class="sxs-lookup"><span data-stu-id="f8a28-110">Getting Started with the ODBC Source and Destination</span></span>  
 <span data-ttu-id="f8a28-111">Прежде чем появится возможность настройки пакетов, в которых используется [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], необходимо обеспечить соблюдение следующих требований.</span><span class="sxs-lookup"><span data-stu-id="f8a28-111">Before you can set up packages that use [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], you must make sure that the following are available.</span></span>  
  
-   [<span data-ttu-id="f8a28-112">Источник «ODBC»</span><span class="sxs-lookup"><span data-stu-id="f8a28-112">ODBC Source</span></span>](odbc-source.md)  
  
-   [<span data-ttu-id="f8a28-113">Назначение «ODBC»</span><span class="sxs-lookup"><span data-stu-id="f8a28-113">ODBC Destination</span></span>](odbc-destination.md)  
  
 <span data-ttu-id="f8a28-114">Источник и назначение ODBC предоставляют простой способ выгрузки и загрузки данных, а также передачи данных из базы данных-источника с поддержкой ODBC в целевую базу данных с поддержкой ODBC.</span><span class="sxs-lookup"><span data-stu-id="f8a28-114">The ODBC source and ODBC destination provide an easy way to unload and load data and transfer data from an ODBC-supported source database to an ODBC-supported destination database.</span></span>  
  
 <span data-ttu-id="f8a28-115">Чтобы использовать источник или назначение для загрузки или выгрузки данных, откройте новые проект [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8a28-115">To use the source or destination to load or unload data, open a new [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] Project in the [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="f8a28-116">Затем перетащите источник или назначение в область конструктора [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8a28-116">Then drag the source or destination onto the design surface of the [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="f8a28-117">Компонент источника ODBC считывает данные из базы данных-источника с поддержкой ODBC.</span><span class="sxs-lookup"><span data-stu-id="f8a28-117">The ODBC source component reads data from the source ODBC-supported database.</span></span>  
  
 <span data-ttu-id="f8a28-118">Предусмотрена возможность подключить источник ODBC к любому назначению или преобразовать компонент, поддерживаемый службами SSIS.</span><span class="sxs-lookup"><span data-stu-id="f8a28-118">You can connect the ODBC source to any destination or transform component supported by SSIS.</span></span>  
  
 <span data-ttu-id="f8a28-119">**См. также**</span><span class="sxs-lookup"><span data-stu-id="f8a28-119">**See also:**</span></span>  
  
 <span data-ttu-id="f8a28-120">ODBC-источник</span><span class="sxs-lookup"><span data-stu-id="f8a28-120">ODBC Source</span></span>  
  
 <span data-ttu-id="f8a28-121">Редактор источника «ODBC» (страница «Диспетчер соединений»)</span><span class="sxs-lookup"><span data-stu-id="f8a28-121">ODBC Source Editor (Connection Manager Page)</span></span>  
  
 <span data-ttu-id="f8a28-122">Редактор источника «ODBC» (страница «Вывод ошибок»)</span><span class="sxs-lookup"><span data-stu-id="f8a28-122">ODBC Source Editor (Error Output Page)</span></span>  
  
-   <span data-ttu-id="f8a28-123">Назначение ODBC загружает данные в базу данных с поддержкой ODBC.</span><span class="sxs-lookup"><span data-stu-id="f8a28-123">The ODBC destination loads data into an ODBC-supported database.</span></span> <span data-ttu-id="f8a28-124">Назначение подключается к любому компоненту источника или преобразования, поддерживаемому службами SSIS.</span><span class="sxs-lookup"><span data-stu-id="f8a28-124">You connect the destination to any source or transform component supported by SSIS.</span></span>  
  
 <span data-ttu-id="f8a28-125">**См. также**</span><span class="sxs-lookup"><span data-stu-id="f8a28-125">**See also:**</span></span>  
  
 <span data-ttu-id="f8a28-126">Назначение ODBC</span><span class="sxs-lookup"><span data-stu-id="f8a28-126">ODBC Destination</span></span>  
  
 <span data-ttu-id="f8a28-127">Редактор назначения «ODBC» (страница «Диспетчер соединений»)</span><span class="sxs-lookup"><span data-stu-id="f8a28-127">ODBC Destination Editor (Connection Manager Page)</span></span>  
  
 <span data-ttu-id="f8a28-128">Редактор назначения «ODBC» (страница «Вывод ошибок»)</span><span class="sxs-lookup"><span data-stu-id="f8a28-128">ODBC Destination Editor (Error Output Page)</span></span>  
  
## <a name="operating-scenarios"></a><span data-ttu-id="f8a28-129">Сценарии работы</span><span class="sxs-lookup"><span data-stu-id="f8a28-129">Operating Scenarios</span></span>  
 <span data-ttu-id="f8a28-130">В этом разделе рассматриваются некоторые из основных способов использования компонентов источника и назначения ODBC.</span><span class="sxs-lookup"><span data-stu-id="f8a28-130">This section describes some of the main uses for the ODBC source and destination components.</span></span>  
  
### <a name="bulk-copy-data-from-sql-server-tables-to-any-odbc-supported-database-table"></a><span data-ttu-id="f8a28-131">Массовое копирование данных из таблиц SQL Server в таблицу любой базы данных с поддержкой ODBC</span><span class="sxs-lookup"><span data-stu-id="f8a28-131">Bulk Copy Data from SQL Server tables to any ODBC-Supported database table</span></span>  
 <span data-ttu-id="f8a28-132">Эти компоненты можно использовать для массового копирования данных из одной или нескольких таблиц [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в одну таблицу базы данных с поддержкой ODBC.</span><span class="sxs-lookup"><span data-stu-id="f8a28-132">You can use the components to bulk copy data from one or more [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables to a single ODBC-supported database table.</span></span>  
  
 <span data-ttu-id="f8a28-133">В следующем примере показано, как создать задачу «Поток данных служб SSIS», которая извлекает данные из таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и загружает их в таблицу DB2.</span><span class="sxs-lookup"><span data-stu-id="f8a28-133">The following example shows how to create an SSIS Data Flow Task that extracts data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table and loads it into a DB2 table.</span></span>  
  
-   <span data-ttu-id="f8a28-134">Создайте проект [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8a28-134">Create an [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] Project in the [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="f8a28-135">Создайте диспетчер соединений OLE DB, который подключается к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , содержащей данные, предназначенные для копирования.</span><span class="sxs-lookup"><span data-stu-id="f8a28-135">Create an OLE DB connection manager that connects to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the data you want to copy.</span></span>  
  
-   <span data-ttu-id="f8a28-136">Создайте диспетчер соединений ODBC, который использует локально установленный драйвер ODBC для DB2 с DSN, указывающий на локальную или удаленную базу данных DB2.</span><span class="sxs-lookup"><span data-stu-id="f8a28-136">Create an ODBC connection manager that uses a locally installed DB2 ODBC driver with a DSN pointing to a local or remote DB2 database.</span></span> <span data-ttu-id="f8a28-137">Эта та база данных, в которую загружены данные из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f8a28-137">This database is where the data from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database is loaded.</span></span>  
  
-   <span data-ttu-id="f8a28-138">Перетащите источник OLE DB в область конструктора, затем настройте источник для получения данных из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и таблицы с данными, которые необходимо извлечь.</span><span class="sxs-lookup"><span data-stu-id="f8a28-138">Drag an OLE DB source to the design surface, then configure the source to get the data from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database and table with the data you are going to extract.</span></span> <span data-ttu-id="f8a28-139">Используйте созданный перед этим диспетчер соединений OLE DB.</span><span class="sxs-lookup"><span data-stu-id="f8a28-139">Use the OLE DB connection manager you created previously.</span></span>  
  
-   <span data-ttu-id="f8a28-140">Перетащите назначение ODBC в область конструктора, подключите вывод источника к назначению ODBC, затем настройте назначение, чтобы загрузить данные в таблицу DB2 с данными, извлеченными из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f8a28-140">Drag an ODBC destination to the design surface, connect the source output to the ODBC destination, then configure the destination to load the data into the DB2 table with the data you extract from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="f8a28-141">Используйте созданный перед этим диспетчер соединений ODBC.</span><span class="sxs-lookup"><span data-stu-id="f8a28-141">Use the ODBC connection manager you created previously.</span></span>  
  
### <a name="bulk-copy-data-from-odbc-supported-database-tables-to-any-sql-server-table"></a><span data-ttu-id="f8a28-142">Массовое копирование данных из таблиц базы данных с поддержкой ODBC в любую таблицу SQL Server</span><span class="sxs-lookup"><span data-stu-id="f8a28-142">Bulk Copy Data from ODBC-supported database tables to any SQL Server table</span></span>  
 <span data-ttu-id="f8a28-143">Компоненты можно использовать для массового копирования данных из одной или нескольких таблиц базы данных с поддержкой ODBC в одну таблицу базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f8a28-143">You can use the components to bulk copy data from one or more ODBC-supported database tables to a single [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database table.</span></span>  
  
 <span data-ttu-id="f8a28-144">В следующем примере показано, как создать задачу «Поток данных SSIS», которая извлекает данные из таблицы базы данных Sybase и загружает их в таблицу базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f8a28-144">The following example shows how to create an SSIS Data Flow Task that extracts data from a Sybase database table and loads it into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database table.</span></span>  
  
-   <span data-ttu-id="f8a28-145">Создайте проект [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8a28-145">Create an [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] Project in the [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]</span></span>  
  
-   <span data-ttu-id="f8a28-146">Создайте диспетчер соединений ODBC, который использует локально установленный драйвер ODBC для Sybase с DSN, указывающим на локальную или удаленную базу данных Sybase.</span><span class="sxs-lookup"><span data-stu-id="f8a28-146">Create an ODBC connection manager that uses a locally installed Sybase ODBC driver with a DSN pointing to a local or remote Sybase database.</span></span> <span data-ttu-id="f8a28-147">Это база данных, из которой извлечены данные.</span><span class="sxs-lookup"><span data-stu-id="f8a28-147">This database is where the data is extracted.</span></span>  
  
-   <span data-ttu-id="f8a28-148">Создайте диспетчер соединений OLE DB, который подключается к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , куда должны быть загружены данные.</span><span class="sxs-lookup"><span data-stu-id="f8a28-148">Create an OLE DB connection manager that connects to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database where you want to load the data.</span></span>  
  
-   <span data-ttu-id="f8a28-149">Перетащите источник ODBC в область конструктора, затем настройте источник для получения данных из таблицы Sybase с данными, которые должны быть скопированы.</span><span class="sxs-lookup"><span data-stu-id="f8a28-149">Drag an ODBC source to the design surface, then configure the source to get the data from the Sybase table with the data you are going to copy.</span></span> <span data-ttu-id="f8a28-150">Используйте созданный перед этим диспетчер соединений ODBC.</span><span class="sxs-lookup"><span data-stu-id="f8a28-150">Use the ODBC connection manager you created previously.</span></span>  
  
-   <span data-ttu-id="f8a28-151">Перетащите назначение «OLE DB» в область конструктора, подключите выход источника к назначению «OLE DB», затем настройте назначение для загрузки данных в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с данными, которые извлечены из базы данных Sybase.</span><span class="sxs-lookup"><span data-stu-id="f8a28-151">Drag an OLE DB destination to the design surface, connect the source output to the OLE DB destination, then configure the destination to load the data into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table with the data you extract from the Sybase database.</span></span> <span data-ttu-id="f8a28-152">Используйте созданный перед этим диспетчер соединений OLE DB.</span><span class="sxs-lookup"><span data-stu-id="f8a28-152">Use the OLE DB connection manager you created previously.</span></span>  
  
## <a name="supported-data-types"></a><span data-ttu-id="f8a28-153">Поддерживаемые типы данных</span><span class="sxs-lookup"><span data-stu-id="f8a28-153">Supported Data Types</span></span>  
 <span data-ttu-id="f8a28-154">Компоненты массовой загрузки ODBC для служб SSIS поддерживают все встроенные типы данных ODBC, включая поддержку больших объектов (CLOB и BLOB).</span><span class="sxs-lookup"><span data-stu-id="f8a28-154">The ODBC Bulk SSIS components support all built-in ODBC data types, including support for large objects (CLOBs and BLOBs).</span></span>  
  
<span data-ttu-id="f8a28-155">Поддержка типов данных для расширяемых типов C, как описано в спецификации ODBC 3.8, отсутствует. В следующей таблице описано, какие типы данных служб SSIS используются для каждого из типов SQL ODBC.</span><span class="sxs-lookup"><span data-stu-id="f8a28-155">There is no data type support for extensible C types as described in the ODBC 3.8 specifications.The following table describes which SSIS data types are used for each ODBC SQL type.</span></span> <span data-ttu-id="f8a28-156">Разработчик служб SSIS может переопределить сопоставление, применяемое по умолчанию, и задать другой тип данных служб SSIS для столбцов ввода-вывода, не оказывая отрицательного воздействия на производительность требуемых преобразований данных.</span><span class="sxs-lookup"><span data-stu-id="f8a28-156">An SSIS developer can override the default mapping and specify a different SSIS data type for input/output columns without impacting the performance for the required data conversions.</span></span>  
  
|<span data-ttu-id="f8a28-157">Тип ODBC SQL</span><span class="sxs-lookup"><span data-stu-id="f8a28-157">ODBC SQL Type</span></span>|<span data-ttu-id="f8a28-158">Тип данных служб SSIS</span><span class="sxs-lookup"><span data-stu-id="f8a28-158">SSIS Data Type</span></span>|<span data-ttu-id="f8a28-159">Комментарии</span><span class="sxs-lookup"><span data-stu-id="f8a28-159">Comments</span></span>|  
|-----------------|------------------|------------|  
|<span data-ttu-id="f8a28-160">SQL_BIT</span><span class="sxs-lookup"><span data-stu-id="f8a28-160">SQL_BIT</span></span>|<span data-ttu-id="f8a28-161">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="f8a28-161">DT_BOOL</span></span>||  
|<span data-ttu-id="f8a28-162">SQL_TINYINT</span><span class="sxs-lookup"><span data-stu-id="f8a28-162">SQL_TINYINT</span></span>|<span data-ttu-id="f8a28-163">DT_I1</span><span class="sxs-lookup"><span data-stu-id="f8a28-163">DT_I1</span></span><br /><br /><span data-ttu-id="f8a28-164">DT_UI1</span><span class="sxs-lookup"><span data-stu-id="f8a28-164">DT_UI1</span></span>|<span data-ttu-id="f8a28-165">Типы данных SQL сопоставляются с типами служб SSIS без знака (DT_UI1, DT_UI2, DT_UI4, DT_UI8), если в драйвере ODBC для свойства UNSIGNED_ATTRIBUTE задано значение SQL_TRUE для этого типа данных SQL.</span><span class="sxs-lookup"><span data-stu-id="f8a28-165">SQL data types are mapped to SSIS unsigned types (DT_UI1, DT_UI2, DT_UI4, DT_UI8) when the ODBC driver sets the UNSIGNED_ATTRIBUTE to SQL_TRUE for that SQL data type.</span></span>|  
|<span data-ttu-id="f8a28-166">SQL_SMALLINT</span><span class="sxs-lookup"><span data-stu-id="f8a28-166">SQL_SMALLINT</span></span>|<span data-ttu-id="f8a28-167">DT_I2</span><span class="sxs-lookup"><span data-stu-id="f8a28-167">DT_I2</span></span><br /><br /><span data-ttu-id="f8a28-168">DT_UI2</span><span class="sxs-lookup"><span data-stu-id="f8a28-168">DT_UI2</span></span>|<span data-ttu-id="f8a28-169">Типы данных SQL сопоставляются с типами служб SSIS без знака (DT_UI1, DT_UI2, DT_UI4, DT_UI8), если в драйвере ODBC для свойства UNSIGNED_ATTRIBUTE задано значение SQL_TRUE для этого типа данных SQL.</span><span class="sxs-lookup"><span data-stu-id="f8a28-169">SQL data types are mapped to SSIS unsigned types (DT_UI1, DT_UI2, DT_UI4, DT_UI8) when the ODBC driver sets the UNSIGNED_ATTRIBUTE to SQL_TRUE for that SQL data type.</span></span>|  
|<span data-ttu-id="f8a28-170">SQL_INTEGER</span><span class="sxs-lookup"><span data-stu-id="f8a28-170">SQL_INTEGER</span></span>|<span data-ttu-id="f8a28-171">DT_I4</span><span class="sxs-lookup"><span data-stu-id="f8a28-171">DT_I4</span></span><br /><br /><span data-ttu-id="f8a28-172">DTUI4</span><span class="sxs-lookup"><span data-stu-id="f8a28-172">DTUI4</span></span>|<span data-ttu-id="f8a28-173">Типы данных SQL сопоставляются с типами служб SSIS без знака (DT_UI1, DT_UI2, DT_UI4, DT_UI8), если в драйвере ODBC для свойства UNSIGNED_ATTRIBUTE задано значение SQL_TRUE для этого типа данных SQL.</span><span class="sxs-lookup"><span data-stu-id="f8a28-173">SQL data types are mapped to SSIS unsigned types (DT_UI1, DT_UI2, DT_UI4, DT_UI8) when the ODBC driver sets the UNSIGNED_ATTRIBUTE to SQL_TRUE for that SQL data type.</span></span>|  
|<span data-ttu-id="f8a28-174">SQL_BIGINT</span><span class="sxs-lookup"><span data-stu-id="f8a28-174">SQL_BIGINT</span></span>|<span data-ttu-id="f8a28-175">DT_I8</span><span class="sxs-lookup"><span data-stu-id="f8a28-175">DT_I8</span></span><br /><br /><span data-ttu-id="f8a28-176">DT_UI8</span><span class="sxs-lookup"><span data-stu-id="f8a28-176">DT_UI8</span></span>|<span data-ttu-id="f8a28-177">Типы данных SQL сопоставляются с типами служб SSIS без знака (DT_UI1, DT_UI2, DT_UI4, DT_UI8), если в драйвере ODBC для свойства UNSIGNED_ATTRIBUTE задано значение SQL_TRUE для этого типа данных SQL.</span><span class="sxs-lookup"><span data-stu-id="f8a28-177">SQL data types are mapped to SSIS unsigned types (DT_UI1, DT_UI2, DT_UI4, DT_UI8) when the ODBC driver sets the UNSIGNED_ATTRIBUTE to SQL_TRUE for that SQL data type.</span></span>|  
|<span data-ttu-id="f8a28-178">SQL_DOUBLE</span><span class="sxs-lookup"><span data-stu-id="f8a28-178">SQL_DOUBLE</span></span>|<span data-ttu-id="f8a28-179">DT_R8</span><span class="sxs-lookup"><span data-stu-id="f8a28-179">DT_R8</span></span>|  
|<span data-ttu-id="f8a28-180">SQL_FLOAT</span><span class="sxs-lookup"><span data-stu-id="f8a28-180">SQL_FLOAT</span></span>|<span data-ttu-id="f8a28-181">DT_R8</span><span class="sxs-lookup"><span data-stu-id="f8a28-181">DT_R8</span></span>|  
|<span data-ttu-id="f8a28-182">SQL_REAL</span><span class="sxs-lookup"><span data-stu-id="f8a28-182">SQL_REAL</span></span>|<span data-ttu-id="f8a28-183">DT_R4</span><span class="sxs-lookup"><span data-stu-id="f8a28-183">DT_R4</span></span>|  
|<span data-ttu-id="f8a28-184">SQL_NUMERIC (p,s)</span><span class="sxs-lookup"><span data-stu-id="f8a28-184">SQL_NUMERIC (p,s)</span></span>|<span data-ttu-id="f8a28-185">DT_NUMERIC (p,s)</span><span class="sxs-lookup"><span data-stu-id="f8a28-185">DT_NUMERIC (p,s)</span></span><br /><br /><span data-ttu-id="f8a28-186">DT_R8</span><span class="sxs-lookup"><span data-stu-id="f8a28-186">DT_R8</span></span><br /><br /><span data-ttu-id="f8a28-187">DT_CY</span><span class="sxs-lookup"><span data-stu-id="f8a28-187">DT_CY</span></span>|<span data-ttu-id="f8a28-188">Числовой тип данных сопоставляется с DT_NUMERIC, если P больше или равно 38, а S больше или равен 0, а S меньше или равен P. Числовой тип данных сопоставляется с DT_R8, если выполняется по крайней мере одно из следующих условий:</span><span class="sxs-lookup"><span data-stu-id="f8a28-188">The numeric data type is mapped to DT_NUMERIC when P is greater than or equal to 38 and S is greater than or equal to 0 and S is less than or equal to P. The numeric data type is mapped to DT_R8 when at least one of the following is true:</span></span><br /><br /><span data-ttu-id="f8a28-189">Точность больше 38</span><span class="sxs-lookup"><span data-stu-id="f8a28-189">Precision is greater than 38</span></span><br /><br /><span data-ttu-id="f8a28-190">Масштаб меньше нуля</span><span class="sxs-lookup"><span data-stu-id="f8a28-190">Scale is less than zero</span></span><br /><br /><span data-ttu-id="f8a28-191">Масштаб больше 38</span><span class="sxs-lookup"><span data-stu-id="f8a28-191">Scale is greater than 38</span></span><br /><br /><span data-ttu-id="f8a28-192">Масштаб больше точности</span><span class="sxs-lookup"><span data-stu-id="f8a28-192">Scale is greater than Precision</span></span><br /><br /><br /><br /><span data-ttu-id="f8a28-193">Обратите внимание, что числовой тип данных сопоставлен DT_CY, если он объявлен как тип данных money.</span><span class="sxs-lookup"><span data-stu-id="f8a28-193">Note that the numeric data type is mapped to DT_CY when it is declared as a money data type.</span></span>|  
|<span data-ttu-id="f8a28-194">SQL_DECIMAL (p,s)</span><span class="sxs-lookup"><span data-stu-id="f8a28-194">SQL_DECIMAL (p,s)</span></span>|<span data-ttu-id="f8a28-195">DT_NUMERIC (p,s)</span><span class="sxs-lookup"><span data-stu-id="f8a28-195">DT_NUMERIC (p,s)</span></span><br /><br /><span data-ttu-id="f8a28-196">DT_R8</span><span class="sxs-lookup"><span data-stu-id="f8a28-196">DT_R8</span></span><br /><br /><span data-ttu-id="f8a28-197">DT_CY</span><span class="sxs-lookup"><span data-stu-id="f8a28-197">DT_CY</span></span>|<span data-ttu-id="f8a28-198">Тип данных decimal сопоставляется с DT_NUMERIC, если P больше или равно 38, а S больше или равно 0, а S меньше или равен P. Тип данных decimal сопоставляется с DT_R8, если выполняется хотя бы одно из следующих условий:</span><span class="sxs-lookup"><span data-stu-id="f8a28-198">The decimal data type is mapped to DT_NUMERIC when P is greater than or equal to 38 and S is greater than or equal to 0 and S is less than or equal to P. The decimal data type is mapped to DT_R8 when at least one of the following is true:</span></span><br /><br /><span data-ttu-id="f8a28-199">Точность больше 38</span><span class="sxs-lookup"><span data-stu-id="f8a28-199">Precision is greater than 38</span></span><br /><br /><span data-ttu-id="f8a28-200">Масштаб меньше нуля</span><span class="sxs-lookup"><span data-stu-id="f8a28-200">Scale is less than zero</span></span><br /><br /><span data-ttu-id="f8a28-201">Масштаб больше 38</span><span class="sxs-lookup"><span data-stu-id="f8a28-201">Scale is greater than 38</span></span><br /><br /><span data-ttu-id="f8a28-202">Масштаб больше точности</span><span class="sxs-lookup"><span data-stu-id="f8a28-202">Scale is greater than Precision</span></span><br /><br /><span data-ttu-id="f8a28-203">Обратите внимание, что тип данных decimal сопоставляется с DT_CY, если он объявлен как тип данных money.</span><span class="sxs-lookup"><span data-stu-id="f8a28-203">Note that the decimal data type is mapped to DT_CY when it is declared as a money data type.</span></span>|  
|<span data-ttu-id="f8a28-204">SQL_DATE</span><span class="sxs-lookup"><span data-stu-id="f8a28-204">SQL_DATE</span></span><br /><br /><span data-ttu-id="f8a28-205">SQL_TYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="f8a28-205">SQL_TYPE_DATE</span></span>|<span data-ttu-id="f8a28-206">DT_DBDATE</span><span class="sxs-lookup"><span data-stu-id="f8a28-206">DT_DBDATE</span></span>|  
|<span data-ttu-id="f8a28-207">SQL_TIME</span><span class="sxs-lookup"><span data-stu-id="f8a28-207">SQL_TIME</span></span><br /><br /><span data-ttu-id="f8a28-208">SQL_TYPE_TIME</span><span class="sxs-lookup"><span data-stu-id="f8a28-208">SQL_TYPE_TIME</span></span>|<span data-ttu-id="f8a28-209">DT_DBTIME</span><span class="sxs-lookup"><span data-stu-id="f8a28-209">DT_DBTIME</span></span>|  
|<span data-ttu-id="f8a28-210">SQL_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="f8a28-210">SQL_TIMESTAMP</span></span><br /><br /><span data-ttu-id="f8a28-211">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="f8a28-211">SQL_TYPE_TIMESTAMP</span></span>|<span data-ttu-id="f8a28-212">DT_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="f8a28-212">DT_DBTIMESTAMP</span></span><br /><br /><span data-ttu-id="f8a28-213">DT_DBTIMESTAMP2</span><span class="sxs-lookup"><span data-stu-id="f8a28-213">DT_DBTIMESTAMP2</span></span>|<span data-ttu-id="f8a28-214">Типы данных SQL_TIMESTAMP сопоставляются с DT_DBTIMESTAMP2, если масштаб больше 3.</span><span class="sxs-lookup"><span data-stu-id="f8a28-214">SQL_TIMESTAMP data types are mapped to DT_DBTIMESTAMP2 if  scale is greater than 3.</span></span> <span data-ttu-id="f8a28-215">Во всех прочих случаях они сопоставляются с DT_DBTIMESTAMP.</span><span class="sxs-lookup"><span data-stu-id="f8a28-215">In all other cases, they are mapped to DT_DBTIMESTAMP.</span></span>|  
|<span data-ttu-id="f8a28-216">SQL_CHAR</span><span class="sxs-lookup"><span data-stu-id="f8a28-216">SQL_CHAR</span></span><br /><br /><span data-ttu-id="f8a28-217">SQLVARCHAR</span><span class="sxs-lookup"><span data-stu-id="f8a28-217">SQLVARCHAR</span></span>|<span data-ttu-id="f8a28-218">DT_STR</span><span class="sxs-lookup"><span data-stu-id="f8a28-218">DT_STR</span></span><br /><br /><span data-ttu-id="f8a28-219">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="f8a28-219">DT_WSTR</span></span><br /><br /><span data-ttu-id="f8a28-220">DT_TEXT</span><span class="sxs-lookup"><span data-stu-id="f8a28-220">DT_TEXT</span></span><br /><br /><span data-ttu-id="f8a28-221">DT_NTEXT</span><span class="sxs-lookup"><span data-stu-id="f8a28-221">DT_NTEXT</span></span>|<span data-ttu-id="f8a28-222">Тип DT_STR используется, если длина столбца меньше или равна 8000 и свойство **ExposeStringsAsUnicode** имеет значение false.</span><span class="sxs-lookup"><span data-stu-id="f8a28-222">DT_STR is used if the column length is less than or equal to 8000 and the **ExposeStringsAsUnicode** property is false.</span></span><br /><br /><span data-ttu-id="f8a28-223">Тип DT_WSTR используется, если длина столбца меньше или равна 8000 и свойство **ExposeStringsAsUnicode** имеет значение true.</span><span class="sxs-lookup"><span data-stu-id="f8a28-223">DT_WSTR is used if the column length is less than or equal to 8000 and the **ExposeStringsAsUnicode** property is true.</span></span><br /><br /><span data-ttu-id="f8a28-224">Тип DT_TEXT используется, если длина столбца больше 8000 и свойство **ExposeStringsAsUnicode** имеет значение false.</span><span class="sxs-lookup"><span data-stu-id="f8a28-224">DT_TEXT is used if the column length is greater than 8000 and the **ExposeStringsAsUnicode** property is false.</span></span><br /><br /><span data-ttu-id="f8a28-225">Тип DT_NTEXT используется, если длина столбца больше 8000 и свойство **ExposeStringsAsUnicode** имеет значение true.</span><span class="sxs-lookup"><span data-stu-id="f8a28-225">DT_NTEXT is used if the column length is greater than 8000 and the **ExposeStringsAsUnicode** property is true.</span></span>|  
|<span data-ttu-id="f8a28-226">SQL_LONGVARCHAR</span><span class="sxs-lookup"><span data-stu-id="f8a28-226">SQL_LONGVARCHAR</span></span>|<span data-ttu-id="f8a28-227">DT_TEXT</span><span class="sxs-lookup"><span data-stu-id="f8a28-227">DT_TEXT</span></span><br /><br /><span data-ttu-id="f8a28-228">DT_NTEXT</span><span class="sxs-lookup"><span data-stu-id="f8a28-228">DT_NTEXT</span></span>|<span data-ttu-id="f8a28-229">Тип DT_NTEXT используется, если свойство **ExposeStringsAsUnicode** имеет значение true.</span><span class="sxs-lookup"><span data-stu-id="f8a28-229">DT_NTEXT is used if the **ExposeStringsAsUnicode** property is true.</span></span>|  
|<span data-ttu-id="f8a28-230">SQL_WCHAR</span><span class="sxs-lookup"><span data-stu-id="f8a28-230">SQL_WCHAR</span></span><br /><br /><span data-ttu-id="f8a28-231">SQL_WVARCHAR</span><span class="sxs-lookup"><span data-stu-id="f8a28-231">SQL_WVARCHAR</span></span>|<span data-ttu-id="f8a28-232">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="f8a28-232">DT_WSTR</span></span><br /><br /><span data-ttu-id="f8a28-233">DT_NTEXT</span><span class="sxs-lookup"><span data-stu-id="f8a28-233">DT_NTEXT</span></span>|<span data-ttu-id="f8a28-234">Тип DT_WSTR используется, если длина столбца меньше или равна 4000.</span><span class="sxs-lookup"><span data-stu-id="f8a28-234">DT_WSTR is used if the column length is less than or equal to 4000.</span></span><br /><br /><span data-ttu-id="f8a28-235">Тип DT_NTEXT используется, если длина столбца больше 4000.</span><span class="sxs-lookup"><span data-stu-id="f8a28-235">DT_NTEXT is used if the column length is greater than 4000.</span></span>|  
|<span data-ttu-id="f8a28-236">SQL_WLONGVARCHAR</span><span class="sxs-lookup"><span data-stu-id="f8a28-236">SQL_WLONGVARCHAR</span></span>|<span data-ttu-id="f8a28-237">DT_NTEXT</span><span class="sxs-lookup"><span data-stu-id="f8a28-237">DT_NTEXT</span></span>|  
|<span data-ttu-id="f8a28-238">SQL_BINARY</span><span class="sxs-lookup"><span data-stu-id="f8a28-238">SQL_BINARY</span></span>|<span data-ttu-id="f8a28-239">DT_BYTE</span><span class="sxs-lookup"><span data-stu-id="f8a28-239">DT_BYTE</span></span><br /><br /><span data-ttu-id="f8a28-240">DT_IMAGE</span><span class="sxs-lookup"><span data-stu-id="f8a28-240">DT_IMAGE</span></span>|<span data-ttu-id="f8a28-241">Тип DT_BYTES используется, если длина столбца меньше или равна 8000.</span><span class="sxs-lookup"><span data-stu-id="f8a28-241">DT_BYTES is used if the column length is less than or equal to 8000.</span></span><br /><br /><span data-ttu-id="f8a28-242">Тип DT_IMAGE используется, если длина столбца больше 8000.</span><span class="sxs-lookup"><span data-stu-id="f8a28-242">DT_IMAGE if the column length is greater than 8000.</span></span>|  
|<span data-ttu-id="f8a28-243">SQL_LONGVARBINARY</span><span class="sxs-lookup"><span data-stu-id="f8a28-243">SQL_LONGVARBINARY</span></span>|<span data-ttu-id="f8a28-244">DT_IMAGE</span><span class="sxs-lookup"><span data-stu-id="f8a28-244">DT_IMAGE</span></span>|  
|<span data-ttu-id="f8a28-245">SQL_GUID</span><span class="sxs-lookup"><span data-stu-id="f8a28-245">SQL_GUID</span></span>|<span data-ttu-id="f8a28-246">DT_GUID</span><span class="sxs-lookup"><span data-stu-id="f8a28-246">DT_GUID</span></span>|  
|<span data-ttu-id="f8a28-247">SQL_INTERVAL_YEAR</span><span class="sxs-lookup"><span data-stu-id="f8a28-247">SQL_INTERVAL_YEAR</span></span><br /><br /><span data-ttu-id="f8a28-248">SQL_INTERVAL_MONTH</span><span class="sxs-lookup"><span data-stu-id="f8a28-248">SQL_INTERVAL_MONTH</span></span><br /><br /><span data-ttu-id="f8a28-249">SQL_INTERVAL_DAY</span><span class="sxs-lookup"><span data-stu-id="f8a28-249">SQL_INTERVAL_DAY</span></span><br /><br /><span data-ttu-id="f8a28-250">SQL_INTERVAL_HOUR</span><span class="sxs-lookup"><span data-stu-id="f8a28-250">SQL_INTERVAL_HOUR</span></span><br /><br /><span data-ttu-id="f8a28-251">SQL_INTERVAL_MINUTE</span><span class="sxs-lookup"><span data-stu-id="f8a28-251">SQL_INTERVAL_MINUTE</span></span><br /><br /><span data-ttu-id="f8a28-252">SQL_INTERVAL_SECOND</span><span class="sxs-lookup"><span data-stu-id="f8a28-252">SQL_INTERVAL_SECOND</span></span><br /><br /><span data-ttu-id="f8a28-253">SQL_INTERVAL_YEAR_TO_MONTH</span><span class="sxs-lookup"><span data-stu-id="f8a28-253">SQL_INTERVAL_YEAR_TO_MONTH</span></span><br /><br /><span data-ttu-id="f8a28-254">SQL_INTERVAL_DAY_TO_HOUR</span><span class="sxs-lookup"><span data-stu-id="f8a28-254">SQL_INTERVAL_DAY_TO_HOUR</span></span><br /><br /><span data-ttu-id="f8a28-255">SQL_INTERVAL_DAY_TO_MINUTE</span><span class="sxs-lookup"><span data-stu-id="f8a28-255">SQL_INTERVAL_DAY_TO_MINUTE</span></span><br /><br /><span data-ttu-id="f8a28-256">SQL_INTERVAL_DAY_TO_SECOND</span><span class="sxs-lookup"><span data-stu-id="f8a28-256">SQL_INTERVAL_DAY_TO_SECOND</span></span><br /><br /><span data-ttu-id="f8a28-257">SQL_INTERVAL_HOUR_TO_MINUTE</span><span class="sxs-lookup"><span data-stu-id="f8a28-257">SQL_INTERVAL_HOUR_TO_MINUTE</span></span><br /><br /><span data-ttu-id="f8a28-258">SQL_INTERVAL_HOUR_TO_SECOND</span><span class="sxs-lookup"><span data-stu-id="f8a28-258">SQL_INTERVAL_HOUR_TO_SECOND</span></span><br /><br /><span data-ttu-id="f8a28-259">SQL_INTERVAL_MINUTE_TO_SECOND</span><span class="sxs-lookup"><span data-stu-id="f8a28-259">SQL_INTERVAL_MINUTE_TO_SECOND</span></span>|<span data-ttu-id="f8a28-260">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="f8a28-260">DT_WSTR</span></span>|  
|<span data-ttu-id="f8a28-261">Типы данных для конкретных поставщиков</span><span class="sxs-lookup"><span data-stu-id="f8a28-261">Provider Specific Data Types</span></span>|<span data-ttu-id="f8a28-262">DT_BYTES</span><span class="sxs-lookup"><span data-stu-id="f8a28-262">DT_BYTES</span></span><br /><br /><span data-ttu-id="f8a28-263">DT_IMAGE</span><span class="sxs-lookup"><span data-stu-id="f8a28-263">DT_IMAGE</span></span>|<span data-ttu-id="f8a28-264">Тип DT_BYTES используется, если длина столбца меньше или равна 8000.</span><span class="sxs-lookup"><span data-stu-id="f8a28-264">DT_BYTES is used if the column length is less than or equal to 8000.</span></span><br /><br /><span data-ttu-id="f8a28-265">Тип DT_IMAGE используется, если длина столбца равна нулю или больше 8000.</span><span class="sxs-lookup"><span data-stu-id="f8a28-265">DT_IMAGE is used if the column length is zero or greater than 8000.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="f8a28-266">в этом разделе</span><span class="sxs-lookup"><span data-stu-id="f8a28-266">In This Section</span></span>  
  
-   [<span data-ttu-id="f8a28-267">Источник «ODBC»</span><span class="sxs-lookup"><span data-stu-id="f8a28-267">ODBC Source</span></span>](odbc-source.md)  
  
-   [<span data-ttu-id="f8a28-268">Назначение «ODBC»</span><span class="sxs-lookup"><span data-stu-id="f8a28-268">ODBC Destination</span></span>](odbc-destination.md)  
  
 