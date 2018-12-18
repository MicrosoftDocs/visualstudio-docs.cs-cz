---
title: V sadě Visual Studio SDK | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e72c5033554310555005de17872ee83110768687
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757039"
---
# <a name="inside-the-visual-studio-sdk"></a>Práce se sadou Visual Studio SDK
Tato část obsahuje podrobné informace o rozšíření sady Visual Studio, včetně architektura sady Visual Studio, součásti, služeb, schémata, nástroje a podobně.

## <a name="extensibility-architecture"></a>Architektura rozšiřitelnosti
 Následující obrázek znázorňuje architekturu rozšíření sady Visual Studio. VSPackages poskytují funkce aplikací, který je sdílen napříč IDE jako služby. Standardní IDE také nabízí širokou škálu služeb, jako například <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, které poskytují přístup k funkci okna IDE.

 ![Obrázek architektury prostředí](../../extensibility/internals/media/environment.gif "prostředí") zobecněn pohled na architekturu Visual Studio

## <a name="vspackages"></a>Balíčky VSPackage
 VSPackages jsou softwarové moduly, které tvoří a rozšíření sady Visual Studio s prvky uživatelského rozhraní, služby, projekty, editory a návrháři. VSPackages jsou centrální architektury jednotek sady Visual Studio. Další informace najdete v tématu [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Shell
 Prostředí sady Visual Studio poskytuje základní funkce a podporovat komunikaci mezi mezi jeho VSPackages a MEF rozšíření komponent. Další informace najdete v tématu [prostředí sady Visual Studio](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Pravidla pro práci s uživatelským prostředím
 Pokud máte v úmyslu návrhu nové funkce pro sadu Visual Studio, byste měli vzít podívejte se na tipy k návrhu a použitelnost těchto pokynů: [Visual Studio prostředí pro práci uživatelů](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="commands"></a>Příkazy
 Příkazy jsou funkce, které provést úkoly, jako je například tisk dokumentu, aktualizovat zobrazení nebo vytvoření nového souboru.

 Když rozšíříte Visual Studio, můžete vytvořit příkazy a zaregistrovat je prostředí sady Visual Studio. Můžete zadat, jak tyto příkazy se zobrazí v integrovaném vývojovém prostředí, například v nabídce nebo na panelu nástrojů. Obvykle vlastního příkazu se zobrazí na **nástroje** nabídek a příkazů pro zobrazení okno nástroje objeví na **ostatní okna** podnabídce **zobrazení** nabídky.

 Při vytváření příkazu, musíte také vytvořit obslužnou rutinu události pro ni. Obslužné rutiny události Určuje, kdy příkaz viditelný nebo povoleno, umožňuje změnit jeho text a zaručuje, že když se aktivuje odpoví příkaz správně. Ve většině případů je IDE zpracovává příkazy pomocí <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní. Příkazy v sadě Visual Studio jsou zpracovávány počínaje kontext nejvnitřnější příkazů, na základě místní výběru a budete pokračovat ve nejkrajnější kontextu, a to na základě globální výběru. Příkazy, které jsou přidány do hlavní nabídky jsou okamžitě k dispozici pro skriptování.

 Další informace najdete v tématu [příkazy, nabídek a panelů nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="menus-and-toolbars"></a>Nabídek a panelů nástrojů
 Nabídek a panelů nástrojů poskytují způsob, jak uživatelům volat příkazy. Nabídky jsou řádky a sloupce příkazy, které se obvykle zobrazují jako jednotlivé text položky v horní části okna nástroje. Dílčích jsou sekundární nabídky, které se zobrazují, když uživatel klikne příkazy, které zahrnují malá šipka. Kontextové nabídky se zobrazí, když uživatel klikne pravým tlačítkem myši některé prvky uživatelského rozhraní. Jsou některé běžné názvy nabídek **soubor**, **upravit**, **zobrazení**, a **okno**. Další informace najdete v tématu [rozšíření nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).

 Panely nástrojů jsou řádky a sloupce tlačítek a jiných ovládacích prvků, jako je například pole se seznamem, seznamy a textová pole. Tlačítka panelu nástrojů obvykle mají ikonu Image, jako jsou ikonou složky pro **otevření souboru** příkaz nebo tiskárny pro **tiskových** příkaz. Všechny prvky panelu nástrojů jsou přidružené příkazy. Při kliknutí na tlačítko panelu nástrojů jeho přidružené příkaz spustí. V případě ovládacího prvku rozevíracího seznamu je přidružen jiný příkaz každou položku v rozevíracím seznamu. Některé ovládací prvky panelu nástrojů, jako je například ovládací prvek typu rozdělovač jsou hybridních. Druhé straně je šipku dolů, který se zobrazí několik příkazů, když po kliknutí na jedné straně ovládací prvek je tlačítka panelu nástrojů.

## <a name="tool-windows"></a>Nástroje systému Windows
 Nástroje systému windows se používají v prostředí IDE pro zobrazení informací. **Sada nástrojů**, **Průzkumníku řešení**, **vlastnosti** okně a **webový prohlížeč** jsou příklady nástroje systému windows.

 Nástroje systému windows obvykle nabízejí různé ovládací prvky, se kterými může uživatel komunikovat. Například **vlastnosti** okno umožňuje uživateli nastavit vlastnosti objektů, které pro konkrétní účel. **Vlastnosti** okno je specializované v tomto smyslu, ale také obecné, protože je možné použít v mnoha různých situacích. Podobně **výstup** okno se specializuje, protože poskytuje textový výstup, ale obecné vzhledem k tomu, že mnoho subsystémy v sadě Visual Studio můžete použít k zajištění výstupu sady Visual Studio uživateli.

 Vezměte v úvahu následující obrázek sady Visual Studio, který obsahuje několik nástroje systému windows.

 ![Snímek obrazovky](../../extensibility/internals/media/t1gui.png "T1gui")

 Některé nástroje Windows jsou ukotven společně v jednom podokně, který zobrazí okno nástroje Průzkumník řešení a skryje jiné nástroje systému windows, ale pak kliknutím na karty dostupné. Obrázek ukazuje dva další nástroje windows **seznam chyb** a **výstup** okně ukotveno společně na jednom podokně.

 Také ukazuje je podokna hlavní dokumentu, které ukazuje několik oken editoru. I když nástroj windows obvykle mají jenom jednu instanci (například může otevřít pouze jeden **Průzkumníku řešení**), editor windows může mít více instancí, z nichž každá používá se k úpravě samostatné dokumentu, ale všechny z nich jsou ukotveny v v podokně stejné. Obrázek ukazuje podokno dokumentu, který má dvě okna editoru, jeden interval návrháře formuláře a okno prohlížeče zobrazující stránku spustit. Kliknutím na karty jsou k dispozici všechny systémy windows v podokně dokumentu, ale okno editor, který obsahuje soubor EditorPane.cs je viditelná a aktivní.

 Když rozšíříte Visual Studio, můžete vytvořit nástroj windows, které umožňují uživatelům se Visual Studio komunikovat s rozšíření. Můžete také vytvořit vlastní editory, které umožňují uživatelům sady Visual Studio úpravám dokumentů. Protože nástroj windows a editory integrují do sady Visual Studio, nemáte programu jejich ukotvení, nebo se zobrazí na kartě správně. Pokud jsou správně registrované v sadě Visual Studio, budou mít automaticky typické funkce nástroje systému windows a windows dokumentu v sadě Visual Studio. Další informace najdete v tématu [rozšíření a přizpůsobení nástrojů Windows](../../extensibility/extending-and-customizing-tool-windows.md).

## <a name="document-windows"></a>Okna dokumentů
 Okna dokumentu je rámcová podřízeného okna okna rozhraní více dokumentů (MDI). Okna dokumentu se obvykle používají k hostování textové editory, editory formuláře (také označované jako Designer) nebo ovládací prvky pro úpravy, ale můžete také uložit jiné typy funkční. **Nový soubor** dialogové okno obsahuje příklady okna dokumentu, které poskytuje Visual Studio.

 Většina editory jsou specifické pro programovací jazyk nebo typ souboru, například stránky HTML, sady rámců, C++ soubory nebo soubory hlaviček. Výběrem šablony, v **nový soubor** dialogové okno, uživatel vytvoří dynamicky okna dokumentu pro editor pro daný typ souboru, který je přidružen šablony. Okna dokumentu se také vytvoří, když uživatel otevře existující soubor.

 Okna dokumentu jsou omezeny na MDI klientské oblasti. Každý okna dokumentu má na kartě nahoře, a pořadí souvisí jiných windows, které může být otevřený v oblasti MDI. Pravým tlačítkem myši na kartu okna dokumentu se zobrazí místní nabídky, který zahrnuje možnosti oblasti MDI rozdělit do několika skupin kartě vodorovně nebo svisle. Rozdělení oblasti MDI umožňuje více souborů, které lze zobrazit najednou. Další informace najdete v tématu [okna dokumentu](../../extensibility/internals/document-windows.md).

## <a name="editors"></a>Editory
 Editoru Visual Studio můžete upravit a použít jej pro vlastní typ obsahu prostřednictvím Managed Extensibility Framework (MEF). V mnoha případech nemusíte vytvářet VSPackage rozšířit editor, ale pokud chcete zahrnout funkce z prostředí (například příkazu nabídky nebo klávesovou zkratku), můžete kombinovat MEF rozšíření s VSPackage.

 Můžete také vytvořit vlastní editor, například pokud chcete číst a zapisovat do databáze, nebo pokud chcete použít návrháře. Můžete také použít externí editoru, jako je například Poznámkový blok nebo Microsoft WordPad. Další informace najdete v tématu [Editor a rozšíření služeb jazyk](../../extensibility/editor-and-language-service-extensions.md).

## <a name="language-services"></a>Jazyk služby
 Pokud chcete editoru Visual Studio pro podporu nového programovací klíčová slova nebo i nové programovací jazyk, vytvoříte služba jazyka. Každá služba jazyka může implementovat určité funkce editor plně, částečně nebo vůbec. V závislosti na tom, jak je nakonfigurovaný můžete zadat služba jazyka zvýraznění syntaxe, odpovídající složené závorce, podporu technologie IntelliSense a další funkce v editoru.

 Jádrem služba jazyka jsou analyzátor a skener. Skener (nebo lexer) rozděluje zdrojového souboru do prvky, které se označují jako tokeny a analyzátor vytvoří vztahy mezi tyto tokeny. Při vytváření služby jazyk, je nutné implementovat analyzátor a skeneru, tak, aby Visual Studio můžete porozumět tokeny a gramatika jazyka. Můžete vytvořit služby jazyk spravované nebo nespravované. Další informace najdete v tématu [rozšíření služby starší verze jazyka](../../extensibility/internals/legacy-language-service-extensibility.md).

## <a name="projects"></a>Projekty
 Projekty v sadě Visual Studio jsou kontejnery, které vývojáři použít k uspořádání a vytvoření zdrojového kódu a další prostředky. Projekty umožňují uspořádat, sestavení, ladění a nasazení zdrojového kódu, odkazuje na webové služby a databáze a dalším prostředkům. VSPackages můžete rozšíření systému projektu sady Visual Studio tím, že poskytuje typy projektů, podtypů projektu a vlastních nástrojů.

 Projekty může také shromáždit do řešení, které je skupina jednoho nebo více projektů, které vzájemně spolupracují a vytvoření aplikace. Projekt a stavové informace, které se vztahují k řešení uloženo v dva soubory řešení, soubor založený na textu řešení (.sln) a soubor binární řešení uživatele možnost (.suo). Tyto soubory jsou podobné soubory skupiny (.vbg), které byly používány v dřívějších verzích [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], a pracovní prostor (.dsw) a uživatelské možnosti (.opt) soubory, které byly používány v dřívějších verzích [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].

 Další informace najdete v tématu [projekty](../../extensibility/internals/projects.md) a [řešení](../../extensibility/internals/solutions.md).

## <a name="project-and-item-templates"></a>Šablony projektů a položek
 Visual Studio obsahuje předem definovaných šablon projektu a šablony položek projektu. Můžete také vytvářet vlastní šablony nebo získat šablony od komunity a pak je integrovat do sady Visual Studio. [Galerie kódů MSDN](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio) je místo, kde přejděte šablon a rozšíření.

 Šablony obsahují projektu strukturu a základní soubory, které jsou nutné k vytvoření konkrétní typ aplikace, ovládací prvek, knihovny nebo třídy. Když chcete k vývoji softwaru, který vypadá takto: jednu z šablon, vytvořit projekt, který je založený na šabloně a potom upravte soubory v tomto projektu.

> [!NOTE]
> Tato architektura šablony není podporován pro [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projekty.

 Další informace najdete v tématu [přidání projektů a šablon položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="properties-and-options"></a>Vlastnosti a možnosti
 **Vlastnosti** okno zobrazuje vlastnosti jeden nebo více vybraných položek: [vlastnosti rozšíření](../../extensibility/internals/extending-properties.md) možnosti stránky obsahují sadu možností, které se týkají jednotlivých součástí, například programovací jazyk nebo VSPackage: [možnosti a možnosti stránky](../../extensibility/internals/options-and-options-pages.md). Nastavení jsou obecně uživatelského rozhraní související funkce, které se dají importovat a exportovat: [podpora pro uživatelských nastavení](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Služby Visual Studio
 Služba poskytuje konkrétní sadu rozhraní pro součásti, které využívají. Visual Studio poskytuje sadu služeb, které mohou být využívána žádné součásti, včetně rozšíření. Například služby Visual Studio umožňují nástroj windows můžete zobrazit nebo skryté dynamicky, povolit přístup k nápovědě, stavový řádek nebo události uživatelského rozhraní. Editoru Visual Studio také poskytuje služby, které můžete importovat pomocí editoru rozšíření. Další informace najdete v tématu [pomocí a poskytování služeb](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>Ladicí program
 Ladicí program je uživatelské rozhraní pro součásti ladění konkrétní jazyk. Pokud jste vytvořili novou službu jazyka, musíte vytvořit konkrétní ladění modul napojit v k ladicího programu. Další informace najdete v tématu [rozšiřitelnost ladicí program Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="source-control"></a>Správa zdrojového kódu
 Informace o implementaci modul plug-in správy zdroje nebo VSPackage najdete v tématu [správy zdrojového kódu](../../extensibility/internals/source-control.md).

## <a name="wizards"></a>Průvodci
 Průvodce lze vytvořit ve spojení s nový typ projektu, tak, aby průvodce může pomoci uživatelům provést správné rozhodnutí o při vytváření nového projektu daného typu. Další informace najdete v tématu [průvodců](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Vlastní nástroje
 Vlastní nástroje umožňují nástroj přidružit položku v projektu a spusťte tento nástroj vždy, když se soubor uložit. Další informace najdete v tématu [vlastní nástroje](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>Nástroje VSSDK
 VSSDK obsahuje sadu nástrojů, které byste mohli potřebovat za účelem práce s různých aspektů VSPackages. Další informace najdete v tématu [VSSDK nástroje](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Pomocí Instalační služby systému Windows
 V některých případech budete muset použít instalační služby systému Windows než instalační program VSIX: například musíte zapsat do registru. Informace o použití Instalační služby systému Windows s rozšíření najdete v tématu [instalaci VSPackages pomocí Instalační služby systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

## <a name="help-viewer"></a>Prohlížeč nápovědy
 Vlastní Nápověda a F1 stránky můžete integrovat do prohlížeče nápovědy. Další informace najdete v tématu [Microsoft pomůže prohlížeč SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).