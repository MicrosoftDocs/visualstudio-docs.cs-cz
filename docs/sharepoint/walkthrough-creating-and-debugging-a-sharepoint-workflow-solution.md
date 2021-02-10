---
title: Vytvoření & ladění řešení pracovního postupu služby SharePoint
description: V tomto návodu vytvoříte a ladíte řešení pracovního postupu služby SharePoint. Vytvoří základní šablonu sekvenčního pracovního postupu. Vytváření aktivit pracovních postupů a zpracování událostí.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 637d46eaa9ac9306d63befed1c011c278b46af24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952717"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>Návod: vytvoření a ladění řešení pracovního postupu služby SharePoint
  Tento návod ukazuje, jak vytvořit šablonu základní sekvenční pracovní postup. Pracovní postup zkontroluje vlastnost sdílené knihovny dokumentů a určí, zda byl dokument zkontrolován. Pokud byl dokument revidován, pracovní postup se dokončí.

 Tento návod znázorňuje následující úlohy:

- Vytváření projektu sekvenčního pracovního postupu definice SharePointového seznamu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Vytváření aktivit pracovního postupu.

- Zpracování událostí aktivity pracovního postupu.

> [!NOTE]
> I když tento návod používá projekt sekvenčního pracovního postupu, je tento proces identický pro projekt pracovního postupu stavového stroje.
>
> Kromě toho může počítač v následujících pokynech zobrazit jiné názvy nebo umístění pro některé prvky uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice Microsoft Windows a SharePointu.

- Visual Studio

## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>Přidat vlastnosti do knihovny sdílených dokumentů SharePoint
 Chcete-li sledovat stav kontroly dokumentů v knihovně **sdílených dokumentů** , vytvoříme na webu služby SharePoint tři nové vlastnosti pro sdílené dokumenty:, a `Status` `Assignee` `Review Comments` . Tyto vlastnosti definujeme v knihovně **sdílených dokumentů** .

#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Přidání vlastností do knihovny sdílených dokumentů SharePoint

1. Ve webovém prohlížeči otevřete web služby SharePoint, například http:// \<system name> /SitePages/Home.aspx.

2. Na panelu Rychlé spuštění klikněte na **SharedDocuments**.

3. Zvolte **Knihovna** na pásu karet **nástroje knihovny** a pak kliknutím na tlačítko **vytvořit sloupec** na pásu karet vytvořte nový sloupec.

4. Pojmenujte sloupec **Document status**, nastavte jeho typ na **Choice (nabídka pro výběr)**, zadejte následující tři možnosti a pak klikněte na tlačítko **OK** :

    - **Nutná kontrola**

    - **Kontrola dokončena**

    - **Požadované změny**

5. Vytvořte dva další sloupce a pojmenujte je jako **pověřené** a podívejte se na **Komentáře**. Jako typ sloupce pro zmocnění zadejte jeden řádek textu a jako více řádků textu se zobrazí sloupec revidovat komentáře.

## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Povolit úpravy dokumentů bez nutnosti rezervace
 Šablonu pracovního postupu je snazší testovat, když můžete upravovat dokumenty, aniž byste je museli rezervovat. V dalším postupu nakonfigurujete web služby SharePoint tak, aby umožňoval.

#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Povolení úpravy dokumentů bez jejich rezervace

1. Na panelu Rychlé spuštění klikněte na odkaz **sdílené dokumenty** .

2. Na pásu karet **nástroje knihovny** klikněte na kartu **Knihovna** a potom kliknutím na tlačítko **Nastavení knihovny** zobrazte stránku **Nastavení knihovny dokumentů** .

3. V části **Obecné nastavení** klikněte na odkaz **Nastavení správy verzí** a zobrazte stránku **Nastavení správy verzí** .

4. Ověřte, že nastavení pro **vyžadování dokumentů, které mají být rezervovány, než bude možné upravovat** , je **ne**. Pokud není, změňte ho na **ne** a pak klikněte na tlačítko **OK** .

