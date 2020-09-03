---
title: Přidání ověřování do n-vrstvé datové sady | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b03f1e85140d62d84ae7c706a9bfee6a7c515abb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673045"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Přidávání ověřování do vícevrstvé datové sady
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Přidání ověřování do datové sady, která je rozdělena do n-vrstvého řešení, je v podstatě totéž jako přidání ověřování do datové sady s jedním souborem (datová sada v jednom projektu). Navrhované umístění pro ověřování dat je v <xref:System.Data.DataTable.ColumnChanging> událostech a/nebo v <xref:System.Data.DataTable.RowChanging> tabulce dat.

Návrhář DataSet poskytuje funkce pro vytváření dílčích tříd, do kterých lze přidat uživatelský kód do událostí, které mění sloupce a řádky tabulek dat v datové sadě. Další informace o přidávání kódu do datové sady v n-vrstvém řešení naleznete v tématu [Přidání kódu do datových sad v n-vrstvých aplikacích](../data-tools/add-code-to-datasets-in-n-tier-applications.md)a [Přidání kódu do objekty TableAdapter v n-vrstvých aplikacích](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Další informace o dílčích třídách naleznete v tématu [How to: rozdělit třídu na částečné třídy (návrhář tříd)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) nebo [částečné třídy a metody](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).

> [!NOTE]
> Při oddělení datových sad z objekty TableAdapter (nastavením vlastnosti **projektu DataSet** ) existující částečné třídy datové sady v projektu nebudou automaticky přesunuty. Existující částečné třídy datové sady je nutné přesunout ručně do projektu datové sady.

> [!NOTE]
> Návrhář datových sad nevytváří automaticky obslužné rutiny událostí v jazyce C# pro <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> události a. Je nutné ručně vytvořit obslužnou rutinu události a připojit obslužnou rutinu události ke zdrojové události. Následující postupy popisují, jak vytvořit požadované obslužné rutiny událostí v Visual Basic i C#.

## <a name="validatechanges-to-individual-columns"></a>Validatechanges na jednotlivé sloupce
 Ověří hodnoty v jednotlivých sloupcích tím, že se <xref:System.Data.DataTable.ColumnChanging> událost zpracuje. <xref:System.Data.DataTable.ColumnChanging>Událost se vyvolá, když se upraví hodnota ve sloupci. Vytvořte obslužnou rutinu události pro <xref:System.Data.DataTable.ColumnChanging> událost dvojitým kliknutím na požadovaný sloupec v datové sadě.

 Když poprvé dvakrát kliknete na sloupec, Návrhář vygeneruje obslužnou rutinu události pro <xref:System.Data.DataTable.ColumnChanging> událost. `If…Then`Vytvoří se také příkaz, který provede testy pro konkrétní sloupec. Například následující kód se vygeneruje, když dvakrát kliknete na sloupec DodatDne v tabulce objednávky Northwind:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> V projektech C# Návrhář datových sad vytvoří pouze částečné třídy pro datovou sadu a jednotlivé tabulky v datové sadě. Návrhář datových sad nevytváří automaticky obslužné rutiny událostí pro <xref:System.Data.DataTable.ColumnChanging> události a <xref:System.Data.DataTable.RowChanging> v jazyce C#, jako by to bylo v Visual Basic. V projektech C# je nutné ručně vytvořit metodu pro zpracování události a připojit metodu k základní události. Následující postup popisuje kroky pro vytvoření požadovaných obslužných rutin událostí v Visual Basic i C#.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Přidání ověřování během změn jednotlivých hodnot sloupců

1. Otevřete datovou sadu v Návrháři dvojitým kliknutím na soubor **XSD** v **Průzkumník řešení**. Další informace najdete v tématu [Postup: otevření datové sady v Návrhář datových sad](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Dvakrát klikněte na sloupec, který chcete ověřit. Tato akce vytvoří <xref:System.Data.DataTable.ColumnChanging> obslužnou rutinu události.

    > [!NOTE]
    > Návrhář datových sad nevytvoří automaticky obslužnou rutinu události pro událost jazyka C#. Kód, který je nezbytný pro zpracování události v jazyce C#, je součástí další části. `SampleColumnChangingEvent` se vytvoří a potom se připojí k <xref:System.Data.DataTable.ColumnChanging> události v <xref:System.Data.DataTable.EndInit%2A> metodě.

3. Přidejte kód pro ověření, zda `e.ProposedValue` obsahuje data, která splňují požadavky vaší aplikace. Pokud navrhovaná hodnota není přijatelná, nastavte sloupec tak, aby označoval, že obsahuje chybu.

     Následující příklad kódu ověřuje, zda sloupec **množství** obsahuje více než 0. Pokud je **množství** menší nebo rovno 0, je sloupec nastaven na chybu. `Else`Klauzule vymaže chybu, pokud je **množství** větší než 0. Kód v obslužné rutině události měnící sloupce by měl vypadat takto:

    ```vb
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then
        If CType(e.ProposedValue, Short) <= 0 Then
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")
        Else
            e.Row.SetColumnError(e.Column, "")
        End If
    End If
    ```

    ```csharp
    // C#
    // Add this code to the DataTable
    // partial class.

        public override void EndInit()
        {
            base.EndInit();
            // Hook up the ColumnChanging event
            // to call the SampleColumnChangingEvent method.
            ColumnChanging += SampleColumnChangingEvent;
        }

        public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)
        {
            if (e.Column.ColumnName == QuantityColumn.ColumnName)
            {
                if ((short)e.ProposedValue <= 0)
                {
                    e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
                }
                else
                {
                    e.Row.SetColumnError("Quantity", "");
                }
            }
        }
    ```

## <a name="validatechanges-to-whole-rows"></a>Validatechanges na celé řádky
 Ověří hodnoty v celých řádcích zpracováním <xref:System.Data.DataTable.RowChanging> události. <xref:System.Data.DataTable.RowChanging>Událost se vyvolá, když jsou hodnoty ve všech sloupcích potvrzeny. V případě, že je <xref:System.Data.DataTable.RowChanging> hodnota v jednom sloupci závislá na hodnotě v jiném sloupci, je nutné ověřit v události. V tabulce Orders v databázi Northwind můžete například zvážit DatumObjednávky a DodatDne.

 Při zadávání objednávek ověří ověření, že objednávka není zadána se DodatDne, která je na nebo před DatumObjednávky. V tomto příkladu je třeba porovnat hodnoty pro sloupce DodatDne a DatumObjednávky, takže ověření jednotlivých změn v jednotlivých sloupcích nesmyslí.

 Vytvořte obslužnou rutinu události pro <xref:System.Data.DataTable.RowChanging> událost dvojitým kliknutím na název tabulky v záhlaví tabulky.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Přidání ověřování během změn na celé řádky

1. Otevřete datovou sadu v Návrháři dvojitým kliknutím na soubor **XSD** v **Průzkumník řešení**. Další informace najdete v tématu [Postup: otevření datové sady v Návrhář datových sad](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Dvakrát klikněte na záhlaví tabulky dat v návrháři.

     Je vytvořena částečná třída s `RowChanging` obslužnou rutinou události a otevře se v editoru kódu.

    > [!NOTE]
    > Návrhář datových sad nevytváří automaticky obslužnou rutinu události pro <xref:System.Data.DataTable.RowChanging> událost v projektech C#. Je nutné vytvořit metodu pro zpracování <xref:System.Data.DataTable.RowChanging> události a spuštění kódu pro připojení události do inicializační metody tabulky.

3. Přidejte uživatelský kód uvnitř deklarace částečné třídy.

4. Následující kód ukazuje, kde přidat uživatelský kód pro ověření během <xref:System.Data.DataTable.RowChanging> události pro Visual Basic:

    ```vb
    Partial Class OrdersDataTable
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging
            ' Add logic to validate columns here.
            If e.Row.RequiredDate <= e.Row.OrderDate Then
                ' Set the RowError if validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"
            Else
                ' Clear the RowError when validation passes.
                e.Row.RowError = ""
            End If
        End Sub
    End Class
    ```

5. Následující kód ukazuje, jak vytvořit `RowChanging` obslužnou rutinu události a kde přidat uživatelský kód pro ověření během <xref:System.Data.DataTable.RowChanging> události pro jazyk C#:

    ```csharp
    partial class OrdersDataTable
    {
        public override void EndInit()
        {
            base.EndInit();
            // Hook up the event to the
            // RowChangingEvent method.
            OrdersRowChanging += RowChangingEvent;
        }

        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)
        {
            // Perform the validation logic.
            if (e.Row.RequiredDate <= e.Row.OrderDate)
            {
                // Set the row to an error when validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";
            }
            else
            {
                // Clear the RowError if validation passes.
                e.Row.RowError = "";
            }
        }
    }
    ```

## <a name="see-also"></a>Viz také
 [Přehled vícevrstvých datových aplikací](../data-tools/n-tier-data-applications-overview.md) [: vytváření n-vrstvých datových aplikací](../data-tools/walkthrough-creating-an-n-tier-data-application.md) [ověření dat v datových sadách](../data-tools/validate-data-in-datasets.md)
