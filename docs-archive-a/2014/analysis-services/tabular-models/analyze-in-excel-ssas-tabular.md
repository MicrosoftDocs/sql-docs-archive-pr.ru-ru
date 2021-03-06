---
title: Анализ в Excel (табличные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2f17b4df-eea2-48c7-a1f2-a3fb7748c15f
author: minewiskan
ms.author: owend
ms.openlocfilehash: ad46515f5710fa7e46b0beb8b3133e925973293a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658429"
---
# <a name="analyze-in-excel-ssas-tabular"></a>Анализ в Excel (табличные службы SSAS)
  Функция «Анализ в Excel» в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]дает разработчику табличных моделей возможность быстро выполнить анализ проекта модели во время разработки. Функция «Анализ в Excel» открывает Microsoft Excel, создает соединение с источником данных, которым выступает база данных рабочей области модели, и автоматически добавляет сводную таблицу на рабочий лист. Объекты базы данных рабочей области (таблицы, столбы и меры) включаются в качестве полей в список полей сводной таблицы. Затем объекты и данные можно просмотреть в контексте действующего пользователя или роли и перспективы.  
  
 Материал этого раздела предполагает, что читатель умеет работать с Microsoft Excel, сводными таблицами и диаграммами. Дополнительные сведения об использовании Excel см. в справке по Excel.  
  
 Разделы данной темы:  
  
-   [Преимущества](#bkmk_benefits)  
  
-   [Связанные задачи](#bkmk_rt)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a> Преимущества  
 Функция «Анализ в Excel» дает разработчику модели возможность проверить производительность проекта модели с помощью такого приложения общего анализа данных, как Microsoft Excel. Для использования функции анализа в Excel необходимо на тот же компьютер, где находится среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], установить Microsoft Office 2003 или более поздней версии.  
  
> [!NOTE]  
>  Если Microsoft Office не установлен на том же компьютере, что и [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], то можно с помощью Excel подключиться с другого компьютера к базе данных рабочей области в качестве источника данных. Затем можно вручную добавить сводную таблицу на лист.  
  
 Функция «Анализ в Excel» открывает Excel и создает новую книгу Excel (.xls). Создается подключение к данным из книги к базе данных рабочей области модели. На рабочий лист добавляется пустая сводная таблица, и в списке полей сводной таблицы заполняются метаданные объекта модели. Затем к сводной таблице можно добавить просматриваемые данные и срезы.  
  
 При использовании функции «Анализ в Excel» по умолчанию действующим пользователем является учетная запись пользователя, выполнившего вход. Как правило, эта учетная запись является администратором без ограничений на просмотр объектов или данных модели. Можно, однако, указать другого действующего пользователя или роль. Это позволит просмотреть проект модели в Excel в контексте определенного пользователя или роли. При указании действующего пользователя можно выбрать один из следующих вариантов.  
  
 **Текущий пользователь Windows**  
 Использует учетную запись пользователя, с которой в настоящее время выполнен вход.  
  
 **Другой пользователь Windows**  
 Использует указанное имя пользователя Windows, а не имя пользователя, выполнившего вход. При использовании другого пользователя Windows пароль не требуется. Объекты и данные могут просматриваться в Excel только в контексте действующего пользователя. В Excel не допускаются изменения объектов или данных модели.  
  
 **Роль**  
 Роль служит для определения разрешений пользователя относительно данных и метаданных объекта. Роли обычно определены для конкретного пользователя или группы пользователей Windows. Некоторые роли могут включать дополнительные фильтры уровня строки, определенные в формуле DAX. При использовании функции «Анализ в Excel» можно дополнительно выбрать роль для использования. Метаданные объекта и представления данных будут ограничены разрешением и фильтрами, определенными для роли. Дополнительные сведения см. в разделе [Создание ролей и управление ими (табличные службы SSAS)](roles-ssas-tabular.md).  
  
 В дополнение к действующему пользователю или роли можно указать перспективу. Перспективы позволяют разработчикам модели определять конкретные представления бизнес-сценариев для объектов модели и данных. По умолчанию перспектива не используется. Чтобы перспективу можно было использовать в функции анализа в Excel, она должна быть предварительно определена в диалоговом окне «Перспективы» в среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Если перспектива указана, то список полей сводной таблицы будет содержать только объекты, выбранные в этой перспективе. Дополнительные сведения см. в статье [Создание и управление перспективами &#40;табличных&#41;SSAS ](perspectives-ssas-tabular.md).  
  
##  <a name="related-tasks"></a><a name="bkmk_rt"></a> Связанные задачи  
  
|**Раздел**|**Описание**|  
|---------------|---------------------|  
|[Анализ табличной модели в Excel (табличные службы SSAS)](analyze-a-tabular-model-in-excel-ssas-tabular.md)|В этом разделе описан порядок использования функции «Анализ в Excel» в конструкторе моделей для открытия Excel, создания соединения с источником данных, которым выступает база данных рабочей области модели, и добавления сводной таблицы на рабочий лист.|  
  
## <a name="see-also"></a>См. также:  
 [Анализ табличной модели в Excel &#40;табличные&#41;SSAS](analyze-a-tabular-model-in-excel-ssas-tabular.md)   
 [Роли &#40;табличные&#41;SSAS](roles-ssas-tabular.md)   
 [Перспективы (табличные службы SSAS)](perspectives-ssas-tabular.md)  
  
  
