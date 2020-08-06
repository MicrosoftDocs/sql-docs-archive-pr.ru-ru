---
title: Шаг 3. Изменение значения конфигурации свойства Directory | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ba2a091f-361c-4331-afe2-53b465164c36
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a71a7a181322d60caca98da4ddf3261cbce99c9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657147"
---
# <a name="step-3-modifying-the-directory-property-configuration-value"></a>Шаг 3. Изменение значения конфигурации свойства Directory
  В этой задаче предстоит изменить хранимый в файле SSISTutorial.dtsConfig параметр настройки свойства Value переменной уровня пакета `User::varFolderName`. Эта переменная обновляет свойство Directory контейнера "цикл по каждому элементу". Измененное значение будет указывать на `New Sample Data` папку, созданную в предыдущей задаче. После изменения параметра настройки конфигурации и выполнения пакета свойство Directory будет обновляться этой переменной с использованием значения из файла конфигурации, а не значения из каталога, первоначально заданного в данном пакете.  
  
### <a name="to-modify-the-configuration-setting-of-the-directory-property"></a>Изменение параметра конфигурации для свойства Directory  
  
1.  В приложении «Блокнот» или другом текстовом редакторе найдите и откройте файл конфигурации SSISTutorial.dtsConfig, созданный в предыдущей задаче с помощью мастера настройки пакета.  
  
2.  Измените значение элемента **ConfiguredValue пуст** , чтобы оно совпадало с путем к `New Sample Data` папке, созданной в предыдущей задаче. Не заключайте этот путь в кавычки. Если `New Sample Data` Папка находится на корневом уровне диска (например, C: \\ ), обновленный код XML должен быть подобен следующему примеру:  
  
     `<?xml version="1.0"?><DTSConfiguration><DTSConfigurationHeading><DTSConfigurationFileInfo GeneratedBy="DOMAIN\UserName" GeneratedFromPackageName="Lesson 5" GeneratedFromPackageID="{F4475E73-59E3-478F-8EB2-B10AFA61D3FA}" GeneratedDate="6/10/2012 8:16:50 AM"/></DTSConfigurationHeading><Configuration ConfiguredType="Property" Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"><ConfiguredValue></ConfiguredValue></Configuration></DTSConfiguration>`  
  
     Разумеется, сведения о заголовке,, `GeneratedBy` `GeneratedFromPackageID` и **женератеддате** будут отличаться в файле. `Configuration` — элемент, на который необходимо обратить внимание. Свойство `Value` переменной `User::varFolderName` теперь содержит значение «C:\New Sample Data».  
  
3.  Сохраните изменения и закройте текстовый редактор.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Шаг 4. Проверка учебного пакета, созданного на занятии 5](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
  
