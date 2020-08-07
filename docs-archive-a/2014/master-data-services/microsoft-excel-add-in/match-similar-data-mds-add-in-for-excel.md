---
title: Сопоставление схожих данных (надстройка MDS для Excel) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f6fd6fc1-3569-42a5-b6cb-87a921c88f3b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 70dea36de557c6fda909d06ee19ff8fa2ed6908d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731794"
---
# <a name="match-similar-data-mds-add-in-for-excel"></a>Сопоставление схожих данных (надстройка MDS для Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]воспользуйтесь возможностями служб Data Quality Services (DQS) для определения схожести данных.  
  
 Для этого можно:  
  
-   использовать базу знаний служб Data Quality Services по умолчанию или  
  
-   создать собственную пользовательскую базу знаний DQS и политику сопоставления. Дополнительные сведения см. в статье [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   Необходимо иметь лист, содержащий данные, управляемые MDS. Дополнительные сведения см. [в статье Загрузка данных из MDS в Excel](export-data-to-excel-from-master-data-services.md).  
  
-   Необязательный элемент. Перед проверкой схожести можно объединить другие данные с данными, управляемыми MDS. Дополнительные сведения см. в разделе [Объединение данных (надстройка MDS для Excel)](combine-data-mds-add-in-for-excel.md).  
  
### <a name="to-find-similarities-by-using-the-default-knowledge-base"></a>Поиск схожести с помощью базы знаний по умолчанию  
  
1.  На листе, который содержит данные, управляемые MDS, в группе **Качество данных** нажмите кнопку **Сопоставить данные**.  
  
2.  В диалоговом окне **Сопоставить данные** в списке **База знаний служб DQS** выберите пункт **Данные служб DQS (по умолчанию)**.  
  
3.  Для каждого столбца, содержащего данные, которые нужно сравнить, добавьте строку в диалоговом окне. Дополнительные сведения о полях в этом диалоговом окне см. в разделе [How to Set Matching Rule Parameters](../../data-quality-services/create-a-matching-policy.md#MatchingRules).  
  
4.  Когда сумма всех значений веса станет равна 100 %, нажмите кнопку **ОК**.  
  
### <a name="to-find-similarities-by-using-a-custom-knowledge-base"></a>Поиск схожести с помощью пользовательской базы знаний  
  
1.  На листе, который содержит данные, управляемые MDS, в группе **Качество данных** нажмите кнопку **Сопоставить данные**.  
  
2.  В списке **База знаний служб DQS** выберите имя пользовательской базы знаний.  
  
3.  Для каждого столбца на листе выберите домен служб DQS.  
  
4.  Когда все домены служб DQS будут сопоставлены со столбцами листа, нажмите кнопку **ОК**.  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   Просмотрите дополнительные сведения для определения схожих данных. Дополнительные сведения см. в разделе [Столбцы сопоставления качества данных (службы DQS)](data-quality-matching-columns-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>См. также:  
 [Сопоставление качества данных в надстройка MDS для Excel](data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Сопоставление данных](../../data-quality-services/data-matching.md)  
  
  