5. Zavřete prohlížeč.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Vytvoření projektu pro sekvenční pracovní postup SharePointu
 Sekvenční pracovní postup je sada kroků, které se spouští v pořadí až do dokončení poslední aktivity. V tomto postupu vytvoříme sekvenční pracovní postup, který bude platit pro náš seznam sdílených dokumentů. Průvodce pracovním postupem umožňuje přidružit pracovní postup k definici webu nebo k definici seznamu a umožňuje určit, kdy se má pracovní postup spustit.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Vytvoření projektu sekvenčního pracovního postupu SharePointu

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Na panelu nabídek vyberte možnost **soubor**  >  **Nový**  >  **projekt** . zobrazí se dialogové okno **Nový projekt** .

3. Rozbalte uzel **služby SharePoint** v rámci **jazyka Visual C#** nebo **Visual Basic** a pak vyberte uzel **2010** .

4. V podokně **šablony** vyberte šablonu **projektu SharePoint 2010** .

5. Do pole **název** zadejte **MySharePointWorkflow** a poté klikněte na tlačítko **OK** .

     Zobrazí se **Průvodce přizpůsobením SharePointu** .

6. Na stránce **Zadejte lokalitu a úroveň zabezpečení pro ladění** zvolte možnost **nasadit jako řešení farmy** a pak kliknutím na tlačítko **Dokončit** přijměte úroveň vztahu důvěryhodnosti a výchozí web.

     Tento krok nastaví úroveň důvěryhodnosti pro řešení jako řešení farmy, což je jediná dostupná možnost pro projekty pracovního postupu. Další informace najdete v tématu [požadavky na řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).

7. V **Průzkumník řešení** zvolte uzel projektu a potom v řádku nabídek zvolte **projekt**  >  **Přidat novou položku**.

8. V části **Visual C#** nebo **Visual Basic** rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

9. V podokně **šablony** zvolte šablonu **sekvenční pracovní postup (pouze řešení farmy)** a pak klikněte na tlačítko **Přidat** .

     Zobrazí se **Průvodce přizpůsobením SharePointu** .

10. Na stránce **Zadejte název pracovního postupu pro ladění** přijměte výchozí název (**MySharePointWorkflow-Workflow1**). Ponechte výchozí hodnotu typu šablony pracovního postupu, **vypsat pracovní postup** a pak klikněte na tlačítko **Další** .

11. V chcete, aby **aplikace Visual Studio automaticky přidružil pracovní postup na stránce relace ladění?** kliknutím na tlačítko **Další** potvrďte všechna výchozí nastavení.

     Tento krok automaticky přidružuje pracovní postup k knihovně sdílených dokumentů.

12. Na stránce **Zadejte podmínky, jak se má pracovní postup** spustit, ponechte vybrané výchozí možnosti v části **jak chcete, aby se pracovní postup spouštěl?** a klikněte na tlačítko **Dokončit** .

     Tato stránka umožňuje určit, kdy se má pracovní postup spustit. Ve výchozím nastavení se pracovní postup spouští buď když ho uživatel ručně spustí na SharePointu, nebo když se vytvoří položka, ke které je přidružený pracovní postup.

## <a name="create-workflow-activities"></a>Vytváření aktivit pracovního postupu
 Pracovní postupy obsahují jednu nebo více *aktivit* , které reprezentují akce, které je potřeba provést. Pomocí návrháře pracovních postupů uspořádejte aktivity pracovního postupu. V tomto postupu přidáme do pracovního postupu dvě aktivity: Aktivita typu HandleExternalEventActivity a OnWorkFlowItemChanged. Tyto aktivity sledují stav revize dokumentů v seznamu **sdílených dokumentů** .

#### <a name="to-create-workflow-activities"></a>Vytvoření aktivit pracovního postupu

1. Pracovní postup by se měl zobrazit v Návrháři pracovních postupů. Pokud není, otevřete buď **Workflow1.cs** nebo **Workflow1. vb** v **Průzkumník řešení**.

2. V návrháři vyberte aktivitu **onWorkflowActivated1** .

3. V okně **vlastnosti** zadejte do pole **vyvolaná** vlastnost **onWorkflowActivated** a pak zvolte klávesu ENTER.

     Otevře se Editor kódu a do souboru kódu Workflow1 se přidá metoda obslužné rutiny události s názvem onWorkflowActivated.

