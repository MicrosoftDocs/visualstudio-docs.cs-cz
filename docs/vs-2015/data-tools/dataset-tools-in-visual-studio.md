---
title: Nástroje datové sady
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 53
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23e4deba53288383a569f6da6e14d27f723825ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657387"
---
# <a name="dataset-tools-in-visual-studio"></a>Nástroje datových sad v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ZNAČTE
> Datové sady a související třídy jsou starší technologie .NET od začátku 2000s, které aplikacím umožňují pracovat s daty v paměti v době, kdy jsou aplikace odpojeny od databáze. Jsou zvláště užitečné pro aplikace, které umožňují uživatelům upravovat data a uchovávat změny zpátky v databázi. I když se datové sady ukázaly jako velmi úspěšná technologie, doporučujeme, aby nové aplikace .NET používaly Entity Framework. Entity Framework poskytuje přirozenější způsob, jak pracovat s tabulkovými daty jako objektovými modely a má jednodušší programovací rozhraní.

 Objekt DataSet je objekt v paměti, který je v podstatě zkrácenou databází. Obsahuje objekty DataTable, DataColumn a DataRow, ve kterých můžete ukládat a upravovat data z jedné nebo více databází, aniž byste museli udržovat otevřené připojení. Datová sada uchovává informace o změnách dat, takže aktualizace je možné sledovat a odeslat zpět do databáze, když se vaše aplikace znovu připojí.

 Datové sady a související třídy jsou definovány v oboru názvů System. data v knihovně tříd .NET Framework. Datové sady můžete vytvářet a upravovat dynamicky v kódu. Další informace o tom, jak to provést, najdete v tématu ADO.NET. Dokumentace v této části ukazuje, jak pracovat s datovými sadami pomocí návrhářů sady Visual Studio. Jedna věc k známce: datové sady, které se provedou prostřednictvím návrháře, používají objekty TableAdapter k interakci s databází, zatímco datové sady, které se provedou programově, používají objekty DataAdapter. Informace o tom, jak vytvořit datové sady prostřednictvím kódu programu, najdete v tématu datové [adaptéry a Datačtecí](https://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74)nástroje.

 Pokud vaše aplikace potřebuje číst data z databáze a neprovádí aktualizace, přidává nebo odstraňuje, můžete obvykle dosáhnout lepšího výkonu pomocí objektu DataReader k načtení dat do objektu obecného seznamu nebo do jiného objektu kolekce. Pokud zobrazujete data, můžete datové vazby navazovat do kolekce.

## <a name="dataset-workflow"></a>Pracovní postup datové sady
 Sada Visual Studio poskytuje mnoho nástrojů pro zjednodušení práce s datovými sadami. Základní kompletní pracovní postup:

- V okně **zdroje dat** můžete vytvořit novou datovou sadu z jednoho nebo více zdrojů dat. Pomocí **Návrhář datových sad** nakonfigurujte datovou sadu a nastavte její vlastnosti. Například musíte určit, které tabulky ze zdroje dat se mají zahrnout, a které sloupce z každé tabulky. Pokud chcete ušetřit množství paměti, které bude datová sada vyžadovat, pečlivě vyberte. Další informace najdete v tématu [Vytvoření a konfigurace datových sad](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Určete vztahy mezi tabulkami, aby se cizí klíče zpracovaly správně. Další informace najdete v tématu [vyplňování datových sad pomocí objekty TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).

- Pomocí **Průvodce konfigurací TableAdapter** určete dotaz nebo uloženou proceduru, která naplní datovou sadu a které operace databáze (aktualizovat, odstranit atd.), které se mají implementovat. Další informace najdete v těchto tématech:

  - [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [Úprava dat v datových sadách](../data-tools/edit-data-in-datasets.md)

  - [Ověřování dat v datových sadách](../data-tools/validate-data-in-datasets.md)

  - [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)

- Dotazování a hledání dat v datové sadě. Další informace najdete v tématu [dotazování datových sad](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] povolí [LINQ (jazykově integrovaný dotaz)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) pro data v objektu <xref:System.Data.DataSet>. Další informace najdete v tématu [LINQ to DataSet](https://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).

- Pomocí okna **zdroje dat** navažte ovládací prvky uživatelského rozhraní s datovou sadou nebo jejími jednotlivými sloupci a určete, které sloupce jsou uživatelsky upravitelné. Další informace najdete v tématu [vázání ovládacích prvků k datům v aplikaci Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Datové sady a N-vrstvá architektura
 Informace o datových sadách v N-vrstvých aplikacích naleznete v tématu [práce s datovými sadami v n-vrstvých aplikacích](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Datové sady a XML
 Informace o převodu datových sad na a z XML naleznete v tématu [Read XML data](../data-tools/read-xml-data-into-a-dataset.md) to a DataSet a [uložte datovou sadu jako XML](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Viz také
 [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
