---
title: Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
ms.assetid: 772b6cf4-cee5-42d0-bc18-b4eb07e22ff0
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 52e0b8f87774b11b1750700d5bef19c5423824c4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667146"
---
# <a name="visual-studio-ide"></a>Visual Studio – sada IDE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Microsoft Visual Studio 2015 je sada nástrojů pro vytváření softwaru, od plánovací fáze až po návrh uživatelského rozhraní, kódování, testování, ladění, Analýza kvality kódu a výkon, nasazení na zákazníky a shromažďování telemetrie o využití. Tyto nástroje jsou navržené tak, aby co nejrychleji spolupracovaly a všechny byly vystavené prostřednictvím integrovaného vývojového prostředí (IDE) sady Visual Studio.

Sadu Visual Studio můžete použít k vytvoření mnoha druhů aplikací, od jednoduchých aplikací pro Store a her pro mobilní klienty až po velké komplexní systémy, které Power Users a datová centra využívají. Můžete vytvořit:

- Aplikace a hry, které nepoužívají systém Windows, ale také Android a iOS.

- Weby a webové služby založené na ASP.NET, JQuery, AngularJS a dalších oblíbených rozhraních.

- Aplikace pro platformy a zařízení, podobně jako Azure, Office, SharePoint, HoloLens, Kinect a Internet věcí, jsou popsány pouze v několika příkladech.

- Hry a aplikace náročné na grafiku pro celou řadu zařízení s Windows, včetně konzoly Xbox, pomocí rozhraní DirectX.

Visual Studio ve výchozím nastavení poskytuje podporu C#pro, C C++a, JavaScript F#, a Visual Basic. Sada Visual Studio funguje a integruje se s aplikacemi třetích stran, jako je Unity, prostřednictvím rozšíření [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) a Apache Cordova prostřednictvím [Visual Studio Tools pro Apache Cordova](https://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42). Aplikaci Visual Studio můžete roztáhnout sami tím, že vytvoříte vlastní nástroje, které provádějí specializované úkoly.

Pokud jste ještě nepoužili Visual Studio, Seznamte se se základy [Začínáme s vývojem v prostředí Visual Studio](../ide/get-started-developing-with-visual-studio.md) a návody.

Pokud se chcete dozvědět o nových funkcích sady Visual Studio 2015, přečtěte si téma [novinky v aplikaci Visual studio 2015](../what-s-new-in-visual-studio-2015.md).

