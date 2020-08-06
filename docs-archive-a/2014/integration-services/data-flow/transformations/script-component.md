---
title: Компонент скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponentdetails.f1
helpviewer_keywords:
- Script transformation
- scripts [Integration Services], transformations
- Script component [Integration Services], about Script component
- Script component [Integration Services]
ms.assetid: 131c2d0c-2e33-4785-94af-ada5c049821e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: af8e500e399b0f69a7e34c9e2e01c74d83256107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752312"
---
# <a name="script-component"></a>Компонент скрипта
  Компонент скрипта размещает скрипт и позволяет пакету включать и выполнять пользовательский код скрипта. Можно использовать компонент скрипта в пакетах для следующих целей.  
  
-   Применить множественные преобразования к данным, вместо того, чтобы использовать множественные преобразования в потоке данных. Например, скрипт может добавить значения в два столбца и затем вычислить среднее значение суммы.  
  
-   Получить доступ к бизнес-правилам в существующей сборке .NET. Например, скрипт может применить бизнес-правило, определяющее диапазон правильных значений в столбце `Income`.  
  
-   Использовать пользовательские формулы и функции в дополнение к функциям и операторам, которые предоставляет грамматика выражений служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] . Например, можно проверить номера кредитных карт, используя формулу LUHN.  
  
-   Проверить данные столбца на правильность и не учитывать записи, содержащие недопустимые данные. Например, скрипт может определять адекватность почтовых расходов и пропускать записи с очень большими или очень маленькими суммами.  
  
 Компонент скрипта обеспечивает простой и быстрый путь включения пользовательских функций в поток данных. Однако, если планируется многократное использование кода скрипта во множестве пакетов, необходимо рассмотреть программирование пользовательского компонента вместо использования компонента скрипта. Дополнительные сведения см. в разделе [Разработка пользовательского компонента потока данных](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
> [!NOTE]  
>  Если компонент скрипта содержит скрипт, пытающийся прочесть значение столбца, равное NULL, то при запуске пакета компонент скрипта завершится с ошибкой. Рекомендуется, чтобы скрипт использовал метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.IsNull%2A> для определения того, является ли столбец значением NULL, перед попыткой чтения значения столбца.  
  
 Компонент скрипта может быть использован как источник, преобразование или назначение. Компонент поддерживает один вход и множество выходов. В зависимости от того, как компонент используется, он поддерживает либо вход, либо выход, либо и вход и выход одновременно. Скрипт вызывается каждой строкой на входе или выходе.  
  
-   Если используется как источник, компонент скрипта поддерживает множество выходов.  
  
-   Если используется как преобразование, компонент скрипта поддерживает один вход и множество выходов.  
  
-   Если используется как назначение, компонент скрипта поддерживает один вход.  
  
 Компонент скрипта не поддерживает выход ошибок.  
  
 После того как выбран подходящий компонент скрипта для пакета, нужно настроить входы и выходы, разработать скрипт, используемый компонентом, и настроить сам компонент.  
  
## <a name="understanding-the-script-component-modes"></a>Основные сведения о режимах компонента скрипта  
 В конструкторе [!INCLUDE[ssIS](../../../includes/ssis-md.md)] у компонента скрипта есть два режима: режим конструирования метаданных и режим конструирования кода. В режиме редактирования метаданных можно добавлять и изменять входы и выходы компонента скрипта, но нельзя писать код. После того как все входы и выходы настроены, переключаетесь в режим редактирования кода, чтобы написать скрипт. Компонент скрипта автоматически создает базовый код из метаданных входов и выходов. Если пользователь изменил метаданные после того, как компонент скрипта создал базовый код, то пользовательский код больше не может быть откомпилированным, потому что измененный базовый код может быть несовместим с пользовательским кодом.  
  
## <a name="writing-the-script-that-the-component-uses"></a>Разработка скрипта, используемого компонентом  
 Компонент скрипта использует для создания скриптов среду [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA). Доступ к VSTA осуществляется из **Редактора преобразования «Скрипт»** . Дополнительные сведения см. в разделе [Редактор преобразования "Скрипт" (страница "Скрипт")](../../script-transformation-editor-script-page.md).  
  
 Компонент скрипта содержит проект VSTA, который включает автоматически создающийся класс, называемый ScriptMain, представляющий метаданные компонента. Например, если компонент скрипта используется как преобразование, имеющее три выхода, ScriptMain содержит метод для каждого выхода. ScriptMain — это точка входа в скрипт.  
  
 Среда VSTA располагает всеми стандартными возможностями среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] , в том числе редактором [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] с цветовым выделением, технологией IntelliSense и браузером объектов. Скрипт, используемый компонентом скрипта, сохранен в определении пакета. При конструировании пакета код скрипта временно записывается в файл проекта.  
  
 Среда VSTA поддерживает языки программирования [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# и [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic.  
  
 Сведения по программированию компонента скрипта см. в разделе [Расширение потока данных с помощью компонента скрипта](script-component.md). Дополнительные сведения о способах настройки компонента скрипта как источника, преобразования или назначения см. в разделе [Developing Specific Types of Script Components](../../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md). Дополнительные примеры, например назначение «ODBC», в которых показано использование компонента скрипта, см. в разделе [Additional Script Component Examples](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).  
  
> [!NOTE]  
>  В отличие от предыдущих версий, где можно было указать, являются ли скрипты предварительно скомпилированными, в версии [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] и более поздних версиях все скрипты компилируются заранее. Если скрипт компилируется заранее, то во время выполнения не загружается языковая подсистема и пакет выполняется быстрее. Однако заранее скомпилированные двоичные файлы занимают значительное место на диске.  
  
## <a name="configuring-the-script-component"></a>Настройка компонента скрипта  
 Можно настроить компонент скрипта следующими способами.  
  
-   Выберите входные столбцы, на которые необходимо ссылаться.  
  
    > [!NOTE]  
    >  При использовании конструктора служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] можно настроить только один вход.  
  
