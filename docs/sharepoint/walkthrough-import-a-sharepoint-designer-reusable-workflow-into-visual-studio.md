---
title: 'Návod: import opakovaně použitelného pracovního postupu návrháře služby SharePoint | Microsoft Docs'
titleSuffix: ''
description: V tomto návodu naimportujete opakovaně použitelný pracovní postup vytvořený v Návrháři služby SharePoint do projektu pracovního postupu aplikace Visual Studio SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d4c12626550e36acc1a135258750f2d96ac5e81d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952587"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow"></a>Návod: import opakovaně použitelného pracovního postupu návrháře služby SharePoint

  Tento návod ukazuje, jak importovat opakovaně použitelný pracovní postup vytvořený v aplikaci SharePoint Designer 2010 do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu pracovního postupu služby SharePoint.

 Pracovní postupy vytvořené v Návrháři SharePoint nebo *deklarativní pracovní postupy* se skládají z [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] příkazů namísto kódu. SharePoint Designer 2010 představuje *opakovaně použitelné pracovní postupy*, které jsou přenosné a deklarativní pracovní postupy, které mohou být používány různými seznamy v sharepointových webech.

 Pracovní postupy vytvořené v nástroji [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] , jako jsou sekvenční a stavové pracovní postupy, se nazývají *pracovní postupy kódu*. Pracovní postupy kódu se skládají ze souborů XML a modulů kódu, ve kterých uživatelé mohou přizpůsobit chování pracovního postupu.

 Visual Studio umožňuje importovat znovu použitelné pracovní postupy vytvořené v aplikaci SharePoint Designer 2010 a převést je na pracovní postupy kódu pro použití na webech služby SharePoint.

 Tento názorný postup ukazuje následující úlohy:

- Vytvoření jednoduchého a opakovaně použitelného pracovního postupu v Návrháři služby SharePoint.

- Export opakovaně použitelného pracovního postupu aplikace SharePoint Designer do souboru *. wsp* a do služby SharePoint.

- Import souboru *. wsp* do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplikace pomocí projektu import opakovaně použitelného pracovního postupu.

- Změna pracovního postupu přidáním kódu.

- Použití importovaného pracovního postupu na webu služby SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- Podporované edice [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] a SharePoint.

- Visual Studio

- Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.

## <a name="create-target-sharepoint-subsites"></a>Vytvoření cílových podřízených webů SharePointu
 Nejprve vytvoříte dvě nové podřízené weby služby SharePoint: jeden pro hostování opakovaně použitelných pracovních postupů z návrháře služby SharePoint, druhý pro hostování převedených pracovních postupů.

#### <a name="to-create-sharepoint-subsites"></a>Vytvoření podřízených webů služby SharePoint

1. V aplikaci SharePoint Designer 2010 na panelu nabídek vyberte možnost **soubor**  >  **nový prázdný web**.

2. V dialogovém okně **nový prázdný web** vyberte web služby SharePoint, kde chcete vytvořit pracovní postup, nebo použijte hodnotu http://<em>System</em>/a pak klikněte na tlačítko **OK** .

    Zobrazí se Domovská stránka.

3. V části **dílčí weby** klikněte na tlačítko **Nový** .

4. V dialogovém okně **Nový** vyberte ze seznamu v levém podokně **šablony služby SharePoint** a v seznamu v pravém podokně vyberte možnost **tým webu** .

5. V poli **Zadejte umístění webového serveru** nahraďte v adrese URL **podlokalitu** aplikace Word řetězcem **SPD1** a poté klikněte na tlačítko **OK** .

    Tím se otevře nový podřízený web do SharePoint designeru. Zavřete tuto instanci aplikace SharePoint Designer a vraťte se k první instanci (lokalita nejvyšší úrovně).

6. Opakováním kroků 3-5 vytvořte druhý podřízený web, tentokrát nahraďte **dílčí lokalitu** aplikace Word v [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] **SPD2**.

## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Vytvoření opakovaně použitelného pracovního postupu návrháře služby SharePoint
 Protože SharePoint neobsahuje žádné opakovaně použitelné pracovní postupy, které můžete použít v tomto příkladu, budete ho vytvářet. V tomto jednoduchém pracovním postupu, když uživatel zadá nový úkol v seznamu úkolů, který má konkrétní název, je úkol přiřazen tomuto uživateli.

#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>Vytvoření opakovaně použitelného pracovního postupu aplikace SharePoint Designer

1. V části **podlokality** vyberte lokalitu **SPD1** , kterou chcete upravit.

2. Na pásu karet klikněte na tlačítko **opakovaně použitelný pracovní postup** .

     Zobrazí se Průvodce vytvořením použitelného pracovního postupu.

3. Do pole **název** zadejte **pracovní postup úlohy SPD**.

4. V seznamu **typ obsahu** zvolte možnost **úkol** a pak klikněte na tlačítko **OK** .

     Pracovní postup se otevře v Návrháři pracovních postupů návrháře služby SharePoint.

5. V Návrháři pracovních postupů zvolte krok 1 a pak na pásu karet klikněte na tlačítko **Podmínka** .

6. V seznamu podmínek vyberte, zda je **pole aktuální položka rovno hodnotě**.

     Tento krok přidá podmínku s názvem, **Pokud se pole rovná hodnotě**.

7. V části **Pokud se pole Pokud se rovná hodnotě** klikněte na odkaz **pole** .

8. V seznamu hodnot vyberte možnost **název**.

9. V části **Pokud se pole Pokud se rovná hodnotě** klikněte na odkaz **hodnota** .

10. Do pole zadejte **Nový úkol**.

     Příkaz Condition nyní čte, **Pokud je aktuální položka: title se rovná New Task**.

11. Zvolte řádek pod příkazem podmínka a pak na pásu karet klikněte na tlačítko **Akce** .

12. V seznamu akcí vyberte možnost **nastavit pole v části aktuální položka**.

13. V poli **nastavit pole na hodnotu** klikněte na odkaz **pole** a potom v seznamu vyberte možnost **přiřazeno**.

14. V akci **nastavit pole na hodnotu** klikněte na odkaz **hodnota** a potom v seznamu existujících uživatelů a skupin zvolte možnost **uživatel, který položku vytvořil**.

15. Klikněte na tlačítko **Přidat** a poté klikněte na tlačítko **OK** .

     Příkaz Action nyní čte **nastavení přiřazený pro aktuální položce: CreatedBy**.

## <a name="save-and-deploy-the-reusable-workflow"></a>Uložení a nasazení opakovaně použitelného pracovního postupu
 Vzhledem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] k tomu, že nástroj může importovat pouze soubory *. wsp* , je nutné uložit opakovaně použitelný pracovní postup jako soubor *. wsp* a nasadit jej do služby SharePoint před importem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

> [!IMPORTANT]
> Pokud se zobrazí chyba modulu runtime provedením následujícího postupu, je nutné provést postup v systému, který má přístup k webu služby SharePoint.

#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Uložení a nasazení opakovaně použitelného pracovního postupu

1. V horní části návrháře služby SharePoint klikněte na tlačítko **Uložit** a uložte svůj průběh. potom kliknutím na tlačítko **publikovat** nasaďte pracovní postup do webu služby **SPD1** SharePoint.

2. V navigačním podokně vyberte objekt **pracovní postupy** .

3. V části **opakovaně použitelný pracovní postup** vyberte možnost **pracovní postup úlohy SPD**.

4. Na pásu karet klikněte na tlačítko **Uložit jako šablonu** a uložte pracovní postup jako soubor *. wsp* .

5. Otevřete web služby SharePoint **SPD1** v prohlížeči a zobrazte soubor *. wsp* na SharePointu.

6. Na panelu Rychlé spuštění klikněte na odkaz **knihovny** .

7. V části **knihovny dokumentů** klikněte na odkaz **prostředky webu** .

     Soubor **pracovního postupu úlohy SPD** je uveden s dalšími prostředky webu.

8. V seznamu souborů vyberte název tohoto souboru.

