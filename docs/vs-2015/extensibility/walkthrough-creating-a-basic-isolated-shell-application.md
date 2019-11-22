---
title: 'Návod: Vytvoření základní aplikace izolovaného prostředí | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b6dc84dd8d9f19012c4d09ba9bfd974ec181b9f6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291270"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Návod: Vytvoření základní aplikace izolovaného prostředí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak vytvořit řešení izolovaného prostředí, přizpůsobit nápovědu k oknu nástrojů a vytvořit instalační program, který nainstaluje izolované prostředí.  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Pro nasazení izolovaného prostředí je nutné také použít Distribuovatelný balíček prostředí Visual Studio Shell (izolovaný režim).  
  
## <a name="creating-an-isolated-shell-solution"></a>Vytvoření řešení izolovaného prostředí  
 V této části se dozvíte, jak použít šablonu projektu izolované prostředí sady Visual Studio k vytvoření řešení izolovaného prostředí. Řešení obsahuje následující projekty:  
  
- *Řešení*. AboutBoxPackage projekt, který umožňuje přizpůsobit vzhled okna s popisem a nápovědu.  
  
- Projekt ShellExtensionsVSIX, který obsahuje soubor source. extension. vsixmanifest definující různé komponenty aplikace izolovaného prostředí.  
  
- Projekt *řešení* , který vytváří spustitelný soubor, který vyvolá aplikaci izolovaného prostředí. Tento projekt obsahuje složku pro přizpůsobení prostředí, která umožňuje upravit vzhled a chování aplikace izolovaného prostředí.  
  
- Projekt uživatelského rozhraní pro *řešení* , který vytváří satelitní sestavení definující příkazy aktivní nabídky a lokalizovatelné řetězce.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Vytvoření základního řešení izolovaného prostředí  
  
1. Otevřete Visual Studio a vytvořte nový projekt.  
  
2. V okně **Nový projekt** rozbalte položku **jiné typy projektů** a potom **rozšiřitelnost**. Vyberte šablonu projektu **izolované prostředí sady Visual Studio** .  
  
3. Pojmenujte projekt `MyVSShellStub` a zadejte umístění. Ujistěte se, že je zaškrtnuté políčko **vytvořit adresář pro řešení** a pak klikněte na **OK**.  
  
     Nové řešení se zobrazí v **Průzkumník řešení**.  
  
4. Sestavte řešení a spusťte ladění aplikace izolovaného prostředí.  
  
     Zobrazí se izolované prostředí sady Visual Studio. Záhlaví se přečte **MyVSShellStub**. Ikona záhlaví je vygenerována z \MyVSShellStub\Resource Files\ApplicationIcon.ico.  
  
## <a name="customizing-the-application-name-and-icon"></a>Přizpůsobení názvu a ikony aplikace  
 Svou aplikaci můžete chtít označit pomocí názvu vaší společnosti a jejího loga v záhlaví. Následující kroky ukazují, jak změnit název a ikonu, které se zobrazí v záhlaví vlastní aplikace, změnou definičního souboru balíčku MyVSShellStub. Application. pkgdef.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Přizpůsobení názvu a ikony aplikace  
  
1. V projektu MyVSShellStub otevřete \Shell Customization\MyVSShellStub.Application.pkgdef.  
  
2. Změňte hodnotu `AppName` elementu na **"AppName" = "Fabrikam Music Editor"** .  
  
3. Chcete-li změnit ikonu aplikace, zkopírujte do adresáře \MyVSShellStub\MyVSShellStub\MyVSShellStub\ jinou ikonu. Přejmenujte existující soubor ApplicationIcon. ico na ApplicationIcon1. ico. Přejmenujte nový soubor na ApplicationIcon. ico.  
  
4. Sestavte řešení a spusťte ladění. Zobrazí se rozhraní IDE izolovaného prostředí. Záhlaví má novou ikonu vedle slov **Editor společnosti Fabrikam Music**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Přizpůsobení domovské stránky výchozího webového prohlížeče  
 V této části se dozvíte, jak změnit výchozí domovskou stránku okna **webového prohlížeče** změnou definičního souboru balíčku.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Přizpůsobení výchozí domovské stránky webového prohlížeče  
  
