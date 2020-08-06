---
title: Настройка зашифрованной зеркальной базы данных | Документы Майкрософт
ms.custom: ''
ms.date: 06/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- cryptography [SQL Server], database mirroring
- encryption [SQL Server], database mirroring
- database master key [SQL Server], database mirroring
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 7329a575-be29-46e0-abc6-1344db37920c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a5148411792f1ea881bba59e599252284575bbdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733046"
---
# <a name="set-up-an-encrypted-mirror-database"></a>Настройка зашифрованной зеркальной базы данных

Чтобы включить автоматическое шифрование главного ключа базы данных зеркальной базы данных, необходимо предоставить пароль, используемый для шифрования главного ключа экземпляра зеркального сервера. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздние версии включают в себя механизмы для передачи пароля. Перед началом зеркального отображения базы данных необходимо создать учетные данные для главного ключа базы данных с помощью хранимой процедуры **sp_control_dbmasterkey_password** . Необходимо повторить этот процесс для каждой базы данных, для которой будет создаваться зеркальное отображение. Дополнительные сведения см. в разделе [sp_control_dbmasterkey_password (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql).
  
> [!CAUTION]  
>  Не включайте дешифрование базы данных отработки отказа, оно не должно быть для **sa** и другим серверам-участникам с обширными правами доступа. База данных может быть настроена таким образом, чтобы иерархия ее ключей не могла быть расшифрована главным ключом службы. Эта возможность поддерживается для максимальной защиты баз данных, содержащих информацию, доступ к которой не может иметь **sa** или другие участники на уровне сервера с обширными правами доступа. Включение расшифровки отработки отказа для такой базы данных сводит на нет эту защиту, позволяя **sa** и другим привилегированным участникам на уровне сервера расшифровывать базу данных.  


<!-- Note: We cannot append '?view=sql-server-2016' to these, even tho in theory we might want to. -->

## <a name="see-also"></a>См. также:

[sp_control_dbmasterkey_password (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql)

[CREATE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/create-master-key-transact-sql)

[ALTER MASTER KEY (Transact-SQL)](/sql/t-sql/statements/alter-master-key-transact-sql)

[Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)

[Настройка зеркального отображения базы данных (SQL Server)](database-mirroring-sql-server.md)

