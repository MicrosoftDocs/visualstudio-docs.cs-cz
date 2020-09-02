---
title: 'Chyba: spuštění Transact-SQL skončilo bez ladění | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 7a4d4999-3973-4339-ba6a-f0d19bcb1d4a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cdfcaa42c55f87711b0889c6a67d1a4799b84fed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681079"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Chyba: Spuštění Transact-SQL skončilo bez ladění.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K této chybě dochází, pokud se pokoušíte ladit proceduru Transact-SQL nebo SQLCLR a ladicí program nepřijímá zprávy ladění z SQL Server.  
  
 Příčinou může být problémy se sítí nebo problémy s SQL Server, ale nejpravděpodobnější příčinou je problém s oprávněními.  
  
 Jsou zapojeny dva účty:  
  
- Účet aplikace je uživatelský účet, který [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] je spuštěný jako.  
  
- Účet připojení je identita, která slouží k vytvoření připojení k SQL Server. To není nutně stejné jako identita, kterou používá Visual Studio, jako by připojení používalo ověřování SQL.  
  
  Ladění SQL vyžaduje, aby se účet aplikace shodoval s účtem připojení nebo se musí jednat o správce systému.  
  
  Pokud používáte přihlášení SQL jako SA, účet aplikace musí být nastaven na SQL Server jako správce systému. Ve výchozím nastavení jsou správci na počítači, na kterém běží SQL Server, na SQL Server sysadmin.  
  
  Chcete-li opravit tuto chybu, může být nutné:  
  
- Ověřte nastavení oprávnění. Další informace najdete v tématu [Postup: nastavení SQL Server oprávnění pro ladění](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
- Ujistěte se, že ladění SQL je nastavené správně.  
  
- Obraťte se na správce sítě nebo databáze.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení ladění SQL](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [Postupy: nastavení SQL Server oprávnění pro ladění](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)   
 [Vzdálené ladění](../debugger/remote-debugging.md)
