---
title: Редактор преобразования «Экспорт столбца» (страница «Столбцы») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileextractortransformation.columns.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: b659a5c2-5509-4b5b-9c82-136c971d5c7f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 404b404e2328228049ae46fb1c3089b0b4089f0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657835"
---
# <a name="export-column-transformation-editor-columns-page"></a>Редактор преобразования «Экспорт столбца» (страница «Столбцы»)
  Страница **Столбцы** диалогового окна **Редактор преобразования «Экспорт столбца»** используется для задания столбцов в потоке данных, извлекаемых в файлы. Можно указать, будет ли преобразование «Экспорт столбца» добавлять данные в конец файла или перезаписывать существующий файл.  
  
 Дополнительные сведения о редакторе преобразований «Экспорт столбца» см. в разделе [Export Column Transformation](data-flow/transformations/export-column-transformation.md).  
  
## <a name="options"></a>Варианты  
 **Извлечь столбец**  
 Производится выбор из списка входных столбцов, содержащих текстовые данные или изображения. Все строки должны иметь определения для параметров **Извлечь столбец** и **Столбец пути к файлу**.  
  
 **Столбец пути к файлу**  
 Производится выбор из списка входных столбцов, содержащих пути к файлам и имена файлов. Все строки должны иметь определения для параметров **Извлечь столбец** и **Столбец пути к файлу**.  
  
 **Разрешить добавление**  
 Определяет, будет ли преобразование добавлять данные к существующим файлам. Значение по умолчанию — `false`.  
  
 **Принудительное усечение**  
 Определяет, будет ли преобразование удалять содержимое существующих файлов перед записью данных. Значение по умолчанию — `false`.  
  
 **Запись BOM**  
 Определяет, будет ли в файл записываться метка порядка следования байтов (BOM). Метка BOM записывается только в случае, если данные имеют тип данных `DT_NTEXT` или DT_WSTR и не присоединяются к существующему файлу данных.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор преобразования "Экспорт столбца" (страница "Вывод ошибок")](../../2014/integration-services/export-column-transformation-editor-error-output-page.md)  
  
  
