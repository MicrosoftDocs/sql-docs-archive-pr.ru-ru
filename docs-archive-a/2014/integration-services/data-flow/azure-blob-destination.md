---
title: Назначение больших двоичных объектов Azure | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobdest.f1
- sql11.dts.designer.afpblobdest.f1
ms.assetid: 820a1e7a-7182-4c7b-ab56-5b4097a7e042
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fb406d38b17748e8284acee4b2849a9fd99e53ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738555"
---
# <a name="azure-blob-destination"></a>Назначение больших двоичных объектов Azure
  Компонент **Назначение больших двоичных объектов Azure** позволяет пакету SSIS записывать данные в BLOB-объект Azure. Поддерживаются следующие форматы файлов: CSV и AVRO. Ддраг. Перетащите **назначение больших двоичных объектов Azure** в конструктор потока данных и дважды щелкните его, чтобы открыть редактор.  
  
1.  В поле **Диспетчер подключений службы хранилища Azure** укажите существующий диспетчер подключений службы хранилища Azure или создайте новый, который ссылается на учетную запись хранения Azure.  
  
2.  В поле **Имя контейнера больших двоичных объектов** укажите имя контейнера больших двоичных объектов, который содержит исходные файлы.  
  
3.  В поле **Имя большого двоичного объекта** укажите путь к большому двоичному объекту.  
  
4.  В поле **Формат файла большого двоичного объекта** укажите формат большого двоичного объекта, который следует использовать.  
  
5.  Если формат файла — CSV, необходимо указать значение **знака-разделителя столбцов** . Также выберите **имена столбцов в первой строке данных** , если первая строка в файле содержит имена столбцов.  
  
6.  После указания сведений о соединении переключитесь на страницу **Столбцы** , чтобы сопоставить столбцы источника со столбцами назначения для потока данных служб SSIS.  
  
  
