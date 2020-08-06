---
title: Занятие 4. Создание базы данных в службе хранилища Azure | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a9ae1501-b614-49d3-b975-6569da8350b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 50fca85111d5897b738e577e7735049e0b055a03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668303"
---
# <a name="lesson-4-create-a-database-in-azure-storage"></a>Занятие 4: Создание базы данных в службе хранилища Azure
  На этом занятии вы узнаете, как создать базу данных с помощью компонента SQL Server Data Files в Azure. Обратите внимание, что перед началом этого занятия необходимо завершить занятия 1, 2 и 3. Занятие 3 является очень важным шагом, так как необходимо сохранить сведения о контейнере хранилища Azure и связанном с ним имени политики и ключе SAS в SQL Server хранилище учетных данных перед занятием 4.  
  
 Для каждого контейнера хранилища, используемого файлом данных или журнала, необходимо создать учетные данные SQL Server, имя которых соответствует пути контейнера. Затем можно создать новую базу данных в службе хранилища Azure.  
  
 Для этого занятия предполагается, что вы уже выполнили следующие шаги.  
  
-   У вас есть учетная запись хранения Azure.  
  
-   Вы создали контейнер в учетной записи хранения Azure.  
  
-   Создали политику в контейнере с правами на чтение, запись и перечисление. Создали ключ SAS.  
  
-   Создали учетные данные SQL Server на исходном компьютере.  
  
 Чтобы создать базу данных в Azure с помощью компонента SQL Server Data Files в службе хранилища Azure, выполните следующие действия.  
  
1.  Подключитесь к среде Microsoft SQL Server Management Studio.  
  
2.  В обозревателе объектов подключитесь к экземпляру установленного компонента Database Engine.  
  
3.  На панели инструментов Стандартная выберите пункт Создать запрос.  
  
4.  Скопируйте и вставьте следующий пример в окно запроса (при необходимости измените). Обратите внимание, что поле FILENAME указывает URI-путь к файлу базы данных в контейнере хранилища, он должен начинаться с https.  
  
    ```  
  
    --Create a database that uses a SQL Server credential    
    CREATE DATABASE TestDB1    
    ON   
    (NAME = TestDB1_data,   
       FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Data.mdf')   
     LOG ON   
    (NAME = TestDB1_log,   
        FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Log.ldf')   
    GO  
  
    ```  
  
     Добавьте данные в вашу базу данных.  
  
    ```  
  
    USE TestDB1;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
5.  Чтобы увидеть новую базу данных TestDB1 на локальном сервере SQL Server, обновите базы данных в обозревателе объектов.  
  
6.  Аналогично, чтобы увидеть вновь созданную базу данных в учетной записи хранения, подключитесь к учетной записи хранения с помощью среды SQL Server Management Studio (SSMS). Чтобы получить сведения о подключении к хранилищу Azure с помощью SQL Server Management Studio, выполните следующие действия.  
  
    1.  Сначала получите сведения об учетной записи хранилища. Войдите на портал управления. После этого щелкните **Хранилище** и выберите нужную учетную запись хранилища. Затем щелкните **Управление ключами доступа** в нижней части страницы. Откроется диалоговое окно, аналогичное следующему:  
  
         ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-1.gif "SQL 14 CTP2")  
  
    2.  Скопируйте значения **имени учетной записи хранения** и **первичного ключа доступа** в диалоговое окно **Подключение к службе хранилища Azure** в SSMS. Затем нажмите кнопку **Подключить**. Сведения о контейнерах учетной записи хранилища появятся в SSMS, как показано на снимке экрана ниже.  
  
         ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2.gif "SQL 14 CTP2")  
  
 На следующем снимке экрана показана новая созданная база данных в локальной среде службы хранилища Azure.  
  
 ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-2b.gif "SQL 14 CTP2")  
  
 **Примечание.** При наличии активных ссылок на файлы данных в контейнере любые попытки удалить связанные ученые данные SQL Server завершатся ошибкой. Аналогично, если определенный файл базы данных в большом двоичном объекте уже арендуется и его необходимо удалить, вначале необходимо разорвать аренду в большом двоичном объекте. Для этого можно использовать [большой двоичный объект](https://msdn.microsoft.com/library/azure/ee691972.aspx).  
  
 С помощью этой новой функции можно настроить SQL Server, чтобы любая инструкция CREATE DATABASE по умолчанию создавала облачную базу данных. Иными словами, можно задать данные и расположения журналов по умолчанию в свойствах экземпляра SQL Server Management Studio Server, так что при каждом создании базы данных все файлы базы данных (MDF, LDF) создаются как страничные BLOB-объекты в службе хранилища Azure.  
  
 Чтобы создать базу данных в службе хранилища Azure с помощью SQL Server Management Studio пользовательского интерфейса, выполните следующие действия.  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента SQL Server Database Engine и разверните его.  
  
2.  Щелкните правой кнопкой мыши элемент Базы данных, а затем выберите пункт Создать базу данных.  
  
3.  В диалоговом окне «Создание базы данных» введите имя базы данных.  
  
4.  Измените значения первичных данных по умолчанию и файлов журнала транзакций, щелкнув соответствующую ячейку в сетке файлов базы данных и введя новое значение. Кроме того, укажите путь к файлу. В поле «Путь» введите URL-адрес контейнера хранилища, например `https://teststorageaccnt.blob.core.windows.net/testcontainer/`. В поле «Имя файла» введите физические имена файлов базы данных (MDF и LDF).  
  
     ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-4-6-4.gif "SQL 14 CTP2")  
  
     Дополнительные сведения см. в статье [AДобавление файлов данных или журналов в базу данных](databases/add-data-or-log-files-to-a-database.md).  
  
5.  Для всех других параметров сохраните значения по умолчанию.  
  
6.  Щелкните ОК.  
  
 Чтобы увидеть новую базу данных TestDB1 на локальном сервере SQL Server, обновите базы данных в обозревателе объектов. Аналогично, чтобы увидеть вновь созданную базу данных в учетной записи хранилища, подключитесь к учетной записи хранилища с помощью среды SQL Server Management Studio (SSMS), как описано ранее в этом занятии.  
  
 **Следующее занятие:**  
  
 [Занятие 5. &#40;необязательно&#41; шифрование базы данных с помощью TDE](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)  
  
  