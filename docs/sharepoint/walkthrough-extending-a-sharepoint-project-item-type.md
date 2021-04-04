---
title: 'Návod: rozšíření typu položky projektu služby SharePoint | Microsoft Docs'
description: V tomto návodu vytvořte rozšíření pro typ položky projektu služby SharePoint, jako je například položka projektu modelu připojení obchodních dat (BDC).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a91cbd863ed613804418cd5d1666412a01f8f542
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217694"
---
# <a name="walkthrough-extend-a-sharepoint-project-item-type"></a>Návod: rozšiřování typu položky projektu služby SharePoint
  Pomocí položky projektu **Model připojení obchodních dat** můžete vytvořit model služby pro připojení obchodních dat (BDC) na SharePointu. Ve výchozím nastavení platí, že při vytváření modelu pomocí této položky projektu se data v modelu nezobrazují uživatelům. Musíte také vytvořit externí seznam na SharePointu, aby uživatelé mohli zobrazit data.

 V tomto návodu vytvoříte rozšíření pro položku projektu **Model připojení obchodních dat** . Vývojáři mohou použít rozšíření k vytvoření externího seznamu v rámci projektu, který zobrazuje data v modelu služby BDC. Tento názorný postup ukazuje následující úlohy:

- Vytvoření rozšíření aplikace Visual Studio, které provádí dvě hlavní úlohy:

  - Vygeneruje externí seznam, který zobrazuje data v modelu služby BDC. Rozšíření používá objektový model pro systém projektu služby SharePoint k vygenerování *Elements.xml* souboru definujícího seznam. Také přidá soubor do projektu, aby byl nasazen společně s modelem služby BDC.

  - Přidá položku místní nabídky do **modelu připojení obchodních dat** do položek projektu v **Průzkumník řešení**. Vývojáři můžou kliknout na tuto položku nabídky a vygenerovat externí seznam pro model služby BDC.

- Sestavení balíčku rozšíření sady Visual Studio (VSIX) pro nasazení sestavení rozšíření.

- Testování rozšíření.

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto Názorného postupu potřebujete na vývojovém počítači následující komponenty:

- Podporované edice Microsoft Windows, SharePointu a sady Visual Studio.

