---
title: 'Návod: Volání do objektového modelu klienta SharePoint v rozšíření Průzkumníka serveru | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f4510aa820e0f82c2fcd73ccb83ed0f8120a1399
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296031"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Návod: Volání do objektového modelu klienta SharePoint v rozšíření Průzkumníka serveru
  Tento návod ukazuje, jak volat z rozšíření pro objektového modelu klienta SharePoint **připojení služby SharePoint** uzel v **Průzkumníka serveru**. Další informace o tom, jak pomocí objektového modelu klienta SharePoint, naleznete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
 Tento návod demonstruje následující úkoly:  
  
-   Vytváření [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozšíření, které rozšiřuje **připojení služby SharePoint** uzlu **Průzkumníka serveru** následujícími způsoby:  
  
    -   Přidá rozšíření **Galerie webových částí** uzel za každý uzel webu služby SharePoint v **Průzkumníka serveru**. Tento nový uzel obsahuje podřízené uzly, které představují jednotlivé webové části v galerii webových částí na webu.  
  
    -   Rozšíření definuje nový typ uzlu, který představuje instanci webové části. Tento nový typ uzlu je základem pro podřízené uzly pod novou **Galerie webových částí** uzlu. Zobrazí informace v nového typu uzlu webové části **vlastnosti** okno o webové části, která představuje uzel.  
  
-   Vytváření balíčku rozšíření Visual Studio (VSIX) k nasazení rozšíření.  
  
-   Ladění a testování rozšíření.  
  
> [!NOTE]  
>  Rozšíření, které vytvoříte v tomto názorném postupu se podobá rozšíření, které vytvoříte v [návod: rozšíření Průzkumníka serveru pro zobrazení částí webu](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). Tento návod používá objektového modelu serveru SharePoint, ale tento návod provede stejné úlohy pomocí objektového modelu klienta.  
  
## <a name="prerequisites"></a>Požadavky  
 Budete potřebovat následující komponenty na vývojovém počítači k dokončení tohoto návodu:  
  
-   Podporované edice systému Windows, SharePoint a Visual Studio.
  
-   Visual Studio SDK. Tento návod používá **projekt VSIX** šablony v sadě SDK k vytvoření balíčku VSIX k nasazení rozšíření. Další informace najdete v tématu [rozšíření nástrojů SharePoint v sadě Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
Znalost následujících konceptů je užitečná, ale není požadována k dokončení návodu:  
  
-   Použití objektového modelu klienta SharePoint. Další informace najdete v tématu [spravované objektového modelu klienta](http://go.microsoft.com/fwlink/?LinkId=177797).  
  
-   Webové části služby SharePoint. Další informace najdete v tématu [přehled webových částí](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="create-the-projects"></a>Vytváření projektů
 K dokončení tohoto návodu, je nutné vytvořit dva projekty:  
  
- Projekt VSIX k vytvoření balíčku VSIX pro nasazení **Průzkumníka serveru** rozšíření.  
  
- Projekt knihovny tříd, který implementuje **Průzkumníka serveru** rozšíření.  
  
  Začněte postup vytvořením projektů.  
  
#### <a name="to-create-the-vsix-project"></a>Vytvoření projektu VSIX  
  
1.  Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  V panelu nabídky zvolte **souboru** > **nový** > **projektu**.  
  
3.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** uzly a klikněte na tlačítko **rozšiřitelnost**.  
  
    > [!NOTE]  
    >  **Rozšiřitelnost** uzel je dostupný jenom v případě, že nainstalujete Visual Studio SDK. Další informace najdete v oddílu požadavky dříve v tomto tématu.  
  
4.  V horní části dialogového okna zvolte **rozhraní .NET Framework 4.5** v seznam verzí rozhraní .NET Framework.  
  
     Rozšíření nástrojů SharePoint vyžaduje funkce v této verzi rozhraní .NET Framework.  
  
5.  Zvolte **projekt VSIX** šablony.  
  
6.  V **název** zadejte **WebPartNode**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **WebPartNode** projektu **Průzkumníka řešení**.  
  
#### <a name="to-create-the-extension-project"></a>Chcete-li vytvořit projekt rozšíření  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro uzel řešení, zvolte **přidat**a klikněte na tlačítko **nový projekt**.  
  
2.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** uzly a klikněte na tlačítko **Windows**.  
  
3.  V horní části dialogového okna zvolte **rozhraní .NET Framework 4.5** v seznam verzí rozhraní .NET Framework.  
  
4.  V seznamu šablon projektu vyberte **knihovny tříd**.  
  
5.  V **název** zadejte **WebPartNodeExtension**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **WebPartNodeExtension** projektu do řešení a otevře soubor výchozího kódu Class1.  
  
6.  Odstraňte soubor kódu Class1 z projektu.  
  
## <a name="configure-the-extension-project"></a>Konfigurace projektu rozšíření
 Než napíšete kód pro vytvoření rozšíření, je nutné přidat soubory kódu a odkazy na sestavení do projektu a je nutné aktualizovat výchozí obor názvů.  
  
#### <a name="to-configure-the-project"></a>Konfigurace projektu  
  
1.  V **WebPartNodeExtension** projektu, přidejte dva soubory kódu, které jsou pojmenovány SiteNodeExtension a WebPartNodeTypeProvider.  
  
2.  Otevřete místní nabídku pro projekt WebPartNodeExtension a klikněte na tlačítko **přidat odkaz**.  
  
3.  V **správce odkazů - WebPartNodeExtension** dialogového okna zvolte **Framework** uzel a potom zaškrtněte políčka pro System.ComponentModel.Composition a System.Windows.Forms sestavení.  
  
4.  Zvolte **rozšíření** uzlu, zaškrtněte políčko pro každé následující sestavení a klikněte na tlačítko **OK** tlačítka:  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Otevřete místní nabídku **WebPartNodeExtension** projektu a klikněte na tlačítko **vlastnosti**.  
  
     **Návrháře projektu** otevře.  
  
6.  Zvolte **aplikace** kartu.  
  
7.  V **výchozí obor názvů** pole (C#) nebo **kořenový obor názvů** (Visual Basic), zadejte **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="create-icons-for-the-new-nodes"></a>Vytvoření ikony pro nové uzly
 Vytvořte dvě ikony pro **Průzkumníka serveru** rozšíření: Ikona pro novou **Galerie webových částí** uzlu a jinou ikonu pro každý podřízený uzel webová část pod **Galerie webových částí** uzel. Později v tomto návodu budete psát kód, která přidružuje tyto ikony uzly.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Vytvoření ikony uzlů  
  
1.  V **Návrháře projektu** WebPartNodeExtension projektu, zvolte **prostředky** kartu.  
  
2.  Zvolte odkaz **tento projekt neobsahuje soubor výchozích prostředků. Vytvořte si ho kliknutím sem.**  
  
     Visual Studio vytvoří soubor prostředků a otevře v návrháři.  
  
3.  V horní části návrháře, klikněte na šipku na **přidat prostředek** nabídky příkazů a klikněte na tlačítko **přidat novou ikonu**.  
  
4.  Zadejte **WebPartsNode** pro na ikonu nový název a klikněte na tlačítko **přidat** tlačítko.  
  
     Nová ikona se otevře v **Editor obrázků**.  
  
5.  Ikona verzi 16 x 16 upravte tak, aby byly k návrhu, který můžete snadno rozpoznat.  
  
6.  Otevřete místní nabídku pro verzi 32 x 32 ikony a klikněte na tlačítko **odstranit typ obrázku**.  
  
7.  Opakujte kroky 3 až 7 pro přidání druhé ikoně pro prostředky projektu a pojmenujte tuto ikonu **webové části**.  
  
8.  V **Průzkumníka řešení**v **prostředky** složku **WebPartNodeExtension** projektu, zvolte *WebPartsNode.ico*.  
  
9. V **vlastnosti** otevřené okno **akce sestavení** seznamu a klikněte na tlačítko **integrovaný prostředek**.  
  
10. Zopakujte poslední dva kroky pro *WebPart.ico*.  
  
## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Přidat uzel galerie webových částí do Průzkumníka serveru
 Vytvořte třídu, která přidá novou **Galerie webových částí** uzlu do každého uzlu webu služby SharePoint. Chcete-li přidat nový uzel, třída implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> rozhraní. Toto rozhraní implementujte, kdykoli budete chtít rozšířit existující uzel v chování **Průzkumníka serveru**, jako je například přidávání nového podřízeného uzlu k uzlu.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Chcete-li přidat uzel galerie webových částí do Průzkumníka serveru
  
1.  Vložte následující kód do **SiteNodeExtension** soubor kódu **WebPartNodeExtension** projektu.  
  
    > [!NOTE]  
    >  Po přidání tohoto kódu bude mít projekt několik chyb kompilace. K těmto chybám předejdete přidáním kódu v dalších krocích.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="define-a-node-type-that-represents-a-web-part"></a>Definujte typ uzlu, který představuje webovou část
 Vytvořte třídu, která definuje nový typ uzlu, který představuje webovou část. Visual Studio používá k zobrazení podřízených uzlů pod tento nový typ uzlu **Galerie webových částí** uzlu. Každá z těchto podřízených uzlů představuje jeden webové části na webu služby SharePoint.  
  
 Chcete-li definovat nový typ uzlu, třída implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> rozhraní. Toto rozhraní implementujte, kdykoli budete chtít definovat nový typ uzlu v **Průzkumníka serveru**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Chcete-li definovat typ uzlu webové části
  
1.  Vložte následující kód do **WebPartNodeTypeProvider** soubor kódu **WebPartNodeExtension** projektu.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku návodu, veškerý kód pro **Galerie webových částí** uzlu je nyní v projektu. Sestavení **WebPartNodeExtension** projektu se ujistěte, že se zkompiluje bez chyb.  
  
#### <a name="to-build-the-project"></a>K sestavení projektu  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku **WebPartNodeExtension** projektu a klikněte na tlačítko **sestavení**.  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Vytvoření balíčku VSIX k nasazení rozšíření
 Pokud chcete nasadit rozšíření, použijte VSIX projekt ve vašem řešení k vytvoření balíčku VSIX. Nejprve nakonfigurujte VSIX balíček úpravou souboru source.extension.vsixmanifest, který je zahrnutý v projektu. Pak vytvořte VSIX balíček vytvořením řešení.  
  
#### <a name="to-configure-the-vsix-package"></a>Konfigurace balíčku VSIX  
  
1.  V **Průzkumníka řešení**v **WebPartNode** projekt, otevřete **source.extension.vsixmanifest** souboru v editoru manifestu.  
  
     Soubor source.extension.vsixmanifest je základem pro soubor extension.vsixmanifest, které vyžadují všechny balíčky VSIX. Další informace o tomto souboru najdete v tématu [odkaz 1.0 schématu rozšíření VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  V **název produktu** zadejte **uzel galerie webových částí pro Průzkumníka serveru**.  
  
3.  V **Autor** zadejte **Contoso**.  
  
4.  V **popis** zadejte **přidá vlastní galerie webových částí uzlu k uzlu připojení služby SharePoint v Průzkumníku serveru**.  
  
5.  Na **prostředky** kartu Editor, zvolte **nový** tlačítko.  
  
6.  V **přidat nové aktivum** v dialogu **typ** klikněte na položku **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Tato hodnota odpovídá `MefComponent` element v souboru extension.vsixmanifest. Tento prvek určuje název sestavení rozšíření v balíčku souboru VSIX. Další informace najdete v tématu [MEFComponent – Element (VSX schéma)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  V **zdroj** klikněte na položku **projekt v aktuálním řešení**.  
  
8.  V **projektu** klikněte na položku **WebPartNodeExtension**a klikněte na tlačítko **OK** tlačítko.  
  
9. V panelu nabídky zvolte **sestavení** > **sestavit řešení**a ujistěte se, že řešení zkompiluje bez chyb.  
  
10. Ujistěte se, že výstupní složka sestavení pro projekt WebPartNode nyní obsahuje soubor WebPartNode.vsix.  
  
     Výchozí je výstupní složka sestavení... složky \Bin\Debug ve složce, která obsahuje váš soubor projektu.  
  
## <a name="test-the-extension"></a>Testování rozšíření
 Nyní jste připraveni k testování nového **Galerie webových částí** uzel v **Průzkumníka serveru**. Nejprve spusťte ladění projektu rozšíření v experimentální instanci sady Visual Studio. Pomocí nové **webových částí** uzlu v experimentální instanci sady Visual Studio.  
  
#### <a name="to-start-debugging-the-extension"></a>Chcete-li začít ladit rozšíření  
  
1.  Restartujte Visual Studio s přihlašovacími údaji správce a pak otevřete **WebPartNode** řešení.  
  
2.  Otevřete v projektu WebPartNodeExtension **SiteNodeExtension** soubor kódu a pak přidejte zarážku na první řádky kódu ve `NodeChildrenRequested` a `CreateWebPartNodes` metody.  
  
3.  Zvolte **F5** klíč pro spuštění ladění.  
  
     Visual Studio nainstaluje rozšíření do %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web uzel rozšíření Galerie částí pro Server Explorer\1. 0 a spustí experimentální instanci sady Visual Studio. Položku projektu budete testovat v této instanci aplikace Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Chcete-li testovat rozšíření  
  
1.  V experimentální instanci sady Visual Studio na panelu nabídek zvolte **zobrazení** > **Průzkumníka serveru**.  
  
2.  Ověřte, že web služby SharePoint, kterou chcete použít pro testování se zobrazí pod **připojení služby SharePoint** uzel v **Průzkumníka serveru**. Pokud není uvedená, postupujte podle těchto kroků:  
  
    1.  Otevřete místní nabídku pro **připojení služby SharePoint**a klikněte na tlačítko **přidat připojení**.  
  
    2.  V **přidat připojení k Sharepointu** dialogového okna zadejte adresu URL pro Sharepointový web, ke kterému chcete připojit a klikněte na tlačítko **OK** tlačítko.  
  
         Chcete-li určit web služby SharePoint ve svém vývojovém počítači, zadejte **http://localhost**.  
  
3.  Rozbalte uzel připojení serveru (který zobrazuje adresu URL vašeho webu) a potom rozbalte uzel serveru podřízený (například **týmový web**).  
  
4.  Ověřte, že kód ve druhé instanci aplikace Visual Studio zastaví na zarážce, kterou jste nastavili dříve v `NodeChildrenRequested` metoda a klikněte na tlačítko **F5** klíč a pokračujte v ladění projektu.  
  
5.  V experimentální instanci sady Visual Studio, rozbalte **Galerie webových částí** uzel, který se zobrazí v lokalitě nejvyšší úrovně uzlu.  
  
6.  Ověřte, že kód ve druhé instanci aplikace Visual Studio zastaví na zarážce, kterou jste nastavili dříve v `CreateWebPartNodes` metoda a klikněte na tlačítko **F5** klíč a pokračujte v ladění projektu.  
  
7.  V experimentální instanci sady Visual Studio, ověřte, že všechny webové části na připojený web se zobrazí pod **Galerie webových částí** uzel v **Průzkumníka serveru**.  
  
8.  Otevřete místní nabídku pro webové části a klikněte na tlačítko **vlastnosti**.  
  
9. V **vlastnosti** okna, ověřte, že se zobrazují podrobnosti o webové části.  
  
10. V **Průzkumníka serveru**, otevřete místní nabídku pro stejné webové části a klikněte na tlačítko **zobrazit zprávu**.  
  
     V okně se zprávou, která se zobrazí, vyberte **OK** tlačítko.  
  
## <a name="uninstall-the-extension-from-visual-studio"></a>Odinstalovat rozšíření ze sady Visual Studio
 Po dokončení testování rozšíření, odinstalujte ji ze sady Visual Studio.  
  
#### <a name="to-uninstall-the-extension"></a>Chcete-li odinstalovat rozšíření  
  
1.  V experimentální instanci sady Visual Studio na panelu nabídek zvolte **nástroje** > **rozšíření a aktualizace**.  
  
     **Rozšíření a aktualizace** zobrazí se dialogové okno.  
  
2.  V seznamu rozšíření zvolte **uzel galerie webových částí pro Průzkumníka serveru**a klikněte na tlačítko **odinstalovat** tlačítko.  
  
3.  V dialogovém okně, které se zobrazí, zvolte **Ano** tlačítko.  
  
4.  Zvolte **restartovat nyní** tlačítko pro dokončení odinstalace.  
  
     Položka projektu je odinstalována také.  
  
5.  Zavřete obě instance programu Visual Studio (experimentální instanci a instanci sady Visual Studio, ve kterém je otevřen WebPartNode řešení).  
  
## <a name="see-also"></a>Viz také:
 [Volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Rozšíření uzlu připojení služby SharePoint v Průzkumníku serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Návod: Rozšíření Průzkumníka serveru pro zobrazení částí webu](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Editor obrázků pro ikony](/cpp/windows/image-editor-for-icons)   
 [Vytvoření ikony nebo jiného obrázku &#40;Editor obrázků pro ikony&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)