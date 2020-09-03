---
title: 'Chyba: uživatel nemohl spustit uloženou proceduru sp_enable_sql_debug | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1da494b5bb8c168775e2183f41113f00d021792
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460062"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Chyba: Uživatel nemohl spustit uloženou proceduru sp_enable_sql_debug.

Uloženou proceduru sp_enable_sql_debug nelze na serveru spustit. Příčinou může být:

- Problém s připojením Musíte mít stabilní připojení k serveru.

- Nedostatek nezbytných oprávnění na serveru. Pro ladění v SQL Server 2005 musí být účet, na kterém běží aplikace Visual Studio, i účet, který se používá pro připojení k SQL Server, členy role sysadmin. Účet použitý pro připojení k SQL Server je buď uživatelský účet systému Windows (Pokud používáte ověřování systému Windows), nebo účet s ID uživatele a heslem (Pokud používáte ověřování SQL).

Další informace najdete v tématu [Postup: nastavení SQL Server oprávnění pro ladění](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

## <a name="see-also"></a>Viz také

- [Postupy: nastavení SQL Server oprávnění pro ladění](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Nastavení ladění SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))