---
title: Служебная программа настройки сервера (надстройки интеллектуального анализа данных для Excel) | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 28435f86-5cec-4a1e-9b7d-b2069c1ddddb
author: minewiskan
ms.author: owend
ms.openlocfilehash: f985338e44bf0f4b591fcb70a4e093901626149f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752408"
---
# <a name="server-configuration-utility-data-mining-add-ins-for-excel"></a>Средство настройки сервера (надстройки интеллектуального анализа данных для Excel)
  При установке надстроек интеллектуального анализа данных для Excel также устанавливается служебная программа настройки сервера, которая будет запускаться при первом открытии надстроек. В этом разделе описывается, как использовать программу для подключения к экземпляру [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] и настройки базы данных для работы с моделями интеллектуального анализа данных.  
  

  
##  <a name="step-1-connect-to-analysis-services"></a><a name="bkmk_step1"></a>Шаг 1. подключение к Analysis Services  
 Выберите сервер служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], который будет предоставлять алгоритмы и сохранять модели интеллектуального анализа данных.  
  
 При создании соединения для интеллектуального анализа данных необходимо выбрать сервер, где можно поэкспериментировать с моделями интеллектуального анализа данных. Рекомендуется создать новую базу данных на сервере и выделить ее для интеллектуального анализа данных либо попросить администратора подготовить сервер интеллектуального анализа данных. Это позволит строить модели, не оказывая влияния на производительность других служб.  
  
 Обратите внимание, что сервер служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], используемый для интеллектуального анализа данных, не должен обязательно находиться на одном сервере с исходными данными.  
  
 **Имя сервера**  
 Введите имя сервера с установленным экземпляром служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], который будет использоваться для интеллектуального анализа данных.  
  
 **Аутентификация**  
 Укажите методы проверки подлинности. Если администратор еще не настроил доступ к серверу с помощью HTTPPump, то для соединения со службами [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] требуется проверка подлинности Windows.  
  
##  <a name="step-2-allow-temporary-models"></a><a name="bkmk_step2"></a>Шаг 2. Разрешение временных моделей  
 Перед использованием надстроек необходимо изменить свойство сервера служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] так, чтобы оно разрешало создание временных моделей интеллектуального анализа данных.  
  
 Временные модели интеллектуального анализа данных также называются *моделями сеансов*. Это связано с тем, что эти модели сохраняются, только пока открыт текущий сеанс. Как только соединение с сервером закрывается, сеанс заканчивается и все модели, использовавшиеся во время сеанса, удаляются.  
  
 Использование моделей интеллектуального анализа данных сеанса не влияет на объем памяти на сервере, но нагрузка, вызванная созданием моделей, может повлиять на производительность сервера.  
  
 Вначале мастер определяет заданные на сервере параметры. Если сервер уже допускает временные модели интеллектуального анализа данных, можно нажать кнопку **Далее** , чтобы продолжить. Мастер также показывает инструкции для включения временных моделей интеллектуального анализа данных на указанном сервере служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] или для выполнения запроса системному администратору служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
##  <a name="step-3-create-database-for-add-in-users"></a><a name="bkmk_step3"></a>Шаг 3. Создание базы данных для пользователей надстроек  
 На этой странице мастера установки и настройки можно создать новую базу данных, которая будет предназначена для интеллектуального анализа данных, или выбрать существующую базу данных [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
> [!WARNING]  
>  Для интеллектуального анализа данных требуется экземпляр служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], работающий в многомерном режиме. Табличный режим не поддерживает интеллектуальный анализ данных.  
  
 Рекомендуется создать отдельную базу данных, специально предназначенную для интеллектуального анализа данных. Это позволит экспериментировать с моделями интеллектуального анализа данных, не оказывая влияния на другие объекты решения.  
  
 Если выбрана существующая база данных на экземпляре служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], убедитесь, что можно перезаписать существующие модели, если окажется, что при создании модели с помощью надстроек модель с таким именем уже существует.  
  
 **Создание базы данных**  
 Выберите этот параметр для создания новой базы данных на заданном сервере. В базе данных интеллектуального анализа данных будут храниться источники данных, структуры и модели интеллектуального анализа данных.  
  
 **Имя базы данных**  
 Введите имя новой базы данных. Если имя не используется, оно будет создано.  
  
 **Использовать существующую базу данных**  
 Выберите этот параметр для использования существующей базы данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 **База данных**  
 Если используется существующая база данных, следует выбрать ее имя из списка.  
  
##  <a name="step-4-give-add-in-users-appropriate-permissions"></a><a name="bkmk_step4"></a>Шаг 4. предоставление пользователям соответствующих разрешений на доступ к надстройкам  
 Следует убедиться, что все пользователи, включая пользователей надстроек, имеют необходимые разрешения на просмотр, изменение, обработку или создание структур и моделей интеллектуального анализа данных.  
  
 По умолчанию для использования надстроек требуется встроенная проверка подлинности Windows.  
  
 **Предоставить пользователям надстроек административные разрешения**  
 Выберите этот параметр для предоставления заданным пользователям административного доступа к базе данных.  
  
> [!NOTE]  
>  Эти разрешения применяются только к базе данных, указанной в поле **имя базы данных** .  
  
 **Имя базы данных**  
 Отображает имя выбранной базы данных.  
  
 **Пользователи или группы для добавления**  
 Выберите имена входа, которые будут иметь доступ к базе данных, используемой для интеллектуального анализа данных.  
  
 **Добавление**  
 Нажмите, чтобы открыть диалоговое окно и добавить пользователей или группы.  
  
 **Удалить**  
 Нажмите, чтобы удалить выбранного пользователя или выбранную группу из списка пользователей с административными разрешениями.  
  
  