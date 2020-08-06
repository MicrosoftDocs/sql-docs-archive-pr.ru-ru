---
title: Создание пакетов в SQL Server Data Tools | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: bb3c085b-1458-49fa-8348-6a76b6e97ea6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 330e0271421dc620f7c4fad9c6944331ebe94881
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658320"
---
# <a name="create-packages-in-sql-server-data-tools"></a>Создание пакетов в SQL Server Data Tools
  Пакет, созданный в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] с помощью конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] , сохраняется в файловой системе. Чтобы сохранить пакет в версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или в хранилище пакетов, необходимо сохранить копию пакета. Дополнительные сведения см. в разделе [Сохранение одной копии пакета](../../2014/integration-services/save-a-copy-of-a-package.md).  
  
 Создать новый пакет в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]можно одним из следующих методов.  
  
-   На основе шаблона пакета в составе служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ;  
  
-   Создание настраиваемого шаблона  
  
     Для использования пользовательских пакетов в качестве шаблонов для создания новых пакетов просто скопируйте их в папку DataTransformationItems. По умолчанию эта папка находится в каталоге «C:\Program Files\Microsoft Visual Studio 9,0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject».  
  
-   Копирование существующего пакета.  
  
     Если существующие пакеты содержат функциональные возможности, которые нужно использовать повторно, то поток управления и поток данных будет быстрее создать путем копирования и вставки объектов из других пакетов. Дополнительные сведения о копировании и вставке в проектах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] см. в разделе [Повторное использование объектов пакета](reuse-of-package-objects.md).  
  
     При создании нового пакета с помощью копирования существующего пакета или с помощью шаблона имя и идентификатор GUID существующего пакета также копируются. Необходимо обновить имя и идентификатор GUID нового пакета, чтобы отличать его от файла, из которого он был скопирован. Например, если у пакетов будет одинаковый идентификатор GUID, это затруднит идентификацию пакета, к которому относятся записанные в журнал данные. Можно повторно сформировать идентификатор GUID в свойстве `ID` и обновить значение свойства `Name` в окне свойств среды [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения см. в разделах [Установка свойств пакета](set-package-properties.md) и [Программа dtutil](dtutil-utility.md).  
  
-   На основе пользовательского пакета, выбранного в качестве шаблона.  
  
-   Запустите мастер импорта и экспорта [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
     Мастер импорта и экспорта [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] создает готовый пакет для выполнения простого импорта и экспорта. В процессе работы мастера настраиваются все соединения, источник и назначение, а также добавляются преобразования данных, необходимые для немедленного импорта или экспорта. При необходимости можно сохранить пакет для последующего запуска или для доработки и расширения в среде [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Однако после сохранения пакета его следует добавить в существующий проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , прежде чем он станет доступным для запуска и изменения в среде [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
 В следующих разделах описано создание и удаление пакетов в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 Видеоматериалы, которые демонстрируют способ создания базового пакета с помощью шаблона пакетов по умолчанию, см. в статье [Создание базового пакета (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131023).  
  
### <a name="to-create-a-package-in-sql-server-data-tools-using-the-package-template"></a>Создание пакета в SQL Server Data Tools с использованием шаблона пакета  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , в котором необходимо создать пакет.  
  
2.  Находясь в обозревателе решений, правой кнопкой мыши щелкните папку **Пакеты служб SSIS** и выберите **Создать пакет служб SSIS**.  
  
3.  При необходимости добавьте к пакету поток управления, задачи потока данных и обработчики событий. Дополнительные сведения см. в разделах [Поток управления](control-flow/control-flow.md), [Поток данных](data-flow/data-flow.md) и [Обработчики событий в службах Integration Services (SSIS)](integration-services-ssis-event-handlers.md).  
  
4.  В меню **Файл** выберите команду **Сохранить выбранные элементы** , чтобы сохранить новый пакет.  
  
    > [!NOTE]  
    >  Можно сохранить пустой пакет.  
  
  
