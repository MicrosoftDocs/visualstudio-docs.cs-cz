---
title: 'Návod: Vytvoření pracovního postupu pomocí formulářů přidružení a inicializace | Dokumentace Microsoftu'
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
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b6aafde6fed0a1f1722c2d355499523114aaaa00
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873874"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>Návod: Vytvoření pracovního postupu pomocí formulářů přidružení a inicializace
  Tento návod ukazuje, jak vytvořit základní sekvenční pracovní postup, který zahrnuje použití formuláře pro asociaci a. Jedná se o ASPX formuláře, které umožňují parametry se mají přidat do pracovního postupu, pokud je první související (formulář přidružení) správcem služby SharePoint a při spuštění pracovního postupu uživatelem (inicializační formulář).  
  
 Tento návod popisuje scénář, kdy uživatel chce vytvořit schvalovací pracovní postup pro vyúčtování, který má následující požadavky:  
  
- Když pracovní postup přidružen se seznamem, správce se zobrazí výzva s formulář přidružení kde vstupem limitem pro vyúčtování.  
  
- Zaměstnanci nahrát jejich vyúčtování seznamu Sdílené dokumenty, spustit pracovní postup a zadejte výdajů celkem inicializační formulář pracovního postupu.  
  
- Pokud vyúčtování celkový počet zaměstnanců překračuje limit předdefinovaného správce, se vytvoří úkol k nadřízenému ke schválení vyúčtování. Pokud zaměstnance výdajů sestavy součet je menší než nebo rovna omezení výdajů, zprávu o schvalovány automaticky zapsat do seznamu historie pracovního postupu.  
  
  Tento návod znázorňuje následující úlohy:  
  
- Vytvoření projektu sekvenční pracovní postup definice seznamu služby SharePoint v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
- Vytvoření plánu pracovního postupu.  
  
- Zpracování události aktivit pracovního postupu.  
  
- Vytvoření formuláře pro asociaci a přidružení pracovního postupu.  
  
- Přidružení pracovního postupu.  
  
- Ruční spuštění pracovního postupu.  
  
> [!NOTE]  
>  I když tento návod používá projekt sekvenčního pracovního postupu, proces je stejný pro pracovní postupy stavu počítače.  
>   
>  Kromě toho, že váš počítač může zobrazit jiné názvy nebo umístění některých [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] prvky uživatelského rozhraní v následujících pokynech. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Edicí a nastavení, které používáte určit tyto prvky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Podporované edice systému [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] a SharePoint.  
  
-   Visual Studio.  
  
## <a name="create-a-sharepoint-sequential-workflow-project"></a>Vytvoření projektu sekvenčního pracovního postupu služby SharePoint
 Nejprve vytvořte projekt sekvenčního pracovního postupu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Sekvenční pracovní postup je posloupnost kroků, které provádí v pořadí, dokud se nedokončí poslední aktivita. V tomto postupu bude Vytvoření sekvenčního pracovního postupu, která se použije k seznamu sdílených dokumentů v Sharepointu. Průvodce pracovním postupu umožňuje pracovní postup přidružit k webu nebo definici seznamu a umožňuje určit, kdy se spustí pracovní postup.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Chcete-li vytvořit projekt sekvenčního pracovního postupu služby SharePoint  
  
1.  V panelu nabídky zvolte **souboru** > **nový** > **projektu** zobrazíte **nový projekt** dialogové okno.  
  
2.  Rozbalte **SharePoint** uzlu buď **Visual C#** nebo **jazyka Visual Basic**a klikněte na tlačítko **2010** uzlu.  
  
3.  V **šablony** podokně, vyberte **projektu služby SharePoint 2010** šablony projektu.  
  
4.  V **název** zadejte **ExpenseReport** a klikněte na tlačítko **OK** tlačítko.  
  
     **Průvodce přizpůsobením SharePoint** se zobrazí.  
  
5.  V **zadejte web a úroveň zabezpečení pro ladění** zvolte **nasadit jako řešení farmy** přepínač a klikněte na tlačítko **Dokončit** tlačítko tak, aby přijímal vztah důvěryhodnosti úroveň a výchozí web.  
  
     Tento krok také nastaví úroveň důvěryhodnosti řešení jako řešení farmy, která je k dispozici jenom možnost pro projekty pracovního postupu.  
  
