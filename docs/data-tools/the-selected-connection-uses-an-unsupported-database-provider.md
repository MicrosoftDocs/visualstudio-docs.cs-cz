---
title: Zvolené připojení využívá nepodporovaného poskytovatele databáze.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d102404cf14fecc89fc65773d283d748914bc0a5
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174158"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Zvolené připojení využívá nepodporovaného poskytovatele databáze.

Tato zpráva se zobrazí při přetažení položky, které nepoužívají zprostředkovatele dat .NET Framework pro SQL Server z **Průzkumníka serveru** nebo **Průzkumník databáze** na [technologie LINQ to SQL nástroje ve Vizuálu Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

**O/R Designer** podporuje pouze datová připojení, které používají zprostředkovatele .NET Framework pro SQL Server. Platí pouze připojení k serveru Microsoft SQL Server nebo soubor databáze Microsoft SQL Server.

Chcete-li opravit tuto chybu, přidávat pouze položky z datová připojení, které používají zprostředkovatele dat .NET Framework pro SQL Server **O/R Designer**.

## <a name="see-also"></a>Viz také:

- <xref:System.Data.SqlClient>
- [Zprávy Návrháře relací objektů](../data-tools/o-r-designer-messages.md)
- [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