-   Предоставьте скрипт, выполняемый компонентом.  
  
-   Укажите язык скрипта.  
  
-   Предоставьте разделенные запятыми списки переменных с разрешениями «только чтение» и «чтение и запись».  
  
-   Добавьте больше выходов, а также выходные столбцы, которым скрипт присваивает значения.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
### <a name="configuring-the-script-component-in-the-designer"></a>Настройка компонента скрипта в конструкторе  
 Дополнительные сведения о свойствах, которые можно установить в диалоговом окне **Редактор преобразования «Скрипт»** , см. в следующих разделах:  
  
-   [Редактор преобразования "Скрипт" (страница "Входные столбцы")](../../script-transformation-editor-input-columns-page.md)  
  
-   [Редактор преобразования "Скрипт" (страница "Входы и выходы")](../../script-transformation-editor-inputs-and-outputs-page.md)  
  
-   [Редактор преобразования "Скрипт" (страница "Скрипт")](../../script-transformation-editor-script-page.md)  
  
-   [Редактор преобразования "Скрипт" (страница "Диспетчеры соединений")](../../script-transformation-editor-connection-managers-page.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Установление свойств компонента потока данных](../set-the-properties-of-a-data-flow-component.md)  
  
### <a name="configuring-the-script-component-programmatically"></a>Программная настройка компонента скрипта  
 Дополнительные сведения о свойствах, которые можно установить в окне **Свойства** или программно, см. в следующих разделах:  
  
-   [Общие свойства](../../common-properties.md)  
  
-   [Пользовательские свойства преобразований](transformation-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в следующих разделах.  
  
-   [Установление свойств компонента потока данных](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a>См. также  
 [Преобразования служб Integration Services](integration-services-transformations.md)  
  
 [Расширение потока данных с помощью компонента скрипта](script-component.md)  
  
  