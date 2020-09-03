---
title: Přidávání kódu do datových sad v n-vrstvých aplikacích | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aed37ee9cdd8c221fcfb114db426a6286ee8ad6f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673117"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Přidávání kódu do datových sad ve vícevrstvých aplikacích
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete roztáhnout funkce datové sady tím, že vytvoříte soubor částečné třídy pro datovou sadu a přidáte do něj kód (místo přidávání kódu do vlastnosti *DataSet*. Soubor DataSet. Designer). Částečné třídy umožňují, aby kód pro konkrétní třídu byl rozdělen mezi několik fyzických souborů. Další informace naleznete v tématu [částečné](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) nebo [částečné třídy a metody](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).

Kód definující datovou sadu je vygenerován pokaždé, když jsou provedeny změny v definici datové sady. Tento kód je také generován, pokud provedete změny během spuštění libovolného průvodce, který upravuje konfiguraci datové sady. Chcete-li zabránit odstranění kódu během obnovování datové sady, přidejte kód do souboru částečné třídy datové sady.

Ve výchozím nastavení platí, že po oddělení datové sady a `TableAdapter` kódu je výsledkem diskrétní soubor třídy v každém projektu. Původní projekt má název *sady*souborů. Designer. vb (nebo *DataSet*. Designer.cs) obsahující `TableAdapter` kód. Projekt, který je určen vlastností **projektu DataSet** , má soubor s názvem *DataSet*. DataSet. Designer. vb (nebo *DataSet*. DataSet.Designer.cs). Tento soubor obsahuje kód datové sady.

> [!NOTE]
> Při oddělení datových sad a `TableAdapter` s (nastavením vlastnosti **projektu DataSet** ) existující částečné třídy datové sady v projektu nebudou automaticky přesunuty. Existující částečné třídy datové sady je nutné přesunout ručně do projektu datové sady.

> [!NOTE]
> Pokud je nutné přidat ověřovací kód, Návrhář DataSet poskytuje funkce pro generování <xref:System.Data.DataTable.ColumnChanging> a <xref:System.Data.DataTable.RowChanging> obslužné rutiny událostí. Další informace najdete v tématu [Přidání ověřování do n-vrstvé datové sady](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="add-code-to-datasets-in-n-tier-applications"></a>Přidávání kódu do datových sad ve vícevrstvých aplikacích

1. Vyhledejte projekt, který obsahuje soubor. XSD (datovou sadu).

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
- [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)
- [TableAdapterManager – přehled](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)
- [Přehled hierarchické aktualizace](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)
- [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)