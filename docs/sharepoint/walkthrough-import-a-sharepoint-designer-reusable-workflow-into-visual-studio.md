---
title: 'Návod: Import opakovaně použitelného pracovního postupu návrháře služby SharePoint do sady Visual Studio | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 249799bc9daf13992bd9fe03dff8c86263f91263
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851475"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>Návod: Importujte opakovaně použitelného pracovního postupu návrháře služby SharePoint do sady Visual Studio
  Tento návod ukazuje, jak pro import opakovaně použitelného pracovního postupu v Návrháři SharePoint 2010 do vytvoří [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu pracovního postupu služby SharePoint.  
  
 Pracovní postupy vytvořené v aplikaci SharePoint Designer nebo *deklarativní pracovních postupů*, obsahovat [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] příkazy namísto kódu. Zavádí SharePoint Designer 2010 *opakovaně použitelných pracovních postupů*, které jsou přenosná deklarativní pracovní postupy, které můžete používat různé seznamy na webech služby SharePoint.  
  
 Pracovní postupy vytvořené v [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], jako jsou pracovní postupy stroje sekvenční federace a jednotlivých států, se nazývají *kódu pracovních postupů*. Pracovní postupy kódu obsahovat soubory XML a kódové moduly, ve kterých mohou uživatelé přizpůsobit chování pracovního postupu.  
  
 Visual Studio umožňuje import opakovaně použitelných pracovních postupů, které jsou vytvořené v Návrháři SharePoint 2010 a převede je do pracovních postupů kód pro použití v Sharepointové weby.  
  
 Tento návod demonstruje následující úkoly:  
  
- Vytvoření jednoduché, opakovaně použitelný pracovní postup v SharePoint designeru.  
  
- Export opakovaně použitelného pracovního postupu návrháře služby SharePoint k *.wsp* soubor a do služby SharePoint.  
  
- Import *.wsp* soubor do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pomocí aplikace project Import opakovaně použitelných pracovních postupů.  
  
- Změna pracovního postupu přidáním kódu.  
  
- Pomocí importovaných pracovních postupů na Sharepointovém webu.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   Podporované edice systému [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] a SharePoint.  
  
-   Visual Studio.  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.  
  
## <a name="create-target-sharepoint-subsites"></a>Vytvoření cílových podřízených webů SharePoint
 Nejprve vytvořit dvě nové podřízené weby služby SharePoint: jeden pro hostování opakovaně použitelných pracovních postupů z Návrháře služby SharePoint, další k hostování převedené pracovní postupy.  
  
#### <a name="to-create-sharepoint-subsites"></a>Vytvoření podřízených webů služby SharePoint  
  
1. V Návrháři SharePoint 2010, na panelu nabídek zvolte **souboru** > **nového prázdného webu**.  
  
2. V **nového prázdného webu** dialogové okno, přejděte na web služby SharePoint, ve kterém chcete vytvořit pracovní postup, nebo použijte hodnotu http://<em>SystemName</em>/ a klikněte na tlačítko **OK** tlačítko.  
  
    Na domovské stránce se zobrazí.  
  
3. V **podřízené lokality** zvolte **nový** tlačítko.  
  
4. V **nový** dialogového okna zvolte **šablon služby SharePoint** ze seznamu v levém podokně a zvolte **týmový web** ze seznamu v pravém podokně.  
  
5. V **zadejte umístění webu** pole, nahraďte slovo **podřízeného webu** v adrese URL s **SPD1**a klikněte na tlačítko **OK** tlačítko.  
  
    Otevře se nové podřízené lokality do návrháře služby SharePoint. Zavřete tuto instanci aplikace SharePoint Designer a vraťte se k první instanci (lokality nejvyšší úrovně).  
  
6. Zopakujte kroky 3 až 5 vytvořte druhý podřízený web, tentokrát nahrazující slovo **podřízeného webu** v [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] s **SPD2**.  
  
## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Vytvoření opakovaně použitelného pracovního postupu návrháře služby SharePoint
 Protože SharePoint neobsahuje opakovaně použitelných pracovních postupů, které můžete použít v tomto příkladu, můžete ho vytvoří. V tomto jednoduchý pracovní postup když uživatel zadá nový úkol v seznamu úkolů, která má konkrétní softwarový úloha je přiřazená tomuto uživateli.  
  
#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>Vytvoření opakovaně použitelného pracovního postupu aplikace SharePoint Designer
  
1.  V **podřízené lokality** zvolte **SPD1** lokality jej upravit.  
  
2.  Na pásu karet, zvolte **opakovaně použitelných pracovních postupů** tlačítko.  
  
     Zobrazí se průvodce vytvořit opakovaně použitelných pracovních postupů.  
  
3.  V **název** zadejte **pracovního postupu úloh SPD**.  
  
4.  V **typ obsahu** klikněte na položku **úloh**a klikněte na tlačítko **OK** tlačítko.  
  
     Pracovní postup se otevře v Návrháři pracovního postupu návrháře služby SharePoint.  
  
5.  V Návrháři postupu provádění, zvolte krok 1 a pak na pásu karet, zvolte **podmínku** tlačítko.  
  
6.  V seznamu podmínek, vyberte **Pokud pole aktuální položky rovná hodnotě**.  
  
     Tento krok přidává podmínku, která má název **Pokud pole se rovná hodnotě**.  
  
7.  V **Pokud pole se rovná hodnotě** podmínky, zvolte **pole** odkaz.  
  
8.  V seznamu hodnot, zvolte **Title**.  
  
9. V **Pokud pole se rovná hodnotě** podmínky, zvolte **hodnotu** odkaz.  
  
10. V dialogovém okně zadejte **nový úkol**.  
  
     Načte příkaz podmínky **Pokud aktuální položky: název rovná se nový úkol**.  
  
11. Zvolte řádek pod příkaz podmínky a pak na pásu karet, zvolte **akce** tlačítko.  
  
12. V seznamu akcí vyberte **sadu pole v aktuální položce**.  
  
13. V **pole nastavit na hodnotu** akce, zvolte **pole** propojit a pak v seznamu zvolte **přiřazená**.  
  
14. V **pole nastavit na hodnotu** akce, zvolte **hodnotu** propojit a pak v seznamu existující uživatele a skupiny, zvolte **uživatele, který vytvořil položku**.  
  
15. Zvolte **přidat** tlačítko a klikněte na tlačítko **OK** tlačítko.  
  
     Načte příkaz akce **nastavit přiřazeno k aktuální položky: CreatedBy**.  
  
## <a name="save-and-deploy-the-reusable-workflow"></a>Uložení a nasazení opakovaně použitelného pracovního postupu
 Protože [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] můžete importovat pouze *.wsp* soubory, je nutné uložit opakovaně použitelného pracovního postupu jako *.wsp* souboru a nasadit ho do Sharepointu, než je naimportujete do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
> [!IMPORTANT]  
>  Pokud se zobrazí chyba za běhu provedením následujících kroků, budete muset provést postup v systému, který má přístup k webu služby SharePoint.  
  
#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Uložení a nasazení opakovaně použitelného pracovního postupu  
  
1.  V horní části stránky návrháře služby SharePoint, zvolte **Uložit** tlačítko rozdělanou práci uložit a klikněte na tlačítko **publikovat** tlačítko nasazení pracovního postupu **SPD1** webu služby SharePoint .  
  
2.  V navigačním podokně, vyberte **pracovních postupů** objektu.  
  
3.  V části **opakovaně použitelných pracovních postupů**, zvolte **pracovního postupu úloh SPD**.  
  
4.  Na pásu karet, zvolte **uložit jako šablonu** tlačítko Uložit jako pracovní postup *.wsp* souboru.  
  
5.  Otevřít **SPD1** webu služby SharePoint v prohlížeči pro zobrazení *.wsp* soubor v Sharepointu.  
  
6.  Na panelu Rychlé spuštění zvolte **knihovny** odkaz.  
  
7.  V **knihovny dokumentů** zvolte **prostředky lokality** odkaz.  
  
     **Pracovního postupu úloh SPD** souboru je uvedený s další prostředky serveru.  
  
8.  V seznamu souborů zvolte název tohoto souboru  
  
9. V **stažení souboru** dialogového okna zvolte **Uložit** tlačítko Uložit *.wsp* souboru v místním systému.  
  
## <a name="import-the-wsp-file-into-visual-studio"></a>Import souboru WSP do sady Visual Studio
 Import *.wsp* soubor do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pomocí projektu Import opakovaně použitelných pracovních postupů. Tento projekt převede pracovního postupu z deklarativní, opakovaně použitelného pracovního postupu do kódu pracovního postupu. Po převodu pracovního postupu použijete změnit její chování kódu.  
  
#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Import pracovního postupu ze souboru WSP a jeho úpravy  
  
1. V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], na panelu nabídek zvolte **souboru** > **nový** > **projektu**.  
  
