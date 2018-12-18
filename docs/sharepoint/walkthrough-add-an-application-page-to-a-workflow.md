---
title: 'Návod: Přidání stránky aplikace do pracovního postupu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4bdb01e5cbb45b9986e61a99e18b5984e92d37dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866893"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>Návod: Přidání stránky aplikace do pracovního postupu
  Tento návod ukazuje, jak přidat stránku aplikace, která zobrazuje data odvozená z pracovního postupu do projektu pracovního postupu. Je nástavbou projektu je popsáno v tématu [návod: vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

 Tento návod demonstruje následující úkoly:

- Přidání stránky ASPX aplikace do projektu pracovního postupu služby SharePoint.

- Získání dat z projektu pracovního postupu a manipulaci.

- Zobrazení dat v tabulce na stránce aplikace.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

-   Podporované edice systému [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] a SharePoint.

-   Visual Studio.

-   Máte také dokončení projektu v tématu [návod: vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

## <a name="ammend-the-workflow-code"></a>Ammend kód pracovního postupu
 Nejprve přidejte řádek kódu do pracovního postupu k nastavení hodnoty ve sloupci výsledek množství vyúčtování. Tato hodnota se používá později při výpočtu souhrnné sestavy výdajů.

#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>Chcete-li nastavit hodnotu sloupce výsledku v pracovním postupu

1.  Načíst dokončený projekt z tématu [návod: vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2.  Spustit kód pro *Workflow1.cs* nebo *Workflow1.vb* (v závislosti na programovacím jazyce).

3.  K dolnímu okraji `createTask1_MethodInvoking` metodu, přidejte následující kód:

    ```vb
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =
      workflowProperties.InitiationData
    ```

    ```csharp
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =
      workflowProperties.InitiationData;
    ```

## <a name="create-an-application-page"></a>Vytvoření stránky aplikace
 V dalším kroku přidejte formulář ASPX do projektu. Tento formulář zobrazí data z projektu pracovního postupu sestavy výdajů. K tomuto účelu se přidání stránky aplikace. Stránky aplikace používá stejnou stránku předlohy jako další stránky služby SharePoint, což znamená, že bude vypadat podobně jako jiné stránky na webu služby SharePoint.

#### <a name="to-add-an-application-page-to-the-project"></a>Přidání stránky aplikace do projektu

1.  Zvolte projekt ExpenseReport a pak na panelu nabídek zvolte **projektu** > **přidat novou položku**.

2.  V **šablony** podokně, vyberte **stránky aplikace** šablony, použití výchozího názvu pro položku projektu (**ApplicationPage1.aspx**) a zvolte **Přidat** tlačítko.

3.  V [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ApplicationPage1.aspx, nahraďte `PlaceHolderMain` oddíl následujícím kódem:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
        <asp:Label ID="Label1" runat="server" Font-Bold="True"
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>
        <br />
        <asp:Table ID="Table1" runat="server">
        </asp:Table>
    </asp:Content>
    ```

     Tento kód přidá na stránku spolu s název tabulky.

4.  Přidat nadpis na stránce aplikace tak, že nahradíte `PlaceHolderPageTitleInTitleArea` oddíl následujícím kódem:

    ```aspx-csharp
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >
        Expense Report Summary
    </asp:Content>
    ```

## <a name="code-the-application-page"></a>Znaková stránka aplikace
 Dále přidejte kód, na stránce souhrnu aplikací sestavy výdajů. Při otevření stránky kontroluje kód v seznamu úloh ve službě SharePoint výdaje, který překročil přidělenou limit útraty. Tato sestava uvádí jednotlivé položky spolu s součet výdaje.

#### <a name="to-code-the-application-page"></a>Do kódu stránky aplikace

1.  Zvolte **ApplicationPage1.aspx** uzel a potom na panelu nabídek zvolte **zobrazení** > **kód** k zobrazení kódu stránky aplikace.

2.  Nahradit **pomocí** nebo **Import** příkazy (v závislosti na programovacím jazyce) v horní části třídy následujícím kódem:

    ```vb
    Imports System
    Imports Microsoft.SharePoint
    Imports Microsoft.SharePoint.WebControls
    Imports System.Collections
    Imports System.Data
    Imports System.Web.UI
    Imports System.Web.UI.WebControls
    Imports System.Web.UI.WebControls.WebParts
    Imports System.Drawing
    Imports Microsoft.SharePoint.Navigation
    ```

    ```csharp
    using System;
    using Microsoft.SharePoint;
    using Microsoft.SharePoint.WebControls;
    using System.Collections;
    using System.Data;
    using System.Web.UI;
    using System.Web.UI.WebControls;
    using System.Web.UI.WebControls.WebParts;
    using System.Drawing;
    using Microsoft.SharePoint.Navigation;
    ```

3.  Přidejte následující kód, který `Page_Load` metody:

    ```vb
    Try
        ' Reference the Tasks list on the SharePoint site.
        ' Replace "TestServer" with a valid SharePoint server name.
        Dim site As SPSite = New SPSite("http://TestServer")
        Dim list As SPList = site.AllWebs(0).Lists("Tasks")
        ' string text = "";
        Dim sum As Integer = 0
        Table1.Rows.Clear()
        ' Add table headers.
        Dim hr As TableHeaderRow = New TableHeaderRow
        hr.BackColor = Color.LightBlue
        Dim hc1 As TableHeaderCell = New TableHeaderCell
        Dim hc2 As TableHeaderCell = New TableHeaderCell
        hc1.Text = "Expense Report Name"
        hc2.Text = "Amount Exceeded"
        hr.Cells.Add(hc1)
        hr.Cells.Add(hc2)
        ' Add the TableHeaderRow as the first item
        ' in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr)
        ' Iterate through the tasks in the Task list and collect those
        ' that have values in the "Related Content" and "Outcome" fields
        ' - the fields written to when expense approval is required.
        For Each item As SPListItem In list.Items
            Dim s_relContent As String = ""
            Dim s_outcome As String = ""
            Try
                ' Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related Content")
                s_outcome = item.GetFormattedValue("Outcome")
            Catch erx As System.Exception
                ' Task does not have fields - skip it.
                Continue For
            End Try
            ' Convert amount to an int and keep a running total.
            If (Not String.IsNullOrEmpty(s_relContent) And Not
              String.IsNullOrEmpty(s_outcome)) Then
                sum = (sum + Convert.ToInt32(s_outcome))
                Dim relContent As TableCell = New TableCell
                relContent.Text = s_relContent
                Dim outcome As TableCell = New TableCell
                outcome.Text = ("$" + s_outcome)
                Dim dataRow2 As TableRow = New TableRow
                dataRow2.Cells.Add(relContent)
                dataRow2.Cells.Add(outcome)
                Table1.Rows.Add(dataRow2)
            End If
        Next
        ' Report the sum of the reports in the table footer.
        Dim tfr As TableFooterRow = New TableFooterRow
        tfr.BackColor = Color.LightGreen
        ' Create a TableCell object to contain the
        ' text for the footer.
        Dim ftc1 As TableCell = New TableCell
        Dim ftc2 As TableCell = New TableCell
        ftc1.Text = "TOTAL: "
        ftc2.Text = ("$" + Convert.ToString(sum))
        ' Add the TableCell object to the Cells
        ' collection of the TableFooterRow.
        tfr.Cells.Add(ftc1)
        tfr.Cells.Add(ftc2)
        ' Add the TableFooterRow to the Rows
        ' collection of the table.
        Table1.Rows.Add(tfr)
    Catch errx As Exception
        System.Diagnostics.Debug.WriteLine(("Error: " + errx.ToString))
    End Try
    ```

    ```csharp
    try
    {
        // Reference the Tasks list on the SharePoint site.
        // Replace "TestServer" with a valid SharePoint server name.
        SPSite site = new SPSite("http://TestServer");
        SPList list = site.AllWebs[0].Lists["Tasks"];

        // string text = "";
        int sum = 0;

        Table1.Rows.Clear();

        // Add table headers.
        TableHeaderRow hr = new TableHeaderRow();
        hr.BackColor = Color.LightBlue;
        TableHeaderCell hc1 = new TableHeaderCell();
        TableHeaderCell hc2 = new TableHeaderCell();
        hc1.Text = "Expense Report Name";
        hc2.Text = "Amount Exceeded";
        hr.Cells.Add(hc1);
        hr.Cells.Add(hc2);
        // Add the TableHeaderRow as the first item
        // in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr);

        // Iterate through the tasks in the Task list and collect those
        // that have values in the "Related Content" and "Outcome"
        // fields - the fields written to when expense approval is
        // required.
        foreach (SPListItem item in list.Items)
        {
            string s_relContent = "";
            string s_outcome = "";

            try
            {
                // Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related
                  Content");
                s_outcome = item.GetFormattedValue("Outcome");
            }
            catch
            {
                // Task does not have fields - skip it.
                continue;
            }

            if (!String.IsNullOrEmpty(s_relContent) &&
              !String.IsNullOrEmpty(s_outcome))
            {
                // Convert amount to an int and keep a running total.
                sum += Convert.ToInt32(s_outcome);
                TableCell relContent = new TableCell();
                relContent.Text = s_relContent;
                TableCell outcome = new TableCell();
                outcome.Text = "$" + s_outcome;
                TableRow dataRow2 = new TableRow();
                dataRow2.Cells.Add(relContent);
                dataRow2.Cells.Add(outcome);
                Table1.Rows.Add(dataRow2);
            }
        }

        // Report the sum of the reports in the table footer.
           TableFooterRow tfr = new TableFooterRow();
        tfr.BackColor = Color.LightGreen;

        // Create a TableCell object to contain the
        // text for the footer.
        TableCell ftc1 = new TableCell();
        TableCell ftc2 = new TableCell();
        ftc1.Text = "TOTAL: ";
        ftc2.Text = "$" + Convert.ToString(sum);

        // Add the TableCell object to the Cells
        // collection of the TableFooterRow.
        tfr.Cells.Add(ftc1);
        tfr.Cells.Add(ftc2);

        // Add the TableFooterRow to the Rows
        // collection of the table.
        Table1.Rows.Add(tfr);
    }

    catch (Exception errx)
    {
        System.Diagnostics.Debug.WriteLine("Error: " + errx.ToString());
    }
    ```

    > [!WARNING]
    >  Nezapomeňte nahradit "TestServer" v kódu s názvem platný server, na kterém běží SharePoint.

## <a name="test-the-application-page"></a>Otestování stránky aplikace
 Dál určete, zda stránka aplikace správně zobrazí data výdajů.

#### <a name="to-test-the-application-page"></a>Otestování stránky aplikace

1. Zvolte **F5** klíč ke spuštění a nasazení projektu SharePoint.

2. Zvolte **Domů** tlačítko a klikněte na tlačítko **sdílené dokumenty** odkaz na panelu Rychlé spuštění a zobrazit seznam sdílených dokumentů na webu služby SharePoint.

3. K reprezentaci vyúčtování pro účely tohoto příkladu, nahrát několik nových dokumentů do seznam dokumentů výběrem **dokumenty** odkaz na **LibraryTools** kartě v horní části stránky a potom kliknete  **Nahrát dokument o** tlačítko na pásu karet.

4. Po odeslání některé dokumenty instance pracovního postupu výběrem **knihovny** odkaz na **LibraryTools** kartě v horní části stránky a pak zvolíte **nastavení knihovny**tlačítko na pásu karet.

5. V **nastavení knihovny dokumentů** zvolte **nastavení pracovního postupu** odkaz v **oprávnění a správa** oddílu.

6. V **nastavení pracovního postupu** zvolte **přidat pracovní postup** odkaz.

7. V **přidat pracovní postup** zvolte **ExpenseReport - Workflow1** pracovního postupu, zadejte název pracovního postupu, jako například **ExpenseTest**a klikněte na tlačítko **Další** tlačítko.

    Zobrazí se formulář přidružení pracovního postupu. Sestava se používá částka omezení výdajů.

8. Vyplňte formulář přidružení **1000** do **Limit pro automatické schvalování** pole a klikněte na tlačítko **přidružení pracovního postupu** tlačítko.

9. Zvolte **domácí** tlačítko pro návrat na domovskou stránku služby SharePoint.

10. Zvolte **sdílené dokumenty** odkaz na panelu Rychlé spuštění.

11. Vyberte jednu z nahraných dokumenty, které se zobrazí na šipku rozevíracího seznamu, vyberte jej a klikněte na tlačítko **pracovních postupů** položky.

12. Zvolte image vedle ExpenseTest zobrazíte inicializační formulář pracovního postupu.

13. V **celkové výdaje** textového pole zadejte hodnotu, která je větší než 1 000 a klikněte na tlačítko **spuštění pracovního postupu** tlačítko.

     Když ohlášené výdajů překračuje velikost přidělené výdajů, přidá se do seznamu úkolů úlohy. Sloupec s názvem **ExpenseTest** s hodnotou **dokončeno** je taky přidaný ke položky sestavy výdajů v seznamu sdílených dokumentů.

14. Opakujte kroky 13. 11 pomocí jiných dokumentů v seznamu sdílených dokumentů. (Přesný počet dokumentů není důležité.)

15. Zobrazit na stránce souhrnu aplikace expense sestavy tak, že otevřete následující adresu URL ve webovém prohlížeči: **http://**<em>SystemName</em>**/_layouts/ExpenseReport/ApplicationPage1.aspx**.

     Na stránce souhrnné sestavy výdajů uvádí všechny sestavy výdajů, který překročil přidělenou velikost, hodnota, kterou překročení jej a celkovou velikost pro všechny sestavy.

## <a name="next-steps"></a>Další kroky
 Další informace o použití stránek služby SharePoint, naleznete v tématu [vytváření stránek aplikací pro SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

 Vám může Další informace o navrhování obsahu stránky služby SharePoint pomocí návrháře Visual Web v sadě Visual Studio naleznete v těchto tématech:

-   [Vytvoření webové části pro SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

-   [Vytvoření opakovaně použitelné ovládací prvky webové části nebo stránky aplikace](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Viz také:

- [Návod: Vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Postupy: vytvoření stránky aplikace](../sharepoint/how-to-create-an-application-page.md)
- [Vytváření stránek aplikací pro SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)