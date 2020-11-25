---
title: 'Návod: rozšíření Průzkumník serveru pro zobrazení Webové části | Microsoft Docs'
titleSuffix: ''
description: V tomto návodu rozšíříte Průzkumník serveru tak, aby se na všech připojených webech SharePointu zobrazila galerie webových částí.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 55950d8498b436d38d2145c2692556330718883e
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970210"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>Návod: roztažení Průzkumník serveru pro zobrazení webových částí
  V aplikaci Visual Studio můžete použít uzel **připojení služby sharepoint** **Průzkumník serveru** k zobrazení komponent na webech služby SharePoint. **Průzkumník serveru** ale ve výchozím nastavení nezobrazuje některé součásti. V tomto návodu rozšíříte **Průzkumník serveru** tak, aby se na všech připojených webech SharePointu zobrazila galerie webových částí.

 Tento názorný postup ukazuje následující úlohy:

- Vytvoření rozšíření sady Visual Studio, které rozšiřuje **Průzkumník serveru** následujícími způsoby:

  - Rozšíření přidá uzel **Galerie webových částí** pod každým uzlem webu služby SharePoint v **Průzkumník serveru**. Tento nový uzel obsahuje podřízené uzly, které reprezentují jednotlivé webové části v galerii webových částí na webu.

  - Rozšíření definuje nový typ uzlu, který představuje instanci webové části. Tento nový typ uzlu je základem pro podřízené uzly v rámci nového uzlu **Galerie webových částí** . Nový typ uzlu webové části zobrazuje informace v okně **vlastnosti** o webové části, kterou představuje. Typ uzlu zahrnuje také vlastní položku místní nabídky, kterou můžete použít jako výchozí bod pro provádění jiných úloh, které se vztahují k webové části.

- Vytvořte dva vlastní příkazy SharePointu, které sestavení rozšíření volá. Příkazy služby SharePoint jsou metody, které mohou být volány sestaveními rozšíření pro použití rozhraní API v objektovém modelu serveru pro službu SharePoint. V tomto návodu vytvoříte příkazy, které načítají informace webové části z místního webu služby SharePoint ve vývojovém počítači. Další informace naleznete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Sestavení balíčku rozšíření sady Visual Studio (VSIX) pro nasazení rozšíření.

- Ladění a testování rozšíření.

