---
title: Nástroje modelu Entity Data
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 942678000cf633caeb0a55d8ca41dc092f1e484f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53047649"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Nástroje modelu dat entity v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Entity Framework je objektově relační mapování technologie, která umožňuje vývojářům .NET pro práci s relačními daty pomocí objektů specifických pro doménu. Díky tomu není nutná většina kódu pro přístup k datům, který vývojáři obvykle musí vytvářet. Entity Framework je doporučené objektově relační mapování (ORM určené) modelování technologie pro nové aplikace .NET.

 Od března 2016 je nejnovější vydanou verzi [Entity Framework 6](https://msdn.microsoft.com/data/ef) . [Entity Frameworku 7](https://docs.efproject.net/en/latest/) je v předběžné verzi.

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Nástroje jsou navrženy pro vám pomůže vytvářet [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] aplikací. Kompletní dokumentaci k [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] nástroje je tady: [Entity Framework](https://msdn.microsoft.com/data/jj590134).

 S [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] nástroje, můžete vytvořit *koncepčního modelu* z existující databáze a pak graficky vizualizovat a upravit koncepčního modelu. Nebo můžete graficky nejprve vytvořte Koncepční model a pak vytvořte databázi, která podporuje model. V obou případech můžete automaticky aktualizovat váš model, pokud základní změny databáze a automatickému generování kódu na objektové vrstvě pro vaši aplikaci. Generování databáze a objektové vrstvě generování kódu jsou přizpůsobitelné.

 Toto jsou konkrétní nástroje, které tvoří Entity Data Model Tools v sadě Visual Studio 2015:

- Můžete použít [!INCLUDE[vstecado](../includes/vstecado-md.md)]  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] návrháře** (**návrháři entit**) pro vizuální vytvoření a úprava entit, přidružení, mapování a vztahy dědičnosti. **Návrháři entit** také vygeneruje [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] nebo [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kódu na objektové vrstvě.

- Můžete použít  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] průvodce** vygenerujte konceptuálního modelu z existující databáze a přidejte informace o připojení databáze do vaší aplikace.

- Můžete použít **vytvořením databáze** nejprve vytvořte Koncepční model a pak vytvořit databázi, která podporuje model.

- Můžete použít **aktualizace modelu průvodce** aktualizovat konceptuální model, úložiště modelu a mapování, když se provedly změny do databáze.

  > [!NOTE]
  >  Od verze Visual Studio 2010, [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] nástroje nepodporují [!INCLUDE[ss2k](../includes/ss2k-md.md)].

  Nástroje pro generování nebo upravit soubor .edmx. Tento soubor obsahuje informace, které popisují konceptuálního modelu, model úložiště a mapování mezi nimi. Další informace najdete v tématu [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).

  Entity Framework Power Tools vám pomůže vytvářet aplikace, které používají modelu Entity Data Model. Nástroje mohou generovat Koncepční model, ověřit existující model, vytvářet soubory zdrojového kódu, které obsahují objekt třídy založené na konceptuální model a vytvářejí soubory zdrojového kódu, které obsahují zobrazení, která generuje modelu. Podrobné informace najdete v tématu [zobrazení mapování Pre-Generated](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|Popisuje způsob použití [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] nástroje, které [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] poskytuje k vytváření aplikací.|
|[Model EDM (Entity Data Model)](http://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|Obsahuje odkazy a informace pro práci s daty, která používá aplikace založené na [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)].|
|[Začínáme na úplné rozhraní .NET (konzola, WinForms, WPF atd.)](https://docs.efproject.net/en/latest/platforms/full-dotnet/getting-started.html)|Kurzy týkající se vytváření desktopových aplikací .NET, které pomocí Entity Frameworku 7.|
|[ASP.NET 5 aplikace pro novou databázi](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Popisuje, jak vytvořit novou aplikaci ASP.NET 5 pomocí Entity Frameworku 7.|

## <a name="see-also"></a>Viz také
 [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
