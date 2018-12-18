---
title: 'Návod: Vytvoření základní izolované aplikace prostředí | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 901bbf12c9c1d153b84b3ed74f6ae8e97ebb2c9b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777315"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Návod: Vytvoření základní aplikace izolovaného prostředí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak vytvořit řešení izolovaného prostředí, přizpůsobit panel nástrojů nápovědy a vytvořit instalační program, který nainstaluje izolovaného prostředí.  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Pokud chcete nasadit izolovaného prostředí, musíte použít také Distribuovatelný balíček prostředí Visual Studio Shell (izolovaný režim).  
  
## <a name="creating-an-isolated-shell-solution"></a>Vytvoření řešení izolovaného prostředí  
 V této části ukazuje, jak vytvořit řešení izolovaného prostředí pomocí Visual Studio Shell izolované šablony projektu. Řešení obsahuje následující projekty:  
  
-   *SolutionName*. AboutBoxPackage projekt, který umožňuje přizpůsobit vzhled Nápověda/o pole.  
  
-   ShellExtensionsVSIX projektu, který obsahuje soubor source.extension.vsixmanifest, který definuje různé součásti aplikací izolovaného prostředí.  
  
-   *SolutionName* projekt, který vytvoří spustitelný soubor, který volá aplikací izolovaného prostředí. Tento projekt obsahuje složku vlastního nastavení prostředí, která umožňuje přizpůsobit vzhled a chování aplikací izolovaného prostředí.  
  
-   *SolutionName* projekt uživatelského rozhraní, který vytvoří satelitní sestavení, který definuje aktivní příkazy a lokalizovatelných řetězců.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>K vytvoření řešení základní izolovaného prostředí  
  
1.  Otevřít Visual Studio a vytvořte nový projekt.  
  
2.  V **nový projekt** okna rozbalte **ostatní typy projektů** a potom **rozšiřitelnost**. Vyberte **Visual Studio Shell izolované** šablony projektu.  
  
3.  Pojmenujte projekt `MyVSShellStub` a zadejte umístění. Ujistěte se, že **vytvořit adresář pro řešení** je zaškrtnuté políčko a potom klikněte na tlačítko **OK**.  
  
     Nové řešení se zobrazí v **Průzkumníka řešení**.  
  
4.  Sestavte řešení a spuštění ladění aplikací izolovaného prostředí.  
  
     Visual Studio, které se zobrazí izolovaného prostředí. Načte záhlaví **MyVSShellStub**. Ikona záhlaví se generuje z \MyVSShellStub\Resource Files\ApplicationIcon.ico.  
  
## <a name="customizing-the-application-name-and-icon"></a>Přizpůsobení aplikace názvu a ikony  
 Můžete k vytvoření aplikace s použitím názvu vaší společnosti a jeho loga v záhlaví programu. Následující kroky ukazují, jak chcete-li změnit název a ikonu, která se zobrazí v záhlaví okna vlastní aplikaci tak, že změníte definiční soubor balíčku, MyVSShellStub.Application.pkgdef.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Chcete-li přizpůsobit název aplikace a ikona  
  
1.  V projektu MyVSShellStub otevřete \Shell Customization\MyVSShellStub.Application.pkgdef.  
  
2.  Změnit `AppName` hodnotu prvku na **"AppName" = "Editor Hudba Fabrikam"**  
  
3.  Chcete-li změnit ikonu aplikace, zkopírujte do adresáře \MyVSShellStub\MyVSShellStub\MyVSShellStub\ jinou ikonu. Přejmenujte stávající soubor ApplicationIcon.ico na ApplicationIcon1.ico. Přejmenujte tento nový soubor do ApplicationIcon.ico.  
  
4.  Sestavte řešení a spusťte ladění. Izolované prostředí IDE se zobrazí. Záhlaví má vaše nová ikona vedle slov **Fabrikam Hudba Editor**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Přizpůsobení stránky výchozí webový prohlížeč-Domů  
 Tato část ukazuje, jak změnit výchozí domovskou stránku **webový prohlížeč** okna tak, že změníte definiční soubor balíčku.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Chcete-li přizpůsobit výchozí domovskou stránku webového prohlížeče  
  