9. V dialogovém okně **Stažení souboru** kliknutím na tlačítko **Uložit** uložte soubor *. wsp* do místního systému.

## <a name="import-the-wsp-file-into-visual-studio"></a>Import souboru. wsp do sady Visual Studio
 Importujte soubor *. wsp* do pomocí [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nástroje Import opakovaně použitelného projektu pracovního postupu. Tento projekt převede pracovní postup z opakovaně použitelného a deklarativního pracovního postupu na pracovní postup kódu. Po převedení pracovního postupu použijete kód pro úpravu jeho chování.

#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Import pracovního postupu ze souboru WSP a jeho úpravy

1. V aplikaci v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

2. V dialogovém okně **Nový projekt** rozbalte uzel **služby SharePoint** v rámci **jazyka Visual C#** nebo **Visual Basic** a pak vyberte uzel **2010** .

3. V podokně **šablony** vyberte šablonu **pracovního postupu importovat opakovaně použitelnou sadu SharePoint 2010** , ponechte název projektu jako **WorkflowImportProject1** a pak klikněte na tlačítko **OK** .

    Zobrazí se Průvodce přizpůsobením SharePointu.

4. Na stránce **Zadejte lokalitu a úroveň zabezpečení pro ladění** zadejte [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] pro druhý podřízený web služby SharePoint, který jste vytvořili dříve: http://<em>System Name</em>/SPD2.

5. V části **co je úroveň důvěryhodnosti pro toto řešení služby SharePoint?** zvolte možnost **nasadit jako řešení farmy** a pak klikněte na tlačítko **Další** .

    Další informace o izolovaném prostoru (sandbox) a řešeních farmy najdete v tématu [požadavky na řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).

6. Na stránce **zadat zdroj nového projektu** vyhledejte umístění v systému, kam jste dříve uložili soubor *. wsp* , otevřete soubor a klikněte na tlačítko **Další** .

   > [!NOTE]
   > Kliknutím na tlačítko **Dokončit** importujte všechny položky, které jsou k dispozici v souboru *. wsp* .

    Zobrazí se seznam opakovaně použitelných pracovních postupů, které jsou k importu k dispozici.

7. V poli **Vyberte položky, které chcete importovat** zvolte pracovní postup **pracovního postupu úlohy SPD** a pak klikněte na tlačítko **Dokončit** .

    Po dokončení operace importu se vytvoří projekt s názvem **WorkflowImportProject1** obsahující pracovní postup s názvem **SPD_Workflow_TestFT**. V této složce je soubor definice pracovního postupu *Elements.xml* a soubor návrháře pracovního postupu (*. XOML*). Návrhář obsahuje dva soubory: soubor pravidel (. Rules) a soubor kódu na pozadí (buď *. cs* nebo *. vb*, v závislosti na programovacím jazyku projektu).

8. V **Průzkumník řešení** odstraňte ostatní složky **importovaných souborů** .

9. V souboru *Elements.xml* odstraňte `InstantiationURL="_layouts/IniErkflIP.sspx"` .

10. V **Průzkumník řešení** zvolte **WorkflowImportProject1** a potom v řádku nabídek zvolte **projekt**  >  **sada jako spouštěný projekt** , abyste nastavili **WorkflowImportProject1** jako položku po spuštění.

     Tím se seznam zobrazuje hned po ladění projektu.

11. Vzhledem k tomu, že šablona **pracovního postupu importovat opakovaně 2010 použitelnou** šablonu neimportuje hodnoty vlastností přidružení pro importovaný pracovní postup, je nutné je zadat. Použijte následující postup:

    1. V **Průzkumník řešení** vyberte uzel **SPD_Workflow_TestFT** .

    2. Klikněte na tlačítko se třemi tečkami (![elipsa ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "Elipsa ASP.NET Mobile Designer")) vedle jedné z vlastností seznamu, jako je například vlastnost **cílový seznam** .

    3. V Průvodci přizpůsobením SharePointu vyplňte chybějící hodnoty a pak klikněte na tlačítko **Dokončit** .

12. Zvolte soubor. XOML a pak na panelu nabídek zvolte **Zobrazit**  >  **Návrhář** a zobrazte si importovaný pracovní postup v Návrháři postupu.

13. V uzlu **Windows Workflow v 3.0** sady **nástrojů** proveďte jeden z následujících kroků:

    - Otevřete místní nabídku aktivity **kódu** a pak zvolte možnost **Kopírovat**. V Návrháři pracovního postupu otevřete místní nabídku pro řádek pod aktivitou **SequenceActivity1** a pak zvolte **Vložit**.

    - Přetáhněte aktivitu **Code** ze **sady nástrojů** do návrháře pracovních postupů a připojte ji k řádku pod aktivitou **SequenceActivity1** .

      Tím se přidá aktivita do návrháře pracovních postupů s názvem **CodeActivity1**. V této aktivitě přidáte akci kódu, která vytvoří oznámení v seznamu oznámení, když uživatel spustí pracovní postup.

14. Proveďte jednu z následujících sad kroků:

    - Poklikejte na **CodeActivity1** pro vygenerování obslužné rutiny události a zobrazení kódu.

    - V okně **vlastnosti** pro **CodeActivity1** nastavte hodnotu vlastnosti **ExecuteCode** na **codeActivity_ExecuteCode**.

15. Do stávajících direktiv **using** nebo **importů** přidejte následující:

     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]

