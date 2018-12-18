---
title: 'Návod: Rozšiřování typu položky projektu služby SharePoint | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 756486daa709efd6ce1ff697d6d190bb7f4a2e34
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295719"
---
# <a name="walkthrough-extend-a-sharepoint-project-item-type"></a>Návod: Rozšíření typu položky projektu SharePoint
  Můžete použít **Model Připojení obchodních dat** položku projektu pro vytvoření modelu služby připojení dat obchodní (BDC) ve službě SharePoint. Ve výchozím nastavení když vytvoříte model pomocí tuto položku projektu data v modelu se uživatelům nezobrazí. Musíte také vytvořit externí seznam na Sharepointu a umožňují uživatelům zobrazovat data.  
  
 V tomto návodu vytvoříte rozšíření pro **Model Připojení obchodních dat** položky projektu. Mohou vývojáři rozšíření vytvořit externí seznam v jejich projektu, který zobrazuje data v modelu služby BDC. Tento návod demonstruje následující úkoly:  
  
-   Vytváření rozšíření pro Visual Studio, který provádí dvě hlavní úlohy:  
  
    -   Generuje externí seznam, který zobrazuje data v modelu služby BDC. Rozšíření používá objektový model pro projekt systému SharePoint ke generování *Elements.xml* soubor, který definuje seznam. Také přidá soubor do projektu tak, aby byl nasazen spolu s modelem služby BDC.  
  
    -   Přidá položky místní nabídky k **Model Připojení obchodních dat** položky v projektu **Průzkumníka řešení**. Vývojáři mohou kliknutím na tuto položku nabídky generovat externí seznam pro model služby BDC.  
  
-   Vytváření rozšíření aplikace Visual Studio (VSIX) balíčku pro nasazení sestavení rozšíření.  
  
-   Testování rozšíření.  
  
## <a name="prerequisites"></a>Požadavky  
 Budete potřebovat následující komponenty na vývojovém počítači k dokončení tohoto návodu:  
  
- Podporované vydání systému Microsoft Windows, SharePoint a Visual Studio.  
  
- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Tento návod používá **projekt VSIX** šablony v sadě SDK k vytvoření balíčku VSIX k nasazení položky projektu. Další informace najdete v tématu [rozšíření nástrojů SharePoint v sadě Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Znalost následujících konceptů je užitečná, ale není požadována k dokončení návodu:  
  
- Služba BDC v [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]. Další informace najdete v tématu [architektura BDC](http://go.microsoft.com/fwlink/?LinkId=177798).  
  
- Schéma XML pro modely služby BDC. Další informace najdete v tématu [Infrastruktura modelu služby BDC](http://go.microsoft.com/fwlink/?LinkId=177799).  
  
## <a name="create-the-projects"></a>Vytváření projektů
 K dokončení tohoto návodu, musíte vytvořit dva projekty:  
  
- Projekt VSIX k vytvoření balíčku VSIX k nasazení rozšíření položky projektu.  
  
- Projekt knihovny tříd, který implementuje rozšíření položky projektu.  
  
  Začněte postup vytvořením projektů.  
  
#### <a name="to-create-the-vsix-project"></a>Vytvoření projektu VSIX  
  
1.  Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  V panelu nabídky zvolte **souboru** > **nový** > **projektu**.  
  
3.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** uzly a klikněte na tlačítko **rozšiřitelnost** uzlu.  
  
    > [!NOTE]  
    >  **Rozšiřitelnost** uzel je dostupný jenom v případě, že nainstalujete Visual Studio SDK. Další informace najdete v oddílu požadavky dříve v tomto tématu.  
  
4.  V seznamu v horní části **nový projekt** dialogového okna zvolte **rozhraní .NET Framework 4.5**.  
  
     Rozšíření nástrojů SharePoint vyžaduje funkce v této verzi rozhraní .NET Framework.  
  
5.  Zvolte **projekt VSIX** šablony.  
  
6.  V **název** zadejte **GenerateExternalDataLists**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **GenerateExternalDataLists** projektu **Průzkumníka řešení**.  
  
7.  Pokud se soubor source.extension.vsixmanifest neotevře automaticky, otevřete místní nabídku v projektu GenerateExternalDataLists a zvolte **otevřít**  
  
8.  Ověřte, zda soubor source.extension.vsixmanifest obsahuje neprázdnou položku (zadejte Contoso) pro pole Autor, uložte soubor a zavřete jej.  
  
#### <a name="to-create-the-extension-project"></a>Chcete-li vytvořit projekt rozšíření  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku **GenerateExternalDataLists** uzel řešení, zvolte **přidat**a klikněte na tlačítko **nový projekt**.  
  
2.  V **přidat nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** uzly a klikněte na tlačítko **Windows** uzlu.  
  
3.  V seznamu v horní části dialogového okna zvolte **rozhraní .NET Framework 4.5**.  
  
4.  V seznamu šablon projektu vyberte **knihovny tříd**.  
  
5.  V **název** zadejte **BdcProjectItemExtension**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **BdcProjectItemExtension** projektu do řešení a otevře soubor výchozího kódu Class1.  
  
6.  Odstraňte soubor kódu Class1 z projektu.  
  
## <a name="configure-the-extension-project"></a>Konfigurace projektu rozšíření
 Než napíšete kód pro vytvoření rozšíření položky projektu, přidejte soubory kódu a odkazy na sestavení do projektu rozšíření.  
  
#### <a name="to-configure-the-project"></a>Konfigurace projektu  
  
1.  V projektu BdcProjectItemExtension přidejte dva soubory kódu, které mají následující názvy:  
  
    -   ProjectItemExtension  
  
    -   GenerateExternalDataLists  
  
2.  Zvolte projekt BdcProjectItemExtension a pak na panelu nabídek zvolte **projektu** > **přidat odkaz**.  
  
3.  V části **sestavení** uzlu, vyberte **Framework** uzlu a zaškrtněte políčko pro každé následující sestavení:  
  
    -   System.ComponentModel.Composition  
  
    -   WindowsBase  
  
4.  V části **sestavení** uzlu, vyberte **rozšíření** uzel a potom zaškrtněte políčko pro následující sestavení:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Zvolte **OK** tlačítko.  
  
## <a name="define-the-project-item-extension"></a>Definování rozšíření položky projektu
 Vytvořte třídu, která definuje rozšíření **Model Připojení obchodních dat** položky projektu. Chcete-li definovat rozšíření, třída implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> rozhraní. Toto rozhraní implementujte, kdykoli budete chtít rozšířit existující typ položky projektu.  
  
#### <a name="to-define-the-project-item-extension"></a>Chcete-li definovat rozšíření položky projektu  
  
1.  Vložte následující kód do souboru s kódem ProjectItemExtension.  
  
    > [!NOTE]  
    >  Po přidání tohoto kódu bude mít projekt několik chyb kompilace. K těmto chybám předejdete přidáním kódu v dalších krocích.  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]  
  
## <a name="create-the-external-data-lists"></a>Vytváření seznamů externích dat
 Přidejte částečnou definici `GenerateExternalDataListsExtension` třídu, která vytváří seznam externích dat pro každou entitu v modelu služby BDC. Chcete-li vytvořit seznam externích dat, tento kód nejprve čte data subjektu v modelu služby BDC pomocí analýzy dat XML v souboru modelu služby BDC. Potom vytvoří instanci seznamu, která je založená na modelu služby BDC a přidá tuto instanci seznamu do projektu.  
  
#### <a name="to-create-the-external-data-lists"></a>Chcete-li vytvořit seznam externích dat  
  
1.  Vložte následující kód do souboru s kódem GenerateExternalDataLists.  
  
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku návodu je celý kód pro rozšíření položky projektu v projektu. Sestavte řešení, abyste měli jistotu, že se projekt zkompiluje bez chyb.  
  
#### <a name="to-build-the-solution"></a>Abyste mohli sestavit řešení  
  
1.  V panelu nabídky zvolte **sestavení** > **sestavit řešení**.  
  
## <a name="create-a-vsix-package-to-deploy-the-project-item-extension"></a>Vytvoření balíčku VSIX k nasazení rozšíření položky projektu
 Pokud chcete nasadit rozšíření, použijte VSIX projekt ve vašem řešení k vytvoření balíčku VSIX. Nejprve nakonfigurujte VSIX balíček úpravou souboru source.extension.vsixmanifest, který je součástí projektu VSIX. Potom vytvořte VSIX balíček vytvořením řešení.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Konfigurace a vytvoření balíčku VSIX  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro soubor source.extension.vsixmanifest v projektu GenerateExternalDataLists a zvolte **otevřete**.  
  
     Visual Studio otevře soubor v editoru manifestu. Soubor source.extension.vsixmanifest je že základem pro soubor extension.vsixmanifest nutného pro všechny balíčky VSIX. Další informace o tomto souboru najdete v tématu [odkaz 1.0 schématu rozšíření VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  V **název produktu** zadejte **Generátor seznamu externích dat**.  
  
3.  V **Autor** zadejte **Contoso**.  
  
4.  V **popis** zadejte **rozšíření pro položky projektu Model Připojení obchodních dat, které lze použít pro vygenerování seznamu externích dat**.  
  
5.  Na **prostředky** kartu Editor, zvolte **nový** tlačítko.  
  
     **Přidat nové aktivum** zobrazí se dialogové okno.  
  
6.  V **typ** klikněte na položku **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Tato hodnota odpovídá `MefComponent` element v souboru extension.vsixmanifest. Tento prvek určuje název sestavení rozšíření v balíčku souboru VSIX. Další informace najdete v tématu [MEFComponent – Element (VSX schéma)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  V **zdroj** klikněte na položku **projekt v aktuálním řešení**.  
  
8.  V **projektu** klikněte na položku **BdcProjectItemExtension**a klikněte na tlačítko **OK** tlačítko.  
  
9. V panelu nabídky zvolte **sestavení** > **sestavit řešení**.  
  
10. Ujistěte se, že se projekt zkompiluje a sestaví bez chyb.  
  
11. Ujistěte se, že výstupní složka sestavení pro projekt GenerateExternalDataLists nyní obsahuje soubor GenerateExternalDataLists.vsix.  
  
     Výchozí je výstupní složka sestavení... složky \Bin\Debug ve složce, která obsahuje váš soubor projektu.  
  
## <a name="test-the-project-item-extension"></a>Testování rozšíření položky projektu
 Nyní jste připraveni k testování rozšíření položky projektu. Nejprve spusťte ladění projektu rozšíření v experimentální instanci sady Visual Studio. Potom použijte rozšíření v experimentální instanci sady Visual Studio k vytvoření externího seznamu pro model služby BDC. Nakonec otevřete externí seznam na Sharepointovém webu k ověření, že funguje podle očekávání.  
  
#### <a name="to-start-debugging-the-extension"></a>Chcete-li začít ladit rozšíření  
  
1.  V případě potřeby restartujte sadu Visual Studio s přihlašovacími údaji správce a pak otevřete řešení GenerateExternalDataLists.  
  
2.  V projektu BdcProjectItemExtension otevřete soubor s kódem ProjectItemExtension a přidejte zarážku na řádek kódu `Initialize` metody.  
  
3.  Otevřete soubor s kódem GenerateExternalDataLists a na první řádek kódu přidejte zarážku `GenerateExternalDataLists_Execute` metody.  
  
4.  Spuštění ladění zvolením **F5** klíče nebo na panelu nabídek, výběrem **ladění** > **spustit ladění**.  
  
     Visual Studio nainstaluje rozšíření do %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External Data List Generator\1. 0 a spustí experimentální instanci sady Visual Studio. Položku projektu budete testovat v této instanci aplikace Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Chcete-li testovat rozšíření  
  
1.  V experimentální instanci sady Visual Studio na panelu nabídek zvolte **souboru** > **nový** > **projektu**.  
  
2.  V **nový projekt** dialogového okna rozbalte **šablony** uzlu, rozbalte **Visual C#** uzlu, rozbalte **SharePoint** uzel a pak Zvolte **2010**.  
  
3.  V seznamu v horní části dialogového okna, ujistěte se, že **rozhraní .NET Framework 3.5** zaškrtnuto. Projekty pro [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] vyžadují tuto verzí rozhraní .NET Framework.  
  
4.  V seznamu šablon projektu vyberte **projektu služby SharePoint 2010**.  
  
5.  V **název** zadejte **SharePointProjectTestBDC**a klikněte na tlačítko **OK** tlačítko.  
  
6.  Průvodce přizpůsobením SharePoint zadejte adresu URL webu, který chcete použít pro ladění, zvolte **nasadit jako řešení farmy**a klikněte na tlačítko **Dokončit** tlačítko.  
  
7.  Otevřete místní nabídku projektu SharePointProjectTestBDC, vyberte možnost **přidat**a klikněte na tlačítko **nová položka**.  
  
8.  V **přidat NewItem – SharePointProjectTestBDC** dialogového okna rozbalte uzel nainstalovaného jazyka, rozbalte položku **SharePoint** uzlu.  
  
9. Zvolte **2010** uzel a klikněte na tlačítko **Model Připojení obchodních dat (pouze řešení farmy)** šablony.  
  
10. V **název** zadejte **TestBDCModel**a klikněte na tlačítko **přidat** tlačítko.  
  
11. Ověřte, že kód ve druhé instanci aplikace Visual Studio zastaví na zarážce, kterou jste nastavili v `Initialize` metoda souboru s kódem ProjectItemExtension.  
  
12. V zastavené instanci Visual Studio, zvolte **F5** klíče, nebo v řádku nabídek zvolte **ladění** > **pokračovat** a pokračujte v ladění projektu.  
  
13. V experimentální instanci sady Visual Studio, zvolte **F5** klíče, nebo na panelu nabídek zvolte **ladění** > **spustit ladění** Pokud chcete sestavit, nasadit a spustit **TestBDCModel** projektu.  
  
     Webový prohlížeč otevře výchozí stránku webu služby SharePoint, která je určena pro ladění.  
  
14. Ověřte, že **uvádí** oddíl v oblast Snadné spuštění ještě neobsahuje seznam, který je založen na výchozím modelu služby BDC v projektu. Seznam externích dat, musíte nejprve vytvořit buď pomocí uživatelského rozhraní služby SharePoint, nebo pomocí rozšíření položky projektu.  
  
15. Zavřete webový prohlížeč.  
  
16. V instanci aplikace Visual Studio, který má projekt TestBDCModel, otevřete místní nabídku **TestBDCModel** uzel v **Průzkumníka řešení**a klikněte na tlačítko **Generovat externí Data Seznam**.  
  
17. Ověřte, že kód ve druhé instanci aplikace Visual Studio zastaví na zarážce, kterou jste nastavili v `GenerateExternalDataLists_Execute` metody. Zvolte **F5** klíče, nebo na panelu nabídek zvolte **ladění** > **pokračovat** a pokračujte v ladění projektu.  
  
18. Experimentální instanci sady Visual Studio přidá instanci seznamu s názvem **Entity1DataList** k TestBDCModel projektu a instance také vytváří funkci s názvem **Feature2** pro seznam instance.  
  
19. Zvolte **F5** klíče, nebo na panelu nabídek zvolte **ladění** > **spustit ladění** k sestavení, nasazení a spuštění projektu TestBDCModel.  
  
     Webový prohlížeč otevře výchozí stránku webu služby SharePoint, který slouží k ladění.  
  
20. V **uvádí** části oblasti Snadné spuštění zvolte **Entity1DataList** seznamu.  
  
21. Ověřte, zda seznam obsahuje sloupce, které jsou s názvem Identifier1 a Message a jednu položku, která má hodnotu 0 Identifier1 a Message s hodnotou Hello World.  
  
     **Model Připojení obchodních dat** šablona projektu generuje výchozí model BDC, který poskytuje všechna tato data.  
  
22. Zavřete webový prohlížeč.  
  
## <a name="clean-up-the-development-computer"></a>Vyčištění vývojovém počítači
 Po dokončení testování rozšíření položky projektu, odebrat externí seznam a model služby BDC z webu služby SharePoint a odeberte rozšíření položky projektu v sadě Visual Studio.  
  
#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>Odebrat seznam externích dat z webu služby SharePoint  
  
1.  V oblasti Snadné spuštění webu služby SharePoint, zvolte **Entity1DataList** seznamu.  
  
2.  Na pásu karet na webu služby SharePoint, zvolte **seznamu** kartu.  
  
3.  Na **seznamu** kartě **nastavení** skupině, zvolte **nastavení seznamu**.  
  
4.  V části **oprávnění a správa**, zvolte **odstranit tento seznam**a klikněte na tlačítko **OK** potvrďte, že chcete odeslat seznam do odpadkového koše.  
  
5.  Zavřete webový prohlížeč.  
  
#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>Odebrat model služby BDC z webu služby SharePoint  
  
1.  V experimentální instanci sady Visual Studio na panelu nabídek zvolte **sestavení** > **odvolat**.  
  
     Visual Studio odebere model služby BDC z webu služby SharePoint.  
  
#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Chcete-li odebrat rozšíření položky projektu v sadě Visual Studio  
  
1.  V experimentální instanci sady Visual Studio na panelu nabídek zvolte **nástroje** > **rozšíření a aktualizace**.  
  
     **Rozšíření a aktualizace** zobrazí se dialogové okno.  
  
2.  V seznamu rozšíření zvolte **Generátor seznamu externích dat**a klikněte na tlačítko **odinstalovat** tlačítko.  
  
3.  V dialogovém okně, které se zobrazí, zvolte **Ano** potvrďte, že chcete odinstalovat rozšíření.  
  
4.  Zvolte **restartovat nyní** dokončete odinstalaci.  
  
5.  Zavřete obě instance programu Visual Studio (experimentální instanci a instanci, ve kterém je otevřené řešení GenerateExternalDataLists).  
  
## <a name="see-also"></a>Viz také:
 [Rozšíření systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Navrhování modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  
