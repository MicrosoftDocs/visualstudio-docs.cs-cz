---
title: 'Návod: Vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2 | Dokumentace Microsoftu'
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
ms.openlocfilehash: d4512dc15d394cdf2442d8bfcf440ccb31623a29
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942072"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>Návod: Vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2
  Po definování vlastního typu položky projektu služby SharePoint a přidružení šablony projektu v sadě Visual Studio, můžete také poskytnout průvodce pro šablony. Průvodce můžete použít ke shromažďování informací od uživatelů při použití šablony k vytvoření nového projektu, který obsahuje položky projektu. Informace, které slouží k inicializaci položky projektu.  
  
 V tomto názorném postupu přidáte průvodce v šabloně projektu sloupce webu, který je znázorněn v [návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md). Když uživatel vytvoří projektu sloupce webu, Průvodce shromažďuje informace o sloupci webu (jako je základním typem a skupiny) a přidá tyto informace *Elements.xml* souboru v novém projektu.  
  
 Tento návod demonstruje následující úkoly:  
  
-   Vytvoření průvodce pro vlastní typ položky projektu služby SharePoint, který je spojen se šablonou projektu.  
  
-   Definování vlastního průvodce, uživatelské rozhraní, které se podobá integrované průvodců pro projekty služby SharePoint v sadě Visual Studio.  
  
-   Vytvoření dvou *příkazů služby SharePoint* , který slouží k volání do místního webu služby SharePoint, je spuštěn průvodce. SharePoint – příkazy jsou metody, které můžete používat s rozšířeními Visual Studia pro volání rozhraní API v objektovém modelu serveru SharePoint. Další informace najdete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Použití nahraditelných parametrů pro inicializaci soubory Sharepointového projektu s daty, která budete shromažďovat průvodce.  
  
-   Vytvoření nového souboru .snk v každé nové instanci projektu sloupce webu. Tento soubor se používá k podepsání projektu výstup tak, aby sestavení řešení služby SharePoint je možné nasadit do globální mezipaměti sestavení.  
  
-   Ladění a testování v průvodci.  
  
