---
title: Указание строки подключения (SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.speconnstring.f1
ms.assetid: 3f89b55b-2659-4e9f-a3ad-ab9a23b6942d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9333c239504a79184e08776acb3f1d845f06cc4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736854"
---
# <a name="specify-a-connection-string-ssas"></a><span data-ttu-id="f66d1-102">Указание строки подключения (SSAS)</span><span class="sxs-lookup"><span data-stu-id="f66d1-102">Specify a connection string (SSAS)</span></span>
  <span data-ttu-id="f66d1-103">На этой странице **мастера импорта таблиц** указывается строка подключения для подключения к источнику данных OLE DB или ODBC.</span><span class="sxs-lookup"><span data-stu-id="f66d1-103">This page of the **Table Import Wizard** enables you to specify a connection string to connect to an OLE DB or ODBC data source.</span></span> <span data-ttu-id="f66d1-104">Для доступа к мастеру из [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]выберите пункт **Импорт из источника данных** в меню **Модель**.</span><span class="sxs-lookup"><span data-stu-id="f66d1-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="f66d1-105">Для соединения с источником данных на компьютере должен быть установлен соответствующий поставщик.</span><span class="sxs-lookup"><span data-stu-id="f66d1-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span> <span data-ttu-id="f66d1-106">Дополнительные сведения о поддерживаемых источниках данных и поставщиках см. в разделе [Поддерживаемые источники данных (табличные службы SSAS)](tabular-models/data-sources-supported-ssas-tabular.md).</span><span class="sxs-lookup"><span data-stu-id="f66d1-106">For more information about supported data sources and providers, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="f66d1-107">Список элементов пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="f66d1-107">UI element list</span></span>  
 <span data-ttu-id="f66d1-108">**Понятное имя для соединения**</span><span class="sxs-lookup"><span data-stu-id="f66d1-108">**Friendly name for this connection**</span></span>  
 <span data-ttu-id="f66d1-109">Введите уникальное имя для соединения с источником данных.</span><span class="sxs-lookup"><span data-stu-id="f66d1-109">Type a unique name for this data source connection.</span></span> <span data-ttu-id="f66d1-110">Это поле является обязательным.</span><span class="sxs-lookup"><span data-stu-id="f66d1-110">This is a required field.</span></span>  
  
 <span data-ttu-id="f66d1-111">**Строка подключения**</span><span class="sxs-lookup"><span data-stu-id="f66d1-111">**Connection String**</span></span>  
 <span data-ttu-id="f66d1-112">Введите строку соединения для соединения с источником данных OLE DB или ODBC.</span><span class="sxs-lookup"><span data-stu-id="f66d1-112">Type a connection string to connect to an OLE DB or ODBC data source.</span></span>  
  
 <span data-ttu-id="f66d1-113">**Сборка**</span><span class="sxs-lookup"><span data-stu-id="f66d1-113">**Build**</span></span>  
 <span data-ttu-id="f66d1-114">Укажите свойства строки соединения в диалоговом окне **Свойства канала передачи данных** .</span><span class="sxs-lookup"><span data-stu-id="f66d1-114">Specify the properties for a connection string by using the **Data Link Properties** dialog box.</span></span> <span data-ttu-id="f66d1-115">Дополнительные сведения см. в справке канала передачи данных Майкрософт, доступной в этом диалоговом окне.</span><span class="sxs-lookup"><span data-stu-id="f66d1-115">For more information, see the Microsoft Data Link Help, which is available from that dialog box.</span></span>  
  
 <span data-ttu-id="f66d1-116">**Проверка соединения**</span><span class="sxs-lookup"><span data-stu-id="f66d1-116">**Test Connection**</span></span>  
 <span data-ttu-id="f66d1-117">Установите соединение с источником данных с использованием заданной строки соединения.</span><span class="sxs-lookup"><span data-stu-id="f66d1-117">Attempt to establish a connection to the data source using the specified connection string.</span></span> <span data-ttu-id="f66d1-118">Появится сообщение об успешном или неуспешном соединении.</span><span class="sxs-lookup"><span data-stu-id="f66d1-118">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
