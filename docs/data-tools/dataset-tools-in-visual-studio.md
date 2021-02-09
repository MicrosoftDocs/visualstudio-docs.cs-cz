---
title: Nástroje datové sady
description: Projděte si nástroje datové sady, které jsou dostupné v sadě Visual Studio. Přečtěte si o pracovním postupu datových sad, datových sadách a N-vrstvých architektuře a datových sadách a XML.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 4e711d60010117f3a5081470ab8e6e656a7e6e90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866993"
---
# <a name="dataset-tools-in-visual-studio"></a>Nástroje datových sad v sadě Visual Studio

> [!NOTE]
> Datové sady a související třídy jsou starší technologie .NET od začátku 2000s, které aplikacím umožňují pracovat s daty v paměti v době, kdy jsou aplikace odpojeny od databáze. Jsou zvláště užitečné pro aplikace, které umožňují uživatelům upravovat data a uchovávat změny zpátky v databázi. I když se datové sady ukázaly jako velmi úspěšná technologie, doporučujeme, aby nové aplikace .NET používaly Entity Framework. Entity Framework poskytuje přirozenější způsob, jak pracovat s tabulkovými daty jako objektovými modely a má jednodušší programovací rozhraní.

`DataSet`Objekt je objekt v paměti, který je v podstatě zkrácenou databází. Obsahuje `DataTable` objekty, `DataColumn` a, `DataRow` ve kterých můžete ukládat a upravovat data z jedné nebo více databází, aniž byste museli udržovat otevřené připojení. Datová sada uchovává informace o změnách dat, takže aktualizace je možné sledovat a odeslat zpět do databáze, když se vaše aplikace znovu připojí.

Datové sady a související třídy jsou definovány v <xref:System.Data?displayProperty=fullName> oboru názvů v rozhraní .NET API. Datové sady můžete vytvářet a upravovat dynamicky v kódu pomocí ADO.NET. Dokumentace v této části ukazuje, jak pracovat s datovými sadami pomocí návrhářů sady Visual Studio. Datové sady, které jsou vytvořené prostřednictvím návrháře, používají objekty **TableAdapter** k interakci s databází. Datové sady, které jsou vytvořeny programově, používají objekty **DataAdapter** . Informace o tom, jak vytvořit datové sady prostřednictvím kódu programu, najdete v tématu datové [adaptéry a Datačtecí](/dotnet/framework/data/adonet/dataadapters-and-datareaders)nástroje.

Pokud vaše aplikace potřebuje číst data z databáze a neprovádí aktualizace, přidává nebo odstraňuje, můžete obvykle dosáhnout lepšího výkonu pomocí `DataReader` objektu pro načtení dat do obecného `List` objektu nebo jiného objektu kolekce. Pokud zobrazujete data, můžete datové vazby navazovat do kolekce.

## <a name="dataset-workflow"></a>Pracovní postup datové sady

Sada Visual Studio poskytuje nástroje pro zjednodušení práce s datovými sadami. Základní kompletní pracovní postup:

- Použijte [okno zdroje dat](add-new-data-sources.md#data-sources-window) k vytvoření nové datové sady z jednoho nebo více zdrojů dat. Pomocí **Návrhář datových sad** nakonfigurujte datovou sadu a nastavte její vlastnosti. Například musíte určit, které tabulky ze zdroje dat se mají zahrnout, a které sloupce z každé tabulky. Pokud chcete ušetřit množství paměti vyžadované datovou sadou, pečlivě vyberte. Další informace najdete v tématu [Vytvoření a konfigurace datových sad](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Určete vztahy mezi tabulkami, aby se cizí klíče zpracovaly správně. Další informace najdete v tématu [vyplňování datových sad pomocí objekty TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).

- Pomocí **Průvodce konfigurací TableAdapter** určete dotaz nebo uloženou proceduru, která naplní datovou sadu a jaké databázové operace (aktualizovat, odstranit atd.) k implementaci. Další informace najdete v těchto tématech:

  - [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [Úprava dat v datových sadách](../data-tools/edit-data-in-datasets.md)

  - [Ověřit data v datových sadách](../data-tools/validate-data-in-datasets.md)

  - [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)

- Dotazování a hledání dat v datové sadě. Další informace najdete v tématu [dotazování datových sad](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] povoluje [LINQ (jazykově integrovaný dotaz)](/dotnet/csharp/linq/) pro data v <xref:System.Data.DataSet> objektu. Další informace najdete v tématu [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

- Pomocí okna **zdroje dat** navažte ovládací prvky uživatelského rozhraní s datovou sadou nebo jejími jednotlivými sloupci a určete, které sloupce jsou uživatelsky upravitelné. Další informace najdete v tématu [vázání ovládacích prvků k datům v aplikaci Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Datové sady a N-vrstvá architektura

Informace o datových sadách v N-vrstvých aplikacích naleznete v tématu [práce s datovými sadami v n-vrstvých aplikacích](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Datové sady a XML

Informace o převodu datových sad na a z XML naleznete v tématu [Read XML data](../data-tools/read-xml-data-into-a-dataset.md) to a DataSet a [uložte datovou sadu jako XML](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Viz také

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
