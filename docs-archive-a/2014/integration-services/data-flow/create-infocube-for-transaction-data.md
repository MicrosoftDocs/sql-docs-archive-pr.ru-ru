---
title: Создание InfoCube для данных транзакции | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 673cea01-a260-4fce-a1a0-f73839289805
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a20fe051cfdd3e6afe285279996fcf696a83c21b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728573"
---
# <a name="create-infocube-for-transaction-data"></a>Создание InfoCube для данных транзакции
  Используйте диалоговое окно **Создание InfoCube для данных транзакции** , чтобы создать новый InfoCube для данных транзакции в системе SAP Netweaver BW.  
  
 Можно открыть диалоговое окно **Создание InfoCube для данных транзакции** на странице **Диспетчер соединений** **Редактора назначений SAP BW**. Дополнительные сведения о назначении SAP BW см. в статье [SAP BW Destination](sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Документация по Microsoft Connector 1.1 для SAP BW предполагает, что читатель знаком со средой SAP Netweaver BW. Дополнительные сведения о SAP Netweaver BW или сведения о настройке объектов и процессов SAP Netweaver BW см. в документации SAP.  
  
 **Открытие диалогового окна «Создание InfoCube для данных транзакции»**  
  
1.  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте пакет [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий назначение SAP BW.  
  
2.  На вкладке **Поток данных** дважды щелкните назначение SAP BW.  
  
3.  В **Редакторе назначений SAP BW**щелкните **Диспетчер соединений** , чтобы открыть страницу редактора **Диспетчер соединений** .  
  
4.  На вкладке **Диспетчер соединений** в поле группы **Создание объектов SAP BW** выберите **InfoCube**и щелкните **Создать**.  
  
## <a name="general-options"></a>Общие параметры  
 **Имя InfoCube**  
 Введите имя для нового InfoCube.  
  
 **Полное описание**  
 Введите описание нового InfoCube.  
  
 **Сохранить и активировать**  
 Сохраните и активируйте новый InfoCube.  
  
## <a name="infocube-transfer-structure-options"></a>Параметры переноса структуры InfoCube  
 Раздел переноса структуры InfoCube позволяет привязать столбцы потока данных в InfoObjects.  
  
 **PipelineElement**  
 Отображает столбец среди выходных данных потока, подключенного к целевому месту SAP BW.  
  
 **PipelineDataType**  
 Отображает тип данных столбца потока данных.  
  
 **InfoObject**  
 Отображает имя InfoObject, связанное со столбцом потока данных.  
  
 **Тип**  
 Отображает тип InfoObject, связанный со столбцом потока данных. В следующей таблице приводятся возможные значения типа.  
  
|Значение|Description|  
|-----------|-----------------|  
|CHA|Характеристики|  
|UNI|Units|  
|KYF|Ключевые цифры|  
|TIM|Характеристики времени|  
  
 **Iobject — поиск**  
 Сопоставьте существующий InfoObject со столбцом потока данных для текущей строки. Чтобы создать это сопоставление, щелкните **Найти**, а затем используйте диалоговое окно **Поиск InfoObject** для выбора существующего InfoObject. Дополнительные сведения об этом диалоговом окне см. в разделе [Look Up InfoObject](look-up-infoobject.md).  
  
 После выбора существующего InfoObject компонент заполняет столбцы **InfoObject** и **Тип** выбранными значениями.  
  
 **Iobject — создать**  
 Создайте новый InfoObject и свяжите этот новый InfoObject со столбцом потока данных в текущей строке. Для создания нового InfoObject щелкните **Создать**, а затем используйте диалоговое окно **Создание InfoObject** для создания InfoObject. Дополнительные сведения об этом диалоговом окне см. в разделе [Create New InfoObject](create-new-infoobject.md).  
  
 После создания нового InfoObject компонент заполняет столбцы **InfoObject** и **Тип** новыми значениями.  
  
 **Iobject — удаление**  
 Удаляет взаимосвязь между InfoObject и столбцом потока данных для текущей строки. Чтобы удалить эту связь, нажмите кнопку **Удалить**.  
  
## <a name="see-also"></a>См. также:  
 [Справка F1 по Microsoft Connector 1.1 для SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
