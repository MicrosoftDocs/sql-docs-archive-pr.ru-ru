---
title: Редактор источника «ODBC» (страница «Столбцы») | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.columns.f1
ms.assetid: 565984eb-8318-4be7-bebc-262209cf5065
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a11ab6a86978366d07fbe63362f1702310b5d89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734358"
---
# <a name="odbc-source-editor-columns-page"></a>Редактор источника «ODBC» (страница «Столбцы»)
  Страница **Столбцы** диалогового окна **Редактор источника ODBC** используется для сопоставления выходного столбца с каждым внешним (исходным) столбцом.  
  
 Дополнительные сведения об источнике ODBC см. в разделе [ODBC Source](data-flow/odbc-source.md).  
  
## <a name="task-list"></a>Список задач  
 **Открытие страницы «Столбцы» редактора источника ODBC**  
  
1.  В среде [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]откройте пакет служб [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] , содержащий источник ODBC.  
  
2.  На вкладке **Поток данных** дважды щелкните источник ODBC.  
  
3.  В окне **Редактор источника ODBC**нажмите кнопку **Столбцы**.  
  
## <a name="options"></a>Параметры  
  
### <a name="available-external-columns"></a>Доступные внешние столбцы  
 Список доступных внешних столбцов источника данных. В этой таблице нельзя добавлять или удалять столбцы. Выберите используемые столбцы источника. Выбранные столбцы добавляются в список **Внешний столбец** в порядке выбора.  
  
 Чтобы выбрать все столбцы, установите флажок **Выделить все** .  
  
### <a name="external-column"></a>Внешний столбец  
 Представление внешних (исходных) столбцов в порядке, заданном при настройке компонентов, которые обрабатывают данные из источника ODBC.  
  
### <a name="output-column"></a>Выходной столбец  
 Введите уникальное имя для каждого выходного столбца. По умолчанию используется имя выбранного внешнего (исходного) столбца, однако можно выбрать любое уникальное описательное имя. Введенное имя отображается в конструкторе служб SSIS.  
  
## <a name="see-also"></a>См. также:  
 [Редактор источника ODBC &#40;страница "Диспетчер соединений"&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md)   
 [Редактор источника ODBC (страница "Вывод ошибок")](../../2014/integration-services/odbc-source-editor-error-output-page.md)  
  
  
