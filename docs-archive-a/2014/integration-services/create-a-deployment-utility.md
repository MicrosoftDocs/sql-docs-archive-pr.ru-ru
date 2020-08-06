---
title: Создание программы развертывания | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- deploying packages [Integration Services], deployment utility
- deployment utility [Integration Services]
ms.assetid: 354322a4-ae8c-4d92-8e71-42d29dbd0614
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bdf1328d440920fed98e5fa1d16024c5fec32cbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665053"
---
# <a name="create-a-deployment-utility"></a>Create a Deployment Utility
  Первый шаг в развертывании пакетов — это создание программы развертывания для проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Программа развертывания — это папка, которая содержит файлы, требуемые для развертывания пакетов проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на другом сервере. Программа развертывания создается на компьютере, где хранится проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 Создание программы развертывания пакета для проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] начинается с настройки конфигурации процесса построения для его создания, и затем построения самого проекта. Когда производится построение проекта, все пакеты и их конфигурации в проекте включаются в него автоматически. Для развертывания дополнительных файлов, таких как файл Readme проекта, поместите файлы в папку **Разное** проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Когда проект построен, эти файлы также автоматически включаются в проект.  
  
 Можно установить независимое развертывание каждого проекта. Перед построением проекта и созданием программы развертывания пакета можно установить свойства программы развертывания, чтобы определить способ развертывания пакетов в проекте. Например, можно указать, будут ли обновлены конфигурации пакета при развертывании проекта. Для получения доступа к свойствам проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] щелкните правой кнопкой мыши проект и затем выберите пункт **Свойства**.  
  
 В следующей таблице производится перечисление свойств программы развертывания.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|AllowConfigurationChange|Значение, указывающее, возможно ли обновление конфигураций во время развертывания.|  
|CreateDeploymentUtility|Значение, указывающее, будет ли во время построения пакета производиться создание программы развертывания. Для создания программы развертывания значение свойства должно быть равно `True`.|  
|DeploymentOutputPath|Расположение программы развертывания, соответствующей проекту служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .|  
  
 При создании проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] создается файл манифеста \<project name>.SSISDeploymentManifest.xml, который добавляется вместе с копиями пакетов проекта и их зависимостей в папку bin\Deployment проекта или в расположение, указанное в свойстве DeploymentOutputPath. Файл манифеста производит перечисление пакетов, их конфигураций, а также иных различных файлов проекта.  
  
 Содержимое папки развертывания обновляется каждый раз при построении проекта. Это означает, что любой файл, сохраненный в этой папке, который не копируется снова в эту папку в процессе построения, будет удален. Например, файлы конфигурации пакета, сохраненные в папку развертывания, будут удалены.  
  
### <a name="to-create-a-package-deployment-utility"></a>Создание программы развертывания пакетов  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте решение, содержащее проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , для которого необходимо создать программу развертывания пакетов.  
  
2.  Щелкните правой кнопкой мыши проект и выберите пункт **Свойства**.  
  
3.  В диалоговом окне **Страницы свойств \<project name>** выберите элемент **Программа развертывания**.  
  
4.  Чтобы обновить конфигурации пакетов при развертывании пакетов, задайте для **AllowConfigurationChanges** значение `True` .  
  
5.  Задайте для параметра `CreateDeploymentUtility` значение `True`.  
  
6.  При необходимости обновите расположение программы развертывания посредством изменения свойства `DeploymentOutputPath`.  
  
7.  Нажмите кнопку **ОК**.  
  
8.  В обозревателе решений щелкните правой кнопкой мыши проект и выберите **Построить**.  
  
9. Просмотрите ход компоновки и ошибки в окне **Выход** .  
  
## <a name="see-also"></a>См. также:  
 [Конфигурации пакетов](../../2014/integration-services/package-configurations.md)   
 [Создание конфигураций пакетов](../../2014/integration-services/create-package-configurations.md)   
 [Развертывание пакетов с помощью программы развертывания](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md)   
 [Развертывание пакетов &#40;&#41;SSIS](packages/legacy-package-deployment-ssis.md)  
  
  