4. Přepněte zpět do návrháře pracovních postupů, otevřete sadu nástrojů a potom rozbalte uzel **Windows Workflow v 3.0** .

5. V uzlu **Windows Workflow v 3.0** sady **nástrojů** proveďte jednu z následujících sad kroků:

    1. Otevřete místní nabídku aktivity **while** a zvolte možnost **Kopírovat**. V Návrháři pracovního postupu otevřete místní nabídku pro řádek pod aktivitou **onWorkflowActivated1** a pak zvolte **Vložit**.

    2. Přetáhněte aktivitu **while** ze **sady nástrojů** do návrháře pracovních postupů a propojte aktivitu s řádkem pod aktivitou **onWorkflowActivated1** .

6. Vyberte aktivitu **whileActivity1** .

7. V okně **vlastnosti** nastavte **Podmínka** na stav kódu.

8. Rozbalte vlastnost **Podmínka** , jako vlastnost **podmínky** podřízeného objektu zadejte **isWorkflowPending** a pak zvolte klávesu ENTER.

     Otevře se Editor kódu a do souboru kódu Workflow1 se přidá metoda s názvem isWorkflowPending.

9. Přepněte zpět do návrháře pracovních postupů, otevřete sadu nástrojů a potom rozbalte uzel **pracovní postup služby SharePoint** .

10. V uzlu **pracovní postup služby SharePoint** v **sadě nástrojů** proveďte jednu z následujících sad kroků:

    - Otevřete místní nabídku aktivity **onWorkflowItemChanged** a pak zvolte možnost **Kopírovat**. V Návrháři pracovního postupu otevřete místní nabídku pro řádek uvnitř aktivity **whileActivity1** a pak zvolte **Vložit**.

    - Přetáhněte aktivitu **onWorkflowItemChanged** ze **sady nástrojů** do návrháře pracovních postupů a propojte aktivitu s řádkem v rámci aktivity **whileActivity1** .

11. Vyberte aktivitu **onWorkflowItemChanged1** .

12. V okně **vlastnosti** nastavte vlastnosti tak, jak je uvedeno v následující tabulce.

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**CorrelationToken**|**workflowToken**|
    |**Vyvolána**|**onWorkflowItemChanged**|

## <a name="handle-activity-events"></a>Zpracování událostí aktivity
 Nakonec ověřte stav dokumentu z každé aktivity. Pokud byl dokument zkontrolován, je pracovní postup dokončen.

#### <a name="to-handle-activity-events"></a>Zpracování událostí aktivity

1. V *Workflow1.cs* nebo *Workflow1. vb* přidejte následující pole do horní části `Workflow1` třídy. Toto pole se používá v aktivitě k určení, zda byl pracovní postup dokončen.

    ```vb
    Dim workflowPending As Boolean = True
    ```

    ```csharp
    Boolean workflowPending = true;
    ```

2. Do třídy přidejte následující metodu `Workflow1` . Tato metoda kontroluje hodnotu `Document Status` Vlastnosti seznamu dokumentů, aby bylo možné zjistit, zda byl dokument zkontrolován. Pokud `Document Status` je vlastnost nastavena na `Review Complete` , pak `checkStatus` Metoda nastaví `workflowPending` pole na **hodnotu false** , aby označovala, že pracovní postup je připravený k dokončení.

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

3. Přidejte následující kód do `onWorkflowActivated` `onWorkflowItemChanged` metody a pro volání `checkStatus` metody. Při spuštění pracovního postupu `onWorkflowActivated` metoda volá `checkStatus` metodu k určení, zda byl dokument již revidován. Pokud nebyl revidován, pracovní postup pokračuje. Při uložení dokumentu `onWorkflowItemChanged` metoda volá `checkStatus` metodu znovu a určí, zda byl dokument zkontrolován. Když `workflowPending` je pole nastaveno na **hodnotu true**, pracovní postup bude nadále spuštěn.

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

