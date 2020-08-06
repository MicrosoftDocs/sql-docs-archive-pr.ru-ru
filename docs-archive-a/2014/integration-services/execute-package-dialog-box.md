---
title: Диалоговое окно «Выполнение пакета» | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackageexecute.f1
- sql12.ssis.ssms.executepackage.f1
ms.assetid: 4f7a806d-4867-4d1f-bc65-b00c1caee7b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b60381054c781cd59f0a9d434710663b72d616c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665017"
---
# <a name="execute-package-dialog-box"></a>Execute Package Dialog Box
  Используйте диалоговое окно **Выполнение пакета** , чтобы запустить пакет, хранящийся на сервере служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 Пакет служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] может содержать параметры, значения которых хранятся в переменных среды. Перед выполнением такого пакета необходимо указать, какая среда будет применяться для задания значений переменных среды. Проект может содержать несколько сред, но для привязки значений переменных среды во время выполнения может использоваться только одна среда. Если в пакете не используются переменные среды, среда не требуется.  
  
 Выбор действия  
  
-   [Открытие диалогового окна «Выполнение пакета»](#open_dialog)  
  
-   [Задание параметров на странице «Общие»](#general)  
  
-   [Задание параметров на вкладке «Параметры»](#parameters)  
  
-   [Задание параметров на вкладке «Диспетчеры соединений»](#connection)  
  
-   [Задание параметров на вкладке «Дополнительно»](#advanced)  
  
-   [Создание скриптов параметров в диалоговом окне выполнения пакета](#script)  
  
##  <a name="open-the-execute-package-dialog-box"></a><a name="open_dialog"></a> Открытие диалогового окна «Выполнение пакета»  
  
1.  В среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]установите соединение с сервером служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
     Устанавливается соединение с экземпляром [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)], в котором размещена база данных SSISDB.  
  
2.  В обозревателе объектов разверните дерево для отображения узла **Каталоги служб Integration Services** .  
  
3.  Разверните узел **SSISDB** .  
  
4.  Разверните папку, содержащую пакет, который необходимо запустить.  
  
5.  Щелкните правой кнопкой мыши пакет и выберите команду **Выполнить**.  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> Задание параметров на странице «Общие»  
 Выберите **Среда** для указания среды, которая будет применена с запуском пакета.  
  
##  <a name="set-the-options-on-the-parameters-tab"></a><a name="parameters"></a> Задание параметров на вкладке «Параметры»  
 На вкладке **Параметры** измените значения параметров, которые используются при выполнении пакета.  
  
##  <a name="set-the-options-on-the-connection-managers-tab"></a><a name="connection"></a> Задание параметров на вкладке «Диспетчеры соединений»  
 На вкладке «Диспетчеры соединений» задайте свойства диспетчеров соединений пакета.  
  
##  <a name="set-the-options-on-the-advanced-tab"></a><a name="advanced"></a> Задание параметров на вкладке «Дополнительно»  
 На вкладке «Дополнительно» выполняется управление свойствами и другими параметрами пакета.  
  
 **Добавить**, **Изменить**, **Удалить**  
 Используйте эти кнопки для добавления, изменения или удаления свойства.  
  
 **Уровень ведения журнала**  
 Выберите уровень ведения журнала для выполнения пакета. Дополнительные сведения см. в разделе [catalog.set_execution_parameter_value (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database).  
  
 **Дамп при ошибках**  
 Укажите, будет ли при возникновении ошибок создаваться файл дампа во время выполнения пакета. Дополнительные сведения см. в статье [Generating Dump Files for Package Execution](troubleshooting/generating-dump-files-for-package-execution.md).  
  
 **32-разрядная среда выполнения**  
 Укажите, что пакет будет выполняться в 32-разрядной системе.  
  
##  <a name="scripting-the-options-in-the-execute-package-dialog-box"></a><a name="script"></a> Создание скриптов параметров в диалоговом окне выполнения пакета  
 Кроме того, в диалоговом окне **Выполнение пакета** вы можете использовать кнопку **Скрипт** на панели инструментов для записи кода [!INCLUDE[tsql](../includes/tsql-md.md)] . Созданный скрипт вызывает хранимые процедуры [catalog.start_execution (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) с теми же параметрами, которые были выбраны в диалоговом окне **Выполнение пакета**. Скрипт отображается в новом окне скрипта в среде [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
  
