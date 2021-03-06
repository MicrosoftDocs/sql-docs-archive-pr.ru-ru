---
title: Параметры (текстовый редактор — XML — страница "Разное") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 1a9509f0-c663-4b31-b396-7f5dc4371651
author: rothja
ms.author: jroth
ms.openlocfilehash: d937368d30122442ccbc40372a6b8e1cabc141e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727329"
---
# <a name="options-text-editor---xml---miscellaneous-page"></a>Параметры ("Текстовый редактор" — "XML" — страница "Разное")

Диалоговое окно **Параметры** позволяет изменять параметры автозаполнения и схемы для редактора XML. Для доступа к этим параметрам в меню **Сервис** щелкните пункт **Параметры**, разверните папку **Редактор текстов** , щелкните пункт **XML** , затем — пункт **Разное** .  
  
## <a name="auto-insert"></a>Автоматическая вставка  
 **Закрывать теги**  
 Текстовый редактор добавляет завершающие теги при составлении элементов XML. Когда выбран начальный тег, редактор вставляет соответствующий завершающий тег, включая соответствующий префикс пространства имен. Этот флажок выбран по умолчанию.  
  
 **Кавычки атрибутов**  
 При составлении XML-атрибутов редактор вставляет символы `="``"` и устанавливает курсор (**^)** внутри них. Этот флажок выбран по умолчанию.  
  
 **Объявления пространств имен**  
 Редактор автоматически вставляет объявления пространств имен, где они необходимы. Этот флажок выбран по умолчанию.  
  
 **Другая разметка (комментарии, CDATA)**  
 Комментарии, CDATA, DOCTYPE, инструкции обработки и другие элементы разметки завершаются автоматически. Этот флажок выбран по умолчанию.  
  
## <a name="network"></a>Сеть  
 **Автоматически загружать DTD и схемы**  
 Схемы и определения типов документов (DTD) автоматически загружаются с адресов HTTP. Эта функция использует System.Net в режиме автоматического определения прокси-сервера. Этот флажок выбран по умолчанию.  
  
## <a name="outlining"></a>Структуризация  
 **Переходить в режим структурирования после открытия файлов**  
 Включает функцию структурирования при открытии файла. Этот флажок выбран по умолчанию.  
  
## <a name="caching"></a>Caching  
 **Схемы**  
 Определяет местоположение кэша схемы. Кнопка обзора (...) открывает текущее расположение кэша схемы в новом окне. Расположение по умолчанию — *\<Management Studio install directory>* \Xml\Schemas.  
