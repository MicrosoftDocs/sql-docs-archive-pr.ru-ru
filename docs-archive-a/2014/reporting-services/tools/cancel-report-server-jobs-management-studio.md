---
title: Отмена заданий сервера отчетов (Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.cancelreportserverjobs.f1
ms.assetid: 1c5b4975-49e9-4d0b-b298-2638e81edbfd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0ef8ada32aab4ac368871da711d0fe63fff7620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737910"
---
# <a name="cancel-report-server-jobs-management-studio"></a>Отмена заданий сервера отчетов (среда Management Studio)
  Диалоговое окно **Отмена заданий сервера отчетов** позволяет просмотреть или отменить выполняющиеся отчеты. В этом диалоговом окне отображаются все задания, выполняемые в данный момент на сервере отчетов. Несмотря на то, что выполняемые задания нельзя приостановить или перезапустить, задачи, завершение которых требует слишком долгого времени, можно отменить — все сразу или по отдельности.  
  
 Отменить можно как пользовательские, так и системные задания.  
  
-   Пользовательским заданием является любое задание, инициированное отдельным пользователем. Сюда входит запуск отчета по требованию, создание моментального снимка журнала отчета или создание снимка состояния выполнения отчета вручную. Выполняющаяся обычная подписка также является пользовательским заданием.  
  
-   Системным заданием является задание, инициируемое сервером отчетов. К системным заданиям относится плановая обработка отчетов.  
  
 Чтобы открыть эту страницу, запустите среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], подключитесь к серверу отчетов, щелкните **Задания**правой кнопкой мыши и выберите команду **Отменить все задания**. Можно также открыть **Задания**, щелкнуть задание, выполняемое на сервере отчетов, правой кнопкой мыши и выбрать команду **Отменить задание**.  
  
 Прежде чем отменить какое-либо задание, можно просмотреть его свойства и определить, когда оно было запущено. Дополнительные сведения см. в разделе [Свойства задания &#40;Management Studio&#41;](job-properties-management-studio.md).  
  
> [!NOTE]  
>  Эта функция не поддерживается в [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services. Эта страница не отображается при запуске выпуска [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].  
  
## <a name="options"></a>Параметры  
 **Название**  
 Отображается имя отчета. Подписки идентифицируются описаниями.  
  
 **Тип**  
 Допустимы следующие значения: **Пользовательское** и **Системное**.  
  
 **Start Time**  
 Указывается время запуска задания.  
  
 **Имя пользователя**  
 Для заданий, запущенных пользователем, в этом столбце отображается имя пользователя.  
  
 **Состояние**  
 Показывается состояние задания. Допустимы следующие значения: **Новое** и **Выполняется**. В начале выполнения задание всегда имеет состояние **Новое** . Через 60 секунд состояние меняется на **Выполняется**. Чтобы отобразить это изменение, необходимо обновить страницу.  
  
 **OK**  
 Отменяет отдельное задание или несколько заданий. Отмена заданий осуществляется немедленно, и их возобновление невозможно. Если отмена задания была выполнена ошибочно, нужно запустить новое задание, повторно отправив запрос на выполнение отчета или подписки.  
  
## <a name="see-also"></a>См. также:  
 [Справка F1 по использованию сервера отчетов среде Management Studio](report-server-in-management-studio-f1-help.md)   
 [Подключение к серверу отчетов в среде Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Управление запущенным процессом](../subscriptions/manage-a-running-process.md)  
  
  