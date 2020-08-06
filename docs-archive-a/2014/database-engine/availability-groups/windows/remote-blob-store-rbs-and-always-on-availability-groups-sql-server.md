---
title: Удаленное хранилище больших двоичных объектов (RBS) и группы доступности AlwaysOn (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 01a70258-d4fd-40bc-bc44-c490b5d6c420
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f12a11162d286731b2b510a9051183e6c3025b2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657321"
---
# <a name="remote-blob-store-rbs-and-alwayson-availability-groups-sql-server"></a>Удаленное хранилище больших двоичных объектов (RBS) и группы доступности AlwaysOn (SQL Server)
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]может предоставить решение для обеспечения высокого уровня доступности и аварийного восстановления для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] объектов BLOB (BLOB) [удаленного хранилища BLOB](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md) . [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] защищает все метаданные и схемы удаленного хранилища больших двоичных объектов, хранящиеся в базе данных доступности, копируя их на вторичные реплики. Эта база данных содержимого SharePoint. В целом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] хранит метаданные этого удаленного хранилища больших двоичных объектов независимо от больших двоичных объектов.  
  
 Защита BLOB-данных в RBD зависит от расположения больших двоичных объектов следующим образом.  
  
|Место хранения большого двоичного объекта|Могут ли группы доступности защищать данные этого большого двоичного объекта?|  
|-------------------------|-----------------------------------------------------|  
|Та же база данных, содержащая метаданные удаленного хранилища больших двоичных объектов (хранимая с помощью удаленного поставщика FILESTREAM хранилища RBS)|Да|  
|Другая база данных в том же экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (хранимая с помощью удаленного поставщика FILESTREAM хранилища RBS)|Да<br /><br /> Рекомендуется поместить эту базу данных в ту же группу доступности, что и базу данных, содержащую метаданные удаленного хранилища больших двоичных объектов.|  
|Другая база данных находится на другом экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (хранимая с помощью удаленного поставщика FILESTREAM хранилища RBS)|Да<br /><br /> Эта база данных должна находиться в отдельной группе доступности.|  
|Стороннее хранилище больших двоичных объектов|Нет<br /><br /> Чтобы защитить эти BLOB-данные, воспользуйтесь механизмами высокого уровня доступности поставщика хранилища больших двоичных объектов.|  
  
##  <a name="limitations"></a><a name="Limitations"></a> Ограничения  
  
-   Программы обслуживания хранилища RBS должны быть нацелены на первичную реплику.  
  
##  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
  
-   Используйте прослушивателя группы доступности. Дополнительные сведения см. в разделе [Прослушиватели групп доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](../../listeners-client-connectivity-application-failover.md).  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> См. также  
  
-   [Обслуживание удаленного хранилища больших двоичных объектов](https://msdn.microsoft.com/library/gg316773\(SQL.105\).aspx) (в электронной документации [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] )  
  
-   [Запуск программы обслуживания удаленного хранилища больших двоичных объектов](https://blogs.msdn.com/b/sqlrbs/archive/2010/03/19/running-rbs-maintainer.aspx) (блог)  
  
-   [Настройка удаленного хранилища больших двоичных объектов (RBS) с поставщиком FILESTREAM (SharePoint 2010)](https://blogs.msdn.com/b/mvpawardprogram/archive/2012/04/02/configure-remote-blob-storage-rbs-with-the-filestream-provider-sharepoint-2010.aspx) (блог)  
  
## <a name="see-also"></a>См. также:  
 [&#40;SQL Server подключения клиента AlwaysOn&#41;](always-on-client-connectivity-sql-server.md)   
 [Удаленное хранилище больших двоичных объектов (RBS) (SQL Server)](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
  
