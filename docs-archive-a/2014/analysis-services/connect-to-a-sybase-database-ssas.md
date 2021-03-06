---
title: Подключение к базе данных Sybase (SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsybasedb.f1
ms.assetid: b4ebdc57-8b2a-4950-b489-88360e6c82c5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 111334ca21d04ad27d306fcb27a6d9b8210e26eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656727"
---
# <a name="connect-to-a-sybase-database-ssas"></a>Соединение с базой данных Sybase (SSAS)
  Эта страница **мастера импорта таблиц** используется для задания параметров для соединения с базой данных Sybase. Для доступа к мастеру из [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]выберите пункт **Импорт из источника данных** в меню **Модель**.  
  
 Для соединения с источником данных на компьютере должен быть установлен соответствующий поставщик.  
  
> [!NOTE]  
>  При выборе базы данных на этой странице используются учетные данные текущего пользователя. Тем не менее импорт не будет успешным, если пользователь, указанный на странице сведений об олицетворении, не имеет достаточных прав для чтения из выбранной базы данных.  
  
## <a name="ui-element-list"></a>Список элементов пользовательского интерфейса  
 **Понятное имя соединения**  
 Введите уникальное имя для соединения с источником данных. Это поле является обязательным.  
  
 **Имя сервера**  
 Введите или выберите экземпляр сервера для подключения.  
  
 **User name**  
 Укажите имя пользователя для подключения к базе данных.  
  
 Это имя пользователя используется при создании строки подключения для источника данных. Эти учетные данные также используются при просмотре и фильтрации данных в окне «Свойства таблицы» и в мастере импорта. Эти учетные данные не используются для импорта или обновления данных. Вместо них используются учетные данные Windows, указанные на странице сведений об олицетворении.  
  
 **Пароль**  
 Укажите пароль для подключения к базе данных.  
  
 **Сохранить мой пароль**  
 Укажите, нужно ли сохранить пароль, введенный в поле **Пароль** .  
  
 **Имя базы данных**  
 Выберите базу данных из списка баз данных.  
  
 **Дополнительно**  
 Задайте дополнительные свойства соединения в диалоговом окне **Задание дополнительных свойств** . Дополнительные сведения см. в разделе [Установка дополнительных свойств (SSAS)](set-advanced-properties-ssas.md).  
  
 **Проверка соединения**  
 Установите соединение с источником данных с использованием текущих параметров. Появится сообщение об успешном или неуспешном соединении.  
  
  
