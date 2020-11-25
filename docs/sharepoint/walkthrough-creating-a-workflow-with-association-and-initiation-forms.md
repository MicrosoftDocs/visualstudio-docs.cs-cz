---
title: Vytvoření pracovního postupu pomocí formulářů přidružení a inicializace
description: V tomto návodu k SharePointu vytvořte základní sekvenční pracovní postup, který zahrnuje použití formulářů přidružení a inicializace.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62501a23695b81ee0437d3210dced7c81f9b054e
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970435"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>Návod: vytvoření pracovního postupu pomocí formulářů přidružení a inicializace
  Tento návod ukazuje, jak vytvořit základní sekvenční pracovní postup, který zahrnuje použití formulářů přidružení a inicializace. Jedná se o formuláře ASPX, které umožňují přidání parametrů do pracovního postupu, když jsou nejprve přidruženy správcem služby SharePoint (formulář přidružení), a pokud je pracovní postup spuštěn uživatelem (inicializační formulář).

 Tento názorný postup popisuje scénář, ve kterém chce uživatel vytvořit pracovní postup schválení pro sestavy výdajů, který má následující požadavky:

- Když je pracovní postup přidružen k seznamu, správce se zobrazí ve formuláři přidružení, kde zadá limit dolaru pro sestavy výdajů.

- Zaměstnanci nahrávají své zprávy o výdajích do seznamu Sdílené dokumenty, spustí pracovní postup a pak v inicializačním formuláři pracovního postupu zadejte celkový výdaj.

- Pokud celkový počet zpráv o výdajích zaměstnanců překročil předdefinovaný limit správce, vytvoří se úkol pro manažera zaměstnance, který schválí sestavu výdajů. Pokud je ale celková Sestava výdajů zaměstnanců menší nebo rovna limitu výdajů, automaticky schválená zpráva se zapíše do seznamu historie pracovního postupu.

  Tento návod znázorňuje následující úlohy:

- Vytváření projektu sekvenčního pracovního postupu definice SharePointového seznamu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Vytváří se plán pracovního postupu.

- Zpracování událostí aktivity pracovního postupu.

- Vytváření přidružení pracovního postupu a inicializačních formulářů.

- Přidružení pracovního postupu.

- Ruční spuštění pracovního postupu.

> [!NOTE]
> I když tento návod používá projekt sekvenčního pracovního postupu, proces je stejný pro pracovní postupy stavového stroje.
>
> Kromě toho může počítač v následujících pokynech zobrazit jiné názvy nebo umístění pro některé [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] prvky uživatelského rozhraní. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Tyto prvky jsou určeny edicí a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] a SharePoint.

- Visual Studio

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Vytvoření projektu pro sekvenční pracovní postup SharePointu
 Nejprve vytvořte projekt sekvenčního pracovního postupu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Sekvenční pracovní postup je série kroků, které se spouští v pořadí až do dokončení poslední aktivity. V tomto postupu vytvoříte sekvenční pracovní postup, který se bude vztahovat na seznam sdílených dokumentů v SharePointu. Průvodce pracovním postupem umožňuje přidružení pracovního postupu k webu nebo k definici seznamu a umožňuje určit, kdy se pracovní postup spustí.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Vytvoření projektu sekvenčního pracovního postupu SharePointu

1. Na panelu nabídek vyberte možnost **soubor**  >  **Nový**  >  **projekt** . zobrazí se dialogové okno **Nový projekt** .

2. Rozbalte uzel **služby SharePoint** v rámci **jazyka Visual C#** nebo **Visual Basic** a pak vyberte uzel **2010** .

3. V podokně **šablony** vyberte šablonu projektu **projektu SharePoint 2010** .

4. Do pole **název** zadejte **ExpenseReport** a poté klikněte na tlačítko **OK** .

     Zobrazí se **Průvodce přizpůsobením SharePointu** .

5. Na stránce **Zadejte lokalitu a úroveň zabezpečení pro ladění** zvolte možnost **nasadit jako řešení farmy** a pak kliknutím na tlačítko **Dokončit** přijměte úroveň vztahu důvěryhodnosti a výchozí web.

     Tento krok také nastaví úroveň důvěryhodnosti pro řešení jako řešení farmy, což je jediná dostupná možnost pro projekty pracovního postupu.

6. V **Průzkumník řešení** vyberte uzel projektu.

7. Na řádku nabídek klikněte na položku **projekt**  >  **Přidat novou položku**.

8. V části **Visual C#** nebo **Visual Basic** rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