## <a name="visual-studio-setup"></a>Instalační program sady Visual Studio
 Můžete zjistit, která edice sady Visual Studio je pro vás vhodná v [edicích sady Visual Studio](http://www.visualstudio.com/products/visual-studio-with-msdn-overview-vs).

 Můžete nainstalovat Visual Studio 2015 stažením ze sady [Visual Studio downloads](http://www.visualstudio.com/downloads/download-visual-studio-vs.aspx). Pokud potřebujete o instalačním procesu získat další informace, přečtěte si téma [instalace sady Visual Studio 2015](../install/install-visual-studio-2015.md).

## <a name="ide-basics"></a>Základní informace o rozhraní IDE
 Následující obrázek ukazuje integrované vývojové prostředí sady Visual Studio s otevřeným projektem a okno Průzkumník řešení pro navigaci v souborech projektu a okno Team Explorer pro navigaci správy zdrojového kódu a pracovní položky. Funkce v záhlaví, které jsou vyvolány, jsou podrobněji vysvětleny níže.

 ![Integrované vývojové prostředí sady Visual Studio](../ide/media/visualstudioide.png "VisualStudioIDE")

### <a name="signing-in"></a>Přihlášení
 Při prvním spuštění sady Visual Studio se můžete přihlásit pomocí účet Microsoft nebo svého pracovního nebo školního účtu. Přihlášení umožňuje synchronizovat vaše nastavení, například rozložení oken, v různých zařízeních a automaticky se připojit k potřebným službám, například k předplatným Azure a Visual Studio Team Services. Pokud máte licenci založenou na předplatném, budete se muset pravidelně přihlašovat k sadě Visual Studio, aby se váš License token udržoval hned nový. Pokud máte licenci ke kódu Product Key, nemusíte se přihlašovat, ale uděláte to tak, aby se připojovaly k Visual Studio Team Servicesům a vašim účtům pomocí Azure, Office 365, Salesforce.com. Další informace najdete v tématu [přihlášení do sady Visual Studio](../ide/signing-in-to-visual-studio.md).

 Pokud máte více Visual Studio Team Services účtů, účtů Azure nebo předplatných MSDN, můžete je propojit a přistupovat k prostředkům a službám ve všech účtech pomocí jednotného přihlašování. Další informace najdete v tématu [práce s několika uživatelskými účty](../ide/work-with-multiple-user-accounts.md).

### <a name="staying-up-to-date"></a>Aktuální čas
 Ikona oznámení v pravém horním rohu záhlaví obsahuje informace o tom, kdy jsou k dispozici aktualizace pro sadu Visual Studio nebo jakékoli související součásti, které jste nainstalovali. Můžete zvolit, zda chcete tato oznámení zavřít nebo zpracovat. Další informace najdete v tématu [oznámení sady Visual Studio](../ide/visual-studio-notifications.md).

### <a name="finding-things-and-getting-help"></a>Hledání věcí a získání informací o nápovědě
 Okno [Snadné spuštění](../ide/reference/quick-launch-environment-options-dialog-box.md) zobrazené níže je rychlý způsob, jak najít příkazy, nástroje, funkce a tak dále v aplikaci Visual Studio, když neznáte klávesovou zkratku nebo umístění nabídky. Stačí zadat, co hledáte a snadné spuštění vám poskytne odkaz na něj.

 ![Výsledky snadného spuštění pro nový projekt](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

 MSDN je webová stránka Microsoftu pro technickou dokumentaci; tuto stránku čtete na MSDN hned teď! V aplikaci Visual Studio můžete stisknutím klávesy **F1** přejít na stránku Nápověda MSDN pro aktivní okno. V editoru kódu můžete také stisknutím klávesy **F1** přejít na stránku Nápověda MSDN pro rozhraní API nebo klíčové slovo na aktuální pozici blikajícího kurzoru. Například v C# souboru umístěte blikající kurzor někam do nebo jen na konci deklarace `System.String` a stisknutím klávesy **F1** přejděte na stránku Nápověda MSDN pro <xref:System.String>.

### <a name="giving-feedback"></a>Poskytnutí zpětné vazby
 Kdykoli budete chtít, můžete poskytnout zpětnou vazbu k aplikaci Visual Studio. Klikněte na ikonu zpětné vazby v záhlaví vedle **Rychlé spuštění** a potom klikněte na **ohlásit problém** nebo **Poskytněte návrh**. Předběžné verze verzí sady Visual Studio mají také hodnotu **Ohodnotit tuto možnost produktu** . Podíváme se na všechny tyto komentáře a využijeme je k vylepšení produktu. Další informace najdete v tématu [o komunikaci s námi](../ide/talk-to-us.md).

### <a name="personalizing-the-ide"></a>Přizpůsobení integrovaného vývojového prostředí
 Rozložení okna můžete přizpůsobit tak, aby vyhovovalo vašemu stylu vývoje. Kdykoli můžete jakékoli okno ukotvit, plovoucí nebo skrýt a můžete Editor spustit i v režimu celé obrazovky. Můžete vytvořit a uložit více vlastních rozložení oken, která zobrazují pouze okna potřebná pro konkrétní kontexty. Můžete například vytvořit rozložení na celou obrazovku, aby se zobrazila pouze Editor kódu. A můžete vytvořit různá rozložení pro ladění a pro operace týmu. Další informace najdete v tématu [přizpůsobení rozložení oken](../ide/customizing-window-layouts-in-visual-studio.md).

 Aplikaci Visual Studio si můžete přizpůsobit mnoha různými způsoby, a pokud pracujete na více počítačích, budete moct nastavení přesměrovat do roamingu. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí](../ide/personalizing-the-visual-studio-ide.md).

 K dispozici jsou klávesové zkratky pro téměř všechno a můžete je také přizpůsobit. Chcete-li vytvořit nové zástupce, v okně snadné spuštění zadejte "klávesnice" a otevřete tak dialogové okno klávesnice. Odtud můžete stisknutím klávesy F1 přejít na stránku Nápověda MSDN, pokud potřebujete další informace o možnostech. Další informace naleznete v tématu [výchozí klávesové zkratky v aplikaci Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="connecting-to-visual-studio-team-services-and-team-foundation-server"></a>Připojení k Visual Studio Team Services a Team Foundation Server
 Visual Studio Team Services (VSTS) je cloudová služba pro hostování softwarových projektů a umožňující spolupráci v týmech. VSTS podporuje i systémy správy zdrojového kódu Git i Team Foundation i metody Scrum, CMMI a agilního vývoje. Správa verzí Team Foundation (TFVC) používá jedno centralizované serverové úložiště ke sledování a k souborům verze. Místní změny se vždycky vrátí do centrálního serveru, kde můžou další vývojáři získat nejnovější změny. Team Foundation Server (TFS) 2015 je Centrum správy životního cyklu aplikací pro Visual Studio. Umožňuje všem zapojeným do procesu vývoje zúčastnit se použití jediného řešení. TFS je vhodný pro správu heterogenních týmů a projektů.

 Pokud máte účet Visual Studio Team Services nebo Team Foundation Server v síti, připojíte se k němu prostřednictvím okna Team Explorer. Z tohoto okna můžete kontrolovat kód do správy zdrojového kódu nebo z něj, spravovat pracovní položky, spouštět sestavení a přistupovat k týmovým místnostem a pracovním prostorům. Team Explorer můžete otevřít z **panelu snadného spuštění** nebo v hlavní nabídce ze **zobrazení &#124; Team Explorer** nebo z **týmu &#124; spravovat připojení**.  Další informace o Visual Studio Team Services najdete v tématu [www.VisualStudio.com](https://www.visualstudio.com/). Další informace o Team Foundation Server najdete v tématu [Team Foundation Server](https://www.visualstudio.com/products/tfs-overview-vs).

 Následující obrázek ukazuje podokno Team Explorer pro řešení hostované v VSTS:

 ![Team Explorer sady Visual Studio](../ide/media/vs2015-teamexplorer.png "VS2015_TeamExplorer")

## <a name="creating-solutions-and-projects"></a>Vytváření řešení a projektů
 I když pomocí sady Visual Studio můžete procházet jednotlivé soubory kódu, častěji budete pracovat v *projektu*. Projekt sady Visual Studio je kolekce souborů a prostředků, které jsou kompilovány do jediného binárního spustitelného souboru pro aplikace (například. exe, DLL nebo appx). Pro weby non-ASP.NET není vytvořen žádný spustitelný soubor a projekt obsahuje pouze soubory HTML, JavaScript a obrázky. Vzhledem k tomu, že někdy může být nutné vytvořit více binárních souborů nebo webů, které úzce souvisejí, Visual Studio má koncept řešení, které může obsahovat více projektů nebo webů. Při vytváření projektu vytváříte ve skutečnosti řešení projektu a v případě potřeby můžete do tohoto řešení přidat další projekty později. Například pokud máte projekt knihovny DLL, můžete přidat projekt. exe do řešení, které načte a zpracuje knihovnu DLL.

 *Šablona projektu* je kolekce předem vyplněných souborů kódu a nastavení konfigurace, která vám pomohou nastavit rychlé vytvoření konkrétního typu aplikace. Visual Studio obsahuje mnoho šablon projektů, ze kterých si můžete vybrat, a pokud žádná z výchozích šablon nefunguje za vás, můžete si vytvořit svoje vlastní. Po vytvoření projektu se šablonou můžete v něm začít psát vlastní kód, a to buď do zadaných souborů, nebo do nově přidaných souborů. Další informace najdete v tématu [řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md). Na následujícím obrázku je znázorněno dialogové okno Nový projekt se šablonami projektu, které jsou k dispozici pro aplikace ASP.NET.

 ![Dialogové okno Nový projekt sady Visual Studio](../ide/media/vs2015-newprojectdialog.png "VS2015_NewProjectDialog")

## <a name="designing-the-user-interface"></a>Návrh uživatelského rozhraní
 Návrhář je intuitivní nástroj, který umožňuje vytvořit uživatelské rozhraní bez psaní kódu. Ovládací prvky uživatelského rozhraní, jako jsou seznamy, kalendáře a tlačítka, lze přetáhnout z okna [Sada nástrojů](../ide/reference/toolbox.md) na návrhovou plochu, která představuje okno nebo dialogové okno. Můžete změnit velikost a změnit uspořádání prvků bez psaní kódu. Návrháři jsou zahrnuti do libovolného typu projektu, který má uživatelské rozhraní.

 Pokud má váš projekt uživatelské rozhraní založené na jazyce XAML, výchozí Návrhář je Blend pro Visual Studio, sofistikovaný grafický nástroj, který funguje bez problémů se sadou Visual Studio.

 ![Panel](../ide/media/b5-artboard.png "b5_artboard")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Zobrazení Návrh** Zobrazí vizuální návrh dokumentu. V tomto zobrazení můžete nakreslit nebo upravovat objekty na návrhové ploše.|
|![](../designers/media/b1-2.png "B1_2")|**Popis cesty** Rychle se přesouvá mezi režimem úprav šablony, režimem úprav stylu a rozsahem úprav objektů pro vybraný objekt.|
|![](../designers/media/b1-3.png "B1_3")|**Zvětšení** Slouží k přiblížení návrhové plochy nebo objektů na návrhové ploše.|
|![](../designers/media/b1-4.png "B1_4")|**Ovládací prvky návrhové plochy** Pomocí těchto ovládacích prvků (**zobrazení mřížky**pro přichycení, **přichycení k** mřížce a **Zapnutí nebo vypnutí přichycení do zarovnávacím čárám**) nastavte možnosti přichycení. Přitahování je užitečné pro sestavování objektů do sebe nebo do rovnoměrného prostoru čar na návrhové ploše.|
|![](../designers/media/b1-5.png "B1_5")|**Editor kódu** Upravte kód XAML, C# C++ nebo Visual Basic kód ručně v editoru kódu.|

 Další informace naleznete v tématu [navrhování XAML v aplikaci Visual Studio a Blend pro Visual Studio](../designers/designing-xaml-in-visual-studio.md).

## <a name="writing-navigating-and-understanding-code"></a>Psaní, navigace a porozumění kódu
 Pokud jste vývojář, okno editoru je tam, kde budete pravděpodobně strávit většinu času. Visual Studio obsahuje editory C#pro C++jazyky,, Visual Basic, JavaScript, XML, HTML, CSS F#a a třetí strany, nabízejí editory a moduly plug-in (a kompilátory) pro mnoho dalších jazyků.

 Jednotlivé soubory v textovém editoru můžete upravit kliknutím na **soubor &#124; &#124; otevřít soubor.** Chcete-li upravit soubory v otevřeném projektu, klikněte na název souboru v Průzkumník řešení. Kód je barevně barevný a můžete přizpůsobit barevné schéma zadáním "barvy" v okně snadné spuštění. Můžete mít spoustu oken textový editor s kartami otevřít najednou. Jednotlivá okna můžete rozdělit nezávisle. Textový editor můžete také spustit v režimu celé obrazovky.

 ![GreetingsConsoleApp. cpp v editoru kódu](../ide/media/c-ide-editorlinenumberswordwrapon.png "IDE_EditorLineNumbersWordWrapOn jazyka C + +")

 Textový editor je vysoce interaktivní (pokud ho chcete mít) s mnoha funkcemi pro zvýšení produktivity, které vám pomůžou rychleji psát lepší kód. Tyto funkce se liší podle jazyka a nemusíte je používat (typ "Editor" v okně snadné spuštění) a zapnout nebo vypnout funkce: některé z běžných funkcí produktivity:

1. [Refaktoring](../ide/refactoring-in-visual-studio.md) zahrnuje operace, jako je například inteligentní přejmenování proměnných, přesunutí vybraných řádků kódu do samostatné funkce, přesunutí kódu do jiných umístění, parametry funkcí redordering a další.

2. *IntelliSense* je zastřešující termín pro sadu oblíbených funkcí, které zobrazují informace o typu kódu přímo v editoru a v některých případech zápis malých bitů kódu za vás. Vypadá to, že je v editoru vložená základní dokumentace, která vám ušetří informace o typech v samostatném okně s přehledem. Funkce IntelliSense se liší podle jazyka. Další informace naleznete v tématu [Visual C# IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md), [Visual Basic specifické pro technologii IntelliSense](../ide/visual-basic-specific-intellisense.md). Následující ilustrace znázorňuje některé funkce technologie IntelliSense v práci:

    ![Seznam členů sady Visual Studio](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")

3. **Vlnovky** upozorňují na chyby nebo potenciální problémy v kódu v reálném čase při psaní, což vám umožní je okamžitě opravit bez čekání na zjištění chyby během kompilace nebo doby běhu. Pokud najedete myší na vlnovku, zobrazí se další informace o chybě. Žárovka se může zobrazit také na levém okraji s návrhy na opravu chyby. Další informace najdete v tématu [provádění rychlých akcí pomocí](../ide/perform-quick-actions-with-light-bulbs.md)žárovek.

    ![Žárovka při najetí myší](../ide/media/vs2015-lightbulb-hover.png "VS2015_LightBulb_Hover")

4. [Záložky](../ide/setting-bookmarks-in-code.md) vám umožní rychle přejít na konkrétní řádky v souborech, na kterých aktivně pracujete.

5. Okno [hierarchie volání](../ide/reference/call-hierarchy.md) lze vyvolat v kontextové nabídce textového editoru pro zobrazení metod, které volají a jsou volány metodou pod blikajícím kurzorem.

6. **Code Lens** umožňuje najít odkazy a změny kódu, propojených chyb, pracovních položek, revizí kódu a testování částí, aniž byste museli opustit Editor. Další informace najdete v tématu [Vyhledání změn kódu a další historie](../ide/find-code-changes-and-other-history-with-codelens.md).

7. V okně **Náhled do definice** se zobrazí definice metody nebo typu inline, bez přechodu z aktuálního kontextu. Toto okno teď funguje i pro XAML.

8. Možnost **Přejít na definici** kontextové nabídky vás provede přímo na místo, kde je funkce nebo objekt definovaný. Další navigační příkazy jsou k dispozici také kliknutím pravým tlačítkem myši v editoru.

9. Související nástroj, [Prohlížeč objektů](https://msdn.microsoft.com/f89acfc5-1152-413d-9f56-3dc16e3f0470), umožňuje zkontrolovat sestavení .net nebo prostředí Windows Runtime ve vašem systému, abyste viděli, jaké typy obsahují a jaké metody a vlastnosti tyto typy obsahují.

     ![Prohlížeč Obect zobrazující System. Timer](../ide/media/objectbrowser.png "ObjectBrowser")

   Většina položek v nabídce Upravit a v nabídce zobrazení se v editoru kódu nějakým způsobem vztahuje. Další informace o editoru naleznete v tématu [Writing Code](../ide/writing-code-in-the-code-and-text-editor.md) and [Editing Code](https://www.visualstudio.com/features/ide-vs).

## <a name="compiling-and-building-your-code"></a>Kompilování a sestavení kódu

Chcete-li sestavit projekt pro zkompilování zdrojového kódu a provedení všech kroků nezbytných k vytvoření spustitelného souboru. Různé jazyky mají různé operace sestavení a běžné weby se nevytvářejí vůbec. Bez ohledu na typ projektu je nabídka sestavení standardním umístěním pro tyto příkazy. Chcete-li zkompilovat a spustit kód jediným stisknutím klávesy F5, stiskněte klávesu F5. Každý kompilátor je zcela konfigurovatelný prostřednictvím integrovaného vývojového prostředí (IDE). Na panelu nástrojů sestavení můžete určit, zda se má sestavit ladicí verze programu se symboly a další kontrola chyb povolených pro podporu zarážek a jednoduchého krokování v ladicím programu nebo sestavení pro vydání, což je to, co budete nakonec poskytovat zákazníkům. Můžete nakonfigurovat další nastavení sestavení a mnoho dalších nastavení na stránce vlastností projektu. V Průzkumník řešení klikněte pravým tlačítkem myši na uzel projektu a vyberte vlastnosti. Sestavení lze také spustit z příkazového řádku.

Výstup sestavení, včetně chybových zpráv nebo zpráv o úspěchu, se zobrazí v okně **výstup** . **Seznam chyb** zobrazuje podrobné informace o chybách sestavení.

## <a name="debugging-your-code"></a>Ladění kódu
 Nejmodernější ladicí program sady Visual Studio umožňuje ladit kód spuštěný v místním projektu, na vzdáleném zařízení nebo v emulátoru, jako jsou ty pro Android nebo Windows Phone. V jednom okamžiku můžete krokovat kód jedním příkazem a při prohlížení proměnných kontrolovat proměnné, které můžete procházet pomocí vícevláknových aplikací, a můžete nastavit zarážky, které jsou k dispozici pouze v případě, že je zadaná podmínka pravdivá. Vše lze nakonfigurovat v editoru kódu samotném, takže nemusíte opustit kontext kódu.

 ![Okno náhledu nastavení zarážky](../ide/media/dbg-breakpoints-peekwindow.png "DBG_Breakpoints_PeekWindow")

 Ladicí program obsahuje několik oken, která umožňují zobrazit a manipulovat s místními proměnnými, zásobníkem volání a dalšími aspekty běhového prostředí. Tato okna můžete najít v nabídce **ladění** .

 [Příkazové okno](../ide/reference/immediate-window.md) umožňuje zadat výraz a okamžitě zobrazit jeho výsledek.

 Okno [IntelliTrace](https://msdn.microsoft.com/629e9660-c59a-446b-8c30-290059158f61) zaznamenává jednotlivá volání metod a další události do běžícího programu .NET a může vám pomohou rychle najít, kde problém vznikl.

 Další informace naleznete v tématu [ladění v aplikaci Visual Studio](../debugger/debugging-in-visual-studio.md).

## <a name="testing-your-code"></a>Testování kódu
 Visual Studio obsahuje rozhraní pro testování částí pro spravovaný kód (.NET) a jeden pro nativní C++. Chcete-li vytvořit testy jednotek, jednoduše do svého řešení přidejte testovací projekt, zapište testy a pak je spusťte z okna Průzkumník testů. Další informace najdete v tématu [testování částí kódu](../test/unit-test-your-code.md).

 ![Průzkumník testů jednotek](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

## <a name="analyzing-code-quality-and-performance"></a>Analýza kvality kódu a výkonu
 Visual Studio obsahuje výkonné nástroje pro statickou a běhovou analýzu. Nástroje statické analýzy vám pomůžou identifikovat možné chyby v návrhu, globalizaci, interoperabilitě, výkonu, zabezpečení a dalších kategoriích. Testování výkonu nebo profilace zahrnuje měření, jak se váš program spouští. K těmto nástrojům přistupujete z nabídky **analyzovat** . Další informace najdete v tématu [zlepšení kvality pomocí sady Visual Studio diagnostické nástroje](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945).

## <a name="connecting-to-cloud-services-and-databases"></a>Připojení ke cloudovým službám a databázím
 Okno [Průzkumník serveru](https://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) v sadě Visual Studio zobrazuje prostředky ve všech účtech spravovaných v rámci vašeho účtu přizpůsobení (ten, ke kterému jste se přihlásili), včetně SQL Server instancí, Azure, Salesforce.com, Office 365 a websites.

 ![Průzkumník serveru](../ide/media/vs2015-serverexplorer3.png "vs2015_ServerExplorer3")

 Visual Studio obsahuje [Nástroje pro Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx) (SSDT), které umožňují sestavovat, ladit, udržovat a Refaktorovat databáze. Můžete pracovat s databázovým projektem nebo přímo s instancí připojené databáze v místním prostředí.

 Průzkumník objektů systému SQL Server v aplikaci Visual Studio nabízí zobrazení databázových objektů podobně jako SQL Server Management Studio. Průzkumník objektů systému SQL Server vám umožní provádět návrh a práci v databázi, včetně úpravy dat tabulky, porovnávání schémat a provádění dotazů, a to pomocí kontextových nabídek přímo z Průzkumník objektů systému SQL Server. SSDT zahrnuje také speciální typy projektů a nástroje pro vývoj SQL Server 2012 Analysis Services, Reporting Services a řešení Integration Services Business Intelligence (BI) (dříve označovaného jako Business Intelligence Development Studio).

 ![Průzkumník objektů systému SQL Server](../ide/media/vs2015-sqlobjectexplorer.png "vs2015_SQLObjectExplorer")

## <a name="deploying-your-finished-application"></a>Nasazení dokončené aplikace
 Když je vaše aplikace připravená k nasazení na zákazníky, Visual Studio poskytuje nástroje k tomu, abyste to provedli, ať už nasazujete do Windows Storu, na web služby SharePoint nebo pomocí technologie InstallShield nebo Instalační služba systému Windows. Vše je přístupné prostřednictvím integrovaného vývojového prostředí (IDE). Další informace najdete v tématu [nasazení aplikací, služeb a součástí](../deployment/deploying-applications-services-and-components.md).

## <a name="architecture-and-modeling-tools-enterprise-only"></a>Nástroje pro architekturu a modelování (jenom Enterprise)
 K návrhu a modelování vaší aplikace můžete použít nástroje pro architekturu a modelování sady Visual Studio. Tyto nástroje vám pomůžou vizualizovat strukturu kódu, chování a vztahy. V rámci procesu vývoje můžete vytvářet modely na různých úrovních podrobností v životním cyklu aplikace. Můžete sledovat požadavky, úkoly, testovací případy, chyby a další práci, která je přidružena k vašim modelům, propojením prvků modelu s Team Foundation Server pracovními položkami a vaším plánem vývoje. Další informace najdete v tématu [Návrh a modelování aplikace](../modeling/analyze-and-model-your-architecture.md).

## <a name="extending-visual-studio-through-the-visual-studio-sdk"></a>Rozšíření sady Visual Studio pomocí sady Visual Studio SDK
 Visual Studio je rozšiřitelná platforma. Rozšíření sady Visual Studio je vlastní nástroj, který se integruje s IDE. Můžete přidat rozšíření třetích stran nebo vytvořit vlastní. Další informace najdete v tématu [vývoj rozšíření sady Visual Studio](https://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14).

 [Pokyny pro uživatelské prostředí sady Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md) jsou zásadním odkazem na rozšíření pro všechny uživatele s psaním pro Visual Studio. Tyto pokyny pro konkrétní platformu obsahují informace o návrhu dialogů, písmech, barvách, ikonách, běžných ovládacích prvcích a dalších vzorcích interakce, které zajistí bezproblémové integraci nové funkce se sadou Visual Studio.

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