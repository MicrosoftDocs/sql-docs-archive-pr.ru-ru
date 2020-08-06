---
title: Экспорт базы знаний в файл DQS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a324ead5-c8aa-4e26-abe3-ef415add00f8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 81dfc8e7f20fae9dacd521595d101be3117a6794
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656563"
---
# <a name="export-a-knowledge-base-to-a-dqs-file"></a>Экспорт базы знаний в файл .dqs
  В этом разделе описывается экспорт всей базы знаний в файл данных DQS в службах [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Экспортировать в файл данных можно домен или всю базу знаний. Сведения об экспорте домена см. в разделе [Экспорт домена в файл DQS](../../2014/data-quality-services/export-a-domain-to-a-dqs-file.md).  
  
 Экспорт базы знаний в файл DQS и последующий импорт в качестве другой базы знаний упрощает процесс создания знаний и экономит время. Благодаря этому можно использовать базу знаний и ее знания совместно с другими пользователями. Файл DQS будет содержать все сведения базы знаний, включая домены и политику сопоставления, кроме присоединенных ссылочных данных. После импорта файла DQS следует повторно добавить необходимые домены в соответствующие службы ссылочных данных. Экспортируются как опубликованные, так и неопубликованные данные базы знаний.  
  
 Файл данных DQS, созданный в процессе экспорта, зашифровывается, его просмотр становится невозможным.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
 Чтобы экспортировать базу знаний в файл данных DQS, необходимо создать и открыть базу знаний. Файл DQS не требуется, он будет создан в процессе экспорта.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для экспорта базы знаний в файл данных DQS необходимо быть членом роли dqs_kb_editor или dqs_administrator в базе данных DQS_MAIN.  
  
##  <a name="export-a-knowledge-base-to-a-dqs-file"></a><a name="Export"></a>Экспорт базы знаний в файл DQS  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Запустите приложение Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  На главном экране клиента [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] откройте базу знаний в разделе управления доменами.  
  
3.  На странице «Управление доменами» (при любой выбранной вкладке) щелкните значок **Экспортировать данные базы знаний** над списком «Домен» и выберите **Экспортировать базу знаний**. Кроме того, вы можете щелкнуть правой кнопкой мыши список **Домен** , указать пункт **Экспорт**, а затем **Экспортировать базу знаний**.  
  
4.  В диалоговом окне **Экспорт в файл данных** перейдите в папку, где планируется сохранить файл, присвойте файлу имя или оставьте имя базы знаний, оставьте **Файлы данных DQS (\*.dqs)** в качестве **Типа файла** и нажмите кнопку **Сохранить**.  
  
5.  В диалоговом окне **Экспортировать базу знаний** убедитесь, что в строке состояния сообщается о завершении экспорта. Нажмите кнопку **ОК**.  
  
##  <a name="follow-up-after-exporting-a-domain-to-a-dqs-file"></a><a name="FollowUp"></a>Дальнейшие действия. После экспорта домена в файл DQS  
 После экспорта базы знаний в файл DQS можно импортировать базу знаний на тот же сервер [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] (с новым именем) или на другой сервер [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].  
  
  
