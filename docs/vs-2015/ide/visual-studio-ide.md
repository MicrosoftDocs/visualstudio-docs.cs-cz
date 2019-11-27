---
title: Visual Studio 2015 | Dokumentace Microsoftu
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
ms.assetid: 772b6cf4-cee5-42d0-bc18-b4eb07e22ff0
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3780e0ee5cf6bffb1a749b17d868445fbda38b13
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296925"
---
# <a name="visual-studio-ide"></a>Visual Studio – sada IDE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Microsoft Visual Studio 2015 je sada nástrojů pro vytváření softwaru, z fáze plánování prostřednictvím uživatelského rozhraní návrh, kódování, testování, ladění, analýza kvality kódu a výkonu, nasazení pro zákazníky a shromažďování telemetrických dat o využití. Tyto nástroje jsou navrženy pro jako možné a jsou všechny vystavené prostřednictvím Visual Studio integrované vývojové prostředí (IDE) bezproblémově fungovat.

Visual Studio slouží k vytvoření mnoha typech aplikací, od jednoduchého úložiště aplikací a her pro mobilní klienty na velké a komplexní systémy, které podniky napájení a dat centra. Můžete vytvořit:

- Aplikace a hry pro Windows, nejen, ale také zařízení s Androidem a iOS.

- Weby a webové služby založené na technologii ASP.NET, JQuery, AngularJS a dalších oblíbených architektur.

- Aplikace pro zařízení nejrůznější Azure, Office, Sharepoint, Hololens, Kinect a Internet of Things pojmenovat jen pár příkladů a platformy.

- Hry a aplikace náročné na grafiku pro širokou škálu zařízení Windows, včetně Xbox, pomocí rozhraní DirectX.

Visual Studio ve výchozím nastavení poskytuje podporu pro C#, C a C++, JavaScript, F#a Visual Basic. Sada Visual Studio funguje a integruje se s aplikacemi třetích stran, jako je Unity, prostřednictvím rozšíření [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) a Apache Cordova prostřednictvím [Visual Studio Tools pro Apache Cordova](https://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42). Můžete rozšířit Visual Studio sami tak, že vytvoříte vlastní nástroje, které se prováděly specializované úkoly.

Pokud jste ještě nepoužili Visual Studio, Seznamte se se základy [Začínáme s vývojem v prostředí Visual Studio](../ide/get-started-developing-with-visual-studio.md) a návody.

Pokud se chcete dozvědět o nových funkcích sady Visual Studio 2015, přečtěte si téma [novinky v aplikaci Visual studio 2015](../what-s-new-in-visual-studio-2015.md).

