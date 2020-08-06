---
title: Просмотр журнала подсистемы аудита SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- audits [SQL Server], viewing logs
- viewing audit logs
- logs [SQL Server], audit
ms.assetid: e8feaca0-7852-422b-895a-319b965d8d9b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 8f9902a4fc92ef0b35bae62eb80170762c52fdec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656287"
---
# <a name="view-a-sql-server-audit-log"></a>Просмотр журнала подсистемы аудита SQL Server
  В этом разделе описано, как просмотреть журнал аудита SQL Server в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Просмотр журнала подсистемы аудита SQL Server с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Требуется разрешение `CONTROL SERVER`.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-a-sql-server-audit-log"></a>Просмотр журнала подсистемы аудита SQL Server  
  
1.  В обозревателе объектов раскройте папку **Безопасность** .  
  
2.  Разверните папку **Аудит** .  
  
3.  Щелкните правой кнопкой мыши журнал аудита, который необходимо просмотреть, и выберите пункт **Просмотр журналов аудита**. Откроется диалоговое окно **Просмотр файла журнала —**_server_name_ . Дополнительные сведения см. в статье [Log File Viewer F1 Help](../../logs/log-file-viewer-f1-help.md).  
  
4.  После завершения нажмите кнопку **Закрыть**.  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] рекомендует просматривать журнал аудита, используя средство просмотра файлов журнала. Однако при создании автоматизированной системы мониторинга информацию в файле аудита можно просматривать напрямую с помощью функции [sys.fn_get_audit_file (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql). При чтении файла напрямую данные возвращаются в несколько ином (необработанном) формате. Дополнительные сведения см. в разделе **sys. fn_get_audit_file** .  
  
## <a name="see-also"></a>См. также:  
 [Подсистема аудита SQL Server (компонент Database Engine)](sql-server-audit-database-engine.md)   
 [Запись событий подсистемы аудита SQL Server в журнал безопасности](write-sql-server-audit-events-to-the-security-log.md)  
  
  