1. V souboru MyVSShellStub. Application. pkgdef změňte hodnotu prvku `DefaultHomePage` na "<https://www.microsoft.com>".  
  
2. Znovu sestavte projekt MyVSShellStub.  
  
3. Sestavte řešení a spusťte ladění.  
  
4. V **zobrazení/jiných oknech**klikněte na **webový prohlížeč**. V okně **webového prohlížeče** se zobrazí domovská stránka společnosti Microsoft Corporation.  
  
## <a name="removing-the-print-command"></a>Odebrání příkazu tisk  
 Soubor. vsct v projektu s uživatelským rozhraním izolovaného prostředí se skládá ze sady deklarací`>`*prvku* `<Define name=No_`formuláře, kde *element* je jednou ze standardních nabídek a příkazů sady Visual Studio.  
  
 Pokud je deklarace odkomentována, tato nabídka nebo příkaz jsou vyloučeny z izolovaného prostředí. Naopak, pokud je deklarace deklarována, nabídka nebo příkaz jsou součástí izolovaného prostředí.  
  
 V následujících krocích zrušíte komentář k příkazu Print v souboru. vsct.  
  
#### <a name="to-remove-the-print-command"></a>Odebrání příkazu tisk  
  
1. Ověřte, že se příkaz **Tisk** zobrazuje v nabídce **soubor** v aplikaci izolovaného prostředí.  
  
2. V projektu MyVSShellStubUI otevřete \Resource Files\MyVSShellStubUI.vsct pro úpravy.  
  
3. Odkomentovat tento řádek:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4. Tím se odebere příkaz Print.  
  
5. Spusťte ladění aplikace izolovaného prostředí. Ověřte, že je pryč příkaz **soubor/tisk** .  
  
## <a name="removing-features-from-the-isolated-shell"></a>Odebrání funkcí z izolovaného prostředí  
 Některé balíčky, které jsou načteny se sadou Visual Studio, můžete odebrat úpravou souboru. pkgundef, pokud nechcete tyto funkce ve vlastní aplikaci izolovaného prostředí. Balíček zadáte v jednom z podklíčů klíče registru $RootKey $ \Packages.  
  
