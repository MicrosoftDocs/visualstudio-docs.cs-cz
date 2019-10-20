---
title: Nástroje model EDM (Entity Data Model)
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d663b86603145f8a665f189e5abfbfa2b0b360ae
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672382"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Nástroje modelu EDM (Entity Data Model) v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entity Framework je objektově-relační technologie mapování, která umožňuje vývojářům v rozhraní .NET pracovat s relačními daty pomocí objektů specifických pro doménu. Díky tomu není nutná většina kódu pro přístup k datům, který vývojáři obvykle musí vytvářet. Entity Framework je doporučená technologie modelování objektů a relačních mapování (ORM) pro nové aplikace .NET.

 Od března 2016 je nejnovější vydaná verze [Entity Framework 6](https://msdn.microsoft.com/data/ef) . [Entity Framework 7](https://docs.efproject.net/en/latest/) je v předběžném vydání.

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] nástroje jsou navržené tak, aby vám pomohly sestavovat [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] aplikace. Kompletní dokumentace k nástrojům pro [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]: [Entity Framework](https://msdn.microsoft.com/data/jj590134).

 Pomocí [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]ch nástrojů můžete vytvořit *koncepční model* z existující databáze a pak graficky vizualizovat a upravit konceptuální model. Nebo můžete graf vytvořit nejprve koncepčního modelu a pak vygenerovat databázi, která podporuje váš model. V obou případech můžete model automaticky aktualizovat, pokud se změní podkladová databáze a automaticky generuje kód objektové vrstvy pro vaši aplikaci. Generování databáze a generování kódu vrstvy objektu jsou přizpůsobitelná.

 Jedná se o konkrétní nástroje, které tvoří model EDM (Entity Data Model) nástrojů v aplikaci Visual Studio 2015:

- K vizuálnímu vytváření a úpravám entit, přidružení, mapování a vztahů dědičnosti můžete použít [!INCLUDE[vstecado](../includes/vstecado-md.md)] **návrháře [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]** (**Entity Designer**). **Entity Designer** také generuje [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] nebo [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kód objektové vrstvy.

- Pomocí **průvodce [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]** můžete vygenerovat koncepční model z existující databáze a přidat do aplikace informace o připojení databáze.

- Pomocí **Průvodce vytvořením databáze** můžete nejdřív vytvořit koncepční model a pak vytvořit databázi, která tento model podporuje.

- **Průvodce aktualizací modelu** můžete použít k aktualizaci koncepčního modelu, modelu úložiště a mapování, pokud byly provedeny změny v podkladové databázi.

  > [!NOTE]
  > Počínaje sadou Visual Studio 2010 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] nástroje nepodporují [!INCLUDE[ss2k](../includes/ss2k-md.md)].

  Nástroje generují nebo upravují soubor. edmx. Tento soubor obsahuje informace, které popisují koncepční model, model úložiště a mapování mezi nimi. Další informace naleznete v tématu [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).

  Entity Framework Power Tools vám pomůžou sestavovat aplikace, které používají model EDM (Entity Data Model). Nástroje mohou generovat koncepční model, ověřit existující model, vytvořit soubory zdrojového kódu, které obsahují třídy objektů založené na koncepčním modelu a vytvořit soubory zdrojového kódu, které obsahují zobrazení, která model generuje. Podrobné informace naleznete v tématu [předem vygenerovaná zobrazení mapování](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[ADO.NET Entity Framework](https://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|Popisuje způsob použití [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]ch nástrojů, které [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] poskytuje k vytváření aplikací.|
|[Model EDM (Entity Data Model)](https://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|Poskytuje odkazy a informace pro práci s daty, která jsou používána aplikacemi založenými na [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)].|
|[Začínáme úplné rozhraní .NET (konzola, WinForms, WPF atd.)](/ef/ef6/get-started)|Poskytuje kurzy k vytváření desktopových aplikací .NET, které používají Entity Framework 7.|
|[Aplikace ASP.NET 5 do nové databáze](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Popisuje, jak vytvořit novou aplikaci ASP.NET 5 pomocí Entity Framework 7.|

## <a name="see-also"></a>Viz také
 [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
