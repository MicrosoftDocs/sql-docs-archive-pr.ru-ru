---
title: Задание свойств источника данных (многомерные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.datasourceproperties.f1
helpviewer_keywords:
- Data Source Properties dialog box
ms.assetid: bf8b600f-5b99-4f7d-908b-8a391721e9dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: e6346d362650b677451468eebe8952c1cb28d239
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656037"
---
# <a name="set-data-source-properties-ssas-multidimensional"></a><span data-ttu-id="c8a45-102">Задание свойств источника данных (многомерные службы SSAS)</span><span class="sxs-lookup"><span data-stu-id="c8a45-102">Set Data Source Properties (SSAS Multidimensional)</span></span>
  <span data-ttu-id="c8a45-103">Объект источника данных в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]задает соединение с внешним хранилищем данных или реляционной базой данных, предоставляющей данные для многомерной модели.</span><span class="sxs-lookup"><span data-stu-id="c8a45-103">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], a data source object specifies a connection to an external data warehouse or relational database that provides data to a multidimensional model.</span></span> <span data-ttu-id="c8a45-104">Свойства источника данных определяют строку соединения, интервал времени ожидания, максимальное число соединений и уровень изоляции транзакций.</span><span class="sxs-lookup"><span data-stu-id="c8a45-104">Properties on the data source determine the connection string, a timeout interval, maximum number of connections, and the transaction isolation level.</span></span>  
  
## <a name="set-data-source-properties-in-sql-server-data-tools"></a><span data-ttu-id="c8a45-105">Настройка свойств источника данных в SQL Server Data Tools</span><span class="sxs-lookup"><span data-stu-id="c8a45-105">Set data source properties in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="c8a45-106">Дважды щелкните источник данных в обозревателе решений, чтобы открыть конструктор источников данных.</span><span class="sxs-lookup"><span data-stu-id="c8a45-106">Double-click a data source in Solution Explorer to open Data Source Designer.</span></span>  
  
