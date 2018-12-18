---
title: Přidání ověřování do vícevrstvé datové sady | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a0f7c21dcffb7c17f859d79d3aed5522beb14acf
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220531"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Přidávání ověřování do vícevrstvé datové sady
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Přidání ověřování do datové sady, která je rozdělena na n vrstvého řešení je v podstatě stejné jako přidání ověřování pro jednosouborovou datovou sadu (datová sada v jednom projektu). Navrhované umístění pro ověřování dat je během <xref:System.Data.DataTable.ColumnChanging> a/nebo <xref:System.Data.DataTable.RowChanging> událostí datové tabulky.  
  
 [Vytváření a úpravy typované datové sady](../data-tools/creating-and-editing-typed-datasets.md) poskytuje funkce pro vytvořit dílčí třídy, na které můžete přidat uživatelský kód pro sloupec – a řádek – Změna události tabulek dat v datové sadě. Další informace o přidání kódu k datové sadě v Nvrstvých řešeních viz [přidání kódu do datových sad v n vrstvé aplikace](../data-tools/add-code-to-datasets-in-n-tier-applications.md), a [přidejte kód do prvků TableAdapters ve víceúrovňových aplikacích](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Další informace o dílčích třídách naleznete v tématu [postupy: rozdělení třídy na částečné třídy (návrhář tříd)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) nebo [částečné třídy a metody](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).  
  
> [!NOTE]
>  Když oddělíte datové sady od adaptérů tabulky (nastavením **projektu DataSet** vlastnost), existující částečné třídy v projektu nebudou automaticky přesunuty. Existující částečné třídy datové sady je nutné ručně přesunout do projektu datové sady.  
  
> [!NOTE]
>  Návrhář Dataset nevytváří automaticky obslužné rutiny událostí v jazyce C# pro <xref:System.Data.DataTable.ColumnChanging> a <xref:System.Data.DataTable.RowChanging> události. Budete muset ručně vytvořit obslužnou rutinu události a připojí obslužnou rutinu události do základní události. Následující postupy popisují postup vytvoření obslužné rutiny události požadované v jazyce Visual Basic i C#.  
  
## <a name="validatechanges-to-individual-columns"></a>Validatechanges jednotlivých sloupcích  
 Ověřte hodnoty v jednotlivých sloupcích pomocí manipulace <xref:System.Data.DataTable.ColumnChanging> událostí. <xref:System.Data.DataTable.ColumnChanging> Událost se vyvolá, když se změní hodnota ve sloupci. Vytvořte obslužnou rutinu události pro <xref:System.Data.DataTable.ColumnChanging> události poklepáním na požadovaný sloupec na [vytváření a úpravy typované datové sady](../data-tools/creating-and-editing-typed-datasets.md).  
  
 Poprvé, když poklepete na sloupec, Návrhář vytvoří obslužnou rutinu události pro <xref:System.Data.DataTable.ColumnChanging> událostí. `If…Then` Příkaz je také vytvořen a testuje určitý sloupec. Například následující kód se vygeneruje, když dvakrát kliknete na sloupec RequiredDate v tabulce objednávky Northwind:  
  
```vb  
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging  
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then  
        ' Add validation code here.  
    End If  
End Sub  
```  
  
> [!NOTE]
>  V projektech C# vytvoří Návrhář datových sad pouze částečné třídy pro datovou sadu a jednotlivé tabulky v datové sadě. Návrhář Dataset nevytváří automaticky obslužné rutiny událostí pro <xref:System.Data.DataTable.ColumnChanging> a <xref:System.Data.DataTable.RowChanging> události v jazyce C# jako je tomu v jazyce Visual Basic. V projektech C# budete muset ručně vytvořit metodu ke zpracování události a metody do základní události připojení. Následující postup obsahuje kroky k vytvoření obslužné rutiny události požadované v jazyce Visual Basic i C#.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Přidání ověřování při změnách hodnot jednotlivých sloupců  
  
1.  Otevřete datovou sadu v [vytváření a úpravy typované datové sady](../data-tools/creating-and-editing-typed-datasets.md) dvojitým kliknutím **XSD** ve **Průzkumníka řešení**. Další informace najdete v tématu [postupy: otevření datové sady v návrháři datových sad](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Poklepejte na sloupec, který chcete ověřit. Tato akce vytvoří <xref:System.Data.DataTable.ColumnChanging> obslužné rutiny události.  
  
    > [!NOTE]
    >  Návrhář Dataset nevytváří automaticky obslužnou rutinu události pro událost C#. Kód, který je potřeba ke zpracování událostí v jazyce C# je zahrnuta v další části. `SampleColumnChangingEvent` je vytvořen a pak připojeno <xref:System.Data.DataTable.ColumnChanging> událost v <xref:System.Data.DataTable.EndInit%2A> metody.  
  
3.  Přidejte kód pro ověření, že `e.ProposedValue` obsahuje data, která splňují požadavky aplikace. Pokud navrhovaná hodnota není přijatelná, nastavte sloupec, aby označoval, že obsahuje chybu.  
  
     Následující příklad kódu ověřuje, **množství** sloupec obsahuje více než 0. Pokud **množství** je menší než nebo rovna 0, sloupec je nastaven na chybu. `Else` Klauzule vymaže chybu, pokud **množství** je větší než 0. Kód v obslužné rutině události měnící sloupec by měl vypadat takto:  
  
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
  
## <a name="validatechanges-to-whole-rows"></a>Validatechanges celých řádcích  
 Ověřte hodnoty v celých řádcích pomocí manipulace <xref:System.Data.DataTable.RowChanging> událostí. <xref:System.Data.DataTable.RowChanging> Událost se vyvolá, když jsou potvrzeny hodnoty ve všech sloupcích. Je nutné ověřit v <xref:System.Data.DataTable.RowChanging> událost, když hodnota v jednom sloupci závisí na hodnotě v jiném sloupci. Zvažte například OrderDate a RequiredDate v tabulce objednávky Northwind.  
  
 Při zadání objednávek ověřování zajišťuje, že objednávka není zadána s hodnotu RequiredDate, která je v nebo před OrderDate. V tomto příkladu hodnoty sloupců RequiredDate a OrderDate nutné srovnat, takže ověření změn jednotlivých sloupců nemá smysl.  
  
 Vytvořte obslužnou rutinu události pro <xref:System.Data.DataTable.RowChanging> události poklikáním na název tabulky v záhlaví tabulky na [vytváření a úpravy typované datové sady](../data-tools/creating-and-editing-typed-datasets.md).  
  
#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Přidání ověřování při změnách celých řádků  
  
1.  Otevřete datovou sadu v [vytváření a úpravy typované datové sady](../data-tools/creating-and-editing-typed-datasets.md) dvojitým kliknutím **XSD** ve **Průzkumníka řešení**. Další informace najdete v tématu [postupy: otevření datové sady v návrháři datových sad](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Poklepejte na záhlaví tabulky dat v návrháři.  
  
     Je vytvořena dílčí třída s `RowChanging` obslužná rutina události a otevře v editoru kódu.  
  
    > [!NOTE]
    >  Návrhář Dataset nevytváří automaticky obslužnou rutinu události pro <xref:System.Data.DataTable.RowChanging> události v projektech C#. Je nutné vytvořit metodu ke zpracování <xref:System.Data.DataTable.RowChanging> události a spouštění kódu k připojení události do metody inicializace tabulky.  
  
3.  Přidejte uživatelský kód do částečné deklarace třídy.  
  
4.  Následující kód ukazuje, kam přidat uživatelský kód pro ověření během <xref:System.Data.DataTable.RowChanging> událostí v jazyce Visual Basic:  
  
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
  
5.  Následující kód ukazuje, jak vytvořit `RowChanging` obslužné rutiny události a kam přidat uživatelský kód pro ověření během <xref:System.Data.DataTable.RowChanging> události pro jazyk C#:  
  
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
 [Přehled vícevrstvých datových aplikací](../data-tools/n-tier-data-applications-overview.md)   
 [Návod: Vytvoření vícevrstvé datové aplikace](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Ověřování dat v datových sadách](../data-tools/validate-data-in-datasets.md)