- Hodnota [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] Tento návod používá šablonu **projektu VSIX** v sadě SDK k vytvoření balíčku VSIX pro nasazení položky projektu. Další informace najdete v tématu věnovaném [rozšiřování nástrojů služby SharePoint v aplikaci Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znalosti následujících konceptů jsou užitečné, ale nevyžadují se k dokončení tohoto postupu:

- Služba BDC v [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] . Další informace najdete v tématu [Architektura služby BDC](/previous-versions/office/developer/sharepoint-2010/ee558876(v=office.14)).

- Schéma XML pro modely služby BDC. Další informace najdete v tématu [infrastruktura modelů služby BDC](/previous-versions/office/developer/sharepoint-2010/ee556378(v=office.14)).

## <a name="create-the-projects"></a>Vytváření projektů
 Chcete-li dokončit tento návod, je nutné vytvořit dva projekty:

- Projekt VSIX pro vytvoření balíčku VSIX pro nasazení rozšíření položky projektu.

- Projekt knihovny tříd, který implementuje rozšíření položky projektu.

  Spusťte návod vytvořením projektů.

#### <a name="to-create-the-vsix-project"></a>Vytvoření projektu VSIX

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

3. V dialogovém okně **Nový projekt** rozbalte uzly **Visual C#** nebo **Visual Basic** a pak zvolte uzel **rozšiřitelnost** .

    > [!NOTE]
    > Uzel **rozšiřitelnosti** je k dispozici pouze v případě, že instalujete sadu Visual Studio SDK. Další informace najdete v části požadavky výše v tomto tématu.

4. V seznamu v horní části dialogového okna **Nový projekt** vyberte možnost **.NET Framework 4,5**.

     Rozšíření nástrojů služby SharePoint vyžadují funkce v této verzi .NET Framework.

5. Vyberte šablonu **projektu VSIX** .

6. Do pole **název** zadejte **GenerateExternalDataLists** a pak klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **GenerateExternalDataLists** do **Průzkumník řešení**.

7. Pokud se soubor source. extension. vsixmanifest neotevře automaticky, otevřete jeho místní nabídku v projektu GenerateExternalDataLists a pak zvolte **otevřít** .

8. Ověřte, že soubor source. extension. vsixmanifest obsahuje položku, která není prázdná (zadejte contoso) pro pole Author, uložte soubor a pak ho zavřete.

#### <a name="to-create-the-extension-project"></a>Vytvoření projektu rozšíření

1. V **Průzkumník řešení** otevřete místní nabídku uzlu řešení **GenerateExternalDataLists** , zvolte možnost **Přidat** a pak zvolte možnost **Nový projekt**.

2. V dialogovém okně **Přidat nový projekt** rozbalte uzly **Visual C#** nebo **Visual Basic** a pak vyberte uzel **Windows** .

3. V seznamu v horní části dialogového okna vyberte možnost **.NET Framework 4,5**.

4. V seznamu šablon projektu vyberte možnost **Knihovna tříd**.

5. Do pole **název** zadejte **BdcProjectItemExtension** a poté klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **BdcProjectItemExtension** do řešení a otevře soubor Default Class1 Code.

6. Odstraňte soubor kódu Class1 z projektu.

## <a name="configure-the-extension-project"></a>Konfigurace projektu rozšíření
 Předtím, než napíšete kód pro vytvoření rozšíření položky projektu, přidejte soubory kódu a odkazy na sestavení do projektu rozšíření.

#### <a name="to-configure-the-project"></a>Konfigurace projektu

1. V projektu BdcProjectItemExtension přidejte dva soubory kódu, které mají následující názvy:

    - ProjectItemExtension

    - GenerateExternalDataLists

2. Zvolte projekt BdcProjectItemExtension a pak na panelu nabídek zvolte **projekt**  >  **Přidat odkaz**.

3. V uzlu **sestavení** zvolte uzel **rozhraní** a zaškrtněte políčko pro každé z následujících sestavení:

    - System. ComponentModel. složení

    - WindowsBase

4. V uzlu **sestavení** zvolte uzel **rozšíření** a potom zaškrtněte políčko pro následující sestavení:

    - Microsoft. VisualStudio. SharePoint

5. Klikněte na tlačítko **OK** .

## <a name="define-the-project-item-extension"></a>Definovat rozšíření položky projektu
 Vytvořte třídu, která definuje rozšíření pro položku projektu **modelu připojení obchodních dat** . Pro definování rozšíření třída implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> rozhraní. Implementovat toto rozhraní vždy, když chcete zvětšit existující typ položky projektu.

#### <a name="to-define-the-project-item-extension"></a>Definování rozšíření položky projektu

1. Vložte následující kód do souboru kódu ProjectItemExtension.

    > [!NOTE]
    > Po přidání tohoto kódu dojde k chybě kompilace v projektu. Tyto chyby zůstanou při přidávání kódu v pozdějších krocích nepřítomné.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb" id="Snippet1":::

## <a name="create-the-external-data-lists"></a>Vytvoření seznamů externích dat
 Přidejte částečnou definici `GenerateExternalDataListsExtension` třídy, která vytvoří seznam externích dat pro každou entitu v modelu služby BDC. Chcete-li vytvořit seznam externích dat, tento kód nejprve přečte data entity v modelu služby BDC pomocí analýzy dat XML v souboru modelu služby BDC. Pak vytvoří instanci seznamu, která je založena na modelu služby BDC a přidá tuto instanci seznamu do projektu.

#### <a name="to-create-the-external-data-lists"></a>Vytvoření seznamů externích dat

1. Vložte následující kód do souboru kódu GenerateExternalDataLists.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs" id="Snippet2":::

## <a name="checkpoint"></a>CheckPoint
 V tomto okamžiku v tomto návodu je veškerý kód pro rozšíření položky projektu nyní v projektu. Sestavte řešení, abyste se ujistili, že se projekt zkompiluje bez chyb.

#### <a name="to-build-the-solution"></a>Sestavení řešení

1. Na řádku nabídek klikněte na **sestavit** sestavení  >  **řešení**.

## <a name="create-a-vsix-package-to-deploy-the-project-item-extension"></a>Vytvoření balíčku VSIX pro nasazení rozšíření položky projektu
 Chcete-li nasadit rozšíření, použijte VSIX projekt ve vašem řešení k vytvoření balíčku VSIX. Nejdřív nakonfigurujte balíček VSIX úpravou souboru source. extension. vsixmanifest, který je zahrnutý v projektu VSIX. Pak vytvořte balíček VSIX sestavením řešení.

#### <a name="to-configure-and-create-the-vsix-package"></a>Konfigurace a vytvoření balíčku VSIX

1. V **Průzkumník řešení** otevřete místní nabídku pro soubor source. extension. vsixmanifest v projektu GenerateExternalDataLists a pak zvolte **otevřít**.

     Visual Studio otevře soubor v editoru manifestu. Soubor source. extension. vsixmanifest je základem pro soubor Extension. vsixmanifest, který je vyžadován všemi balíčky VSIX. Další informace o tomto souboru najdete v referenčních informacích k [schématu rozšíření VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. Do pole **název produktu** zadejte **Generátor seznamu externích dat**.

3. Do pole **Autor** zadejte **Contoso**.

4. Do pole **Popis** zadejte **rozšíření pro položky projektu model připojení obchodních dat, které lze použít ke generování seznamů externích dat**.

5. Na kartě **assets (prostředky** ) Editoru klikněte na tlačítko **Nový** .

     Zobrazí se dialogové okno **Přidat nový prostředek** .

6. V seznamu **typ** vyberte možnost **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Tato hodnota odpovídá `MefComponent` prvku v souboru extension. vsixmanifest. Tento prvek určuje název sestavení rozšíření v balíčku VSIX. Další informace naleznete v tématu [MefComponent element (VSX Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. V seznamu **zdroj** vyberte **projekt v aktuálním řešení**.

8. V seznamu **projekt** zvolte možnost **BdcProjectItemExtension** a pak klikněte na tlačítko **OK** .

9. Na řádku nabídek klikněte na **sestavit** sestavení  >  **řešení**.

10. Ujistěte se, že se projekt zkompiluje a sestaví bez chyb.

11. Ujistěte se, že výstupní složka sestavení pro projekt GenerateExternalDataLists nyní obsahuje soubor GenerateExternalDataLists. VSIX.

     Ve výchozím nastavení je výstupní složka sestavení.. Složka \bin\Debug ve složce, která obsahuje soubor projektu.

## <a name="test-the-project-item-extension"></a>Testování rozšíření položky projektu
 Nyní jste připraveni k otestování rozšíření položky projektu. Nejprve spusťte ladění projektu rozšíření v experimentální instanci aplikace Visual Studio. Pak použijte rozšíření v experimentální instanci aplikace Visual Studio k vygenerování externího seznamu pro model služby BDC. Nakonec otevřete externí seznam na webu služby SharePoint a ověřte, zda funguje podle očekávání.

#### <a name="to-start-debugging-the-extension"></a>Spuštění ladění rozšíření

1. V případě potřeby restartujte Visual Studio s přihlašovacími údaji správce a pak otevřete řešení GenerateExternalDataLists.

2. V projektu BdcProjectItemExtension otevřete soubor kódu ProjectItemExtension a poté přidejte zarážku do řádku kódu v `Initialize` metodě.

3. Otevřete soubor kódu GenerateExternalDataLists a pak přidejte zarážku do prvního řádku kódu v `GenerateExternalDataLists_Execute` metodě.

4. Spusťte ladění tak, že vyberete klávesu **F5** nebo v řádku nabídek vyberete **ladění**  >  **Spustit ladění**.

     Visual Studio nainstaluje rozšíření do%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External data list Generator\1.0 a spustí experimentální instanci sady Visual Studio. Budete testovat položku projektu v této instanci aplikace Visual Studio.

#### <a name="to-test-the-extension"></a>Otestování rozšíření

1. V experimentální instanci aplikace Visual Studio, na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

2. V dialogovém okně **Nový projekt** rozbalte uzel **šablony** , rozbalte uzel **Visual C#** , rozbalte uzel **SharePoint** a pak zvolte **2010**.

3. V seznamu v horní části dialogového okna se ujistěte, že je vybrána možnost **.NET Framework 3,5** . Projekty pro [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] vyžadují tuto verzi .NET Framework.

4. V seznamu šablon projektu vyberte **projekt SharePoint 2010**.

5. Do pole **název** zadejte **SharePointProjectTestBDC** a poté klikněte na tlačítko **OK** .

6. V Průvodci vlastním nastavením služby SharePoint zadejte adresu URL webu, který chcete použít pro ladění, zvolte možnost **nasadit jako řešení farmy** a pak klikněte na tlačítko **Dokončit** .

7. Otevřete místní nabídku projektu SharePointProjectTestBDC, zvolte možnost **Přidat** a pak zvolte možnost **Nová položka**.

8. V dialogovém okně **Přidat zástupného prvku NewItem-SharePointProjectTestBDC** rozbalte uzel nainstalovaného jazyka a rozbalte uzel **služby SharePoint** .

9. Zvolte uzel **2010** a pak zvolte šablonu **Připojení obchodních dat (pouze řešení farmy)** .

10. Do pole **název** zadejte **TestBDCModel** a poté klikněte na tlačítko **Přidat** .

11. Ověřte, zda se kód v jiné instanci sady Visual Studio zastaví na zarážce, kterou jste nastavili v `Initialize` metodě souboru kódu ProjectItemExtension.

12. V zastavené instanci aplikace Visual Studio vyberte klávesu **F5** nebo v řádku nabídek vyberte možnost **ladit**  >  **pokračovat** a pokračujte v ladění projektu.

13. V experimentální instanci aplikace Visual Studio vyberte klávesu **F5** nebo v řádku nabídek vyberte **ladit**  >  **Spustit ladění** pro sestavení, nasazení a spuštění projektu **TestBDCModel** .

     Webový prohlížeč otevře výchozí stránku webu služby SharePoint, která je určena pro ladění.

14. Ověřte, že oddíl **seznamy** v oblasti snadného spuštění zatím neobsahuje seznam, který je založený na výchozím modelu služby BDC v projektu. Je nutné nejprve vytvořit seznam externích dat buď pomocí uživatelského rozhraní služby SharePoint nebo pomocí rozšíření položky projektu.

15. Zavřete webový prohlížeč.

16. V instanci aplikace Visual Studio, která má otevřený projekt TestBDCModel otevřete místní nabídku uzlu **TestBDCModel** v **Průzkumník řešení** a pak zvolte možnost **Generovat seznam externích dat**.

17. Ověřte, zda se kód v jiné instanci sady Visual Studio zastaví na zarážce, kterou jste nastavili v `GenerateExternalDataLists_Execute` metodě. Klikněte na klávesu **F5** nebo na panelu nabídek vyberte možnost **ladit**  >  **pokračovat** a pokračujte v ladění projektu.

18. Experimentální instance sady Visual Studio přidá instanci seznamu s názvem **Entity1DataList** do projektu TestBDCModel a instance také vygeneruje funkci s názvem **Feature2** pro instanci seznamu.

19. Klikněte na klávesu **F5** nebo na panelu nabídek vyberte **ladit**  >  **Spustit ladění** pro sestavení, nasazení a spuštění projektu TestBDCModel.

     Webový prohlížeč otevře výchozí stránku webu služby SharePoint, která se používá pro ladění.

20. V části **seznamy** v oblasti snadné spuštění vyberte seznam **Entity1DataList** .

21. Ověřte, zda seznam obsahuje sloupce s názvem identifier1 a Message, kromě jedné položky, která má hodnotu identifier1 0 a hodnotu Hello World zprávy.

     Šablona projektu **Model připojení obchodních dat** vygeneruje výchozí model služby BDC, který poskytuje všechna tato data.

22. Zavřete webový prohlížeč.

## <a name="clean-up-the-development-computer"></a>Vyčištění vývojového počítače
 Po dokončení testování rozšíření položky projektu odeberte externí seznam a model služby BDC z webu služby SharePoint a odeberte rozšíření položky projektu ze sady Visual Studio.

#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>Odebrání seznamu externích dat z webu služby SharePoint

1. V oblasti snadné spuštění webu služby SharePoint vyberte seznam **Entity1DataList** .

2. Na pásu karet na webu služby SharePoint vyberte kartu **seznam** .

3. Na kartě **seznam** ve skupině **Nastavení** vyberte možnost **Nastavení seznamu**.

4. V části **oprávnění a Správa** zvolte **Odstranit tento seznam** a pak kliknutím na **OK** potvrďte, že chcete odeslat seznam do koše.

5. Zavřete webový prohlížeč.

#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>Odebrání modelu služby BDC z webu služby SharePoint

1. V experimentální instanci aplikace Visual Studio, na panelu nabídek vyberte možnost **sestavení**  >  **odvolání**.

     Visual Studio odebere model služby BDC z webu služby SharePoint.

#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Odebrání rozšíření položky projektu ze sady Visual Studio

1. V experimentální instanci aplikace Visual Studio, na panelu nabídek vyberte **nástroje**  >  **rozšíření a aktualizace**.

     Otevře se dialogové okno **rozšíření a aktualizace** .

2. V seznamu rozšíření zvolte **Generátor seznamu externích dat** a pak klikněte na tlačítko **odinstalovat** .

3. V dialogovém okně, které se zobrazí, kliknutím na **Ano** potvrďte, že chcete rozšíření odinstalovat.

4. Kliknutím na **restartovat nyní** dokončete odinstalaci.

5. Zavřete obě instance sady Visual Studio (experimentální instance a instance, ve které je řešení GenerateExternalDataLists otevřené).

## <a name="see-also"></a>Viz také
- [Rozšíří systém projektu služby SharePoint.](../sharepoint/extending-the-sharepoint-project-system.md)
- [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)