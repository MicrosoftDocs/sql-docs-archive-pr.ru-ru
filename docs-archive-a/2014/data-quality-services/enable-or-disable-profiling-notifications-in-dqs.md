---
title: Включение или отключение уведомлений по профилированию в DQS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- enable notifications
- notifications,enable
- notifications,disable
ms.assetid: e439bb29-60cc-4afd-a79a-f629b8d843c1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b3b5e8cec1cac3eb1ce4357480c0f994a33d4c40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732050"
---
# <a name="enable-or-disable-profiling-notifications-in-dqs"></a><span data-ttu-id="df484-102">Включение или отключение уведомлений по профилированию в DQS</span><span class="sxs-lookup"><span data-stu-id="df484-102">Enable or Disable Profiling Notifications in DQS</span></span>
  <span data-ttu-id="df484-103">В этом разделе описывается включение или отключение уведомлений по профилированию в [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span><span class="sxs-lookup"><span data-stu-id="df484-103">This topic describes how to enable or disable profiling notifications in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="df484-104">По умолчанию уведомления по профилированию в DQS включены.</span><span class="sxs-lookup"><span data-stu-id="df484-104">By default, profiling notifications are enabled in DQS.</span></span> <span data-ttu-id="df484-105">Уведомления по профилированию сообщают важные сведения об источнике данных и эффективности текущего действия, выполняемого с данными.</span><span class="sxs-lookup"><span data-stu-id="df484-105">Profiling notifications tell you important facts about the data source and the effectiveness of the current activity performed on the data.</span></span> <span data-ttu-id="df484-106">Дополнительные сведения см. в разделе [Профилирование данных и уведомления в DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md).</span><span class="sxs-lookup"><span data-stu-id="df484-106">For more information, see [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="df484-107">Перед началом</span><span class="sxs-lookup"><span data-stu-id="df484-107">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="df484-108">безопасность</span><span class="sxs-lookup"><span data-stu-id="df484-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="df484-109">Permissions</span><span class="sxs-lookup"><span data-stu-id="df484-109">Permissions</span></span>  
 <span data-ttu-id="df484-110">Для включения уведомлений необходимо иметь роль dqs_administrator в базе данных DQS_MAIN.</span><span class="sxs-lookup"><span data-stu-id="df484-110">You must have the dqs_administrator role on the DQS_MAIN database to enable notifications.</span></span>  
  
##  <a name="enable-or-disable-profiling-notifications"></a><a name="Enable"></a><span data-ttu-id="df484-111">Включение или отключение уведомлений о профилировании</span><span class="sxs-lookup"><span data-stu-id="df484-111">Enable or Disable Profiling Notifications</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="df484-112">[Запустите приложение Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span><span class="sxs-lookup"><span data-stu-id="df484-112">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="df484-113">На главном экране клиента [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] нажмите кнопку **Конфигурация**.</span><span class="sxs-lookup"><span data-stu-id="df484-113">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="df484-114">Далее щелкните вкладку **Общие параметры** .</span><span class="sxs-lookup"><span data-stu-id="df484-114">Next, click the **General Settings** tab.</span></span>  
  
4.  <span data-ttu-id="df484-115">Установите или снимите флажок **Включить уведомления** , чтобы отключить или включить уведомления по профилированию для различных действий в DQS.</span><span class="sxs-lookup"><span data-stu-id="df484-115">Clear or select the **Enable Notifications** check box to disable or enable profiling notifications for various activities in DQS.</span></span>  
  
5.  <span data-ttu-id="df484-116">Нажмите кнопку **Закрыть**.</span><span class="sxs-lookup"><span data-stu-id="df484-116">Click **Close**.</span></span>  
  
  