---
title: Entity Framework Tools
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6efcd0ca4e8274df7667b5a5b2b75020def8c358
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72807026"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Entity Framework Tools v aplikaci Visual Studio

Entity Framework je objektově-relační technologie mapování, která umožňuje vývojářům v rozhraní .NET pracovat s relačními daty pomocí objektů specifických pro doménu. Díky tomu není nutná většina kódu pro přístup k datům, který vývojáři obvykle musí vytvářet. Entity Framework je doporučená technologie modelování objektů a relačních mapování (ORM) pro nové aplikace .NET.

Entity Framework Tools jsou navržené tak, aby vám pomohly sestavovat aplikace Entity Framework (EF). Kompletní dokumentace k Entity Framework je tady: [Přehled – EF 6](/ef/ef6/).

  > [!NOTE]
  > Entity Framework Tools popsané na této stránce se používají ke generování souborů *. edmx* , které nejsou v EF Core podporované. Pokud chcete vygenerovat model EF Core z existující databáze, přečtěte si téma [Zpětná analýza-EF Core](/ef/core/managing-schemas/scaffolding). Další informace o rozdílech mezi EF 6 a EF Core najdete v tématu [porovnání EF 6 a EF Core](/ef/efcore-and-ef6/).

Pomocí Entity Framework Tools můžete vytvořit *koncepční model* z existující databáze a pak graficky vizualizovat a upravit konceptuální model. Nebo můžete graf vytvořit nejprve koncepčního modelu a pak vygenerovat databázi, která podporuje váš model. V obou případech můžete model automaticky aktualizovat, pokud se změní podkladová databáze a automaticky generuje kód objektové vrstvy pro vaši aplikaci. Generování databáze a generování kódu vrstvy objektu jsou přizpůsobitelná.

Nástroje Entity Framework jsou nainstalovány v rámci úlohy **ukládání a zpracování dat** v instalační program pro Visual Studio. Můžete je také nainstalovat jako jednotlivé komponenty v kategorii sady **SDK, knihovny a architektury** .

Jedná se o konkrétní nástroje, které tvoří Entity Framework nástrojů v aplikaci Visual Studio:

- K vizuálnímu vytváření a úpravám entit, přidružení, mapování a vztahů dědičnosti můžete použít [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] **návrháře[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]** (**Entity Designer**). **Entity Designer** také generuje [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] nebo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kód objektové vrstvy.

- Pomocí **průvodce[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]** můžete vygenerovat koncepční model z existující databáze a přidat do aplikace informace o připojení databáze.

- Pomocí **Průvodce vytvořením databáze** můžete nejdřív vytvořit koncepční model a pak vytvořit databázi, která tento model podporuje.

- **Průvodce aktualizací modelu** můžete použít k aktualizaci koncepčního modelu, modelu úložiště a mapování, pokud byly provedeny změny v podkladové databázi.

  > [!NOTE]
  > Počínaje sadou Visual Studio 2010 Entity Framework nástroje nepodporují [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].

Nástroje generují nebo upravují soubor *. edmx* . Tento soubor *. edmx* obsahuje informace, které popisují koncepční model, model úložiště a mapování mezi nimi. Další informace naleznete v tématu [EDMX](/ef/ef6/).

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) vám pomůžou sestavovat aplikace, které používají model EDM (Entity Data Model). Nástroje Power Tools mohou generovat koncepční model, ověřit existující model, vytvořit soubory zdrojového kódu, které obsahují třídy objektů založené na koncepčním modelu, a vytvořit soubory zdrojového kódu, které obsahují zobrazení, která model generuje. Podrobné informace naleznete v tématu [předem vygenerovaná zobrazení mapování](https://docs.microsoft.com/ef/ef6/fundamentals/performance/pre-generated-views).

## <a name="related-topics"></a>Související témata

| Název | Popis |
| - | - |
| [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index) | Popisuje způsob použití [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]ch nástrojů, které [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] poskytuje k vytváření aplikací. |
| [Model EDM (Entity Data Model)](/dotnet/framework/data/adonet/entity-data-model) | Poskytuje odkazy a informace pro práci s daty, která jsou používána aplikacemi založenými na [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]. |
| [Dokumentace k Entity Framework (EF)](/ef/ef6/get-started) | Poskytuje rejstřík videí, výukových kurzů a pokročilých dokumentů, které vám pomůžou vydávat maximum z Entity Framework. |
| [Aplikace ASP.NET 5 do nové databáze](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | Popisuje, jak vytvořit novou aplikaci ASP.NET 5 pomocí Entity Framework 7. |

## <a name="see-also"></a>Viz také:

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)