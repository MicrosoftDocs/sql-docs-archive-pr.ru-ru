---
title: Создание нового Integration Services проекта | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Integration Services], creating
- Integration Services projects, creating
- SQL Server Integration Services projects, creating
- SSIS projects, creating
ms.assetid: 1e23f259-0401-4333-ab4f-89809aae63b1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f62d3ac2d33bb51a0ccc3b77d9f8b5ec0f52b345
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658334"
---
# <a name="create-a-new-integration-services-project"></a>Создание нового проекта служб Integration Services
  Данная процедура создает новый проект и новое решение служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
### <a name="to-create-a-new-integration-services-project"></a>Создание нового проекта служб Integration Services  
  
1.  Откройте среду [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.  
  
3.  В диалоговом окне **Создание проекта** на панели **Шаблоны** выберите шаблон **Проект служб Integration Services** .  
  
     Шаблон **Проект служб Integration Services** создает проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий единственный пустой пакет.  
  
4.  (Необязательно) При необходимости измените имя и расположение проекта.  
  
     Имя решения автоматически обновляется для соответствия с именем проекта.  
  
5.  Чтобы создать отдельную папку для файла решения, выберите **Создать каталог для решения**. Это параметр по умолчанию.  
  
6.  Если на компьютере установлено программное обеспечение для системы управления версиями, выберите **Добавить в систему управления версиями**  , чтобы связать проект с этой системой управления версиями.  
  
7.  Если в качестве программного обеспечения для управления версиями используется [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, откроется диалоговое окно **Вход в Visual SourceSafe** . В окне **Вход в Visual SourceSafe**укажите имя пользователя, пароль и имя базы данных [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe. Нажмите кнопку **Обзор** , чтобы указать базу данных.  
  
    > [!NOTE]  
    >  Чтобы просмотреть и изменить выбранный встраиваемый модуль управления версиями, а также настроить среду управления версиями, выберите пункт **Параметры** в меню **Сервис**, а затем разверните узел **Управление версиями**.  
  
8.  Нажмите кнопку **ОК** , чтобы добавить решение в **проводник решения**r и добавить проект в решение.  
  
## <a name="see-also"></a>См. также:  
 [Integration Services &#40;проектов&#41; SSIS](integration-services-ssis-projects-and-solutions.md)   
 [Добавление или удаление проектом служб Integration Services из решения](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)  
  
  
