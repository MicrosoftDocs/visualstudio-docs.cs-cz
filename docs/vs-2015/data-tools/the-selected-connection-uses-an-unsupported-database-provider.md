---
title: Vybrané připojení používá nepodporovaného poskytovatele databáze | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4e79d8408fba54cf192d51f9d2ead8c0ffafe1f0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667197"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Zvolené připojení využívá nepodporovaného poskytovatele databáze.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato zpráva se zobrazí, když přetáhnete položky, které nepoužívají .NET Framework Zprostředkovatel dat pro SQL Server z **Průzkumník serveru** /**Průzkumník databáze** do [nástrojů LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

 @No__t_0 podporuje pouze datová připojení, která používají poskytovatele .NET Framework pro SQL Server. Platná jsou pouze připojení k souboru databáze Microsoft SQL Server nebo Microsoft SQL Server.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Přidejte pouze položky z datových připojení, která pro SQL Server [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] používají Zprostředkovatel dat .NET Framework.

## <a name="see-also"></a>Viz také
 Návod pro [poskytovatele dat <xref:System.Data.SqlClient> .NET Framework](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) [: vytváření tříd LINQ to SQL (Návrhář O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)