---
title: Создание, изменение и удаление селективных XML-индексов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: c398f396-f630-4a2d-a264-f243c5346de1
author: rothja
ms.author: jroth
ms.openlocfilehash: bf4123a46cc13359c936e6f9cfc0db3dcfdaa175
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730249"
---
# <a name="create-alter-and-drop-selective-xml-indexes"></a>Создание, изменение и удаление селективных XML-индексов
  Описывает способы создания нового селективного XML-индекса, изменения или удаления существующего селективного XML-индекса.  
  
 Дополнительные сведения о селективных XML-индексах см. в разделе [Выборочный XML-индекс (SXI)](selective-xml-indexes-sxi.md).  
  
##  <a name="creating-a-selective-xml-index"></a><a name="create"></a> Создание селективного XML-индекса  
  
### <a name="how-to-create-a-selective-xml-index"></a>Руководство. Создание селективного XML-индекса  
 **Создание нового селективного XML-индекса с помощью Transact-SQL**  
 Создание селективного XML-индекса путем вызова инструкции CREATE SELECTIVE XML INDEX. Дополнительные сведения см. в разделе [CREATE SELECTIVE XML INDEX (Transact-SQL)](/sql/t-sql/statements/create-selective-xml-index-transact-sql).  
  
 **Пример**  
  
 В следующем примере показан синтаксис для создания селективного XML-индекса. Он также содержит несколько вариантов синтаксиса для описания индексируемых путей с указаниями по оптимизации.  
  
```sql  
CREATE SELECTIVE XML INDEX sxi_index  
ON Tbl(xmlcol)  
  
FOR(  
    pathab   = '/a/b' as XQUERY 'node()'  
    pathabc  = '/a/b/c' as XQUERY 'xs:double',   
    pathdtext = '/a/b/d/text()' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON  
    pathabe = '/a/b/e' as SQL NVARCHAR(100)  
)  
```  
  
  
  
##  <a name="altering-a-selective-xml-index"></a><a name="alter"></a> Изменение селективного XML-индекса  
  
### <a name="how-to-alter-a-selective-xml-index"></a>Руководство. Изменение селективного XML-индекса  
 **изменить селективный XML-индекс с помощью Transact-SQL**  
 Измените существующий селективный XML-индекс с помощью инструкции ALTER INDEX. Дополнительные сведения см. в разделе [ALTER INDEX (селективные XML-индексы)](../indexes/indexes.md).  
  
 **Пример**  
  
 В следующем примере показана инструкция ALTER INDEX. Эта инструкция добавляет путь `'/a/b/m'` в часть XQuery индекса и удаляет путь `'/a/b/e'` из части SQL индекса, созданного в примере в разделе [CREATE SELECTIVE XML INDEX (Transact-SQL)](/sql/t-sql/statements/create-selective-xml-index-transact-sql). Путь для удаления определяется по имени, указанному при его создании.  
  
```sql  
ALTER INDEX sxi_index  
ON Tbl  
FOR   
(  
    ADD pathm = '/a/b/m' as XQUERY 'node()' ,  
    REMOVE pathabe  
)  
```  
  
  
  
##  <a name="dropping-a-selective-xml-index"></a><a name="drop"></a> Удаление селективного XML-индекса  
  
### <a name="how-to-drop-a-selective-xml-index"></a>Руководство. Удаление селективного XML-индекса  
 **Удаление селективного XML-индекса с помощью Transact-SQL**  
 Удалите селективный XML-индекс с помощью инструкции DROP INDEX. Дополнительные сведения см. в разделе [DROP INDEX (селективные XML-индексы)](/sql/t-sql/statements/drop-index-selective-xml-indexes).  
  
 **Пример**  
  
 В следующем примере показана инструкция DROP INDEX.  
  
```sql  
DROP INDEX sxi_index ON tbl  
```  
  
 
  
  