## <a name="visual-studio-setup"></a>Instalace sady Visual Studio
 Můžete zjistit, která edice sady Visual Studio je pro vás vhodná v [edicích sady Visual Studio](https://visualstudio.microsoft.com/vs/).

 Můžete nainstalovat Visual Studio 2015 stažením ze sady [Visual Studio downloads](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx). Pokud potřebujete o instalačním procesu získat další informace, přečtěte si téma [instalace sady Visual Studio 2015](../install/install-visual-studio-2015.md).

## <a name="ide-basics"></a>Základní informace o integrovaném vývojovém prostředí
 Následující obrázek ukazuje IDE sady Visual Studio s projektem open a navigace v souborech projektu v okně Průzkumník řešení a okno Průzkumníku týmových projektů pro navigaci zdrojový ovládací prvek a sledování pracovních položek. Funkce v záhlaví okna, která jsou vyznačeny jsou vysvětleny níže podrobněji.

 ![Integrované vývojové prostředí sady Visual Studio](../ide/media/visualstudioide.png "VisualStudioIDE")

### <a name="signing-in"></a>Přihlášení
 Při prvním spuštění aplikace Visual Studio, můžete přihlásit pomocí účtu Microsoft nebo pracovního nebo školního účtu. Probíhá přihlašování umožňuje synchronizaci nastavení, například rozložení oken na různých zařízeních a automaticky se připojovat ke službám, které můžete potřebovat, jako je Visual Studio Team Services a předplatných Azure. Pokud máte licenci na základě předplatného, budete potřebovat k přihlášení k sadě Visual Studio v pravidelných intervalech abychom zachovali aktuální token vaší licence. Pokud máte licenci kód product key, není nutné se přihlásit, ale to tak je to více vhodné pro připojení k Visual Studio Team Services a svoje účty pomocí služby Azure, Office 365, Salesforce.com. Další informace najdete v tématu [přihlášení do sady Visual Studio](../ide/signing-in-to-visual-studio.md).

 Pokud máte víc účtů Visual Studio Team Services, Azure účty ani předplatná MSDN, můžete propojit v rámci účtů s jednotné přihlašování a přístup k prostředkům a službám. Další informace najdete v tématu [práce s několika uživatelskými účty](../ide/work-with-multiple-user-accounts.md).

### <a name="staying-up-to-date"></a>Udržování
 Na ikonu oznámení v pravém horním rohu záhlaví zjistíte, když jsou k dispozici pro sadu Visual Studio aktualizace nebo příslušné součásti, které jste si nainstalovali. Můžete zvolit, jestli se má zrušit nebo s nimi pracovat tato oznámení. Další informace najdete v tématu [oznámení sady Visual Studio](../ide/visual-studio-notifications.md).

### <a name="finding-things-and-getting-help"></a>Hledání věci a získání nápovědy
 Okno [Snadné spuštění](../ide/reference/quick-launch-environment-options-dialog-box.md) zobrazené níže je rychlý způsob, jak najít příkazy, nástroje, funkce a tak dále v aplikaci Visual Studio, když neznáte klávesovou zkratku nebo umístění nabídky. Stačí zadat, co hledáte a snadné spuštění získáte odkaz na něj.

 ![Výsledky snadného spuštění pro nový projekt](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

 MSDN je na webu společnosti Microsoft technickou dokumentaci; tuto stránku na webu MSDN při čtení hned teď! V aplikaci Visual Studio můžete stisknutím klávesy **F1** přejít na stránku Nápověda MSDN pro aktivní okno. V editoru kódu můžete také stisknutím klávesy **F1** přejít na stránku Nápověda MSDN pro rozhraní API nebo klíčové slovo na aktuální pozici blikajícího kurzoru. Například v C# souboru umístěte blikající kurzor někam do nebo jen na konci deklarace `System.String` a stisknutím klávesy **F1** přejděte na stránku Nápověda MSDN pro <xref:System.String>.

### <a name="giving-feedback"></a>Poskytuje zpětnou vazbu
 Je snadné sdělte nám svůj názor na Visual Studio pokaždé, když se vám líbí. Klikněte na ikonu zpětné vazby v záhlaví vedle **Rychlé spuštění** a potom klikněte na **ohlásit problém** nebo **Poskytněte návrh**. Předběžné verze verzí sady Visual Studio mají také hodnotu **Ohodnotit tuto možnost produktu** . Podívejte se na tyto komentáře jsme využít k vylepšení produktu. Další informace najdete v tématu [o komunikaci s námi](../ide/talk-to-us.md).

### <a name="personalizing-the-ide"></a>Přizpůsobení integrovaného vývojového prostředí
 Můžete upravit rozložení okna podle stylu vývoje. Můžete ukotvit, float nebo jakékoli okno skrýt v okamžiku, a také můžete spustit v editoru v režimu celé obrazovky. Můžete vytvořit a uložit několik vlastní rozložení oken, které zobrazují pouze systému windows, které potřebujete pro konkrétní kontexty. Můžete například vytvořit rozložení celou obrazovku tak, aby všechno, co se zobrazí editoru kódu. A můžete vytvořit různá rozložení pro ladění a operace týmu. Další informace najdete v tématu [přizpůsobení rozložení oken](../ide/customizing-window-layouts-in-visual-studio.md).

 Můžete přizpůsobit mnoha dalšími způsoby sady Visual Studio a roaming nastavení, pokud pracujete ve více počítačích. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí](../ide/personalizing-the-visual-studio-ide.md).

 Existují klávesové zkratky pro téměř vše, co a si můžete také přizpůsobit. Pokud chcete vytvořit nové klávesové zkratky, zadejte "Klávesnici" Snadné spuštění otevřete dialogové okno klávesnice. Odtud můžete stisknutím klávesy F1 přejděte na stránku nápovědy na webu MSDN, pokud potřebujete další informace o možnostech. Další informace naleznete v tématu [výchozí klávesové zkratky v aplikaci Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="connecting-to-visual-studio-team-services-and-team-foundation-server"></a>Připojení k sadě Visual Studio Team Services a Team Foundation Server
 Visual Studio Team Services (VSTS) je Cloudová služba pro hostování softwarových projektů a povolení spolupráci v týmech. VSTS podporuje systémy Gitu a Team Foundation Source Control, jakož i vývojové metodologie Scrum a Agile a CMMI. Team Foundation verze ovládacího prvku (TFVC) používá jeden centralizované serverové úložiště ke sledování a verze souborů. Místní změny se vždycky změnami do centrálního serveru, kde můžou další vývojáři získat poslední změny. Team Foundation Server (TFS) 2015 je Centrum správy životního cyklu aplikace pro sadu Visual Studio. Umožňuje všem uživatelům zapojené do procesu vývoje se zúčastnit prostřednictvím jediného řešení. TFS je užitečné při správě heterogenních týmům a projektům, příliš.

 Pokud máte účet služby Visual Studio Team Services nebo Team Foundation Server v síti, můžete k němu připojit přes okno Průzkumníku týmových projektů. Z tohoto okna můžete zkontrolovat kód do nebo ze správy zdrojového kódu, správě pracovních položek, spusťte sestavení a přístup týmové místnosti a pracovní prostory. Team Explorer můžete otevřít z **panelu snadného spuštění** nebo v hlavní nabídce ze **zobrazení &#124; Team Explorer** nebo z **týmu &#124; spravovat připojení**.  Další informace o Visual Studio Team Services najdete v tématu [www.VisualStudio.com](https://www.visualstudio.com/). Další informace o Team Foundation Server najdete v tématu [Team Foundation Server](https://www.visualstudio.com/products/tfs-overview-vs).

 V podokně Průzkumník týmových projektů pro řešení, které je hostovaná ve VSTS na následujícím obrázku:

 ![Team Explorer sady Visual Studio](../ide/media/vs2015-teamexplorer.png "VS2015_TeamExplorer")

## <a name="creating-solutions-and-projects"></a>Vytváření řešení a projektů
 I když pomocí sady Visual Studio můžete procházet jednotlivé soubory kódu, častěji budete pracovat v *projektu*. Projekt sady Visual Studio je kolekce souborů a prostředků, které jsou kompilovány do jednoho binárního spustitelného souboru pro aplikace (například .exe, knihovny DLL nebo appx). Pro moduly websites – technologie ASP.NET není vytvořen žádný spustitelný soubor a projekt obsahuje pouze HTML, JavaScript soubory a obrázky. Vzhledem k tomu, že někdy je potřeba vytvořit několik souborů nebo weby, které úzce souvisejí, Visual Studio obsahuje koncepci řešení, které může obsahovat více projekty nebo weby. Když vytvoříte projekt, vytvoříte projekt v řešení a můžete přidat další projekty do řešení později potřebujete. Například pokud máte projekt knihovny DLL, je přidání .exe projektu do řešení, která načte a zpracuje knihovny DLL.

 *Šablona projektu* je kolekce předem vyplněných souborů kódu a nastavení konfigurace, která vám pomohou nastavit rychlé vytvoření konkrétního typu aplikace. Visual Studio přinášejí mnoho šablon projektu lze vybírat, a pokud žádná z výchozí šablony pro vás nejvhodnější, můžete vytvořit vlastní. Po vytvoření projektu pomocí šablony, můžete začít psát vlastní kód v ní, buď v souborech k dispozici nebo nové soubory, které přidáte. Další informace najdete v tématu [řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md). Na následujícím obrázku je dialogové okno Nový projekt pomocí šablony projektu, které jsou k dispozici pro aplikace ASP.NET.

 ![Dialogové okno Nový projekt sady Visual Studio](../ide/media/vs2015-newprojectdialog.png "VS2015_NewProjectDialog")

## <a name="designing-the-user-interface"></a>Návrh uživatelského rozhraní
 Návrhář je intuitivní nástroj, který vám umožní vytvářet uživatelské rozhraní bez psaní kódu. Ovládací prvky uživatelského rozhraní, jako jsou seznamy, kalendáře a tlačítka, lze přetáhnout z okna [Sada nástrojů](../ide/reference/toolbox.md) na návrhovou plochu, která představuje okno nebo dialogové okno. Můžete změnit velikost a uspořádání prvků bez psaní kódu. Návrháři jsou uvedené pro jakýkoli typ projektu, který má uživatelské rozhraní.

 Pokud má váš projekt na základě XAML uživatelské rozhraní, je výchozí návrháře Blendu for Visual Studio, nástroj sofistikované grafiky, která bezproblémově pracuje s aplikací Visual Studio.

 ![Panel](../ide/media/b5-artboard.png "b5_artboard")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Zobrazení Návrh** Zobrazí vizuální návrh dokumentu. V tomto zobrazení můžete kreslení nebo úpravě objektů na návrhové ploše.|
|![](../designers/media/b1-2.png "B1_2")|**Popis cesty** Rychle se přesouvá mezi režimem úprav šablony, režimem úprav stylu a rozsahem úprav objektů pro vybraný objekt.|
|![](../designers/media/b1-3.png "B1_3")|**Zvětšení** Slouží k přiblížení návrhové plochy nebo objektů na návrhové ploše.|
|![](../designers/media/b1-4.png "B1_4")|**Ovládací prvky návrhové plochy** Pomocí těchto ovládacích prvků (**zobrazení mřížky**pro přichycení, **přichycení k** mřížce a **Zapnutí nebo vypnutí přichycení do zarovnávacím čárám**) nastavte možnosti přichycení. Přichycení je užitečné pro zarovnání objektů do sebe navzájem a rovnoměrně rozmístěné řádků na návrhové ploše.|
|![](../designers/media/b1-5.png "B1_5")|**Editor kódu** Upravte kód XAML, C# C++ nebo Visual Basic kód ručně v editoru kódu.|

 Další informace naleznete v tématu [navrhování XAML v aplikaci Visual Studio a Blend pro Visual Studio](../designers/designing-xaml-in-visual-studio.md).

## <a name="writing-navigating-and-understanding-code"></a>Vytváření, procházení a porozumění kódu
 Pokud jste vývojář, je okno editoru, bude pravděpodobně strávíte tady většinu svého času. Visual Studio obsahuje editory pro C#, C++, Visual Basic, JavaScript, XML, HTML, CSS, a F#, a třetích stran nabízejí modulu plug-in editory (a kompilátory) pro mnoho dalších jazyků.

 Jednotlivé soubory v textovém editoru můžete upravit kliknutím na **soubor &#124; &#124; otevřít soubor.** Chcete-li upravit soubory v otevřeném projektu, klikněte na název souboru v Průzkumníku řešení. Obarvené kódu a barevné schéma můžete přizpůsobit tak, že zadáte "Barvy" Snadné spuštění. Máte spoustu textového editoru s kartami windows otevřete najednou. Každé okno můžete rozdělit nezávisle na sobě. Do textového editoru můžete také spustit v celoobrazovkovém režimu.

 ![GreetingsConsoleApp. cpp v editoru kódu](../ide/media/c-ide-editorlinenumberswordwrapon.png "IDE_EditorLineNumbersWordWrapOn c++")

 Textový editor, je vysoce interaktivní (Pokud chcete, aby se) s mnoha produktivitu funkcí, které vám pomůžou pište lepší kód rychleji. Funkce se liší podle jazyka a není nutné použít některý z nich (typu "Editor" v Snadné spuštění) k zapnutí nebo vypnutí funkce: některé běžné pro zvýšení produktivity jsou:

1. [Refaktoring](../ide/refactoring-in-visual-studio.md) zahrnuje operace, jako je například inteligentní přejmenování proměnných, přesunutí vybraných řádků kódu do samostatné funkce, přesunutí kódu do jiných umístění, parametry funkcí redordering a další.

2. *IntelliSense* je zastřešující termín pro sadu oblíbených funkcí, které zobrazují informace o typu kódu přímo v editoru a v některých případech zápis malých bitů kódu za vás. Je to jako mít základní dokumentaci vložené v editoru, což vám ušetří nebudou muset vyhledat informace o typu v okně samostatného nápovědy. Funkce technologie IntelliSense se liší podle jazyka. Další informace naleznete v tématu [Visual C# IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md), [Visual Basic specifické pro technologii IntelliSense](../ide/visual-basic-specific-intellisense.md). Některé funkce technologie IntelliSense při práci na následujícím obrázku:

    ![Seznam členů sady Visual Studio](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")

3. **Vlnovky** upozorňují na chyby nebo potenciální problémy v kódu v reálném čase při psaní, což vám umožní je okamžitě opravit bez čekání na zjištění chyby během kompilace nebo doby běhu. Pokud najedete myší vlnovka, zobrazí se další informace o této chybě. Žárovky může také zobrazit na levém okraji s návrhy k vyřešení chyby. Další informace najdete v tématu [provádění rychlých akcí pomocí](../ide/perform-quick-actions-with-light-bulbs.md)žárovek.

    ![Žárovka při najetí myší](../ide/media/vs2015-lightbulb-hover.png "VS2015_LightBulb_Hover")

4. [Záložky](../ide/setting-bookmarks-in-code.md) vám umožní rychle přejít na konkrétní řádky v souborech, na kterých aktivně pracujete.

5. Okno [hierarchie volání](../ide/reference/call-hierarchy.md) lze vyvolat v kontextové nabídce textového editoru pro zobrazení metod, které volají a jsou volány metodou pod blikajícím kurzorem.

6. **Code Lens** umožňuje najít odkazy a změny kódu, propojených chyb, pracovních položek, revizí kódu a testování částí, aniž byste museli opustit Editor. Další informace najdete v tématu [Vyhledání změn kódu a další historie](../ide/find-code-changes-and-other-history-with-codelens.md).

7. V okně **Náhled do definice** se zobrazí definice metody nebo typu inline, bez přechodu z aktuálního kontextu. Toto okno teď funguje i pro XAML, příliš.

8. Možnost **Přejít na definici** kontextové nabídky vás provede přímo na místo, kde je funkce nebo objekt definovaný. Další příkazy pro navigaci jsou k dispozici také kliknutím pravým tlačítkem myši v editoru.

9. Související nástroj, [Prohlížeč objektů](https://msdn.microsoft.com/f89acfc5-1152-413d-9f56-3dc16e3f0470), umožňuje zkontrolovat sestavení .net nebo prostředí Windows Runtime ve vašem systému, abyste viděli, jaké typy obsahují a jaké metody a vlastnosti tyto typy obsahují.

     ![Prohlížeč Obect zobrazující System. Timer](../ide/media/objectbrowser.png "ObjectBrowser")

   Většina položek v nabídce Úpravy a zobrazení nabídky se vztahuje k editoru kódu nějakým způsobem. Další informace o editoru naleznete v tématu [Writing Code](../ide/writing-code-in-the-code-and-text-editor.md) and [Editing Code](https://www.visualstudio.com/features/ide-vs).

## <a name="compiling-and-building-your-code"></a>Kompilování a sestavování svého kódu

Sestavení projektu znamená, že ke kompilaci zdrojového kódu a provádění jakýchkoli kroků je nezbytných k vytvoření spustitelného souboru. Různé jazyky mají různé operace a pravidelné websites nesestavujte vůbec. V nabídce sestavení bez ohledu na typ projektu je standardní umístění pro tyto příkazy. Kompilace a spuštění kódu pomocí jednoho stisknutí kláves, stiskněte klávesu F5. Každý kompilátor je zcela konfigurovat přes rozhraní IDE. Panel nástrojů sestavení umožňuje určit, jestli se má sestavení verze ladění programu, symboly a kontrola dalších chyb povolit, aby podporovalo zarážky a krokování v ladicím programu, nebo sestavení pro vydání, což je co vám poskytne nakonec zákazníkům. Na stránce vlastností projektu můžete nakonfigurovat další nastavení buildu a mnoho dalších nastavení. Klikněte pravým tlačítkem na uzel projektu v Průzkumníku řešení a zvolte možnost Vlastnosti. Můžete také spustit sestavení z příkazového řádku.

Výstup sestavení, včetně chybových zpráv nebo zpráv o úspěchu, se zobrazí v okně **výstup** . **Seznam chyb** zobrazuje podrobné informace o chybách sestavení.

## <a name="debugging-your-code"></a>Ladění kódu
 Ladicí program stav grafiky sady Visual Studio umožňuje ladit kód spuštěný v místní projekt na vzdálené zařízení nebo emulátoru, jako jsou ty pro Android nebo Windows Phone. Můžete krokovat kód jeden příkaz najednou a kontrolovat proměnné, jak můžete přejít, lze krokovat vícevláknové aplikace a můžete nastavit zarážky, které jsou pouze přístupů, když je zadaná podmínka pravdivá. To všechno dá v editoru kódu, takže není nutné opustit kontext kódu.

 ![Okno náhledu nastavení zarážky](../ide/media/dbg-breakpoints-peekwindow.png "DBG_Breakpoints_PeekWindow")

 Na samotný ladicí program má více oken, které vám umožní zobrazit a pracovat s lokální proměnné, zásobník volání a dalších aspektů běhové prostředí. Tato okna můžete najít v nabídce **ladění** .

 [Příkazové okno](../ide/reference/immediate-window.md) umožňuje zadat výraz a okamžitě zobrazit jeho výsledek.

 Okno [IntelliTrace](https://msdn.microsoft.com/629e9660-c59a-446b-8c30-290059158f61) zaznamenává jednotlivá volání metod a další události do běžícího programu .NET a může vám pomohou rychle najít, kde problém vznikl.

 Další informace naleznete v tématu [ladění v aplikaci Visual Studio](../debugger/debugging-in-visual-studio.md).

## <a name="testing-your-code"></a>Testování kódu
 Visual Studio obsahuje rozhraní testování částí pro spravovaný kód (.NET) a jeden pro nativní kód C++. K vytvoření jednotky jednoduše přidejte testovací projekt do řešení, testy, psát testy a spusťte z okna Průzkumníka testů. Další informace najdete v tématu [testování částí kódu](../test/unit-test-your-code.md).

 ![Průzkumník testů jednotek](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

## <a name="analyzing-code-quality-and-performance"></a>Analýza kvality kódu a výkonu
 Visual Studio obsahuje výkonné nástroje pro analýzu statického a modulu runtime. Nástroje statické analýzy mohli snadno identifikovat potenciální chyby v návrhu, globalizace, vzájemná funkční spolupráce, výkon, zabezpečení a jiných kategorií. Testování výkonu nebo profilování, zahrnuje měření vykonávání programu. K těmto nástrojům přistupujete z nabídky **analyzovat** . Další informace najdete v tématu [zlepšení kvality pomocí sady Visual Studio diagnostické nástroje](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945).

## <a name="connecting-to-cloud-services-and-databases"></a>Připojení ke cloudovým službám a databází
 Okno [Průzkumník serveru](https://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) v sadě Visual Studio zobrazuje prostředky ve všech účtech spravovaných v rámci vašeho účtu přizpůsobení (ten, ke kterému jste se přihlásili), včetně SQL Server instancí, Azure, Salesforce.com, Office 365 a websites.

 ![Průzkumník serveru](../ide/media/vs2015-serverexplorer3.png "vs2015_ServerExplorer3")

 Visual Studio obsahuje [Nástroje pro Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx) (SSDT), které umožňují sestavovat, ladit, udržovat a Refaktorovat databáze. Můžete pracovat s projektem databáze, nebo přímo s připojeném databázovém instance nebo vypnout místně.

 Průzkumník objektů systému SQL Server v sadě Visual Studio nabízí přehled vaše databázové objekty, podobně jako SQL Server Management Studio. Průzkumník objektů systému SQL Server umožňuje práci lehká databáze správy a návrh, včetně úprav data v tabulce, porovnávání schémat a zpracování dotazů pomocí kontextové nabídky přímo z Průzkumníku objektů SQL serveru. SSDT také zahrnuje typy speciální projektů a nástrojů pro vývoj služby SQL Server 2012 Analysis Services, služby Reporting Services a integrace služby Business Intelligence (BI) řešení (dříve označované jako Business Intelligence Development Studio).

 ![Průzkumník objektů systému SQL Server](../ide/media/vs2015-sqlobjectexplorer.png "vs2015_SQLObjectExplorer")

## <a name="deploying-your-finished-application"></a>Nasazení dokončené aplikace
 Když je aplikace připravená k nasazení pro zákazníky, Visual Studio poskytuje nástroje k tomu, jestli nasazujete do Windows Store, na Sharepointový web, nebo s technologiemi InstallShield nebo instalační služby systému Windows. To je vše je přístupné prostřednictvím rozhraní IDE. Další informace najdete v tématu [nasazení aplikací, služeb a součástí](../deployment/deploying-applications-services-and-components.md).

## <a name="architecture-and-modeling-tools-enterprise-only"></a>Architektura a modelování nástroje (pouze v Enterprise)
 Architektura a modelování nástrojů sady Visual Studio můžete použít pro návrh a modelování vaší aplikace. Tyto nástroje umožňují vizualizovat strukturu kódu, chování a vztahy. Modely můžete vytvořit na různých úrovních podrobností v průběhu životního cyklu aplikací v rámci vašeho vývojového procesu. Můžete sledovat požadavky, úkoly, testovací případy, chyby a další práci související s vašimi modely propojením prvků modelu s pracovní položky serveru Team Foundation Server a váš plán vývoje. Další informace najdete v tématu [Návrh a modelování aplikace](../modeling/analyze-and-model-your-architecture.md).

## <a name="extending-visual-studio-through-the-visual-studio-sdk"></a>Rozšíření sady Visual Studio pomocí sady Visual Studio SDK
 Visual Studio je rozšiřitelná platforma. Rozšíření sady Visual Studio je vlastní nástroj, který se integruje s prostředím IDE. Můžete přidat rozšíření třetích stran nebo vytvořit vlastní. Další informace najdete v tématu [vývoj rozšíření sady Visual Studio](https://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14).

 [Pokyny pro uživatelské prostředí sady Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md) jsou zásadním odkazem na rozšíření pro všechny uživatele s psaním pro Visual Studio. Tyto pokyny specifické pro platformu také informace o návrhu dialogového okna, písma, barvy, ikony, běžných ovládacích prvků a jiné vzory interakcí, které způsobí, že vaši novou funkci se hladce integrují s Visual Studio.

## <a name="in-this-guide"></a>V této příručce

|||
|-|-|
|[Uživatelské účty a aktualizace](../ide/user-accounts-and-updates.md)|[Přizpůsobení integrovaného vývojového prostředí](../ide/personalizing-the-visual-studio-ide.md)|
|[Návody: Pohyb v integrovaném vývojovém prostředí](../ide/how-to-move-around-in-the-visual-studio-ide.md)|[Začínáme s vývojem pomocí jazyka Visual C++](../ide/get-started-developing-with-visual-studio.md)|
|[Hledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|[Řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md)|
|[Psaní kódu](../ide/writing-code-in-the-code-and-text-editor.md)|[Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md)|
|[Nástroje pro profilaci](../profiling/profiling-tools.md)|[Zlepšení kvality kódu](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|
|[Návrh uživatelského rozhraní](../designers/designing-user-interfaces.md)|[Analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md)|
|[Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)|[Nasazení aplikací, služeb a komponent](../deployment/deploying-applications-services-and-components.md)|
|[Podpora pro 64bitové integrované vývojové prostředí sady Visual Studio](../ide/visual-studio-ide-64-bit-support.md)|[Zabezpečení](../ide/security-in-visual-studio.md)|
|[Ukázky sady Visual Studio](../ide/visual-studio-samples.md)|[Microsoft Help Viewer 2.2](../ide/microsoft-help-viewer.md)|
|[Globalizace a lokalizace aplikací](../ide/globalizing-and-localizing-applications.md)|[Reference k uživatelskému rozhraní](../ide/reference/general-user-interface-elements-visual-studio.md)|

## <a name="see-also"></a>Viz také

- [Instalace sady Visual Studio 2015](../install/install-visual-studio-2015.md)
- [Úprava kódu](https://www.visualstudio.com/features/ide-vs)
- [Novinky v sadě Visual Studio 2015](../what-s-new-in-visual-studio-2015.md)
- [Přenosy, migrace a upgrade projektů sady Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
- [Kontaktujte nás](../ide/talk-to-us.md)