2.  <span data-ttu-id="c8a45-107">В конструкторе источников данных перейдите на вкладку **Сведения об олицетворении** .</span><span class="sxs-lookup"><span data-stu-id="c8a45-107">Click the **Impersonation Information** tab in Data Source Designer.</span></span> <span data-ttu-id="c8a45-108">Дополнительные сведения о создании источника данных см. в разделе [Создание источника данных (многомерные службы SSAS)](create-a-data-source-ssas-multidimensional.md).</span><span class="sxs-lookup"><span data-stu-id="c8a45-108">For more information about creating a data source, see [Create a Data Source &#40;SSAS Multidimensional&#41;](create-a-data-source-ssas-multidimensional.md).</span></span>  
  
## <a name="set-data-source-properties-in-management-studio"></a><span data-ttu-id="c8a45-109">Настройка свойств источника данных в среде Management Studio</span><span class="sxs-lookup"><span data-stu-id="c8a45-109">Set data source properties in Management Studio</span></span>  
  
1.  <span data-ttu-id="c8a45-110">Разверните папку базы данных, откройте папку **Источник данных** в узле имени базы данных, щелкните правой кнопкой мыши источник данных в **обозревателе объектов** и выберите **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="c8a45-110">Expand the database folder, open the **Data Source** folder under the database name, right-click a data source in **Object Explorer** and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="c8a45-111">Вы также можете изменить имя, описание или параметр олицетворения.</span><span class="sxs-lookup"><span data-stu-id="c8a45-111">Optionally, modify the name, description, or impersonation option.</span></span> <span data-ttu-id="c8a45-112">Дополнительные сведения см. в разделе [Задание параметров олицетворения (многомерная база данных SSAS)](set-impersonation-options-ssas-multidimensional.md).</span><span class="sxs-lookup"><span data-stu-id="c8a45-112">For more information, see [Set Impersonation Options &#40;SSAS - Multidimensional&#41;](set-impersonation-options-ssas-multidimensional.md).</span></span>  
  
## <a name="data-source-properties"></a><span data-ttu-id="c8a45-113">Свойства источника данных</span><span class="sxs-lookup"><span data-stu-id="c8a45-113">Data Source properties</span></span>  
  
|<span data-ttu-id="c8a45-114">Термин</span><span class="sxs-lookup"><span data-stu-id="c8a45-114">Term</span></span>|<span data-ttu-id="c8a45-115">Определение</span><span class="sxs-lookup"><span data-stu-id="c8a45-115">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="c8a45-116">**Имя, идентификатор, описание**</span><span class="sxs-lookup"><span data-stu-id="c8a45-116">**Name, ID, Description**</span></span>|<span data-ttu-id="c8a45-117">Имя, идентификатор и описание используются для определения и описания объекта источника данных в многомерной модели.</span><span class="sxs-lookup"><span data-stu-id="c8a45-117">Name, ID, and Description are used to identify and describe the data source object in the multidimensional model.</span></span><br /><br /> <span data-ttu-id="c8a45-118">После развертывания и обработки решения можно указать имя и описание в среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] или [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c8a45-118">Name and Description can be specified in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] or in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] after you deploy or process the solution.</span></span><br /><br /> <span data-ttu-id="c8a45-119">Идентификатор задается при создании объекта.</span><span class="sxs-lookup"><span data-stu-id="c8a45-119">ID is generated when the object is created.</span></span> <span data-ttu-id="c8a45-120">Имя и описание можно легко изменить, а идентификаторы доступны только для чтения и не могут быть изменены.</span><span class="sxs-lookup"><span data-stu-id="c8a45-120">Although you can easily modify the name and description, IDs are read-only and should not be changed.</span></span> <span data-ttu-id="c8a45-121">Постоянство идентификаторов объектов гарантирует сохранение зависимостей объектов и ссылок для всей модели.</span><span class="sxs-lookup"><span data-stu-id="c8a45-121">A fixed object ID preserves object dependencies and references throughout the model.</span></span>|  
|<span data-ttu-id="c8a45-122">**Отметка времени создания**</span><span class="sxs-lookup"><span data-stu-id="c8a45-122">**Create Timestamp**</span></span>|<span data-ttu-id="c8a45-123">Это свойство, доступное только для чтения, отображается в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8a45-123">This read-only property appears in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="c8a45-124">Оно отображает дату и время создания источника данных.</span><span class="sxs-lookup"><span data-stu-id="c8a45-124">It displays the date and time the data source was created.</span></span>|  
|<span data-ttu-id="c8a45-125">**Последнее обновление схемы**</span><span class="sxs-lookup"><span data-stu-id="c8a45-125">**Last Schema Update**</span></span>|<span data-ttu-id="c8a45-126">Это свойство, доступное только для чтения, отображается в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8a45-126">This read-only property appears in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="c8a45-127">Оно отображает дату и время последнего обновления метаданных для источника данных.</span><span class="sxs-lookup"><span data-stu-id="c8a45-127">It displays the date and time the metadata for the data source was last updated.</span></span> <span data-ttu-id="c8a45-128">Это значение обновляется при развертывании решения.</span><span class="sxs-lookup"><span data-stu-id="c8a45-128">This value is updated when you deploy the solution.</span></span>|  
|<span data-ttu-id="c8a45-129">**Время ожидания запроса**</span><span class="sxs-lookup"><span data-stu-id="c8a45-129">**Query Timeout**</span></span>|<span data-ttu-id="c8a45-130">Указывает продолжительность ожидания запроса на соединение перед его удалением.</span><span class="sxs-lookup"><span data-stu-id="c8a45-130">Specifies how long a connection request will be attempted before it is dropped.</span></span><br /><br /> <span data-ttu-id="c8a45-131">Введите время ожидания запроса в следующем формате:</span><span class="sxs-lookup"><span data-stu-id="c8a45-131">Type the query timeout in the following format:</span></span><br /><br /> <span data-ttu-id="c8a45-132">*\<Hours>*:*\<Minutes>*:*\<Seconds>*</span><span class="sxs-lookup"><span data-stu-id="c8a45-132">*\<Hours>*:*\<Minutes>*:*\<Seconds>*</span></span><br /><br /> <span data-ttu-id="c8a45-133">Это свойство может быть переопределено свойством сервера `DatabaseConnectionPoolTimeoutConnection`.</span><span class="sxs-lookup"><span data-stu-id="c8a45-133">This property can be overruled by the `DatabaseConnectionPoolTimeoutConnection` server property.</span></span> <span data-ttu-id="c8a45-134">Если значение свойства сервера меньше, оно будет использовано вместо свойства **Время ожидания запроса**.</span><span class="sxs-lookup"><span data-stu-id="c8a45-134">If the server property is smaller, it will be used instead of **Query Timeout**.</span></span><br /><br /> <span data-ttu-id="c8a45-135">Дополнительные сведения о свойстве **Время ожидания запроса** см. в разделе <xref:Microsoft.AnalysisServices.DataSource.Timeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="c8a45-135">For more information about the **Query Timeout** property, see <xref:Microsoft.AnalysisServices.DataSource.Timeout%2A>.</span></span> <span data-ttu-id="c8a45-136">Дополнительные сведения о свойстве сервера см. в разделе [OLAP Properties](../server-properties/olap-properties.md).</span><span class="sxs-lookup"><span data-stu-id="c8a45-136">For more information about the server property, see [OLAP Properties](../server-properties/olap-properties.md).</span></span>|  
|<span data-ttu-id="c8a45-137">**Строка подключения**</span><span class="sxs-lookup"><span data-stu-id="c8a45-137">**Connection String**</span></span>|<span data-ttu-id="c8a45-138">Задает физическое расположение базы данных, которая предоставляет данные многомерной модели, а также поставщик данных, используемый для соединения.</span><span class="sxs-lookup"><span data-stu-id="c8a45-138">Specifies the physical location of a database that provides data to a multidimensional model, and the data provider used for the connection.</span></span> <span data-ttu-id="c8a45-139">Эти сведения направляются клиентской библиотеке, выполняющей запрос на соединение.</span><span class="sxs-lookup"><span data-stu-id="c8a45-139">This information is provided to a client library making the connection request.</span></span> <span data-ttu-id="c8a45-140">Поставщик определяет свойства, которые можно задать в строке подключения.</span><span class="sxs-lookup"><span data-stu-id="c8a45-140">The provider determines which properties can be set on the connection string.</span></span><br /><br /> <span data-ttu-id="c8a45-141">Строка подключения содержит сведения, указанные в диалоговом окне **Диспетчер соединений** .</span><span class="sxs-lookup"><span data-stu-id="c8a45-141">The connection string is built using the information you provide in the **Connection Manager** dialog box.</span></span> <span data-ttu-id="c8a45-142">Кроме того, просмотреть и изменить строку подключения можно в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] на странице свойств источника данных.</span><span class="sxs-lookup"><span data-stu-id="c8a45-142">You can also view and edit the connection string in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] in the data source property page.</span></span><br /><br /> <span data-ttu-id="c8a45-143">Для базы данных SQL Server строка подключения, которая содержит `user ID`, обозначает проверку подлинности базы данных; строка подключения, которая содержит `Integrated Security=SSPI`, обозначает проверку подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="c8a45-143">For a SQL Server database, a connection string that contains `user ID` indicates database authentication; a connection containing `Integrated Security=SSPI` indicates Windows authentication.</span></span><br /><br /> <span data-ttu-id="c8a45-144">Можно изменить имя сервера или базы данных, если база данных была перемещена в другое место.</span><span class="sxs-lookup"><span data-stu-id="c8a45-144">You can change the server or database name if the database was moved to a new location.</span></span> <span data-ttu-id="c8a45-145">Убедитесь в том, что указанные учетные данные для соединения соответствуют имени входа базы данных.</span><span class="sxs-lookup"><span data-stu-id="c8a45-145">Be sure to verify that the credentials currently specified for the connection are mapped to a database login.</span></span>|  
|<span data-ttu-id="c8a45-146">**Максимальное число подключений**</span><span class="sxs-lookup"><span data-stu-id="c8a45-146">**Maximum number of connections**</span></span>|<span data-ttu-id="c8a45-147">Указывает максимальное число соединений, разрешенных службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для подключения к источнику данных.</span><span class="sxs-lookup"><span data-stu-id="c8a45-147">Specifies the maximum number of connections allowed by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to connect to the data source.</span></span> <span data-ttu-id="c8a45-148">При поступлении большего количества запросов на соединение службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] будут ожидать возможности подключения.</span><span class="sxs-lookup"><span data-stu-id="c8a45-148">If more connections are needed, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will wait until a connection becomes available.</span></span> <span data-ttu-id="c8a45-149">Значение по умолчанию равно 10.</span><span class="sxs-lookup"><span data-stu-id="c8a45-149">The default is 10.</span></span> <span data-ttu-id="c8a45-150">Ограничение числа соединений защищает внешний источник данных от перегрузки запросами служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c8a45-150">Constraining the number of connections ensures that the external data source is not overloaded with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] requests.</span></span>|  
|<span data-ttu-id="c8a45-151">**Изоляция**</span><span class="sxs-lookup"><span data-stu-id="c8a45-151">**Isolation**</span></span>|<span data-ttu-id="c8a45-152">Задает поведение блокировки и управления версиями строк команд SQL, выполненных соединением с реляционной базой данных.</span><span class="sxs-lookup"><span data-stu-id="c8a45-152">Specifies the locking and row versioning behavior of SQL commands issued by a connection to a relational database.</span></span> <span data-ttu-id="c8a45-153">Допустимые значения — ReadCommitted или Snapshot.</span><span class="sxs-lookup"><span data-stu-id="c8a45-153">Valid values are ReadCommitted or Snapshot.</span></span> <span data-ttu-id="c8a45-154">Значение по умолчанию ReadCommitted, которое задает необходимость фиксации данных до их чтения и предотвращает чтение «грязных» данных.</span><span class="sxs-lookup"><span data-stu-id="c8a45-154">The default is ReadCommitted, which specifies that data must be committed before it will be read, preventing dirty reads.</span></span> <span data-ttu-id="c8a45-155">Значение Snapshot указывает, что выполняется считывание из моментального снимка зафиксированных ранее данных.</span><span class="sxs-lookup"><span data-stu-id="c8a45-155">Snapshot specifies that reads are from a snapshot of previously committed data.</span></span> <span data-ttu-id="c8a45-156">Дополнительные сведения об уровнях изоляции в SQL Server см. в разделе [SET TRANSACTION ISOLATION LEVEL (Transact-SQL)](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="c8a45-156">For more information about isolation level in SQL Server, see [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span>|  
|<span data-ttu-id="c8a45-157">**Управляемый поставщик**</span><span class="sxs-lookup"><span data-stu-id="c8a45-157">**Managed Provider**</span></span>|<span data-ttu-id="c8a45-158">Отображает имя управляемого поставщика, такого как System.Data.SqlClient или System.Data.OracleClient, если источник данных использует управляемый поставщик.</span><span class="sxs-lookup"><span data-stu-id="c8a45-158">Displays the name of the managed provider, such as System.Data.SqlClient or System.Data.OracleClient, if the data source uses a managed provider.</span></span><br /><br /> <span data-ttu-id="c8a45-159">Если источник данных не использует управляемый поставщик, то это свойство отображает пустую строку.</span><span class="sxs-lookup"><span data-stu-id="c8a45-159">If the data source does not use a managed provider, this property displays an empty string.</span></span><br /><br /> <span data-ttu-id="c8a45-160">Это свойство доступно только для чтения в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8a45-160">This property is read-only in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="c8a45-161">Чтобы изменить используемый для соединения поставщик, измените строку подключения.</span><span class="sxs-lookup"><span data-stu-id="c8a45-161">To change the provider used on the connection, edit the connection string.</span></span>|  
|<span data-ttu-id="c8a45-162">**Сведения об олицетворении**</span><span class="sxs-lookup"><span data-stu-id="c8a45-162">**Impersonation Info**</span></span>|<span data-ttu-id="c8a45-163">Задает идентификатор Windows, под которым запускаются службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] при соединении с источником данных, использующим проверку подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="c8a45-163">Specifies the Windows identity that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] runs under when connecting to a data source that uses Windows authentication.</span></span> <span data-ttu-id="c8a45-164">Параметры включают использование стандартного набора учетных данных Windows, учетную запись службы, идентификатор текущего пользователя или наследуемого параметра, который может потребоваться, если модель содержит несколько объектов источника данных.</span><span class="sxs-lookup"><span data-stu-id="c8a45-164">Options include using a predefined set of Windows credentials, the service account, the identity of the current user, or an inherit option that can be useful if your model contains multiple data source objects.</span></span> <span data-ttu-id="c8a45-165">Дополнительные сведения см. в разделе [Задание параметров олицетворения (многомерная база данных SSAS)](set-impersonation-options-ssas-multidimensional.md).</span><span class="sxs-lookup"><span data-stu-id="c8a45-165">For more information, see [Set Impersonation Options &#40;SSAS - Multidimensional&#41;](set-impersonation-options-ssas-multidimensional.md).</span></span><br /><br /> <span data-ttu-id="c8a45-166">В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]список допустимых значений содержит следующие:</span><span class="sxs-lookup"><span data-stu-id="c8a45-166">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], the valid values list includes these values:</span></span><br /><br /> <span data-ttu-id="c8a45-167">**ImpersonateAccount** (использовать конкретное имя пользователя Windows и пароль для подключения к источнику данных).</span><span class="sxs-lookup"><span data-stu-id="c8a45-167">**ImpersonateAccount** (use a specific Windows user name and password to connect to the data source).</span></span><br /><br /> <span data-ttu-id="c8a45-168">**ImpersonateServiceAccount** (использовать идентификатор безопасности учетной записи службы для подключения к источнику данных).</span><span class="sxs-lookup"><span data-stu-id="c8a45-168">**ImpersonateServiceAccount** (use the security identity of the service account to connect to the data source).</span></span> <span data-ttu-id="c8a45-169">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c8a45-169">This is the default value.</span></span><br /><br /> <span data-ttu-id="c8a45-170">**ImpersonateCurrentUser** (использовать идентификатор безопасности текущего пользователя для подключения к источнику данных).</span><span class="sxs-lookup"><span data-stu-id="c8a45-170">**ImpersonateCurrentUser** (use the security identity of the current user to connect to the data source).</span></span> <span data-ttu-id="c8a45-171">Этот параметр допустим только для запросов интеллектуального анализа данных, которые получают данные из внешнего хранилища или базы данных. Его нельзя выбрать для подключения к данным, используемым для обработки, загрузки или обратной записи в многомерной базе данных.</span><span class="sxs-lookup"><span data-stu-id="c8a45-171">This option is only valid for data mining queries that retrieve data from an external data warehouse or database; do not choose it for data connections used for processing, loading, or write-back in a multidimensional database.</span></span><br /><br /> <span data-ttu-id="c8a45-172">**Наследовать** или **по умолчанию** (используются параметры олицетворения базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , которая содержит этот объект источника данных).</span><span class="sxs-lookup"><span data-stu-id="c8a45-172">**Inherit** or **default** (use the impersonation settings of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that contains this data source object).</span></span> <span data-ttu-id="c8a45-173">Свойства базы данных включают параметры олицетворения.</span><span class="sxs-lookup"><span data-stu-id="c8a45-173">Database properties include impersonation options.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8a45-174">См. также:</span><span class="sxs-lookup"><span data-stu-id="c8a45-174">See Also</span></span>  
 <span data-ttu-id="c8a45-175">[Источники данных в многомерных моделях](data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="c8a45-175">[Data Sources in Multidimensional Models](data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="c8a45-176">Создание источника данных (многомерные службы SSAS)</span><span class="sxs-lookup"><span data-stu-id="c8a45-176">Create a Data Source &#40;SSAS Multidimensional&#41;</span></span>](create-a-data-source-ssas-multidimensional.md)  
  
  