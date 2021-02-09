---
title: Nepodporovaný zprostředkovatel databáze
description: Vybrané připojení používá nepodporovaného poskytovatele databáze. Zobrazit informace o této zprávě aplikace Visual Studio Návrhář relací objektů (Návrhář O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 246559abc0d1cbc12754b708bbc5938e9e190ddd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858302"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Zvolené připojení využívá nepodporovaného poskytovatele databáze.

Tato zpráva se zobrazí, když přetáhnete položky, které nepoužívají .NET Framework Zprostředkovatel dat pro SQL Server od **Průzkumník serveru** nebo **Průzkumníka databáze** do [nástrojů LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

**Návrhář o/R** podporuje pouze datová připojení, která používají poskytovatele .NET Framework pro SQL Server. Platná jsou pouze připojení k souboru databáze Microsoft SQL Server nebo Microsoft SQL Server.

Chcete-li tuto chybu opravit, přidejte pouze položky z datových připojení, která používají Zprostředkovatel dat .NET Framework pro SQL Server **designeru v/R**.

## <a name="see-also"></a>Viz také

- <xref:System.Data.SqlClient>
- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
