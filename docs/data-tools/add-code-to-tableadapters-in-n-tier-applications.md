---
title: Přidávání kódu do objektů TableAdapter ve vícevrstvých aplikacích
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e5d240726030a3a08d184b3015f56f65d9168e9f
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113328"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Přidávání kódu do objektů TableAdapter ve vícevrstvých aplikacích
Funkci TableAdapter můžete roztáhnout tak, že vytvoříte soubor částečné třídy pro TableAdapter a přidáte do něj kód (místo přidávání kódu do souboru *DataSet. DataSet. Designer* ). Částečné třídy umožňují, aby kód pro konkrétní třídu byl rozdělen mezi několik fyzických souborů. Další informace naleznete v tématu [částečný](/dotnet/visual-basic/language-reference/modifiers/partial) nebo [částečný (typ)](/dotnet/csharp/language-reference/keywords/partial-type).

Kód, který definuje TableAdapter, je vygenerován pokaždé, když jsou provedeny změny TableAdapter v datové sadě. Tento kód je vygenerován také v případě, že se změny provedou při spuštění libovolného průvodce, který upraví konfiguraci TableAdapter. Chcete-li zabránit odstranění kódu během obnovování TableAdapter, přidejte kód do souboru dílčí třídy TableAdapter.

Ve výchozím nastavení platí, že po oddělení datové sady a kódu TableAdapter je výsledkem diskrétní soubor třídy v každém projektu. Původní projekt obsahuje soubor s názvem *DataSet. Designer. vb* (nebo *DatasetName.Designer.cs*), který obsahuje kód TableAdapter. Projekt, který je určen vlastností **projektu DataSet** , má soubor pojmenovaný *DataSet. DataSet. Designer. vb* (nebo *DatasetName.DataSet.Designer.cs*), který obsahuje kód datové sady.

> [!NOTE]
> Při oddělení datových sad a objekty TableAdapter (nastavením vlastnosti **projektu DataSet** ) existující částečné třídy datové sady v projektu nebudou automaticky přesunuty. Existující třídy částečné datové sady je nutné přesunout ručně do projektu datové sady.

> [!NOTE]
> Datová sada poskytuje funkce pro generování <xref:System.Data.DataTable.ColumnChanging> a <xref:System.Data.DataTable.RowChanging> obslužných rutin událostí, pokud je vyžadováno ověření. Další informace najdete v tématu [Přidání ověřování do n-vrstvé datové sady](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Přidání uživatelského kódu do TableAdapter v n-vrstvé aplikaci

1. Vyhledejte projekt, který obsahuje soubor *. xsd* .

2. Dvojím kliknutím na soubor *. xsd* otevřete **Návrhář datových sad**.

3. Klikněte pravým tlačítkem na TableAdapter, do kterého chcete přidat kód, a pak vyberte **Zobrazit kód**.

     Je vytvořena částečná třída, která se otevře v editoru kódu.

4. Přidejte kód do deklarace částečné třídy.

5. Následující příklad ukazuje, kde přidat kód do `CustomersTableAdapter` v `NorthwindDataSet`:

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>Viz také:

- [Přehled N-vrstvých datových aplikací](../data-tools/n-tier-data-applications-overview.md)
- [Přidávání kódu do datových sad ve vícevrstvých aplikacích](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Vytvoření a konfigurace objektů TableAdapter](create-and-configure-tableadapters.md)
- [Přehled hierarchické aktualizace](hierarchical-update.md)
