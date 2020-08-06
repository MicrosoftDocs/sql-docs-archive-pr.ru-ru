---
title: Увеличение размера базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], size
- increasing database size
- database size [SQL Server], increasing
- size [SQL Server], databases
ms.assetid: 14f4206d-3afa-4ba9-9849-23e81d63306d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 71dcb00b3f5525f7059fc54911baed929f763008
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751087"
---
# <a name="increase-the-size-of-a-database"></a>Увеличение размера базы данных
  Этот подраздел описывает, как увеличить размер базы данных [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. База данных расширяется или путем увеличения размера существующих данных либо файла журнала, или путем добавления нового файла к базе данных.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Увеличение размера базы данных с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Добавить или удалить файл во время выполнения инструкции BACKUP невозможно.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER на базу данных.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-increase-the-size-of-a-database"></a>Увеличение размера базы данных  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Разверните узел **Базы данных**, щелкните правой кнопкой мыши базу данных, размер которой необходимо увеличить, и выберите пункт **Свойства**.  
  
3.  В окне **Свойства базы данных**выберите страницу **Файлы** .  
  
4.  Чтобы увеличить размер существующего файла, увеличьте значение в столбце **Исходный размер (МБ)** для файла. Необходимо увеличить размер базы данных, по крайней мере, на 1 мегабайт.  
  
5.  Чтобы увеличить размер базы данных путем добавления нового файла, нажмите кнопку **Добавить** и введите значения для нового файла. Дополнительные сведения см. в статье [AДобавление файлов данных или журналов в базу данных](add-data-or-log-files-to-a-database.md).  
  
6.  Нажмите кнопку **ОК**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-increase-the-size-of-a-database"></a>Увеличение размера базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере увеличивается размер файла `test1dat3`.  
  
 [!code-sql[DatabaseDDL#AlterDatabase5](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase5)]  
  
 Дополнительные сведения см. в разделе [Параметры инструкции ALTER DATABASE для файлов и файловых групп (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options).  
  
## <a name="see-also"></a>См. также:  
 [Добавление файлов данных или журналов в базу данных](add-data-or-log-files-to-a-database.md)   
 [Сжатие базы данных](shrink-a-database.md)  
  
  
