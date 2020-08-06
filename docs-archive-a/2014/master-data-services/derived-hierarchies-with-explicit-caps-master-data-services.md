---
title: Производные иерархии с явными ограничениями (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], derived hierarchies with explicit caps
- explicit hierarchies, derived hierarchies with explicit caps
- derived hierarchies, derived hierarchies with explicit caps
ms.assetid: 6a82ff66-c137-4757-99bb-787d189b4295
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d2460ddf098f0547c2876dd9689f5d2bf9b461a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656437"
---
# <a name="derived-hierarchies-with-explicit-caps-master-data-services"></a>Производные иерархии с явными ограничениями (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]использование уровней явной иерархии в качестве высших уровней производной иерархии называется «производной иерархией с явным ограничением».

 Явная иерархия должна быть основана на той же сущности, что и сущность на вершине производной иерархии.

 В пользовательском интерфейсе [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] такой тип иерархии можно создать, перетащив явную иерархию на вершину производной иерархии.

 ![mds_conc_explicit_cap_UI_structure](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-structure.gif "mds_conc_explicit_cap_UI_structure")

## <a name="derived-hierarchy-with-explicit-cap-example"></a>Образец производной иерархии с явным ограничением
 В данном примере элементы явной иерархии происходят из сущности «Подкатегория». В производной иерархии элементы высшего уровня также происходят из сущности «Подкатегория».

 ![mds_conc_explicit_cap_UI_example](../../2014/master-data-services/media/mds-conc-explicit-cap-ui-example.gif "mds_conc_explicit_cap_UI_example")

 При использовании явной иерархии на вершине производной иерархии производная иерархия становится неоднородной.

## <a name="rules"></a>Правила

-   В производной иерархии с явным ограничением не может быть больше одной явной иерархии.

-   Одну и ту же явную иерархию можно использовать как ограничение для нескольких производных иерархий.

-   Нельзя назначить разрешения на элементы иерархии производным иерархиям с явными ограничениями. Если назначить разрешение явной иерархии или производной иерархии индивидуально, то разрешение затронет обе иерархии.

## <a name="related-tasks"></a>Связанные задачи

|Описание задачи|Раздел|
|----------------------|-----------|
|Создание производной иерархии.|[Создание производной иерархии (службы Master Data Services)](create-a-derived-hierarchy-master-data-services.md)|
|Создание явной иерархии.|[Создание явной иерархии (службы Master Data Services)](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)|
|Удаление существующей производной иерархии.|[Удаление производной иерархии (службы Master Data Services)](../../2014/master-data-services/delete-a-derived-hierarchy-master-data-services.md)|
|||

## <a name="related-content"></a>См. также

-   [Производные иерархии (службы Master Data Services)](../../2014/master-data-services/derived-hierarchies-master-data-services.md)

-   [Явные иерархии (службы Master Data Services)](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)


