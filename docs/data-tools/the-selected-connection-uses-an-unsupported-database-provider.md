---
title: Zvolené připojení využívá nepodporovaného poskytovatele databáze.
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 52b88e1de91c2b2da629b6b9034ac552b8d88d5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281315"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Zvolené připojení využívá nepodporovaného poskytovatele databáze.

Tato zpráva se zobrazí, když přetáhnete položky, které nepoužívají .NET Framework Zprostředkovatel dat pro SQL Server od **Průzkumník serveru** nebo **Průzkumníka databáze** do [nástrojů LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

**Návrhář o/R** podporuje pouze datová připojení, která používají poskytovatele .NET Framework pro SQL Server. Platná jsou pouze připojení k souboru databáze Microsoft SQL Server nebo Microsoft SQL Server.

Chcete-li tuto chybu opravit, přidejte pouze položky z datových připojení, která používají Zprostředkovatel dat .NET Framework pro SQL Server **designeru v/R**.

## <a name="see-also"></a>Viz také

- <xref:System.Data.SqlClient>
- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
