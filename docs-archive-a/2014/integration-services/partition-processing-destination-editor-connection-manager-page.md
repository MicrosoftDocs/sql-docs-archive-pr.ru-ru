---
title: Редактор назначения обработки секций (страница «Диспетчер соединений») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.connection.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: 7add6f82-eed1-47fc-a5d7-7b91f3f24d34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a0f79dfcc9c0d98d871a49618f4dabfb8a3bbac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658875"
---
# <a name="partition-processing-destination-editor-connection-manager-page"></a>Редактор назначения обработки секций (страница «Диспетчер соединений»)
  Используйте страницу **Диспетчер соединений** диалогового окна **Редактор назначения обработки секций**, чтобы определить соединение с проектом служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] или экземпляром служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Дополнительные сведения о назначении «Обработка секций» см. в разделе [Partition Processing Destination](data-flow/partition-processing-destination.md).  
  
> [!NOTE]  
>  Описанные здесь задачи не применимы к табличным моделям служб Analysis Services.  Нельзя связать входные столбцы со столбцами секционирования для табличных моделей. Вместо этого для обработки секции следует использовать задачу выполнения DDL [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) служб Analysis Services.  
  
## <a name="options"></a>Параметры  
 **Connection manager**  
 Выберите из списка существующий диспетчер соединений или создайте новое соединение, нажав кнопку **Создать**.  
  
 **Создать**  
 Создайте новое соединение, воспользовавшись диалоговым окном **Добавление диспетчера соединений со службами Analysis Services** .  
  
 **Список доступных секций**  
 Выберите секцию для обработки.  
  
 **Метод обработки**  
 Выберите метод обработки. Значение этого параметра по умолчанию — **Полная**.  
  
|Значение|Описание|  
|-----------|-----------------|  
|Добавление (дополнительное)|Выполнить дополнительную обработку секции.|  
|Полное|Выполнить полную обработку секции.|  
|Только данные|Выполнить обработку обновления секции.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор назначения "Обработка секций" &#40;"сопоставления"&#41;](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md)   
 [Редактор назначения "Обработка секций" (страница "Дополнительно")](../../2014/integration-services/partition-processing-destination-editor-advanced-page.md)  
  
  
