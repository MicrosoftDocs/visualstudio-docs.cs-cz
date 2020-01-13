---
title: 'Chyba: spuštění Transact-SQL skončilo bez ladění | Microsoft Docs'
ms.date: 11/08/2018
ms.topic: troubleshooting
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e86e24f775d8470b54ed7b9c54d27a5d3c1ee8da
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916306"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Chyba: Spuštění Transact-SQL skončilo bez ladění.

K této chybě dochází, pokud se pokoušíte ladit proceduru Transact-SQL nebo SQLCLR a ladicí program nepřijímá zprávy ladění z SQL Server.

K tomuto problému může dojít kvůli problémům se sítí nebo k problémům s SQL Server, ale nejpravděpodobnější příčinou je problém s oprávněním.

Jsou zapojeny dva účty:

- Účet aplikace je uživatelský účet, pod kterým [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] běžet.

- Účet připojení je identita, která slouží k vytvoření připojení k SQL Server. Tento účet není nutně stejný jako identita, kterou používá Visual Studio, jako by připojení používalo ověřování SQL.

  Ladění SQL vyžaduje, aby se účet aplikace shodoval s účtem připojení, nebo musí být sysadmin.

  Pokud používáte název účtu SQL jako SA, musí být účet aplikace nastavený na SQL Server jako správce systému. Ve výchozím nastavení jsou správci na počítači, na kterém běží SQL Server, SQL Server sysadmin.

  Chcete-li opravit tuto chybu, může být nutné:

  - Ověřte nastavení oprávnění. Další informace najdete v tématu [Postup: nastavení SQL Server oprávnění pro ladění](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

  - Ujistěte se, že ladění SQL je nastavené správně.

  - Obraťte se na správce sítě nebo databáze.

## <a name="see-also"></a>Viz také:

- [Nastavení ladění SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Postupy: nastavení SQL Server oprávnění pro ladění](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)