6.  V **Průzkumníka řešení**, zvolte uzel projektu.  
  
7.  V panelu nabídky zvolte **projektu** > **přidat novou položku**.  
  
8.  V části **Visual C#** nebo **jazyka Visual Basic**, rozbalte **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.  
  
9. V **šablony** podokně zvolte **sekvenčního pracovního postupu (pouze řešení farmy)** šablony a klikněte na tlačítko **přidat** tlačítko.  
  
     **Průvodce přizpůsobením SharePoint** se zobrazí.  
  
10. V **zadejte název pracovního postupu pro ladění** stránce, přijměte výchozí název (**ExpenseReport - Workflow1**). Ponechte výchozí hodnotu typu šablony pracovního postupu (**pracovní postup seznamu)**. Zvolte **Další** tlačítko.  
  
11. V **přejete si Visual Studio automaticky přidružovala pracovní postup v ladicí relaci?** stránce, zrušte zaškrtnutí pole, které se automaticky přidruží šablony pracovního postupu, pokud je zaškrtnuto.  
  
     Tento krok umožňuje ručně přidružení pracovního postupu s později na seznamu Sdílené dokumenty, které zobrazí formulář přidružení.  
  
12. Zvolte **Dokončit** tlačítko.  
  
## <a name="add-an-association-form-to-the-workflow"></a>Přidat formulář přidružení pracovního postupu
 Dále vytvořte. Formulář přidružení ASPX, který se zobrazí, když správce Sharepointu nejprve přidruží pracovní postup s dokumentem sestavy výdajů.  
  
#### <a name="to-add-an-association-form-to-the-workflow"></a>Chcete-li přidat formulář přidružení pracovního postupu  
  
1.  Zvolte **Workflow1** uzel v **Průzkumníka řešení**.  
  
2.  V panelu nabídky zvolte **projektu** > **přidat novou položku** zobrazíte **přidat novou položku** dialogové okno.  
  
3.  Ve stromovém zobrazení pole dialogového okna rozbalte buď **Visual C#** nebo **jazyka Visual Basic** (v závislosti na jazyku projektu), rozbalte **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.  
  
4.  V seznamu šablon vyberte **formulář přidružení pracovního postupu** šablony.  
  
5.  V **název** textové pole, zadejte **ExpenseReportAssocForm.aspx**.  
  
6.  Zvolte **přidat** tlačítko pro přidání formuláře do projektu.  
  
## <a name="designing-and-coding-the-association-form"></a>Návrh a kódování formulář přidružení
 V tomto postupu zavedení funkce do formuláře přidružení tak, že do ní přidáte ovládací prvky a kódem.  
  
#### <a name="to-design-and-code-the-association-form"></a>Návrh a kód formulář přidružení  
  
1.  Formulář přidružení (ExpenseReportAssocForm.aspx), vyhledejte `asp:Content` element, který má `ID="Main"`.  
  
2.  Přímo za první řádek v tomto obsahu elementu, přidejte následující kód k vytvoření popisku a textového pole, které zobrazí výzvu k zadání schválení limitu výdajů (*AutoApproveLimit*):  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  Rozbalte **ExpenseReportAssocForm.aspx** ve **Průzkumníka řešení** zobrazíte jeho závislých souborů.  
  
    > [!NOTE]  
    >  Pokud je váš projekt v [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], je nutné vybrat **zobrazit všechny soubory** tlačítko k provedení tohoto kroku.  
  
4.  Otevřete místní nabídku pro soubor ExpenseReportAssocForm.aspx a zvolte **zobrazit kód**.  
  
5.  Nahradit `GetAssociationData` metody:  
  
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
  
## <a name="add-an-initiation-form-to-the-workflow"></a>Přidat inicializační formulář pracovního postupu
 Dále vytvořte inicializační formulář, který se zobrazí, když uživatelé spustí pracovní postup před jejich vyúčtování.  
  
#### <a name="to-create-an-initiation-form"></a>Chcete-li vytvořit inicializační formulář  
  
1.  Zvolte **Workflow1** uzel v **Průzkumníka řešení**.  
  
2.  V panelu nabídky zvolte **projektu** > **přidat novou položku** zobrazení **přidat novou položku** dialogové okno.  
  
3.  Ve stromovém zobrazení pole dialogového okna rozbalte buď **Visual C#** nebo **jazyka Visual Basic** (v závislosti na jazyku projektu), rozbalte **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.  
  
