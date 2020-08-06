---
title: Настройка параметра конфигурации сервера remote proc trans
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote proc trans option
- distributed transactions [SQL Server], enforcing
ms.assetid: cfbc6158-ab96-44b4-87eb-ea278c1b0c6b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 54fcaafa51eef33acb1ae8d1e2f36022840b76a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657882"
---
# <a name="configure-the-remote-proc-trans-server-configuration-option"></a>Настройка параметра конфигурации сервера remote proc trans
  В этом разделе описываются способы настройки параметра конфигурации сервера **remote proc trans** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **remote proc trans** предназначен для защиты действий межсерверной процедуры с помощью транзакции координатора распределенных транзакций [!INCLUDE[msCoName](../../includes/msconame-md.md)] (MS DTC).  
  
 Установите значение параметра **remote proc trans** равным 1, чтобы применить распределенную транзакцию координатора MS DTC, защищающую свойства ACID (atomic, consistent, isolated, durable — атомарность, согласованность, изолированность, надежность) транзакций. Сеансы, начатые после установки этого параметра в 1, наследуют значение этого параметра в качестве значения по умолчанию.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Предварительные требования](#Prerequisites)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Настройка параметра remote proc trans с помощью различных средств**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметра remote proc trans](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
  
-   Это значение можно установить только при разрешенных соединениях с удаленными серверами.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
  
-   Этот параметр предоставляется в целях совместимости с предыдущими версиями [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для приложений, использующих удаленные хранимые процедуры. Вместо вызовов удаленных хранимых процедур используйте распределенные запросы, которые ссылаются на связанные серверы, определенные с помощью процедуры [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-remote-proc-trans-option"></a>Настройка параметра remote proc trans  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Выберите узел **Соединения** .  
  
3.  В области **Удаленные серверные соединения**установите флажок **Требовать распределенных транзакций для межсерверных соединений** .  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-remote-proc-trans-option"></a>Настройка параметра remote proc trans  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование процедуры [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) для задания значения параметра `remote proc trans` равным `1`.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote proc trans', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md).  
  
##  <a name="follow-up-after-you-configure-the-remote-proc-trans-option"></a><a name="FollowUp"></a> Дальнейшие действия. После настройки параметра remote proc trans  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
