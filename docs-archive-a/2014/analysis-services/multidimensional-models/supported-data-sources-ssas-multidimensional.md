---
title: Поддерживаемые источники данных (многомерные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Analysis Services, data sources
- data sources [Analysis Services], about data sources
- Analysis Services, data sources
- connections [Analysis Services]
- SSAS, data sources
ms.assetid: c97e0f8d-7ddd-4941-8b51-e7832f30fbbe
author: minewiskan
ms.author: owend
ms.openlocfilehash: 93c09424a7cc5fa6a17d84b7464798c0b4412612
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666234"
---
# <a name="data-sources-supported-ssas-multidimensional"></a><span data-ttu-id="0f841-102">Поддерживаемые источники данных (многомерные службы SSAS)</span><span class="sxs-lookup"><span data-stu-id="0f841-102">Data Sources Supported (SSAS Multidimensional)</span></span>
  <span data-ttu-id="0f841-103">В этом разделе описываются типы источников данных, которые можно использовать в многомерной модели.</span><span class="sxs-lookup"><span data-stu-id="0f841-103">This topic describes the types of data sources that you can use in a multidimensional model.</span></span>  
  
##  <a name="supported-data-sources"></a><a name="bkmk_supported_ds"></a><span data-ttu-id="0f841-104">Поддерживаемые источники данных</span><span class="sxs-lookup"><span data-stu-id="0f841-104">Supported Data Sources</span></span>  
 <span data-ttu-id="0f841-105">Данные можно получать из источников данных, перечисленных в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="0f841-105">You can retrieve data from the data sources in the following table.</span></span> <span data-ttu-id="0f841-106">При установке среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]программа установки не устанавливает поставщиков, указанных для каждого из источников данных.</span><span class="sxs-lookup"><span data-stu-id="0f841-106">When you install [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], setup does not install the providers that are listed for each data source.</span></span> <span data-ttu-id="0f841-107">Некоторые поставщики могут быть уже установлены в компьютер с другими приложениями, а в других случаях потребуется загрузить и установить необходимый поставщик.</span><span class="sxs-lookup"><span data-stu-id="0f841-107">Some providers might already be installed with other applications on your computer; in other cases you will need to download and install the provider.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f841-108">Для подключения к сторонним базам данных можно использовать сторонние поставщики (например, Oracle OLE DB). Их поддержка осуществляется сторонними производителями.</span><span class="sxs-lookup"><span data-stu-id="0f841-108">Third party providers, such as the Oracle OLE DB Provider, may also be used to connect to third party databases, with support provided by those third parties.</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="0f841-109">Источник</span><span class="sxs-lookup"><span data-stu-id="0f841-109">Source</span></span>|<span data-ttu-id="0f841-110">Версии</span><span class="sxs-lookup"><span data-stu-id="0f841-110">Versions</span></span>|<span data-ttu-id="0f841-111">Тип файла</span><span class="sxs-lookup"><span data-stu-id="0f841-111">File type</span></span>|<span data-ttu-id="0f841-112">Поставщики <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0f841-112">Providers <sup>1</sup></span></span>|  
