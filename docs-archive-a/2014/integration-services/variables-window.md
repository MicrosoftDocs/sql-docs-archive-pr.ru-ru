---
title: Окно "Переменные" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.variables.f1
helpviewer_keywords:
- Variables Window dialog box
ms.assetid: f405e5ce-ef69-4c58-8c7d-a3d44dfe9ab0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ffd6da67386291c14ebf588da9a1cf8f399214b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666116"
---
# <a name="variables-window"></a>Окно переменных
  Окно **Переменные** используется для создания и изменения переменных, определяемых пользователем, и просмотра системных переменных.  
  
 По умолчанию окно **Переменные** располагается ниже области **Диспетчеры соединений** конструктора служб SSIS в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Если окно **Переменные** не отображается, выберите пункт **Переменные** в меню **Службы SSIS**, чтобы отобразить его.  
  
 При необходимости окно **Переменные** можно открыть, назначив команде View.Variables нужное сочетание клавиш на странице **Клавиатура** диалогового окна **Параметры** .  
  
> [!NOTE]
>  Первым символом в значениях свойств `Name` и `Namespace` согласно стандарту Юникод 2.0 должна быть буква или символ подчеркивания (_). Далее могут следовать буквы или цифры по определению стандарта Юникод 2.0 или символ подчеркивания (\_).  
  
## <a name="options"></a>Параметры  
 **Добавить переменную**  
 Добавить переменную, определяемую пользователем.  
  
 **Переместить переменную**  
 Выберите переменную из списка, а затем нажмите **Переместить переменную** , чтобы изменить область переменной. В диалоговом окне **Выбор новой области** выберите пакет, контейнер, задачу или обработчик событий в пакете, чтобы изменить область переменной.  
  
 Дополнительные сведения об области переменной см. в разделе [Переменные в службах Integration Services (SSIS)](integration-services-ssis-variables.md).  
  
 **Удалить переменную**  
 Выберите переменную из списка и щелкните **Удалить переменную**.  
  
 **Параметры сетки**  
 Нажмите, чтобы открыть диалоговое окно **Параметры сетки переменных** , в котором можно изменить выбор столбцов и применить фильтры к окну **Переменные** . Дополнительные сведения см. в статье [Параметры сетки переменных](../../2014/integration-services/variable-grid-options.md).  
  
 `Name`  
 Посмотреть имя переменной. Имена пользовательских переменных можно изменить.  
  
 **Область**  
 Посмотреть область переменной. Областью переменной может быть весь пакет, а также контейнер или задача. Область переменной должна быть достаточной, чтобы переменная была видна любым другим задачам и компонентам, которые должны считывать или устанавливать ее значение.  
  
 Можно изменить область, щелкнув переменную и нажав **Переместить переменную** в окне **Переменные** .  
  
 **Тип данных**  
 Посмотреть тип данных переменной. Для пользовательских переменных можно выбрать тип данных из списка.  
  
> [!NOTE]  
>  При присваивании выражения переменной тип данных нельзя изменить.  
  
 **Значение**  
 Посмотреть значение переменной. Значение пользовательской переменной можно изменить. Это значение может быть буквенным или представлять собой выражение, а значение может быть многостроковым. Чтобы назначить выражение переменной, нажмите кнопку троеточия рядом с столбцом **Выражение** в окне **Переменные** .  
  
 `Namespace`  
 Посмотреть имя пространства имен. Пользовательские переменные изначально создаются в пространстве имен **User** , но имя пространства имен можно изменить в `Namespace` поле. Для вывода этого столбца щелкните **Параметры сетки**.  
  
 **Создать событие изменения**  
 Указывает, будет ли активировано событие `OnVariableValueChanged` в случае изменения значения. Значение пользовательской и системной переменной можно изменить. По умолчанию окно **Переменные** не включает этот столбец. Для вывода этого столбца щелкните **Параметры сетки**.  
  
 **Описание**  
 Просмотр описания переменной. Можно изменить описание для пользовательских переменных. По умолчанию окно **Переменные** не включает этот столбец. Для вывода этого столбца щелкните **Параметры сетки**.  
  
 **Выражение**  
 Просмотр выражения, присвоенного переменной. Чтобы присвоить выражение, нажмите кнопку троеточия.  
  
 При присваивании выражения переменной рядом с переменной отображается специальный маркер значка. Этот специальный маркер значка отображается также рядом с диспетчерами соединений и задачами, для которых заданы выражения.  
  
## <a name="see-also"></a>См. также:  
 [Переменные в службах Integration Services (SSIS)](integration-services-ssis-variables.md)   
 [Использование переменных в пакетах](../../2014/integration-services/use-variables-in-packages.md)   
 [Выражения&#41; Integration Services &#40;SSIS](expressions/integration-services-ssis-expressions.md)   
 [Создание файлов дампа для выполнения пакетов](troubleshooting/generating-dump-files-for-package-execution.md)  
  
  