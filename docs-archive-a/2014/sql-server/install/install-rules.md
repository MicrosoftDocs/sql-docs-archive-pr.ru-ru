---
title: Правила установки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SCC
- System Configuration Check, Setup
helpviewer_keywords:
- System Configuration Check page [SQL Server Installation Wizard]
- SQL Server Installation Wizard, System Configuration Check page
- SCC [SQL Server]
ms.assetid: 168c0445-5651-42fc-91f4-d9f27d9e2281
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b3d9fe413174613cadc9277e5c7f21695a4021c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737580"
---
# <a name="install-rules"></a>Установка правил
  Программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверяет конфигурацию компьютера перед началом установки. Во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средство проверки конфигурации системы (SCC) просматривает компьютер, на котором устанавливается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Средство SCC проверяет наличие условий, препятствующих успешной установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Прежде чем программа установки запустит мастер установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , SCC получает сведения о состоянии каждого элемента. Затем оно сравнивает результаты с требуемыми условиями и предоставляет рекомендации по устранению критических препятствий.  
  
 При проверке конфигурации системы создается отчет, содержащий краткое описание всех выполненных правил и состояния выполнения. Отчет о проверке конфигурации системы находится в папке% ProgramFiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ .  
  
 Прежде чем начинать установку, ознакомьтесь со следующими разделами:  
  
1.  [Требования к аппаратному и программному обеспечению для установки SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [Возможности, поддерживаемые различными выпусками SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [Вопросы безопасности при установке SQL Server](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [Версии SQL Server на местных языках](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 Другие ссылки:  
  
1.  [Поддерживаемые обновления версий и выпусков](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [Подготовка к установке отказоустойчивого кластера](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="additional-rule-topics"></a>Дополнительные разделы по правилам  
 См. следующие разделы об указаниях по установке в зависимости от сценария:  
  
-   [Правила установки](../../../2014/sql-server/install/installation-rules.md)  
  
-   [Правила компонентов &#40;обновление&#41;](../../../2014/sql-server/install/feature-rules-upgrade.md)  
  
-   [Правила обновления выпуска](../../../2014/sql-server/install/edition-upgrade-rules.md)  
  
-   [Правила удаления](../../../2014/sql-server/install/uninstallation-rules.md)  
  
-   [Правила подготовки образа](../../../2014/sql-server/install/prepare-image-rules.md)  
  
-   [Правила завершения образа](../../../2014/sql-server/install/complete-image-rules.md)  
  
  
