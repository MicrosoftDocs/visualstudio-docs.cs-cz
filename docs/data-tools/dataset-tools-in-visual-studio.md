---
title: Nástroje datové sady
ms.date: 11/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- data-storage
ms.openlocfilehash: 3a8a1ac0f2ac4e4b147fbe11dba8d88ccea4c255
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304984"
---
# <a name="dataset-tools-in-visual-studio"></a>Nástroje datové sady v sadě Visual Studio

> [!NOTE]
> Datové sady a související třídy jsou starší verze technologie .NET v rané fázi 2000s, která umožňují aplikacím pro práci s daty v paměti z databáze se odpojené aplikace. Jsou zvláště užitečné pro aplikace, které umožňují uživatelům upravovat data a zachová tak změny zpět do databáze. I když datové sady ukázaly jako velmi úspěšná technologie, doporučujeme použít rozhraní Entity Framework nové aplikace .NET. Entity Framework poskytuje přirozenější způsob, jak fungují s tabulkovými daty jako objektové modely a je jednodušší programovací rozhraní.

A `DataSet` objekt je objekt v paměti, která je v podstatě zkrácené databáze. Obsahuje `DataTable`, `DataColumn`, a `DataRow` objekty, ve kterých můžete ukládat a upravit data z jedné nebo víc databází, aniž byste museli udržovat otevřené připojení. Datovou sadu uchovává informace o změny dat, takže aktualizace můžete sledovat a odesílá zpět do databáze, když vaše aplikace bude znovu připojeny.

Datové sady a související třídy jsou definovány v <xref:System.Data?displayProperty=fullName> oboru názvů v knihovně tříd rozhraní .NET Framework. Můžete vytvářet a upravovat datové sady dynamicky v kódu pomocí technologie ADO.NET. Dokumentace v této části ukazuje, jak pracovat s datovými sadami pomocí návrháře sady Visual Studio. Datové sady, které jsou vytvořeny pomocí návrhářů **TableAdapter** objekty k interakci s databází. Použití datových sad, které jsou vytvořené prostřednictvím kódu programu **DataAdapter** objekty. Informace o vytváření datových sad prostřednictvím kódu programu najdete v tématu [adaptéry a čtečky dat](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

Pokud vaše aplikace je potřeba jenom číst data z databáze a nebude provádět aktualizace, přidá nebo odstraní, obvykle můžete získat lepší výkon pomocí `DataReader` objektu k načtení dat do obecného `List` nebo jiný objekt kolekce. Pokud je zobrazení dat, je můžete vytvořte datovou vazbu uživatelského rozhraní do kolekce.

## <a name="dataset-workflow"></a>Pracovní postup datové sady

Visual Studio poskytuje nástroje ke zjednodušení práce s datovými sadami. Je základní pracovní postup začátku do konce:

- Použití [okna zdroje dat](add-new-data-sources.md#data-sources-window) k vytvoření nové datové sady z jednoho nebo více zdrojů dat. Použití **Návrhář Dataset** konfigurace datové sady a nastavte jeho vlastnosti. Například musíte zadat tabulky ze zdroje dat chcete zahrnout a které sloupce z každé tabulky. Pečlivě kvůli úspoře množství paměti, které se vyžaduje datové sady. Další informace najdete v tématu [vytvoření a konfigurace datové sady](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Zadejte relace mezi tabulkami, tak, že jsou správně zpracovány cizí klíče. Další informace najdete v tématu [vyplnění datové sady s použitím objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).

- Použití **Průvodce nastavením TableAdapter** k určení dotazu nebo uložené procedury, které naplňuje datovou sadu a jaké operace databáze (update, delete a podobně) k implementaci. Další informace najdete v těchto tématech:

    - [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)

    - [Úprava dat v datových sadách](../data-tools/edit-data-in-datasets.md)

    - [Ověřování dat v datových sadách](../data-tools/validate-data-in-datasets.md)

    - [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)

- Dotazování a hledání dat v datové sadě. Další informace najdete v tématu [dotazování datových sad](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] umožňuje [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) nad daty v <xref:System.Data.DataSet> objektu. Další informace najdete v tématu [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

- Použití **zdroje dat** okno pro vytvoření vazby ovládacích prvků uživatelského rozhraní datové sady nebo jeho jednotlivé sloupce a chcete-li určit sloupce, které se uživatel upravovat. Další informace najdete v tématu [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Datové sady a N-vrstvou architekturu

Informace o datových sad v N-vrstvé aplikace najdete v tématu [práce s datovými sadami ve vícevrstvých aplikacích](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Datové sady a XML

Informace o převodu datových sad do a ze souboru XML, naleznete v tématu [XML pro čtení dat do datové sady](../data-tools/read-xml-data-into-a-dataset.md) a [uložení datové sady ve formátu XML](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Viz také:

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)