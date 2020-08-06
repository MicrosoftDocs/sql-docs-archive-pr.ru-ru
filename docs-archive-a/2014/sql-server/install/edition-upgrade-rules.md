---
title: Правила обновления выпуска | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 77c4d751-4fea-4e69-a7c8-ab8fc0dbadb2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 453944ede41bfc5cf258c6f0946b15b716c6c22c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659191"
---
# <a name="edition-upgrade-rules"></a>Правила обновления выпуска
  Программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверяет конфигурацию компьютера перед началом установки. Во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средство проверки конфигурации системы (SCC) просматривает компьютер, на котором устанавливается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Средство SCC проверяет наличие условий, препятствующих успешной установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Прежде чем программа установки запустит обновление выпуска, SCC получает сведения о состоянии каждого элемента. Затем оно сравнивает результаты с требуемыми условиями и предоставляет рекомендации по устранению критических препятствий.  
  
 При проверке конфигурации системы создается отчет, содержащий краткое описание всех выполненных правил и состояния выполнения. Отчет о проверке конфигурации системы находится в папке% ProgramFiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ .  
  
 Прежде чем начинать установку, ознакомьтесь со следующими разделами:  
  
1.  [Требования к аппаратному и программному обеспечению для установки SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [Возможности, поддерживаемые различными выпусками SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [Вопросы безопасности при установке SQL Server](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [Версии SQL Server на местных языках](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 Другие ссылки:  
  
1.  [Поддерживаемые обновления версий и выпусков](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [Подготовка к установке отказоустойчивого кластера](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="see-also"></a>См. также:  
 [Установка правил](../../../2014/sql-server/install/install-rules.md)  
  
  