2. V **nový projekt** dialogového okna rozbalte **SharePoint** uzlu buď **Visual C#** nebo **jazyka Visual Basic**a klikněte na tlačítko **2010** uzlu.  
  
3. V **šablony** podokně, vyberte **pracovního postupu Import opakovaně použitelného služby SharePoint 2010** šablony, ponechte název projektu jako **WorkflowImportProject1**a klikněte na tlačítko **OK** tlačítko.  
  
    Zobrazí se Průvodce přizpůsobením SharePoint.  
  
4. Na **zadejte web a úroveň zabezpečení pro ladění** stránky, zadejte [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] pro druhý podřízeného webu služby SharePoint, který jste vytvořili dříve: http://<em>systémový název</em>/SPD2.  
  
5. V **co je úroveň důvěryhodnosti pro toto řešení SharePoint?** zvolte **nasadit jako řešení farmy** přepínač a klikněte na tlačítko **Další** tlačítko.  
  
    Další informace o izolovaných oproti řešení ve farmách, naleznete v tématu [aspekty řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).  
  
6. V **zadat nový zdroj projektu** stránce, přejděte do umístění v systému, které jste dříve uložili *.wsp* soubor, otevřete soubor a klikněte na tlačítko **Další** tlačítko.  
  
   > [!NOTE]  
   >  Zvolte **Dokončit** tlačítko naimportovány všechny položky k dispozici v *.wsp* souboru.  
  
    Zobrazí se seznam dostupných pro import opakovaně použitelných pracovních postupů.  
  
