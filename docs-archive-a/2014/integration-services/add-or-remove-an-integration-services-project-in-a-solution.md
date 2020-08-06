---
title: Добавление или удаление проекта Integration Services в решении | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- Integration Services projects, adding
- SQL Server Integration Services projects, adding
- SSIS projects, adding
- projects [Integration Services], adding
ms.assetid: f01f6475-b63c-41dc-82ac-b62162b3adf7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 49984c61047a6b716015bd72e518b73cb08b3226
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654471"
---
# <a name="add-or-remove-an-integration-services-project-in-a-solution"></a>Добавление или удаление проектом служб Integration Services из решения
  Следующие процедуры описывают способы добавления или удаления проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в решении.  
  
 Добавлять проекты к существующему решению и удалять их из него можно только тогда, когда решение отображается в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Если вы выбрали параметр **всегда показывать решение** в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] будет отображать решение, даже если это решение содержит только один проект. В противном случае среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] будет отображать решение, только когда в нем более одного проекта. Дополнительными могут быть проекты служб [!INCLUDE[ssIS](../includes/ssis-md.md)] или проекты других типов.  
  
## <a name="adding-an-integration-services-project"></a>Добавление проекта служб Integration Services  
 При добавлении проекта можно создать новый пустой проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] или добавить проект, созданный для другого решения. Добавить проект к существующему решению можно, только если решение отображается в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
#### <a name="to-add-a-new-integration-services-project-to-a-solution"></a>Добавление нового проекта служб Integration Services к решению  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте решение, к которому нужно добавить новый проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , и выполните одно из следующих действий:  
  
    -   Щелкните решение правой кнопкой, выберите пункт **Добавить**, а затем **Новый проект**.  
  
    -   В меню **Файл** выберите пункт **Добавить**, затем щелкните **Создание проекта**.  
  
2.  В диалоговом окне **Добавить новый проект** щелкните **Проект служб Integration Services** на панели **Шаблоны** .  
  
3.  Дополнительно можно изменить имя и расположение проекта.  
  
4.  Нажмите кнопку **ОК**.  
  
#### <a name="to-add-an-existing-integration-services-project-to-a-solution"></a>Добавление существующего проекта служб Integration Services к решению  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте решение, к которому нужно добавить существующий проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , и выполните одно из следующих действий:  
  
    -   Щелкните решение правой кнопкой мыши, выберите **Добавить**, а затем щелкните **Существующий проект**.  
  
    -   В меню **Файл** выберите **Добавить**, а затем — **Существующий проект**.  
  
2.  В диалоговом окне **Добавление существующего проекта** выберите локальный проект, который нужно добавить, и щелкните **Открыть**.  
  
3.  Проект будет добавлен в папку решений **Обозревателя решений**.  
  
## <a name="removing-an-integration-services-project"></a>Удаление проекта служб Integration Services  
 Удалить проект из решения можно, только если решение отображается в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. После отображения решения можно удалить все проекты, кроме одного. Когда остается только один проект, среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] больше не отображает папку решения и удалить последний проект становится невозможным.  
  
#### <a name="to-remove-an-integration-services-project-from-a-solution"></a>Удаление проекта служб Integration Services из решения  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]нужно открыть решение, из которого необходимо удалить проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
2.  В обозревателе решений щелкните правой кнопкой мыши проект и выберите команду **Выгрузить проект**.  
  
3.  Нажмите кнопку **ОК** для подтверждения удаления.  
  
## <a name="see-also"></a>См. также:  
 [Integration Services &#40;проектов&#41; SSIS](integration-services-ssis-projects-and-solutions.md)   
 [Создание нового проекта Integration Services](../../2014/integration-services/create-a-new-integration-services-project.md)  
  
  
