---
title: Spuštění Transact-SQL skončilo bez ladění | Microsoft Docs
ms.date: 11/08/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 660b6c8b1f8d09baf35d3d019fe80d428e9d7525
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871127"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Chyba: Spuštění Transact-SQL skončilo bez ladění.

K této chybě dochází, pokud se pokoušíte ladit proceduru Transact-SQL nebo SQLCLR a ladicí program nepřijímá zprávy ladění z SQL Server.

K tomuto problému může dojít kvůli problémům se sítí nebo k problémům s SQL Server, ale nejpravděpodobnější příčinou je problém s oprávněním.

Jsou zapojeny dva účty:

- Účet aplikace je uživatelský účet, který [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] je spuštěný jako.

- Účet připojení je identita, která slouží k vytvoření připojení k SQL Server. Tento účet není nutně stejný jako identita, kterou používá Visual Studio, jako by připojení používalo ověřování SQL.

  Ladění SQL vyžaduje, aby se účet aplikace shodoval s účtem připojení, nebo musí být sysadmin.

  Pokud používáte název účtu SQL jako SA, musí být účet aplikace nastavený na SQL Server jako správce systému. Ve výchozím nastavení jsou správci na počítači, na kterém běží SQL Server, SQL Server sysadmin.

  Chcete-li opravit tuto chybu, může být nutné:

  - Ověřte nastavení oprávnění. Další informace najdete v tématu [Postup: nastavení SQL Server oprávnění pro ladění](/previous-versions/w1bhybwz(v=vs.100)).

  - Ujistěte se, že ladění SQL je nastavené správně.

  - Obraťte se na správce sítě nebo databáze.

## <a name="see-also"></a>Viz také

- [Nastavení ladění SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Postupy: nastavení SQL Server oprávnění pro ladění](/previous-versions/w1bhybwz(v=vs.100))
- [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)