> [!NOTE]
> Alternativní verzi tohoto Názorného postupu, který používá objektový model klienta pro službu SharePoint namísto jeho objektového modelu serveru, naleznete v tématu [Návod: volání do modelu objektu klienta služby SharePoint v rozšíření Průzkumník serveru](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto Názorného postupu potřebujete na vývojovém počítači následující komponenty:

- Podporované edice Windows, SharePointu a sady Visual Studio.

- Sada Visual Studio SDK. Tento návod používá šablonu **projektu VSIX** v sadě SDK k vytvoření balíčku VSIX pro nasazení položky projektu. Další informace najdete v tématu věnovaném [rozšiřování nástrojů služby SharePoint v aplikaci Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znalosti následujících konceptů jsou užitečné, ale nevyžadují se k dokončení tohoto postupu:

- Použití objektového modelu serveru pro službu SharePoint. Další informace naleznete v tématu [použití modelu objektu Server-Side SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).

- Webové části v řešeních služby SharePoint. Další informace najdete v tématu [přehled webové části](/previous-versions/office/ms432401(v=office.14)).

## <a name="create-the-projects"></a>Vytváření projektů
 Chcete-li dokončit tento návod, je nutné vytvořit tři projekty:

- Projekt VSIX k vytvoření balíčku VSIX pro nasazení rozšíření.

- Projekt knihovny tříd, který implementuje rozšíření. Tento projekt musí být zaměřen na .NET Framework 4,5.

- Projekt knihovny tříd, který definuje vlastní příkazy služby SharePoint. Tento projekt musí být cílen na the.NET Framework 3,5.

  Spusťte návod vytvořením projektů.

#### <a name="to-create-the-vsix-project"></a>Vytvoření projektu VSIX

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

3. V dialogovém okně  **Nový projekt** rozbalte uzly **Visual C#** nebo **Visual Basic** a pak zvolte uzel **rozšiřitelnost** .

    > [!NOTE]
    > Uzel **rozšiřitelnosti** je k dispozici pouze v případě, že instalujete sadu Visual Studio SDK. Další informace najdete v části požadavky výše v tomto tématu.

4. V horní části dialogového okna vyberte v seznamu verzí .NET Framework **.NET Framework 4,5** .

5. Zvolte šablonu **projektu VSIX** , pojmenujte projekt **WebPartNode** a pak klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **WebPartNode** do **Průzkumník řešení**.

#### <a name="to-create-the-extension-project"></a>Vytvoření projektu rozšíření

1. V **Průzkumník řešení** otevřete místní nabídku uzlu řešení, zvolte možnost **Přidat** a pak zvolte možnost **Nový projekt**.

2. V dialogovém okně **Nový projekt** rozbalte uzel **Visual C#** nebo **Visual Basic** a pak vyberte uzel **Windows** .

3. V horní části dialogového okna vyberte v seznamu verzí .NET Framework **.NET Framework 4,5** .

4. V seznamu šablon projektu zvolte možnost **Knihovna tříd**, pojmenujte projekt **WebPartNodeExtension** a pak klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **WebPartNodeExtension** do řešení a otevře soubor Default Class1 Code.

5. Odstraňte soubor kódu Class1 z projektu.

#### <a name="to-create-the-sharepoint-commands-project"></a>Vytvoření projektu příkazů SharePointu

1. V **Průzkumník řešení** otevřete místní nabídku uzlu řešení, zvolte možnost **Přidat** a pak zvolte možnost **Nový projekt**.

2. V dialogovém okně  **Nový projekt** rozbalte uzel **Visual C#** nebo **Visual Basic** a pak vyberte uzel **Windows** .

3. V horní části dialogového okna vyberte v seznamu verzí .NET Framework **.NET Framework 3,5** .

4. V seznamu šablon projektu zvolte možnost **Knihovna tříd**, pojmenujte projekt **WebPartCommands** a poté klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **WebPartCommands** do řešení a otevře soubor Default Class1 Code.

5. Odstraňte soubor kódu Class1 z projektu.

## <a name="configure-the-projects"></a>Konfigurace projektů
 Předtím, než napíšete kód pro vytvoření rozšíření, je nutné přidat soubory kódu a odkazy na sestavení a nakonfigurovat nastavení projektu.

#### <a name="to-configure-the-webpartnodeextension-project"></a>Konfigurace projektu WebPartNodeExtension

1. V projektu WebPartNodeExtension přidejte čtyři soubory kódu, které mají následující názvy:

    - SiteNodeExtension

    - WebPartNodeTypeProvider

    - WebPartNodeInfo

    - WebPartCommandIds

2. Otevřete místní nabídku projektu **WebPartNodeExtension** a pak zvolte možnost **Přidat odkaz**.

3. V dialogovém okně **Správce odkazů – WebPartNodeExtension** zvolte kartu **rozhraní** a potom zaškrtněte políčko pro každé z následujících sestavení:

    - System. ComponentModel. složení

    - System. Windows. Forms

4. Zvolte kartu **rozšíření** , zaškrtněte políčko pro sestavení Microsoft. VisualStudio. SharePoint a pak klikněte na tlačítko **OK** .

5. V **Průzkumník řešení** otevřete místní nabídku uzlu projektu **WebPartNodeExtension** a zvolte možnost **vlastnosti**.

     Otevře se **Návrhář projektu** .

6. Vyberte kartu **aplikace** .

7. Do pole **výchozí obor názvů** (C#) nebo **kořenového oboru názvů** ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) zadejte **ServerExplorer. SharePointConnections. WebPartNode**.

#### <a name="to-configure-the-webpartcommands-project"></a>Konfigurace projektu WebPartCommands

1. V projektu WebPartCommands přidejte soubor kódu s názvem WebPartCommands.

2. V **Průzkumník řešení** otevřete místní nabídku uzlu projektu **WebPartCommands** , zvolte možnost **Přidat** a poté možnost **existující položka**.

3. V dialogovém okně **Přidat existující položku** přejděte do složky, která obsahuje soubory kódu projektu WebPartNodeExtension, a pak zvolte soubory kódu WebPartNodeInfo a WebPartCommandIds.

4. Klikněte na šipku vedle tlačítka **Přidat** a v zobrazené nabídce zvolte možnost **Přidat jako odkaz** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá soubory kódu do projektu WebPartCommands jako odkazy. V důsledku toho se soubory kódu nacházejí v projektu WebPartNodeExtension, ale kód v souborech je zkompilován také v projektu WebPartCommands.

5. Znovu otevřete místní nabídku pro projekt **WebPartCommands** a vyberte možnost **Přidat odkaz**.

6. V dialogovém okně **Správce odkazů – WebPartCommands** zvolte kartu **rozšíření** , zaškrtněte políčko pro každé z následujících sestavení a pak klikněte na tlačítko **OK** :

    - Microsoft. SharePoint

    - Microsoft. VisualStudio. SharePoint. Commands

7. V **Průzkumník řešení** znovu otevřete místní nabídku pro projekt **WebPartCommands** a pak zvolte možnost **vlastnosti**.

     Otevře se **Návrhář projektu** .

8. Vyberte kartu **aplikace** .

9. Do pole **výchozí obor názvů** (C#) nebo **kořenového oboru názvů** ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) zadejte **ServerExplorer. SharePointConnections. WebPartNode**.

## <a name="create-icons-for-the-new-nodes"></a>Vytvořit ikony pro nové uzly
 Vytvořte dvě ikony pro rozšíření **Průzkumník serveru** : ikonu pro nový uzel **Galerie webových částí** a další ikonu pro každý podřízený uzel webové části v uzlu **Galerie webových částí** . Později v tomto návodu budete psát kód, který přidruží tyto ikony k uzlům.

#### <a name="to-create-icons-for-the-nodes"></a>Vytvoření ikon pro uzly

1. V **Průzkumník řešení** otevřete místní nabídku projektu **WebPartNodeExtension** a pak zvolte možnost **vlastnosti**.

2. Otevře se **Návrhář projektu** .

3. Zvolte kartu **prostředky** a pak zvolte, že **Tento projekt neobsahuje výchozí soubor prostředků. Kliknutím sem vytvoříte jeden** odkaz.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Vytvoří soubor prostředků a otevře ho v návrháři.

4. V horní části návrháře klikněte na šipku vedle příkazu nabídky **Přidat prostředek** a v zobrazené nabídce zvolte možnost **Přidat novou ikonu** .

5. V dialogovém okně **Přidat nový prostředek** zadejte název nové ikony **WebPartsNode** a pak klikněte na tlačítko **Přidat** .

     Nová ikona se otevře v **editoru obrázků**.

6. Upravte verzi 16x16 ikony tak, aby měla návrh, který můžete snadno rozpoznat.

7. Otevřete místní nabídku pro verzi 32x32 ikony a zvolte možnost **Odstranit typ obrázku**.

8. Opakujte kroky 5 až 8 pro přidání druhé ikony do prostředků projektu a pojmenujte tuto **webovou část** ikona.

9. V **Průzkumník řešení** ve složce **Resources (prostředky** ) projektu **WebPartNodeExtension** otevřete místní nabídku pro **WebPartsNode. ico**.

10. V okně **vlastnosti** klikněte na šipku vedle možnosti **sestavit akci** a v zobrazené nabídce vyberte možnost **Integrovaný prostředek** .

11. Zopakujte poslední dva kroky pro **WebPart. ico**.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Přidat uzel galerie webových částí do Průzkumník serveru
 Vytvořte třídu, která přidá nový uzel **Galerie webových částí** do každého uzlu webu služby SharePoint. Chcete-li přidat nový uzel, třída implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> rozhraní. Implementujte toto rozhraní vždy, když chcete rozšíření chování existujícího uzlu v **Průzkumník serveru**, jako je například přidání podřízeného uzlu do uzlu.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Přidání uzlu Galerie webových částí do Průzkumník serveru

1. V projektu WebPartNodeExtension otevřete soubor kódu SiteNodeExtension a vložte do něj následující kód.

    > [!NOTE]
    > Po přidání tohoto kódu dojde k chybě při kompilaci projektu, ale při přidávání kódu v pozdějších krocích zmizí.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Definujte typ uzlu, který představuje webovou část.
 Vytvořte třídu, která definuje nový typ uzlu, který představuje webovou část. Visual Studio používá tento nový typ uzlu k zobrazení podřízených uzlů v uzlu **Galerie webových částí** . Každý podřízený uzel představuje jednu webovou část na webu služby SharePoint.

 Chcete-li definovat nový typ uzlu, třída implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> rozhraní. Implementujte toto rozhraní vždy, když chcete definovat nový typ uzlu v **Průzkumník serveru**.

#### <a name="to-define-the-web-part-node-type"></a>Definování typu uzlu webové části

1. V projektu WebPartNodeExtension otevřete soubor kódu WebPartNodeTypeProvder a vložte do něj následující kód.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]

## <a name="define-the-web-part-data-class"></a>Definovat datovou třídu webové části
 Definujte třídu, která obsahuje data o jedné webové části na webu služby SharePoint. Později v tomto návodu vytvoříte vlastní příkaz SharePointu, který načte data o každé webové části na webu a následně přiřadí data do instancí této třídy.

#### <a name="to-define-the-web-part-data-class"></a>Chcete-li definovat datovou třídu webové části

1. V projektu WebPartNodeExtension otevřete soubor kódu WebPartNodeInfo a vložte do něj následující kód.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]

## <a name="define-the-ids-for-the-sharepoint-commands"></a>Definování ID pro příkazy služby SharePoint
 Definujte několik řetězců, které identifikují vlastní příkazy služby SharePoint. Tyto příkazy budete implementovat později v tomto návodu.

#### <a name="to-define-the-command-ids"></a>Definování identifikátorů příkazů

1. V projektu WebPartNodeExtension otevřete soubor kódu WebPartCommandIds a vložte do něj následující kód.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]

## <a name="create-the-custom-sharepoint-commands"></a>Vytvoření vlastních příkazů SharePointu
 Vytvořte vlastní příkazy, které volají do objektového modelu serveru pro službu SharePoint a načtou data o Webové části na webu služby SharePoint. Každý příkaz je metoda, která má <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> použitu.

#### <a name="to-define-the-sharepoint-commands"></a>Definování příkazů služby SharePoint

1. V projektu WebPartCommands otevřete soubor kódu WebPartCommands a vložte do něj následující kód.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]

