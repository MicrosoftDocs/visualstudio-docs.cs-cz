---
title: 'Návod: Přidání stránky aplikace do pracovního postupu | Microsoft Docs'
description: V tomto návodu přidejte stránku aplikace do řešení pracovního postupu služby SharePoint. Změnit kód pracovního postupu. Vytváření, kódování a testování stránky aplikace.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d07b5272a31a0c649e12f353aefaa7c63c335eb5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882658"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>Návod: Přidání stránky aplikace do pracovního postupu
  Tento návod ukazuje, jak přidat stránku aplikace, která zobrazuje data odvozená z pracovního postupu do projektu pracovního postupu. Sestaví se na projektu popsaném v tématu [Názorný postup: vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

 Tento názorný postup ukazuje následující úlohy:

- Přidání stránky aplikace ASPX do projektu pracovního postupu služby SharePoint.

- Získávání dat z projektu pracovního postupu a manipulace s nimi.

- Zobrazení dat v tabulce na stránce aplikace.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] a SharePoint.

- Visual Studio

- Také je nutné projekt dokončit v tématu [Návod: vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

## <a name="amend-the-workflow-code"></a>Změnit kód pracovního postupu
 Nejprve do pracovního postupu přidejte řádek kódu, který nastaví hodnotu sloupce výsledek na množství sestavy výdajů. Tato hodnota se používá později v souhrnném výpočtu sestavy výdajů.

#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>Nastavení hodnoty sloupce výsledek v pracovním postupu

1. Načíst dokončený projekt z tématu [Návod: vytvoření pracovního postupu s formuláři přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Otevřete kód pro *Workflow1.cs* nebo *Workflow1. vb* (v závislosti na vašem programovacím jazyce).

3. Do dolní části `createTask1_MethodInvoking` metody přidejte následující kód:

    ```vb
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =
      workflowProperties.InitiationData
    ```

    ```csharp
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =
      workflowProperties.InitiationData;
    ```

## <a name="create-an-application-page"></a>Vytvoření stránky aplikace
 Potom do projektu přidejte formulář ASPX. V tomto formuláři se zobrazí data získaná z projektu pracovního postupu sestavy výdajů. K tomu budete moct přidat stránku aplikace. Stránka aplikace používá stejnou stránku předlohy jako jiné stránky SharePoint, což znamená, že se bude podobat ostatním stránkám na webu služby SharePoint.

#### <a name="to-add-an-application-page-to-the-project"></a>Přidání stránky aplikace do projektu

1. Zvolte projekt ExpenseReport a pak na panelu nabídek zvolte **projekt**  >  **Přidat novou položku**.

2. V podokně **šablony** vyberte šablonu **stránky aplikace** , použijte výchozí název položky projektu (**ApplicationPage1. aspx**) a klikněte na tlačítko **Přidat** .

3. V [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ApplicationPage1. aspx nahraďte `PlaceHolderMain` oddíl následujícím:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
        <asp:Label ID="Label1" runat="server" Font-Bold="True"
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>
        <br />
        <asp:Table ID="Table1" runat="server">
        </asp:Table>
    </asp:Content>
    ```

     Tento kód přidá tabulku na stránku spolu s názvem.

4. Přidejte nadpis na stránku aplikace tím, že nahradíte `PlaceHolderPageTitleInTitleArea` oddíl následujícím způsobem:

    ```aspx-csharp
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >
        Expense Report Summary
    </asp:Content>
    ```

## <a name="code-the-application-page"></a>Kód stránky aplikace
 Dále přidejte kód na stránku souhrnnou aplikaci sestavy výdajů. Když otevřete stránku, kód vyhledá v seznamu úkolů na SharePointu výdaje, které překročily přidělený limit útraty. Sestava obsahuje všechny položky společně se součtem nákladů.

#### <a name="to-code-the-application-page"></a>Chcete-li kódovat stránku aplikace

1. Zvolte uzel **ApplicationPage1. aspx** a pak na panelu nabídek zvolte **Zobrazit**  >  **kód** . zobrazí se kód za stránkou aplikace.

2. Nahraďte příkazy **using** nebo **Import** (v závislosti na vašem programovacím jazyce) v horní části třídy následujícím způsobem:

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

3. Do metody `Page_Load` přidejte následující kód:

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
    > Nezapomeňte nahradit text "TestServer" v kódu názvem platného serveru, na kterém je spuštěna služba SharePoint.

## <a name="test-the-application-page"></a>Testování stránky aplikace
 Dále určete, zda stránka aplikace zobrazuje data o výdajích správně.

#### <a name="to-test-the-application-page"></a>Otestování stránky aplikace

1. Klikněte na klávesu **F5** ke spuštění a nasazení projektu do SharePointu.

2. Klikněte na tlačítko **Domů** a potom kliknutím na odkaz **sdílené dokumenty** na panelu Rychlé spuštění zobrazte seznam sdílených dokumentů na webu služby SharePoint.

3. Chcete-li znázornit sestavy výdajů v tomto příkladu, nahrajte některé nové dokumenty do seznamu dokumentů tak, že na kartě **LibraryTools** v horní části stránky kliknete na odkaz **dokumenty** a pak na pásu karet nástroje kliknete na tlačítko **Nahrát dokument** .

4. Po nahrání některých dokumentů vytvořte instanci pracovního postupu tak, že na kartě **LibraryTools** v horní části stránky kliknete na odkaz **Knihovna** a pak na pásu karet nástroje kliknete na tlačítko **Nastavení knihovny** .

5. Na stránce **Nastavení knihovny dokumentů** klikněte v části **oprávnění a Správa** na odkaz **Nastavení pracovního postupu** .

6. Na stránce **Nastavení pracovního postupu** klikněte na odkaz **Přidat pracovní postup** .

7. Na stránce **Přidat pracovní postup** zvolte pracovní postup **ExpenseReport-Workflow1** , zadejte název pracovního postupu, například **ExpenseTest**, a pak klikněte na tlačítko **Další** .

    Zobrazí se formulář přidružení pracovního postupu. Použijte ji k oznámení částky limitu výdajů.

8. Ve formuláři přidružení zadejte do pole **limit automatického schvalování** hodnotu **1000** a pak klikněte na tlačítko **přidružit pracovní postup** .

9. Klikněte na tlačítko **Domů** a vraťte se na domovskou stránku služby SharePoint.

10. Na panelu Rychlé spuštění klikněte na odkaz **sdílené dokumenty** .

11. Zvolte jeden z odesílaných dokumentů, chcete-li zobrazit šipku rozevíracího seznamu, vyberte ji a potom zvolte položku **pracovní postupy** .

12. Vyberte obrázek vedle ExpenseTest k zobrazení inicializačního formuláře pracovního postupu.

13. Do textového pole **Celkový počet výdajů** zadejte hodnotu, která je větší než 1000, a pak klikněte na tlačítko **Spustit pracovní postup** .

     Když hlášené náklady překročí přidělenou částku výdajů, přidá se do Seznam úkolů úkol. Do položky sestavy výdajů v seznamu Sdílené dokumenty se přidá také sloupec s názvem **ExpenseTest** s hodnotou **dokončeno** .

14. Opakujte kroky 11-13 s dalšími dokumenty v seznamu Sdílené dokumenty. (Přesný počet dokumentů není důležitý.)

15. Zobrazte stránku souhrnná aplikace sestavy výdajů otevřením následující adresy URL ve webovém prohlížeči: **http://**<em>System</em>**/_layouts/ExpenseReport/ApplicationPage1.aspx**.

     Stránka Souhrn sestavy výdajů obsahuje seznam všech sestav výdajů, které překročily přidělené množství, o částku, kterou ji překročil, a celkovou částku pro všechny sestavy.

## <a name="next-steps"></a>Další kroky
 Další informace o stránkách aplikace SharePoint naleznete v tématu [Vytvoření stránek aplikace pro službu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

 Další informace o návrhu obsahu stránky SharePointu pomocí vizuálního webového návrháře v aplikaci Visual Studio najdete v těchto tématech:

- [Vytvořte webové části pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Vytváření opakovaně použitelných ovládacích prvků pro webové části nebo stránky aplikací](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Viz také

- [Návod: vytvoření pracovního postupu pomocí formulářů přidružení a inicializace](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Postupy: Vytvoření stránky aplikace](../sharepoint/how-to-create-an-application-page.md)
- [Vytváření stránek aplikací pro službu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)