---
title: Uvnitř sady Visual Studio SDK | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e72020795bc3181e11f0f90eff580a2365d4000
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707572"
---
# <a name="inside-the-visual-studio-sdk"></a>Práce se sadou Visual Studio SDK

Tato část obsahuje podrobné informace o rozšíření sady Visual Studio, včetně architektury sady Visual Studio, komponenty, služby, schémata, nástroje a podobně.

## <a name="extensibility-architecture"></a>Architektura rozšiřitelnosti
 Následující obrázek znázorňuje architekturu rozšiřitelnosti sady Visual Studio. VSPackages poskytují funkce aplikace, která je sdílena v rámci ide jako služby. Standardní ide také nabízí širokou škálu <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>služeb, jako je například , které poskytují přístup k funkci okna ide.

 ![Architektura prostředí – grafika](../../extensibility/internals/media/environment.gif "environment") Zobecněné zobrazení architektury sady Visual Studio

## <a name="vspackages"></a>Balíčky VSPackage
 VSPackages jsou softwarové moduly, které tvoří a rozšiřují Visual Studio s prvky uživatelského rozhraní, služby, projekty, editory a návrháři. VSPackages jsou centrální architektonickou jednotkou sady Visual Studio. Další informace naleznete v tématu [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Shell
 Prostředí Visual Studio poskytuje základní funkce a podporu křížové komunikace mezi jeho součásti VSPackages a MEF rozšíření. Další informace naleznete v [tématu Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Pravidla pro práci s uživatelským prostředím
 Pokud plánujete navrhnout nové funkce pro Visual Studio, měli byste se podívat na tyto pokyny pro návrh a použitelnost tipy: [Visual Studio pokyny pro uživatelské prostředí](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="commands"></a>Příkazy
 Příkazy jsou funkce, které provádějí úkoly, jako je tisk dokumentu, aktualizace zobrazení nebo vytvoření nového souboru.

 Při rozšíření sady Visual Studio můžete vytvořit příkazy a zaregistrovat je pomocí prostředí Sady Visual Studio. Můžete určit, jak se tyto příkazy zobrazí v prostředí IDE, například v nabídce nebo panelu nástrojů. V nabídce **Nástroje** se obvykle zobrazí vlastní příkaz a příkaz pro zobrazení okna nástroje se zobrazí v podnabídce **Ostatní windows** v nabídce **Zobrazení.**

 Při vytváření příkazu je nutné pro něj také vytvořit obslužnou rutinu události. Obslužná rutina události určuje, kdy je příkaz viditelný nebo povolený, umožňuje upravit jeho text a zaručuje, že příkaz při aktivaci odpovídajícím způsobem reaguje. Ve většině případů ide zpracovává příkazy pomocí <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní. Příkazy v sadě Visual Studio jsou zpracovány počínaje nejvnitřnější mste, na základě místního výběru a přecvakující k nejvzdálenějšímu kontextu na základě globálního výběru. Příkazy přidané do hlavní nabídky jsou okamžitě k dispozici pro skriptování.

 Další informace naleznete v [tématu Příkazy, Nabídky a Panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="menus-and-toolbars"></a>Nabídky a panely nástrojů
 Nabídky a panely nástrojů umožňují uživatelům vyvolat příkazy. Nabídky jsou řádky nebo sloupce příkazů, které jsou obvykle zobrazeny jako jednotlivé textové položky v horním okně nástroje. Podnabídky jsou sekundární nabídky, které se zobrazí, když uživatel klepne na příkazy, které obsahují malou šipku. Kontextové nabídky se zobrazí, když uživatel klepne pravým tlačítkem myši na určité prvky uživatelského rozhraní. Některé běžné názvy nabídek jsou **Soubor**, **Úprava**, **Zobrazení**a **Okno**. Další informace naleznete [v tématu Rozšíření nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).

 Panely nástrojů jsou řádky nebo sloupce tlačítek a dalších ovládacích prvků, jako jsou pole se seznamem, seznamy a textová pole. Tlačítka panelu nástrojů mají obvykle obrázky ikon ikon, například ikonu složky pro příkaz **Otevřít soubor** nebo tiskárnu pro příkaz **Tisk.** Všechny prvky panelu nástrojů jsou přidruženy k příkazům. Po klepnutí na tlačítko panelu nástrojů se spustí jeho přidružený příkaz. V případě rozevíracího ovládacího prvku je každá položka v rozevíracím seznamu přidružena k jinému příkazu. Některé ovládací prvky panelu nástrojů, například ovládací prvek rozdělovače, jsou hybridy. Jedna strana ovládacího prvku je tlačítko panelu nástrojů a druhá strana je šipka dolů, která zobrazuje několik příkazů po klepnutí.

## <a name="tool-windows"></a>Nástroj Windows
 Okna nástrojů se používají v ide pro zobrazení informací. **Panel nástrojů**, **Průzkumník řešení**, Okno **Vlastnosti** a **Webový prohlížeč** jsou příklady oken nástrojů.

 Okna nástrojů obvykle nabízejí různé ovládací prvky, se kterými může uživatel pracovat. Například okno **Vlastnosti** umožňuje uživateli nastavit vlastnosti objektů, které slouží určitému účelu. **Vlastnosti** okno se specializuje v tomto smyslu, ale také obecné, protože jej lze použít v mnoha různých situacích. Podobně je okno **Výstup** specializované, protože poskytuje textový výstup, ale obecně, protože mnoho subsystémů v sadě Visual Studio jej může použít k poskytování výstupu uživateli sady Visual Studio.

 Zvažte následující obrázek sady Visual Studio, která obsahuje několik oken nástrojů:

 ![Snímek obrazovky](../../extensibility/internals/media/t1gui.png "T1gui (Fr.)")

 Některá okna nástrojů jsou ukotvena společně v jednom podokně, které zobrazuje okno nástroje Průzkumník řešení a skryje ostatní okna nástrojů, ale zpřístupní je klepnutím na karty. Obrázek znázorňuje další dvě okna nástrojů, okno **Seznam chyb** a **Výstup,** ukotvené společně v jednom podokně.

 Zobrazeno je také podokno hlavního dokumentu, které zobrazuje několik oken editoru. Přestože okna nástrojů mají obvykle pouze jednu instanci (například můžete otevřít pouze **jednu Průzkumníka řešení**), okna editoru mohou mít více instancí, z nichž každá se používá k úpravě samostatného dokumentu, ale všechny jsou ukotveny ve stejném podokně. Obrázek znázorňuje podokno dokumentu, které má dvě okna editoru, jedno okno návrháře formulářů. Všechna okna v podokně dokumentu jsou k dispozici klepnutím na karty, ale okno editoru, které obsahuje EditorPane.cs soubor, je viditelné a aktivní.

 Při rozšíření sady Visual Studio můžete vytvořit okna nástrojů, která uživatelům sady Visual Studio umožní interakci s vaší příponou. Můžete také vytvořit vlastní editory, které umožňují uživatelům sady Visual Studio upravovat dokumenty. Vzhledem k tomu, že okna nástrojů a editory budou integrovány do sady Visual Studio, není třeba je naprogramovat tak, aby se ukotvily nebo se správně zobrazily na kartě. Pokud jsou správně registrovány v sadě Visual Studio, budou mít automaticky typické funkce oken nástrojů a oken dokumentů v sadě Visual Studio. Další informace naleznete v [tématu Rozšíření a přizpůsobení systému Windows .](../../extensibility/extending-and-customizing-tool-windows.md)

## <a name="document-windows"></a>Okna dokumentů
 Okno dokumentu je zarámované podřízené okno okna rozhraní mdi (multiple-document). Okna dokumentů se obvykle používají k hostování textových editorů, editorů formulářů (označované také jako návrháři) nebo k úpravám ovládacích prvků, ale mohou také hostovat jiné typy funkcí. Dialogové okno **Nový soubor** obsahuje příklady oken dokumentů, která visual studio poskytuje.

 Většina editorů je specifická pro programovací jazyk nebo typ souboru, jako jsou stránky HTML, sady rámců, soubory Jazyka C++ nebo soubory hlaviček. Výběrem šablony v dialogovém okně **Nový soubor** uživatel dynamicky vytvoří okno dokumentu pro editor pro typ souboru, který je přidružen k šabloně. Okno dokumentu je také vytvořeno, když uživatel otevře existující soubor.

 Okna dokumentů jsou omezena na klientskou oblast MDI. Každé okno dokumentu má kartu v horní části a pořadí karet je propojeno s jinými okny, která mohou být otevřena v oblasti MDI. Kliknutím pravým tlačítkem myši na kartu okna dokumentu se zobrazí místní nabídka, která obsahuje možnosti rozdělení oblasti MDI na více vodorovných nebo svislých skupin karet. Rozdělení oblasti MDI umožňuje zobrazit více souborů současně. Další informace naleznete [v tématu Document Windows](../../extensibility/internals/document-windows.md).

## <a name="editors"></a>Editory
 Editor Sady Visual Studio umožňuje přizpůsobit jej a použít pro vlastní typ obsahu pomocí rozhraní MEF spravované rozšiřitelnosti (MEF). V mnoha případech nebudete muset vytvořit VSPackage rozšířit editor, i když pokud chcete zahrnout funkce z prostředí (například příkaz nabídky nebo klávesovou zkratku), můžete kombinovat rozšíření MEF s VSPackage.

 Můžete také vytvořit vlastní editor, například pokud chcete číst a zapisovat do databáze, nebo pokud chcete použít návrháře. Můžete také použít externí editor, například Poznámkový blok nebo Microsoft WordPad. Další informace naleznete v [tématu Editor and Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

## <a name="language-services"></a>Jazykové služby
 Pokud chcete, aby editor sady Visual Studio podporoval nová programovací klíčová slova nebo dokonce nový programovací jazyk, vytvořte jazykovou službu. Každá jazyková služba může implementovat některé funkce editoru zcela, částečně nebo vůbec. V závislosti na konfiguraci může jazyková služba poskytovat zvýraznění syntaxe, porovnávání složených závorek, podporu Technologie IntelliSense a další funkce v editoru.

 Jádrem jazykové služby jsou analyzátor a skener. Skener (nebo lexer) rozdělí zdrojový soubor na prvky, které jsou známé jako tokeny a analyzátor vytvoří vztahy mezi těmito tokeny. Při vytváření služby jazyka je nutné implementovat analyzátor a skener tak, aby Visual Studio může pochopit tokeny a gramatiku jazyka. Můžete vytvořit spravované nebo nespravované jazykové služby. Další informace naleznete [v tématu Legacy Language Service Tensibility](../../extensibility/internals/legacy-language-service-extensibility.md).

## <a name="projects"></a>Projekty

V sadě Visual Studio jsou projekty kontejnery, které vývojáři používají k uspořádání a sestavení zdrojového kódu a dalších prostředků. Projekty umožňují organizovat, vytvářet, ladit a nasazovat zdrojový kód, odkazy na webové služby a databáze a další prostředky. VSPackages můžete rozšířit systém projektu sady Visual Studio tím, že poskytuje typy projektů, podtypy projektu a vlastní nástroje.

Projekty mohou být také shromážděny v *řešení*, což je seskupení jednoho nebo více projektů, které spolupracují na vytvoření aplikace. Informace o projektu a stavu, které se týkající se řešení jsou uloženy ve dvou souborech řešení, souboru s textovým [řešením (.sln)](solution-dot-sln-file.md) a souboru možnosti uživatele binárního [řešení (.suo).](solution-user-options-dot-suo-file.md) Tyto soubory jsou podobné souborům skupiny (.vbg), které byly použity v dřívějších verzích jazyka Visual Basic, a souborům pracovního prostoru (.dsw) a uživatelských možností (.opt), které byly použity v dřívějších verzích jazyka C++.

Další informace naleznete v [tématu Projekty](../../extensibility/internals/projects.md) a [řešení](../../extensibility/internals/solutions-overview.md).

## <a name="project-and-item-templates"></a>Šablony projektů a položek
 Visual Studio obsahuje předdefinované šablony projektů a šablony položek projektu. Můžete také vytvořit vlastní šablony nebo získat šablony z komunity a pak je integrovat do sady Visual Studio. [Galerie kódu MSDN](https://code.msdn.microsoft.com/site/search?query=visual%20studio) je místo, kam jít pro šablony a rozšíření.

 Šablony obsahují strukturu projektu a základní soubory, které jsou nutné k vytvoření určitého druhu aplikace, ovládacího prvku, knihovny nebo třídy. Pokud chcete vyvíjet software, který se podobá jedné ze šablon, vytvořte projekt založený na šabloně a potom upravte soubory v tomto projektu.

> [!NOTE]
> Tato architektura šablony [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] není podporována pro projekty.

 Další informace naleznete [v tématu Přidání šablon položek projektu a projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="properties-and-options"></a>Vlastnosti a možnosti
 Okno **Vlastnosti** zobrazuje vlastnosti jedné nebo více vybraných položek: Rozšíření stránek [Možnosti vlastností](../../extensibility/internals/extending-properties.md) obsahuje sady možností, které se týkají určité součásti, například programovací jazyk nebo VSPackage: [Volby a stránky možností](../../extensibility/internals/options-and-options-pages.md). Nastavení jsou obecně funkce související s uživatelským rozhraním, které lze importovat a exportovat: [Podpora uživatelských nastavení](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Služby Visual Studio
 Služba poskytuje určitou sadu rozhraní pro součásti využívat. Visual Studio poskytuje sadu služeb, které lze použít všechny součásti, včetně rozšíření. Služby sady Visual Studio například umožňují dynamické zobrazení nebo skrytí oken nástrojů, umožňují přístup k nápovědě, stavovému řádku nebo událostem uj. Editor sady Visual Studio také poskytuje služby, které lze importovat pomocí rozšíření editoru. Další informace naleznete [v tématu Using and Providing Services](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>Ladicí program
 Ladicí program je uživatelské rozhraní pro součásti ladění specifické pro jazyk. Pokud jste vytvořili novou jazykovou službu, budete muset vytvořit konkrétní ladicí modul pro připojení do ladicího programu. Další informace naleznete v [tématu Visual Studio Debugger rozšiřitelnost](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="source-control"></a>Správa zdrojového kódu
 Informace o implementaci modulu plug-in správy zdrojového kódu nebo balíčku VSPackage naleznete [v tématu Source Control](../../extensibility/internals/source-control.md).

## <a name="wizards"></a>Průvodci
 Průvodce můžete vytvořit ve spojení s novým typem projektu, aby průvodce mohl uživatelům pomoci při vytváření nového projektu tohoto typu správně rozhodovat. Další informace naleznete v [tématu Wizards](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Vlastní nástroje
 Vlastní nástroje umožňují přidružit nástroj k položce v projektu a spustit tento nástroj při každém uložení souboru. Další informace naleznete [v tématu Vlastní nástroje](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>Nástroje VSSDK
 Sada VSSDK obsahuje sadu nástrojů, které můžete potřebovat pro práci s různými aspekty VSPackages. Další informace naleznete v tématu [VSSDK Utilities](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Použití Instalační služby systému Windows
 V některých případech může být nutné použít Instalační službu systému Windows spíše než Instalační služba VSIX: například bude nutné zapisovat do registru. Informace o použití Instalační služby systému Windows s rozšířeními naleznete [v tématu Instalace balíčků VSPackages With Installer systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

## <a name="help-viewer"></a>Prohlížeč nápovědy
 Do prohlížeče nápovědy můžete integrovat vlastní nápovědu a stránky F1. Další informace naleznete v sadě [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).
