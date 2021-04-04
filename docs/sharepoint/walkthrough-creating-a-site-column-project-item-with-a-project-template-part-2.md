---
title: Vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2
titleSuffix: ''
description: Přidejte průvodce do šablony projektu sloupce webu pro shromáždění dat od uživatelů při použití šablony k vytvoření projektu služby SharePoint obsahujícího položku projektu.
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
ms.openlocfilehash: 13a2f2c147bbf175a7601cd465dc8acbba9b5388
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217746"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2
  Po definování vlastního typu položky projektu služby SharePoint a jejich přidružení k šabloně projektu v aplikaci Visual Studio můžete také pro šablonu poskytnout průvodce. Průvodce můžete použít ke shromáždění informací z uživatelů při použití šablony k vytvoření nového projektu, který obsahuje položku projektu. Informace, které shromáždíte, lze použít k inicializaci položky projektu.

 V tomto návodu přidáte průvodce do šablony projektu sloupce webu, která je znázorněna v [návodu Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md). Když uživatel vytvoří projekt sloupce webu, průvodce shromáždí informace o sloupci webu (jako je jeho základní typ a skupina) a přidá tyto informace do souboru *Elements.xml* v novém projektu.

 Tento názorný postup ukazuje následující úlohy:

- Vytvoření průvodce pro vlastní typ položky projektu služby SharePoint, který je spojen se šablonou projektu.

- Definování vlastního uživatelského rozhraní průvodce, které se podobá vestavěným průvodcům pro projekty služby SharePoint v aplikaci Visual Studio.

- Vytváření dvou *příkazů SharePointu* , které se používají pro volání na místní web služby SharePoint v době, kdy je spuštěn průvodce. Příkazy služby SharePoint jsou metody, které mohou používat rozšíření aplikace Visual Studio pro volání rozhraní API v objektovém modelu serveru SharePoint. Další informace naleznete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Použití nahraditelných parametrů k inicializaci souborů projektu služby SharePoint s daty, která shromažďujete v průvodci.

- Vytvoření nového souboru. snk v každé nové instanci projektu sloupce webu. Tento soubor se používá k podepsání výstupu projektu, aby bylo možné nasadit sestavení řešení služby SharePoint do globální mezipaměti sestavení (GAC).

- Ladění a testování průvodce.

