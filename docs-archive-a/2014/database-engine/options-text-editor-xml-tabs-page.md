---
title: 'Параметры (текстовый редактор: XML: Страница «Табуляция») | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Tabs
ms.assetid: 13bf5f8c-aba3-4c05-b8bb-eb475797c9bd
author: rothja
ms.author: jroth
ms.openlocfilehash: 3047d6c05ffb88d07a4bf2e5b1d4143412046c04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727321"
---
# <a name="options-text-editorxmltabs-page"></a>Параметры (текстовый редактор: XML: страница "Табуляция")
  Это диалоговое окно используется для изменения режима табуляции в редакторе XML, который используется для изменения XML-документов. Для вывода этих параметров выберите пункт **Параметры** в меню **Сервис** , раскройте узел **Текстовый редактор** , раскройте узел **XML** и щелкните **Табуляции**.  
  
## <a name="setting-options-in-multiple-locations"></a>Настройка параметров в нескольких местах  
 Параметры редактора XML можно также задать в диалоговом окне **Все языки/Общие** . Если диалоговое окно **Все языки** используется для задания различных параметров для других редакторов среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , таких как DMX или MDX, необходимо сбросить параметры редактора XML с помощью этого окна.  
  
## <a name="indenting"></a>Отступы  
 **None**  
 Если данный параметр выбран, при нажатии клавиши ВВОД отступ у новой строки создаваться не будет. Курсор помещается в первый столбец новой строки.  
  
 **Заблокировать**  
 Если выбран данный режим, то новая строка, создаваемая при нажатии клавиши ВВОД, будет автоматически перемещена на такое же расстояние, что и предыдущая.  
  
 **Структура**  
 Если выбран этот параметр, после нажатия клавиши ВВОД новая строка располагается в соответствии с контекстом. Например при вводе открывающейся скобки ({) соответствующие строки автоматически сдвигаются на дополнительную позицию табулятора. Соответствующая закрывающаяся скобка (}) выравнивается с открывающейся.  
  
## <a name="tabs"></a>Вкладки  
 **Размер интервала табуляции**  
 Устанавливает расстояние в пробелах между табуляторами. По умолчанию этот параметр равен четырем пробелам.  
  
 **Размер отступа**  
 Устанавливается размер автоматического отступа в пробелах. По умолчанию этот параметр равен четырем пробелам. Символы табуляции, символы пробела или оба этих вида символов будут вставлены для заполнения указанного размера.  
  
 **Вставлять пробелы**  
 При выборе этого параметра операции отступа вставляют только пробелы, а не символы табуляции. Например, если для параметра **Размер отступа** задано значение 5, то при каждом нажатии клавиши TAB или нажатии кнопки **увеличить отступ** на панели инструментов в главном окне вставляются пять символов пробела [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] .  
  
 **Сохранять знаки табуляции**  
 При выборе этого параметра операции отступа вставляют максимально возможное количество символов табуляции. Каждый символ табуляции включает количество пробелов, указанное в параметре **Размер интервала табуляции**. Если параметр **Размер отступа** не кратен точно параметру **Размер интервала табуляции**, для заполнения остатка вставляются пробелы.  
  
  
