---
title: 'Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 2 | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2c37ab6f42be8e363dcba8a3e2aa6ef78816bff0
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296239"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 2
  Po definování vlastního typu položky projektu služby SharePoint a přidružte jej k šabloně položky v sadě Visual Studio, můžete také poskytnout průvodce pro šablony. Průvodce můžete použít ke shromažďování informací od uživatelů při použití šablony přidáte novou instanci položky projektu do projektu. Informace, které slouží k inicializaci položky projektu.  
  
 V tomto názorném postupu přidáte průvodce do položky projektu vlastní akce, která je znázorněna v [návod: vytvoření vlastní akce položky projektu pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Když uživatel přidá vlastní akce položky projektu do projektu služby SharePoint, Průvodce shromažďuje informace o vlastní akci (třeba jeho umístění a adresa URL má přejít, když koncový uživatel vybere) a přidá tyto informace *Elements.xml* soubor v nové položce projektu.  
  
 Tento návod demonstruje následující úkoly:  
  
-   Vytvoření průvodce pro vlastní typ položky projektu služby SharePoint, který je přidružen k šabloně položky.  
  
-   Definování vlastního průvodce, uživatelské rozhraní, které se podobá vestavěné průvodce pro položky projektu služby SharePoint v sadě Visual Studio.  
  
-   Použití nahraditelných parametrů pro inicializaci soubory Sharepointového projektu s daty, která budete shromažďovat průvodce.  
  
-   Ladění a testování v průvodci.  
  
> [!NOTE]  
>  Můžete si stáhnout ukázky z [Githubu](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) , který ukazuje, jak vytvořit vlastní aktivity pracovního postupu.  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li provést Tento názorný postup, musíte nejdřív vytvořit CustomActionProjectItem řešení provedením [návod: vytvoření vlastní akce položky projektu pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 Budete potřebovat následující komponenty na vývojovém počítači k dokončení tohoto návodu:  
  
- Podporované edice systému Windows, SharePoint a Visual Studio.
  
- Visual Studio SDK. Tento návod používá **projekt VSIX** šablony v sadě SDK k vytvoření balíčku VSIX k nasazení položky projektu. Další informace najdete v tématu [rozšíření nástrojů SharePoint v sadě Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Znalost následujících konceptů je užitečná, ale není požadována k dokončení návodu:  
  
- Průvodce pro šablony projektů a položek v sadě Visual Studio. Další informace najdete v tématu [postupy: použití průvodců se šablonami projektů](../extensibility/how-to-use-wizards-with-project-templates.md) a <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní.  
  
- Vlastní akce v Sharepointu. Další informace najdete v tématu [vlastní akce](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
## <a name="create-the-wizard-project"></a>Vytvoření projektu průvodce
 K dokončení tohoto návodu, musíte přidat projekt do řešení CustomActionProjectItem, které jste vytvořili v [návod: vytvoření vlastní akce položky projektu pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Budete implementovat <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní a definovat Průvodce uživatelského rozhraní v tomto projektu.  
  
#### <a name="to-create-the-wizard-project"></a>Vytvoření projektu průvodce  
  
1.  V sadě Visual Studio otevřete řešení CustomActionProjectItem  
  
2.  V **Průzkumníka řešení**, otevřete místní nabídku pro uzel řešení, zvolte **přidat**a klikněte na tlačítko **nový projekt**.  
  
3.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** uzly a klikněte na tlačítko **Windows** uzlu.  
  
4.  V horní části **nový projekt** dialogové okno pole, ujistěte se, že **rozhraní .NET Framework 4.5** je vybrán v seznamu verzí rozhraní .NET Framework.  
  
5.  Zvolte **Knihovna uživatelských ovládacích prvků WPF** šablony projektu, pojmenujte projekt **ItemTemplateWizard**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **ItemTemplateWizard** projektu do řešení.  
  
6.  Odstraňte UserControl1 položku z projektu.  
  
## <a name="configure-the-wizard-project"></a>Konfigurace Průvodce projektu
 Před vytvořením průvodce, musíte přidat okno Windows Presentation Foundation (WPF), souboru kódu a odkazy na sestavení do projektu.  
  
#### <a name="to-configure-the-wizard-project"></a>Ke konfiguraci projektu průvodce  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku z **ItemTemplateWizard** uzel projektu a klikněte na tlačítko **vlastnosti**.  
  
2.  V **Návrháře projektu**, ujistěte se, že Cílová architektura, která je nastavena na rozhraní .NET Framework 4.5.  
  
     Pro projekty Visual C#, můžete tuto hodnotu nastavit na **aplikace** kartu. Pro projekty jazyka Visual Basic, můžete tuto hodnotu nastavit na **kompilaci** kartu. Další informace najdete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
3.  V **ItemTemplateWizard** projektu, přidejte **okno (WPF)** položky do projektu a potom zadejte název položky **WizardWindow**.  
  
4.  Přidejte dva soubory kódu, které jsou pojmenovány CustomActionWizard a řetězce.  
  
5.  Otevřete místní nabídku **ItemTemplateWizard** projektu a klikněte na tlačítko **přidat odkaz**.  
  
6.  V **správce odkazů - ItemTemplateWizard** dialogovém okně **sestavení** uzlu, vyberte **rozšíření** uzlu.  
  
7.  Zaškrtněte políčka u následujících sestavení a klikněte na tlačítko **OK** tlačítka:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  V **Průzkumníka řešení**v **odkazy** ItemTemplateWizard projektu, zvolte **EnvDTE** odkaz.  
  
9. V **vlastnosti** okna, změňte hodnotu **Embed Interop Types** vlastnost **False**.  
  
## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Definovat výchozí umístění a ID řetězce pro vlastní akce
 Každá vlastní akce má umístění a ID, které je zadáno v `GroupID` a `Location` atributy `CustomAction` prvek *Elements.xml* souboru. V tomto kroku definujete některé platné řetězce pro tyto atributy v projektu ItemTemplateWizard. Po dokončení tohoto návodu, tyto řetězce jsou zapsány do *Elements.xml* soubor v položce projektu vlastní akce, když uživatelé zadat umístění a ID v průvodci.  
  
 Pro zjednodušení tento příklad podporuje pouze podmnožinu identifikátory a dostupná výchozí umístění. Úplný seznam najdete v tématu [výchozí umístění vlastní akce a ID](http://go.microsoft.com/fwlink/?LinkId=181964).  
  
#### <a name="to-define-the-default-location-and-id-strings"></a>Chcete-li definovat výchozí umístění a ID řetězce
  
1.  Otevřít.  
  
2.  V **ItemTemplateWizard** projektu, nahraďte kód v souboru kódu řetězce s následujícím kódem.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]  
  
## <a name="create-the-wizard-ui"></a>Vytvořit průvodce uživatelského rozhraní
 Přidejte XAML k definování uživatelského rozhraní průvodce a přidejte nějaký kód pro vazbu některé ovládací prvky v průvodci na ID řetězce. Průvodce, který vytvoříte se podobá integrovaného průvodce pro projekty služby SharePoint v sadě Visual Studio.  
  
#### <a name="to-create-the-wizard-ui"></a>Chcete-li vytvořit průvodce uživatelského rozhraní
  
1.  V **ItemTemplateWizard** projektu, otevřete místní nabídku **WizardWindow.xaml** souboru a klikněte na tlačítko **otevřete** otevření okna v návrháři.  
  
2.  V XAML zobrazení nahraďte aktuální XAML následující XAML. XAML definuje uživatelské rozhraní, které obsahuje nadpis, ovládací prvky pro určení chování vlastní akce a navigačních tlačítek v dolní části okna.  
  
    > [!NOTE]  
    >  Po přidání tohoto kódu, bude mít projekt několik chyb kompilace. K těmto chybám předejdete přidáním kódu v dalších krocích.  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  V okně, které se vytvoří v tomto XAML je odvozen z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> základní třídy. Když přidáte vlastní dialogové okno WPF se sadou Visual Studio, doporučujeme odvodit vaše dialogové okno z této třídy, aby stylů konzistentní vzhledem k aplikacím s další dialogová okna v sadě Visual Studio a aby se zabránilo problémům, které by jinak mohlo dojít s modálních dialogových oken. Další informace najdete v tématu [vytváření a správa modálních dialogových oken](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Pokud vyvíjíte projekt jazyka Visual Basic, odeberte `ItemTemplateWizard` obor názvů z `WizardWindow` název třídy v `x:Class` atribut `Window` elementu. Tento element má na prvním řádku XAML. Až budete hotovi, první řádek by měl vypadat následovně:  
  
    ```xml  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  V souboru kódu na pozadí pro soubor WizardWindow.xaml nahraďte aktuální kód následujícím kódem.  
  
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]  
  
## <a name="implement-the-wizard"></a>Implementace průvodce
 Definovat funkci Průvodce implementací <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní.  
  
#### <a name="to-implement-the-wizard"></a>K implementaci Průvodce  
  
1.  V **ItemTemplateWizard** projekt, otevřete **CustomActionWizard** soubor kódu a aktuální kód v tomto souboru nahraďte následujícím kódem:  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku návodu je celý kód pro průvodce v projektu. Sestavte projekt, abyste měli jistotu, že se zkompiluje bez chyb.  
  
#### <a name="to-build-your-project"></a>K sestavení projektu  
  
1.  V panelu nabídky zvolte **sestavení** > **sestavit řešení**.  
  
## <a name="associate-the-wizard-with-the-item-template"></a>Průvodce přidružit k šabloně položky
 Teď, když naimplementujete průvodci, musíte ho přidružit **vlastní akce** šablony položky provedením tři hlavní kroky:  
  
1.  Podepsání sestavení silným názvem průvodce.  
  
2.  Získání tokenu veřejného klíče pro sestavení průvodce.  
  
3.  V souboru .vstemplate přidejte odkaz na sestavení průvodce **vlastní akce** šablony položky.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>K podepsání sestavení silným názvem Průvodce  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku z **ItemTemplateWizard** uzel projektu a klikněte na tlačítko **vlastnosti**.  
  
2.  Na **podepisování** kartu, vyberte **podepsat sestavení** zaškrtávací políčko.  
  
3.  V **vyberte soubor klíče se silným názvem** klikněte na položku  **\<nový … >**.  
  
4.  V **vytvořit klíč se silným názvem** dialogového okna zadejte název, zrušte **chránit můj soubor klíče s heslem** zaškrtněte políčko a klikněte na tlačítko **OK** tlačítko.  
  
5.  V panelu nabídky zvolte **sestavení** > **sestavit řešení**.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>K získání tokenu veřejného klíče pro sestavení průvodce  
  
1.  V okně Příkazový řádek sady Visual Studio, spusťte následující příkaz a nahraďte *PathToWizardAssembly* s úplnou cestou k ItemTemplateWizard.dll sestavení pro projekt ItemTemplateWizard na vývoj počítač.  
  
    ```xml  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Token veřejného klíče pro *ItemTemplateWizard.dll* sestavení je zapsán do okna příkazového řádku aplikace Visual Studio.  
  
2.  Nechte okno Příkazový řádek sady Visual Studio otevřené. Budete potřebovat další postup token veřejného klíče.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Chcete-li přidat odkaz na sestavení průvodce v souboru .vstemplate  
  
1.  V **Průzkumníka řešení**, rozbalte **ItemTemplate** uzel projektu a pak otevřete *ItemTemplate.vstemplate* souboru.  
  
2.  Na konci souboru, přidejte následující `WizardExtension` prvek mezi `</TemplateContent>` a `</VSTemplate>` značky. Nahradit *YourToken* hodnotu `PublicKeyToken` atribut s veřejným klíčem, který jste získali v předchozím postupu.  
  
    ```xml  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Další informace o `WizardExtension` prvku, naleznete v tématu [WizardExtension – Element &#40;šablony sady Visual Studio&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Soubor uložte a zavřete.  
  
## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Nahraditelné parametry pro přidání *Elements.xml* soubor v šabloně položky
 Přidat několik nahraditelné parametry *Elements.xml* soubor v projektu ItemTemplate. Tyto parametry jsou inicializovány v `PopulateReplacementDictionary` metodu `CustomActionWizard` třídu, která jste definovali dříve. Když uživatel přidá vlastní akce položky projektu do projektu, Visual Studio automaticky nahradí tyto parametry v *Elements.xml* soubor novou položku projektu s hodnotami, které jsou zadány v průvodci.  
  
 Nahraditelných parametrů je token, který začíná a končí znakem dolaru ($). Kromě definování nahraditelné parametry, můžete použít předdefinované parametry, které definuje systému Sharepointových projektů a inicializuje. Další informace najdete v tématu [nahraditelné parametry](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Nahraditelné parametry pro přidání *Elements.xml* souboru
  
1.  V projektu ItemTemplate, nahraďte obsah *Elements.xml* soubor s následující kód XML.  
  
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
  
     Nové XML změní hodnoty `Id`, `GroupId`, `Location`, `Description`, a `Url` atributy pro nahraditelné parametry.  
  
2.  Soubor uložte a zavřete.  
  
## <a name="add-the-wizard-to-the-vsix-package"></a>Přidat průvodce k balíčku VSIX
 V souboru source.extension.vsixmanifest v projektu VSIX přidejte odkaz na projekt průvodce tak, aby byl nasazen spolu s balíčkem VSIX, který obsahuje položky projektu.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Chcete-li přidat průvodce k balíčku VSIX  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku z **source.extension.vsixmanifest** souboru v projektu CustomActionProjectItem a klikněte na tlačítko **otevřete** otevřít soubor v editoru manifestu.  
  
2.  V editoru manifestu vyberte **prostředky** kartu a pak zvolte **nový** tlačítko.  
  
     **Přidat nové aktivum** zobrazí se dialogové okno.  
  
3.  V **typ** klikněte na položku **Microsoft.VisualStudio.Assembly**.  
  
4.  V **zdroj** klikněte na položku **projekt v aktuálním řešení**.  
  
5.  V **projektu** klikněte na položku **ItemTemplateWizard**a klikněte na tlačítko **OK** tlačítko.  
  
6.  V panelu nabídky zvolte **sestavení** > **sestavit řešení**a ujistěte se, že řešení zkompiluje bez chyb.  
  
## <a name="test-the-wizard"></a>Průvodce testu
 Nyní jste připraveni k testování průvodce. Nejprve spusťte ladění řešení CustomActionProjectItem v experimentální instanci sady Visual Studio. Otestujte průvodce pro vlastní akce položky projektu v projektu služby SharePoint v experimentální instanci sady Visual Studio. Nakonec sestavte a spusťte projekt SharePoint, chcete-li ověřit, že vlastní akce funguje podle očekávání.  
  
#### <a name="to-start-to-debug-the-solution"></a>Pro spuštění ladění řešení  
  
1.  Restartujte sadu Visual Studio s přihlašovacími údaji správce a pak otevřete CustomActionProjectItem řešení.  
  
2.  V projektu ItemTemplateWizard, otevřete soubor kódu CustomActionWizard a na první řádek kódu přidejte zarážku `RunStarted` metody.  
  
3.  V panelu nabídky zvolte **ladění** > **výjimky**.  
  
4.  V **výjimky** dialogové okno pole, ujistěte se, že **vyvolání** a **uživatelem neošetřené** zaškrtnutí políček u **výjimky modulu Common Language Runtime**jsou vymazány a klikněte na tlačítko **OK** tlačítko.  
  
5.  Spuštění ladění zvolením **F5** klíče, nebo v řádku nabídek, výběrem **ladění** > **spustit ladění**.  
  
     Visual Studio nainstaluje rozšíření do %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom akce Project Item\1. 0 a spustí experimentální instanci sady Visual Studio. Položku projektu budete testovat v této instanci aplikace Visual Studio.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>K otestování průvodce v sadě Visual Studio  
  
1.  V experimentální instanci sady Visual Studio na panelu nabídek zvolte **souboru** > **nový** > **projektu**.  
  
2.  Rozbalte **Visual C#** nebo **jazyka Visual Basic** uzel (v závislosti na jazyk, který podporuje vaši šablonu položky), Rozbalit **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.  
  
3.  V seznamu šablon projektu vyberte **projektu služby SharePoint 2010**, pojmenujte projekt **CustomActionWizardTest**a klikněte na tlačítko **OK** tlačítko.  
  
4.  V **Průvodce přizpůsobením SharePoint**, zadejte adresu URL webu, který chcete použít pro ladění a klikněte na tlačítko **Dokončit** tlačítko.  
  
5.  V **Průzkumníka řešení**, otevřete místní nabídku pro uzel projektu, zvolte **přidat**a klikněte na tlačítko **nová položka**.  
  
6.  V **přidat novou položku - CustomItemWizardTest** dialogového okna rozbalte **SharePoint** uzel a potom rozbalte **2010** uzlu.  
  
7.  V seznamu položek projektu, zvolte **vlastní akce** položku a klikněte na tlačítko **přidat** tlačítko.  
  
8.  Ověřte, že kód ve druhé instanci aplikace Visual Studio zastaví na zarážce, kterou jste nastavili dříve v `RunStarted` metody.  
  
9. Pokračovat v ladění projektu výběrem **F5** klíče nebo na panelu nabídek, výběrem **ladění** > **pokračovat**.  
  
     Zobrazí se Průvodce přizpůsobením SharePoint.  
  
10. V části **umístění**, zvolte **úprava seznamu** přepínač.  
  
11. V **ID skupiny** klikněte na položku **komunikace**.  
  
12. V **Title** zadejte **SharePoint Developer Center**.  
  
13. V **popis** zadejte **otevře web SharePoint Developer Center**.  
  
14. V **URL** zadejte **https://docs.microsoft.com/sharepoint/dev/** a klikněte na tlačítko **Dokončit** tlačítko.  
  
     Visual Studio přidá položku s názvem **CustomAction1** projekt a otevře *Elements.xml* souboru v editoru. Ověřte, že *Elements.xml* obsahuje hodnoty, které jste zadali v průvodci.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>Testování vlastní akce v Sharepointu  
  
1.  V experimentální instanci sady Visual Studio, zvolte **F5** klíče, nebo na panelu nabídek zvolte **ladění** > **spustit ladění**.  
  
     Vlastní akce je zabalit a nasadit na web služby SharePoint, které jsou určené **adresa URL webu** vlastnosti projektu a webový prohlížeč otevře výchozí stránku webu.  
  
    > [!NOTE]  
    >  Pokud **ladění skriptů zakázáno** dialogové okno se zobrazí, zvolte **Ano** tlačítko.  
  
2.  V oblasti seznamy z webu služby SharePoint, zvolte **úlohy** odkaz.  
  
     **Úkoly – všechny úkoly** se zobrazí stránka.  
  
3.  Na **nástroje seznamu** kartu na pásu karet, zvolte **seznamu** kartu a pak na **nastavení** skupině, zvolte **nastavení seznamu**.  
  
     **Nastavení seznamu** se zobrazí stránka.  
  
4.  V části **komunikace** záhlaví v horní části stránky, zvolte **středisko pro vývojáře služby SharePoint** propojení, ověřte, že v prohlížeči se otevře web https://docs.microsoft.com/sharepoint/dev/a pak ukončete prohlížeč.  
  
## <a name="cleaning-up-the-development-computer"></a>Čištění vývojového počítače
 Po dokončení testování položku projektu, odeberte šablony položky projektu z experimentální instanci sady Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Chcete-li vyčistit vývojovém počítači  
  
1.  V experimentální instanci sady Visual Studio na panelu nabídek zvolte **nástroje** > **rozšíření a aktualizace**.  
  
     **Rozšíření a aktualizace** zobrazí se dialogové okno.  
  
2.  V seznamu rozšíření zvolte **vlastní položky projektu akce** rozšíření a klikněte na tlačítko **odinstalovat** tlačítko.  
  
3.  V dialogovém okně, které se zobrazí, zvolte **Ano** potvrďte, že chcete odinstalovat rozšíření a klikněte na tlačítko **restartovat nyní** tlačítko pro dokončení odinstalace.  
  
4.  Zavřete obě instance programu Visual Studio (experimentální instanci a instanci sady Visual Studio, ve kterém je otevřen CustomActionProjectItem řešení).  
  
## <a name="see-also"></a>Viz také:
 [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Vytváření šablon položek a projektů pro položky projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Odkaz na schéma šablon sady Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Postupy: použití průvodců se šablonami projektů](../extensibility/how-to-use-wizards-with-project-templates.md)   
 [Výchozí umístění vlastní akce a ID](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
