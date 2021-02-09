---
title: Přidávání kódu do datových sad ve vícevrstvých aplikacích
description: Přidejte kód do datových sad v n-vrstvých aplikacích v sadě Visual Studio. Vytvořte soubor částečné třídy pro datovou sadu a přidejte do něj kód (místo do sady DataSet. DataSet. Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending DataSets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c1a6e424fe76b94321ca79ab08496cd160969890
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867526"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Přidávání kódu do datových sad ve vícevrstvých aplikacích

Můžete roztáhnout funkce datové sady tím, že vytvoříte soubor částečné třídy pro datovou sadu a přidáte do něj kód (místo přidávání kódu do vlastnosti *DataSet*. Soubor DataSet. Designer). Částečné třídy umožňují, aby kód pro konkrétní třídu byl rozdělen mezi několik fyzických souborů. Další informace naleznete v tématu [částečné](/dotnet/visual-basic/language-reference/modifiers/partial) nebo [částečné třídy a metody](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

Kód, který definuje datovou sadu, je vygenerován pokaždé, když se změní definice datové sady (v typované datové sadě). Tento kód je také generován, pokud provedete změny během spuštění libovolného průvodce, který upravuje konfiguraci datové sady. Chcete-li zabránit odstranění kódu během obnovování datové sady, přidejte kód do souboru částečné třídy datové sady.

Ve výchozím nastavení platí, že po oddělení datové sady a kódu TableAdapter je výsledkem diskrétní soubor třídy v každém projektu. Původní projekt obsahuje soubor s názvem *DataSet. Designer. vb* (nebo *DatasetName.Designer.cs*), který obsahuje kód TableAdapter. Projekt, který je určen vlastností **projektu DataSet** , má soubor s názvem *DataSet. DataSet. Designer. vb* (nebo *DatasetName.DataSet.Designer.cs*). Tento soubor obsahuje kód datové sady.

> [!NOTE]
> Při oddělení datových sad a objekty TableAdapter (nastavením vlastnosti **projektu DataSet** ) existující částečné třídy datové sady v projektu nebudou automaticky přesunuty. Existující částečné třídy datové sady je nutné přesunout ručně do projektu datové sady.

> [!NOTE]
> Pokud je nutné přidat ověřovací kód, typová datová sada poskytuje funkce pro generování <xref:System.Data.DataTable.ColumnChanging> a <xref:System.Data.DataTable.RowChanging> obslužné rutiny událostí. Další informace najdete v tématu [Přidání ověřování do n-vrstvé datové sady](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Přidání kódu do datových sad v n-vrstvých aplikacích

1. Vyhledejte projekt, který obsahuje soubor *. xsd* .

2. Vyberte soubor **. xsd** a otevřete datovou sadu.

3. Klikněte pravým tlačítkem na tabulku dat, do které chcete přidat kód (název tabulky v záhlaví), a pak vyberte **Zobrazit kód**.

     Je vytvořena částečná třída, která se otevře v editoru kódu.

4. Přidejte kód do deklarace částečné třídy.

     Následující příklad ukazuje, kde přidat kód do CustomersDataTable v NorthwindDataSet:

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```

    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>Viz také

- [Přehled N-vrstvých datových aplikací](../data-tools/n-tier-data-applications-overview.md)
- [Přidávání kódu do objektů TableAdapter ve vícevrstvých aplikacích](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Vytvoření a konfigurace objektů TableAdapter](create-and-configure-tableadapters.md)
- [Přehled hierarchické aktualizace](hierarchical-update.md)
- [Nástroje datové sady v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