> [!NOTE]
> Řadu ukázkových pracovních postupů najdete v tématu [ukázky pracovních postupů služby SharePoint](/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Požadavky
 Chcete-li provést tento návod, je nutné nejprve vytvořit řešení SiteColumnProjectItem, a to dokončením [návodu: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 K dokončení tohoto Názorného postupu potřebujete také následující komponenty na vývojovém počítači:

- Podporované edice Windows, SharePointu a sady Visual Studio.

- Sada Visual Studio SDK. Tento návod používá šablonu **projektu VSIX** v sadě SDK k vytvoření balíčku VSIX pro nasazení položky projektu. Další informace najdete v tématu věnovaném [rozšiřování nástrojů služby SharePoint v aplikaci Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znalosti následujících konceptů jsou užitečné, ale nevyžadují se k dokončení tohoto postupu:

- Průvodci pro šablony projektů a položek v aplikaci Visual Studio. Další informace najdete v tématu [Postupy: použití průvodců se šablonami projektů](../extensibility/how-to-use-wizards-with-project-templates.md) a <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraním.

- Sloupce webu ve službě SharePoint. Další informace najdete v tématu [sloupce](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

## <a name="understand-the-wizard-components"></a>Pochopení součástí Průvodce
 Průvodce, který je znázorněn v tomto návodu, obsahuje několik komponent. Tyto součásti jsou popsány v následující tabulce.

|Komponenta|Popis|
|---------------|-----------------|
|Implementace průvodce|Toto je třída s názvem `SiteColumnProjectWizard` , která implementuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní. Toto rozhraní definuje metody, které Visual Studio volá při spuštění a dokončení průvodce, a v některých případech i při spuštění průvodce.|
|Uživatelské rozhraní Průvodce|Toto je okno založené na WPF s názvem `WizardWindow` . Toto okno obsahuje dva uživatelské ovládací prvky s názvem `Page1` a `Page2` . Tyto uživatelské ovládací prvky reprezentují dvě stránky průvodce.<br /><br /> V tomto návodu <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> Metoda implementace průvodce zobrazí uživatelské rozhraní průvodce.|
|Model dat Průvodce|Jedná se o zprostředkující třídu s názvem `SiteColumnWizardModel` , která poskytuje vrstvu mezi uživatelským rozhraním průvodce a implementací průvodce. Tato ukázka používá tuto třídu k tomu, aby usnadnila abstrakci implementace průvodce a uživatelské rozhraní průvodce. Tato třída není požadovaná součást všech průvodců.<br /><br /> V tomto návodu implementace průvodce předá `SiteColumnWizardModel` objekt do okna Průvodce při zobrazení uživatelského rozhraní průvodce. Uživatelské rozhraní Průvodce používá metody tohoto objektu k uložení hodnot ovládacích prvků v uživatelském rozhraní a k provádění úkolů, jako je ověření, že adresa URL vstupního webu je platná. Jakmile uživatel dokončí průvodce, implementace průvodce pomocí `SiteColumnWizardModel` objektu určí konečný stav uživatelského rozhraní.|
|Správce podepisování projektu|Toto je pomocná třída s názvem `ProjectSigningManager` , která je použita implementací průvodce pro vytvoření nového souboru key. snk v každé nové instanci projektu.|
|SharePoint – příkazy|Jedná se o metody, které jsou používány modelem dat Průvodce pro volání do místního webu služby SharePoint, když je spuštěn průvodce. Vzhledem k tomu, že příkazy služby SharePoint musí cílit na .NET Framework 3,5, jsou tyto příkazy implementovány v jiném sestavení než zbývající část kódu průvodce.|

## <a name="create-the-projects"></a>Vytváření projektů
 Chcete-li dokončit tento návod, je nutné přidat několik projektů do řešení SiteColumnProjectItem, které jste vytvořili v [návodu: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):

- Projekt WPF. Implementujete <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní a definujete uživatelské rozhraní průvodce v tomto projektu.

- Projekt knihovny tříd, který definuje příkazy služby SharePoint. Tento projekt musí být cílen na the.NET Framework 3,5.

  Spusťte návod vytvořením projektů.

#### <a name="to-create-the-wpf-project"></a>Vytvoření projektu WPF

1. V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otevřete řešení SiteColumnProjectItem.

2. V **Průzkumník řešení** otevřete místní nabídku uzlu řešení **SiteColumnProjectItem** , zvolte možnost **Přidat** a pak zvolte možnost **Nový projekt**.

3. V horní části dialogového okna **Přidat nový projekt** se ujistěte, že je v seznamu verzí .NET Framework zvolena možnost **.NET Framework 4,5** .

4. Rozbalte uzel **Visual C#** nebo uzel **Visual Basic** a vyberte uzel **Windows** .

5. V seznamu šablon projektu zvolte možnost **Knihovna uživatelských ovládacích prvků WPF**, pojmenujte projekt **ProjectTemplateWizard** a poté klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **ProjectTemplateWizard** do řešení a otevře výchozí soubor UserControl1. XAML.

6. Odstraňte soubor UserControl1. XAML z projektu.

#### <a name="to-create-the-sharepoint-commands-project"></a>Vytvoření projektu příkazů SharePointu

1. V **Průzkumník řešení** otevřete místní nabídku uzlu řešení SiteColumnProjectItem, zvolte možnost **Přidat** a pak zvolte možnost **Nový projekt**.

2. V horní části dialogového okna **Přidat nový projekt** vyberte v seznamu verzí .NET Framework **.NET Framework 3,5** .

3. Rozbalte uzel **Visual C#** nebo uzel  **Visual Basic** a pak vyberte uzel **Windows** .

4. Zvolte šablonu projektu **Knihovna tříd** , pojmenujte projekt **SharePointCommands** a pak klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **SharePointCommands** do řešení a otevře soubor Default Class1 Code.

5. Odstraňte soubor kódu Class1 z projektu.

## <a name="configure-the-projects"></a>Konfigurace projektů
 Před vytvořením průvodce musíte do projektů přidat některé soubory kódu a odkazy na sestavení.

#### <a name="to-configure-the-wizard-project"></a>Konfigurace projektu průvodce

1. V **Průzkumník řešení** otevřete místní nabídku uzlu projektu **ProjectTemplateWizard** a poté zvolte možnost **vlastnosti**.

2. V **Návrháři projektu** vyberte kartu **aplikace** pro projekt jazyka Visual C# nebo kartu **kompilovat** pro Visual Basic projekt.

3. Ujistěte se, že je cílová architektura nastavena na .NET Framework 4,5, nikoli na profil klienta .NET Framework 4,5.

     Další informace najdete v tématu [Postup: cílení na verzi .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

4. Otevřete místní nabídku projektu **ProjectTemplateWizard** , zvolte možnost **Přidat** a pak zvolte možnost **Nová položka**.

5. Zvolte položku **okna (WPF)** , pojmenujte položku **WizardWindow** a pak klikněte na tlačítko **Přidat** .

6. Přidejte do projektu položky dvou **uživatelských ovládacích prvků (WPF)** a pojmenujte je **Page1** a **Page2**.

7. Přidejte do projektu čtyři soubory kódu a poskytněte jim následující názvy:

    - SiteColumnProjectWizard

    - SiteColumnWizardModel

    - ProjectSigningManager

    - CommandIds

8. Otevřete místní nabídku uzlu projektu **ProjectTemplateWizard** a poté zvolte možnost **Přidat odkaz**.

9. Rozbalte uzel **sestavení** , zvolte uzel **rozšíření** a potom zaškrtněte políčka vedle následujících sestavení:

    - EnvDTE

    - Microsoft. VisualStudio. OLE. Interop

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. Shell. 11.0

    - Microsoft. VisualStudio. Shell. Interop. 10.0

    - Microsoft. VisualStudio. Shell. Interop. 11.0

    - Microsoft. VisualStudio. TemplateWizardInterface

10. Chcete-li přidat sestavení do projektu, klikněte na tlačítko **OK** .

11. V **Průzkumník řešení** ve složce **odkazy** pro projekt **ProjectTemplateWizard** vyberte možnost **EnvDTE**.

12. V okně **vlastnosti** změňte hodnotu vlastnosti **Embed Interop Types** na **false**.

13. Pokud vyvíjíte Visual Basic projekt, importujte obor názvů ProjectTemplateWizard do projektu pomocí **Návrháře projektu**.

     Další informace najdete v tématu [Postup: Přidání nebo odebrání importovaných oborů názvů &#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).

#### <a name="to-configure-the-sharepointcommands-project"></a>Konfigurace projektu SharePointcommands

1. V **Průzkumník řešení** vyberte uzel projektu **SharePointCommands** .

2. V panelu nabídek klikněte na položku **projekt**,  **Přidat existující položku**.

3. V dialogovém okně **Přidat existující položku** přejděte do složky, která obsahuje soubory kódu projektu ProjectTemplateWizard, a pak zvolte soubor s kódem **CommandIds** .

4. Klikněte na šipku vedle tlačítka **Přidat** a potom v zobrazené nabídce zvolte možnost **Přidat jako odkaz** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá soubor s kódem do projektu **SharePointCommands** jako odkaz. Soubor kódu je umístěn v projektu **ProjectTemplateWizard** , ale kód v souboru je také zkompilován v projektu **SharePointCommands** .

5. V projektu **SharePointCommands** přidejte další soubor kódu s názvem Commands.

6. Zvolte projekt SharePointCommands a pak na panelu nabídek zvolte **projekt**  >  **Přidat odkaz**.

7. Rozbalte uzel **sestavení** , zvolte uzel **rozšíření** a potom zaškrtněte políčka vedle následujících sestavení:

    - Microsoft. SharePoint

    - Microsoft. VisualStudio. SharePoint. Commands

8. Chcete-li přidat sestavení do projektu, klikněte na tlačítko **OK** .

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Vytvoření modelu průvodce, správce podepisování a ID příkazů služby SharePoint
 Přidejte do projektu ProjectTemplateWizard kód, který implementuje následující komponenty v ukázce:

- ID příkazů SharePointu Tyto řetězce identifikují příkazy služby SharePoint, které používá Průvodce. Později v tomto návodu přidáte do projektu SharePointCommands kód, který implementuje příkazy.

- Model dat průvodce.

- Správce podepisování projektu.

  Další informace o těchto součástech naleznete v tématu [pochopení součástí Průvodce](#understand-the-wizard-components).

#### <a name="to-define-the-sharepoint-command-ids"></a>Definování ID příkazů SharePointu

1. V projektu ProjectTemplateWizard otevřete soubor kódu CommandIds a pak celý obsah tohoto souboru nahraďte následujícím kódem.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs" id="Snippet5":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb" id="Snippet5":::

#### <a name="to-create-the-wizard-model"></a>Vytvoření modelu Průvodce

1. Otevřete soubor kódu SiteColumnWizardModel a celý obsah tohoto souboru nahraďte následujícím kódem.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb" id="Snippet6":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs" id="Snippet6":::

#### <a name="to-create-the-project-signing-manager"></a>Vytvoření správce podepisování projektu

1. Otevřete soubor kódu ProjectSigningManager a pak celý obsah tohoto souboru nahraďte následujícím kódem.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb" id="Snippet8":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs" id="Snippet8":::

## <a name="create-the-wizard-ui"></a>Vytvoření uživatelského rozhraní Průvodce
 Přidejte XAML pro definování uživatelského rozhraní okna průvodce a dvou uživatelských ovládacích prvků, které poskytují uživatelské rozhraní pro stránky průvodce, a přidejte kód pro definování chování okna a uživatelských ovládacích prvků. Průvodce, který vytvoříte, bude vypadat jako vestavěný průvodce pro projekty služby SharePoint v aplikaci Visual Studio.

> [!NOTE]
> V následujících krocích bude mít projekt některé chyby kompilace po přidání kódu XAML nebo kódu do projektu. Tyto chyby zůstanou při přidávání kódu v pozdějších krocích nepřítomné.

#### <a name="to-create-the-wizard-window-ui"></a>Vytvoření uživatelského rozhraní okna Průvodce

1. V projektu ProjectTemplateWizard otevřete místní nabídku pro soubor WizardWindow. XAML a pak zvolte možnost **otevřít** . otevře se okno v návrháři.

2. V zobrazení jazyka XAML návrháře nahraďte aktuální kód XAML následujícím XAML. Jazyk XAML definuje uživatelské rozhraní, které obsahuje záhlaví, a <xref:System.Windows.Controls.Grid> obsahuje stránky průvodce a navigační tlačítka v dolní části okna.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml" id="Snippet10":::

    > [!NOTE]
    > Okno, které je vytvořeno v tomto XAML, je odvozeno od <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> základní třídy. Když přidáte vlastní dialogové okno WPF do sady Visual Studio, doporučujeme, abyste z této třídy odvodili dialogové okno tak, aby měly konzistentní styly s ostatními dialogovými okny sady Visual Studio, a aby se předešlo problémům s modálními dialogy, které by jinak mohly nastat. Další informace naleznete v tématu [vytváření a Správa modálních](../extensibility/creating-and-managing-modal-dialog-boxes.md)dialogových oken.

3. Pokud vyvíjíte Visual Basic projekt, odeberte `ProjectTemplateWizard` obor názvů z `WizardWindow` názvu třídy v `x:Class` atributu `Window` elementu. Tento prvek je na prvním řádku XAML. Až budete hotovi, první řádek by měl vypadat jako v následujícím příkladu.

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. Otevřete soubor kódu na pozadí souboru WizardWindow. XAML.

5. Nahraďte obsah tohoto souboru s výjimkou `using` deklarací v horní části souboru s následujícím kódem.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb" id="Snippet4":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs" id="Snippet4":::

#### <a name="to-create-the-first-wizard-page-ui"></a>Vytvoření prvního uživatelského rozhraní stránky průvodce

1. V projektu ProjectTemplateWizard otevřete místní nabídku pro soubor Page1. XAML a pak zvolte možnost **otevřít** a otevřete uživatelský ovládací prvek v návrháři.

2. V zobrazení jazyka XAML návrháře nahraďte aktuální kód XAML následujícím XAML. Jazyk XAML definuje uživatelské rozhraní, které obsahuje textové pole, kde mohou uživatelé zadat adresu URL místních webů, které chtějí použít pro ladění. Uživatelské rozhraní také obsahuje přepínače, u kterých uživatelé mohou určit, zda je projekt v izolovaném prostoru.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml" id="Snippet11":::

3. Pokud vyvíjíte Visual Basic projekt, odeberte `ProjectTemplateWizard` obor názvů z `Page1` názvu třídy v `x:Class` atributu `UserControl` elementu. Toto je první řádek XAML. Až skončíte, první řádek by měl vypadat nějak takto.

    ```xml
    <UserControl x:Class="Page1"
    ```

4. Nahraďte obsah souboru Page1. XAML s výjimkou `using` deklarací v horní části souboru s následujícím kódem.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs" id="Snippet2":::

#### <a name="to-create-the-second-wizard-page-ui"></a>Vytvoření druhého uživatelského rozhraní stránky průvodce

1. V projektu ProjectTemplateWizard otevřete místní nabídku pro soubor Page2. XAML a pak zvolte možnost **otevřít**.

     Uživatelský ovládací prvek se otevře v návrháři.

2. V zobrazení XAML nahraďte aktuální kód XAML následujícím XAML. Jazyk XAML definuje uživatelské rozhraní, které obsahuje rozevírací seznam pro výběr základního typu sloupce webu, pole se seznamem pro zadání předdefinované nebo vlastní skupiny, pod kterou se má zobrazit sloupec webu v galerii, a textové pole pro zadání názvu sloupce webu.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml" id="Snippet12":::

3. Pokud vyvíjíte Visual Basic projekt, odeberte `ProjectTemplateWizard` obor názvů z `Page2` názvu třídy v `x:Class` atributu `UserControl` elementu. Toto je první řádek XAML. Až skončíte, první řádek by měl vypadat nějak takto.

    ```xml
    <UserControl x:Class="Page2"
    ```

4. Nahraďte obsah souboru kódu na pozadí souboru Page2. XAML s výjimkou `using` deklarací v horní části souboru s následujícím kódem.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs" id="Snippet3":::

## <a name="implement-the-wizard"></a>Implementace průvodce
 Definujte hlavní funkčnost Průvodce implementací <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní. Toto rozhraní definuje metody, které Visual Studio volá při spuštění a dokončení průvodce, a v některých případech i při spuštění průvodce.

#### <a name="to-implement-the-wizard"></a>Implementace průvodce

1. V projektu ProjectTemplateWizard otevřete soubor s kódem SiteColumnProjectWizard.

2. Celý obsah tohoto souboru nahraďte následujícím kódem.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb" id="Snippet7":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs" id="Snippet7":::

## <a name="create-the-sharepoint-commands"></a>Vytvoření příkazů SharePointu
 Vytvořte dva vlastní příkazy, které volají do objektového modelu serveru SharePoint. Jeden příkaz určuje, zda je adresa URL webu, kterou uživatel v průvodci používá, platná. Druhý příkaz načte všechny typy polí ze zadaného webu služby SharePoint, aby uživatelé mohli vybrat, které z nich se má použít jako základ pro svůj nový sloupec webu.

#### <a name="to-define-the-sharepoint-commands"></a>Definování příkazů služby SharePoint

1. V projektu **SharePointCommands** otevřete soubor kódu Commands.

2. Celý obsah tohoto souboru nahraďte následujícím kódem.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb" id="Snippet9":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs" id="Snippet9":::

## <a name="checkpoint"></a>CheckPoint
 V tomto okamžiku v tomto návodu je veškerý kód průvodce nyní v projektu. Sestavte projekt, abyste se ujistili, že se zkompiluje bez chyb.

#### <a name="to-build-your-project"></a>Sestavení projektu

1. Na řádku nabídek klikněte na **sestavit** sestavení  >  **řešení**.

## <a name="removing-the-keysnk-file-from-the-project-template"></a>Odebrání souboru key. snk ze šablony projektu
 V [tomto návodu: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), vytvořená šablona projektu obsahuje soubor Key. snk, který se používá k podepsání instance projektu sloupce webu. Tento soubor Key. snk již není nutný, protože průvodce nyní vygeneruje nový soubor Key. snk pro každý projekt. Odeberte soubor Key. snk ze šablony projektu a odeberte odkazy na tento soubor.

#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Odebrání souboru key. snk ze šablony projektu

1. V **Průzkumník řešení** v uzlu **SiteColumnProjectTemplate** otevřete místní nabídku pro soubor **Key. snk** a pak zvolte **Odstranit**.

2. V potvrzovacím dialogovém okně, které se zobrazí, klikněte na tlačítko **OK** .

3. V uzlu **SiteColumnProjectTemplate** otevřete soubor SiteColumnProjectTemplate. vstemplate a poté z něj odeberte následující prvek.

    ```xml
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
    ```

4. Uložte soubor a zavřete ho.

5. V uzlu **SiteColumnProjectTemplate** otevřete soubor ProjectTemplate. csproj nebo ProjectTemplate. vbproj a poté `PropertyGroup` z něj odeberte následující prvek.

    ```xml
    <PropertyGroup>
      <SignAssembly>true</SignAssembly>
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
    </PropertyGroup>
    ```

6. Odeberte následující `None` prvek.

    ```xml
    <None Include="key.snk" />
    ```

7. Uložte soubor a zavřete ho.

## <a name="associating-the-wizard-with-the-project-template"></a>Přidružení průvodce k šabloně projektu
 Nyní, když jste implementovali průvodce, je nutné přidružit průvodce k šabloně projektu **sloupce webu** . Existují tři postupy, které je třeba provést:

1. Podepište sestavení průvodce silným názvem.

2. Získejte token veřejného klíče pro sestavení průvodce.

3. Přidejte odkaz na sestavení průvodce v souboru. vstemplate pro šablonu projektu **sloupce webu** .

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Podepsání sestavení průvodce silným názvem

1. V **Průzkumník řešení** otevřete místní nabídku pro projekt **ProjectTemplateWizard** a pak zvolte možnost **vlastnosti**.

2. Na kartě **podepisování** vyberte zaškrtávací políčko **podepsat sestavení** .

3. V seznamu **Vyberte soubor klíče se silným názvem** vyberte **\<New...>** .

4. V dialogovém okně **vytvořit klíč se silným názvem** zadejte název nového souboru klíče, zrušte zaškrtnutí políčka **chránit soubor klíče heslem** a pak klikněte na tlačítko **OK** .

5. Otevřete místní nabídku pro projekt **ProjectTemplateWizard** a pak zvolte možnost **sestavit** a vytvořte soubor ProjectTemplateWizard.dll.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Získání tokenu veřejného klíče pro sestavení průvodce

1. V **nabídce Start** klikněte na položku **všechny programy**, zvolte **možnost Microsoft Visual Studio**, zvolte možnost **Visual Studio Tools** a pak zvolte možnost **Developer Command Prompt**.

     Otevře se okno příkazového řádku sady Visual Studio.

2. Spusťte následující příkaz a nahraďte *PathToWizardAssembly* úplnou cestou k sestavenému ProjectTemplateWizard.dll sestavení pro projekt ProjectTemplateWizard na vývojovém počítači:

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     Token veřejného klíče pro sestavení ProjectTemplateWizard.dll se zapisuje do okna příkazového řádku sady Visual Studio.

3. Nechte okno příkazového řádku sady Visual Studio otevřené. V dalším postupu budete potřebovat token veřejného klíče.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Přidání odkazu na sestavení průvodce v souboru. vstemplate

1. V **Průzkumník řešení** rozbalte uzel projektu **SiteColumnProjectTemplate** a otevřete soubor SiteColumnProjectTemplate. vstemplate.

2. Poblíž konce souboru přidejte následující `WizardExtension` prvek mezi `</TemplateContent>` `</VSTemplate>` značky a. Nahraďte hodnotu *tokenu* `PublicKeyToken` atributu tokenem veřejného klíče, který jste získali v předchozím postupu.

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     Další informace o elementu naleznete `WizardExtension` v tématu [wizardextension – element &#40;Templates sady Visual Studio&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Uložte soubor a zavřete ho.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Přidání nahraditelných parametrů do souboru Elements.xml v šabloně projektu
 Do souboru *Elements.xml* v projektu SiteColumnProjectTemplate přidejte několik nahraditelných parametrů. Tyto parametry jsou inicializovány v `RunStarted` metodě ve `SiteColumnProjectWizard` třídě, kterou jste definovali dříve. Když uživatel vytvoří projekt sloupce webu, Visual Studio automaticky nahradí tyto parametry v souboru *Elements.xml* v novém projektu hodnotami uvedenými v průvodci.

 Nahraditelný parametr je token, který začíná a končí znakem dolaru ($). Kromě definování vlastních nahraditelných parametrů můžete použít předdefinované parametry, které jsou definovány a inicializovány systémem projektu služby SharePoint. Další informace najdete v tématu [nahraditelných parametrů](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Přidání nahraditelných parametrů do souboru Elements.xml

1. V projektu SiteColumnProjectTemplate nahraďte obsah souboru *Elements.xml* následujícím kódem XML.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
             Name="$fieldname$"
             DisplayName="$fieldname$"
             Type="$selectedfieldtype$"
             Group="$selectedgrouptype$">
      </Field>
    </Elements>
    ```

     Nové XML změní hodnoty `Name` `DisplayName` atributů,, `Type` a `Group` na vlastní nahraditelný parametr.

2. Uložte soubor a zavřete ho.

## <a name="add-the-wizard-to-the-vsix-package"></a>Přidání průvodce do balíčku VSIX
 Chcete-li nasadit průvodce pomocí balíčku VSIX, který obsahuje šablonu projektu sloupce webu, přidejte odkazy na projekt průvodce a projekt příkazy služby SharePoint do souboru source. extension. vsixmanifest v projektu VSIX.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Přidání průvodce do balíčku VSIX

1. V **Průzkumník řešení** v projektu **SiteColumnProjectItem** otevřete místní nabídku pro soubor **source. extension. vsixmanifest** a pak zvolte **otevřít**.

     Visual Studio otevře soubor v editoru manifestu.

2. Na kartě **assets (prostředky** ) Editoru klikněte na tlačítko **Nový** .

     Otevře se dialogové okno **Přidat nový prostředek** .

3. V seznamu **typ** vyberte možnost **Microsoft. VisualStudio. Assembly**.

4. V seznamu **zdroj** vyberte **projekt v aktuálním řešení**.

5. V seznamu **projekt** zvolte možnost **ProjectTemplateWizard** a pak klikněte na tlačítko **OK** .

6. Na kartě **assets (prostředky** ) editoru znovu klikněte na tlačítko **Nový** .

     Otevře se dialogové okno **Přidat nový prostředek** .

7. V seznamu **typ** zadejte **SharePoint. Commands. v4**.

8. V seznamu **zdroj** vyberte **projekt v aktuálním řešení**.

9. V seznamu **projekt** vyberte projekt **SharePointCommands** a pak klikněte na tlačítko **OK** .

10. V panelu nabídek zvolte sestavení sestavení   >  **sestavení** a pak se ujistěte, že řešení je sestavení bez chyb.

## <a name="test-the-wizard"></a>Otestování Průvodce
 Nyní jste připraveni otestovat Průvodce. Nejdřív začněte ladit řešení SiteColumnProjectItem v experimentální instanci sady Visual Studio. Pak otestujte průvodce pro projekt sloupce webu v experimentální instanci aplikace Visual Studio. Nakonec sestavte a spusťte projekt, abyste ověřili, že sloupec web funguje podle očekávání.

#### <a name="to-start-debugging-the-solution"></a>Spuštění ladění řešení

1. Restartujte Visual Studio s přihlašovacími údaji správce a pak otevřete řešení SiteColumnProjectItem.

2. V projektu ProjectTemplateWizard otevřete soubor kódu SiteColumnProjectWizard a poté přidejte zarážku do prvního řádku kódu v `RunStarted` metodě.

3. Na panelu nabídek vyberte možnost **ladění**  >  **výjimek**.

4. V dialogovém okně **výjimky** ověřte, zda jsou **vyvolaná** a **uživatelem Neošetřená** zaškrtávací políčka pro **výjimky modulu CLR** vymazána a poté klikněte na tlačítko **OK** .

5. Spusťte ladění tak, že vyberete klávesu **F5** nebo v řádku nabídek vyberete **ladění**  >  **Spustit ladění**.

     Visual Studio nainstaluje rozšíření na%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 a spustí experimentální instanci sady Visual Studio. Otestujete položku projektu v této instanci aplikace Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Testování průvodce v aplikaci Visual Studio

1. V experimentální instanci aplikace Visual Studio, na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

2. Rozbalte uzel **Visual C#** nebo **Visual Basic** uzel (v závislosti na jazyku, který podporuje šablona projektu), rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

3. V seznamu šablon projektu zvolte **sloupec web**, pojmenujte projekt **SiteColumnWizardTest** a pak klikněte na tlačítko **OK** .

4. Ověřte, zda se kód v jiné instanci sady Visual Studio zastaví na zarážce, kterou jste nastavili dříve v `RunStarted` metodě.

5. Pokračujte v ladění projektu volbou klávesy **F5** nebo v řádku nabídek zvolte možnost **ladění**  >  **pokračovat**.

6. V **Průvodci vlastním nastavením služby SharePoint** zadejte adresu URL webu, který chcete použít pro ladění, a poté klikněte na tlačítko **Další** .

7. Na druhé stránce **Průvodce vlastním nastavením služby SharePoint** proveďte následující výběry:

   - V seznamu **typ** vyberte možnost **Boolean**.

   - V seznamu **Skupina** vyberte možnost **vlastní Ano/žádné sloupce**.

   - Do pole **název** zadejte **sloupec ano/ne** a pak klikněte na tlačítko **Dokončit** .

     V **Průzkumník řešení** se zobrazí nový projekt a obsahuje položku projektu s názvem **pole1** a aplikace Visual Studio otevře soubor *Elements.xml* projektu v editoru.

8. Ověřte, zda *Elements.xml* obsahuje hodnoty, které jste zadali v průvodci.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Testování sloupce webu ve službě SharePoint

1. V experimentální instanci aplikace Visual Studio, vyberte klávesu **F5** .

     Sloupec web je zabalen a nasazen na webu služby SharePoint, který určuje vlastnost **Adresa URL webu** projektu. Webový prohlížeč otevře výchozí stránku tohoto webu.

    > [!NOTE]
    > Pokud se zobrazí dialogové okno **ladění skriptu zakázáno** , klikněte na tlačítko **Ano** a pokračujte v ladění projektu.

2. V nabídce **Akce webu** klikněte na možnost **Nastavení webu**.

3. Na stránce nastavení lokality v části **Galerie** vyberte odkaz **sloupce webu** .

4. V seznamu sloupců lokality ověřte, že vlastní skupina s **Ano/bez sloupců** obsahuje sloupec s názvem **můj sloupec ano/ne** a pak zavřete webový prohlížeč.

## <a name="clean-up-the-development-computer"></a>Vyčištění vývojového počítače
 Po dokončení testování položky projektu odeberte šablonu projektu z experimentální instance aplikace Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Vyčištění vývojového počítače

1. V experimentální instanci aplikace Visual Studio, na panelu nabídek vyberte **nástroje**  >  **rozšíření a aktualizace**.

     Otevře se dialogové okno **rozšíření a aktualizace** .

2. V seznamu rozšíření zvolte **sloupec lokalita** a pak klikněte na tlačítko **odinstalovat** .

3. V dialogovém okně, které se zobrazí, kliknutím na tlačítko **Ano** potvrďte, že chcete rozšíření odinstalovat, a kliknutím na tlačítko **restartovat nyní** dokončete odinstalaci.

4. Zavřete experimentální instanci sady Visual Studio a instanci, ve které je řešení CustomActionProjectItem otevřené.

     Informace o tom, jak nasadit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozšíření, najdete v tématu [odeslání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

## <a name="see-also"></a>Viz také
- [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Vytváření šablon položek a projektů pro položky projektu služby SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Postupy: Použití průvodců se šablonami projektů](../extensibility/how-to-use-wizards-with-project-templates.md)