## <a name="checkpoint"></a>CheckPoint
 V tomto okamžiku v tomto návodu se všechny kódy pro uzel **Galerie webových částí** a příkazy služby SharePoint nyní nacházejí v projektech. Sestavte řešení, aby se zajistilo, že oba projekty budou zkompilovány bez chyb.

#### <a name="to-build-the-solution"></a>Sestavení řešení

1. Na řádku nabídek klikněte na **sestavit** sestavení  >  **řešení**.

    > [!WARNING]
    > V tomto okamžiku může mít projekt WebPartNode chybu sestavení, protože soubor manifestu VSIX nemá hodnotu pro autora. Tato chyba zmizí, když přidáte hodnotu v pozdějších krocích.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Vytvoření balíčku VSIX pro nasazení rozšíření
 Chcete-li nasadit rozšíření, použijte VSIX projekt ve vašem řešení k vytvoření balíčku VSIX. Nejprve nakonfigurujte balíček VSIX úpravou souboru source. extension. vsixmanifest v projektu VSIX. Pak vytvořte balíček VSIX sestavením řešení.

#### <a name="to-configure-the-vsix-package"></a>Konfigurace balíčku VSIX

1. V **Průzkumník řešení** v projektu WebPartNode otevřete soubor **source. extension. vsixmanifest** v editoru manifestu.

     Soubor source. extension. vsixmanifest je základem pro soubor Extension. vsixmanifest, který vyžaduje všechny balíčky VSIX. Další informace o tomto souboru najdete v referenčních informacích k [schématu rozšíření VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. Do pole **název produktu** zadejte **uzel galerie webových částí pro Průzkumník serveru**.

3. Do pole **Autor** zadejte **Contoso**.

4. V poli **Popis** zadejte do **uzlu připojení služby SharePoint v Průzkumník serveru přidat vlastní uzel galerie webových částí. Toto rozšíření používá vlastní příkaz SharePoint pro volání do objektového modelu serveru.**

5. Zvolte kartu **aktiva** v editoru a pak klikněte na tlačítko **Nový** .

     Zobrazí se dialogové okno **Přidat nový prostředek** .

6. V seznamu **typ** vyberte možnost **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Tato hodnota odpovídá `MefComponent` prvku v souboru extension. vsixmanifest. Tento prvek určuje název sestavení rozšíření v balíčku VSIX. Další informace naleznete v tématu [MefComponent element (VSX Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. V seznamu  **zdroj** vyberte **projekt v aktuálním řešení**.

8. V seznamu **projekt** zvolte **WebPartNodeExtension** a pak klikněte na tlačítko **OK** .

9. V editoru manifestu znovu klikněte na tlačítko **Nový** .

     Zobrazí se dialogové okno **Přidat nový prostředek** .

10. Do pole **typ** zadejte **SharePoint. Commands. v4**.

    > [!NOTE]
    > Tento prvek určuje vlastní rozšíření, které chcete zahrnout do rozšíření aplikace Visual Studio. Další informace naleznete v tématu [Asset – element (schéma VSX)](/previous-versions/dd393737(v=vs.110)).

11. V seznamu **zdroj** vyberte **projekt v aktuální** položce seznamu řešení.

12. V seznamu **projekt** zvolte možnost **WebPartCommands** a pak klikněte na tlačítko **OK** .

13. V panelu nabídek zvolte **sestavit**  >  **sestavení řešení** a pak se ujistěte, že se řešení zkompiluje bez chyb.

14. Ujistěte se, že výstupní složka sestavení pro projekt WebPartNode nyní obsahuje soubor WebPartNode. VSIX.

     Ve výchozím nastavení je výstupní složka sestavení.. Složka \bin\Debug ve složce, která obsahuje soubor projektu.

## <a name="test-the-extension"></a>Test rozšíření
 Nyní jste připraveni otestovat nový uzel **Galerie webových částí** v **Průzkumník serveru**. Nejprve spusťte ladění rozšíření v experimentální instanci aplikace Visual Studio. Pak použijte nový uzel **webové části** v experimentální instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-start-debugging-the-extension"></a>Spuštění ladění rozšíření

1. Restartujte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] s přihlašovacími údaji správce a pak otevřete řešení WebPartNode.

2. V projektu WebPartNodeExtension otevřete soubor kódu SiteNodeExtension a pak přidejte zarážku do prvního řádku kódu v `NodeChildrenRequested` `CreateWebPartNodes` metodách a.

3. Kliknutím na klávesu **F5** spusťte ladění.

     Visual Studio nainstaluje rozšíření na rozšíření uzlu Galerie částí%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web pro server Explorer\1.0 a spustí experimentální instanci sady Visual Studio. Budete testovat položku projektu v této instanci aplikace Visual Studio.

#### <a name="to-test-the-extension"></a>Otestování rozšíření

1. V experimentální instanci aplikace [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] na panelu nabídky vyberte možnost **Zobrazit**  >  **Průzkumník serveru**.

2. Proveďte následující kroky, pokud se web služby SharePoint, který chcete použít pro testování, nezobrazuje v uzlu **připojení služby SharePoint** v **Průzkumník serveru**:

    1. V **Průzkumník serveru** otevřete místní nabídku pro **připojení služby SharePoint** a poté zvolte možnost **Přidat připojení**.

    2. V dialogovém okně **Přidat připojení služby SharePoint** zadejte adresu URL webu služby SharePoint, ke kterému se chcete připojit, a poté klikněte na tlačítko **OK** .

         Pokud chcete na svém vývojovém počítači zadat SharePointový web, zadejte **http://localhost** .

3. Rozbalte uzel připojení lokality (zobrazuje adresu URL vašeho webu) a potom rozbalte uzel podřízené lokality (například **týmový web**).

4. Ověřte, zda kód v jiné instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zastaví na zarážce, kterou jste nastavili dříve v `NodeChildrenRequested` metodě, a pak zvolte **F5** pro pokračování v ladění projektu.

5. V experimentální instanci aplikace Visual Studio ověřte, že se v uzlu lokalita nejvyšší úrovně zobrazuje nový uzel s názvem **Galerie webových částí** , a poté rozbalte uzel **Galerie webových částí** .

6. Ověřte, zda se kód v jiné instanci sady Visual Studio zastaví na zarážce, kterou jste nastavili dříve v `CreateWebPartNodes` metodě, a pak zvolte klávesu **F5** pro pokračování v ladění projektu.

7. V experimentální instanci aplikace Visual Studio ověřte, že se všechny Webové části připojeného webu zobrazují v uzlu **Galerie webových částí** v **Průzkumník serveru**.

8. V **Průzkumník serveru** otevřete místní nabídku pro jednu z webové části a zvolte možnost **vlastnosti**.

9. V instanci, kterou [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ladíte, ověřte, že se v okně **vlastnosti** zobrazí podrobnosti o webové části.

## <a name="uninstall-the-extension-from-visual-studio"></a>Odinstalace rozšíření ze sady Visual Studio
 Po dokončení testování rozšíření odinstalujte rozšíření ze sady Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Odinstalace rozšíření

1. V experimentální instanci aplikace [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] na řádku nabídek vyberte možnost **Tools**  >  **rozšíření a aktualizace** nástrojů.

     Otevře se dialogové okno **rozšíření a aktualizace** .

2. V seznamu rozšíření zvolte **rozšíření uzel galerie webových částí pro Průzkumník serveru** a pak klikněte na tlačítko **odinstalovat** .

3. V dialogovém okně, které se zobrazí, kliknutím na tlačítko **Ano** potvrďte, že chcete rozšíření odinstalovat, a kliknutím na tlačítko **restartovat nyní** dokončete odinstalaci.

4. Zavřete obě instance aplikace Visual Studio (experimentální instance a instance sady Visual Studio, ve které je řešení WebPartNode otevřeno).

## <a name="see-also"></a>Viz také
- [Rozšíří uzel připojení služby SharePoint v Průzkumník serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Návod: volání do objektového modelu klienta služby SharePoint v rozšíření Průzkumník serveru](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [Editor obrázků pro ikony](/cpp/windows/image-editor-for-icons)
- [Vytvoření ikony nebo jiného obrázku &#40;Editor obrázků pro ikony&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)