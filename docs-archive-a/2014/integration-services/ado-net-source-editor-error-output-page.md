---
title: Редактор источника «ADO NET» (страница «вывод ошибок») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.erroroutput.f1
ms.assetid: 4dd9d129-a95c-4d3a-bbbf-e84a39089950
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9ee480caa8764d70b52b25a416f200f353d30c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740256"
---
# <a name="ado-net-source-editor-error-output-page"></a>Редактор источника данных «ADO.NET» (страница «Вывод ошибок»)
  Страница **Вывод ошибок** диалогового окна **Редактор источника «ADO.NET»** используется для выбора параметров обработки ошибок, а также для установки свойств выходных столбцов ошибок.  
  
 Дополнительные сведения об источниках данных «ADO.NET» см. в разделе [ADO NET Source](data-flow/ado-net-source.md).  
  
 **Открытие страницы «Вывод ошибок»**  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий источник данных «ADO.NET».  
  
2.  На вкладке **Поток данных** дважды щелкните источник данных "ADO.NET".  
  
3.  В окне **Редактор источника «ADO.NET»** нажмите кнопку **Вывод ошибок**.  
  
## <a name="options"></a>Параметры  
 **Ввод-вывод**  
 Просмотр имени источника данных.  
  
 **Столбец**  
 Просмотрите внешние (исходные) столбцы, выбранные на странице **Диспетчер подключений** диалогового окна **Редактор источника "ADO.NET"** .  
  
 **Error**  
 Задайте действие, которое необходимо выполнить при возникновении ошибки: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
 **См. также:** [Обработка ошибок в данных](data-flow/error-handling-in-data.md)  
  
 **Усечение**  
 Укажите, что нужно сделать при усечении: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
 **Описание**  
 Просмотреть описание ошибки.  
  
 **Присвоить указанное значение выбранным ячейкам**  
 Укажите действие, которое необходимо применить ко всем выбранным ячейкам при возникновении ошибки или усечения: пропустить ошибку, перенаправить строку или вызвать сбой компонента.  
  
 **Применить**  
 Применить параметр обработки ошибок к выбранным ячейкам.  
  
## <a name="see-also"></a>См. также:  
 [Редактор источника «ADO NET» &#40;«диспетчер соединений»&#41;](../../2014/integration-services/ado-net-source-editor-connection-manager-page.md)   
 [Редактор источника «ADO NET» &#40;столбцы&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md)   
 [Диспетчер подключений ADO.NET](connection-manager/ado-net-connection-manager.md)  
  
  
