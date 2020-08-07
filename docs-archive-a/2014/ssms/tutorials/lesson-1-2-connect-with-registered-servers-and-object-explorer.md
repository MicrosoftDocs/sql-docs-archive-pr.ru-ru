---
title: Подключение к зарегистрированным серверам и к обозревателю объектов | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: d6b3911f-68b4-4483-831b-df89d6400add
author: stevestein
ms.author: sstein
ms.openlocfilehash: b4bc75ad7f3682765dc102064a5621cd541ccd12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727822"
---
# <a name="connect-with-registered-servers-and-object-explorer"></a>Подключение к зарегистрированным серверам и к обозревателю объектов
  В этом учебнике показано, как использовать зарегистрированные серверы и обозреватель объектов.  
  
 В этом учебнике используется образец базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . По соображениям безопасности образцы базы данных по умолчанию не устанавливаются. Дополнительные сведения см. в разделе [Установка образцов кода и образцов баз данных SQL Server](http://sqlserversamples.codeplex.com).  
  
## <a name="connecting-to-servers"></a>Подключение к серверам  
 Панель инструментов компонента «Зарегистрированные серверы» содержит кнопки для компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], а также служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]и [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Можно зарегистрировать один или более из этих типов серверов, чтобы упростить управление ими. В этом упражнении предстоит зарегистрировать базу данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
#### <a name="to-register-the-database"></a>Регистрация базы данных  
  
1.  Если потребуется, на панели инструментов "Зарегистрированные серверы" нажмите кнопку **Ядро СУБД** . (Этот режим может быть уже выбран).  
  
2.  Разверните узел **Ядро СУБД**.  
  
3.  Щелкните правой кнопкой мыши пункт **Группы локальных серверов**и выберите пункт **Регистрация нового сервера**.  
  
4.  В диалоговом окне **Регистрация нового сервера** в текстовом поле **Имя сервера** введите имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  В поле **Имя зарегистрированного сервера** введите [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
6.  На вкладке **Свойства соединения** в списке **Подключение к базе данных** выберите **\<Browse server...>** .  
  
7.  В диалоговом окне **Просмотр баз данных** нажмите кнопку **Да**.  
  
8.  В диалоговом окне **Поиск базы данных на сервере** выберите [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]и нажмите кнопку **ОК**.  
  
9. Чтобы убедиться в том, что сервер был зарегистрирован правильно, нажмите кнопку **Проверка**.  
  
10. В диалоговом окне **Регистрация нового сервера** нажмите кнопку **Сохранить**.  
  
## <a name="connecting-with-object-explorer"></a>Подключение с помощью обозревателя объектов  
 Как и зарегистрированные серверы, обозреватель объектов может подключаться к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)], а также к службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
#### <a name="to-connect-with-object-explorer"></a>Подключение с помощью обозревателя объектов  
  
1.  На панели инструментов обозревателя объектов нажмите кнопку **Подключиться** , чтобы раскрыть список возможных типов соединений, а затем выберите параметр **Ядро СУБД**.  
  
2.  В диалоговом окне **Соединение с сервером** в поле **Имя сервера** введите имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Нажмите кнопку **Параметры** и изучите доступные варианты.  
  
4.  Для подключения к серверу нажмите **Подключиться**. Если соединение уже установлено, последует возврат в окно обозревателя объектов с фокусом, установленным на нужном сервере.  
  
     С помощью обозревателя объектов можно управлять системой безопасности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , репликацией и компонентом Database Mail. Обозреватель объектов позволяет управлять лишь некоторыми из возможностей служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]и [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Каждый из этих компонентов имеет дополнительные специальные инструменты работы.  
  
5.  В обозревателе объектов разверните папку **Базы данных** и выберите [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
     Обратите внимание, что в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] системные базы данных находятся в отдельной папке.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Изменение макета окружения](lesson-1-3-change-the-environment-layout.md)  
  
  
