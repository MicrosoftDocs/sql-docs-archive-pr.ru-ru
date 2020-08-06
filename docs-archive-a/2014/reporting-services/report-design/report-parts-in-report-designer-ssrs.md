---
title: Части отчетов в конструкторе отчетов (SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.components.f1
ms.assetid: 0c34311d-05d6-4bd2-b452-545fa95f8e7f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7535c5c2c514bc32a11a5fc0d97c6aee1cf5f2d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654801"
---
# <a name="report-parts-in-report-designer-ssrs"></a>Части отчетов в конструкторе отчетов (SSRS)
  В конструкторе отчетов можно создавать таблицы, графики и другие элементы отчетов в проекте, а также публиковать их в виде *элементов отчета* на сервере отчетов или сайте SharePoint, интегрированном с сервером отчетов, для дальнейшего использования в других отчетах.  
  
 В общем, элементы отчетов работают одинаково в конструкторе отчетов и построителе отчетов. Сведения о базовых функциях см. в разделе [Report parts &#40;построитель отчетов и SSRS&#41;](../report-parts-report-builder-and-ssrs.md) в [документации построитель отчетов](https://go.microsoft.com/fwlink/?LinkId=154494) по MSDN.Microsoft.com.  
  
 Существуют фундаментальные отличия в том, как элементы отчетов работают в конструкторе отчетов. Основное отличие заключается в потоке операций. Построитель отчетов позволяет совместно создавать отчеты: один пользователь создает элемент отчета и публикует его. Другой пользователь может повторно использовать, изменять и переиздавать ее. В конструкторе отчетов публикация является односторонней: элемент отчета из конструктора отчетов можно опубликовать и использовать повторно. Но нельзя повторно использовать существующий элемент отчета в конструкторе отчетов. Эти отличия будут рассмотрены в данном разделе после общих сведений об элементах отчета.  
  
##  <a name="life-cycle-of-report-part-publishing"></a><a name="ComponentWorkflow"></a> Жизненный цикл публикации элементов отчета  
 ![rs_ComponentCreation](../media/rs-componentcreation.gif "rs_ComponentCreation")  
  
1.  В конструкторе отчетов пользователь А создает проект, содержащий отчет с диаграммой, которая зависит от внедренного набора данных.  
  
2.  Пользователь А отмечает флажком диаграмму с ее внедренным набором данных для публикации. Конструктор отчетов присваивает ей уникальный идентификатор. Пользователь А разворачивает отчет на сервере отчетов. Конструктор отчетов публикует диаграмму.  
  
3.  Пользователь Б создает пустой отчет в построителе отчетов и добавляет к нему диаграмму. Диаграмма теперь становится частью отчета пользователя Б наряду с внедренным набором данных. Пользователь Б может изменять экземпляры диаграммы и набора данных, которые находятся в отчете. Это никак не будет влиять на экземпляры диаграммы и набора данных на сервере отчетов, а также не приведет к разрыву связи между экземплярами в отчете и на сервере отчетов.  
  
     ![rs_BIDScomponentupdate](../media/rs-bidscomponentupdate.gif "rs_BIDScomponentupdate")  
  
4.  В построителе отчетов пользователь А изменяет диаграмму в исходном отчете.  
  
5.  Пользователь А повторно разворачивает отчет, который в свою очередь повторно публикует диаграмму на сервере и таким образом обновляет диаграмму на сервере.  
  
6.  В построителе отчетов пользователь Б принимает обновленную диаграмму с сервера. Это приводит к перезаписи изменений, внесенных пользователем Б в диаграмму отчета пользователя Б.  
  
##  <a name="publishing-report-parts"></a><a name="PublishingComponents"></a> Публикация элементов отчета  
 Если элемент отчета будет опубликован, конструктор отчетов присвоит ему уникальный идентификатор. С этого момента часть отчета сохраняет этот идентификатор независимо от других изменений, вносимых в нее. Идентификатор связывает исходный элемент отчета в конкретном отчете с частью отчета. При повторном использовании элемента отчета другими авторами отчетов в построителе отчетов этот идентификатор также связывает элемент отчета в их отчетах с этим элементом отчета.  
  
 Ниже перечислены элементы отчета, которые можно публиковать как части отчета.  
  
-   Диаграммы  
  
-   Датчики  
  
-   Изображения и внедренные изображения  
  
-   Maps  
  
-   Параметры  
  
-   Прямоугольники  
  
-   Таблицы  
  
-   Матрицы  
  
-   Списки  
  
 Если публикуется элемент отчета, отображающий данные, такие как таблица, матрица или диаграмма, он может основываться на общем наборе данных. В противном случае в момент публикации элемента отчета набор данных, от которого он зависит, сохраняется в качестве внедренного набора данных. Внедренные наборы данных могут основываться на внедренных источниках данных, однако учетные данные не сохраняются во внедренных источниках данных. Таким образом, если элемент отчета зависит от внедренного набора данных, который использует внедренный источник данных, любой пользователь, повторно использующий данный элемент отчета, должен будет ввести учетные данные для внедренного источника данных. Чтобы избежать этого, следует основывать внедренные и общие наборы данных на общих источниках данных с сохраненными учетными данными. Дополнительные сведения см. в разделе [элементы отчетов и наборы данных в построитель отчетов](../report-data/report-parts-and-datasets-in-report-builder.md) в [документации по построитель отчетов](https://go.microsoft.com/fwlink/?LinkId=154494) в MSDN.Microsoft.com.  
  
 Публикация элемента отчета в конструкторе отчетов — это двухэтапный процесс.  
  
1.  Отметьте флажком элементы отчета, которые следует опубликовать в диалоговом окне **Публикация частей отчетов** .  
  
2.  Разверните отчет.  
  
 Во время развертывания отчета элемент отчета публикуется на сайте SharePoint или сервере отчетов, поэтому другие пользователи смогут его повторно использовать. Чтобы опубликовать элемент отчета, следует установить соединение с сервером отчетов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и иметь на нем достаточные разрешения в момент публикации отчета.  
  
  
##  <a name="reusing-report-parts"></a><a name="SearchReuseComponents"></a> Повторное использование элементов отчета  
 В отличие от построителя отчетов нельзя искать и повторно использовать элемент отчета в других проектах, не относящихся к этому элементу отчета.  
  
 Авторы отчетов, работающие в построителе отчетов, могут искать и повторно использовать элементы отчетов, которые были опубликованы в отчетах, созданных ими.  
  
##  <a name="republishing-report-parts"></a><a name="RepublishingComponents"></a> Повторная публикация элементов отчетов  
 В конструкторе отчетов следует обновить существующий элемент отчета из отчета, в котором он был создан. В построителе отчетов авторы отчетов могут повторно использовать элемент отчета и публиковать его в качестве нового элемента отчета без необходимости заменять опубликованный элемент отчета. Если имеются достаточные разрешения, авторы также смогут обновить элемент отчета, опубликованного другим пользователем. Любой пользователь с достаточными разрешения для открытия папки на сайте или сервере может обновлять элементы отчета, хранящиеся в ней. Последнее обновление перепишет предыдущее.  
  
 Можно изменить и затем повторно опубликовать элемент отчета на сайте или сервере. Другие авторы отчетов в построителе отчетов, которые добавили рассматриваемый элемент отчета к своим отчетам, получат сообщение об изменении при очередном открытии этих отчетов. Они могут решить, принимать конкретные изменения или нет.  
  
 Также можно опубликовать уже опубликованный отчет как новый. В диалоговом окне «Публикация элементов отчетов» нажмите «Опубликовать как новый элемент отчета». Данный новый элемент отчета имеет уникальный идентификатор и не связан со старым элементом.  
  
  
## <a name="see-also"></a>См. также:  
 [Управление элементами отчета](managing-report-parts.md)  
  
  