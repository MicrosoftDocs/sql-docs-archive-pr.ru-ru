---
title: Редактор преобразования "Извлечение терминов" (вкладка "Дополнительно") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextraction.advanced.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 87118281-6e3c-499e-bac4-fa4c24bb12c6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4be56f8ac2deeab49e43071a07894a466019287
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734289"
---
# <a name="term-extraction-transformation-editor-advanced-tab"></a>Редактор преобразования «Извлечение терминов» (вкладка «Дополнительно»)
  Вкладка **Дополнительно** диалогового окна **Редактор преобразования «Извлечение терминов»** используется для задания свойств извлечения, таких как частота, длина и предмет извлечения (слова или фразы).  
  
 Дополнительные сведения о преобразовании «Извлечения терминов» см. в разделе [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Имя существительное**  
 Указывает, что при преобразовании будут извлекаться только отдельные существительные.  
  
 **Субстантивное словосочетание**  
 Указывает, что при преобразовании будут извлекаться только субстантивные словосочетания.  
  
 **Имя существительное и субстантивное словосочетание**  
 Указывает, что при преобразовании будут извлекаться как существительные, так и субстантивные словосочетания.  
  
 **Частота**  
 Указывает, что целевой функцией является частота термина.  
  
 **TFIDF**  
 Указывает, что целевой функцией является значение TFIDF термина. Функция TFIDF расшифровывается как "частота термина и обратная частота документа" (Term Frequency and Inverse Document Frequency) и определяется формулой: TFIDF термина T = (частота_T) * log (#число_строк_во_входных_данных) / (#число_строк_включающих_T)  
  
 **Порог частоты**  
 Позволяет задать число вхождений слова или фразы, необходимое для их извлечения. Значение по умолчанию — 2.  
  
 **Максимальная длина термина**  
 Позволяет задать максимальную длину фразы или слова. Этот параметр затрагивает только субстантивные словосочетания. Значение по умолчанию — 12.  
  
 **Учитывать регистр при извлечении терминов**  
 Указывает, будет ли учитываться регистр при извлечении. Значение по умолчанию — `False`.  
  
 **Настройка вывода ошибок**  
 Используйте диалоговое окно [Настройка вывода ошибок](../../2014/integration-services/configure-error-output.md) для указания метода обработки ошибок для строк, вызвавших ошибку.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор преобразования "Извлечение терминов" &#40;вкладка "Извлечение терминов"&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md)   
 [Редактор преобразования "Извлечение терминов" &#40;вкладка "исключения"&#41;](../../2014/integration-services/term-extraction-transformation-editor-exclusion-tab.md)   
 [Преобразование "Уточняющий запрос термина"](data-flow/transformations/lookup-transformation.md)  
  
  
