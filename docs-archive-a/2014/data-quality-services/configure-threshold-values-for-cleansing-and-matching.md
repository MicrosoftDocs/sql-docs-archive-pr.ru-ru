---
title: Настройка пороговых значений для очистки и сопоставления | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.general.f1
helpviewer_keywords:
- cleansing,threshold value
- cleansing threshold values
- matching,threshold value
ms.assetid: d2305409-7115-45a4-8f60-1213c0a47368
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0faf64e96468a3a9aac0de12d3ec3acbb1e1ed85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728722"
---
# <a name="configure-threshold-values-for-cleansing-and-matching"></a>Настройка пороговых значений для очистки и сопоставления
  В этом разделе описывается настройка пороговых значений, которые будут использоваться в ходе операций автоматизированной очистки и сопоставления в службах [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для настройки этих пороговых значений необходимо иметь роль dqs_administrator в базе данных DQS_MAIN.  
  
##  <a name="configuring-the-threshold-values"></a><a name="Configure"></a> Настройка пороговых значений  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Запустите приложение Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На главном экране клиента [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] нажмите кнопку **Конфигурация**.  
  
3.  Затем перейдите на вкладку **Общие параметры** . На этой вкладке можно указать пороговые значения для очистки, а также соответствующие действия.  
  
4.  Пороговые значения для операции очистки задаются в следующих полях в области **Интерактивная очистка** :  
  
    -   **Минимальный показатель для предложений**. Минимальная оценка или уровень достоверности, которые будут использоваться службами DQS для предложения значений на замену в ходе автоматизированного процесса очистки. Введите значение в десятичной нотации для соответствующего значения в процентах. Например, введите 0,75 для 75 %. Это значение должно быть меньше или равно значению, указанному в поле **Минимальная оценка для автоматического исправления** . Значение по умолчанию — 0,7.  
  
    -   **Минимальный показатель для автоматического исправления**. Минимальная оценка или уровень достоверности, которые будут использоваться службами DQS для автоматического исправления значений в ходе автоматизированного процесса очистки. Введите значение в десятичной нотации для соответствующего значения в процентах. Например, введите 0,9 для 90 %. Значение по умолчанию — 0,8.  
  
5.  Пороговое значение для операции сопоставления задается в поле **Минимальная оценка для записи** в области **Сопоставление** . Это значение задает минимальную оценку для записи, которая позволяет считать ее соответствующей другой записи. Значение по умолчанию — 80 %.  
  
6.  Нажмите кнопку **Закрыть**.  
  
  
