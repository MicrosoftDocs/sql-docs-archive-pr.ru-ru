---
title: Организатор конфигураций пакетов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.packageconfigurationorganizer.f1
helpviewer_keywords:
- Package Configurations Organizer dialog box
ms.assetid: f20ae6cb-9e6a-4d24-88ff-d7a903a4e8d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 67fdc9ca0faeff57c18fdb6e4d10acca3e9963f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736524"
---
# <a name="package-configurations-organizer"></a>Организатор конфигураций пакетов
  Диалоговое окно **Организатор конфигураций пакетов** используется для включения конфигураций пакетов, просмотра списка конфигураций для текущего пакета, а также для указания порядка, в котором следует загружать конфигурации.  
  
> [!NOTE]  
>  Доступны конфигурации для модели развертывания пакетов. Для моделей развертывания проектов вместо конфигураций используются параметры. Модель развертывания проектов позволяет развертывать проекты служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на сервере служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Дополнительные сведения о моделях развертывания см. в разделе [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).  
  
 Если несколько конфигураций обновляют одно и то же свойство, то значения из конфигураций, расположенных в нижней части списка, заменят значения из конфигураций, расположенных в верхней части списка. Последнее значение, загружаемое в свойства, является значением, которое используется при выполнении пакета. Кроме того, если пакет использует сочетание прямой конфигурации, например XML-файла конфигурации, и непрямой конфигурации, например переменной среды, то непрямая конфигурация, указывающая на расположение прямой конфигурации, должна располагаться выше в списке.  
  
> [!NOTE]  
>  При загрузке в указанном порядке конфигурации загружаются с верхней части списка, показанного в диалоговом окне **Организатор конфигураций пакетов** , в нижнюю часть списка. Однако во время выполнения конфигурации пакетов могут загружаться в другом порядке. В частности, конфигурации родительских пакетов загружаются после всех остальных конфигураций.  
  
 Конфигурации пакета обновляют значения свойств объектов пакета во время выполнения. После загрузки пакета значения, полученные из конфигураций, заменяют значения, установленные при разработке пакета. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] поддерживают различные типы конфигураций. Например, можно использовать XML-файл, содержащий несколько конфигураций, или переменную среды, содержащую всего одну конфигурацию. Дополнительные сведения см. в статье [Package Configurations](../../2014/integration-services/package-configurations.md).  
  
## <a name="options"></a>Параметры  
 **Включить конфигурацию пакетов**  
 Выберите, чтобы использовать конфигурации с пакетом.  
  
 **Имя конфигурации**  
 Просмотр имени конфигурации.  
  
 **Тип конфигурации**  
 Просмотр типа месторасположения конфигураций.  
  
 **Строка конфигурации**  
 Просмотр расположения значений конфигураций. Расположение может представлять собой путь к файлу, имя переменной среды, имя переменной родительского пакета, раздел реестра или имя таблицы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 **Целевой объект**  
 Просмотр имени объекта, обновляемого конфигурацией. Если конфигурация является XML-файлом конфигурации или таблицей SQL Server, столбец остается пустым, потому что конфигурация может содержать несколько объектов.  
  
 **Целевое свойство**  
 Просмотр имени свойства, измененного конфигурацией. Этот столбец пустой, если тип конфигурации поддерживает одновременно несколько конфигураций.  
  
 **Добавление**  
 Добавление конфигурации с помощью мастера настройки пакета.  
  
 **Edit** (Изменение)  
 Редактирование существующей конфигурации при помощи перезапуска мастера настройки пакета.  
  
 **Удалить**  
 Выберите конфигурацию, а затем нажмите кнопку **Удалить**.  
  
 **Стрелки**  
 Выберите конфигурацию и, используя стрелки вверх и вниз, переместите ее вверх или вниз в списке. Конфигурации загружаются в последовательности, указанной в списке.  
  
## <a name="see-also"></a>См. также:  
 [Создание конфигурации пакетов](../../2014/integration-services/create-package-configurations.md)  
  
  