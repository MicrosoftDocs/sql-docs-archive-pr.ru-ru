---
title: Задание свойств элемента управления очередностью | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Precedence Constraint Editor dialog box
- precedence constraints [Integration Services], properties
ms.assetid: d990f600-5c09-4cd5-8528-0a58d79dc9f2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 55b95bdb79d801156bef6198bc0f57accb5d9517
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667791"
---
# <a name="set-the-properties-of-a-precedence-constraint"></a>Установка свойств управления очередностью
  Для установки свойств элементов управления очередностью можно использовать следующие средства.  
  
-   Можно воспользоваться диалоговым окном **Редактор управления очередностью** .  
  
-   Можно использовать окно «Свойства». Окно «Свойства» содержит свойства для настройки элементов управления очередностью, недоступные в диалоговом окне **Редактор управления очередностью** . В окне «Свойства» можно указать описание и имя управления очередностью и настроить заметку, которая будет отображена для управления очередностью в области конструктора.  
  
 Следующие процедуры описывают способы настройки свойств элементов управления очередностью с помощью этих средств.  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-precedence-constraint-editor"></a>Настройка свойств управления очередностью с помощью редактора управления очередностью  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Перейдите на вкладку **Поток управления** .  
  
4.  Дважды щелкните объект управления очередностью.  
  
     Открывается **Редактор управления очередностью** .  
  
5.  В раскрывающемся списке **Операция оценки** выберите операцию оценки.  
  
6.  В раскрывающемся `Value` списке выберите результат выполнения приоритетного исполняемого объекта.  
  
7.  Если в операции вычисления используется выражение, в `Expression` поле введите выражение и нажмите кнопку **проверить** , чтобы оценить выражение.  
  
    > [!NOTE]  
    >  В именах переменных учитывается регистр букв.  
  
8.  Если к исполняемому объекту с ограничением подключено несколько задач или контейнеров, выберите **логическое и** , чтобы указать, что результаты выполнения всех предшествующих исполняемых файлов должны иметь значение `true` . Выберите **логическое или** , чтобы указать, что только один результат выполнения должен иметь значение `true` .  
  
9. Нажмите кнопку **ОК** , чтобы закрыть **Редактор управления очередностью**.  
  
10. Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-properties-window"></a>Настройка свойств управления очередностью с помощью редактора управления очередностью  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий пакет, который необходимо изменить.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Перейдите на вкладку **поток управления** . В области конструктора на вкладке **поток управления** щелкните правой кнопкой мыши элемент Управление очередностью и выберите пункт **свойства**. В окне «Свойства» измените значения свойств.  
  
4.  В окне **Свойства** установите следующие свойства элементов управления очередностью, доступные для чтения-записи.  
  
    |Свойство, доступное для чтения-записи|Действие настройки|  
    |--------------------------|--------------------------|  
    |Описание|Введите описание.|  
    |EvalOp|Выберите операцию вычисления. Если `Expression` выбрана операция, **ExpressionAndConstant**или **ExpressionOrConstant** , можно указать выражение.|  
    |Выражение|Если операция вычисления включает в себя выражение, введите выражение. Выражение должно иметь логическое значение. Дополнительные сведения о языке выражений см. в разделе [Выражения служб Integration Services (SSIS)](expressions/integration-services-ssis-expressions.md).|  
    |LogicalAnd|Задайте значение, `LogicalAnd` указывающее, вычисляется ли управление очередностью вместе с другими ограничениями очередностью, когда несколько исполняемых объектов предшествуют и связываются с исполняемым объектом с ограничением.|  
    |Имя|Обновите имя элемента управления очередностью.|  
    |ShowAnnotation|Укажите тип заметки, который должен использоваться. Выберите значение **Never** , чтобы отключить заметки, **AsNeeded** , чтобы разрешить заметки по запросу, **ConstraintName** , чтобы автоматически вставлять заметки, используя значения свойства Name, **ConstraintDescription** , чтобы автоматически вставлять заметки, используя значения свойства Description, и **ConstraintOptions** , чтобы автоматически вставлять заметки, используя значения свойств Value и Expression.|  
    |Значение|Если операция вычисления, указанная в свойстве EvalOP, содержит ограничение, выберите результат выполнения исполняемого объекта с ограничением.|  
  
5.  Закройте окно «Свойства».  
  
6.  Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также:  
 [Управление очередностью](control-flow/precedence-constraints.md)   
 [Подключение задач и контейнеров с помощью управления очередностью по умолчанию](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)   
 [Установка значения управления очередностью с помощью контекстного меню](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)   
 [Использование выражения в элементах управлении очередностью](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  