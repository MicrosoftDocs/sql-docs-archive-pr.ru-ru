---
title: Запуск программу sqlcmd
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
author: rothja
ms.author: jroth
ms.openlocfilehash: d71e6f140238599b3f22850ee9b63a0ee25d900b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656291"
---
# <a name="start-the-sqlcmd-utility"></a>Запуск программу sqlcmd
  Чтобы начать использовать программу `sqlcmd`, требуется запустить ее и подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Можно соединиться или с экземпляром, установленным по умолчанию, или с именованным экземпляром. Первый шаг — запуск программы `sqlcmd`.  
  
> [!NOTE]  
>  По умолчанию в программе `sqlcmd` используется проверка подлинности Windows. Для использования проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуется указать имя пользователя и пароль, применяя параметры **-U** и **-P** .  
  
> [!NOTE]  
>  По умолчанию [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] устанавливается как именованный экземпляр с именем **sqlexpress**.  
  
 Если подключение к этому экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] не было выполнено, то, возможно, потребуется настроить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на прием соединений.  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-default-instance-of-sql-server"></a>Запуск программы «sqlcmd» и подключение к экземпляру SQL Server по умолчанию  
  
1.  В меню **Пуск** выберите команду **выполнить**. В поле **Открыть** введите **cmd**, а затем нажмите кнопку **ОК** , чтобы открыть окно командной строки.  
  
2.  В командной строке введите `sqlcmd`.  
  
3.  Нажмите клавишу ВВОД.  
  
     Теперь установлено доверительное соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию, запущенным на этом компьютере.  
  
     **1>** — это `sqlcmd` запрос, указывающий номер строки. При каждом нажатии клавиши ВВОД номер увеличивается на единицу.  
  
4.  Чтобы завершить `sqlcmd` сеанс, введите `EXIT` в `sqlcmd` командной строке.  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-named-instance-of-sql-server"></a>Запуск программы sqlcmd и соединение с именованным экземпляром SQL Server  
  
1.  Откройте окно командной строки и введите `sqlcmd -S` *myServer\instanceName*. Замените *мойСервер\имяЭкземпляра* именем компьютера и экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , с которым нужно соединиться.  
  
2.  Нажмите клавишу ВВОД.  
  
     `sqlcmd`Приглашение (1>) указывает, что вы подключены к указанному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    > [!NOTE]  
    >  Введенные инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] хранятся в буфере. Они выполняются как пакет при обнаружении команды GO.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение файлов скрипта Transact-SQL с использованием программы sqlcmd](sqlcmd-run-transact-sql-script-files.md)  
  
  
