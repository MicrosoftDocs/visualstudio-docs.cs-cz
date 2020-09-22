---
title: Uživatel nemohl spustit uloženou proceduru sp_enable_sql_debug | Microsoft Docs
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
ms.openlocfilehash: c8131c7b16205b308e04b621dd1fcb536ba94c14
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852423"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Chyba: Uživatel nemohl spustit uloženou proceduru sp_enable_sql_debug.

Uloženou proceduru sp_enable_sql_debug nelze na serveru spustit. Příčinou může být:

- Problém s připojením Musíte mít stabilní připojení k serveru.

- Nedostatek nezbytných oprávnění na serveru. Pro ladění v SQL Server 2005 musí být účet, na kterém běží aplikace Visual Studio, i účet, který se používá pro připojení k SQL Server, členy role sysadmin. Účet použitý pro připojení k SQL Server je buď uživatelský účet systému Windows (Pokud používáte ověřování systému Windows), nebo účet s ID uživatele a heslem (Pokud používáte ověřování SQL).

Další informace najdete v tématu [Postup: nastavení SQL Server oprávnění pro ladění](/previous-versions/w1bhybwz(v=vs.100)).

## <a name="see-also"></a>Viz také

- [Postupy: nastavení SQL Server oprávnění pro ladění](/previous-versions/w1bhybwz(v=vs.100))
- [Nastavení ladění SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))