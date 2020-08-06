---
title: Задача 9. Настройка службы ссылочных данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d0535fce-2bf5-4f6d-b517-ffe6fa13738d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1e7c685de13a2f5c495482f816818ff6b838fc7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751543"
---
# <a name="task-9-configuring-a-reference-data-service"></a>Задача 9. Настройка службы эталонных данных
  В этой задаче вы настраиваете DQS для использования службы ссылочных данных в Azure Marketplace. В следующей задаче будет настроен домен **проверки адресов** для использования этой службы. Во время выполнения операция очистки служб DQS передает значения доменов в домене **проверки адреса** службе для очистки. Дополнительные сведения см. [в статье Настройка служб DQS для использования справочных данных](https://msdn.microsoft.com/library/hh213070.aspx) .  
  
1.  На главной странице **клиента DQS**в области **Администрирование** щелкните **Конфигурация**.  
  
2.  Убедитесь, что вкладка **Ссылочные данные** активна.  
  
3.  В области **Параметры сети** введите соответствующие значения в полях **прокси-сервер** и **порт** , если для подключения к Интернету необходимо использовать прокси-сервер.  
  
4.  Введите **ключ учетной записи Azure Marketplace** для поля **идентификатор учетной записи DataMarket** .  
  
     ![Учетная запись службы эталонных данных Azure Data Market](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "Учетная запись службы эталонных данных Azure Data Market")  
  
5.  Нажмите кнопку **проверить** рядом с текстовым полем, чтобы проверить идентификатор учетной записи.  
  
6.  Нажмите кнопку **ОК** в окне сообщения.  
  
7.  Нажмите кнопку **Закрыть** в нижней части страницы, чтобы перейти на главную страницу клиента DQS.  
  
## <a name="next-task"></a>Следующая задача  
 [Задача 10. Настройка составного домена для использования службы эталонных данных](../../2014/tutorials/task-10-configuring-composite-domain-to-use-reference-data-service.md)  
  
  