7. V **vybrat položky k importu** zvolte **pracovního postupu úloh SPD** pracovního postupu a klikněte na tlačítko **Dokončit** tlačítko.  
  
    Po dokončení operace importu projektu s názvem **WorkflowImportProject1** se vytvoří s pracovním postupem s názvem **SPD_Workflow_TestFT**. V této složce je soubor definice pracovního postupu *Elements.xml* a soubor návrháře pracovního postupu (*XOML*). Návrhář obsahuje dva soubory: soubor pravidel (.rules) a soubor kódu na pozadí (buď *.cs* nebo *.vb*, v závislosti na programovacím jazyce vašeho projektu).  
  
8. V **Průzkumníka řešení**, odstranit **ostatní soubory importovat** složky.  
  
9. V *Elements.xml* souborů, odstranění `InstantiationURL="_layouts/IniErkflIP.sspx"`.  
  
10. V **Průzkumníka řešení**, zvolte **WorkflowImportProject1**a potom na panelu nabídek zvolte **projektu** > **nastavit jako spouštěný projekt**  nastavit **WorkflowImportProject1** jako položku při spuštění.  
  
     V seznamu zobrazí okamžitě při ladění projektu.  
  
11. Vzhledem k tomu, **Import opakovaně použitelného 2010 pracovního postupu služby SharePoint** šablony neimportuje přidružení hodnoty vlastností pro importované pracovního postupu, je nutné zadat. To uděláte takto:  
  
    1.  V **Průzkumníka řešení**, zvolte **SPD_Workflow_TestFT** uzlu.  
  
    2.  Zvolte tři tečky (![elipsa ASP.NET – Návrhář mobilních řešení](../sharepoint/media/mwellipsis.gif "elipsa ASP.NET – Návrhář mobilních řešení")) tlačítko vedle jeden seznam vlastností, jako **cílového seznamu** vlastnost.  
  
    3.  Zadejte chybějící hodnoty v průvodce přizpůsobením SharePoint a klikněte na tlačítko **Dokončit** tlačítko.  
  
