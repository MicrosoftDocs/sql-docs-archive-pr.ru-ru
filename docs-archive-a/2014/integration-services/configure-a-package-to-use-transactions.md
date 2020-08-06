---
title: Настройка пакета для использования транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], configuring packages to use
ms.assetid: 8bf14957-27b4-456b-81d9-e1a0e0ca94b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f469c2439deb2d16ac9046a1628e82c34e39b31d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729721"
---
# <a name="configure-a-package-to-use-transactions"></a>Настройка пакета для использования транзакций
  Существуют два режима настройки пакета для использования транзакций.  
  
-   Одна транзакция на пакет. В этом случае *инициирует* транзакцию сам пакет, а индивидуальные задачи и контейнеры пакета участвуют в этой одиночной транзакции.  
  
-   Несколько транзакций на пакет. В этом случае пакет поддерживает транзакции, но в действительности инициируют эти транзакции индивидуальные задачи и контейнеры пакета.  
  
 В следующих двух процедурах описывается настройка в каждом из режимов.  
  
## <a name="configuring-a-single-transaction"></a>Настройка варианта с одиночной транзакцией  
 В этом режиме инициирует одиночную транзакцию сам пакет. Настройте пакет для инициации этой транзакции, задав для свойства TransactionOption пакета значение `Required` .  
  
 Далее, прикрепите к этой одиночной транзакции конкретные задачи и контейнеры. Чтобы прикрепить задачу или контейнер в транзакции, задайте для свойства TransactionOption этой задачи или контейнера значение `Supported` .  
  
#### <a name="to-configure-a-package-to-use-a-single-transaction"></a>Настройка пакета для использования одиночной транзакции  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] с пакетом, который необходимо настроить на использование транзакции.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Перейдите на вкладку **Поток управления** .  
  
4.  Щелкните правой кнопкой мыши в области конструктора потока управления и выберите **Свойства**.  
  
5.  В окне **Свойства** задайте для свойства TransactionOption значение `Required` .  
  
6.  Чтобы зарегистрировать задачу или контейнер в транзакции, щелкните их правой кнопкой мыши в рабочей области конструирования на вкладке **Поток управления** , а затем выберите пункт **Свойства**.  
  
7.  В окне **Свойства** задайте для свойства TransactionOption значение `Supported` .  
  
    > [!NOTE]  
    >  Чтобы прикрепить соединение к транзакции, зарегистрируйте в транзакции задачи, использующие это соединение. Дополнительные сведения см. в разделе [Соединения в службах Integration Services (SSIS)](connection-manager/integration-services-ssis-connections.md).  
  
8.  Повторите шаги 6 и 7 для каждой задачи и контейнера, которые должны быть зарегистрированы в транзакции.  
  
## <a name="configuring-multiple-transactions"></a>Настройка варианта с множественными транзакциями  
 В этом режиме пакет сам по себе поддерживает транзакции, но не запускает их. Настройте пакет для поддержки транзакций, задав для свойства TransactionOption пакета значение `Supported` .  
  
 Далее настройте задачи и контейнеры пакета, которые должны инициировать транзакции или участвовать в них. Чтобы настроить задачу или контейнер для инициации транзакции, задайте для свойства TransactionOption этой задачи или контейнера значение `Required` .  
  
#### <a name="to-configure-a-package-to-use-multiple-transactions"></a>Настройка пакета для использования множественных транзакций  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий пакет, который нужно настроить для использования транзакций.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Перейдите на вкладку **Поток управления** .  
  
4.  Щелкните правой кнопкой мыши в области конструктора потока управления и выберите **Свойства**.  
  
5.  В окне **Свойства** задайте для свойства TransactionOption значение `Supported` .  
  
    > [!NOTE]  
    >  Пакет поддерживает транзакции, но транзакции запускаются задачами или контейнерами в пакете.  
  
6.  В рабочей области конструирования на вкладке **Поток управления** щелкните правой кнопкой мыши задачу или контейнер в пакете, для которого необходимо начать транзакцию, и выберите пункт **Свойства**.  
  
7.  В окне **Свойства** задайте для свойства TransactionOption значение `Required` .  
  
8.  Если транзакция начата контейнером, щелкните правой кнопкой мыши задачу или контейнер, которые необходимо зарегистрировать в транзакции, и выберите пункт **Свойства**.  
  
9. В окне **Свойства** задайте для свойства TransactionOption значение `Supported` .  
  
    > [!NOTE]  
    >  Чтобы прикрепить соединение к транзакции, зарегистрируйте в транзакции задачи, использующие это соединение. Дополнительные сведения см. в разделе [Соединения в службах Integration Services (SSIS)](connection-manager/integration-services-ssis-connections.md).  
  
10. Повторите шаги с 6 по 9 для каждой задачи и контейнера, которые запускают транзакцию.  
  
## <a name="see-also"></a>См. также:  
 [Транзакции служб Integration Services](integration-services-transactions.md)  
  
  