---
title: Преобразование "Многоадресная доставка" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multicasttrans.f1
helpviewer_keywords:
- multiple outputs
- Multicast transformation
- datasets [Integration Services], multiple outputs
- multiple transformations
ms.assetid: 32194784-1684-40cd-9f91-1aba4d8360d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7b5c0a38c966c89f426a213f302b45c390b77cfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752324"
---
# <a name="multicast-transformation"></a>преобразование «Многоадресная доставка»
  Преобразование «Многоадресная доставка» распределяет данные на входе на один или более выходов. Это преобразование схоже с преобразованием «Условное разбиение». Оба вида преобразований направляют данные на входе на несколько выходов. Их различие состоит в том, что преобразование «Многоадресная доставка» направляет каждую строку на все выходы, а преобразование «Условное разбиение» направляет одну строку на один выход. Дополнительные сведения см. в статье [Conditional Split Transformation](conditional-split-transformation.md).  
  
 Можно производить настройку преобразования «Многоадресная доставка» путем добавления выходов.  
  
 Используя преобразование «Многоадресная доставка», пакет может создавать логические копии данных. Эта возможность полезна, если пакету необходимо применить несколько наборов преобразований к одним и тем же данным. Например, одна копия данных статистически обрабатывается и в назначение загружается только сводная информация, а в другую копию данных перед загрузкой в назначение добавляются значения уточняющего запроса и производные столбцы.  
  
 Это преобразование имеет один вход и несколько выходов. Вывод ошибок не поддерживается.  
  
## <a name="configuration-of-the-multicast-transformation"></a>Настройка преобразования «Многоадресная доставка»  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
 Сведения о свойствах, которые можно установить в диалоговом окне **Редактор преобразования «Многоадресная доставка»** , см. в разделе [Multicast Transformation Editor](../../multicast-transformation-editor.md).  
  
 Сведения о свойствах, которые можно задать программно, см. в разделе [Common Properties](../../common-properties.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о настройке свойств компонента см. в разделе [Установление свойств компонента потока данных](../set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>См. также:  
 [Поток данных](../data-flow.md)   
 [Преобразования служб Integration Services](integration-services-transformations.md)  
  
  
