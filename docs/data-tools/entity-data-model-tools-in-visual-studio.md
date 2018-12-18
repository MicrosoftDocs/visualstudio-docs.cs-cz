---
title: Entity Framework Tools
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 14a0e5b6b746356e38dfc71c26f53ced5a470e34
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066794"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Entity Framework Tools v sadě Visual Studio

Entity Framework je objektově relační mapování technologie, která umožňuje vývojářům .NET pro práci s relačními daty pomocí objektů specifických pro doménu. Díky tomu není nutná většina kódu pro přístup k datům, který vývojáři obvykle musí vytvářet. Entity Framework je doporučené objektově relační mapování (ORM určené) modelování technologie pro nové aplikace .NET.

Entity Framework Tools jsou určeny pro vám pomůže vytvářet aplikace Entity Framework (EF). Úplnou dokumentaci rozhraní Entity Framework je tady: [EF Core a EF 6](/ef/).

Pomocí Entity Framework Tools můžete vytvářet *koncepčního modelu* z existující databáze a pak graficky vizualizovat a upravit koncepčního modelu. Nebo můžete graficky nejprve vytvořte Koncepční model a pak vytvořte databázi, která podporuje model. V obou případech můžete automaticky aktualizovat váš model, pokud základní změny databáze a automatickému generování kódu na objektové vrstvě pro vaši aplikaci. Generování databáze a objektové vrstvě generování kódu jsou přizpůsobitelné.

Jsou nainstalované nástroje Entity Framework jako součást **ukládání a zpracování dat** úlohy v instalačním programu sady Visual Studio. Můžete také nainstalovat v rámci jednotlivých součástí **sad SDK, knihoven a architektur** kategorie.

Toto jsou konkrétní nástroje, které tvoří rozhraní Entity Framework tools v sadě Visual Studio:

- Můžete použít [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] návrháře** (**návrháři entit**) pro vizuální vytvoření a úprava entit, přidružení, mapování a vztahy dědičnosti. **Návrháři entit** také vygeneruje [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] nebo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kódu na objektové vrstvě.

- Můžete použít  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] průvodce** vygenerujte konceptuálního modelu z existující databáze a přidejte informace o připojení databáze do vaší aplikace.

- Můžete použít **vytvořením databáze** nejprve vytvořte Koncepční model a pak vytvořit databázi, která podporuje model.

- Můžete použít **aktualizace modelu průvodce** aktualizovat konceptuální model, úložiště modelu a mapování, když se provedly změny do databáze.

  > [!NOTE]
  > Od verze Visual Studio 2010, Entity Framework tools nepodporují [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].

Nástroje pro generování nebo upravit *edmx* souboru. To *edmx* soubor obsahuje informace, které popisují konceptuálního modelu, model úložiště a mapování mezi nimi. Další informace najdete v tématu [EDMX](https://docs.microsoft.com/ef/ef6/).

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) vám pomůže vytvářet aplikace, které používají modelu Entity Data Model. Nástroje pro výkon můžete generovat Koncepční model, ověření existující model, vytvářejí soubory zdrojového kódu, které obsahují objekt třídy založené na konceptuální model a vytvoření soubory zdrojového kódu, které obsahují zobrazení, která generuje modelu. Podrobné informace najdete v tématu [zobrazení mapování Pre-Generated](https://docs.microsoft.com/ef/ef6/fundamentals/performance/pre-generated-views).

## <a name="related-topics"></a>Související témata

| Název | Popis |
| - | - |
| [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index) | Popisuje způsob použití [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] nástroje, které [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] poskytuje k vytváření aplikací. |
| [Model EDM (Entity Data Model)](/dotnet/framework/data/adonet/entity-data-model) | Obsahuje odkazy a informace pro práci s daty, která používá aplikace založené na [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]. |
| [Dokumentace Entity Framework (EF))](https://docs.microsoft.com/ef/ef6/get-started) | Poskytuje index videa, kurzy a pokročilé dokumentací a pomohou vám využít na maximum Entity Framework. |
| [ASP.NET 5 aplikace pro novou databázi](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | Popisuje, jak vytvořit novou aplikaci ASP.NET 5 pomocí Entity Frameworku 7. |

## <a name="see-also"></a>Viz také:

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)