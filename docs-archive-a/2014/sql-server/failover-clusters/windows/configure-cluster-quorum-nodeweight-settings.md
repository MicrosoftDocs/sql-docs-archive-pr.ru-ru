---
title: Настройка параметров NodeWeight кворума кластера | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: cb3fd9a6-39a2-4e9c-9157-619bf3db9951
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e469d5fc0fc030304a7cf2f1bdd894eb578aa056
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659285"
---
# <a name="configure-cluster-quorum-nodeweight-settings"></a>Настройка параметров NodeWeight кворума кластера
  В этом разделе описан порядок настройки параметров NodeWeight для узла элемента в отказоустойчивом кластере Windows Server (WSFC). Параметры NodeWeight используются при определении голосов в кворуме для поддержки аварийного восстановления и сценариев с несколькими подсетями для экземпляров отказоустойчивого кластера [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   **Перед началом работы:**  [Обязательные условия](#Prerequisites), [Безопасность](#Security)  
  
-   **Просмотр параметров NodeWeight кворума с помощью:** [Powershell](#PowerShellProcedure), [Cluster.exe](#CommandPromptProcedure)  
  
-   [См. также](#RelatedContent)  
  
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
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Использование Powershell  
  
### <a name="to-configure-nodeweight-settings"></a>Настройка параметров NodeWeight
  
1.  Запустите повышенный режим Windows PowerShell с помощью команды **Запуск от имени администратора**.  
  
2.  Импортируйте модуль `FailoverClusters` для включения командлетов кластера.  
  
3.  Используйте объект `Get-ClusterNode` для задания свойства `NodeWeight` для каждого узла в кластере.  
  
4.  Выведите свойства узла кластера в удобном для чтения формате.  
  
 В следующем примере изменяется параметр NodeWeight в целях удаления голоса кворума для узла AlwaysOnSrv1, а затем происходит вывод параметров для всех узлов в этом кластере.
  
```powershell  
Import-Module FailoverClusters  
  
$node = "AlwaysOnSrv1"  
(Get-ClusterNode $node).NodeWeight = 0  
  
$cluster = (Get-ClusterNode $node).Cluster  
$nodes = Get-ClusterNode -Cluster $cluster  
  
$nodes | Format-Table -property NodeName, State, NodeWeight  
```  
  
##  <a name="using-clusterexe"></a><a name="CommandPromptProcedure"></a> Использование Cluster.exe  
  
> [!NOTE]  
>  Программа cluster.exe является устаревшей в выпуске [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] .  Для будущих разработок используйте PowerShell с отказоустойчивым кластером.  Программа cluster.exe будет удалена в следующем выпуске Windows Server. Дополнительные сведения см. в разделе [Сопоставление команд Cluster.exe с командлетами Windows PowerShell для отказоустойчивых кластеров](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx).  
  
### <a name="to-configure-nodeweight-settings"></a>Настройка параметров NodeWeight
  
1.  Запустите повышенный режим командной строки с помощью команды **Запуск от имени администратора**.  
  
2.  Используйте программу **cluster.exe** для задания значений `NodeWeight` .  

 В следующем примере изменяется значение NodeWeight для удаления голоса кворума узла AlwaysOnSrv1 в кластере Cluster001.  
  
```cmd
cluster.exe Cluster001 node AlwaysOnSrv1 /prop NodeWeight=0  
```  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> См. также  
  
-   [Просмотр событий и журналов для отказоустойчивого кластера](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)  
  
-   [Командлет Get-ClusterLog отказоустойчивого кластера](https://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a>См. также:  
 [Режимы кворума WSFC и &#40;настройки голосования SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md)   
 [Просмотр параметров NodeWeight кворума кластера](view-cluster-quorum-nodeweight-settings.md)   
 [Командлеты отказоустойчивого кластера в Windows PowerShell по выполняемым задачам](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)  
