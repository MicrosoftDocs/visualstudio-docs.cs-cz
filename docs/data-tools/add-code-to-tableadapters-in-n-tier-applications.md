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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e5a9aad4aaecb629f5860fadf56e35a55455be63
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38783087"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Přidávání kódu do objektů TableAdapter ve vícevrstvých aplikacích
Funkcí objektů TableAdapter můžete rozšířit vytvořením souboru částečné třídy pro TableAdapter a přidáním kódu k němu (místo přidání kódu *DatasetName.DataSet.Designer* souboru). Částečné třídy povolit kód pro konkrétní třídu rozdělit mezi několik fyzických souborů. Další informace najdete v tématu [částečné](/dotnet/visual-basic/language-reference/modifiers/partial) nebo [partial (typ)](/dotnet/csharp/language-reference/keywords/partial-type).

Kód, který definuje objektu TableAdapter je generována pokaždé, když dojde ke změně do TableAdapter v datové sadě. Tento kód je generován také při změně v době běhu všechny průvodce, který upraví konfiguraci objektu TableAdapter. Abyste zabránili odstranění při generování objektu TableAdapter kódu, přidejte kód do souboru částečné třídy TableAdapter.

Ve výchozím nastavení po oddělíte datové sady a kód třídy TableAdapter, výsledkem je soubor samostatné třídy v každém projektu. Původní projekt obsahuje soubor s názvem *DatasetName.Designer.vb* (nebo *DatasetName.Designer.cs*), která obsahuje kód objektu TableAdapter. Projekt, který je zadaný ve **projektu Dataset** vlastnost má soubor s názvem *DatasetName.DataSet.Designer.vb* (nebo *DatasetName.DataSet.Designer.cs*), který obsahuje kód datové sady.

> [!NOTE]
>  Když oddělíte datové sady a objekty TableAdapter (nastavením **projektu DataSet** vlastnost), existující částečné třídy v projektu nebudou automaticky přesunuty. Existující částečné třídy je nutné ručně přesunout do projektu datové sady.

> [!NOTE]
> Datová sada poskytuje funkce pro generování <xref:System.Data.DataTable.ColumnChanging> a <xref:System.Data.DataTable.RowChanging> obslužných rutin událostí v případě potřeby ověřování. Další informace najdete v tématu [přidání ověřování do vícevrstvé datové sady](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Chcete-li přidat uživatelský kód do objektu TableAdapter v n vrstvou aplikaci

1.  Najít projekt, který obsahuje *XSD* souboru.

2.  Dvakrát klikněte *XSD* soubor otevřete **Návrhář Dataset**.

3.  Klikněte pravým tlačítkem na TableAdapter, které chcete přidat kód a pak vyberte **zobrazit kód**.

     Částečné třídy se vytvoří a otevře v editoru kódu.

4.  Přidejte kód do částečné deklarace třídy.

5.  Následující příklad ukazuje, kde přidat kód pro `CustomersTableAdapter` v `NorthwindDataSet`:

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

- [Přehled vícevrstvých datových aplikací](../data-tools/n-tier-data-applications-overview.md)
- [Přidávání kódu do datových sad ve vícevrstvých aplikacích](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Vytvoření a konfigurace objektů TableAdapter](create-and-configure-tableadapters.md)
- [Přehled hierarchické aktualizace](hierarchical-update.md)
