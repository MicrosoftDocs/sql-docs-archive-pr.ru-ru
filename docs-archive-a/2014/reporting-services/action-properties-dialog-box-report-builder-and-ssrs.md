---
title: Диалоговое окно «Свойства действия» (построитель отчетов и службы SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.action.f1
- "10413"
- "10504"
- sql12.rtp.rptdesigner.calculatedseriesproperties.action.f1
- sql12.rtp.rptdesigner.pictureproperties.action.f1
- sql12.rtp.rptdesigner.actionproperties.f1
- sql12.rtp.rptdesigner.charttitleproperties.action.f1
- "10133"
- "10052"
- "10147"
- sql12.rtp.rptdesigner.chartproperties.action.f1
- "10122"
- sql12.rtp.rptdesigner.serieslabelproperties.action.f1
- sql12.rtp.rptdesigner.textboxproperties.action.f1
- "10162"
- "10168"
- sql12.rtp.rptdesigner.textproperties.action.f1
- sql12.rtp.rptdesigner.placeholderproperties.action.f1
- "10250"
- "10129"
- "10244"
- sql12.rtp.rptdesigner.seriesproperties.action.f1
ms.assetid: 2c5d915b-4f97-42cf-b8f1-49ca3ff3d0f9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77b51af0763010676b95fcedb433ab963fc7fcdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665880"
---
# <a name="action-properties-dialog-box-report-builder-and-ssrs"></a>Диалоговое окно «Свойства действия» (построитель отчетов и службы SSRS)
  С помощью диалогового окна **Действие** можно включить параметры гиперссылок для диаграммы, датчика и элементов карты, поддерживающих ссылки. Определите действие, чтобы дать пользователю возможность щелкнуть отчет и перейти по URL-адресу к другому отчету на том же сервере отчетов или на сайте SharePoint, интегрированном с сервером отчетов, или к другому расположению в текущем отчете.  
  
## <a name="options"></a>Варианты  
 **Включить как действие**  
 Выберите параметр, указывающий на действие, которое будет выполняться при щелчке изображения мышью.  
  
 **None**  
 Выберите этот параметр, чтобы указать на отсутствие у элемента действия.  
  
 **Перейти к отчету**  
 Выберите этот параметр, чтобы создать ссылку на детализированный отчет, расположенный на сервере отчетов. После выбора пункта **Перейти к отчету**появляются следующие дополнительные параметры.  
  
 **Выберите отчет**  
 Введите или выберите имя отчета, который будет использован в качестве детализированного. Детализированные отчеты должны располагаться на том же сервере, что и данный отчет.  
  
 Для отчета, который опубликован на сервере отчетов, настроенном для работы в собственном режиме, используется полный или относительный путь без расширения имени файла. Если отчет находится в той же папке, что и текущий отчет, указывается только имя отчета. Если отчет находится в другой папке на том же сервере отчетов, используйте относительный путь к отчету. Относительный путь к отчету начинается с текущей папки и проходит до иерархии папок, например ../Folder2/Report1. Полный путь начинается с /, домашней папки. Например, /Reports/Report1.  
  
 Для отчета, который опубликован на сервере отчетов, настроенном для работы в режиме интеграции с SharePoint, используется полный URL-адрес, включая расширение имени файла (RDL). Например, http:// *\<SharePointservername>/\<site>* /Documents/Report1.RDL. Относительные пути не поддерживаются.  
  
 Дополнительные сведения см. в разделе [Указание путей к внешним элементам (построитель отчетов и службы SSRS)](report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md) в [документации по построителю отчетов](https://go.microsoft.com/fwlink/?LinkId=154494) на сайте msdn.microsoft.com.  
  
 **Использовать эти параметры при выполнении отчета**  
 Добавьте список параметров для передачи детализированному отчету. Имена параметров должны совпадать с параметрами, определенными для целевого отчета. Добавление и удаление параметров производится при помощи кнопок **Добавить** и **Удалить** , а изменение их порядка в списке — стрелками вверх и вниз.  
  
 **Добавление**  
 Добавить параметр для передачи детализированному отчету.  
  
 **Удалить**  
 Удалить параметр детализированного отчета.  
  
 **Стрелка вверх**  
 Переместить параметр в списке вверх.  
  
 **Стрелка вниз**  
 Переместить параметр в списке вниз.  
  
 **имя**;  
 Введите текст, представляющий имя параметра, определенного в детализированном отчете.  
  
 **Значение**  
 Введите или выберите значение именованного параметра для передачи детализированному отчету. Нажмите кнопку **выражение** (*FX*), чтобы изменить выражение.  
  
 **Пропустить**  
 Выберите, чтобы при запуске этот параметр не обрабатывался. По умолчанию этот флажок снят и неактивен. Чтобы установить этот флажок, нажмите кнопку **Выражение** (*fx*) и введите **True** или создайте выражение. Флажок устанавливается при нажатии кнопки **ОК** в диалоговом окне **Выражение** .  
  
 **Перейти к закладке**  
 Выберите этот параметр, чтобы задать ссылку на закладку в текущем отчете. После выбора **Перейти к закладке**появляются следующие дополнительные параметры.  
  
 **Выберите закладку**  
 Введите или выберите идентификатор закладки в отчете, к которой пользователь переходит по ссылке. Чтобы изменить выражение, нажмите кнопку Выражение (**fx**). Идентификатор закладки может быть статическим идентификатором или выражением, результатом которого является идентификатор закладки. Это выражение может включать в себя поле, содержащее идентификатор закладки.  
  
 Чтобы создать ссылку на закладку, необходимо сначала установить свойство «Закладка» элемента отчета. Чтобы установить свойство «Закладка», выберите элемент отчета и в панели «Свойства» введите значение или выражение идентификатора закладки, например, SalesChart или 5TopSales.  
  
 **Перейти по URL-адресу**  
 Выберите этот параметр, чтобы задать ссылку на веб-страницу. Введите или выберите URL-адрес веб-страницы или выражение, значением которого является URL-адрес веб-страницы. Чтобы изменить выражение, нажмите кнопку **Выражение** (*fx*). Это выражение может включать поле, содержащее URL-адрес. После выбора **Перейти по URL-адресу**появляются следующие дополнительные параметры.  
  
 **Выберите URL-адрес**  
 Введите или вставьте URL-адрес элемента. Для элемента, опубликованного на сервере отчетов, который настроен для работы в собственном режиме, указывается полный или относительный путь. Например, http:// *\<servername>* /images/image1.jpg. Для элемента, опубликованного на сервере отчетов, настроенном в режиме интеграции с SharePoint, используйте полный URL-адрес (например, http:// *\<SharePointservername>/\<site>* /документс/имажес/image1.jpg).  
  
## <a name="see-also"></a>См. также:  
 [Диаграммы &#40;построитель отчетов и службы SSRS&#41;](report-design/charts-report-builder-and-ssrs.md)   
 [Построитель отчетов справки по диалоговым окнам, панелям и мастерам](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Параметры отчета &#40;построитель отчетов и конструктор отчетов&#41;](report-design/report-parameters-report-builder-and-report-designer.md)   
 [Добавление вложенного отчета и параметров &#40;построитель отчетов и SSRS&#41;](report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md)   
 [Интерактивная сортировка, схемы документов и ссылки (построитель отчетов и службы SSRS)](report-design/interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)  
  
  