4.  V seznamu šablon vyberte **inicializační formulář pracovního postupu** šablony.  
  
5.  V **název** textové pole, zadejte **ExpenseReportInitForm.aspx**.  
  
6.  Zvolte **přidat** tlačítko pro přidání formuláře do projektu.  
  
## <a name="designing-and-coding-the-initiation-form"></a>Návrh a kódování inicializační formulář
 V dalším kroku zavedení funkce, které inicializační formulář tak, že do ní přidáte ovládací prvky a kódem.  
  
#### <a name="to-code-the-initiation-form"></a>Do kódu inicializační formulář  
  
1.  Inicializační formulář (ExpenseReportInitForm.aspx), vyhledejte `asp:Content` element, který obsahuje `ID="Main"`.  
  
2.  Přímo za první řádek v tomto obsahu elementu, přidejte následující kód k vytvoření popisku a textového pole, která zobrazuje schválení limitu výdajů (*AutoApproveLimit*), který jste zadali v formulář přidružení a další popisek a textové pole pro zadání celkové náklady (*ExpenseTotal*):  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  Rozbalte **ExpenseReportInitForm.aspx** ve **Průzkumníka řešení** zobrazíte jeho závislých souborů.  
  
4.  Otevřete místní nabídku pro soubor ExpenseReportInitForm.aspx a zvolte **zobrazit kód**.  
  
5.  Nahradit `Page_Load` metodou v následujícím příkladu:  
  
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
  
6.  Nahradit `GetInitiationData` metodou v následujícím příkladu:  
  
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
  
## <a name="cutomize-the-workflow"></a>Vlastní nastavení pracovního postupu
 Dále přizpůsobte pracovní postup. Později kterou přidružíte dvě různými formami do pracovního postupu.  
  
#### <a name="to-customize-the-workflow"></a>Přizpůsobení pracovního postupu  
  
1.  Zobrazení pracovního postupu tak, že otevřete Workflow1 v projektu v Návrháři pracovních postupů.  
  
2.  V **nástrojů**, rozbalte **pracovního postupu Windows v3.0** uzlu a vyhledejte **IfElse** aktivity.  
  
3.  Přidejte tuto aktivitu do pracovního postupu pomocí jedné z následujících kroků:  
  
    -   Otevřete místní nabídku **IfElse** aktivitu, zvolte **kopírování**, otevřete místní nabídku pro řádek u **onWorkflowActivated1** aktivity v Návrháři postupu provádění a klikněte na tlačítko **vložit**.  
  
    -   Přetáhněte **IfElse** aktivita z **nástrojů**a připojte ho k řádku pod **onWorkflowActiviated1** aktivity v Návrháři pracovních postupů.  
  
4.  Na panelu nástrojů rozbalte **pracovního postupu služby SharePoint** uzlu a vyhledejte **createtask –** aktivity.  
  
5.  Přidejte tuto aktivitu do pracovního postupu pomocí jedné z následujících kroků:  
  
    -   Otevřete místní nabídku **createtask –** aktivitu, zvolte **kopírování**, otevřete místní nabídku pro jednu ze dvou **Sem přetáhněte aktivity** oblastí v rámci  **IfElseActivity1** v Návrháři pracovních postupů a klikněte na tlačítko **vložit**.  
  
    -   Přetáhněte **createtask –** aktivita z **nástrojů** na jednu ze dvou **Sem přetáhněte aktivity** oblastí v rámci **IfElseActivity1**.  
  
6.  V **vlastnosti** okno, zadejte hodnotu vlastnosti *taskToken* pro **CorrelationToken** vlastnost.  
  
7.  Rozbalte **CorrelationToken** vlastnost kliknutím na symbol plus (![TreeView plus](../sharepoint/media/plus.gif "TreeView plus")) vedle sebe.  
  
8.  Klikněte na šipku rozevíracího seznamu na **OwnerActivityName** dílčí vlastnost a nastavte *Workflow1* hodnotu.  
  
9. Zvolte **TaskId** vlastnost a klikněte na tlačítko se třemi tečkami (![ASP.NET – Návrhář mobilních řešení Elipsa](../sharepoint/media/mwellipsis.gif "elipsa ASP.NET – Návrhář mobilních řešení")) tlačítko pro zobrazení **Svázat vlastnost** dialogové okno.  
  
