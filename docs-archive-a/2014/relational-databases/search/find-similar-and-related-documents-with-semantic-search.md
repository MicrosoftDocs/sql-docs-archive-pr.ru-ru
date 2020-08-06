---
title: Поиск похожих и связанных документов с помощью семантического поиска | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], document similarity queries
ms.assetid: 9f527883-031b-442f-8e95-24bc0151ecbf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b11493b5b04fa9308e3afbe56176251225248338
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668734"
---
# <a name="find-similar-and-related-documents-with-semantic-search"></a>Поиск похожих и связанных документов с использованием семантического поиска
  Описывает процесс поиска схожих или связанных документов или текстовых значений и сведений об их сходстве или связи в столбцах, настроенных для статистического семантического индексирования.  
  
##  <a name="finding-similar-or-related-documents"></a><a name="BasicsQuerySimilar"></a>Поиск схожих или связанных документов  
  
###  <a name="how-to-find-similar-or-related-documents-with-semanticsimilaritytable"></a><a name="HowToQuerySimilar"></a>Как найти похожие или связанные документы с помощью SEMANTICSIMILARITYTABLE  
 Чтобы найти схожие или связанные документы в данном столбце, запросите функцию [semanticsimilaritytable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql).  
  
 Функция**SEMANTICSIMILARITYTABLE** возвращает таблицу, состоящую из нуля, одной или нескольких строк, содержимое которых в указанном столбце семантически схоже с заданным документом. На эту функцию набора строк можно ссылаться в предложении FROM инструкции SELECT как на обычное имя таблицы.  
  
 Искать схожие документы по разным столбцам невозможно. Функция **SEMANTICSIMILARITYTABLE** извлекает результаты только из столбца, совпадающего с исходным столбцом, определяемым аргументом **source_key** .  
  
 Подробные сведения о параметрах функции **SEMANTICSIMILARITYTABLE** и о возвращаемой таблице результатов см. в статье [semanticsimilaritytable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql).  
  
> [!IMPORTANT]  
>  Для целевых столбцов должно быть включено полнотекстовое и семантическое индексирование.  
  
###  <a name="example-find-the-top-documents-that-are-similar-to-another-document"></a><a name="HowToIdentifySimilar"></a>Пример. Поиск лучших документов, которые похожи на другой документ  
 В следующем примере извлекаются 10 лучших кандидатов, которые похожи на кандидат, указанный в *@CandidateID* таблице HumanResources. JobCandidate в образце базы данных AdventureWorks2012.  
  
```scr  
SELECT TOP(10) KEY_TBL.matched_document_key AS Candidate_ID  
FROM SEMANTICSIMILARITYTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume,  
    @CandidateID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
##  <a name="finding-information-about-how-documents-are-similar-or-related"></a><a name="BasicsQuerySimilarity"></a>Поиск сведений о схожих и связанных документах  
  
###  <a name="how-to-find-information-about-how-documents-are-similar-or-related-with-semanticsimilaritydetailstable"></a><a name="HowToQuerySimilarity"></a>Инструкции. Поиск сведений о том, как документы похожи или связаны с SEMANTICSIMILARITYDETAILSTABLE  
 Чтобы получить дополнительные сведения о ключевых фразах, которые делают документы схожими или связанными, вызовите функцию [semanticsimilaritydetailstable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql).  
  
 Функция **SEMANTICSIMILARITYDETAILSTABLE** возвращает таблицу из нуля, одной или нескольких строк с ключевыми фразами, общими для двух документов (исходного документа и сопоставленного документа), содержимое которых семантически схоже. На эту функцию набора строк можно ссылаться в предложении FROM инструкции SELECT как на обычное имя таблицы.  
  
 Подробные сведения о параметрах функции **SEMANTICSIMILARITYDETAILSTABLE** и о возвращаемой таблице результатов см. в статье [semanticsimilaritydetailstable (Transact-SQL)](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql).  
  
> [!IMPORTANT]  
>  Для целевых столбцов должно быть включено полнотекстовое и семантическое индексирование.  
  
###  <a name="example-find-the-top-key-phrases-that-are-similar-between-documents"></a><a name="HowToSimilarPhrases"></a>Пример. Поиск основных ключевых фраз, которые похожи на документы  
 В следующем примере производится извлечение 5 ключевых фраз, имеющих высший показатель подобия среди указанных кандидатов в таблице **HumanResources.JobCandidate** образца базы данных AdventureWorks2012.  
  
```sql  
SELECT TOP(5) KEY_TBL.keyphrase, KEY_TBL.score  
FROM SEMANTICSIMILARITYDETAILSTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume, @CandidateID,  
    Resume, @MatchedID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
  
