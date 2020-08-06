---
title: Включение удаленного издателя на распространителе (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- remote Distributors [SQL Server replication]
- Publishers [SQL Server replication]
ms.assetid: 6f8e2831-5c45-4e39-8e51-d37e2813cf3d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 06c85924731b79e8b3c79cfbcc354b5bedf69b62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655620"
---
# <a name="enable-a-remote-publisher-at-a-distributor-sql-server-management-studio"></a>включить удаленный издатель на распространителе (среда SQL Server Management Studio)
  Предоставьте издателю разрешение использовать удаленный распространитель на странице **Издатели** . Эта страница доступна в мастере настройки распространителя и диалоговом окне **Свойства распространителя — \<Distributor>** . Дополнительные сведения об использовании мастера и о доступе к этому диалоговому окну см. в статьях [Настройка публикации и распространения](configure-publishing-and-distribution.md) и [Просмотр и изменение свойств издателя и распространителя](view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-enable-a-publisher-in-the-configure-distribution-wizard"></a>Включение издателя в мастере настройки распространителя  
  
1.  На странице **Издатели** мастера настройки распространителя щелкните **Добавить**.  
  
2.  Щелкните **Добавить издатель SQL Server**. Сведения о том, как разрешить издателю Oracle использовать распространитель, см. в разделе [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md).  
  
3.  В диалоговом окне **Соединение с сервером** укажите сведения о соединении для издателя, который будет использовать удаленный распространитель, а затем щелкните **Соединить**.  
  
4.  На странице **Пароль распространителя** в текстовых полях **Пароль** и **Подтверждение пароля** укажите надежный пароль для учетной записи **distributor_admin** , используемой системой репликации, чтобы подключить издателя к распространителю для выполнения административных задач.  
  
5.  Для просмотра и изменения параметров издателя нажмите кнопку свойств с многоточием ( **…** ).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-enable-a-publisher-in-the-distributor-properties-dialog-box"></a>Включение издателя в диалоговом окне «Свойства распространителя»  
  
1.  На странице **Издатели** диалогового окна **Свойства распространителя — \<Distributor>** нажмите кнопку **Добавить**.  
  
2.  Щелкните **Добавить издатель SQL Server**. Сведения о том, как разрешить издателю Oracle использовать распространитель, см. в разделе [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md).  
  
3.  В диалоговом окне **Соединение с сервером** укажите сведения о соединении для издателя, который будет использовать удаленный распространитель, а затем щелкните **Соединить**.  
  
4.  На странице **Издатели** в текстовых полях **Пароль** и **Подтверждение пароля** укажите надежный пароль для учетной записи **distributor_admin** , используемой системой репликации, чтобы подключить издатель к распространителю для выполнения административных задач.  
  
5.  Для просмотра и изменения параметров издателя нажмите кнопку свойств с многоточием ( **…** ).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Настройка публикации и распространения](configure-publishing-and-distribution.md)   
 [Настройка распространения](configure-distribution.md)   
 [Защита распространителя](security/secure-the-distributor.md)  
  
  
