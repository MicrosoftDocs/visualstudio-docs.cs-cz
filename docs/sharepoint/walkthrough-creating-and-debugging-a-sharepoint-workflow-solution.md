---
title: 'Návod: Vytváření a ladění řešení pracovního postupu služby SharePoint | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c254f6f3e044f938ed2749567d66ee7a313081e7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42626485"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>Návod: Vytváření a ladění řešení pracovního postupu služby SharePoint
  Tento návod ukazuje, jak vytvořit šablonu základního sekvenčního pracovního postupu. Pracovní postup kontroluje vlastnosti knihovny dokumentů sdílené k určení, zda byly zkontrolovány dokumentu. Pokud byly zkontrolovány dokumentu, dokončení pracovního postupu.  
  
 Tento návod znázorňuje následující úlohy:  
  
-   Vytvoření projektu sekvenční pracovní postup definice seznamu služby SharePoint v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Vytváření aktivit pracovního postupu.  
  
-   Zpracování události aktivit pracovního postupu.  
  
> [!NOTE]  
>  I když tento návod používá projekt sekvenčního pracovního postupu, proces je stejný jako pro projekt stavu počítače pracovního postupu.  
>   
>  Také váš počítač může zobrazit jiné názvy nebo umístění pro některé uživatele sady Visual Studio prvky rozhraní v následujících pokynech. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Podporované vydání systému Microsoft Windows a SharePoint.  
  
-   Visual Studio.  
  
## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>Přidání vlastnosti do knihovny SharePoint sdílené dokumenty
 Ke sledování stavu revize dokumentů v **sdílené dokumenty** knihovny, vytvoříme tři nové vlastnosti u sdílených dokumentů na našem webu služby SharePoint: `Status`, `Assignee`, a `Review Comments`. Jsme definovali v těchto vlastností **sdílené dokumenty** knihovny.  
  
#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Přidání vlastnosti do Sharepointu sdílené dokumenty knihovny  
  
1.  Otevřete web Sharepointu, třeba http://\<systémový název > / SitePages/Home.aspx ve webovém prohlížeči.  
  
2.  Na panelu Rychlé spuštění zvolte **SharedDocuments**.  
  
3.  Zvolte **knihovny** na **nástroje knihovny** pásu karet a klikněte na tlačítko **vytvořit sloupec** tlačítko na pásu karet a vytvoří nový sloupec.  
  
4.  Název sloupce **stav dokumentu**, nastavte její typ na **volba (nabídka)**, zadejte následující tři možnosti a klikněte na tlačítko **OK** tlačítka:  
  
    -   **Musí se provést kontrola**  
  
    -   **Dokončení kontroly**  
  
    -   **Požadované změny**  
  
5.  Vytvořte další dva sloupce a pojmenujte je **pověřené osoby** a **komentáře k revizi**. Typ pověřené osoby sloupec jako jeden řádek textu a typ sloupce komentáře k revizi nastavte jako více řádků textu.  
  
## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Povolit dokumenty upravovat bez nutnosti rezervaci
 Je snazší testování šablony pracovního postupu, když upravíte dokumenty bez nutnosti nerezervujete. V dalším postupu konfigurace webu služby SharePoint, která umožňuje.  
  
#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Chcete-li povolit dokumenty upravovat bez jejich registrace  
  
1.  Na panelu Rychlé spuštění zvolte **sdílené dokumenty** odkaz.  
  
2.  Na **nástroje knihovny** pásu karet, zvolte **knihovny** kartu a klikněte na tlačítko **nastavení knihovny** tlačítka pro zobrazení **nastavení knihovny dokumentů** stránky.  
  
3.  V **obecné nastavení** zvolte **nastavení správy verzí** odkazu zobrazíte **nastavení správy verzí** stránky.  
  
4.  Ověřte, že nastavení **dokumenty, které se před provedením úpravy mohou vyžadovat** je **ne**. Pokud není, změňte ho na **ne** a klikněte na tlačítko **OK** tlačítko.  
  
5.  Zavřete prohlížeč.  
  
## <a name="create-a-sharepoint-sequential-workflow-project"></a>Vytvoření projektu sekvenčního pracovního postupu služby SharePoint
 Sekvenční pracovní postup je sadu kroků, které provádí v pořadí, dokud se nedokončí poslední aktivita. V tomto postupu vytvoříme sekvenční pracovní postup, který se bude vztahovat na našem seznamu Sdílené dokumenty. Pracovní postup Průvodce umožňuje přidružit definice webu nebo seznamu definice pracovního postupu a umožňuje určit, kdy se spustí pracovní postup.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Chcete-li vytvořit projekt sekvenčního pracovního postupu služby SharePoint  
  