10. Zvolte **vytvořit vazbu na nového člena** , vyberte **vytvořit pole** přepínač a klikněte na tlačítko **OK** tlačítko.  
  
11. Zvolte **TaskProperties** vlastnost a klikněte na tlačítko se třemi tečkami (![elipsa ASP.NET – Návrhář mobilních řešení](../sharepoint/media/mwellipsis.gif "ASP.NET – Návrhář mobilních řešení Elipsa")) tlačítko pro zobrazení  **Vytvořit vazbu vlastnosti** dialogové okno.  
  
12. Zvolte **vytvořit vazbu na nového člena** , vyberte **vytvořit pole** přepínač a klikněte na tlačítko **OK** tlačítko.  
  
13. V **nástrojů**, rozbalte **pracovního postupu služby SharePoint** uzel a vyhledejte **LogToHistoryListActivity** aktivity.  
  
14. Přidejte tuto aktivitu do pracovního postupu pomocí jedné z následujících kroků:  
  
    -   Otevřete místní nabídku **LogToHistoryListActivity** aktivitu, zvolte **kopírování**, otevřete místní nabídku pro ostatní **Sem přetáhněte aktivity** oblasti v rámci **IfElseActivity1** v Návrháři pracovních postupů a klikněte na tlačítko **vložit**.  
  
    -   Přetáhněte **LogToHistoryListActivity** aktivita z **nástrojů**a umístěte ho na druhou **Sem přetáhněte aktivity** oblasti v rámci **IfElseActivity1** .  
  
## <a name="add-code-to-the-workflow"></a>Přidejte kód do pracovního postupu
 Dál přidejte kód do pracovního postupu pro ni funkce.  
  
#### <a name="to-add-code-to-the-workflow"></a>Přidání kódu do pracovního postupu  
  
1.  Otevřete místní nabídku **createTask1** aktivity v Návrháři postupu provádění a klikněte na tlačítko **zobrazit kód**.  
  
2.  Přidejte následující metodu:  
  
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
    >  V kódu, nahraďte `somedomain\\someuser` s doména a uživatelské jméno, pro kterou se vytvoří úkol, například "`Office\\JoeSch`". Pro účely testování je nejjednodušší na používání účtu, který vyvíjíte s.  
  
3.  Níže `MethodInvoking` metodu, přidejte v následujícím příkladu:  
  
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
  
4.  V Návrháři postupu provádění, zvolte **ifElseBranchActivity1** aktivity.  
  
5.  V **vlastnosti** okno, zvolte šipku rozevíracího seznamu **podmínku** vlastnost a poté nastavte *podmínka kódu* hodnotu.  
  
6.  Rozbalte **podmínku** vlastnost kliknutím na symbol plus (![TreeView plus](../sharepoint/media/plus.gif "TreeView plus")) vedle něj a pak nastavte jej na hodnotu *checkApprovalNeeded* .  
  
7.  V Návrháři postupu provádění, otevřete místní nabídku **logToHistoryListActivity1** aktivitu a klikněte na tlačítko **Generovat obslužné rutiny** vytvořit prázdnou metodu pro `MethodInvoking` událostí.  
  
8.  Nahradit `MethodInvoking` kód následujícím kódem:  
  
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
  
9. Zvolte **F5** klíč pro ladění programu.  
  
     Kompilaci aplikace, balíčky ho, ho nasadí, aktivuje jeho funkce, recykluje [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] fond aplikací a pak spustí prohlížeč v umístění zadané v **adresa Url webu** vlastnost.  
  
## <a name="associating-the-workflow-to-the-documents-list"></a>Přidružení pracovního postupu do seznam dokumentů
 V dalším kroku tím, že přidružíte pracovní postup s zobrazit formulář přidružení pracovního postupu **SharedDocuments** seznam na Sharepointovém webu.  
  
#### <a name="to-associate-the-workflow"></a>Pro přidružení pracovního postupu  
  
1.  Zvolte **sdílené dokumenty** odkaz na panelu Rychlé spuštění.  
  
2.  Zvolte **knihovny** odkaz na **nástroje knihovny** kartě a klikněte na tlačítko **nastavení knihovny** tlačítko na pásu karet.  
  