1. V souboru MyVSShellStub.Application.pkgdef změnit `DefaultHomePage` hodnotu prvku na "<http://www.microsoft.com>".  
  
2. Znovu sestavte projekt MyVSShellStub.  
  
3. Sestavte řešení a spusťte ladění.  
  
4. V **zobrazení / ostatní Windows**, klikněte na tlačítko **webový prohlížeč**. **Webový prohlížeč** okně se zobrazí domovská stránka Microsoft Corporation.  
  
## <a name="removing-the-print-command"></a>Odebírá se příkaz pro tisk  
 Souboru .vsct v projektu aplikace izolovaného prostředí uživatelského rozhraní se skládá ze sady deklarací v podobě `<Define name=No_` *Element*`>`, kde *Element* je jedním z standardní nabídky sady Visual Studio a příkazy.  
  
 Pokud je prohlášení neokomentovaném textu, tuto nabídku nebo příkaz je vyloučen z izolovaného prostředí. Naopak pokud deklarace je zakomentovaný, nabídky nebo příkaz je součástí izolované prostředí.  
  
 V následujících krocích Odkomentujte příkaz pro tisk v souboru .vsct.  
  
#### <a name="to-remove-the-print-command"></a>Chcete-li odebrat příkaz pro tisk  
  
1.  Ověřte, že **tisk** příkazu se zobrazí na **souboru** nabídky v aplikaci izolovaného prostředí.  
  
2.  V projektu MyVSShellStubUI otevřete \Resource Files\MyVSShellStubUI.vsct pro úpravy.  
  
3.  Zrušením komentáře u tohoto řádku:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  Tato operace odebere příkaz pro tisk.  
  
5.  Spusťte ladění aplikací izolovaného prostředí. Ověřte, že **souboru / tisk** příkaz je odstraněný.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Odebírání funkcí z izolovaného prostředí  
 Můžou odebrat některé balíčky, které jsou načteny pomocí sady Visual Studio pomocí úpravy souboru .pkgundef, pokud nechcete, aby tyto funkce v aplikaci vlastní izolovaného prostředí. Zadejte balíček v jednom z podklíčů klíče registru \Packages $RootKey$.  
  