|<span data-ttu-id="0f841-113">Базы данных Access</span><span class="sxs-lookup"><span data-stu-id="0f841-113">Access databases</span></span>|<span data-ttu-id="0f841-114">Microsoft Access 2007, 2010, 2013.</span><span class="sxs-lookup"><span data-stu-id="0f841-114">Microsoft Access 2007, 2010, 2013.</span></span>|<span data-ttu-id="0f841-115">ACCDB или MDB</span><span class="sxs-lookup"><span data-stu-id="0f841-115">.accdb or .mdb</span></span>|<span data-ttu-id="0f841-116">Поставщик Microsoft OLE DB для Jet 4.0</span><span class="sxs-lookup"><span data-stu-id="0f841-116">Microsoft Jet 4.0 OLE DB provider</span></span>|  
|<span data-ttu-id="0f841-117">SQL Server реляционные базы данных <sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="0f841-117">SQL Server relational databases <sup>5</sup></span></span>|<span data-ttu-id="0f841-118">Microsoft SQL Server 2005, 2008, 2008 R2, 2012, 2014 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] <sup>2</sup>, SQL Server Parallel Data Warehouse (PDW) <sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0f841-118">Microsoft SQL Server 2005, 2008, 2008 R2, 2012, 2014 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<sup>2</sup>, SQL Server Parallel Data Warehouse (PDW) <sup>3</sup></span></span>|<span data-ttu-id="0f841-119">(неприменимо)</span><span class="sxs-lookup"><span data-stu-id="0f841-119">(not applicable)</span></span>|<span data-ttu-id="0f841-120">Поставщик OLE DB для SQL Server</span><span class="sxs-lookup"><span data-stu-id="0f841-120">OLE DB Provider for SQL Server</span></span><br /><br /> <span data-ttu-id="0f841-121">Поставщик OLE DB для собственного клиента SQL Server</span><span class="sxs-lookup"><span data-stu-id="0f841-121">SQL Server Native Client OLE DB Provider</span></span><br /><br /> <span data-ttu-id="0f841-122">Поставщик OLE DB для собственного клиента SQL Server 11,0</span><span class="sxs-lookup"><span data-stu-id="0f841-122">SQL Server Native 11.0 Client OLE DB Provider</span></span><br /><br /> <span data-ttu-id="0f841-123">Поставщик данных .NET Framework для клиента SQL</span><span class="sxs-lookup"><span data-stu-id="0f841-123">.NET Framework Data Provider for SQL Client</span></span>|  
|<span data-ttu-id="0f841-124">Реляционные базы данных Oracle</span><span class="sxs-lookup"><span data-stu-id="0f841-124">Oracle relational databases</span></span>|<span data-ttu-id="0f841-125">Oracle 9i, 10g, 11g.</span><span class="sxs-lookup"><span data-stu-id="0f841-125">Oracle 9i, 10g, 11g.</span></span>|<span data-ttu-id="0f841-126">(неприменимо)</span><span class="sxs-lookup"><span data-stu-id="0f841-126">(not applicable)</span></span>|<span data-ttu-id="0f841-127">Поставщик OLE DB для Oracle</span><span class="sxs-lookup"><span data-stu-id="0f841-127">Oracle OLE DB Provider</span></span><br /><br /> <span data-ttu-id="0f841-128">Поставщик данных .NET Framework для клиента Oracle</span><span class="sxs-lookup"><span data-stu-id="0f841-128">.NET Framework Data Provider for Oracle Client</span></span><br /><br /> <span data-ttu-id="0f841-129">Поставщик данных .NET Framework для SQL Server</span><span class="sxs-lookup"><span data-stu-id="0f841-129">.NET Framework Data Provider for SQL Server</span></span><br /><br /> <span data-ttu-id="0f841-130">MSDAORA OLE DB поставщик <sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="0f841-130">MSDAORA OLE DB provider <sup>4</sup></span></span><br /><br /> <span data-ttu-id="0f841-131">OraOLEDB</span><span class="sxs-lookup"><span data-stu-id="0f841-131">OraOLEDB</span></span><br /><br /> <span data-ttu-id="0f841-132">MSDASQL</span><span class="sxs-lookup"><span data-stu-id="0f841-132">MSDASQL</span></span>|  
|<span data-ttu-id="0f841-133">Реляционные базы данных Teradata</span><span class="sxs-lookup"><span data-stu-id="0f841-133">Teradata relational databases</span></span>|<span data-ttu-id="0f841-134">Teradata V2R6, V12</span><span class="sxs-lookup"><span data-stu-id="0f841-134">Teradata V2R6, V12</span></span>|<span data-ttu-id="0f841-135">(неприменимо)</span><span class="sxs-lookup"><span data-stu-id="0f841-135">(not applicable)</span></span>|<span data-ttu-id="0f841-136">Поставщик TDOLEDB OLE DB</span><span class="sxs-lookup"><span data-stu-id="0f841-136">TDOLEDB OLE DB provider</span></span><br /><br /> <span data-ttu-id="0f841-137">Поставщик данных .NET для Teradata</span><span class="sxs-lookup"><span data-stu-id="0f841-137">.Net Data Provider for Teradata</span></span>|  
|<span data-ttu-id="0f841-138">Реляционные базы данных Informix</span><span class="sxs-lookup"><span data-stu-id="0f841-138">Informix relational databases</span></span>|<span data-ttu-id="0f841-139">V11.10</span><span class="sxs-lookup"><span data-stu-id="0f841-139">V11.10</span></span>|<span data-ttu-id="0f841-140">(неприменимо)</span><span class="sxs-lookup"><span data-stu-id="0f841-140">(not applicable)</span></span>|<span data-ttu-id="0f841-141">Поставщик OLE DB для Informix</span><span class="sxs-lookup"><span data-stu-id="0f841-141">Informix OLE DB provider</span></span>|  
|<span data-ttu-id="0f841-142">Реляционные базы данных IBM DB2</span><span class="sxs-lookup"><span data-stu-id="0f841-142">IBM DB2 relational databases</span></span>|<span data-ttu-id="0f841-143">8.1</span><span class="sxs-lookup"><span data-stu-id="0f841-143">8.1</span></span>|<span data-ttu-id="0f841-144">(неприменимо)</span><span class="sxs-lookup"><span data-stu-id="0f841-144">(not applicable)</span></span>|<span data-ttu-id="0f841-145">DB2OLEDB</span><span class="sxs-lookup"><span data-stu-id="0f841-145">DB2OLEDB</span></span>|  
|<span data-ttu-id="0f841-146">Реляционные базы данных Sybase Adaptive Server Enterprise (ASE)</span><span class="sxs-lookup"><span data-stu-id="0f841-146">Sybase Adaptive Server Enterprise (ASE) relational databases</span></span>|<span data-ttu-id="0f841-147">15.0.2</span><span class="sxs-lookup"><span data-stu-id="0f841-147">15.0.2</span></span>|<span data-ttu-id="0f841-148">(неприменимо)</span><span class="sxs-lookup"><span data-stu-id="0f841-148">(not applicable)</span></span>|<span data-ttu-id="0f841-149">Поставщик OLE DB для Sybase</span><span class="sxs-lookup"><span data-stu-id="0f841-149">Sybase OLE DB provider</span></span>|  
|<span data-ttu-id="0f841-150">Другие реляционные базы данных</span><span class="sxs-lookup"><span data-stu-id="0f841-150">Other relational databases</span></span>|<span data-ttu-id="0f841-151">(неприменимо)</span><span class="sxs-lookup"><span data-stu-id="0f841-151">(not applicable)</span></span>|<span data-ttu-id="0f841-152">(неприменимо)</span><span class="sxs-lookup"><span data-stu-id="0f841-152">(not applicable)</span></span>|<span data-ttu-id="0f841-153">Поставщик OLE DB</span><span class="sxs-lookup"><span data-stu-id="0f841-153">An OLE DB provider</span></span>|  
  
 <span data-ttu-id="0f841-154"><sup>1</sup> источники данных ODBC не поддерживаются для многомерных решений.</span><span class="sxs-lookup"><span data-stu-id="0f841-154"><sup>1</sup> ODBC data sources are not supported for multidimensional solutions.</span></span> <span data-ttu-id="0f841-155">Хотя соединение будут обеспечивать сами службы Analysis Services, конструкторы в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] , применяемые для создания решений, не могут подключаться к источнику данных ODBC, даже если используется драйвер MSDASQL.</span><span class="sxs-lookup"><span data-stu-id="0f841-155">Although Analysis Services itself will handle the connection, the designers in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] used for building solutions cannot connect to an ODBC data source, even when using the MSDASQL driver.</span></span> <span data-ttu-id="0f841-156">Если бизнес-требования включают источник данных ODBC, рассмотрите альтернативную возможность — создание табличного решения.</span><span class="sxs-lookup"><span data-stu-id="0f841-156">If your business requirements include an ODBC data source, consider building a tabular solution instead.</span></span>  
  
 <span data-ttu-id="0f841-157"><sup>2</sup> дополнительные сведения см [!INCLUDE[ssSDS](../../includes/sssds-md.md)] . в разделе на [Azure.Microsoft.com](https://go.microsoft.com/fwlink/?LinkID=157856).</span><span class="sxs-lookup"><span data-stu-id="0f841-157"><sup>2</sup> For more information, see [!INCLUDE[ssSDS](../../includes/sssds-md.md)], on [azure.microsoft.com](https://go.microsoft.com/fwlink/?LinkID=157856).</span></span>  
  
 <span data-ttu-id="0f841-158"><sup>3</sup> дополнительные сведения о [!INCLUDE[ssSDS](../../includes/sssds-md.md)] PDW см. в статье [SQL Server Parallel Data Warehouse](https://go.microsoft.com/fwlink/?LinkId=150895).</span><span class="sxs-lookup"><span data-stu-id="0f841-158"><sup>3</sup> For more information about [!INCLUDE[ssSDS](../../includes/sssds-md.md)] PDW, see [SQL Server Parallel Data Warehouse](https://go.microsoft.com/fwlink/?LinkId=150895).</span></span>  
  
 <span data-ttu-id="0f841-159"><sup>4</sup> в некоторых случаях использование поставщика MSDAORA OLE DB может привести к ошибкам подключения, особенно с более новыми версиями Oracle.</span><span class="sxs-lookup"><span data-stu-id="0f841-159"><sup>4</sup> In some cases, using the MSDAORA OLE DB provider can result in connection errors, particularly with newer versions of Oracle.</span></span> <span data-ttu-id="0f841-160">Если возникают ошибки, рекомендуется использовать один из других поставщиков для Oracle.</span><span class="sxs-lookup"><span data-stu-id="0f841-160">If you encounter any errors, we recommend that you use one of the other providers listed for Oracle.</span></span>  
  
 <span data-ttu-id="0f841-161"><sup>5</sup> для некоторых функций требуется SQL Server реляционной базы данных, которая работает в локальной среде.</span><span class="sxs-lookup"><span data-stu-id="0f841-161"><sup>5</sup> Some features require a SQL Server relational database that runs on-premises.</span></span> <span data-ttu-id="0f841-162">Это требуется для функции обратной записи и хранилища ROLAP — используемый источник данных должен быть реляционной базой данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0f841-162">Specifically, writeback and ROLAP storage require that the underlying data source is a SQL Server relational database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f841-163">См. также:</span><span class="sxs-lookup"><span data-stu-id="0f841-163">See Also</span></span>  
 <span data-ttu-id="0f841-164">[Поддерживаемые источники данных &#40;табличные&#41;SSAS](../tabular-models/data-sources-supported-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="0f841-164">[Data Sources Supported &#40;SSAS Tabular&#41;](../tabular-models/data-sources-supported-ssas-tabular.md) </span></span>  
 <span data-ttu-id="0f841-165">[Источники данных в многомерных моделях](data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="0f841-165">[Data Sources in Multidimensional Models](data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="0f841-166">Представления источников данных в многомерных моделях</span><span class="sxs-lookup"><span data-stu-id="0f841-166">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)  
  
  