9. V podokně **šablony** zvolte šablonu **sekvenční pracovní postup (pouze řešení farmy)** a pak klikněte na tlačítko **Přidat** .

     Zobrazí se **Průvodce přizpůsobením SharePointu** .

10. Na stránce **Zadejte název pracovního postupu pro ladění** přijměte výchozí název (**ExpenseReport-Workflow1**). Ponechte výchozí hodnotu typu šablony pracovního postupu (**list Workflow)**. Klikněte na tlačítko **Další** .

11. V případě, že chcete, **aby aplikace Visual Studio automaticky přidružil pracovní postup na stránce relace ladění?** zrušte zaškrtnutí políčka, které automaticky přidruží šablonu pracovního postupu, pokud je zaškrtnuto.

     Tento krok vám umožní ručně přidružit pracovní postup k seznamu Sdílené dokumenty, který zobrazuje formulář přidružení.

12. Klikněte na tlačítko **Dokončit** .

## <a name="add-an-association-form-to-the-workflow"></a>Přidání formuláře přidružení k pracovnímu postupu
 Dále vytvořte. Formulář přidružení ASPX, který se zobrazí, když správce služby SharePoint poprvé přidruží pracovní postup k dokumentu sestavy výdajů.

#### <a name="to-add-an-association-form-to-the-workflow"></a>Přidání formuláře přidružení k pracovnímu postupu

1. V **Průzkumník řešení** vyberte uzel **Workflow1** .

2. Na panelu nabídek vyberte možnost **projekt**  >  **Přidat novou položku** , chcete-li zobrazit dialogové okno **Přidat novou položku** .

3. V zobrazení stromu dialogového okna rozbalte možnost **Visual C#** nebo **Visual Basic** (v závislosti na jazyku projektu), rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

4. V seznamu šablon vyberte šablonu **formuláře přidružení pracovního postupu** .

5. Do textového pole **název** zadejte **ExpenseReportAssocForm. aspx**.

6. Kliknutím na tlačítko **Přidat** přidejte formulář do projektu.

## <a name="designing-and-coding-the-association-form"></a>Návrh a kódování formuláře přidružení
 V tomto postupu zavedete do formuláře přidružení funkce a přidáte do něj ovládací prvky a kód.

#### <a name="to-design-and-code-the-association-form"></a>Návrh a kódování formuláře přidružení

1. Ve formuláři asociace (ExpenseReportAssocForm. aspx) vyhledejte `asp:Content` element, který má `ID="Main"` .

