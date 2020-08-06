---
title: Источник OData | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ODATASOURCE.F1
ms.assetid: cc9003c9-638e-432b-867e-e949d50cec90
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 98b14ef034597f6098f70386ca41c1b90be86500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750036"
---
# <a name="odata-source"></a>Источник OData
  Компонент источника OData используется в пакете служб SSIS для получения данных от служб OData. Компонент поддерживает протоколы OData v2 и v3, а также форматы данных ATOM и JSON.  
  
> [!NOTE]  
>  Источник OData можно использовать для чтения данных из списков SharePoint. Чтобы просмотреть все списки на сервере SharePoint, используйте следующий URL-адрес: http:// \<server> /_vti_bin/листдата.СВК. Дополнительные сведения о соглашениях об URL-адресах SharePoint см. в разделе [Интерфейс REST SharePoint Foundation](https://msdn.microsoft.com/library/ff521587.aspx).  
  
## <a name="odata-format"></a>Формат OData  
 Большинство служб OData возвращают результаты в различных форматах. Можно указать формат результирующего набора с помощью параметра $format запроса. Такие форматы, как JSON и JSON Light, более эффективны, чем ATOM/XML, и способны обеспечить более высокую производительность при передаче больших объемов данных. В следующей таблице отображаются результаты типовых тестов. Как видно, выигрыш в производительности при переключении с ATOM на JSON составил 30–53 и 67 % при переходе с ATOM на новый формат JSON Light (доступный в WCF Data Services 5.1).  
  
|||||  
|-|-|-|-|  
|Строки|ATOM|JSON|JSON (Light)|  
|10000|113 секунд|74 секунды|68 секунд|  
|1000000|1110 секунд|853 секунды|665 с|  
  
> [!NOTE]  
>  Источник OData служб SSIS использует ODataLib 5.5.0 для синтаксического анализа каналов OData и может считывать все форматы, поддерживаемые этой библиотекой.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Установка и удаление компонента источника OData](../install-and-uninstall-odata-source-component.md)  
  
-   [Учебник. Использование источника OData &#91;SSIS&#93;](tutorial-using-the-odata-source.md)  
  
-   [Изменение запроса источника OData во время выполнения](modify-odata-source-query-at-runtime.md)  
  
-   [Редактор источника OData (страница "Подключение")](../odata-source-editor-connection-page.md)  
  
-   [Редактор источника OData (страница "Столбцы")](../odata-source-editor-columns-page.md)  
  
-   [Редактор источника OData (страница "Вывод ошибок")](../odata-source-editor-error-output-page.md)  
  
-   [Свойства источника OData](odata-source-properties.md)  
  
## <a name="see-also"></a>См. также:  
 [Диспетчер соединений OData](../connection-manager/odata-connection-manager.md)  
  
  
