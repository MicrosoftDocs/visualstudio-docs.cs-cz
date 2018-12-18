---
title: 'Návod: Rozšíření Průzkumníka serveru pro zobrazení částí webu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6d32f76965c0dbef359e54bda114221e460a9bfd
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296382"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>Návod: Rozšíření Průzkumníka serveru pro zobrazení částí webu
  V sadě Visual Studio, můžete použít **připojení služby SharePoint** uzlu **Průzkumníka serveru** zobrazíte komponenty na webech služby SharePoint. Ale **Průzkumníka serveru** nezobrazí některé součásti ve výchozím nastavení. V tomto návodu budete rozšíříte **Průzkumníka serveru** tak, aby zobrazil galerii webových částí na každý z nich připojený web služby SharePoint.  
  
 Tento návod demonstruje následující úkoly:  
  
-   Vytváření rozšíření pro Visual Studio, který rozšiřuje **Průzkumníka serveru** následujícími způsoby:  
  
    -   Přidá rozšíření **Galerie webových částí** uzel za každý uzel webu služby SharePoint v **Průzkumníka serveru**. Tento nový uzel obsahuje podřízené uzly, které představují jednotlivé webové části v galerii webových částí na webu.  
  
    -   Rozšíření definuje nový typ uzlu, který představuje instanci webové části. Tento nový typ uzlu je základem pro podřízené uzly pod novou **Galerie webových částí** uzlu. Nový typ uzlu webovou část se zobrazí informace v **vlastnosti** okno o webové části, který představuje. Typ uzlu je také položky vlastní místní nabídky, který slouží jako výchozí bod pro provádění další úloh, které se týkají webové části.  
  
-   Vytvoření dvou vlastních příkazů služby SharePoint, která volá sestavení rozšíření. SharePoint – příkazy jsou metody, které je možné vyvolat v sestavení rozšíření, které chcete používat rozhraní API v objektovém modelu serveru SharePoint. V tomto návodu vytvoříte příkazy, které načítají informace webové části z místního webu služby SharePoint ve vývojovém počítači. Další informace najdete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Vytváření balíčku rozšíření Visual Studio (VSIX) k nasazení rozšíření.  
  
-   Ladění a testování rozšíření.  
  
