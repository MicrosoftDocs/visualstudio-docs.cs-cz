---
title: 'Průzkumník serveru: rozšíření uzlu připojení služby SharePoint'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d7f1ac5b0fb1f25d04139d76efa816ebd059d7da
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585573"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Návod: volání do objektového modelu klienta služby SharePoint v rozšíření Průzkumník serveru
  Tento návod ukazuje, jak volat objektový model klienta služby SharePoint z rozšíření pro uzel **připojení služby SharePoint** v **Průzkumník serveru**. Další informace o použití objektového modelu klienta služby SharePoint naleznete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

 Tento názorný postup ukazuje následující úlohy:

- Vytvoření [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozšíření, které rozšiřuje uzel **připojení sharepointu** **Průzkumník serveru** následujícími způsoby:

  - Rozšíření přidá uzel **Galerie webových částí** pod každým uzlem webu služby SharePoint v **Průzkumník serveru**. Tento nový uzel obsahuje podřízené uzly, které reprezentují jednotlivé webové části v galerii webových částí na webu.

  - Rozšíření definuje nový typ uzlu, který představuje instanci webové části. Tento nový typ uzlu je základem pro podřízené uzly v rámci nového uzlu **Galerie webových částí** . Nový typ uzlu webové části zobrazuje informace v okně **vlastnosti** o webové části, kterou uzel představuje.

- Sestavení balíčku rozšíření sady Visual Studio (VSIX) pro nasazení rozšíření.

- Ladění a testování rozšíření.

> [!NOTE]
> Rozšíření, které vytvoříte v tomto návodu, se podobá rozšíření, které jste vytvořili v [návodu: rozšíření Průzkumník serveru pro zobrazení webových částí](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). Tento návod používá objektový model serveru SharePoint, ale tento návod provádí stejné úlohy pomocí objektového modelu klienta.

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto Názorného postupu potřebujete na vývojovém počítači následující komponenty:

- Podporované edice Windows, SharePointu a sady Visual Studio.

- Sada Visual Studio SDK. Tento návod používá šablonu **projektu VSIX** v sadě SDK k vytvoření balíčku VSIX pro nasazení rozšíření. Další informace najdete v tématu věnovaném [rozšiřování nástrojů služby SharePoint v aplikaci Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

Znalosti následujících konceptů jsou užitečné, ale nevyžadují se k dokončení tohoto postupu:

- Pomocí objektového modelu klienta služby SharePoint. Další informace najdete v tématu [objektový model spravovaného klienta](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14)).

- Webové části ve službě SharePoint. Další informace najdete v tématu [přehled webové části](/previous-versions/office/ms432401(v=office.14)).

## <a name="create-the-projects"></a>Vytváření projektů
 Chcete-li dokončit tento návod, je nutné vytvořit dva projekty:

- Projekt VSIX k vytvoření balíčku VSIX k nasazení rozšíření **Průzkumník serveru** .

- Projekt knihovny tříd, který implementuje rozšíření **Průzkumník serveru** .

  Spusťte návod vytvořením projektů.

#### <a name="to-create-the-vsix-project"></a>Vytvoření projektu VSIX

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

3. V dialogovém okně **Nový projekt** rozbalte uzel **Visual C#** nebo **Visual Basic** a pak zvolte možnost **rozšiřitelnost**.

    > [!NOTE]
    > Uzel **rozšiřitelnosti** je k dispozici pouze v případě, že instalujete sadu Visual Studio SDK. Další informace najdete v části požadavky výše v tomto tématu.

4. V horní části dialogového okna vyberte v seznamu verzí .NET Framework **.NET Framework 4,5** .

     Rozšíření nástrojů služby SharePoint vyžadují funkce v této verzi .NET Framework.

5. Vyberte šablonu **projektu VSIX** .

6. Do pole **název** zadejte příkaz **WebPartNode**a pak klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **WebPartNode** do **Průzkumník řešení**.

#### <a name="to-create-the-extension-project"></a>Vytvoření projektu rozšíření

1. V **Průzkumník řešení**otevřete místní nabídku uzlu řešení, zvolte možnost **Přidat**a pak zvolte možnost **Nový projekt**.

2. V dialogovém okně  **Nový projekt** rozbalte uzel **Visual C#** nebo **Visual Basic** a pak zvolte možnost **Windows**.

3. V horní části dialogového okna vyberte v seznamu verzí .NET Framework **.NET Framework 4,5** .

4. V seznamu šablon projektu vyberte možnost **Knihovna tříd**.

5. Do pole **název** zadejte **WebPartNodeExtension**a pak klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **WebPartNodeExtension** do řešení a otevře soubor Default Class1 Code.

6. Odstraňte soubor kódu Class1 z projektu.

## <a name="configure-the-extension-project"></a>Konfigurace projektu rozšíření
 Předtím, než napíšete kód pro vytvoření rozšíření, je nutné přidat soubory kódu a odkazy na sestavení do projektu a musíte aktualizovat výchozí obor názvů.

#### <a name="to-configure-the-project"></a>Konfigurace projektu

1. V projektu **WebPartNodeExtension** přidejte dva soubory kódu s názvem SiteNodeExtension a WebPartNodeTypeProvider.

2. Otevřete místní nabídku projektu WebPartNodeExtension a pak zvolte možnost **Přidat odkaz**.

3. V dialogovém okně **Správce odkazů – WebPartNodeExtension** zvolte uzel **rozhraní** a potom zaškrtněte políčka pro sestavení System. ComponentModel. složení a System. Windows. Forms.

4. Zvolte uzel **rozšíření** , zaškrtněte políčko pro každé z následujících sestavení a pak klikněte na tlačítko **OK** :

    - Microsoft. SharePoint. Client

    - Microsoft. SharePoint. Client. Runtime

    - Microsoft. VisualStudio. SharePoint

5. Otevřete místní nabídku projektu **WebPartNodeExtension** a zvolte možnost **vlastnosti**.

     Otevře se **Návrhář projektu** .

6. Vyberte kartu **aplikace** .

7. Do pole **výchozí obor názvů** (C#) nebo **kořenového oboru názvů** (Visual Basic) zadejte **ServerExplorer. SharePointConnections. WebPartNode**.

## <a name="create-icons-for-the-new-nodes"></a>Vytvořit ikony pro nové uzly
 Vytvořte dvě ikony pro rozšíření **Průzkumník serveru** : ikonu pro nový uzel **Galerie webových** částí a další ikonu pro každý podřízený uzel webové části v uzlu **Galerie webových částí** . Později v tomto návodu napíšete kód, který přidruží tyto ikony k uzlům.

#### <a name="to-create-icons-for-the-nodes"></a>Vytvoření ikon pro uzly

1. V **Návrháři projektu** pro projekt WebPartNodeExtension klikněte na kartu **prostředky** .

2. Vyberte odkaz **Tento projekt neobsahuje výchozí soubor prostředků. Pokud ho chcete vytvořit, klikněte sem.**

     Visual Studio vytvoří soubor prostředků a otevře ho v návrháři.

3. V horní části návrháře klikněte na šipku v příkazu **Přidat prostředek** a zvolte možnost **Přidat novou ikonu**.

4. Jako název nové ikony zadejte **WebPartsNode** a pak klikněte na tlačítko **Přidat** .

     Nová ikona se otevře v **editoru obrázků**.

5. Upravte verzi 16x16 ikony tak, aby měla návrh, který můžete snadno rozpoznat.

6. Otevřete místní nabídku pro verzi 32x32 ikony a zvolte možnost **Odstranit typ obrázku**.

7. Opakujte kroky 3 až 7 pro přidání druhé ikony do prostředků projektu a pojmenujte tuto **webovou část**ikona.

8. V **Průzkumník řešení**ve složce **Resources** projektu **WebPartNodeExtension** vyberte *WebPartsNode. ico*.

9. V okně **vlastnosti** otevřete seznam **Akce sestavení** a pak zvolte možnost **Integrovaný prostředek**.

10. Zopakujte poslední dva kroky pro *WebPart. ico*.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Přidat uzel galerie webových částí do Průzkumník serveru
 Vytvořte třídu, která přidá nový uzel **Galerie webových částí** do každého uzlu webu služby SharePoint. Chcete-li přidat nový uzel, třída implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> rozhraní. Implementujte toto rozhraní vždy, když chcete rozšíření chování existujícího uzlu v **Průzkumník serveru**, jako je například přidání nového podřízeného uzlu do uzlu.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Přidání uzlu Galerie webových částí do Průzkumník serveru

1. Vložte následující kód do souboru kódu **SiteNodeExtension** pro projekt **WebPartNodeExtension** .

    > [!NOTE]
    > Po přidání tohoto kódu dojde k chybě kompilace v projektu. Tyto chyby zůstanou při přidávání kódu v pozdějších krocích nepřítomné.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Definujte typ uzlu, který představuje webovou část.
 Vytvořte třídu, která definuje nový typ uzlu, který představuje webovou část. Visual Studio používá tento nový typ uzlu k zobrazení podřízených uzlů v uzlu **Galerie webových částí** . Každý z těchto podřízených uzlů představuje jednu webovou část na webu služby SharePoint.

 Chcete-li definovat nový typ uzlu, třída implementuje <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> rozhraní. Implementujte toto rozhraní vždy, když chcete definovat nový typ uzlu v **Průzkumník serveru**.

#### <a name="to-define-the-web-part-node-type"></a>Definování typu uzlu webové části

1. Vložte následující kód do souboru kódu **WebPartNodeTypeProvider** pro projekt **WebPartNodeExtension** .

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]

## <a name="checkpoint"></a>CheckPoint
 V tomto okamžiku v tomto návodu je veškerý kód pro uzel **Galerie webových částí** teď v projektu. Sestavte projekt **WebPartNodeExtension** , abyste se ujistili, že se zkompiluje bez chyb.

#### <a name="to-build-the-project"></a>Sestavení projektu

1. V **Průzkumník řešení**otevřete místní nabídku projektu **WebPartNodeExtension** a pak zvolte možnost **sestavit**.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Vytvoření balíčku VSIX pro nasazení rozšíření
 Chcete-li nasadit rozšíření, použijte VSIX projekt ve vašem řešení k vytvoření balíčku VSIX. Nejdřív nakonfigurujte balíček VSIX úpravou souboru source. extension. vsixmanifest, který je zahrnutý v projektu. Pak vytvořte balíček VSIX sestavením řešení.

#### <a name="to-configure-the-vsix-package"></a>Konfigurace balíčku VSIX

1. V **Průzkumník řešení**v projektu **WebPartNode** otevřete soubor **source. extension. vsixmanifest** v editoru manifestu.

     Soubor source. extension. vsixmanifest je základem pro soubor Extension. vsixmanifest, který vyžaduje všechny balíčky VSIX. Další informace o tomto souboru najdete v referenčních informacích k [schématu rozšíření VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. Do pole **název produktu** zadejte **uzel galerie webových částí pro Průzkumník serveru**.

3. Do pole **Autor** zadejte **Contoso**.

4. V poli **Popis** zadejte do **uzlu připojení služby SharePoint v Průzkumník serveru přidat vlastní uzel galerie webových částí**.

5. Na kartě **assets (prostředky** ) Editoru klikněte na tlačítko **Nový** .

6. V dialogovém okně **Přidat nový prostředek** vyberte v seznamu **typ** možnost **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Tato hodnota odpovídá `MefComponent` prvku v souboru extension. vsixmanifest. Tento prvek určuje název sestavení rozšíření v balíčku VSIX. Další informace naleznete v tématu [MefComponent element (VSX Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. V seznamu **zdroj** vyberte **projekt v aktuálním řešení**.

8. V seznamu **projekt** zvolte **WebPartNodeExtension**a pak klikněte na tlačítko **OK** .

9. V panelu nabídek zvolte **sestavit**  >  **sestavení řešení**a pak se ujistěte, že se řešení zkompiluje bez chyb.

10. Ujistěte se, že výstupní složka sestavení pro projekt WebPartNode nyní obsahuje soubor WebPartNode. VSIX.

     Ve výchozím nastavení je výstupní složka sestavení.. Složka \bin\Debug ve složce, která obsahuje soubor projektu.

## <a name="test-the-extension"></a>Test rozšíření
 Nyní jste připraveni otestovat nový uzel **Galerie webových částí** v **Průzkumník serveru**. Nejprve spusťte ladění projektu rozšíření v experimentální instanci aplikace Visual Studio. Pak použijte nový uzel **webové části** v experimentální instanci aplikace Visual Studio.

#### <a name="to-start-debugging-the-extension"></a>Spuštění ladění rozšíření

1. Restartujte Visual Studio s přihlašovacími údaji správce a pak otevřete řešení **WebPartNode** .

2. V projektu WebPartNodeExtension otevřete soubor kódu **SiteNodeExtension** a poté přidejte zarážku do prvního řádku kódu v `NodeChildrenRequested` `CreateWebPartNodes` metodách a.

3. Kliknutím na klávesu **F5** spusťte ladění.

     Visual Studio nainstaluje rozšíření na rozšíření uzlu Galerie částí%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web pro server Explorer\1.0 a spustí experimentální instanci sady Visual Studio. Otestujete položku projektu v této instanci aplikace Visual Studio.

#### <a name="to-test-the-extension"></a>Otestování rozšíření

1. V experimentální instanci aplikace Visual Studio, na panelu nabídek vyberte možnost **Zobrazit**  >  **Průzkumník serveru**.

2. Ověřte, zda se web služby SharePoint, který chcete použít pro testování, zobrazuje v uzlu **připojení služby SharePoint** v **Průzkumník serveru**. Pokud není v seznamu uveden, postupujte takto:

    1. Otevřete místní nabídku pro **připojení služby SharePoint**a poté zvolte možnost **Přidat připojení**.

    2. V dialogovém okně **Přidat připojení služby SharePoint** zadejte adresu URL webu služby SharePoint, ke kterému se chcete připojit, a poté klikněte na tlačítko **OK** .

         Chcete-li na svém vývojovém počítači zadat web služby SharePoint, zadejte **http://localhost** .

3. Rozbalte uzel připojení lokality (zobrazuje adresu URL vašeho webu) a potom rozbalte uzel podřízené lokality (například **týmový web**).

4. Ověřte, zda se kód v jiné instanci sady Visual Studio zastaví na zarážce, kterou jste nastavili dříve v `NodeChildrenRequested` metodě, a pak zvolte klávesu **F5** pro pokračování v ladění projektu.

5. V experimentální instanci aplikace Visual Studio rozbalte uzel **Galerie webových částí** , který se zobrazí pod uzlem lokalita nejvyšší úrovně.

6. Ověřte, zda se kód v jiné instanci sady Visual Studio zastaví na zarážce, kterou jste nastavili dříve v `CreateWebPartNodes` metodě, a pak zvolte klávesu **F5** pro pokračování v ladění projektu.

7. V experimentální instanci aplikace Visual Studio ověřte, že se všechny Webové části připojené lokality zobrazí v uzlu **Galerie webových částí** v **Průzkumník serveru**.

8. Otevřete místní nabídku pro webovou část a zvolte možnost **vlastnosti**.

9. V okně **vlastnosti** ověřte, zda se zobrazí podrobnosti o webové části.

10. V **Průzkumník serveru**otevřete místní nabídku pro stejnou webovou část a zvolte možnost **Zobrazit zprávu**.

     V zobrazeném okně se zprávou klikněte na tlačítko **OK** .

## <a name="uninstall-the-extension-from-visual-studio"></a>Odinstalace rozšíření ze sady Visual Studio
 Po dokončení testování rozšíření ho odinstalujte ze sady Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Odinstalace rozšíření

1. V experimentální instanci aplikace Visual Studio, na panelu nabídek vyberte **nástroje**  >  **rozšíření a aktualizace**.

     Otevře se dialogové okno **rozšíření a aktualizace** .

2. V seznamu rozšíření zvolte **uzel galerie webových částí pro Průzkumník serveru**a pak klikněte na tlačítko **odinstalovat** .

3. V dialogovém okně, které se zobrazí, klikněte na tlačítko **Ano** .

4. Kliknutím na tlačítko **restartovat nyní** dokončete odinstalaci.

     Položka projektu je také odinstalována.

5. Zavřete obě instance aplikace Visual Studio (experimentální instance a instance sady Visual Studio, ve které je řešení WebPartNode otevřeno).

## <a name="see-also"></a>Viz také
- [Volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Rozšíří uzel připojení služby SharePoint v Průzkumník serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Návod: roztažení Průzkumník serveru pro zobrazení webových částí](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Editor obrázků pro ikony](/cpp/windows/image-editor-for-icons)
- [Vytvoření ikony nebo jiného obrázku &#40;Editor obrázků pro ikony&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)