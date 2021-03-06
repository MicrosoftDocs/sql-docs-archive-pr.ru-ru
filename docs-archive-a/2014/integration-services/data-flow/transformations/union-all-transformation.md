---
title: Преобразование "Объединить все" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unionalltrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 942e4b90-9c41-4e9c-a6f3-80b3afe57f2f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eaaab1abf2587979e947cc1be24cbedf8f61b6e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667304"
---
# <a name="union-all-transformation"></a>преобразование «Объединить все»
  Преобразование «Объединить все» объединяет несколько входов в один выход. Например, выходы из пяти различных источников неструктурированных файлов можно сделать входами для преобразования «Объединить все» и объединить в один выход.  
  
## <a name="inputs-and-outputs"></a>Входы и выходы  
 Входы преобразования добавляются к выходу преобразования один за другим без переупорядочения строк. Если пакет требует сортировки выхода, то вместо преобразования «Объединить все» следует применять преобразование «Слияние».  
  
 Первый вход, подключенный к преобразованию «Объединить все» — это вход, из которого преобразование создает собственный выход. Входные столбцы, которые впоследствии будут подключены к преобразованию, сопоставляются со столбцами в выходе преобразования.  
  
 Для слияния входов нужно сопоставить входные и выходные столбцы. Необходимо, чтобы хотя бы один вход был сопоставлен каждому выходному столбцу. Сопоставление двух столбцов требует, чтобы метаданные этих столбцов совпадали. Например, сопоставленные столбцы должны относиться к одному и тому же типу данных.  
  
 Если сопоставленные столбцы содержат строковые данные, а длина выходного столбца меньше, чем длина входного, то выходной столбец автоматически увеличивается до нужной длины. Входные столбцы, не сопоставленные выходным столбцам, получают на выходных столбцах значения NULL.  
  
 Это преобразование имеет несколько входов и один выход. Вывод ошибок не поддерживается.  
  
## <a name="configuration-of-the-union-all-transformation"></a>Настройка преобразования «Объединить все»  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно установить в диалоговом окне **Редактор преобразования «Объединить все»** , см. в разделе [Union All Transformation Editor](../../union-all-transformation-editor.md).  
  
 Дополнительные сведения о свойствах, которые можно задать программно, см. в разделе [Common Properties](../../common-properties.md).  
  
 Дополнительные сведения о настройке свойств см. в следующих разделах.  
  
-   [Установление свойств компонента потока данных](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Выполнение слияния данных с помощью преобразования «Объединить все»](union-all-transformation.md)  
  
  
