---
title: Nepodporovaný zprostředkovatel databáze
description: Zvolené připojení využívá nepodporovaného poskytovatele databáze.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c8fa073b47927f673914156c586bf27a121e53ea
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037566"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Zvolené připojení využívá nepodporovaného poskytovatele databáze.

Tato zpráva se zobrazí, když přetáhnete položky, které nepoužívají .NET Framework Zprostředkovatel dat pro SQL Server od **Průzkumník serveru** nebo **Průzkumníka databáze** do [nástrojů LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

**Návrhář o/R** podporuje pouze datová připojení, která používají poskytovatele .NET Framework pro SQL Server. Platná jsou pouze připojení k souboru databáze Microsoft SQL Server nebo Microsoft SQL Server.

Chcete-li tuto chybu opravit, přidejte pouze položky z datových připojení, která používají Zprostředkovatel dat .NET Framework pro SQL Server **designeru v/R**.

## <a name="see-also"></a>Viz také

- <xref:System.Data.SqlClient>
- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