2. Přímo po prvním řádku v tomto elementu obsahu přidejte následující kód pro vytvoření popisku a textového pole s výzvou k omezení pro schválení výdajů (*AutoApproveLimit*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" runat="server" />
    <br /><br />
    ```

3. Rozbalením souboru **ExpenseReportAssocForm. aspx** v **Průzkumník řešení** zobrazíte jeho závislé soubory.

    > [!NOTE]
    > Pokud je projekt v [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] , musíte pro provedení tohoto kroku zvolit tlačítko **Zobrazit všechny soubory** .

4. Otevřete místní nabídku pro soubor ExpenseReportAssocForm. aspx a vyberte možnost **Zobrazit kód**.

5. Nahraďte `GetAssociationData` metodu pomocí:

    ```vb
    Private Function GetAssociationData() As String
        ' TODO: Return a string that contains the association data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return Me.AutoApproveLimit.Text
    End Function
    ```

    ```csharp
    private string GetAssociationData()
    {
        // TODO: Return a string that contains the association data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.AutoApproveLimit.Text;
    }
    ```

## <a name="add-an-initiation-form-to-the-workflow"></a>Přidání inicializačního formuláře do pracovního postupu
 Dále vytvořte inicializační formulář, který se zobrazí, když uživatelé spouštějí pracovní postup na svých sestavách výdajů.

#### <a name="to-create-an-initiation-form"></a>Vytvoření inicializačního formuláře

1. V **Průzkumník řešení** vyberte uzel **Workflow1** .

2. Na panelu nabídek vyberte možnost **projekt**  >  **Přidat novou položku** . zobrazí se dialogové okno **Přidat novou položku** .

3. V zobrazení stromu dialogového okna rozbalte možnost **Visual C#** nebo **Visual Basic**  (v závislosti na jazyku projektu), rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

4. V seznamu šablon vyberte šablonu **formuláře pro zahájení pracovního postupu** .

5. Do textového pole **název** zadejte **ExpenseReportInitForm. aspx**.

6. Kliknutím na tlačítko **Přidat** přidejte formulář do projektu.

## <a name="designing-and-coding-the-initiation-form"></a>Návrh a kódování inicializačního formuláře
 Dále zaveďte do inicializačního formuláře funkce přidáním ovládacích prvků a kódu.

#### <a name="to-code-the-initiation-form"></a>Chcete-li vytvořit kód inicializačního formuláře

1. V inicializačním formuláři (ExpenseReportInitForm. aspx) vyhledejte `asp:Content` prvek, který obsahuje `ID="Main"` .

2. Přímo po prvním řádku tohoto elementu obsahu přidejte následující kód k vytvoření popisku a textového pole, ve kterém se zobrazí limit pro schvalování výdajů (*AutoApproveLimit*), který byl zadán ve formuláři přidružení, a další popisek a textové pole, které má vyzvat k vyúčtování nákladů (*ExpenseTotal*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />
    <br /><br />
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />

    <asp:TextBox ID="ExpenseTotal" runat="server" />
    <br /><br />
    ```

3. Rozbalením souboru **ExpenseReportInitForm. aspx** v **Průzkumník řešení** zobrazíte jeho závislé soubory.

4. Otevřete místní nabídku pro soubor ExpenseReportInitForm. aspx a vyberte možnost **Zobrazit kód**.

5. Nahraďte `Page_Load` metodu následujícím příkladem:

    ```vb
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As
      EventArgs) Handles Me.Load
        InitializeParams()
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New
          Guid(associationGuid)).AssociationData
        ' Optionally, add code here to pre-populate your form fields.
    End Sub
    ```

    ```csharp
    protected void Page_Load(object sender, EventArgs e)
    {
        InitializeParams();
        this.AutoApproveLimit.Text =
          workflowList.WorkflowAssociations[new
          Guid(associationGuid)].AssociationData;
    }
    ```

6. Nahraďte `GetInitiationData` metodu následujícím příkladem:

    ```vb
    ' This method is called when the user clicks the button to start the workflow.
    Private Function GetInitiationData() As String
        Return Me.ExpenseTotal.Text
        ' TODO: Return a string that contains the initiation data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return String.Empty
    End Function
    ```

    ```csharp
    // This method is called when the user clicks the button to start the workflow.
    private string GetInitiationData()
    {
        // TODO: Return a string that contains the initiation data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.ExpenseTotal.Text;
    }
    ```

## <a name="cutomize-the-workflow"></a>Cutomize pracovní postup
 Dále upravte pracovní postup. Později přidružíte k pracovnímu postupu dva formuláře.

#### <a name="to-customize-the-workflow"></a>Postup přizpůsobení pracovního postupu

1. V Návrháři pracovního postupu zobrazte pracovní postup otevřením Workflow1 v projektu.

2. V sadě **nástrojů** rozbalte uzel **Windows Workflow v 3.0** a vyhledejte aktivitu **IfElse** .

3. Přidejte tuto aktivitu do pracovního postupu provedením jednoho z následujících kroků:

    - Otevřete místní nabídku aktivity **IfElse** , zvolte možnost **Kopírovat**, otevřete místní nabídku pro řádek pod aktivitou **onWorkflowActivated1** v Návrháři pracovních postupů a pak zvolte možnost **Vložit**.

    - Přetáhněte aktivitu **IfElse** ze **sady nástrojů** a připojte ji k řádku pod aktivitou **onWorkflowActiviated1** v Návrháři pracovních postupů.

4. V sadě nástrojů rozbalte uzel **pracovní postup služby SharePoint** a vyhledejte aktivitu **CreateTask –** .

5. Přidejte tuto aktivitu do pracovního postupu provedením jednoho z následujících kroků:

    - Otevřete místní nabídku aktivity **CreateTask –** , zvolte možnost **Kopírovat**, otevřete místní nabídku pro jednu ze dvou oblastí **přetažení** v rámci **IfElseActivity1** v Návrháři postupu provádění a pak zvolte možnost **Vložit**.

    - Přetáhněte aktivitu **CreateTask –** ze **sady nástrojů** na jednu ze dvou **aktivit přetažení** v oblasti **IfElseActivity1**.

6. V okně **vlastnosti** zadejte jako vlastnost **CorrelationToken** hodnotu vlastnosti *taskToken* .

7. Rozbalte vlastnost **CorrelationToken** výběrem znaménka plus (![TreeView plus](../sharepoint/media/plus.gif "TreeView plus")) vedle něj.

8. Vyberte šipku rozevíracího seznamu u dílčí vlastnosti **OwnerActivityName** a nastavte hodnotu *Workflow1* .

9. Zvolte vlastnost **taskid** a potom kliknutím na tlačítko se třemi tečkami (![Elipsa ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "Elipsa ASP.NET Mobile Designer")) zobrazte dialogové okno **vlastností vazby** .

10. Zvolte kartu **vazba na novou členskou** položku, klikněte na tlačítko **vytvořit pole** a pak klikněte na tlačítko **OK** .

11. Zvolte vlastnost **TaskProperties** a potom klikněte na tlačítko se třemi tečkami (![Elipsa ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "Elipsa ASP.NET Mobile Designer")) k zobrazení dialogového okna **vlastností vazby** .

12. Zvolte kartu **vazba na novou členskou** položku, klikněte na tlačítko **vytvořit pole** a pak klikněte na tlačítko **OK** .

13. V sadě **nástrojů** rozbalte uzel **pracovní postup služby SharePoint** a vyhledejte aktivitu **LogToHistoryListActivity** .

14. Přidejte tuto aktivitu do pracovního postupu provedením jednoho z následujících kroků:

    - Otevřete místní nabídku aktivity **LogToHistoryListActivity** , zvolte možnost **Kopírovat**, v Návrháři pracovního postupu otevřete místní nabídku pro ostatní **aktivity přetažení** v rámci **IfElseActivity1** a pak zvolte možnost **Vložit**.

    - Přetáhněte aktivitu **LogToHistoryListActivity** ze **sady nástrojů** a přetáhněte ji do jiných oblastí **přetažení** v rámci **IfElseActivity1**.

## <a name="add-code-to-the-workflow"></a>Přidat kód do pracovního postupu
 Potom do pracovního postupu přidejte kód, který bude poskytovat funkci IT.

#### <a name="to-add-code-to-the-workflow"></a>Přidání kódu do pracovního postupu

1. Otevřete místní nabídku aktivity **createTask1** v Návrháři postupu a pak zvolte možnost **Zobrazit kód**.

2. Přidejte následující metodu:

    ```vb
    Private Sub createTask1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        createTask1_TaskId1 = Guid.NewGuid
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"
        createTask1_TaskProperties1.Description = "Please approve the
          expense report"
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed"
    End Sub
    ```

    ```csharp
    private void createTask1_MethodInvoking(object sender, EventArgs e)
    {
        createTask1_TaskId1 = Guid.NewGuid();
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";
        createTask1_TaskProperties1.Description = "Please approve the
          expense report";
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed";
    }
    ```

    > [!NOTE]
    > V kódu nahraďte `somedomain\\someuser` doménou a uživatelským jménem, pro které bude úkol vytvořen, například " `Office\\JoeSch` ". Pro účely testování je nejjednodušší použít účet, se kterým vyvíjíte.

3. Pod `MethodInvoking` metodu přidejte následující příklad:

    ```vb
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As
      ConditionalEventArgs)
        Dim approval As Boolean = False
        If (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData)) Then
            approval = True
        End If
        e.Result = approval
    End Sub
    ```

    ```csharp
    private void checkApprovalNeeded(object sender, ConditionalEventArgs
      e)
    {
        bool approval = false;
        if (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData))
        {
            approval = true;
        }
        e.Result = approval;
    }
    ```

4. V Návrháři pracovních postupů vyberte aktivitu **ifElseBranchActivity1** .

5. V okně **vlastnosti** klikněte na šipku rozevíracího seznamu vlastnosti **Podmínka** a pak nastavte hodnotu *podmínky kódu* .

6. Rozbalte vlastnost **Condition** výběrem znaménka plus (![TreeView plus](../sharepoint/media/plus.gif "TreeView plus")) vedle něj a nastavte jeho hodnotu na *checkApprovalNeeded*.

7. V Návrháři pracovního postupu otevřete místní nabídku aktivity **logToHistoryListActivity1** a pak zvolte možnost **Generovat obslužné rutiny** pro vygenerování prázdné metody pro `MethodInvoking` událost.

8. Nahraďte `MethodInvoking` kód následujícím kódem:

    ```vb
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto
          approved for " + workflowProperties.InitiationData)
    End Sub
    ```

    ```csharp
    private void logToHistoryListActivity1_MethodInvoking(object sender,
      EventArgs e)
    {
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was
          auto approved for " + workflowProperties.InitiationData;
    }
    ```

9. Pro ladění programu vyberte klávesu **F5** .

     Tím se aplikace zkompiluje, zabalí, nasadí ji, aktivuje její funkce, recykluje [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] fond aplikací a potom spustí prohlížeč v umístění zadaném ve vlastnosti **Adresa URL webu** .

## <a name="associating-the-workflow-to-the-documents-list"></a>Přiřazení pracovního postupu k seznamu dokumentů
 Potom zobrazte formulář přidružení pracovního postupu přiřazením pracovního postupu k seznamu **SharedDocuments** na webu služby SharePoint.

#### <a name="to-associate-the-workflow"></a>Postup přidružení pracovního postupu

1. Na panelu Rychlé spuštění klikněte na odkaz **sdílené dokumenty** .

2. Zvolte odkaz **Knihovna** na kartě **nástroje knihovny** a pak zvolte tlačítko pro pás karet **Nastavení knihovny** .

3. V části **oprávnění a Správa** zvolte odkaz **Nastavení pracovního postupu** a pak klikněte na odkaz **Přidat pracovní postup** na stránku **pracovní postupy** .

4. V horním seznamu na stránce nastavení pracovního postupu vyberte šablonu **ExpenseReport-Workflow1** .

5. Do dalšího pole zadejte **ExpenseReportWorkflow** a potom klikněte na tlačítko **Další** .

     Tím se pracovní postup přidruží k seznamu **sdílené dokumenty** a zobrazí se formulář přidružení pracovního postupu.

6. Do textového pole **limit pro automatické schválení** zadejte **1200** a potom klikněte na tlačítko **přidružit pracovní postup** .

## <a name="start-the-workflow"></a>Spuštění pracovního postupu
 Potom přidružte pracovní postup k jednomu z dokumentů v seznamu **sdílené dokumenty** , aby se zobrazil inicializační formulář pracovního postupu.

#### <a name="to-start-the-workflow"></a>Spuštění pracovního postupu

1. Na stránce SharePoint klikněte na tlačítko **Domů** .

2. Kliknutím na odkaz **sdílené dokumenty** na panelu Rychlé spuštění zobrazte seznam **sdílených dokumentů** .

3. V horní části stránky klikněte na odkaz **dokumenty** na kartě **nástroje knihovny** a pak na pásu karet klikněte na tlačítko **Nahrát dokument** a nahrajte nový dokument do seznamu **sdílené dokumenty** .

4. V dialogovém okně **Nahrát dokument** klikněte na tlačítko **Procházet** , zvolte libovolný soubor dokumentu, klikněte na tlačítko **otevřít** a pak klikněte na tlačítko **OK** .

     Nastavení dokumentu v tomto dialogovém okně můžete změnit, ale ponechte výchozí hodnoty výběrem tlačítka **Uložit** .

5. Zvolte nahraný dokument, klikněte na šipku rozevíracího seznamu, která se zobrazí, a potom zvolte položku **pracovní postupy** .

6. Vyberte obrázek vedle ExpenseReportWorkflow.

     Tím se zobrazí inicializační formulář pracovního postupu. (Všimněte si, že hodnota zobrazená v poli **omezení automatického schvalování** je jen pro čtení, protože byla zadána do formuláře přidružení.)

7. Do textového pole **Celková cena za výdaj** zadejte **1600** a pak klikněte na tlačítko **Spustit pracovní postup** .

     Tím se znovu zobrazí seznam **sdílených dokumentů** . Nový sloupec s názvem **ExpenseReportWorkflow** s hodnotou **Completed** se přidá do položky pracovního postupu, který jste právě spustili.

8. Zvolte šipku rozevíracího seznamu vedle nahraného dokumentu a pak zvolte položku **pracovní postupy** pro zobrazení stránky stavu pracovního postupu. V části **dokončené pracovní postupy** vyberte **Dokončená** hodnota. Úloha je uvedena v části **úlohy** .

9. Vyberte název úlohy, pro kterou chcete zobrazit podrobnosti o úloze.

10. Vraťte se do seznamu **SharedDocuments** a restartujte pracovní postup, a to buď pomocí stejného dokumentu, nebo jiného.

11. Zadejte částku na inicializační stránce, která je menší nebo rovna hodnotě zadané na stránce asociace (**1200**).

     V takovém případě se místo úlohy vytvoří položka v seznamu historie. Položka se zobrazí v části **historie pracovního postupu** na stránce stavu pracovního postupu. Poznamenejte si zprávu ve sloupci **výsledek** události historie. Obsahuje text zadaný v `logToHistoryListActivity1.MethodInvoking` události, která obsahuje automaticky schválenou hodnotu.

## <a name="next-steps"></a>Další kroky
 Další informace o tom, jak vytvořit šablony pracovního postupu, najdete v těchto tématech:

- Další informace o pracovních postupech služby SharePoint naleznete v tématu [pracovní postupy ve službě Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms416312(v=office.14)).

## <a name="see-also"></a>Viz také
- [Vytváření řešení pracovního postupu služby SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Návod: Přidání stránky aplikace do pracovního postupu](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)