1.  Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  V panelu nabídky zvolte **souboru** > **nový** > **projektu** zobrazíte **nový projekt** dialogové okno.  
  
3.  Rozbalte **SharePoint** uzlu buď **Visual C#** nebo **jazyka Visual Basic**a klikněte na tlačítko **2010** uzlu.  
  
4.  V **šablony** podokně, vyberte **projektu služby SharePoint 2010** šablony.  
  
5.  V **název** zadejte **MySharePointWorkflow** a klikněte na tlačítko **OK** tlačítko.  
  
     **Průvodce přizpůsobením SharePoint** se zobrazí.  
  
6.  V **zadejte web a úroveň zabezpečení pro ladění** zvolte **nasadit jako řešení farmy** přepínač a klikněte na tlačítko **Dokončit** tlačítko tak, aby přijímal vztah důvěryhodnosti úroveň a výchozí web.  
  
     Tento krok nastaví úroveň důvěryhodnosti řešení jako řešení farmy, jediná dostupná možnost pro projekty pracovního postupu. Další informace najdete v tématu [aspekty řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  V **Průzkumníka řešení**, zvolte uzel projektu a pak na panelu nabídek zvolte **projektu** > **přidat novou položku**.  
  
8.  V části **Visual C#** nebo **jazyka Visual Basic**, rozbalte **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.  
  
9. V **šablony** podokně, vyberte **sekvenčního pracovního postupu (pouze řešení farmy)** šablony a klikněte na tlačítko **přidat** tlačítko.  
  
     **Průvodce přizpůsobením SharePoint** se zobrazí.  
  
10. V **zadejte název pracovního postupu pro ladění** stránce, přijměte výchozí název (**MySharePointWorkflow - Workflow1**). Ponechte výchozí pracovní postup šablony typu hodnotu **pracovní postup seznamu**a klikněte na tlačítko **Další** tlačítko.  
  
11. V **přejete si Visual Studio automaticky přidružovala pracovní postup v ladicí relaci?** zvolte **Další** tlačítko přijměte všechna výchozí nastavení.  
  
     Tento krok automaticky přidruží pracovní postup s knihovnou sdílené dokumenty.  
  
12. V **zadat podmínky spuštění pracovního postupu** ponechte výchozí možnosti vybrané v **jak chcete pracovní postup spustit?** části a zvolte **Dokončit** tlačítko.  
  
     Na této stránce můžete zadat při spuštění pracovního postupu. Ve výchozím nastavení spustí pracovní postup buď když uživatel ručně spustí v Sharepointu nebo když je vytvořena položka ke kterému je přidružené pracovní postup.  
  
## <a name="create-workflow-activities"></a>Vytvoření aktivity pracovního postupu
 Pracovní postupy obsahují jeden nebo více *aktivity* , které představují akce k provedení. Pomocí návrháře postupu provádění můžete uspořádat aktivity pracovního postupu. V tomto postupu přidáme dvě aktivity do pracovního postupu: Aktivita typu HandleExternalEventActivity a OnWorkFlowItemChanged. Tyto aktivity monitorování stavu revize dokumentů v **sdílené dokumenty** seznamu  
  
#### <a name="to-create-workflow-activities"></a>K vytváření aktivit pracovního postupu  
  
1.  Pracovní postup má být zobrazena v Návrháři pracovních postupů. Pokud není, pak otevřete **Workflow1.cs** nebo **Workflow1.vb** v **Průzkumníka řešení**.  
  
2.  V návrháři, zvolte **OnWorkflowActivated1** aktivity.  
  
3.  V **vlastnosti** okno, zadejte **onWorkflowActivated** vedle **vyvolaný** vlastnost a potom stiskněte klávesu Enter.  
  
     Otevře se Editor kódu a metoda obslužné rutiny události s názvem onWorkflowActivated se přidá do souboru kódu Workflow1.  
  
4.  Přepněte zpět do návrháře postupu provádění, otevřete sadu nástrojů a potom rozbalte **pracovního postupu Windows v3.0** uzlu.  
  
5.  V **pracovního postupu Windows v3.0** uzlu **nástrojů**, proveďte jednu z následujících sad kroků:  
  
    1.  Otevřete místní nabídku **při** aktivitu a klikněte na tlačítko **kopírování**. V Návrháři postupu provádění, otevřete místní nabídku pro řádek u **onWorkflowActivated1** aktivitu a klikněte na tlačítko **vložit**.  
  
    2.  Přetáhněte **při** aktivita z **nástrojů** do Návrháře pracovního postupu a připojte se k řádku v rámci aktivity **onWorkflowActivated1** aktivity.  
  
6.  Zvolte **WhileActivity1** aktivity.  
  
7.  V **vlastnosti** okno, nastavte **podmínku** do kódu podmínky.  
  
8.  Rozbalte **podmínku** vlastnost, zadejte **isWorkflowPending** vedle podřízené **podmínku** vlastnost a potom stiskněte klávesu Enter.  
  
     Otevře se Editor kódu a metodu s názvem isWorkflowPending se přidá do souboru kódu Workflow1.  
  
9. Přepněte zpět do návrháře postupu provádění, otevřete sadu nástrojů a potom rozbalte **pracovního postupu služby SharePoint** uzlu.  
  
10. V **pracovního postupu služby SharePoint** uzlu **nástrojů**, proveďte jednu z následujících sad kroků:  
  
    -   Otevřete místní nabídku **OnWorkflowItemChanged** aktivitu a klikněte na tlačítko **kopírování**. V Návrháři postupu provádění, otevřete místní nabídku pro řádek uvnitř **whileActivity1** aktivitu a klikněte na tlačítko **vložit**.  
  
    -   Přetáhněte **OnWorkflowItemChanged** aktivita z **nástrojů** do Návrháře pracovního postupu a připojte se k řádku uvnitř aktivity **whileActivity1** aktivity.  
  
11. Zvolte **onWorkflowItemChanged1** aktivity.  
  
12. V **vlastnosti** okno, nastavte vlastnosti, jak je znázorněno v následující tabulce.  
  
    |Vlastnost|Hodnota|  
    |--------------|-----------|  
    |**CorrelationToken**|**workflowToken**|  
    |**Vyvolání**|**onWorkflowItemChanged**|  
  
## <a name="handle-activity-events"></a>Zpracování události aktivit
 Nakonec zkontrolujte stav dokumentu z každé aktivity. Pokud byly zkontrolovány dokumentu, je dokončení pracovního postupu.  
  
#### <a name="to-handle-activity-events"></a>Zpracování událostí aktivit  
  
1.  V *Workflow1.cs* nebo *Workflow1.vb*, přidejte následující pole do horní části `Workflow1` třídy. Toto pole se používá v nějaké aktivitě k určení, zda je pracovní postup byl dokončen.  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  Přidejte následující metodu do `Workflow1` třídy. Tato metoda zkontroluje hodnotu vlastnosti `Document Status` vlastnost seznamu dokumenty k určení, zda byly zkontrolovány dokumentu. Pokud `Document Status` je nastavena na `Review Complete`, pak bude `checkStatus` metody nastaví `workflowPending` pole **false** k označení, že je připravený na dokončení pracovního postupu.  
  
    ```vb  
    Private Sub checkStatus()  
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then  
            workflowPending = False  
        End If  
    End Sub   
    ```  
  
    ```csharp  
    private void checkStatus()  
    {  
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")  
        workflowPending = false;  
    }  
    ```  
  
3.  Přidejte následující kód, který `onWorkflowActivated` a `onWorkflowItemChanged` metod k volání `checkStatus` metody. Při spuštění pracovního postupu, `onWorkflowActivated` volání metod `checkStatus` metodou ke zjištění, zda již byly zkontrolovány dokumentu. Pokud nebyl byly zkontrolovány, pracovní postup pokračuje. Když je dokument uložen, `onWorkflowItemChanged` volání metod `checkStatus` metodou znovu ke zjištění, zda byly zkontrolovány dokumentu. Zatímco `workflowPending` je nastaveno na **true**, pracovní postup i nadále běžel.  
  
    ```vb  
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
  
    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
    ```  
  
    ```csharp  
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
  
    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
    ```  
  
4.  Přidejte následující kód, který `isWorkflowPending` metodu ke kontrole stavu `workflowPending` vlastnost. Pokaždé, když je dokument uložen, **whileActivity1** volání aktivity `isWorkflowPending` metody. Tato metoda prověří <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> vlastnost <xref:System.Workflow.Activities.ConditionalEventArgs> objektem pro určení, zda **WhileActivity1** by měl pokračovat nebo dokončení aktivity. Pokud je nastavena na **true**, aktivita bude pokračovat. Jinak aktivita dokončí a dokončení pracovního postupu.  
  
    ```vb  
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)  
        e.Result = workflowPending  
    End Sub  
    ```  
  
    ```csharp  
    private void isWorkflowPending(object sender, ConditionalEventArgs e)  
    {  
        e.Result = workflowPending;  
    }  
    ```  
  
5.  Uložte projekt.  
  
## <a name="test-the-sharepoint-workflow-template"></a>Test šablony pracovního postupu služby SharePoint
 Když spustíte ladicí program, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nasadí šablony pracovního postupu na server SharePoint a přidruží pracovní postup s **sdílené dokumenty** seznamu. K testování pracovního postupu, spuštění instance pracovního postupu z dokumentu **sdílené dokumenty** seznamu.  
  
#### <a name="to-test-the-sharepoint-workflow-template"></a>K otestování šablony pracovního postupu služby SharePoint  
  
1.  V *Workflow1.cs* nebo *Workflow1.vb*, nastavte zarážku vedle **onWorkflowActivated** metody.  
  
2.  Zvolte **F5** klíče pro sestavení a spuštění řešení.  
  
     Zobrazí se web služby SharePoint.  
  
3.  V navigačním podokně na Sharepointu, zvolte **sdílené dokumenty** odkaz.  
  
4.  V **sdílené dokumenty** zvolte **dokumenty** odkaz na **nástroje knihovny** kartu a klikněte na tlačítko **uložit dokument** tlačítko .  
  
5.  V **uložit dokument** dialogového okna zvolte **Procházet** tlačítko, vyberte libovolný soubor dokumentu, zvolte **otevřít** tlačítko a klikněte na tlačítko **OK** tlačítko.  
  
     To nahraje vybraný dokument do **sdílené dokumenty** seznam a spustí pracovní postup.  
  
6.  V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ověřte, že ladicí program zastaví na zarážce vedle `onWorkflowActivated` metody.  
  
7.  Zvolte **F5** klíč pro pokračování v provádění.  
  
8.  Můžete změnit nastavení pro dokument tady ale ponechte jejich výchozí hodnoty prozatím výběrem **Uložit** tlačítko.  
  
     Tím se vrátíte do **sdílené dokumenty** stránky výchozího webu služby SharePoint.  
  
9. V **sdílené dokumenty** stránce ověřte, jestli hodnota pod **MySharePointWorkflow - Workflow1** sloupec je nastaven na **probíhá**. To znamená, že pracovní postup probíhá a že dokumentu čeká na revizi.  
  
10. V **sdílené dokumenty** stránce vyberte dokumentu, vyberte šipku, která se zobrazí a klikněte na tlačítko **upravit vlastnosti** položky nabídky.  
  
11. Nastavte **stav dokumentu** k **revize kompletní**a klikněte na tlačítko **Uložit** tlačítko.  
  
     Tím se vrátíte do **sdílené dokumenty** stránky výchozího webu služby SharePoint.  
  
12. V **sdílené dokumenty** stránce ověřte, jestli hodnota pod **stav dokumentu** sloupec je nastaven na **revize kompletní**. Aktualizovat **sdílené dokumenty** stránky a ověřte, že hodnota pod **MySharePointWorkflow - Workflow1** sloupec je nastaven na **dokončeno**. Znamená to, že dokončení pracovního postupu a revidovaný dokumentu.  
  
## <a name="next-steps"></a>Další kroky
 Další informace o tom, jak vytvořit pracovní postup šablony naleznete v těchto tématech:  
  
-   Další informace o aktivitách pracovního postupu služby SharePoint, naleznete v tématu [aktivity pracovních postupů pro službu SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=178992).  
  
-   Další informace o aktivitách Windows Workflow Foundation, najdete v článku [System.Workflow.Activities Namespace](http://go.microsoft.com/fwlink/?LinkId=178993).  
  
## <a name="see-also"></a>Viz také:
 [Vytváření řešení pracovního postupu služby SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [A šablony položek projektu služby SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [Sestavování a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
