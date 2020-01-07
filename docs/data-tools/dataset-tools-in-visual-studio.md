---
title: Nástroje datové sady
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cb41a4e3e4ed1c0032c579779a18c7df0bc22477
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586715"
---
# <a name="dataset-tools-in-visual-studio"></a>Nástroje datových sad v sadě Visual Studio

> [!NOTE]
> Datové sady a související třídy jsou starší verze technologie .NET v rané fázi 2000s, která umožňují aplikacím pro práci s daty v paměti z databáze se odpojené aplikace. Jsou zvláště užitečné pro aplikace, které umožňují uživatelům upravovat data a zachová tak změny zpět do databáze. I když datové sady ukázaly jako velmi úspěšná technologie, doporučujeme použít rozhraní Entity Framework nové aplikace .NET. Entity Framework poskytuje přirozenější způsob, jak fungují s tabulkovými daty jako objektové modely a je jednodušší programovací rozhraní.

Objekt `DataSet` je objekt v paměti, který je v podstatě zkrácenou databází. Obsahuje `DataTable`, `DataColumn`a `DataRow` objekty, ve kterých můžete ukládat a upravovat data z jedné nebo více databází, aniž byste museli udržovat otevřené připojení. Datovou sadu uchovává informace o změny dat, takže aktualizace můžete sledovat a odesílá zpět do databáze, když vaše aplikace bude znovu připojeny.

Datové sady a související třídy jsou definovány v oboru názvů <xref:System.Data?displayProperty=fullName> v rozhraní .NET API. Datové sady můžete vytvářet a upravovat dynamicky v kódu pomocí ADO.NET. Dokumentace v této části ukazuje, jak pracovat s datovými sadami pomocí návrháře sady Visual Studio. Datové sady, které jsou vytvořené prostřednictvím návrháře, používají objekty **TableAdapter** k interakci s databází. Datové sady, které jsou vytvořeny programově, používají objekty **DataAdapter** . Informace o vytváření datových sad prostřednictvím kódu programu najdete v tématu [adaptéry a čtečky dat](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

Pokud vaše aplikace potřebuje číst data z databáze a neprovádí aktualizace, přidává nebo odstraňuje, můžete obvykle dosáhnout lepšího výkonu pomocí objektu `DataReader` k načtení dat do obecného objektu `List` nebo jiného objektu kolekce. Pokud je zobrazení dat, je můžete vytvořte datovou vazbu uživatelského rozhraní do kolekce.

## <a name="dataset-workflow"></a>Pracovní postup datové sady

Sada Visual Studio poskytuje nástroje pro zjednodušení práce s datovými sadami. Je základní pracovní postup začátku do konce:

- Použijte [okno zdroje dat](add-new-data-sources.md#data-sources-window) k vytvoření nové datové sady z jednoho nebo více zdrojů dat. Použití **Návrhář Dataset** konfigurace datové sady a nastavte jeho vlastnosti. Například musíte zadat tabulky ze zdroje dat chcete zahrnout a které sloupce z každé tabulky. Pokud chcete ušetřit množství paměti vyžadované datovou sadou, pečlivě vyberte. Další informace najdete v tématu [vytvoření a konfigurace datové sady](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Zadejte relace mezi tabulkami, tak, že jsou správně zpracovány cizí klíče. Další informace najdete v tématu [vyplnění datové sady s použitím objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).

- Pomocí **Průvodce konfigurací TableAdapter** určete dotaz nebo uloženou proceduru, která naplní datovou sadu a jaké databázové operace (aktualizovat, odstranit atd.) k implementaci. Další informace najdete v těchto tématech:

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
