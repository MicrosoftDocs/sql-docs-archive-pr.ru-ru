---
title: 'Группы доступности AlwaysOn: взаимодействие (SQL Server) | Документы Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], interoperability
ms.assetid: daf87f90-2623-42ca-912c-b8f07d210510
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bbd9de348b2e36feefd7efea52dee0b8c13a9f34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655967"
---
# <a name="always-on-availability-groups-interoperability-sql-server"></a>Группы доступности AlwaysOn: взаимодействие (SQL Server)
  В этом разделе описывается совместимость [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] с другими функциями [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  

  
##  <a name="features-that-interoperate-with-alwayson-availability-groups"></a><a name="Interop"></a>Функции, которые взаимодействуют с группы доступности AlwaysOn  
 В следующей таблице перечислены функции [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , совместимые с [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Ссылка в столбце **Дополнительные сведения** указывает, что имеются замечания по совместимости данной функции.  
  
|Признак|Дополнительные сведения|  
|-------------|----------------------|  
|система отслеживания измененных данных|[Репликация, Отслеживание изменений, система отслеживания измененных данных и группы доступности AlwaysOn &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|Change tracking|[Репликация, Отслеживание изменений, система отслеживания измененных данных и группы доступности AlwaysOn &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|Автономные базы данных|[Автономные базы данных с группами доступности AlwaysOn (SQL Server)](always-on-availability-groups-sql-server.md)|  
|Шифрование базы данных|[Зашифрованные базы данных с группы доступности AlwaysOn &#40;SQL Server&#41;](encrypted-databases-with-always-on-availability-groups-sql-server.md)|  
|Моментальные снимки базы данных|[Моментальные снимки базы данных с группы доступности AlwaysOn &#40;SQL Server&#41;](database-snapshots-with-always-on-availability-groups-sql-server.md)|  
|FILESTREAM и FileTable|[FILESTREAM и FileTable с группы доступности AlwaysOn &#40;SQL Server&#41;](filestream-and-filetable-with-always-on-availability-groups-sql-server.md)|  
|Полнотекстовый поиск|Примечание. Полнотекстовые индексы синхронизируются с базами данных-получателями AlwaysOn.|  
|Доставка журналов|[Необходимые условия для перехода с доставки журналов на группы доступности AlwaysOn &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)|  
|Удаленное хранилище больших двоичных объектов|[Удаленное хранилище больших двоичных объектов &#40;&#41; RBS и группы доступности AlwaysOn &#40;SQL Server](remote-blob-store-rbs-and-always-on-availability-groups-sql-server.md)|  
|Репликация[Настройка репликации для группы доступности AlwaysOn (SQL Server)](configure-replication-for-always-on-availability-groups-sql-server.md)<br /><br /> [Обслуживание базы данных публикации AlwaysOn &#40;SQL Server&#41;](maintaining-an-always-on-publication-database-sql-server.md)<br /><br /> [Репликация, Отслеживание изменений, система отслеживания измененных данных и группы доступности AlwaysOn &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)<br /><br /> [Подписчики репликации и группы доступности AlwaysOn &#40;SQL Server&#41;](replication-subscribers-and-always-on-availability-groups-sql-server.md)|  
|Службы Analysis Services|[Службы Analysis Services с группами доступности AlwaysOn](analysis-services-with-always-on-availability-groups.md)|  
|Службы Reporting Services|Используйте вторичные реплики, доступные только для чтения, в качестве источника данных для отчетов для снижения нагрузки на первичную реплику, доступную для чтения и записи.<br /><br /> [Reporting Services с группы доступности AlwaysOn &#40;SQL Server&#41;](reporting-services-with-always-on-availability-groups-sql-server.md)|  
|Компонент Service Broker|[Service Broker с группы доступности AlwaysOn &#40;SQL Server&#41;](service-broker-with-always-on-availability-groups-sql-server.md)|  
|Агент SQL Server||  
  
##  <a name="features-that-do-not-interoperate-with-alwayson-availability-groups"></a><a name="NoInterop"></a>Функции, которые не взаимодействуют с группы доступности AlwaysOn  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] не работает в сочетании со следующими функциями.  
  
-   Транзакции между разными базами данных или распределенные транзакции  
  
     Сведения о том, почему не поддерживаются такие транзакции, см. в разделе [Транзакции между базами данных не поддерживаются при зеркальном отображении баз данных или в группах доступности AlwaysOn (SQL Server)](transactions-always-on-availability-and-database-mirroring.md).  
  
-   Зеркальное отображение базы данных  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> См. также  
  
-   **Блоги**  
  
     [Руководство по миграции. Миграция в отказоустойчивую кластеризацию и группы доступности SQL Server 2012 с предшествующих развертываний с кластеризацией и зеркальным отображением](https://blogs.msdn.com/b/sqlalwayson/archive/2012/04/09/now-available-migration-guide-migrating-to-sql-server-2012-failover-clustering-and-availability-groups-from-prior-clustering-and-mirroring-deployments.aspx)  
  
     [Блоги команды разработчиков SQL Server AlwaysOn: официальный блог по SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Блоги инженеров CSS SQL Server](https://blogs.msdn.com/b/psssql/)  
  
-   **Технические документы**  
  
     [Руководство по миграции. Переход на группы доступности AlwaysOn с предыдущих развертываний, сочетающих зеркальное отображение базы данных и доставку журналов](https://msdn.microsoft.com/library/jj635217)  
  
     [Руководство по решениям режима AlwaysOn в Microsoft SQL Server для обеспечения высокой доступности и аварийного восстановления](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Технические документы Майкрософт Microsoft по SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Технические документы группы консультантов по SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Предварительные требования, ограничения и рекомендации для группы доступности AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
