---
title: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 2
titleSuffix: ''
description: V tomto návodu přidejte průvodce pro shromáždění informací od uživatelů, když používají šablonu položky k přidání položky projektu vlastní akce na webu služby SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4b6fad27342c086e551320977cdf712f816b383c
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217941"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 2
  Po definování vlastního typu položky projektu služby SharePoint a jejich přidružení k šabloně položky v aplikaci Visual Studio můžete také pro šablonu poskytnout průvodce. Průvodce můžete použít ke shromáždění informací z uživatelů při použití šablony k přidání nové instance položky projektu do projektu. Informace, které shromáždíte, lze použít k inicializaci položky projektu.

 V tomto návodu přidáte průvodce k položce projektu vlastní akce, která je znázorněna v [návodu: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Když uživatel přidá položku projektu vlastní akce do projektu služby SharePoint, průvodce shromáždí informace o vlastní akci (například jeho umístění a adresu URL pro přechod na, když ji koncový uživatel zvolí) a přidá tyto informace do souboru *Elements.xml* v nové položce projektu.

 Tento názorný postup ukazuje následující úlohy:

- Vytvoření průvodce pro vlastní typ položky projektu služby SharePoint, který je přidružen k šabloně položky.

- Definování vlastního uživatelského rozhraní průvodce, které se podobá vestavěným průvodcům pro položky projektu služby SharePoint v aplikaci Visual Studio.

- Použití nahraditelných parametrů k inicializaci souborů projektu služby SharePoint s daty, která shromažďujete v průvodci.

- Ladění a testování průvodce.

> [!NOTE]
> Ukázku si můžete stáhnout z [GitHubu](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) , kde se dozvíte, jak vytvořit vlastní aktivity pro pracovní postup.

## <a name="prerequisites"></a>Požadavky
 Chcete-li provést tento návod, je nutné nejprve vytvořit řešení CustomActionProjectItem dokončením [návodu: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 K dokončení tohoto Názorného postupu potřebujete také následující komponenty na vývojovém počítači:

- Podporované edice Windows, SharePointu a sady Visual Studio.

- Sada Visual Studio SDK. Tento návod používá šablonu **projektu VSIX** v sadě SDK k vytvoření balíčku VSIX pro nasazení položky projektu. Další informace najdete v tématu věnovaném [rozšiřování nástrojů služby SharePoint v aplikaci Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znalosti následujících konceptů jsou užitečné, ale nevyžadují se k dokončení tohoto postupu:

- Průvodci pro šablony projektů a položek v aplikaci Visual Studio. Další informace najdete v tématu [Postupy: použití průvodců se šablonami projektů](../extensibility/how-to-use-wizards-with-project-templates.md) a <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraním.

- Vlastní akce v SharePointu Další informace najdete v tématu [vlastní akce](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

## <a name="create-the-wizard-project"></a>Vytvoření projektu průvodce
 Chcete-li dokončit tento návod, je nutné přidat projekt do řešení CustomActionProjectItem, které jste vytvořili v [návodu: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Implementujete <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní a definujete uživatelské rozhraní průvodce v tomto projektu.

#### <a name="to-create-the-wizard-project"></a>Vytvoření projektu průvodce

1. V aplikaci Visual Studio otevřete řešení CustomActionProjectItem

2. V **Průzkumník řešení** otevřete místní nabídku uzlu řešení, zvolte možnost **Přidat** a pak zvolte možnost **Nový projekt**.

3. V dialogovém okně **Nový projekt** rozbalte uzly **Visual C#** nebo **Visual Basic** a pak vyberte uzel **Windows** .

4. V horní části dialogového okna **Nový projekt** se ujistěte, že je v seznamu verzí .NET Framework zvolena možnost **.NET Framework 4,5** .

5. Zvolte šablonu projektu **Knihovna uživatelských ovládacích prvků WPF** , pojmenujte si projekt **ItemTemplateWizard** a pak klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá do řešení projekt **ItemTemplateWizard** .

6. Odstraňte položku UserControl1 z projektu.

## <a name="configure-the-wizard-project"></a>Konfigurace projektu průvodce
 Před vytvořením průvodce musíte přidat okno Windows Presentation Foundation (WPF), soubor kódu a odkazy na sestavení do projektu.

#### <a name="to-configure-the-wizard-project"></a>Konfigurace projektu průvodce

1. V **Průzkumník řešení** otevřete místní nabídku z uzlu projektu **ItemTemplateWizard** a zvolte možnost **vlastnosti**.

2. V **Návrháři projektu** se ujistěte, že je cílová architektura nastavena na .NET Framework 4,5.

     Pro projekty Visual C# můžete tuto hodnotu nastavit na kartě **aplikace** . U Visual Basic projektů můžete tuto hodnotu nastavit na kartě **kompilovat** . Další informace najdete v tématu [Postup: cílení na verzi .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

3. V projektu **ItemTemplateWizard** přidejte položku **okna (WPF)** do projektu a poté Pojmenujte položku **WizardWindow**.

4. Přidejte dva soubory kódu s názvem CustomActionWizard a Strings.

5. Otevřete místní nabídku pro projekt **ItemTemplateWizard** a pak zvolte možnost **Přidat odkaz**.

6. V dialogovém okně **Správce odkazů – ItemTemplateWizard** pod uzlem **sestavení** vyberte uzel **rozšíření** .

7. Zaškrtněte políčka vedle následujících sestavení a poté klikněte na tlačítko **OK** :

    - EnvDTE

    - Microsoft. VisualStudio. Shell. 11.0

    - Microsoft. VisualStudio. TemplateWizardInterface

8. V **Průzkumník řešení** ve složce **odkazy** pro projekt ItemTemplateWizard vyberte odkaz **EnvDTE** .

9. V okně **vlastnosti** změňte hodnotu vlastnosti **Embed Interop Types** na **false**.

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Definujte výchozí umístění a řetězce ID pro vlastní akce.
 Každá vlastní akce má umístění a ID, které je zadáno v `GroupID` `Location` atributech a `CustomAction` elementu v souboru *Elements.xml* . V tomto kroku definujete některé platné řetězce pro tyto atributy v projektu ItemTemplateWizard. Po dokončení tohoto návodu jsou tyto řetězce zapsány do souboru *Elements.xml* v položce projektu vlastní akce, když uživatelé určí umístění a ID v průvodci.

 Pro zjednodušení Tato ukázka podporuje pouze podmnožinu dostupných výchozích umístění a ID. Úplný seznam najdete v tématu [výchozí umístění vlastních akcí a ID](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14)).

#### <a name="to-define-the-default-location-and-id-strings"></a>Definování výchozího umístění a řetězců ID

1. otevírají.

2. V projektu **ItemTemplateWizard** nahraďte kód v souboru kódu řetězce následujícím kódem.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs" id="Snippet6":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb" id="Snippet6":::

## <a name="create-the-wizard-ui"></a>Vytvoření uživatelského rozhraní Průvodce
 Přidejte XAML pro definování uživatelského rozhraní průvodce a přidejte nějaký kód pro svázání některých ovládacích prvků v průvodci s řetězci ID. Průvodce, který vytvoříte, bude vypadat jako vestavěný průvodce pro projekty služby SharePoint v aplikaci Visual Studio.

#### <a name="to-create-the-wizard-ui"></a>Vytvoření uživatelského rozhraní Průvodce

1. V projektu **ItemTemplateWizard** otevřete místní nabídku pro soubor **WizardWindow. XAML** a pak zvolte **otevřít** . otevře se okno v návrháři.

2. V zobrazení XAML nahraďte aktuální kód XAML následujícím XAML. Jazyk XAML definuje uživatelské rozhraní, které obsahuje záhlaví, ovládací prvky pro určení chování vlastní akce a navigačních tlačítek v dolní části okna.

    > [!NOTE]
    > Po přidání tohoto kódu bude mít projekt nějaké chyby kompilace. Tyto chyby zůstanou při přidávání kódu v pozdějších krocích nepřítomné.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml" id="Snippet9":::

    > [!NOTE]
    > Okno, které je vytvořeno v tomto XAML, je odvozeno od <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> základní třídy. Když přidáte vlastní dialogové okno WPF do sady Visual Studio, doporučujeme, abyste z této třídy odvodili dialogové okno, aby měly konzistentní styly s ostatními dialogovými okny v aplikaci Visual Studio a aby nedocházelo k problémům, které by jinak mohly nastat v modálních dialogových oknech. Další informace naleznete v tématu [vytváření a Správa modálních](../extensibility/creating-and-managing-modal-dialog-boxes.md)dialogových oken.

3. Pokud vyvíjíte Visual Basic projekt, odeberte `ItemTemplateWizard` obor názvů z `WizardWindow` názvu třídy v `x:Class` atributu `Window` elementu. Tento prvek je na prvním řádku XAML. Po dokončení by se měl první řádek podobat následujícímu kódu:

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. V souboru kódu na pozadí souboru WizardWindow. xaml nahraďte aktuální kód následujícím kódem.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb" id="Snippet7":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs" id="Snippet7":::

## <a name="implement-the-wizard"></a>Implementace průvodce
 Definujte funkčnost Průvodce implementací <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní.

#### <a name="to-implement-the-wizard"></a>Implementace průvodce

1. V projektu **ItemTemplateWizard** otevřete soubor kódu **CustomActionWizard** a potom nahraďte aktuální kód v tomto souboru následujícím kódem:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs" id="Snippet8":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb" id="Snippet8":::

## <a name="checkpoint"></a>CheckPoint
 V tomto okamžiku v tomto návodu je veškerý kód průvodce nyní v projektu. Sestavte projekt, abyste se ujistili, že se zkompiluje bez chyb.

#### <a name="to-build-your-project"></a>Sestavení projektu

1. Na řádku nabídek klikněte na **sestavit** sestavení  >  **řešení**.

## <a name="associate-the-wizard-with-the-item-template"></a>Přidružení průvodce k šabloně položky
 Nyní, když jste implementovali průvodce, je nutné jej přidružit k šabloně položky **vlastní akce** , a to provedením tří hlavních kroků:

1. Podepište sestavení průvodce silným názvem.

2. Získejte token veřejného klíče pro sestavení průvodce.

3. Přidejte odkaz na sestavení průvodce v souboru. vstemplate pro šablonu položky **vlastní akce** .

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Podepsání sestavení průvodce silným názvem

1. V **Průzkumník řešení** otevřete místní nabídku z uzlu projektu **ItemTemplateWizard** a zvolte možnost **vlastnosti**.

2. Na kartě **podepisování** vyberte zaškrtávací políčko **podepsat sestavení** .

3. V seznamu **Vyberte soubor klíče se silným názvem** vyberte **\<New...>** .

4. V dialogovém okně **vytvořit klíč se silným názvem** zadejte název, zrušte zaškrtnutí políčka **chránit soubor klíče heslem** a pak klikněte na tlačítko **OK** .

5. Na řádku nabídek klikněte na **sestavit** sestavení  >  **řešení**.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Získání tokenu veřejného klíče pro sestavení průvodce

1. V okně příkazového řádku sady Visual Studio spusťte následující příkaz a nahraďte *PathToWizardAssembly* úplnou cestou k sestavenému ItemTemplateWizard.dll sestavení pro projekt ItemTemplateWizard na vašem vývojovém počítači.

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     Token veřejného klíče pro sestavení *ItemTemplateWizard.dll* se zapisuje do okna příkazového řádku sady Visual Studio.

2. Nechte okno příkazového řádku sady Visual Studio otevřené. K dokončení dalšího postupu budete potřebovat token veřejného klíče.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Přidání odkazu na sestavení průvodce v souboru. vstemplate

1. V **Průzkumník řešení** rozbalte uzel projektu **ItemTemplate** a poté otevřete soubor *ItemTemplate. vstemplate* .

2. Poblíž konce souboru přidejte následující `WizardExtension` prvek mezi `</TemplateContent>` `</VSTemplate>` značky a. Nahraďte hodnotu *YourToken* `PublicKeyToken` atributu tokenem veřejného klíče, který jste získali v předchozím postupu.

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     Další informace o elementu naleznete `WizardExtension` v tématu [wizardextension – element &#40;Templates sady Visual Studio&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Uložte soubor a zavřete ho.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Přidání nahraditelných parametrů do souboru *Elements.xml* v šabloně položky
 Do souboru *Elements.xml* v projektu ItemTemplate přidejte několik nahraditelných parametrů. Tyto parametry jsou inicializovány v `PopulateReplacementDictionary` metodě ve `CustomActionWizard` třídě, kterou jste definovali dříve. Když uživatel přidá položku projektu vlastní akce do projektu, Visual Studio automaticky nahradí tyto parametry v souboru *Elements.xml* v nové položce projektu hodnotami, které jsou zadány v průvodci.

 Nahraditelný parametr je token, který začíná a končí znakem dolaru ($). Kromě definování vlastních nahraditelných parametrů můžete použít vestavěné parametry, které definuje a inicializuje systém projektu služby SharePoint. Další informace najdete v tématu [nahraditelných parametrů](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Přidání nahraditelných parametrů do souboru *Elements.xml*

1. V projektu ItemTemplate nahraďte obsah *Elements.xml* souboru následujícím kódem XML.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="$IdValue$"
                    GroupId="$GroupIdValue$"
                    Location="$LocationValue$"
                    Sequence="1000"
                    Title="$TitleValue$"
                    Description="$DescriptionValue$" >
        <UrlAction Url="$UrlValue$"/>
      </CustomAction>
    </Elements>
    ```

     Nový kód XML změní hodnoty `Id` `GroupId` atributů,, `Location` , `Description` a `Url` na nahraditelné parametry.

2. Uložte soubor a zavřete ho.

## <a name="add-the-wizard-to-the-vsix-package"></a>Přidání průvodce do balíčku VSIX
 V souboru source. extension. vsixmanifest v projektu VSIX přidejte odkaz na projekt průvodce tak, aby byl nasazen s balíčkem VSIX, který obsahuje položku projektu.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Přidání průvodce do balíčku VSIX

1. V **Průzkumník řešení** otevřete místní nabídku ze souboru **source. extension. vsixmanifest** v projektu CustomActionProjectItem a pak zvolením možnosti **otevřít** otevřete soubor v editoru manifestu.

2. V editoru manifestu klikněte na kartu **assets (prostředky** ) a pak klikněte na tlačítko **Nový** .

     Zobrazí se dialogové okno **Přidat nový prostředek** .

3. V seznamu **typ** vyberte možnost **Microsoft. VisualStudio. Assembly**.

4. V seznamu **zdroj** vyberte **projekt v aktuálním řešení**.

5. V seznamu **projekt** zvolte možnost **ItemTemplateWizard** a pak klikněte na tlačítko **OK** .

6. V panelu nabídek zvolte **sestavit**  >  **sestavení řešení** a pak se ujistěte, že se řešení zkompiluje bez chyb.

## <a name="test-the-wizard"></a>Otestování Průvodce
 Nyní jste připraveni otestovat Průvodce. Nejdřív začněte ladit řešení CustomActionProjectItem v experimentální instanci sady Visual Studio. Pak otestujte průvodce pro položku projektu vlastní akce v projektu služby SharePoint v experimentální instanci aplikace Visual Studio. Nakonec sestavte a spusťte projekt služby SharePoint, abyste ověřili, že vlastní akce funguje podle očekávání.

#### <a name="to-start-to-debug-the-solution"></a>Spuštění ladění řešení

1. Restartujte Visual Studio s přihlašovacími údaji správce a pak otevřete řešení CustomActionProjectItem.

2. V projektu ItemTemplateWizard otevřete soubor kódu CustomActionWizard a pak přidejte zarážku do prvního řádku kódu v `RunStarted` metodě.

3. Na panelu nabídek vyberte možnost **ladění**  >  **výjimek**.

4. V dialogovém okně **výjimky** ověřte, zda jsou **vyvolaná** a **uživatelem Neošetřená** zaškrtávací políčka pro **výjimky modulu CLR** vymazána a poté klikněte na tlačítko **OK** .

5. Spusťte ladění tak, že vyberete klávesu **F5** nebo v řádku nabídek zvolíte **ladění**  >  **Spustit ladění**.

     Visual Studio nainstaluje rozšíření do projektu akce%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Item\1.0 a spustí experimentální instanci sady Visual Studio. Otestujete položku projektu v této instanci aplikace Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Testování průvodce v aplikaci Visual Studio

1. V experimentální instanci aplikace Visual Studio, na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

2. Rozbalte uzel **Visual C#** nebo **Visual Basic** (v závislosti na jazyku, který vaše šablona položky podporuje), rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

3. V seznamu šablon projektu zvolte **projekt SharePoint 2010**, pojmenujte projekt **CustomActionWizardTest** a pak klikněte na tlačítko **OK** .

4. V **Průvodci vlastním nastavením služby SharePoint** zadejte adresu URL webu, který chcete použít pro ladění, a poté klikněte na tlačítko **Dokončit** .

5. V **Průzkumník řešení** otevřete místní nabídku uzlu projektu, zvolte možnost **Přidat** a poté **položku Nová položka**.

6. V dialogovém okně **Přidat novou položku – CustomItemWizardTest** rozbalte uzel **SharePoint** a potom rozbalte uzel **2010** .

7. V seznamu položek projektu zvolte položku **vlastní akce** a poté klikněte na tlačítko **Přidat** .

8. Ověřte, zda se kód v jiné instanci sady Visual Studio zastaví na zarážce, kterou jste nastavili dříve v `RunStarted` metodě.

9. Pokračujte v ladění projektu volbou klávesy **F5** nebo v řádku nabídek zvolte možnost **ladění**  >  **pokračovat**.

     Zobrazí se Průvodce přizpůsobením SharePointu.

10. V části **umístění** klikněte na tlačítko pro **úpravy seznamu** .

11. V seznamu **ID skupiny** vyberte možnost **komunikace**.

12. Do pole **název** zadejte **SharePoint Developer Center**.

13. V poli  **Popis** **otevřete otevřít web centra pro vývojáře služby SharePoint**.

14. Do pole **Adresa URL** zadejte **https://docs.microsoft.com/sharepoint/dev/** a pak klikněte na tlačítko **Dokončit** .

     Visual Studio přidá do projektu položku s názvem **CustomAction1** a otevře soubor *Elements.xml* v editoru. Ověřte, zda *Elements.xml* obsahuje hodnoty, které jste zadali v průvodci.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Testování vlastní akce v SharePointu

1. V experimentální instanci aplikace Visual Studio klikněte na klávesu **F5** nebo na panelu nabídek vyberte **ladění**  >  **Spustit ladění**.

     Vlastní akce je zabalená a nasazená na SharePointový web určený vlastností **Adresa URL webu** projektu a webový prohlížeč se otevře na výchozí stránce této lokality.

    > [!NOTE]
    > Pokud se zobrazí dialogové okno **ladění skriptu zakázané** , klikněte na tlačítko **Ano** .

2. V oblasti seznamy na webu služby SharePoint vyberte odkaz **úkoly** .

     Zobrazí se stránka **úkoly – všechny úlohy** .

3. Na kartě **Nástroje seznamu** na pásu karet klikněte na kartu **seznam** a pak ve skupině **Nastavení** zvolte **Nastavení seznamu**.

     Zobrazí se stránka **Nastavení seznamu** .

4. V části **komunikace** v horní části stránky vyberte odkaz **Centrum pro vývojáře služby SharePoint** , ověřte, že prohlížeč web otevře https://docs.microsoft.com/sharepoint/dev/ , a pak zavřete prohlížeč.

## <a name="cleaning-up-the-development-computer"></a>Vyčištění vývojového počítače
 Po dokončení testování položky projektu odeberte šablonu položky projektu z experimentální instance aplikace Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Vyčištění vývojového počítače

1. V experimentální instanci aplikace Visual Studio, na panelu nabídek vyberte **nástroje**  >  **rozšíření a aktualizace**.

     Otevře se dialogové okno **rozšíření a aktualizace** .

2. V seznamu rozšíření zvolte rozšíření **položky projektu vlastní akce** a poté klikněte na tlačítko **odinstalovat** .

3. V dialogovém okně, které se zobrazí, kliknutím na tlačítko **Ano** potvrďte, že chcete rozšíření odinstalovat, a kliknutím na tlačítko **restartovat nyní** dokončete odinstalaci.

4. Zavřete obě instance sady Visual Studio (experimentální instance a instance sady Visual Studio, ve které je řešení CustomActionProjectItem otevřené).

## <a name="see-also"></a>Viz také
- [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Vytváření šablon položek a šablon projektů pro položky projektu služby SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Postupy: Použití průvodců se šablonami projektů](../extensibility/how-to-use-wizards-with-project-templates.md)
- [Výchozí umístění a ID vlastních akcí](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14))