3.  V **oprávnění a správa** zvolte **nastavení pracovního postupu** propojit a klikněte na tlačítko **přidat pracovní postup** odkaz na **pracovníchpostupů** stránky.  
  
4.  V horním seznamu na stránce nastavení pracovního postupu, vyberte **ExpenseReport - Workflow1** šablony.  
  
5.  V další pole, zadejte **ExpenseReportWorkflow** a klikněte na tlačítko **Další** tlačítko.  
  
     To přiřadí pracovní postup s **sdílené dokumenty** seznamu a zobrazí formulář přidružení pracovního postupu.  
  
6.  V **Limit pro automatické schvalování** textové pole, zadejte **1200** a klikněte na tlačítko **přidružení pracovního postupu** tlačítko.  
  
## <a name="start-the-workflow"></a>Spuštění pracovního postupu
 V dalším kroku přidružení pracovního postupu k jednomu z dokumentů v **sdílené dokumenty** seznamu zobrazíte inicializační formulář pracovního postupu.  
  
#### <a name="to-start-the-workflow"></a>Spustit pracovní postup  
  
1.  Na stránce služby SharePoint, zvolte **Domů** tlačítko.  
  
2.  Zvolte **sdílené dokumenty** odkaz na panelu Rychlé spuštění zobrazíte **sdílené dokumenty** seznamu.  
  
3.  Zvolte **dokumenty** odkaz na **nástroje knihovny** kartě v horní části stránky a klikněte na tlačítko **uložit dokument** tlačítko na pásu karet a nahrát nový dokument do **Sdílené dokumenty** seznamu.  
  
4.  V **uložit dokument** dialogového okna zvolte **Procházet** tlačítko, vyberte libovolný soubor dokumentu, zvolte **otevřít** tlačítko a klikněte na tlačítko **OK** tlačítko.  
  
     Můžete změnit nastavení pro dokument v tomto dialogovém, ale ponechte jejich výchozí hodnoty výběrem **Uložit** tlačítko.  
  
5.  Zvolte odeslaný dokument, zvolte šipku rozevíracího seznamu, který se zobrazí a klikněte na tlačítko **pracovních postupů** položky.  
  
6.  Zvolte image vedle ExpenseReportWorkflow.  
  
     Zobrazí se inicializační formulář pracovního postupu. (Všimněte si, že hodnota zobrazena v **Limit pro automatické schvalování** pole je jen pro čtení, protože jste zadali v formulář přidružení.)  
  
7.  V **celkové výdaje** text zadejte **1600**a klikněte na tlačítko **spuštění pracovního postupu** tlačítko.  
  
     Zobrazí se **sdílené dokumenty** znovu. Nový sloupec s názvem **ExpenseReportWorkflow** s hodnotou **dokončeno** se přidá do položky jenom se spustil pracovního postupu.  
  
8.  Klikněte na šipku rozevíracího seznamu vedle nahraného dokumentu a klikněte na tlačítko **pracovních postupů** položky k zobrazení stavové stránce pracovního postupu. Zvolte **dokončeno** pod **dokončit pracovní postupy**. Úloha je uvedený v části **úlohy** oddílu.  
  
9. Zvolte název úlohy zobrazíte její podrobnosti úlohy.  
  
10. Přejděte zpět **SharedDocuments** seznamu a restartujte pomocí stejného dokumentu nebo jiný pracovní postup.  
  
11. Zadejte dobu, jakou se na zahájení stránce, která je menší než velikost zadaná na stránce přidružení (**1200**).  
  
     Pokud k tomu dojde, položky v seznamu historie vytvořil, a nikoli úkolu. Položka se zobrazí v **historie pracovního postupu** na stránce stavu pracovního postupu. Mějte na paměti tuto zprávu najdete v **výsledek** sloupec Historie událostí. Obsahuje text zadaný do `logToHistoryListActivity1.MethodInvoking` událost, která zahrnuje množství, která byla automaticky schválena.  
  
## <a name="next-steps"></a>Další kroky
 Další informace o tom, jak vytvořit pracovní postup šablony naleznete v těchto tématech:  
  
-   Další informace o pracovních postupech služby SharePoint, naleznete v tématu [pracovní postupy ve službě Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=166275).  
  
## <a name="see-also"></a>Viz také:
 [Vytváření řešení pracovního postupu služby SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Návod: Přidání stránky aplikace do pracovního postupu](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