16. Nahraďte `codeActivity1_ExecuteCode` následujícím:

     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]

## <a name="deploy-the-project-and-associate-the-workflow"></a>Nasazení projektu a přidružení pracovního postupu
 V dalším kroku spusťte WorkflowImportProject1 a nasaďte ho na SharePointový web a pak přidružte pracovní postup k seznamu úkoly, abyste mohli zobrazit a otestovat upravený, převedený pracovní postup.

#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Nasazení projektu a přidružení pracovního postupu

1. V aplikaci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] klikněte na klávesu **F5** ke spuštění a nasazení převedeného projektu pracovního postupu.

2. Na panelu Rychlé spuštění klikněte na odkaz **úlohy** a zobrazte seznam úkoly.

3. Na kartě **Nástroje seznamu** klikněte na tlačítko **položky** a pak klikněte na tlačítko **Nová položka** .

     Otevře se dialogové okno **úkoly – nová položka** .

4. Do pole **název** zadejte **Nový úkol** a pak klikněte na tlačítko **Uložit** .

5. Na kartě **Nástroje seznamu** klikněte na tlačítko **seznam** a pak klikněte na tlačítko **seznam nastavení** .

     Zobrazí se stránka **Nastavení seznamu** .

6. V části **oprávnění a Správa** vyberte odkaz **Nastavení pracovního postupu** .

     Zobrazí se stránka **Nastavení pracovního postupu** .

7. Klikněte na odkaz **Přidat pracovní postup** .

8. V seznamu **pracovní postup** vyberte **test pracovního postupu WorkflowImportProject1-SPD**.

9. Do pole **název** zadejte **test pracovního postupu SPD** a pak klikněte na tlačítko **OK** .

10. Na panelu Rychlé spuštění vyberte seznam **úkoly** .

11. Zvolte šipku vedle možnosti **Nový úkol** a potom v seznamu zvolte **pracovní postupy**.

12. V části **zahájit nový pracovní postup** zvolte odkaz pro **test pracovního postupu SPD** a pak zvolte tlačítko **Start** pro zahájení pracovního postupu.

    > [!NOTE]
    > Případně můžete automaticky přidružit pracovní postup k seznamu spuštěním Průvodce nastavením pracovního postupu a nastavením pracovního postupu pro automatické přidružení.

     Všimněte si, že pracovní postup provede dvě akce: vaše jméno se zobrazí ve sloupci **přiřazený pro** úkolu a v seznamu **oznámení** se zobrazí oznámení.

## <a name="see-also"></a>Viz také
- [Import položek z existujícího webu služby SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Vytváření opakovaně použitelných ovládacích prvků pro webové části nebo stránky aplikací](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
