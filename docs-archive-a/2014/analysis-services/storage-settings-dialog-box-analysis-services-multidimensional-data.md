---
title: Диалоговое окно "настройки хранилища" (Analysis Services-многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitiondesigner.partitionstoragesettings.f1
- sql12.asvs.cubeeditor.cubebuilder.measuregroupstoragesettings.f1
ms.assetid: 80c41c71-226c-45fe-b9cf-af824b592fe1
author: minewiskan
ms.author: owend
ms.openlocfilehash: a2ec48f97e7d0a86f64f53e41f5c5df1c0728fff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738870"
---
# <a name="storage-settings-dialog-box-analysis-services---multidimensional-data"></a>Диалоговое окно «Настройки хранилища» (службы Analysis Services — многомерные данные)
  Используйте диалоговое окно **Настройки хранилища** в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] для задания свойств упреждающего кэширования, хранилища и уведомлений для измерения, куба, группы мер или секции. Диалоговое окно **Настройки хранилища** в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] можно отобразить:  
  
-   Нажмите кнопку с многоточием (**...**) для `ProactiveCaching` значения свойства измерения, Куба, группы мер или секции в окне **Свойства** [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] .  
  
-   Путем раскрытия группы мер на вкладке **Секции** окна **Конструктор кубов** , щелкнув **Настройки хранилища**.  
  
-   Путем раскрытия группы мер и выбора секции в сетке, соответствующей этой группе мер, на вкладке **Секции** окна **Конструктор кубов** , щелкнув **Настройки хранилища**.  
  
-   Путем раскрытия группы мер и выбора секции в сетке, соответствующей этой группе мер, на вкладке **Секции** окна **Конструктор кубов** , щелкнув **Настройки хранилища** на панели **Панель инструментов** вкладки **Секции** окна **Конструктор кубов**.  
  
## <a name="options"></a>Варианты  
  
|Термин|Определение|Значения|  
|----------|----------------|------------|  
|**Стандартные настройки**|Выберите, чтобы задействовать ползунок **Стандартные настройки** и использовать предопределенные настройки режима хранения и возможностей упреждающего кэширования.||  
|**Стандартные настройки**|Установите одну из следующих предустановленных настроек:<br /><br /> **ROLAP в реальном времени**<br /><br /> Выберите, чтобы использовать следующие параметры хранения и упреждающего кэширования:|Режим хранилища ROLAP<br /><br /> Включить упреждающее кэширование<br /><br /> Удалять устаревшие данные из кэша с периодом задержки 0 секунд.<br /><br /> Приводить объект в режим в сети немедленно|  
||**HOLAP в реальном времени**<br /><br /> Выберите, чтобы использовать следующие параметры хранения и упреждающего кэширования:|Режим хранилища HOLAP<br /><br /> Включить упреждающее кэширование<br /><br /> Удалять устаревшие данные из кэша с периодом задержки 0 секунд.<br /><br /> Обновлять кэш при изменении данных с интервалом бездействия в 0 секунд и без интервала прерывания бездействия<br /><br /> Приводить объект в режим в сети немедленно|  
||**MOLAP с небольшой задержкой**<br /><br /> Выберите, чтобы использовать следующие параметры хранения и упреждающего кэширования:|Режим хранения MOLAP<br /><br /> Включить упреждающее кэширование<br /><br /> Удалять устаревшие данные из кэша с периодом задержки 30 минут<br /><br /> Обновлять кэш при изменении данных с интервалом бездействия в 10 секунд и интервалом прерывания бездействия в 10 минут<br /><br /> Приводить объект в режим в сети немедленно|  
||**MOLAP со средней задержкой**<br /><br /> Выберите, чтобы использовать следующие параметры хранения и упреждающего кэширования:|Режим хранения MOLAP<br /><br /> Включить упреждающее кэширование<br /><br /> Удалять устаревшие данные из кэша с периодом задержки 4 часа<br /><br /> Обновлять кэш при изменении данных с интервалом бездействия в 10 секунд и интервалом прерывания бездействия в 10 минут<br /><br /> Приводить объект в режим в сети немедленно|  
||**Автоматический MOLAP**<br /><br /> Выберите, чтобы использовать следующие параметры хранения и упреждающего кэширования:|Режим хранения MOLAP<br /><br /> Включить упреждающее кэширование<br /><br /> Обновлять кэш при изменении данных с интервалом бездействия в 0 секунд и без интервала прерывания бездействия|  
||**Запланированный MOLAP**<br /><br /> Выберите, чтобы использовать следующие параметры хранения и упреждающего кэширования:|Режим хранения MOLAP<br /><br /> Разрешить упреждающее кэширование<br /><br /> Периодически обновляет кэш с интервалом перестроения в 1 день|  
||**MOLAP**<br /><br /> Выберите, чтобы использовать следующие параметры хранения и упреждающего кэширования:|Режим хранения MOLAP|  
|**Пользовательские настройки**|Выберите, чтобы явно установить параметры режима хранения, упреждающего кэширования и уведомлений.||  
|**Параметры**|Щелкните, чтобы вывести диалоговое окно **Параметры хранилища** и явно задать параметры режима хранения, упреждающего кэширования и уведомлений. Дополнительные сведения о диалоговом окне **Параметры хранилища** см. в разделе [Диалоговое окно "Параметры хранилища" (службы Analysis Services — многомерные данные)](storage-options-dialog-box-analysis-services-multidimensional-data.md).||  
  
## <a name="see-also"></a>См. также:  
 [Analysis Services конструкторов и диалоговых окон &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Упреждающее кэширование &#40;секций&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)   
 [Хранилище Куба &#40;Analysis Services многомерных данных&#41;](multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)  
  
  