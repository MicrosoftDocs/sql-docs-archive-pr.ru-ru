---
title: Просмотр параметров NodeWeight кворума кластера | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: b845e73a-bb01-4de2-aac2-8ac12abebc95
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef2176d4916e8affbb9ef89c9b26499289c520ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659270"
---
# <a name="view-cluster-quorum-nodeweight-settings"></a>Просмотр параметров NodeWeight кворума кластера
  В этом разделе описан порядок просмотра параметров NodeWeight для каждого узла элемента в кластере отказоустойчивого кластера Windows Server (WSFC). Параметры NodeWeight используются при определении голосов в кворуме для поддержки аварийного восстановления и сценариев с несколькими подсетями для экземпляров отказоустойчивого кластера [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   **Перед началом работы:**  [Обязательные условия](#Prerequisites), [Безопасность](#Security)  
  
-   **Просмотр параметров NodeWeight кворума с помощью:** [Transact-SQL](#TsqlProcedure), [PowerShell](#PowerShellProcedure), [Cluster.exe](#CommandPromptProcedure)  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> Перед началом работы  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
 Эта функция поддерживается только в [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] или более поздних версиях.  
  
> [!IMPORTANT]  
>  Для использования параметров NodeWeight необходимо применить следующее исправление ко всем серверам в кластере WSFC:  
>   
>  [KB2494036](https://support.microsoft.com/kb/2494036): доступно исправление, позволяющее настраивать узел кластера, не имеющий голосов кворума, в [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] и [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]  
  
> [!TIP]  
>  Если это исправление не установлено, то в примерах этого раздела будут возвращены пустые значения или значения NULL для NodeWeight.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 Пользователь должен входить в учетную запись домена, которая является членом локальной группы администраторов, на каждом узле кластера WSFC.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
##### <a name="to-view-nodeweight-settings"></a>Просмотр параметров NodeWeight  
  
1.  Подключитесь к любому экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в кластере.  
  
2.  Выполните запрос к представлению [sys].[dm_hadr_cluster_members].  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)  
 В следующем примере выполняется запрос к системному представлению для возврата значений для всех узлов в кластере данного экземпляра.  
  
```sql  
SELECT  member_name, member_state_desc, number_of_quorum_votes  
 FROM   sys.dm_hadr_cluster_members;  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Использование Powershell  
  
### <a name="to-view-nodeweight-settings"></a>Просмотр параметров NodeWeight
  
1.  Запустите повышенный режим Windows PowerShell с помощью команды **Запуск от имени администратора**.  
  
2.  Импортируйте модуль `FailoverClusters` для включения командлетов кластера.  
  
3.  Использование объекта `Get-ClusterNode` для возврата коллекции объектов узла кластера.  
  
4.  Выведите свойства узла кластера в удобном для чтения формате.  
  
### <a name="example-powershell"></a>Пример (Powershell)  
 В следующем примере показан вывод некоторых свойств узла для кластера с именем Cluster001.  
  
```powershell  
Import-Module FailoverClusters  
  
$cluster = "Cluster001"  
$nodes = Get-ClusterNode -Cluster $cluster  
  
$nodes | Format-Table -Property NodeName, State, NodeWeight  
```  
  
##  <a name="using-clusterexe"></a><a name="CommandPromptProcedure"></a> Использование Cluster.exe  
  
> [!NOTE]  
>  Программа cluster.exe является устаревшей в выпуске [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] .  Для будущих разработок используйте PowerShell с отказоустойчивым кластером.  Программа cluster.exe будет удалена в следующем выпуске Windows Server. Дополнительные сведения см. в разделе [Сопоставление команд Cluster.exe с командлетами Windows PowerShell для отказоустойчивых кластеров](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx).  
  
##### <a name="to-view-nodeweight-settings"></a>Просмотр параметров NodeWeight  
  
1.  Запустите повышенный режим командной строки с помощью команды **Запуск от имени администратора**.  
  
2.  Использование **cluster.exe** для возврата состояния узла и значений NodeWeight  
  
### <a name="example-clusterexe"></a>Пример (Cluster.exe)  
 В следующем примере показан вывод некоторых свойств узла для кластера с именем Cluster001.  
  
```cmd
cluster.exe Cluster001 node /status /properties  
```  
  
## <a name="see-also"></a>См. также:  
 [Режим кворума и участвующая в голосовании конфигурация WSFC (SQL Server)](wsfc-quorum-modes-and-voting-configuration-sql-server.md)   
 [Настройка параметров NodeWeight кворума кластера](configure-cluster-quorum-nodeweight-settings.md)   
 [sys.dm_hadr_cluster_members (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)   
 [Командлеты отказоустойчивого кластера в Windows PowerShell по выполняемым задачам](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)  