> [!NOTE]  
> Řadu ukázkový pracovní postupy, najdete v části [ukázky pracovního postupu služby SharePoint](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples).  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li provést Tento názorný postup, musíte nejdřív vytvořit řešení SiteColumnProjectItem provedením [návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 Budete potřebovat následující komponenty na vývojovém počítači k dokončení tohoto návodu:  
  
- Podporované edice systému Windows, SharePoint a Visual Studio.
  
- Visual Studio SDK. Tento návod používá **projekt VSIX** šablony v sadě SDK k vytvoření balíčku VSIX k nasazení položky projektu. Další informace najdete v tématu [rozšíření nástrojů SharePoint v sadě Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Znalost následujících konceptů je užitečná, ale není požadována k dokončení návodu:  
  
- Průvodce pro šablony projektů a položek v sadě Visual Studio. Další informace najdete v tématu [postupy: použití průvodců se šablonami projektů](../extensibility/how-to-use-wizards-with-project-templates.md) a <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní.  
  
- Sloupce webu ve službě SharePoint. Další informace najdete v tématu [sloupce](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
## <a name="understand-the-wizard-components"></a>Seznámení s komponentami Průvodce
 Průvodce předváděnou v tomto názorném postupu obsahuje několik součástí. Následující tabulka popisuje tyto komponenty.  
  
|Součást|Popis|  
|---------------|-----------------|  
|Průvodce implementací|Jedná se o třídu s názvem `SiteColumnProjectWizard`, která implementuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní. Toto rozhraní definuje metody, které Visual Studio se volá při spuštění a dokončení a v určitých časech během průvodce spustí průvodce.|  
|Průvodce uživatelského rozhraní|To je okno založeného na WPF, s názvem `WizardWindow`. Toto okno obsahuje dva uživatelské ovládací prvky, s názvem `Page1` a `Page2`. Tyto uživatelské ovládací prvky představují dvě stránky průvodce.<br /><br /> V tomto názorném postupu <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metoda implementaci Průvodce zobrazí Průvodce uživatelského rozhraní.|  
|Průvodce datového modelu|Jedná se o zprostředkující třídu s názvem `SiteColumnWizardModel`, která poskytuje vrstvu mezi Průvodce uživatelského rozhraní a implementaci průvodce. Tato ukázka používá tuto třídu účelem abstrahování implementaci průvodce a Průvodce uživatelského rozhraní od sebe navzájem; Tato třída není požadovaná součást všech průvodců.<br /><br /> V tomto názorném postupu předá implementaci průvodce `SiteColumnWizardModel` objekt v okně Průvodce poznat Průvodce uživatelského rozhraní. Průvodce uživatelské rozhraní používá metody tohoto objektu k uložení hodnot ovládacích prvků v uživatelském rozhraní a provádět úkoly, jako je ověření, že vstupní adresa URL je platná. Po dokončení Průvodce uživatel používá implementaci průvodce `SiteColumnWizardModel` objektem pro určení konečný stav uživatelského rozhraní.|  
|Podepisování vedoucí projektu|Toto je pomocná třída s názvem `ProjectSigningManager`, který se používá v implementaci průvodce k vytvoření nového souboru klíč.snk v každé nové instance projektu.|  
|SharePoint – příkazy|Toto jsou metody, které jsou používány Průvodce datovým modelem provést volání do místního webu služby SharePoint, je-li spuštěn průvodce. Protože příkazy Sharepointu musí cílit na rozhraní .NET Framework 3.5, tyto příkazy jsou implementovány v jiném sestavení než zbytek kódu průvodce.|  
  
## <a name="create-the-projects"></a>Vytváření projektů
 K dokončení tohoto návodu, budete muset přidat různé projekty do řešení SiteColumnProjectItem, které jste vytvořili v [návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):  
  
- Projekt WPF. Budete implementovat <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní a definovat Průvodce uživatelského rozhraní v tomto projektu.  
  
- Projekt knihovny tříd, který definuje příkazů služby SharePoint. Tento projekt musí cílit na rozhraní.NET Framework 3.5.  
  
  Začněte postup vytvořením projektů.  
  
#### <a name="to-create-the-wpf-project"></a>Vytvoření projektu WPF
  
1.  V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], otevřete řešení SiteColumnProjectItem.  
  
2.  V **Průzkumníka řešení**, otevřete místní nabídku **SiteColumnProjectItem** uzel řešení, zvolte **přidat**a klikněte na tlačítko **nový projekt**.  
  
3.  V horní části **přidat nový projekt** dialogové okno pole, ujistěte se, že **rozhraní .NET Framework 4.5** je vybrán v seznamu verzí rozhraní .NET Framework.  
  
4.  Rozbalte **Visual C#** uzlu nebo **jazyka Visual Basic** uzel a zvolte **Windows** uzlu.  
  
5.  V seznamu šablon projektu vyberte **Knihovna uživatelských ovládacích prvků WPF**, pojmenujte projekt **ProjectTemplateWizard**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **ProjectTemplateWizard** projektu do řešení a otevře soubor výchozího UserControl1.xaml.  
  
6.  Odstraňte UserControl1.xaml soubor z projektu.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>Chcete-li vytvořit příkazy projektu služby SharePoint  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro uzel SiteColumnProjectItem řešení, zvolte **přidat**a klikněte na tlačítko **nový projekt**.  
  
2.  V horní části **přidat nový projekt** dialogového okna zvolte **rozhraní .NET Framework 3.5** v seznam verzí rozhraní .NET Framework.  
  
3.  Rozbalte **Visual C#** uzlu nebo **jazyka Visual Basic** uzel a klikněte na tlačítko **Windows** uzlu.  
  
4.  Zvolte **knihovny tříd** šablony projektu, pojmenujte projekt **SharePointCommands**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **SharePointCommands** projektu do řešení a otevře soubor výchozího kódu Class1.  
  
5.  Odstraňte soubor kódu Class1 z projektu.  
  
## <a name="configure-the-projects"></a>Konfigurace projektů
 Před vytvořením průvodce, musíte přidat některé soubory kódu a odkazy na sestavení do projektů.  
  
#### <a name="to-configure-the-wizard-project"></a>Ke konfiguraci projektu průvodce  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku **ProjectTemplateWizard** uzel projektu a klikněte na tlačítko **vlastnosti**.  
  
2.  V **Návrháře projektu**, zvolte **aplikace** kartu pro projekt jazyka Visual C# nebo **kompilaci** kartu pro projekt jazyka Visual Basic.  
  
3.  Ujistěte se, že Cílová architektura, která je nastavena na rozhraní .NET Framework 4.5, není rozhraní .NET Framework 4.5 Client Profile.  
  
     Další informace najdete v tématu [postupy: cílení na určitou verzi rozhraní .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
4.  Otevřete místní nabídku **ProjectTemplateWizard** projektu, zvolte **přidat**a klikněte na tlačítko **nová položka**.  
  
5.  Zvolte **okno (WPF)** položky, název položky **WizardWindow**a klikněte na tlačítko **přidat** tlačítko.  
  
6.  Přidejte dva **uživatelské ovládací prvek (WPF)** položky do projektu a pojmenujte je **Page1** a **strany Page2**.  
  
7.  Přidejte čtyři soubory kódu do projektu a přiřaďte jim následující názvy:  
  
    -   SiteColumnProjectWizard  
  
    -   SiteColumnWizardModel  
  
    -   ProjectSigningManager  
  
    -   CommandIds  
  
8.  Otevřete místní nabídku **ProjectTemplateWizard** uzel projektu a klikněte na tlačítko **přidat odkaz**.  
  
9. Rozbalte **sestavení** uzlu, vyberte **rozšíření** uzlu a pak vyberte zaškrtávací políčka vedle následující sestavení:  
  
    -   EnvDTE  
  
    -   Sestavení Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
10. Zvolte **OK** tlačítko pro přidání sestavení do projektu.  
  
11. V **Průzkumníka řešení**v části **odkazy** složku **ProjectTemplateWizard** projektu, zvolte **EnvDTE**.  
  
12. V **vlastnosti** okna, změňte hodnotu **Embed Interop Types** vlastnost **False**.  
  
13. Pokud vytváříte projekt jazyka Visual Basic, importujte obor názvů ProjectTemplateWizard do svého projektu pomocí **Návrháře projektu**.  
  
     Další informace najdete v tématu [postupy: Přidání nebo odebrání importovaných oborů názvů &#40;jazyka Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>Ke konfiguraci projektu SharePointcommands
  
1.  V **Průzkumníka řešení**, zvolte **SharePointCommands** uzel projektu.  
  
2.  V panelu nabídky zvolte **projektu**, **přidat existující položku**.  
  
3.  V **přidat existující položku** dialogové okno, přejděte do složky, která obsahuje soubory kódu pro projekt ProjectTemplateWizard a klikněte na tlačítko **CommandIds** soubor kódu.  
  
4.  Klikněte na šipku vedle položky **přidat** tlačítko a klikněte na tlačítko **přidat jako odkaz** možnost v nabídce, která se zobrazí.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá soubor kódu **SharePointCommands** projekt jako odkaz. Soubor kódu je umístěn v **ProjectTemplateWizard** projektu, ale kód v souboru také kompilováno do **SharePointCommands** projektu.  
  
5.  V **SharePointCommands** projektu, přidejte další soubor kódu, který je pojmenován příkazy.  
  
6.  Zvolte projekt SharePointCommands a pak na panelu nabídek zvolte **projektu** > **přidat odkaz**.  
  
7.  Rozbalte **sestavení** uzlu, vyberte **rozšíření** uzlu a pak vyberte zaškrtávací políčka vedle následující sestavení:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
8.  Zvolte **OK** tlačítko pro přidání sestavení do projektu.  
  
## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Vytvoření modelu průvodce, podpisové správce a ID příkazů služby SharePoint
 Přidání kódu do projektu ProjectTemplateWizard implementovat následující součásti v ukázce:  
  
- Identifikátory příkazů služby SharePoint. Tyto řetězce identifikovat příkazů služby SharePoint, které používá průvodce. Dále v tomto názorném postupu přidáte kód do projektu SharePointCommands provádět příkazy.  
  
- Průvodce datového modelu.  
  
- Podepisování vedoucí projektu.  
  
  Další informace o těchto součástech naleznete v tématu [seznámení se s komponentami průvodce](#wizardcomponents).  
  
#### <a name="to-define-the-sharepoint-command-ids"></a>Chcete-li definovat ID příkazů služby SharePoint
  
1.  V projektu ProjectTemplateWizard otevřete soubor kódu CommandIds a celý obsah tohoto souboru nahraďte následujícím kódem.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]  
  
#### <a name="to-create-the-wizard-model"></a>Chcete-li vytvořit model Průvodce  
  
1.  Otevřete soubor kódu SiteColumnWizardModel a celý obsah tohoto souboru nahraďte následujícím kódem.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]  
  
#### <a name="to-create-the-project-signing-manager"></a>Chcete-li vytvořit podpisový vedoucí projektu  
  
1.  Otevřete soubor kódu ProjectSigningManager a celý obsah tohoto souboru nahraďte následujícím kódem.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]  
  
## <a name="create-the-wizard-ui"></a>Vytvořit průvodce uživatelského rozhraní
 Přidejte XAML k definování uživatelského rozhraní v okně průvodce a dva uživatelské ovládací prvky, které poskytují uživatelské rozhraní pro stránky průvodce a přidejte kód, který definuje chování okna a uživatelské ovládací prvky. Průvodce, který vytvoříte se podobá integrovaného průvodce pro projekty služby SharePoint v sadě Visual Studio.  
  
> [!NOTE]  
>  V následujících krocích, vaše bude mít projekt několik chyb kompilace poté, co přidáte kód nebo XAML do projektu. K těmto chybám předejdete přidáním kódu v dalších krocích.  
  
#### <a name="to-create-the-wizard-window-ui"></a>Chcete-li vytvořit v okně Průvodce uživatelského rozhraní
  
1.  V projektu ProjectTemplateWizard, otevřete místní nabídku pro soubor WizardWindow.xaml a klikněte na tlačítko **otevřete** otevření okna v návrháři.  
  
2.  V zobrazení XAML v Návrháři nahraďte aktuální XAML následující XAML. XAML definuje uživatelské rozhraní, která obsahuje nadpis, <xref:System.Windows.Controls.Grid> , která obsahuje stránky průvodce a navigačních tlačítek v dolní části okna.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]  
  
    > [!NOTE]  
    >  V okně, které se vytvoří v tomto XAML je odvozen z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> základní třídy. Když přidáte vlastní dialogové okno WPF se sadou Visual Studio, doporučujeme odvodit vaše dialogové okno z této třídy mít konzistentní stylu s jiná dialogová okna Visual Studio a aby se zabránilo problémům modální dialogové okno, které by jinak mohlo dojít. Další informace najdete v tématu [vytváření a správa modálních dialogových oken](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Pokud vyvíjíte projekt jazyka Visual Basic, odeberte `ProjectTemplateWizard` obor názvů z `WizardWindow` název třídy v `x:Class` atribut `Window` elementu. Tento element má na prvním řádku XAML. Jakmile budete hotovi, první řádek by měl vypadat jako v následujícím příkladu.  
  
    ```xml  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  Otevřete soubor kódu na pozadí pro soubor WizardWindow.xaml.  
  
5.  Nahraďte obsah tohoto souboru, s výjimkou `using` deklarace v horní části souboru následujícím kódem.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]  
  
#### <a name="to-create-the-first-wizard-page-ui"></a>Vytvoření první stránce průvodce uživatelského rozhraní
  
1.  V projektu ProjectTemplateWizard, otevřete místní nabídku pro soubor Page1.xaml a klikněte na tlačítko **otevřete** otevřete uživatelský ovládací prvek v návrháři.  
  
2.  V zobrazení XAML v Návrháři nahraďte aktuální XAML následující XAML. XAML definuje uživatelské rozhraní, která obsahuje textové pole, kde mohou uživatelé zadat adresu URL místní servery, které chtějí používat pro ladění. Uživatelské rozhraní také možnost tlačítka, pomocí kterého mohou uživatelé zadat, zda je projekt v izolovaném prostoru.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]  
  
3.  Pokud vyvíjíte projekt jazyka Visual Basic, odeberte `ProjectTemplateWizard` obor názvů z `Page1` název třídy v `x:Class` atribut `UserControl` elementu. Toto je na prvním řádku XAML. Jakmile budete hotovi, první řádek by měl vypadat nějak takto.  
  
    ```xml  
    <UserControl x:Class="Page1"  
    ```  
  
4.  Nahraďte obsah souboru Page1.xaml, s výjimkou `using` deklarace v horní části souboru následujícím kódem.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]  
  
#### <a name="to-create-the-second-wizard-page-ui"></a>Chcete-li vytvořit na druhé stránce průvodce uživatelského rozhraní
  
1.  V projektu ProjectTemplateWizard, otevřete místní nabídku pro soubor Page2.xaml a klikněte na tlačítko **otevřete**.  
  
     Uživatelský ovládací prvek se otevře v návrháři.  
  
2.  V XAML zobrazení nahraďte aktuální XAML následující XAML. XAML definuje uživatelské rozhraní, která zahrnuje rozevíracího seznamu pro výběr základního typu sloupce webu, pole se seznamem pro zadání vestavěná nebo vlastní skupinu v rámci kterého se má zobrazit sloupce webu ve galerii a textové pole pro zadání názvu sloupce webu.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]  
  
3.  Pokud vyvíjíte projekt jazyka Visual Basic, odeberte `ProjectTemplateWizard` obor názvů z `Page2` název třídy v `x:Class` atribut `UserControl` elementu. Toto je na prvním řádku XAML. Jakmile budete hotovi, první řádek by měl vypadat nějak takto.  
  
    ```xml  
    <UserControl x:Class="Page2"  
    ```  
  
4.  Nahraďte obsah souboru použití modelu code-behind Page2.xaml souboru, s výjimkou `using` deklarace v horní části souboru následujícím kódem.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]  
  
## <a name="implement-the-wizard"></a>Implementace průvodce
 Definujte hlavní funkce Průvodce implementací <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní. Toto rozhraní definuje metody, které Visual Studio se volá při spuštění a dokončení a v určitých časech během průvodce spustí průvodce.  
  
#### <a name="to-implement-the-wizard"></a>K implementaci Průvodce  
  
1.  V projektu ProjectTemplateWizard otevřete soubor kódu SiteColumnProjectWizard.  
  
2.  Celý obsah tohoto souboru nahraďte následujícím kódem.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]  
  
## <a name="create-the-sharepoint-commands"></a>Vytvoření příkazu SharePoint
 Vytvořte dvě vlastní příkazy, které provede volání do objektového modelu serveru SharePoint. Jeden příkaz určuje, zda je platná adresa URL webu, že uživatel zadá v průvodci. Tento příkaz načte všechny typy polí v zadaném Sharepointovém webu tak, aby uživatelé mohli vybrat, který z nich se použije jako základ pro jejich nové sloupce webu.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Chcete-li definovat příkazů služby SharePoint  
  
1.  V **SharePointCommands** projektu, otevřete soubor kódu příkazy.  
  
2.  Celý obsah tohoto souboru nahraďte následujícím kódem.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku návodu je celý kód pro průvodce v projektu. Sestavte projekt, abyste měli jistotu, že se zkompiluje bez chyb.  
  
#### <a name="to-build-your-project"></a>K sestavení projektu  
  
1.  V panelu nabídky zvolte **sestavení** > **sestavit řešení**.  
  
## <a name="removing-the-keysnk-file-from-the-project-template"></a>Odstraňuje se soubor klíč.snk ze šablony projektu
 V [návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), šablony projektu, který jste vytvořili obsahuje klíč.snk soubor, který se používá k podepsání každou instanci projektu sloupce webu. Tento soubor klíč.snk již není nezbytné, protože nyní vygeneruje nový soubor klíč.snk u každého projektu průvodce. Odebrat soubor klíč.snk ze šablony projektu a odeberte odkazy na tento soubor.  
  
#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Odebrání souboru klíč.snk ze šablony projektu  
  
1.  V **Průzkumníku řešení**v části **SiteColumnProjectTemplate** uzel, otevřete místní nabídku **klíč.snk** souboru a klikněte na tlačítko **odstranit**.  
  
2.  V dialogovém okně potvrzení, která se zobrazí, zvolte **OK** tlačítko.  
  
3.  V části **SiteColumnProjectTemplate** uzel, otevřete soubor SiteColumnProjectTemplate.vstemplate a potom z něj odebrat následující element.  
  
    ```xml  
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
    ```  
  
4.  Soubor uložte a zavřete.  
  
5.  V části **SiteColumnProjectTemplate** uzel, otevřete soubor ProjectTemplate.csproj nebo ProjectTemplate.vbproj a odeberte následující `PropertyGroup` element z něj.  
  
    ```xml  
    <PropertyGroup>  
      <SignAssembly>true</SignAssembly>  
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
    </PropertyGroup>  
    ``` 
  
6.  Odebrat následující `None` elementu.  
  
    ```xml  
    <None Include="key.snk" />  
    ```  
  
7.  Soubor uložte a zavřete.  
  
## <a name="associating-the-wizard-with-the-project-template"></a>Průvodce přidružení šablony projektu
 Teď, když naimplementujete průvodci, je třeba přidružit v průvodci **sloupce webu** šablony projektu. Existují tři postupy, které musíte udělat toto:  
  
1.  Podepsání sestavení silným názvem průvodce.  
  
2.  Získání tokenu veřejného klíče pro sestavení průvodce.  
  
3.  V souboru .vstemplate přidejte odkaz na sestavení průvodce **sloupce webu** šablony projektu.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>K podepsání sestavení silným názvem Průvodce  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku **ProjectTemplateWizard** projektu a klikněte na tlačítko **vlastnosti**.  
  
2.  Na **podepisování** kartu, vyberte **podepsat sestavení** zaškrtávací políčko.  
  
3.  V **vyberte soubor klíče se silným názvem** klikněte na položku  **\<nový … >**.  
  
4.  V **vytvořit klíč se silným názvem** dialogové okno, zadejte název pro nový soubor klíče, zrušte zaškrtnutí pole **chránit můj soubor klíče s heslem** zaškrtněte políčko a klikněte na tlačítko **OK** tlačítko.  
  
5.  Otevřete místní nabídku **ProjectTemplateWizard** projektu a klikněte na tlačítko **sestavení** k vytvoření souboru ProjectTemplateWizard.dll.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>K získání tokenu veřejného klíče pro sestavení průvodce  
  
1.  Na **nabídky Start**, zvolte **všechny programy**, zvolte **sady Microsoft Visual Studio**, zvolte **Visual Studio Tools**a klikněte na tlačítko  **Developer Command Prompt**.  
  
     Otevře se okno Příkazový řádek sady Visual Studio.  
  
2.  Spusťte následující příkaz a nahraďte *PathToWizardAssembly* s úplnou cestou k ProjectTemplateWizard.dll sestavení pro projekt ProjectTemplateWizard ve svém vývojovém počítači:  
  
    ```cmd  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Token veřejného klíče pro sestavení ProjectTemplateWizard.dll se zapisují do okna příkazového řádku aplikace Visual Studio.  
  
3.  Nechte okno Příkazový řádek sady Visual Studio otevřené. Při dalším postupu budete potřebovat token veřejného klíče.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Chcete-li přidat odkaz na sestavení průvodce v souboru .vstemplate  
  
1.  V **Průzkumníka řešení**, rozbalte **SiteColumnProjectTemplate** uzel projektu a otevřete soubor SiteColumnProjectTemplate.vstemplate.  
  
2.  Na konci souboru, přidejte následující `WizardExtension` prvek mezi `</TemplateContent>` a `</VSTemplate>` značky. Nahradit *tokenu* hodnotu `PublicKeyToken` atribut s veřejným klíčem, který jste získali v předchozím postupu.  
  
    ```xml  
    <WizardExtension>  
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>  
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Další informace o `WizardExtension` prvku, naleznete v tématu [WizardExtension – Element &#40;šablony sady Visual Studio&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Soubor uložte a zavřete.  
  
## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>V šabloně projektu souboru Elements.xml přidejte nahraditelné parametry
 Přidat několik nahraditelné parametry *Elements.xml* soubor v projektu SiteColumnProjectTemplate. Tyto parametry jsou inicializovány v `RunStarted` metodu `SiteColumnProjectWizard` třídu, která jste definovali dříve. Když uživatel vytvoří projektu sloupce webu, aplikace Visual Studio automaticky nahradí tyto parametry v *Elements.xml* souboru v novém projektu s hodnotami, které jsou zadány v průvodci.  
  
 Nahraditelných parametrů je token, který začíná a končí znakem dolaru ($). Kromě definování nahraditelné parametry, můžete použít předdefinované parametry, které jsou definovány a inicializován pomocí systému Sharepointových projektů. Další informace najdete v tématu [nahraditelné parametry](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Chcete-li přidat do souboru Elements.xml nahraditelné parametry
  
1.  V projektu SiteColumnProjectTemplate nahraďte obsah *Elements.xml* soubor s následující kód XML.  
  
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
  
     Nové XML změní hodnoty `Name`, `DisplayName`, `Type`, a `Group` atributy pro vlastní nahraditelné parametry.  
  
2.  Soubor uložte a zavřete.  
  
## <a name="add-the-wizard-to-the-vsix-package"></a>Přidat průvodce k balíčku VSIX
 Průvodce spolu s balíčkem VSIX, který obsahuje šablonu projektu sloupce webu nasadit, přidejte odkazy na Průvodce projektu a projekt služby SharePoint příkazy pro soubor source.extension.vsixmanifest v projektu VSIX.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Chcete-li přidat průvodce k balíčku VSIX  
  
1.  V **Průzkumníka řešení**v **SiteColumnProjectItem** projektu, otevřete místní nabídku **source.extension.vsixmanifest** souboru a klikněte na tlačítko **Otevřít**.  
  
     Visual Studio otevře soubor v editoru manifestu.  
  
2.  Na **prostředky** kartu Editor, zvolte **nový** tlačítko.  
  
     **Přidat nové aktivum** zobrazí se dialogové okno.  
  
3.  V **typ** klikněte na položku **Microsoft.VisualStudio.Assembly**.  
  
4.  V **zdroj** klikněte na položku **projekt v aktuálním řešení**.  
  
5.  V **projektu** klikněte na položku **ProjectTemplateWizard**a klikněte na tlačítko **OK** tlačítko.  
  
6.  Na **prostředky** kartu Editor, zvolte **nový** tlačítko znovu.  
  
     **Přidat nové aktivum** zobrazí se dialogové okno.  
  
7.  V **typ** seznamu, zadejte **SharePoint.Commands.v4**.  
  
8.  V **zdroj** klikněte na položku **projekt v aktuálním řešení**.  
  
9. V **projektu** klikněte na položku **SharePointCommands** projektu a klikněte na tlačítko **OK** tlačítko.  
  
10. V panelu nabídky zvolte **sestavení** > **sestavit řešení**a ujistěte se, že toto řešení vytvoří bez chyb.  
  
## <a name="test-the-wizard"></a>Průvodce testu
 Nyní jste připraveni k testování průvodce. Nejprve spusťte ladění řešení SiteColumnProjectItem v experimentální instanci sady Visual Studio. Otestujte Průvodce projektu sloupce webu v experimentální instanci sady Visual Studio. Nakonec sestavte a spusťte projekt tak, aby ověřte, že sloupec webu funguje podle očekávání.  
  
#### <a name="to-start-debugging-the-solution"></a>Spusťte ladění řešení  
  
1.  Restartujte sadu Visual Studio s přihlašovacími údaji správce a pak otevřete SiteColumnProjectItem řešení.  
  
2.  V projektu ProjectTemplateWizard, otevřete soubor kódu SiteColumnProjectWizard a na první řádek kódu přidejte zarážku `RunStarted` metody.  
  
3.  V panelu nabídky zvolte **ladění** > **výjimky**.  
  
4.  V **výjimky** dialogové okno pole, ujistěte se, že **vyvolání** a **uživatelem neošetřené** zaškrtnutí políček u **výjimky modulu Common Language Runtime**jsou vymazány a klikněte na tlačítko **OK** tlačítko.  
  
5.  Spuštění ladění zvolením **F5** klíče nebo na panelu nabídek, výběrem **ladění** > **spustit ladění**.  
  
     Visual Studio nainstaluje rozšíření do %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 a spustí experimentální instanci sady Visual Studio. Položku projektu budete testovat v této instanci aplikace Visual Studio.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>K otestování průvodce v sadě Visual Studio  
  
1. V experimentální instanci sady Visual Studio na panelu nabídek zvolte **souboru** > **nový** > **projektu**.  
  
2. Rozbalte **Visual C#** uzlu nebo **jazyka Visual Basic** uzel (v závislosti na jazyk, který podporuje šablony projektu), Rozbalit **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.  
  
3. V seznamu šablon projektu vyberte **sloupce webu**, pojmenujte projekt **SiteColumnWizardTest**a klikněte na tlačítko **OK** tlačítko.  
  
4. Ověřte, že kód ve druhé instanci aplikace Visual Studio zastaví na zarážce, kterou jste nastavili dříve v `RunStarted` metody.  
  
5. Pokračovat v ladění projektu výběrem **F5** klíče nebo na panelu nabídek, výběrem **ladění** > **pokračovat**.  
  
6. V **Průvodce přizpůsobením SharePoint**, zadejte adresu URL webu, který chcete použít pro ladění a klikněte na tlačítko **Další** tlačítko.  
  
7. Na druhé stránce **Průvodce přizpůsobením SharePoint**, proveďte následující výběr:  
  
   - V **typ** klikněte na položku **logická**.  
  
   - V **skupiny** klikněte na položku **vlastní sloupce logická**.  
  
   - V **název** zadejte **tento sloupec Logická**a klikněte na tlačítko **Dokončit** tlačítko.  
  
     V **Průzkumníku řešení**, zobrazí se nový projekt a obsahuje položku projektu s názvem **pole1**, a sady Visual Studio otevře projektu *Elements.xml* souboru v editoru.  
  
8. Ověřte, že *Elements.xml* obsahuje hodnoty, které jste zadali v průvodci.  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>K otestování sloupce webu ve službě SharePoint  
  
1.  V experimentální instanci sady Visual Studio, zvolte **F5** klíč.  
  
     Sloupec webu je zabalit a nasadit do Sharepointu webu, který **adresa URL webu** určuje vlastnost projektu. Webový prohlížeč otevře výchozí stránku webu.  
  
    > [!NOTE]  
    >  Pokud **ladění skriptů zakázáno** dialogové okno se zobrazí, zvolte **Ano** tlačítka pokračovat v ladění projektu.  
  
2.  Na **Akce webu** nabídce zvolte **nastavení webu**.  
  
3.  Na stránce Nastavení lokality v rámci **Galerie**, zvolte **sloupce webu** odkaz.  
  
4.  V seznamu sloupců webu, ověřte, že **vlastní sloupce logická** skupina obsahuje sloupec s názvem **tento sloupec Logická**a pak zavřete webový prohlížeč.  
  
## <a name="clean-up-the-development-computer"></a>Vyčištění vývojovém počítači
 Po dokončení testování položku projektu, odeberte šablony projektu z experimentální instanci sady Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Chcete-li vyčistit vývojovém počítači  
  
1.  V experimentální instanci sady Visual Studio na panelu nabídek zvolte **nástroje** > **rozšíření a aktualizace**.  
  
     **Rozšíření a aktualizace** zobrazí se dialogové okno.  
  
2.  V seznamu rozšíření zvolte **sloupce webu**a klikněte na tlačítko **odinstalovat** tlačítko.  
  
3.  V dialogovém okně, které se zobrazí, zvolte **Ano** potvrďte, že chcete odinstalovat rozšíření a klikněte na tlačítko **restartovat nyní** tlačítko pro dokončení odinstalace.  
  
4.  Ukončete experimentální instanci sady Visual Studio a instance, ve kterém je otevřen CustomActionProjectItem řešení.  
  
     Informace o tom, jak nasadit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozšíření, naleznete v tématu [přesouvání rozšíření sady Visual Studio](/visualstudio/extensibility/shipping-visual-studio-extensions).  
  
## <a name="see-also"></a>Viz také:
 [Návod: Vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Vytváření šablon položek a projektů pro položky projektu služby SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Odkaz na schéma šablon sady Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Postupy: Použití průvodců se šablonami projektů](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