12. Zvolte soubor XOML a pak na panelu nabídek zvolte **zobrazení** > **návrháře** zobrazíte importovaných pracovních postupů v Návrháři pracovních postupů.  
  
13. V **pracovního postupu Windows v3.0** uzlu **nástrojů**, proveďte jednu z následujících kroků:  
  
    - Otevřete místní nabídku **kód** aktivitu a klikněte na tlačítko **kopírování**. V Návrháři postupu provádění, otevřete místní nabídku pro řádek u **SequenceActivity1** aktivitu a klikněte na tlačítko **vložit**.  
  
    - Přetáhněte **kód** aktivita z **nástrojů** do Návrháře pracovního postupu a připojte ho k řádku pod **SequenceActivity1** aktivity.  
  
      Tento postup přidá aktivitu do pracovního postupu návrháře s názvem **CodeActivity1**. V této činnosti přidejte kód akce, která vytvoří oznámení v seznamu oznámení, když uživatel spustí pracovní postup.  
  
14. Proveďte jednu z následujících sad kroků:  
  
    -   Dvakrát klikněte na panel **CodeActivity1** Generovat obslužné rutiny události a zobrazení kódu.  
  
    -   V **vlastnosti** okně **CodeActivity1**, nastavte hodnotu **ExecuteCode** vlastnost **codeActivity_ExecuteCode**.  
  
15. Přidejte následující pod existující **pomocí** nebo **importy** příkazy:  
  
     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. Nahraďte `codeActivity1_ExecuteCode` následujícím kódem:  
  
     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## <a name="deploy-the-project-and-associate-the-workflow"></a>Nasazení projektu a přidružení pracovního postupu
 V dalším kroku spusťte WorkflowImportProject1 ji nasadit na Sharepointový web a pracovní postup přidružit seznamu Úkoly k zobrazení a otestovat změny, převést pracovní postup.  
  
#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Nasazení projektu a přidružení pracovního postupu  
  
1.  V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], zvolte **F5** klíč ke spuštění a nasazení projektu převedený pracovního postupu.  
  
2.  Na panelu Rychlé spuštění zvolte **úlohy** odkaz k zobrazení seznamu úloh.  
  
3.  Na **nástroje seznamu** , vyberte **položky** tlačítko a klikněte na tlačítko **nová položka** tlačítko.  
  
     **Úkoly – nová položka** zobrazí se dialogové okno.  
  
4.  V **Title** zadejte **nový úkol**a klikněte na tlačítko **Uložit** tlačítko.  
  
5.  Na **nástroje seznamu** , vyberte **seznamu** tlačítko a klikněte na tlačítko **nastavení seznamu** tlačítko.  
  
     **Nastavení seznamu** se zobrazí stránka.  
  
6.  V **oprávnění a správa** zvolte **nastavení pracovního postupu** odkaz.  
  
     **Nastavení pracovního postupu** se zobrazí stránka.  
  
7.  Zvolte **přidat pracovní postup** odkaz.  
  
8.  V **pracovního postupu** klikněte na položku **WorkflowImportProject1 – pracovní postup Test SPD**.  
  
9. V **název** zadejte **SPD pracovní postup Test**a klikněte na tlačítko **OK** tlačítko.  
  
10. Na panelu Rychlé spuštění, zvolte **úlohy** seznamu.  
  
11. Klikněte na šipku vedle položky **nový úkol**a pak v seznamu zvolte **pracovních postupů**.  
  
12. V **spustit nový pracovní postup** zvolte odkaz pro **SPD pracovní postup Test**a klikněte na tlačítko **Start** tlačítko započít pracovní postup.  
  
    > [!NOTE]  
    >  Alternativně je můžete automatické přidružení pracovního postupu se seznamem spuštěním Průvodce nastavení pracovního postupu a nastavení automatické přidružení pracovního postupu.  
  
     Všimněte si, že dvě akce provádí pracovní postup: název se zobrazí v úkolu **přiřazeno** sloupce a oznámení se zobrazí v **oznámení** seznamu.  
  
## <a name="see-also"></a>Viz také:
 [Import položek z existující stránky SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Vytvoření opakovaně použitelné ovládací prvky webové části nebo stránky aplikace](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
