---
title: Редактор преобразования "Нечеткий уточняющий запрос" (вкладка "столбцы") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.columns.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: aaf45327-79e9-4760-9b4d-546ace91b5b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9294022b52536940916a381d7b811437eaa5814
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729626"
---
# <a name="fuzzy-lookup-transformation-editor-columns-tab"></a>Редактор преобразования «Нечеткий уточняющий запрос» (вкладка «Столбцы»)
  Вкладка **Столбцы** диалогового окна **Редактор преобразования «Нечеткий уточняющий запрос»** используется для установки свойств входных и выходных столбцов.  
  
 Дополнительные сведения о преобразовании «Нечеткий уточняющий запрос» см. в разделе [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Параметры  
 **Доступные входные столбцы**  
 Перетащите входные столбцы для подсоединения к доступным уточняющим столбцам. Эти столбцы должны иметь совпадающие и поддерживаемые типы данных. Выберите строку сопоставления и щелкните ее правой кнопкой мыши, чтобы изменить ее в диалоговом окне [Создание связей](data-flow/transformations/create-relationships.md) .  
  
 **имя**;  
 Просмотрите имена доступных входных столбцов.  
  
 **Передать**  
 Укажите, нужно ли включать входные столбцы в вывод преобразования.  
  
 **Доступные уточняющие столбцы**  
 С помощью флажков выберите столбцы, по которым выполняется нечеткий уточняющий запрос.  
  
 **Уточняющий столбец**  
 Выберите уточняющие столбцы из списка доступных столбцов в ссылочной таблице. Выбор отражается установкой флажков в таблице **Доступные столбцы подстановок** . При выборе столбца в таблице **Доступные столбцы подстановок** создается выходной столбец, содержащий значение столбца ссылочной таблицы для каждой совпадающей возвращаемой строки.  
  
 **Псевдоним вывода**  
 Введите псевдоним выхода для каждого уточняющего столбца. По умолчанию, это будет имя уточняющего столбца с присоединенным индексным значением; однако можно выбрать любое уникальное описательное имя.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор преобразования "Нечеткий уточняющий запрос" &#40;вкладка "ссылочная таблица"&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [Редактор преобразования "Нечеткий уточняющий запрос" (вкладка "Дополнительно")](../../2014/integration-services/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  