> [!NOTE]
> Identifikátory GUID funkcí sady Visual Studio najdete v tématu [GUID balíčků funkcí sady Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
 Následující postup ukazuje, jak odebrat Editor XML z izolovaného prostředí.  
  
#### <a name="to-remove-the-xml-editor"></a>Odebrání editoru XML  
  
1. Otevřete soubor MyVSShellStub. pkgundef ve složce vlastního nastavení prostředí projektu MyVSShellStub.  
  
2. Odkomentujte následující řádek:  
  
     [$RootKey$\Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3. Znovu sestavte řešení a spusťte ladění izolovaného prostředí. Otevřete soubor XML, například \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Ověřte, že klíčová slova XML v souboru nejsou zabarvení a že při zadání "<" na řádku se nepřinesou popisy XML.  
  
## <a name="customizing-the-helpabout-box"></a>Přizpůsobení pole help/o  
 Můžete přizpůsobit pole pro nápovědu/informace, které je vytvořeno jako součást šablony projektu izolované prostředí.  
  
#### <a name="to-customize-the-company-name"></a>Přizpůsobení názvu společnosti  
  
1. Název společnosti, informace o autorských právech, verze produktu a popis produktu najdete v projektu MyVSShellStub. AboutBoxPackage v souboru \Properties\AssemblyInfo.cs. Otevřete tento soubor.  
  
2. Změňte `AssemblyCompany` hodnotu na **Fabrikam**, `AssemblyProduct` a `AssemblyTitle` hodnoty na **Fabrikam Music Editor**a `AssemblyCopyright` hodnotu **Copyright © Fabrikam 2015**:  
  
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
  
3. Chcete-li přidat popis produktu, změňte hodnotu `AssemblyDescription` na popis programu **Fabrikam Music Editor.** :  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4. Spusťte ladění a v aplikaci izolovaného prostředí otevřete okno **help/o** . Měli byste vidět změněné řetězce. Název pole help/o je stejný jako hodnota `AssemblyTitle` v AssemblyInfo.cs.  
  
5. V souboru MyVSShellStub. AboutBoxPackage\AboutBox.xaml se nacházejí vlastnosti samotného pole **help/o** . Chcete-li změnit šířku pole help/o, přejděte do bloku `AboutDialogStyle` a nastavte vlastnost `Width` na 200:  
  
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
  
6. Znovu sestavte řešení a spusťte ladění izolovaného prostředí. Pole help/o by mělo být přibližně čtvercové.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Před nasazením aplikace izolovaného prostředí  
 Vaše aplikace izolovaného prostředí se dá nainstalovat na libovolný počítač, který má Distribuovatelný balíček prostředí Visual Studio Shell (izolovaný režim). Další informace o redistribuovatelných balíčcích najdete na webu věnovaném [stažení rozšiřitelnosti sady Visual Studio](https://go.microsoft.com/fwlink/?LinkID=119298) .  
  
## <a name="deploying-the-isolated-shell-application"></a>Nasazení aplikace izolovaného prostředí  
 Aplikaci izolovaného prostředí nasadíte do cílového počítače vytvořením projektu instalace. Je nutné zadat tyto věci:  
  
- Rozložení složek a souborů v cílovém počítači.  
  
- Podmínky spuštění, které zaručují, že .NET Framework a modul runtime prostředí sady Visual Studio jsou nainstalovány v cílovém počítači.  
  
  V následujícím postupu budete muset na svém počítači nainstalovat program InstallShield Limited Edition.  
  
#### <a name="to-create-the-setup-project"></a>Vytvoření projektu instalace  
  
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel řešení a pak klikněte na **Přidat nový projekt**.  
  
2. V dialogovém okně **Nový projekt** rozbalte položku **jiné typy projektů** a potom vyberte možnost **nastavení a nasazení**. Vyberte šablonu InstallShield. Zadejte název nového projektu `MySetup` a klikněte na tlačítko **OK**.  
  
3. Pokud je již nainstalována aplikace InstallShield s omezením verze, pokračujte k dalšímu kroku.  
  
    Pokud již není nainstalována aplikace InstallShield s omezením verze, zobrazí se stránka pro stažení InstallShield. Podle pokynů stáhněte a nainstalujte produkt a zvolte verzi programu InstallShield, která je kompatibilní s vaší verzí sady Visual Studio. Musíte se rozhodnout, jestli chcete zaregistrovat instalaci programu InstallShield, nebo ho použít jako zkušební verzi. Po dokončení instalace je nutné restartovat aplikaci Visual Studio.  
  
   > [!IMPORTANT]
   > Před vytvořením projektu InstallShield je nutné spustit aplikaci Visual Studio jako správce. Pokud to neuděláte, při sestavování projektu se zobrazí chyba.  
  
   Následující kroky ukazují, jak nakonfigurovat projekt instalace.  
  
> [!IMPORTANT]
> Před konfigurací projektu instalace se ujistěte, že jste sestavili konfiguraci verze svého projektu izolovaného prostředí alespoň jednou.  
  
#### <a name="to-configure-the-setup-project"></a>Konfigurace projektu instalace  
  
1. V **Průzkumník řešení**v projektu **MySetup** vyberte možnost **Pomocník projektu**. V dolním řádku okna **asistenta projektu** vyberte možnost **informace o aplikaci**. Jako název vaší aplikace zadejte **Fabrikam** jako název vaší společnosti a programový **Editor Fabrikam** . V pravém dolním rohu **pomocníka projektu**vyberte šipku pro posun.  
  
2. V **části** **aplikace vyžaduje, aby byl v počítači nainstalován veškerý software?** potom vyberte možnost **Microsoft .NET Framework 4,5 úplný balíček**.  
  
3. V dolní části okna klikněte na tlačítko **soubory aplikace** a ujistěte se, že je vybraná složka **Editor hudby společnosti Fabrikam** .  
  
4. Klikněte na tlačítko **Přidat soubory** . V dialogovém okně **Přidat soubory** přidejte ze složky **MyVSShellStub\Release** následující soubory:  
  
    1. MyVSShellStub.exe.config  
  
    2. DebuggerProxy.dll  
  
    3. DebuggerProxy.dll.manifest  
  
    4. MyVSShellStub.pkgdef  
  
    5. MyVSShellStub. pkgundef  
  
    6. MyVSShellStub.winprf  
  
    7. Úvodní. bmp  
  
5. Klikněte na tlačítko **Přidat výstupy projektu** a přidejte **MyVSShellStub/primární výstup**. Klikněte na tlačítko **OK**.  
  
6. V levém podokně v části **cílový počítač**klikněte pravým tlačítkem myši na **uzel programu pro úpravu hudby společnosti Fabrikam [INSTALLDIR]** a přidejte **novou složku** s názvem **Extensions**.  
  
7. V levém podokně klikněte pravým tlačítkem na uzel **rozšíření** a přidejte novou složku s názvem **Application (aplikace**).  
  
8. Vyberte složku **aplikace** a klikněte na tlačítko **Přidat výstupy projektu** a pak vyberte primární výstup z projektu MyVSShellStub. AboutBoxPackage.  
  
9. Klikněte na tlačítko **Přidat soubory** a ze složky \MyVSShellStub\Release\Extensions\Application\ přidejte následující soubory:  
  
    - MyVSShellStub.AboutBoxPackage.pkgdef  
  
    - MyVSShellStub.Application.pkgdef  
  
10. V levém podokně klikněte pravým tlačítkem na uzel **hudební editor společnosti Fabrikam [INSTALLDIR]** a přidejte novou složku s názvem **1033**.  
  
11. Vyberte složku 1033 a potom klikněte na tlačítko **Přidat výstupy projektu** a vyberte primární výstup z projektu MyVSShellStubUI.  
  
12. Přejděte do okna s **použitím klávesových zkratek** .  
  
13. Kliknutím na **Nový** vytvořte zástupce a vyberte **[Složkaprogramfiles] \Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output**.  
  
14. Přejděte do podokna **pohovor na instalaci** .  
  
15. Nastavit všechny položky na **ne**.  
  
16. V **Průzkumník řešení**v projektu MySetup otevřete položku **definovat požadavky na instalaci a akce \ požadavky**. Otevře se okno **požadavky** .  
  
17. Klikněte pravým tlačítkem na **požadavky na systémový software** a vyberte **vytvořit novou podmínku spuštění**. Zobrazí se **Průvodce systémem vyhledávání** .  
  
18. V podokně **co chcete najít?** v rozevíracím seznamu vyberte **položku registru** a klikněte na **Další**.  
  
19. V podokně **jak ho chcete vyhledat?** vyberte jako kořen registru **HKEY_LOCAL_MACHINE** . Zadejte **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** pro 64 systémy nebo **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** pro 32 bitové systémy a jako hodnotu registru zadejte **install** . Klikněte na **Další**.  
  
20. V podokně **co chcete s hodnotou?** zadejte **Tento produkt vyžaduje instalaci sady Visual Studio 2015 Isolated Shell Redistributable.** jako text zobrazení a klikněte na tlačítko **Dokončit**.  
  
21. Znovu sestavte řešení izolovaného prostředí a vytvořte projekt instalace.  
  
     Soubor Setup. exe můžete najít v následující složce:  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Testování instalačního programu  
 Chcete-li otestovat instalaci, zkopírujte soubor Setup. exe do jiného počítače a spusťte spustitelný soubor instalace. Měli byste být schopni spustit aplikaci izolovaného prostředí.