> [!NOTE]  
>  Alternativní verze tohoto názorného postupu, který používá namísto jeho objektový model serveru objektového modelu klienta pro službu SharePoint, naleznete v tématu [návod: volání do objektového modelu klienta SharePoint v rozšíření Průzkumníka serveru](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="prerequisites"></a>Požadavky  
 Budete potřebovat následující komponenty na vývojovém počítači k dokončení tohoto návodu:  
  
- Podporované edice systému Windows, SharePoint a Visual Studio.  
  
- Visual Studio SDK. Tento návod používá **projekt VSIX** šablony v sadě SDK k vytvoření balíčku VSIX k nasazení položky projektu. Další informace najdete v tématu [rozšíření nástrojů SharePoint v sadě Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Znalost následujících konceptů je užitečná, ale není požadována k dokončení návodu:  
  
- Použití objektového modelu serveru pro službu SharePoint. Další informace najdete v tématu [pomocí objektového modelu SharePoint Foundation na straně serveru](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
- Webové části v řešení služby SharePoint. Další informace najdete v tématu [přehled webových částí](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="create-the-projects"></a>Vytváření projektů
 K dokončení tohoto návodu, je nutné vytvořit tři projekty:  
  
- Projekt VSIX k vytvoření balíčku VSIX k nasazení rozšíření.  
  
- Projekt knihovny tříd, který implementuje rozšíření. Tento projekt musí cílit na rozhraní .NET Framework 4.5.  
  
- Projekt knihovny tříd, který definuje vlastní příkazy služby SharePoint. Tento projekt musí cílit na rozhraní.NET Framework 3.5.  
  
  Začněte postup vytvořením projektů.  
  
#### <a name="to-create-the-vsix-project"></a>Vytvoření projektu VSIX  
  
1.  Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  V panelu nabídky zvolte **souboru** > **nový** > **projektu**.  
  
3.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** uzly a klikněte na tlačítko **rozšiřitelnost** uzlu.  
  
    > [!NOTE]  
    >  **Rozšiřitelnost** uzel je dostupný jenom v případě, že nainstalujete Visual Studio SDK. Další informace najdete v oddílu požadavky dříve v tomto tématu.  
  
4.  V horní části dialogového okna zvolte **rozhraní .NET Framework 4.5** v seznam verzí rozhraní .NET Framework.  
  
5.  Zvolte **projekt VSIX** šablony, pojmenujte projekt **WebPartNode**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **WebPartNode** projektu **Průzkumníka řešení**.  
  
#### <a name="to-create-the-extension-project"></a>Chcete-li vytvořit projekt rozšíření  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro uzel řešení, zvolte **přidat**a klikněte na tlačítko **nový projekt**.  
  
2.  V **nový projekt** dialogového okna rozbalte **Visual C#** uzlu nebo **jazyka Visual Basic** uzel a pak zvolte **Windows** uzlu.  
  
3.  V horní části dialogového okna zvolte **rozhraní .NET Framework 4.5** v seznam verzí rozhraní .NET Framework.  
  
4.  V seznamu šablon projektu vyberte **knihovny tříd**, pojmenujte projekt **WebPartNodeExtension**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **WebPartNodeExtension** projektu do řešení a otevře soubor výchozího kódu Class1.  
  
5.  Odstraňte soubor kódu Class1 z projektu.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>Chcete-li vytvořit příkazy projektu služby SharePoint  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro uzel řešení, zvolte **přidat**a klikněte na tlačítko **nový projekt**.  
  
2.  V **nový projekt** dialogového okna rozbalte **Visual C#** uzlu nebo **jazyka Visual Basic** uzel a klikněte na tlačítko **Windows** uzlu.  
  
3.  V horní části dialogového okna zvolte **rozhraní .NET Framework 3.5** v seznam verzí rozhraní .NET Framework.  
  
4.  V seznamu šablon projektu vyberte **knihovny tříd**, pojmenujte projekt **WebPartCommands**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **WebPartCommands** projektu do řešení a otevře soubor výchozího kódu Class1.  
  
5.  Odstraňte soubor kódu Class1 z projektu.  
  
## <a name="configure-the-projects"></a>Konfigurace projektů
 Než napíšete kód pro vytvoření rozšíření, musíte přidat soubory kódu a odkazy na sestavení a konfigurace nastavení projektu.  
  
#### <a name="to-configure-the-webpartnodeextension-project"></a>Ke konfiguraci projektu WebPartNodeExtension
  
1.  V projektu WebPartNodeExtension přidání čtyři souborů s kódy, které mají následující názvy:  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  Otevřete místní nabídku **WebPartNodeExtension** projektu a klikněte na tlačítko **přidat odkaz**.  
  
3.  V **správce odkazů - WebPartNodeExtension** dialogového okna zvolte **Framework** kartu a potom zaškrtněte políčko pro každé následující sestavení:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  Zvolte **rozšíření** kartu, zaškrtněte políčko pro sestavení Microsoft.VisualStudio.SharePoint a klikněte na tlačítko **OK** tlačítko.  
  
5.  V **Průzkumníka řešení**, otevřete místní nabídku **WebPartNodeExtension** uzel projektu a klikněte na tlačítko **vlastnosti**.  
  
     **Návrháře projektu** otevře.  
  
6.  Zvolte **aplikace** kartu.  
  
7.  V **výchozí obor názvů** pole (C#) nebo **kořenový obor názvů** pole ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), zadejte **ServerExplorer.SharePointConnections.WebPartNode**.  
  
#### <a name="to-configure-the-webpartcommands-project"></a>Ke konfiguraci projektu webpartcommands
  
1.  V projektu WebPartCommands přidejte soubor kódu, který je pojmenován WebPartCommands.  
  
2.  V **Průzkumníka řešení**, otevřete místní nabídku **WebPartCommands** uzel projektu, zvolte **přidat**a klikněte na tlačítko **existující položku**.  
  
3.  V **přidat existující položku** dialogové okno, přejděte do složky, která obsahuje soubory kódu pro projekt WebPartNodeExtension a klikněte na tlačítko WebPartNodeInfo a WebPartCommandIds soubory kódu.  
  
4.  Klikněte na šipku vedle položky **přidat** tlačítko a pak zvolte **přidat jako odkaz** v zobrazené nabídce.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá soubory kódu do projektu WebPartCommands jako odkazy. V důsledku toho kód soubory jsou umístěny v projektu WebPartNodeExtension, ale kód v souborech jsou také zkompilovány v projektu WebPartCommands.  
  
5.  Otevřete místní nabídku **WebPartCommands** znovu projekt a zvolte **přidat odkaz**.  
  
6.  V **správce odkazů - WebPartCommands** dialogového okna zvolte **rozšíření** kartu, zaškrtněte políčko pro každé následující sestavení a klikněte na tlačítko **OK** tlačítko:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  V **Průzkumníka řešení**, otevřete místní nabídku **WebPartCommands** projekt znovu a klikněte na tlačítko **vlastnosti**.  
  
     **Návrháře projektu** otevře.  
  
8.  Zvolte **aplikace** kartu.  
  
9. V **výchozí obor názvů** pole (C#) nebo **kořenový obor názvů** pole ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), zadejte **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="create-icons-for-the-new-nodes"></a>Vytvoření ikony pro nové uzly
 Vytvořte dvě ikony pro **Průzkumníka serveru** rozšíření: Ikona pro novou **Galerie webových částí** uzel a jinou ikonu pro každý podřízený uzel webová část pod **Galerie webových částí** uzel. Později v tomto návodu budete psát kód, který přidruží tyto ikony uzly.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Vytvoření ikony uzlů  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku **WebPartNodeExtension** projektu a klikněte na tlačítko **vlastnosti**.  
  
2.  **Návrháře projektu** otevře.  
  
3.  Zvolte **prostředky** kartu a klikněte na tlačítko **tento projekt neobsahuje soubor výchozích prostředků. Kliknutím sem vytvoříte jeden** odkaz.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Vytvoří soubor prostředků a otevře v návrháři.  
  
4.  V horní části návrháře, klikněte na šipku vedle položky **přidat prostředek** nabídky příkazů a klikněte na tlačítko **přidat novou ikonu** v zobrazené nabídce.  
  
5.  V **přidat nový prostředek** dialogové okno, název přes novou ikonu **WebPartsNode**a klikněte na tlačítko **přidat** tlačítko.  
  
     Nová ikona se otevře v **Editor obrázků**.  
  
6.  Ikona verzi 16 x 16 upravte tak, aby byly k návrhu, který můžete snadno rozpoznat.  
  
7.  Otevřete místní nabídku pro verzi 32 x 32 ikony a klikněte na tlačítko **odstranit typ obrázku**.  
  
8.  Opakujte kroky 5 až 8 přidejte druhou ikonu do projektu prostředků a název tuto ikonu **webové části**.  
  
9. V **Průzkumníka řešení**v části **prostředky** složku **WebPartNodeExtension** projektu, otevřete místní nabídku pro **WebPartsNode.ico**.  
  
10. V **vlastnosti** okna, klikněte na šipku vedle položky **akce sestavení**a klikněte na tlačítko **integrovaný prostředek** v nabídce, která se zobrazí.  
  
11. Zopakujte poslední dva kroky pro **WebPart.ico**.  
  
## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Přidání uzlu galerii webových částí do Průzkumníka serveru
 Vytvořte třídu, která přidá novou **Galerie webových částí** uzlu do každého uzlu webu služby SharePoint. Chcete-li přidat nový uzel, třída implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> rozhraní. Toto rozhraní implementujte, kdykoli budete chtít rozšířit existující uzel v chování **Průzkumníka serveru**, jako je přidání podřízeného uzlu k uzlu.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Chcete-li přidat uzel galerie webových částí do Průzkumníka serveru
  
1.  V projektu WebPartNodeExtension otevřete soubor kódu SiteNodeExtension a vložte následující kód do něj.  
  
    > [!NOTE]  
    >  Po přidání tohoto kódu, bude mít projekt několik chyb kompilace, ale zmizí při vložení kódu v dalších krocích.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="define-a-node-type-that-represents-a-web-part"></a>Definujte typ uzlu, který představuje webovou část
 Vytvořte třídu, která definuje nový typ uzlu, který představuje webovou část. Visual Studio používá k zobrazení podřízených uzlů pod tento nový typ uzlu **Galerie webových částí** uzlu. Každý podřízený uzel představuje jeden webové části na webu služby SharePoint.  
  
 Chcete-li definovat nový typ uzlu, třída implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> rozhraní. Toto rozhraní implementujte, kdykoli budete chtít definovat nový typ uzlu v **Průzkumníka serveru**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Chcete-li definovat typ uzlu webové části
  
1.  V projektu WebPartNodeExtension otevřete soubor kódu WebPartNodeTypeProvder a vložte následující kód do něj.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]  
  
## <a name="define-the-web-part-data-class"></a>Definování třídy webové části dat.
 Definujte třídu, která obsahuje data o jedné webové části na webu služby SharePoint. Později v tomto návodu vytvoříte vlastní příkaz SharePoint, který načte data o každé webové části na webu a poté přiřadí data do instance této třídy.  
  
#### <a name="to-define-the-web-part-data-class"></a>Definice třídy dat webové části
  
1.  V projektu WebPartNodeExtension otevřete soubor kódu WebPartNodeInfo a vložte následující kód do něj.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]  
  
## <a name="define-the-ids-for-the-sharepoint-commands"></a>Definovat ID pro příkazy služby SharePoint
 Definujte několik řetězců, které identifikují vlastních příkazů služby SharePoint. Dále v tomto návodu budete implementovat tyto příkazy.  
  
#### <a name="to-define-the-command-ids"></a>Chcete-li definovat identifikátory příkazů
  
1.  V projektu WebPartNodeExtension otevřete soubor kódu WebPartCommandIds a vložte následující kód do něj.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]  
  
## <a name="create-the-custom-sharepoint-commands"></a>Vytvoření vlastních příkazů služby SharePoint
 Vytvořte vlastní příkazy pro volání do objektového modelu serveru pro službu SharePoint k načtení dat o webové části na web služby SharePoint. Každý příkaz je metoda, která má <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> použit.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Chcete-li definovat příkazů služby SharePoint  
  
1.  V projektu WebPartCommands otevřete soubor kódu WebPartCommands a vložte následující kód do něj.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku návodu, veškerý kód pro **Galerie webových částí** uzlu a příkazů služby SharePoint jsou teď v projektech. Sestavte řešení, abyste měli jistotu, že oba projekty kompilovat bez chyb.  
  
#### <a name="to-build-the-solution"></a>Abyste mohli sestavit řešení  
  
1.  V panelu nabídky zvolte **sestavení** > **sestavit řešení**.  
  
    > [!WARNING]  
    >  V tomto okamžiku WebPartNode projektu může mít k chybě sestavení, protože soubor manifestu VSIX nemá hodnotu pro autora. Tato chyba zmizí při přidání hodnoty v dalších krocích.  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Vytvoření balíčku VSIX k nasazení rozšíření
 Pokud chcete nasadit rozšíření, použijte VSIX projekt ve vašem řešení k vytvoření balíčku VSIX. Nejprve nakonfigurujte VSIX balíček úpravou souboru source.extension.vsixmanifest v projektu VSIX. Potom vytvořte VSIX balíček vytvořením řešení.  
  
#### <a name="to-configure-the-vsix-package"></a>Konfigurace balíčku VSIX  
  
1.  V **Průzkumníka řešení**, v rámci WebPartNode projektu, otevřete **source.extension.vsixmanifest** souboru v editoru manifestu.  
  
     Soubor source.extension.vsixmanifest je základem pro soubor extension.vsixmanifest, které vyžadují všechny balíčky VSIX. Další informace o tomto souboru najdete v tématu [odkaz 1.0 schématu rozšíření VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  V **název produktu** zadejte **uzel galerie webových částí pro Průzkumníka serveru**.  
  
3.  V **Autor** zadejte **Contoso**.  
  
4.  V **popis** zadejte **přidá vlastní galerie webových částí uzlu k uzlu připojení služby SharePoint v Průzkumníku serveru. Toto rozšíření používá vlastní příkaz služby SharePoint pro volání do objektového modelu serveru.**  
  
5.  Zvolte **prostředky** karta editoru a klikněte na tlačítko **nový** tlačítko.  
  
     **Přidat nové aktivum** zobrazí se dialogové okno.  
  
6.  V **typ** klikněte na položku **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Tato hodnota odpovídá `MefComponent` element v souboru extension.vsixmanifest. Tento prvek určuje název sestavení rozšíření v balíčku souboru VSIX. Další informace najdete v tématu [MEFComponent – Element (VSX schéma)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  V **zdroj** klikněte na položku **projekt v aktuálním řešení**.  
  
8.  V **projektu** klikněte na položku **WebPartNodeExtension** a klikněte na tlačítko **OK** tlačítko.  
  
9. V editoru manifestu vyberte **nový** tlačítko znovu.  
  
     **Přidat nové aktivum** zobrazí se dialogové okno.  
  
10. V **typ** zadejte **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Tento prvek určuje vlastní rozšíření, které chcete zahrnout do rozšíření aplikace Visual Studio. Další informace najdete v tématu [Asset – Element (VSX schéma)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. V **zdroj** klikněte na položku **projekt v aktuálním řešení** položky seznamu.  
  
12. V **projektu** klikněte na položku **WebPartCommands**a klikněte na tlačítko **OK** tlačítko.  
  
13. V panelu nabídky zvolte **sestavení** > **sestavit řešení**a ujistěte se, že řešení zkompiluje bez chyb.  
  
14. Ujistěte se, že výstupní složka sestavení pro projekt WebPartNode nyní obsahuje soubor WebPartNode.vsix.  
  
     Výchozí je výstupní složka sestavení... složky \Bin\Debug ve složce, která obsahuje váš soubor projektu.  
  
## <a name="test-the-extension"></a>Testování rozšíření
 Teď jste připraveni k testování nového **Galerie webových částí** uzel v **Průzkumníka serveru**. Nejprve spusťte ladění rozšíření v experimentální instanci sady Visual Studio. Potom použijte nové **webových částí** uzel v experimentální instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-start-debugging-the-extension"></a>Chcete-li začít ladit rozšíření  
  
1.  Restartujte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] s přihlašovacími údaji správce a pak otevřete WebPartNode řešení.  
  
2.  V projektu WebPartNodeExtension otevřete soubor kódu SiteNodeExtension a na první řádek kódu přidejte zarážku `NodeChildrenRequested` a `CreateWebPartNodes` metody.  
  
3.  Zvolte **F5** klíč pro spuštění ladění.  
  
     Visual Studio nainstaluje rozšíření do %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web uzel rozšíření Galerie částí pro Server Explorer\1. 0 a spustí experimentální instanci sady Visual Studio. Položku projektu budete testovat v této instanci aplikace Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Chcete-li testovat rozšíření  
  
1.  V experimentální instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], na panelu nabídek zvolte **zobrazení** > **Průzkumníka serveru**.  
  
2.  Proveďte následující kroky, pokud se web služby SharePoint, kterou chcete použít pro testování nezobrazí v části **připojení služby SharePoint** uzel v **Průzkumníka serveru**:  
  
    1.  V **Průzkumníka serveru**, otevřete místní nabídku pro **připojení služby SharePoint**a klikněte na tlačítko **přidat připojení**.  
  
    2.  V **přidat připojení k Sharepointu** dialogového okna zadejte adresu URL pro Sharepointový web, ke kterému chcete připojit a klikněte na tlačítko **OK** tlačítko.  
  
         Chcete-li určit web služby SharePoint ve svém vývojovém počítači, zadejte **http://localhost**.  
  
3.  Rozbalte uzel připojení serveru (který zobrazuje adresu URL vašeho webu) a potom rozbalte uzel serveru podřízený (například **týmový web**).  
  
4.  Ověřte, že kód ve druhé instanci aplikace [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zastaví na zarážce, kterou jste nastavili dříve v `NodeChildrenRequested` metoda a klikněte na tlačítko **F5** a pokračujte v ladění projektu.  
  
5.  V experimentální instanci sady Visual Studio, ověřte, že nový uzel s názvem **Galerie webových částí** se zobrazí v lokalitě nejvyšší úrovně uzlu a potom rozbalte **Galerie webových částí** uzlu.  
  
6.  Ověřte, že kód ve druhé instanci aplikace Visual Studio zastaví na zarážce, kterou jste nastavili dříve v `CreateWebPartNodes` metoda a klikněte na tlačítko **F5** klíč a pokračujte v ladění projektu.  
  
7.  V experimentální instanci sady Visual Studio, ověřte, že všechny webové části na připojený web se zobrazí pod **Galerie webových částí** uzel v **Průzkumníka serveru**.  
  
8.  V **Průzkumníka serveru**, otevřete místní nabídku pro jednu z webové části a klikněte na tlačítko **vlastnosti**.  
  
9. V instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , kterou ladíte, ověřte, že v zobrazují podrobnosti o webové části **vlastnosti** okna.  
  
## <a name="uninstall-the-extension-from-visual-studio"></a>Odinstalovat rozšíření ze sady Visual Studio
 Po dokončení testování rozšíření odinstalujte rozšíření ze sady Visual Studio.  
  
#### <a name="to-uninstall-the-extension"></a>Chcete-li odinstalovat rozšíření  
  
1.  V experimentální instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], na panelu nabídek zvolte **nástroje** > **rozšíření a aktualizace**.  
  
     **Rozšíření a aktualizace** zobrazí se dialogové okno.  
  
2.  V seznamu rozšíření zvolte **uzel rozšíření Galerie webových částí pro Průzkumníka serveru**a klikněte na tlačítko **odinstalovat** tlačítko.  
  
3.  V dialogovém okně, které se zobrazí, zvolte **Ano** potvrďte, že chcete odinstalovat rozšíření a klikněte na tlačítko **restartovat nyní** tlačítko pro dokončení odinstalace.  
  
4.  Zavřete obě instance programu Visual Studio (experimentální instanci a instanci sady Visual Studio, ve kterém je otevřen WebPartNode řešení).  
  
## <a name="see-also"></a>Viz také:
 [Rozšíření uzlu připojení služby SharePoint v Průzkumníku serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Návod: Volání do objektového modelu klienta SharePoint v rozšíření Průzkumníka serveru](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Editor obrázků pro ikony](/cpp/windows/image-editor-for-icons)   
 [Vytvoření ikony nebo jiného obrázku &#40;Editor obrázků pro ikony&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
