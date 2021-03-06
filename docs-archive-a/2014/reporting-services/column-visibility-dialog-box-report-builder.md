---
title: Диалоговое окно «Видимость столбца» (построитель отчетов) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10127"
ms.assetid: 0c030cab-6087-45a5-99f0-c7bd693f20a1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4c775734a4dbba2120a2af86e35a3872f5fff718
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730222"
---
# <a name="column-visibility-dialog-box-report-builder"></a>Диалоговое окно «Видимость столбцов» (построитель отчетов)
  Используйте диалоговое окно **Видимость столбца** , чтобы отобразить или скрыть выбранный столбец при первом запуске отчета либо назначить другой элемент отчета для переключения видимости столбца.  
  
## <a name="options"></a>Варианты  
 **При первоначальном запуске отчета**  
 Выберите параметр, определяющий, как элемент отчета отображается в отчете первоначально.  
  
 **Показать**  
 Выберите этот параметр, чтобы отобразить столбец.  
  
 **Скрыть**  
 Выберите этот параметр, чтобы скрыть столбец.  
  
 **Отображать или скрывать в зависимости от выражения**  
 Этот параметр используется для изменения исходной видимости с помощью выражения.  
  
 Введите выражение, результат вычисления которого имеет тип `Boolean` (при значении `True` элемент скрыт, а при значении `False` отображается). Нажмите кнопку Выражение (*FX*), чтобы изменить выражение.  
  
 **Отображение может переключаться этим элементом отчета**  
 Выберите данный параметр для вывода изображения переключателя, который позволяет пользователю отображать или скрывать данный столбец в средстве просмотра отчетов в формате HTML.  
  
 Введите или выберите имя текстового поля отчета для отображения изображения отчета, например, Textbox1. Выбранное текстовое поле должно быть в текущей области или области, содержащей этот элемент отчета. Например, чтобы включить видимость строк, связанных с дочерней группой, выберите текстовое поле в строке, связанной с родительской группой. Чтобы переключить видимость диаграммы, выберите текстовое поле в той же области, где находится эта диаграмма, например, в тексте отчета или в прямоугольнике.  
  
## <a name="see-also"></a>См. также:  
 [Примеры выражений (построитель отчетов и службы SSRS)](report-design/expression-examples-report-builder-and-ssrs.md)   
 [Добавление действия "развернуть" или "Свернуть" к элементу &#40;построитель отчетов и службам SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)   
 [Образы &#40;построитель отчетов и службы SSRS&#41;](report-design/images-report-builder-and-ssrs.md)   
 [Построитель отчетов справки по диалоговым окнам, панелям и мастерам](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Диалоговое окно "Свойства изображения" — "Общие" (построитель отчетов и службы SSRS)](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
