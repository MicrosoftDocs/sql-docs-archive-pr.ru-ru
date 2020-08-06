---
title: Роли (табличные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e547382a-c064-4bc6-818c-5127890af334
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0293bf6d9ac4ee71df34ece92672311ca9f90436
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727369"
---
# <a name="roles-ssas-tabular"></a>Роли (табличные службы SSAS)
  В табличной модели роли определяют разрешения члена для модели. В каждой роли имеются члены, различаемые по имени пользователя или группе Windows, а также разрешениям (чтение, обработка, администрирование). Члены роли могут выполнять с моделью действия, заданные в разрешении роли. Роли, которым заданы разрешения на чтение, также могут обеспечивать дополнительную защиту на уровне строк с помощью фильтров уровня строк.  
  
> [!IMPORTANT]  
>  Чтобы пользователь мог подключиться к развернутой модели с помощью клиентского приложения для создания отчетов или анализа данных, необходимо создать хотя бы одну роль с разрешением на чтение, членом которой должен быть этот пользователь.  
  
 Сведения в этом разделе предназначены для создателей табличных моделей, определяющих роли с помощью диалогового окна «Диспетчер моделей» в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Роли, определенные при создании модели, применяются к базе данных рабочей области модели. После развертывания базы данных модели администраторы этой базы данных могут управлять (добавлять, изменять, удалять) членами роли с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Сведения об управлении членами ролей в развернутой базе данных модели см. в разделе [Роли табличных моделей (табличные службы SSAS)](tabular-model-roles-ssas-tabular.md).  
  
 Раздел [Табличное моделирование (учебник по Adventure Works)](../tabular-modeling-adventure-works-tutorial.md) содержит дополнительные сведения об использовании этой функции и обучающие материалы.  
  
 Разделы данной темы:  
  
-   [Основные сведения о ролях](#bkmk_underst)  
  
-   [Разрешения](#bkmk_permissions)  
  
-   [Фильтры строк](#bkmk_rowfliters)  
  
-   [Проверка ролей](#bkmk_testroles)  
  
-   [Связанные задачи](#bkmk_rt)  
  
##  <a name="understanding-roles"></a><a name="bkmk_underst"></a>Основные сведения о ролях  
 Роли используются в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для управления безопасностью [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и данными. В службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]существует два типа ролей.  
  
-   Роль сервера — фиксированная роль, предоставляющая права администратора для доступа к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
-   Роли базы данных — роли, определенные авторами моделей и администраторами для контроля доступа к шаблонам базы данных и данным пользователями, которые не являются администраторами.  
  
 Роли, определенные для табличной модели, являются ролями базы данных. Иными словами, членами этих ролей являются пользователи и группы Windows, обладающие определенными разрешениями. Эти разрешения определяют действия, которые члены ролей могут совершать в шаблоне базы данных. Роль базы данных создается как отдельный объект в базе данных и применяется только к базе данных, в которой она создана. Пользователи и/или группы Windows включаются в роль автором модели, который по умолчанию обладает разрешениями администратора на сервере базы данных рабочей области (или администратором, если речь идет о развернутой модели).  
  
 В табличных моделях роли можно детализировать с помощью фильтров строк. Фильтры строк используют выражения DAX для определения строк в таблице и любых строк на стороне связи «многие», которые может просматривать пользователь. Фильтры строк, в которых используются выражения DAX, могут быть определены только для разрешений на чтение, чтение и обработку. Дополнительные сведения см. в подразделе [фильтры строк](#bkmk_rowfliters) далее в этой статье.  
  
 По умолчанию при создании нового проекта табличной модели в нем нет никаких ролей. Роли можно определять с помощью диалогового окна «Диспетчер ролей» в среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. При определении ролей во время создания модели они применяются к базе данных рабочей области модели. Когда модель развернута, те же роли применяются к развернутой модели. После развертывания модели члены роли сервера (администратор служб[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ) и администраторы базы данных с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]могут управлять ролями, связанными в этой моделью, а также членами, связанными с каждой ролью.  
  
> [!NOTE]  
>  В ролях, определенных для модели в режиме DirectQuery, нельзя использовать фильтры строк, однако определенные для каждой роли разрешения продолжают действовать.  
  
##  <a name="permissions"></a><a name="bkmk_permissions"></a> Permissions  
 Каждая роль определяет одно разрешение для базы данных (за исключением объединенного разрешения на чтение и обработку). По умолчанию новая роль имеет разрешение «Нет». То есть члены этой роли, добавленные с разрешением «Нет», не смогут изменять базу данных, выполнять операции по обработке, запрашивать данные и даже видеть базу данных, пока им не будет предоставлено другое разрешение.  
  
 Пользователь или группа Windows может быть членом любого числа ролей, при этом каждая роль может обладать разными разрешениями. Когда пользователь является членом нескольких ролей, он обладает всеми разрешениями, определенными для каждой из них. Например, если пользователь является членом роли с разрешением на чтение, а также роли с разрешением «Нет», этот пользователь будет обладать разрешением на чтение.  
  
 Каждой роли можно назначить одно из следующих разрешений.  
  
|Разрешения|Описание|Фильтры строк с DAX|  
|-----------------|-----------------|----------------------------|  
|Нет|Члены не могут вносить изменения в схему шаблона базы данных, а также просматривать данные.|Фильтры строк не применяются. Пользователи в этой роли не могут видеть данные|  
|Чтение|Члены могут запрашивать данные (с учетом фильтров строк), но не могут видеть шаблон базы данных в среде SSMS, не могут вносить изменения в схему шаблона базы данных, и пользователь не может обработать модель.|Фильтры строк могут применяться. Пользователи могут видеть только данные, указанные в формуле DAX фильтра строк.|  
|Чтение и обработка|Члены могут просматривать данные (с учетом фильтров уровня строк) и выполнять операции по обработке, запуская скрипты или пакеты, содержащие команду обработки, но не могут вносить изменения в базу данных. Не могут просматривать базу данных модели в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|Фильтры строк могут применяться. Выполнять запросы можно только к данным, указанным в формуле DAX фильтра строк.|  
|Процесс|Члены могут выполнять операции по обработке путем запуска скриптов или пакетов, содержащих команды обработки. Не могут изменять схему шаблона базы данных. Запросы к данным невозможны. Запросы к шаблону базы данных в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]невозможны.|Фильтры строк не применяются. Члены этой роли не могут запрашивать данные|  
|Администратор|Члены могут вносить изменения в схему базы данных модели и запрашивать любые данные в конструкторе модели, клиенте отчетов и среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|Фильтры строк не применяются. Члены этой роли могут запрашивать любые данные|  
  
##  <a name="row-filters"></a><a name="bkmk_rowfliters"></a>Фильтры строк  
 Фильтры строк определяют, какие строки в таблице могут запросить участники определенной роли. Фильтры строк для каждой таблицы модели определяются с помощью формул DAX.  
  
 Они могут быть определены только для ролей с разрешениями "Чтение" и "Чтение и обработка". По умолчанию, если фильтр строк не задан для какой-то таблицы, члены роли с разрешением на чтение или на чтение и обработку могут просматривать все строки таблицы, если нет перекрестной фильтрации из другой таблицы.  
  
 Если для таблицы задан фильтр строк, формула DAX, результат вычисления которой должен быть равен TRUE или FALSE, определяет строки, которые могут запрашиваться членами этой роли. Строки, не включенные в формулу DAX, запрашиваться не могут. Например, для членов роли Sales таблица Customers со следующим выражением фильтров строк *= Customers [Country] = "USA"*, участники роли "продажи", смогут видеть только клиентов в США.  
  
 Фильтры строк применяются к указанным, а также к связанным строкам. Когда таблица содержит несколько связей, фильтры применяют защиту к связи, которая является активной. Фильтры строк пересекаются с другими фильтрами строк, определенными в связанных таблицах, например:  
  
|Таблица|Выражение DAX|  
|-----------|--------------------|  
|Регион|=Region[Country]="USA"|  
|Категория продукта|=ProductCategory[Name]="Bicycles"|  
|Транзакции|=Transactions[Year]=2008|  
  
 В результате применения этих разрешений к таблице Transactions члены роли смогут запрашивать только строки данных, в которых клиенты находятся в США, категория продуктов — велосипеды, а год — 2008. Пользователи не смогут запрашивать сделки, совершенные не в США, не по велосипедам и не в 2008 году, если они не являются членами другой роли, которая предоставляет такие разрешения.  
  
 Вы можете использовать фильтр *=FALSE()*, чтобы запретить доступ ко всем строкам для всей таблицы.  
  
### <a name="dynamic-security"></a>Динамическая безопасность  
 Динамическая безопасность позволяет задать защиту на уровне строк с учетом имени пользователя, который находится в системе в данный момент, или свойства CustomData из строки подключения. Для реализации динамической безопасности в модель необходимо включить таблицу со значениями имен входа (имена пользователей Windows) для пользователей, а также поле, которое можно использовать для определения конкретных разрешений, например таблицу dimEmployees с идентификаторами входа (домен или имя пользователя) и значением подразделения для каждого сотрудника.  
  
 Для реализации динамической безопасности можно использовать следующие функции в формуле DAX для получения имени пользователя, который находится в системе в данный момент, или свойства CustomData из строки подключения.  
  
|Функция|Описание|  
|--------------|-----------------|  
|[Функция USERNAME &#40;DAX&#41;](/dax/username-function-dax)|Возвращает значение вида «домен\имя пользователя» для пользователя, который находится в системе в настоящий момент.|  
|[CUSTOMDATA &#40;DAX&#41;](/dax/customdata-function-dax)|Возвращает свойство CustomData в строке подключения.|  
  
 Функция LOOKUPVALUE позволяет возвращать значения для столбца, в котором имя пользователя Windows соответствует имени пользователя, возвращенного функцией USERNAME, или строке, возвращенной функцией CustomData. После этого можно ограничить запросы строками, в которых значения, возвращенные функцией LOOKUPVALUE, совпадают со значениями в этой же или связанной таблице.  
  
 Пример использования формулы  
  
 `='dimDepartmentGroup'[DepartmentGroupId]=LOOKUPVALUE('dimEmployees'[DepartmentGroupId], 'dimEmployees'[LoginId], USERNAME(), 'dimEmployees'[LoginId], 'dimDepartmentGroup'[DepartmentGroupId])`  
  
 Функция LOOKUPVALUE возвращает значения для столбца dimEmployees[DepartmentId], где значение dimEmployees[LoginId] равно идентификатору входа текущего пользователя, возвращенному функцией USERNAME, а значения для dimEmployees[DepartmentId] равны значениям для dimDepartmentGroup[DepartmentId]. Значения в поле DepartmentId, возвращенные функцией LOOKUPVALUE, используются для ограничения строк, запрашиваемых в таблице dimDepartment и любых таблицах, связанных по столбцу DepartmentId. Возвращаются только строки, столбец DepartmentId в которых входит в список значений DepartmentId, возвращенных функцией LOOKUPVALUE.  
  
 **dimEmployees**  
  
|LastName|FirstName|LoginID|DepartmentName|DepartmentId|  
|--------------|---------------|-------------|--------------------|------------------|  
|Коричневый|Кевин|Adventure-works\kevin0|Marketing|7|  
|Bradley|David|Adventure-works\david0|Marketing|7|  
|Dobney|JoLynn|Adventure-works\JoLynn0|Рабочие|4|  
|Baretto DeMattos|Paula|Adventure-works\Paula0|Human Resources|2|  
  
 **dimDepartment**  
  
|DepartmentId|DepartmentName|  
|------------------|--------------------|  
|1|Корпоративный|  
|2|Executive General and Administration|  
|3|Inventory Management|  
|4|Производство|  
|5|Контроль качества|  
|6|Научные исследования и разработки|  
|7|Сбыт и маркетинг|  
  
##  <a name="testing-roles"></a><a name="bkmk_testroles"></a>Тестирование ролей  
 При создании проекта модели с помощью функции «Анализ в Excel» можно протестировать эффективность заданных ролей. Если в меню **Модель** конструктора моделей выбрать команду **Анализ в Excel**, еще до открытия окна Excel появляется диалоговое окно **Выбор учетных данных и перспективы** . В этом диалоговом окне можно указать текущее имя пользователя, другое имя пользователя, роль и перспективу, которые будут использоваться для подключения к базе данных рабочей области модели в качестве источника данных. Дополнительные сведения см. далее в подразделе [Анализ в Excel (табличные службы SSAS)](analyze-in-excel-ssas-tabular.md).  
  
##  <a name="related-tasks"></a><a name="bkmk_rt"></a> Связанные задачи  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Создание ролей и управление ими (табличные службы SSAS)](create-and-manage-roles-ssas-tabular.md)|Задачи в этом разделе демонстрируют создание ролей и управление ими с помощью диалогового окна **Диспетчер ролей** .|  
  
## <a name="see-also"></a>См. также:  
 [Перспективы &#40;табличные&#41;SSAS](perspectives-ssas-tabular.md)   
 [Анализ в Excel &#40;табличные&#41;SSAS](analyze-in-excel-ssas-tabular.md)   
 [Функция USERNAME &#40;DAX&#41;](/dax/username-function-dax)   
 [Функция LOOKUPVALUE &#40;DAX&#41;](/dax/lookupvalue-function-dax)   
 [CUSTOMDATA &#40;DAX&#41;](/dax/customdata-function-dax)  
  
  