4. Přidejte následující kód do `isWorkflowPending` metody pro kontrolu stavu `workflowPending` Vlastnosti. Pokaždé, když se dokument uloží, aktivita **whileActivity1** zavolá `isWorkflowPending` metodu. Tato metoda prověřuje <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> vlastnost <xref:System.Workflow.Activities.ConditionalEventArgs> objektu a určí, zda má aktivita **whileActivity1** pokračovat nebo dokončit. Pokud je vlastnost nastavena na **hodnotu true**, aktivita pokračuje. V opačném případě se aktivita dokončí a pracovní postup se dokončí.

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

5. Uložte projekt.

## <a name="test-the-sharepoint-workflow-template"></a>Testování šablony pracovního postupu služby SharePoint
 Když spustíte ladicí program, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nasadí šablonu pracovního postupu na server SharePoint a přidruží pracovní postup k seznamu **sdílené dokumenty** . Chcete-li otestovat pracovní postup, spusťte instanci pracovního postupu z dokumentu v seznamu **sdílené dokumenty** .

#### <a name="to-test-the-sharepoint-workflow-template"></a>Testování šablony pracovního postupu služby SharePoint

1. V *Workflow1.cs* nebo *Workflow1. vb* nastavte zarážku vedle metody **onWorkflowActivated** .

2. Klikněte na klávesu **F5** a sestavte a spusťte řešení.

     Zobrazí se stránka SharePoint.

3. V navigačním podokně služby SharePoint klikněte na odkaz **sdílené dokumenty** .

4. Na stránce **sdílené dokumenty** klikněte na odkaz **dokumenty** na kartě **nástroje knihovny** a pak klikněte na tlačítko **Nahrát dokument** .

5. V dialogovém okně **Nahrát dokument** klikněte na tlačítko **Procházet** , zvolte libovolný soubor dokumentu, klikněte na tlačítko **otevřít** a pak klikněte na tlačítko **OK** .

     Tím se vybraný dokument nahraje do seznamu **sdílené dokumenty** a spustí se pracovní postup.

6. V nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ověřte, zda ladicí program zastaví na zarážce vedle `onWorkflowActivated` metody.

7. Pro pokračování v provádění klikněte na klávesu **F5** .

8. Nastavení dokumentu můžete změnit tady, ale ponechte výchozí hodnoty nyní, a to tak, že kliknete na tlačítko **Uložit** .

     Tím se vrátíte na stránku **sdílené dokumenty** na výchozím webu služby SharePoint.

9. Na stránce **sdílené dokumenty** ověřte, zda je hodnota pod sloupcem **MySharePointWorkflow-Workflow1** nastavena na hodnotu probíhá **.** To znamená, že pracovní postup probíhá a že dokument čeká na revizi.

10. Na stránce **sdílené dokumenty** zvolte dokument, zvolte šipku, která se zobrazí, a pak zvolte položku nabídky **Upravit vlastnosti** .

11. Nastavte **stav dokumentu** na **zkontrolovat dokončeno** a pak klikněte na tlačítko **Uložit** .

     Tím se vrátíte na stránku **sdílené dokumenty** na výchozím webu služby SharePoint.

12. Na stránce **sdílené dokumenty** ověřte, zda je hodnota pod sloupcem **stav dokumentu** nastavena na hodnotu **zkontrolovat dokončeno**. Aktualizujte stránku **sdílené dokumenty** a ověřte, že hodnota pod sloupcem **MySharePointWorkflow-Workflow1** je nastavená na **dokončeno**. To znamená, že pracovní postup je dokončen a že dokument byl zkontrolován.

## <a name="next-steps"></a>Další kroky
 Další informace o tom, jak vytvořit šablony pracovního postupu, najdete v těchto tématech:

- Další informace o aktivitách pracovního postupu služby SharePoint naleznete v tématu [aktivity pracovního postupu pro službu SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

- Další informace o aktivitách programovací model Windows Workflow Foundation najdete v tématu [obor názvů System. Workflow. Activities](/dotnet/api/system.windows.media.color).

## <a name="see-also"></a>Viz také
- [Vytváření řešení pracovního postupu služby SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Šablony projektů a položek projektu služby SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md)
- [Sestavování a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