> [!NOTE]
>  Identifikátory GUID sady Visual Studio funkce, najdete v tématu [balíček identifikátory GUID z funkce sady Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
 Následující postup ukazuje, jak odebrat XML editor z izolovaného prostředí.  
  
#### <a name="to-remove-the-xml-editor"></a>Chcete-li odebrat editoru XML  
  
1.  Otevřete soubor MyVSShellStub.pkgundef ve složce projektu MyVSShellStub vlastního nastavení prostředí.  
  
2.  Zrušte komentář u následujícího řádku:  
  
     [$RootKey$ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3.  Znovu sestavte řešení a spustit ladění izolovaného prostředí. Otevřete soubor XML, třeba \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Ověřte, že nejsou barevně zvýrazněné klíčová slova jazyka XML v souboru a zadejte tento text "<" na řádku nelze vyvolat popisy XML.  
  
## <a name="customizing-the-helpabout-box"></a>Přizpůsobení Nápověda/o pole  
 Můžete přizpůsobit Nápověda/o pole, který je vytvořen jako součást šablony projektu izolovaného prostředí.  
  
#### <a name="to-customize-the-company-name"></a>Chcete-li přizpůsobit název společnosti  
  
1.  Název společnosti, informace o autorských právech, verze produktu a popis produktu se nacházejí v projektu MyVSShellStub.AboutBoxPackage v souboru \Properties\AssemblyInfo.cs. Tento soubor otevřete.  
  
2.  Změnit `AssemblyCompany` hodnota, která se **Fabrikam**, `AssemblyProduct` a `AssemblyTitle` hodnoty **Fabrikam Hudba Editor**a `AssemblyCopyright` hodnota, která se **Copyright © Společnost Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3.  Chcete-li přidat popis produktu, změňte `AssemblyDescription` hodnota, která se **popis editor Fabrikam Music.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4.  Spustit ladění a v izolovaném prostředí aplikace, otevřete **Nápověda / o** pole. Měli byste vidět změněných řetězců. Název Nápověda/o pole je stejné jako `AssemblyTitle` hodnotu v AssemblyInfo.cs.  
  
5.  Vlastnosti **Nápověda/o** samotného pole se nacházejí v souboru MyVSShellStub.AboutBoxPackage\AboutBox.xaml. Chcete-li změnit šířku Nápověda/o aplikaci, přejděte na `AboutDialogStyle` blokovat a nastavit `Width` vlastnost na hodnotu 200:  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window">  
        <Setter Property="Height" Value="Auto" />  
        <Setter Property="Width" Value="200" />  
        <Setter Property="ShowInTaskbar" Value="False" />  
        <Setter Property="ResizeMode" Value="NoResize" />  
        <Setter Property="WindowStyle" Value="SingleBorderWindow" />  
        <Setter Property="SizeToContent" Value="Height" />  
    </Style>  
    ```  
  
6.  Znovu sestavte řešení a spustit ladění izolovaného prostředí. Nápověda/o pole by měla být přibližně čtvereček.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Před nasazením aplikací izolovaného prostředí  
 Vaše aplikace izolovaného prostředí lze nainstalovat na jakýkoli počítač, který má Distribuovatelný balíček prostředí Visual Studio Shell (izolovaný režim). Další informace o opětovné distribuci balíčku najdete v tématu [stahování rozšíření sady Visual Studio](http://go.microsoft.com/fwlink/?LinkID=119298) webu.  
  
## <a name="deploying-the-isolated-shell-application"></a>Nasazení aplikací izolovaného prostředí  
 Nasazení aplikace izolovaného prostředí na cílovém počítači tak, že vytvoříte projekt instalace. Je nutné zadat tyto věci:  
  
- Rozložení složky a soubory v cílovém počítači.  
  
- Podmínky spuštění, které zaručit, že rozhraní .NET Framework a sady Visual Studio prostředí modulu runtime jsou nainstalovány v cílovém počítači.  
  
  V následujícím postupu musíte do počítače nainstalovat program InstallShield Limited Edition.  
  
#### <a name="to-create-the-setup-project"></a>Vytvoření projektu instalace  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel řešení a potom klikněte na tlačítko **přidat nový projekt**.  
  
2. V **nový projekt** dialogového okna rozbalte **ostatní typy projektů** a pak vyberte **instalace a nasazení**. Vyberte šablonu InstallShield. Název nového projektu `MySetup` a potom klikněte na tlačítko **OK**.  
  
3. Pokud je už nainstalovaný program InstallShield Limited Edition, pokračujte k dalšímu kroku.  
  
    Pokud ještě není nainstalovaný program InstallShield Limited Edition, zobrazí se stránka stahování programu InstallShield. Postupujte podle pokynů ke stažení a instalace produktu, výběr verze nástroje InstallShield, který je kompatibilní s vaší verzí sady Visual Studio. Musíte se rozhodnout, jestli se má zaregistrovat instalaci programu InstallShield nebo ho používat jako zkušební verzi. Po dokončení instalace je nutné restartovat Visual Studio.  
  
   > [!IMPORTANT]
   >  Před vytvořením projektu InstallShield, je nutné spustit aplikaci Visual Studio jako správce. Pokud to neprovedete, zobrazí se chyba při vytváření projektu.  
  
   Další kroky ukazují, jak nakonfigurovat nastavení projektu.  
  
> [!IMPORTANT]
>  Ujistěte se, že jste vytvořili konfigurace pro vydání izolovaného prostředí projektu nejméně jednou předtím, než nakonfigurujete nastavení projektu.  
  
#### <a name="to-configure-the-setup-project"></a>Konfigurace projektu instalace  
  
1.  V **Průzkumníka řešení**v části **MySetup** projektu, zvolte **Project Assistant**. V dolním řádku **Project Assistant** okně zvolte **informací o aplikaci**. Zadejte **Fabrikam** jako název vaší společnosti a **Fabrikam Hudba Editor** jako název vaší aplikace. Zvolte šipku vpřed v pravém dolním rohu **Project Assistant**.  
  
2.  Vyberte **Ano** pod **vaše aplikace vyžaduje veškerý software nainstalovaný na počítači?** a pak vyberte **balíček úplné rozhraní Microsoft .NET Framework 4.5**.  
  
3.  Zvolte **soubory aplikace** tlačítko v dolní části okna a ujistěte se, že **Fabrikam Hudba Editor** je vybrána složka.  
  
4.  Zvolte **přidat soubory** tlačítko. V **přidat soubory** dialogového okna přidejte následující soubory z **MyVSShellStub\Release** složky:  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  Debuggerproxy.dll.manifest měly  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  Klikněte na tlačítko **přidat výstupy projektu** tlačítko a přidejte **MyVSShellStub/primární výstup**. Klikněte na tlačítko **OK**.  
  
6.  V levém podokně v části **cílový počítač**, klikněte pravým tlačítkem na **Fabrikam Hudba Editor [INSTALLDIR]** uzlu a přidejte **novou složku** s názvem **rozšíření** .  
  
7.  Klikněte pravým tlačítkem myši **rozšíření** uzlu v levém podokně a přidejte novou složku s názvem **aplikace**.  
  
8.  Vyberte **aplikace** složky a klikněte na tlačítko **přidat výstupy projektu** tlačítko a pak vyberte primární výstup z projektu MyVSShellStub.AboutBoxPackage.  
  
9. Klikněte na tlačítko **přidat soubory** tlačítko a ve složce \MyVSShellStub\Release\Extensions\Application\ přidat následující soubory:  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. Klikněte pravým tlačítkem myši **Fabrikam Hudba Editor [INSTALLDIR]** uzlu v levém podokně a přidejte novou složku s názvem **1033**.  
  
11. Vyberte složku, 1033 a potom klikněte na tlačítko **přidat výstupy projektu** tlačítko a vyberte primární výstup z projektu MyVSShellStubUI.  
  
12. Přesunout **aplikačních zkratek** okna.  
  
13. Klikněte na tlačítko **nový** vytvořte zástupce a vyberte **[ProgramFilesFolder] \Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output**.  
  
14. Přesunout **instalační Interview** podokně.  
  
15. Nastavit všechny položky **ne**.  
  
16. V **Průzkumníka řešení**, otevřete v projektu MySetup **definovat požadavky na nastavení a akce \ požadavky**. **Požadavky** otevře se okno.  
  
17. Klikněte pravým tlačítkem myši **systémové požadavky softwaru** a vyberte **vytvořit novou podmínku spuštění**. **Průvodce vyhledáváním systému** se zobrazí.  
  
18. V **co chcete najít?** podokně zvolte **záznam v registru** v rozevíracím seznamu a klikněte na **Další**.  
  
19. V **jak chcete hledat?** vyberte **HKEY_LOCAL_MACHINE** jako kořenový klíč registru. Zadejte **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** pro 64bitové systémy nebo **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** pro 32bitové systémy a zadejte  **Nainstalujte** jako hodnotu registru. Klikněte na tlačítko **Další**.  
  
20. V **co chcete udělat s hodnotou?** podokně zadejte **vyžaduje Visual Studio 2015 izolovaného prostředí Redistributable k instalaci tohoto produktu.** zobrazení textu a klikněte na **Dokončit**.  
  
21. Znovu sestavte řešení izolovaného prostředí pro vytvoření projektu instalace.  
  
     Soubor setup.exe najdete v následující složce:  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Testování instalačního programu  
 Pokud chcete otestovat nastavení, zkopírujte soubor setup.exe na jiný počítač a spusťte spustitelný soubor instalace. Je třeba možné spouštět aplikace izolovaného prostředí.

