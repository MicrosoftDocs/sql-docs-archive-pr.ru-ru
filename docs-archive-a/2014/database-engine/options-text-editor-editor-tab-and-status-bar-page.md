---
title: 'Параметры (текстовый редактор: вкладка редактора и страница строки состояния) | Документация Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqleditors.editorcontextsettings
- VS.ToolsOptionsPages.Text_Editor.EditorTabAndStatusBar
ms.assetid: e4815678-7885-4631-878f-c6a2b857ee05
author: rothja
ms.author: jroth
ms.openlocfilehash: 920b7d48b5f7a2472a521af21c8217b1adba486a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667392"
---
# <a name="options-text-editor-editor-tab-and-status-bar-page"></a>Параметры (страница "Текстовый редактор" — "Вкладка редактора и строка состояния")
  На странице **Вкладка редактора и строка состояния** можно настроить сведения, которые показываются в редакторах запросов [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] . Можно указать уровень сведений, отображаемых на вкладке и в строке состояния редактора запросов, а также место расположения строки состояния: вверху или внизу окна редактора.  
  
## <a name="option-settings-by-editor"></a>Параметры, задаваемые с помощью редактора  
 Вкладка редактора и строка состояния доступны во всех редакторах среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , однако они отличаются разным уровнем функциональности.  
  
 Редактор запросов Database Engine может подключаться к группе серверов, в этом случае он открывает соединения со всеми экземплярами в группе серверов и может одновременно запускать один и тот же запрос для каждого соединения. В этом диалоговом окне можно указать, что строка состояния будет иметь другой цвет при подключении к нескольким экземплярам вместо одного. Изменить параметры результатов для нескольких серверов можно на странице [Параметры (результаты запроса/SQL Server/многосерверные)](../../2014/database-engine/options-query-results-sql-server-multi-server.md).  
  
## <a name="status-bar-content"></a>Содержимое строки состояния  
 Определяет сведения, которые отображаются в строке состояния редактора запросов.  
  
 **Отображать время выполнения**  
 Включает время выполнения скрипта. Доступны следующие параметры.  
  
 **None**  
 В строке состояния не отображаются сведения о времени.  
  
 **END**  
 В строке состояния отображается текущее время, пока выполняется скрипт. По завершении скрипта показывается время окончания скрипта.  
  
 **Затраченное**  
 В строке состояния отображается продолжительность выполнения скрипта на данный момент. По завершении скрипта показывается общая продолжительность выполнения скрипта.  
  
 **Включить имя базы данных**  
 Включает имя текущей базы данных для данного соединения. При первом открытии редактора запросов это база данных по умолчанию для имени входа. Контекст базы данных можно сменить позже с помощью инструкции USE языка Transact-SQL.  
  
 **Включить имя входа**  
 Включает имя входа.  
  
 **Отображать количество строк**  
 Включает количество строк, которые были обработаны скриптом, выполняемым в настоящее время.  
  
 **Включить имя сервера**  
 Включает имя сервера. Для локальных соединений это имя экземпляра. Для удаленных соединений это имя удаленного компьютера и имя экземпляра.  
  
## <a name="status-bar-layout-and-colors"></a>Макет и цвета строки состояния  
 Указывает цвета для элементов в строке состояния редактора запросов.  
  
 **Групповые соединения**  
 Установите цвет строки состояния, применяемый, если редактор запросов имеет больше одного соединения.  
  
 **Соединения с одиночным сервером**  
 Установите цвет строки состояния, применяемый, если редактор запросов имеет одно соединение.  
  
 **Расположение строки состояния**  
 Указывает расположение строки состояния. Доступны следующие параметры.  
  
 **Top**  
 Строка состояния появляется в верхней части окна редактора запросов.  
  
 **Последние**  
 Строка состояния появляется в нижней части окна редактора запросов.  
  
## <a name="tab-text"></a>Текст вкладки  
 Задает текст, который появляется на вкладке в верхней части окна «Редактор запросов». Если текста слишком много, чтобы его отобразить, можно просмотреть полную строку во всплывающей подсказке, которая появляется при наведении указателя мыши на вкладку.  
  
 **Включить имя базы данных**  
 Включает имя текущей базы данных для данного соединения. При первом открытии редактора запросов это база данных по умолчанию для имени входа. Контекст базы данных можно сменить позже с помощью инструкции USE языка Transact-SQL.  
  
 **Включить имя файла**  
 Включает имя файла, в котором хранится скрипт.  
  
 **Включить имя папки**  
 Включает путь к папке, в которой хранится файл скрипта.  
  
 **Включить имя входа**  
 Включает имя входа.  
  
 **Включить имя сервера**  
 Включает имя сервера. Для локальных соединений это имя экземпляра. Для удаленных соединений это имя удаленного компьютера и имя экземпляра.  
  
## <a name="see-also"></a>См. также:  
 [Параметры &#40;среда: страница "шрифты и цвета"&#41;](../ssms/menu-help/options-environment-fonts-and-colors-page.md)   
 [Выделение цветом в редакторах запросов](../relational-databases/scripting/color-coding-in-query-editors.md)  
  
  