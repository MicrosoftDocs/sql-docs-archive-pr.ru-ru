---
title: Параметры атрибутов неизменности и изменяемых атрибутов (мастер медленно изменяющихся измерений) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.attriboption.f1
ms.assetid: c841345c-7d03-452f-9379-1c8c464f029c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df654cd97b343179828ebd94dea40eacc90e003d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656490"
---
# <a name="fixed-and-changing-attribute-options-slowly-changing-dimension-wizard"></a>Параметры атрибутов неизменности и изменяемых атрибутов (мастер медленно изменяющихся измерений)
  В диалоговом окне **Параметры атрибутов неизменности и изменяемых атрибутов** можно определить реакцию на изменения фиксированных и изменяемых атрибутов.  
  
 Дополнительные сведения о работе этого мастера см. в разделе [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Атрибуты неизменности**  
 Для атрибутов неизменности определяет, должна ли задача закончиться неудачей, если обнаружено изменение в атрибуте неизменности.  
  
 **Изменяемые атрибуты**  
 Для изменяемых атрибутов определяет, должна ли задача изменить все устаревшие записи или записи с истекшим сроком действия, в дополнение к текущим, при обнаружении изменения в изменяемом атрибуте. Записью с истекшим сроком действия является та, которая была заменена более новой записью в результате изменения атрибута с предысторией (изменение типа 2). Выбор этого параметра может наложить дополнительные требования к обработке в многомерном объекте, созданном в реляционном хранилище данных.  
  
## <a name="see-also"></a>См. также:  
 [Настройка выходов с помощью мастера медленно изменяющихся измерений](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  