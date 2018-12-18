---
title: V sadě Visual Studio SDK | Dokumentace Microsoftu
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
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b7a7642d8cd33d53bb7d6d2a472a0690713e25d3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795827"
---
# <a name="inside-the-visual-studio-sdk"></a>Práce se sadou Visual Studio SDK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tato část obsahuje podrobné informace o rozšíření sady Visual Studio, včetně architektury sady Visual Studio, komponenty, služby, schémata, nástroje a podobně.  
  
## <a name="extensibility-architecture"></a>Architektura rozšíření  
 Následující obrázek znázorňuje architekturu rozšiřitelnost sady Visual Studio. Rozšíření VSPackages poskytují funkčnost aplikace, který je sdílen napříč IDE rozhraním jako služby. Standardní prostředí IDE, jako také nabízí celou řadu služeb, <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, které poskytují přístup k oddílová funkce integrovaného vývojového prostředí.  
  
 ![Obrázek architektury prostředí](../../extensibility/internals/media/environment.gif "prostředí")  
Zobecněný zobrazení architektury v sadě Visual Studio  
  
## <a name="vspackages"></a>Balíčky VSPackage  
 Rozšíření VSPackages jsou softwarové moduly, které společně tvoří a rozšíření sady Visual Studio s prvky uživatelského rozhraní, služby, projekty, editory a návrháře. Rozšíření VSPackages jsou centrální architektury částí sady Visual Studio. Další informace najdete v tématu [rozšíření VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="visual-studio-shell"></a>Visual Studio Shell  
 Prostředí sady Visual Studio poskytuje základní funkce a podporují různé komunikaci mezi jeho součást rozšíření VSPackages a rozhraní MEF. Další informace najdete v tématu [prostředí sady Visual Studio](../../extensibility/internals/visual-studio-shell.md).  
  
## <a name="user-experience-guidelines"></a>Pravidla pro práci s uživatelským prostředím  
 Pokud máte v úmyslu návrh nových funkcí pro Visual Studio, byste měli podniknout podívejte se na tyto pokyny pro návrh a použitelnost tipy: [Visual Studio zkušenosti uživatelů](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="commands"></a>Příkazy  
 Příkazy jsou funkce, které provádět úlohy, jako je například tisk dokumentu, aktualizuje zobrazení nebo vytvoření nového souboru.  
  
 Když rozšíříte sady Visual Studio, můžete vytvořit příkazy a zaregistrovat je v rámci prostředí sady Visual Studio. Můžete určit, jak tyto příkazy se zobrazí v integrovaném vývojovém prostředí, například na nabídku nebo panel nástrojů. Obvykle se zobrazí na vlastní příkaz **nástroje** nabídky a příkaz pro zobrazování okna nástroje by se zobrazí na **ostatní Windows** podnabídce **zobrazení** nabídky.  
  
 Při vytváření příkazu musíte také vytvořit obslužnou rutinu události pro něj. Obslužná rutina události Určuje, kdy příkaz viditelné nebo povoleno, umožňuje měnit jeho textu a zaručuje, že příkaz náležitě reaguje při aktivaci. Ve většině případů, rozhraní IDE zpracovává příkazy pomocí <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní. Příkazy v sadě Visual Studio jsou zpracovány počínaje kontext nejvnitřnější příkazů, na základě výběru v místní a pokračuje na vnější kontext na základě výběru v globální. Příkazy, které jsou přidány do hlavní nabídky jsou okamžitě k dispozici pro skriptování.  
  
 Další informace najdete v tématu [příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="menus-and-toolbars"></a>Nabídky a panely nástrojů  
 Nabídky a panely nástrojů poskytují způsob, jak uživatelům umožnit vyvolání příkazů. Nabídky jsou řádky nebo sloupce příkazů, které se obvykle zobrazují jako jednotlivé textové položky v horní části panelu nástrojů. Podnabídek jsou sekundární nabídky, které se zobrazí po kliknutí příkazy, které zahrnují malou šipku. Kontextové nabídky se zobrazí, když uživatel klepne pravým tlačítkem myši některé prvky uživatelského rozhraní. Jsou některé běžné názvy nabídek **souboru**, **upravit**, **zobrazení**, a **okno**. Další informace najdete v tématu [rozšiřování nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).  
  
 Panely nástrojů jsou řádky nebo sloupce tlačítka a další ovládací prvky, jako je například pole se seznamem, pole se seznamem a textová pole. Tlačítka panelu nástrojů obvykle obsahují obrázky ikon, jako je například ikonu složky pro **otevřít soubor** příkaz nebo tiskárny pro **tisk** příkazu. Všechny prvky panel nástrojů jsou spojeny s příkazy. Po kliknutí na tlačítko panelu nástrojů, spustí jeho přidružený příkaz. V případě ovládací prvek rozevírací seznam je přidružen k jinému příkazu každou položku v rozevíracím seznamu. Některé ovládací prvky panelu nástrojů, jako je například ovládací prvek splitter, jsou hybridních. Druhé straně je šipku dolů, která zobrazí několik příkazů, když dojde ke kliknutí na jedné straně ovládacího prvku je tlačítka panelu nástrojů.  
  
## <a name="tool-windows"></a>Nástroj Windows  
 Nástroje systému windows jsou v integrovaném vývojovém prostředí slouží k zobrazení informací. **Panel nástrojů**, **Průzkumníka řešení**, **vlastnosti** okně a **webový prohlížeč** jsou příklady oken nástrojů.  
  
 Okna nástrojů obvykle nabízejí různé ovládací prvky, se kterými se uživatelé můžou komunikovat. Například **vlastnosti** okno umožňuje uživateli nastavit vlastnosti objektů, které pro konkrétní účel. **Vlastnosti** okna je v tomto smyslu specializovaná, ale také obecné, protože je možné v mnoha různých situacích. Podobně **výstup** okna je specializovat, protože poskytuje textový výstup, ale Obecné, protože mnoho subsystémy v sadě Visual Studio můžete použít k poskytnutí výstup pro uživatele sady Visual Studio.  
  
 Vezměte v úvahu následující obrázek sady Visual Studio, který obsahuje několika okny nástrojů.  
  
 ![Snímek obrazovky](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 Některá okna nástrojů jsou ukotveny na jedno podokno, které zobrazí panel nástrojů Průzkumník řešení a skryje jiné nástroje systému windows, ale zpřístupňuje je kliknutím na karty. Na obrázku ukazuje dvě ostatním oknům nástrojů **seznam chyb** a **výstup** okno ukotvených dohromady na jedno podokno.  
  
 Navíc zobrazí se podokno hlavní dokument, který ukazuje několik oken editoru. I když obvykle mají pouze jednu instanci okna nástrojů (například lze otevřít pouze jeden **Průzkumníka řešení**), editor windows může mít více instancí, z nichž každý se používá k úpravě samostatné dokumentu, ale všechny z nich jsou ukotveny v podokno. Obrázek ukazuje panel dokumentu, který má dvě okna editoru, jedno okno návrháře formulářů a okno prohlížeče zobrazující úvodní stránky. Kliknutím na karty jsou k dispozici všechna okna v podokně dokumentu, ale je okno editoru obsahující soubor EditorPane.cs viditelné a aktivní.  
  
 Při rozšíření sady Visual Studio můžete vytvořit nástroj pro windows, které umožní uživatelům aplikace Visual Studio pracovat s rozšíření. Můžete také vytvořit vlastní editorů, které umožní uživatelům aplikace Visual Studio, úpravy dokumentů. Protože oken nástrojů a editory, bude se integrovat do sady Visual Studio, nemají programovat ukotvit nebo se zobrazí na kartě správně. Pokud jsou správně registrovány v sadě Visual Studio, mají se automaticky typické funkce nástrojů a oken dokumentu v sadě Visual Studio. Další informace najdete v tématu [rozšíření a přizpůsobení nástrojů Windows](../../extensibility/extending-and-customizing-tool-windows.md).  
  
## <a name="document-windows"></a>Okna dokumentů  
 Okno dokumentu je orámované podřízeného okna okna rozhraní více dokumentů (MDI). Okna dokumentu se obvykle používají k hostování textových editorů, editory formuláře (označované také jako návrháři) nebo ovládací prvky pro úpravy, ale mohli hostovat i jiné typy funkční. **Nový soubor** dialogové okno obsahuje příklady okna dokumentu, která poskytuje sada Visual Studio.  
  
 Většina editory jsou specifické pro programovací jazyk nebo typ souboru, například stránky HTML, sad rámců, C++ soubory nebo soubory hlaviček. Výběrem šablony v **nový soubor** dialogovém okně, uživatel dynamicky vytvoří okno dokumentu v editoru pro typ souboru, která je přidružená k šabloně. Okno dokumentu se také vytvoří, když uživatel otevře existující soubor.  
  
 Okna dokumentů jsou omezené na oblasti klienta MDI. Každé okno dokumentu je na kartě v horní části, a pořadí ovládacích prvků je propojený s ostatní okna, které je možná otevřená v oblasti MDI. Pravým tlačítkem myši na kartě okna dokumentu zobrazí místní nabídku, která obsahuje možnosti, které oblasti MDI rozdělit do několika skupin vodorovné nebo svislé kartě. Rozdělení oblasti MDI umožňuje více souborů, které lze zobrazit ve stejnou dobu. Další informace najdete v tématu [dokumentu Windows](../../extensibility/internals/document-windows.md).  
  
## <a name="editors"></a>Editory  
 Editor sady Visual Studio můžete přizpůsobit a používat ho pro vlastní typ obsahu prostřednictvím Managed Extensibility Framework (MEF). V mnoha případech nemusíte vytvářet VSPackage pro rozšíření editoru, ale pokud chcete zahrnout funkce v prostředí (například příkaz nabídky nebo klávesové zkratky), můžete kombinovat MEF rozšíření pomocí VSPackage.  
  
 Můžete také vytvořit vlastní editor, například pokud chcete číst a zapisovat do databáze, nebo pokud budete chtít použít návrháře. Můžete také použít externí editor jako je například Poznámkový blok nebo Microsoft WordPad. Další informace najdete v tématu [Editor a rozšíření služeb jazyka](../../extensibility/editor-and-language-service-extensions.md).  
  
## <a name="language-services"></a>Jazykové služby  
 Pokud chcete editoru sady Visual Studio pro podporu nových programovací klíčových slov nebo dokonce i nový programovací jazyk, vytvoříte službu jazyka. Každá služba jazyka může implementovat určité funkce editoru plně, částečně nebo vůbec ne. V závislosti na tom, jak je nakonfigurovaný může poskytnout službě jazyka zvýrazňování syntaxe, párování složených závorek, podporu technologie IntelliSense a dalších funkcích v editoru.  
  
 V srdci služba jazyka je analyzátor a skener. Skener (nebo lexeru) rozdělí do zdrojového souboru na prvky, které jsou označovány jako tokeny a analyzátor vytvoří vztahy mezi těchto tokenů. Při vytváření služby jazyka, musíte implementovat analyzátor a skener tak, aby Visual Studio by rozuměla tokeny a gramatiku jazyka. Můžete vytvořit spravované nebo nespravované jazykové služby. Další informace najdete v tématu [rozšíření služeb starší verze jazyka](../../extensibility/internals/legacy-language-service-extensibility.md).  
  
## <a name="projects"></a>Projekty  
 Projekty v sadě Visual Studio, jsou kontejnery, které vývojáři použít k uspořádání a vytvoření zdrojového kódu a další prostředky. Projekty umožňují organizovat, vytváření, ladění a nasazení zdrojového kódu, odkazy na webové služby a databáze a další prostředky. Rozšíření VSPackages můžete rozšířit systém projektu sady Visual Studio poskytnutím typy projektů, podtypů projektů a vlastních nástrojů.  
  
 Projekty mohou také shromáždit do jediného řešení, což je seskupení jednoho nebo více projektů, které vzájemně spolupracují na vytvoření aplikace. Projekt a stavové informace, které se vztahují k řešení je uložené v dva soubory řešení, soubor založený na textu řešení (.sln) a soubor binární řešení uživatelské možnosti (.suo). Tyto soubory jsou podobné soubory skupiny (.vbg), které byly použity v dřívějších verzích [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], a pracovní prostor (.dsw) a uživatelské možnosti (.opt) soubory, které byly použity v dřívějších verzích [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].  
  
 Další informace najdete v tématu [projekty](../../extensibility/internals/projects.md) a [řešení](../../extensibility/internals/solutions.md).  
  
## <a name="project-and-item-templates"></a>Šablony projektů a položek  
 Visual Studio obsahuje šablony projektů předdefinované a šablony položek projektu. Můžete také vytvořit vlastní šablony nebo získání šablony z komunity a integrovat je do sady Visual Studio. [Galerie kódů MSDN](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio) je místo, kde lze získat šablony a rozšíření.  
  
 Šablony obsahují projekt strukturu a základní soubory, které jsou nutné k vytvoření určitého druhu aplikace, ovládací prvek, knihovny nebo třídy. Pokud chcete k vývoji softwaru, který se podobá některou ze šablon, vytvořit projekt, který je založen na šabloně a potom upravte soubory v daném projektu.  
  
> [!NOTE]
>  Tato architektura šablony není podporován pro [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projekty. Informace o tom, jak vytvořit [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] šablony projektů, naleznete v tématu [návrhu průvodce](http://msdn.microsoft.com/library/a7c0be7e-9297-4fed-83e3-5645c896d56b).  
  
 Další informace najdete v tématu [přidání projektů a šablon položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="properties-and-options"></a>Vlastnosti a možnosti  
 **Vlastnosti** okně zobrazí vlastnosti jednoho nebo více vybraných položek: [vlastnosti rozšíření](../../extensibility/internals/extending-properties.md) možnosti stránky obsahují sadu možností, které se týkají konkrétní součástí, například programovací jazyk nebo VSPackage: [možnosti a stránky možnosti](../../extensibility/internals/options-and-options-pages.md). Nastavení jsou obecně související s Uživatelským rozhraním funkce, které můžete importovat a exportovat: [podpora pro uživatelská nastavení](../../extensibility/internals/support-for-user-settings.md).  
  
## <a name="visual-studio-services"></a>Služby Visual Studio  
 Služba obsahuje konkrétní sadu rozhraní pro součásti využívají. Visual Studio poskytuje sada služeb, které mohou využívat všechny komponenty, včetně rozšíření. Například služby Visual Studio umožňují okna nástrojů zobrazený nebo skrytý dynamicky, povolení přístupu k nápovědě, stavový řádek nebo události uživatelského rozhraní. Editor sady Visual Studio také poskytuje služby, které lze importovat rozšířeními editoru. Další informace najdete v tématu [Using a poskytování služeb](../../extensibility/using-and-providing-services.md).  
  
## <a name="debugger"></a>Ladicí program  
 Ladicí program je uživatelské rozhraní pro komponenty ladění specifické pro jazyk. Pokud nová jazyková služba, kterou jste vytvořili, musíte vytvořit konkrétní ladicí modul k připojení k ladicímu programu v. Další informace najdete v tématu [rozšiřitelnosti ladicího programu sady Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="source-control"></a>Správa zdrojového kódu  
 Informace o implementaci modulu plug-in správy zdrojového kódu nebo balíčku VSPackage najdete v tématu [správy zdrojových kódů](../../extensibility/internals/source-control.md).  
  
## <a name="wizards"></a>Průvodci  
 Průvodce lze vytvořit ve spojení s novým typem projektu, tak, aby průvodce může pomoci uživatelům dělat správná rozhodnutí při vytváření nového projektu daného typu. Další informace najdete v tématu [průvodců](../../extensibility/internals/wizards.md).  
  
## <a name="custom-tools"></a>Vlastní nástroje  
 Vlastní nástroje vám umožní přidružit nástroj položky v projektu a spusťte tento nástroj pokaždé, když je soubor uložen. Další informace najdete v tématu [vlastní nástroje](../../extensibility/internals/custom-tools.md).  
  
## <a name="vssdk-utilities"></a>Nástroje VSSDK  
 VSSDK zahrnuje sadu nástrojů, které je nutné, abyste mohli pracovat s různými aspekty rozšíření VSPackages. Další informace najdete v tématu [nástroje VSSDK](../../extensibility/internals/vssdk-utilities.md).  
  
## <a name="using-windows-installer"></a>Pomocí Instalační služby systému Windows  
 V některých případech budete muset použít instalační služby systému Windows než instalátor VSIX: například může potřebovat k zápisu do registru. Informace o použití Instalační služby systému Windows se rozšíření najdete v tématu [instalace rozšíření VSPackages s Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
## <a name="help-viewer"></a>Aplikaci Help Viewer  
 Vlastní Nápověda a F1 stránky můžete integrovat do aplikace Help Viewer. Další informace najdete v tématu [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).

