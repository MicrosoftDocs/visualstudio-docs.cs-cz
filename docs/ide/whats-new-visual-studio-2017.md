---
title: Novinky v sadě Visual Studio 2017
titleSuffix: ''
description: Seznamte se s novými funkcemi v aplikaci Visual Studio 2017.
ms.date: 12/18/2018
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 4fd3bde36b81dde254f3447d46bd05ffc41c6cde
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925910"
---
# <a name="whats-new-in-visual-studio-2017"></a>Novinky v sadě Visual Studio 2017

**Aktualizováno pro [verzi 15.9](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)**

Hledáte upgrade z předchozí verze sady Visual Studio? Zde je uvedeno, co vám Visual Studio 2017 může nabídnout: Nekonkurenční produktivita pro jakékoli vývoj, aplikace a platformy Pomocí sady Visual Studio 2017 můžete vyvíjet aplikace pro Android, iOS, Windows, Linux, web i Cloud. Svůj kód můžete rychle psát, snadno ladit a diagnostikovat, často testovat a bez obav vydávat. Navíc si můžete sadu Visual Studio rozšířit a přizpůsobit pomocí svých vlastních rozšíření. Používejte správu verzí, agilní a efektivní spolupráci s touto verzí!

>[!div class="button"]
>[Stáhnout Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

Zde je rekapitulace vysoké úrovně změn, které byly provedeny od předchozí verze, Visual Studio 2015:

* **[Předefinované základy](#redefined-fundamentals)** . Nové prostředí pro instalaci znamená, že můžete nainstalovat rychleji a nainstalovat to, co chcete, když ho potřebujete.
* **[Výkon a produktivita](#performance-and-productivity)** . Zaměřili jsme se na nové a moderní možnosti vývoje mobilních, cloudových a desktopových aplikací. A Visual Studio se spouští rychleji, je rychlejší reagovat a používá méně paměti než předtím.
* **[Vývoj cloudových aplikací v Azure](#cloud-app-development-with-azure)** Integrovaná sada nástrojů Azure vám umožní snadno vytvářet aplikace zaměřené na Cloud, které využívají Microsoft Azure. Sada Visual Studio usnadňuje konfiguraci, sestavování, ladění, balení a nasazení aplikací a služeb v Azure.
* **[Vývoj aplikací pro Windows](#windows-app-development)** . Použijte šablony UWP v aplikaci Visual Studio 2017 k vytvoření jednoho projektu pro všechna zařízení &ndash; s Windows 10 PC, tablet, telefon, Xbox, HoloLens, Surface Hub a další.
* **[Vývoj mobilních aplikací](#mobile-app-development)** . Proveďte inovace a získejte výsledky rychle pomocí Xamarin, který sjednocuje vaše mobilní požadavky na více platforem na jeden základní základ kódu a sadu dovedností.
* **[Vývoj pro různé platformy](#cross-platform-development)** . Bez problémů doručovat software na libovolnou cílovou platformu. Rozšiřování procesů DevOps do SQL Server prostřednictvím nástrojů pro data Redgate a bezpečné automatizaci nasazování databází ze sady Visual Studio. Nebo pomocí .NET Core napište aplikace a knihovny, které se spouštějí nezměněné v operačních systémech Windows, Linux a macOS.
* **[Vývoj her](#games-development)** . S Visual Studio Tools pro Unity (VSTU) můžete použít Visual Studio napsat hru a editor skriptů v jazyce C# a pak použijte jeho výkonný ladicí program najít a opravit chyby.
* **[Vývoj AI](#ai-development)** . Pomocí Visual Studio Tools for AI můžete využívat funkce produktivity sady Visual Studio k urychlení inovací AI. Sestavujte, testujte a nasaďte řešení pro hloubkové učení a AI, která se bezproblémově integrují s Azure Machine Learning pro robustní možnosti experimentování.

> [!NOTE]
> Úplný seznam nových funkcí a funkcí v aplikaci Visual Studio 2017 najdete v tématu [aktuální poznámky k verzi](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017). A pro náhled v budoucích nabídkách funkcí si přečtěte [poznámky k verzi Preview](/visualstudio/releasenotes/vs2017-preview-relnotes?context=visualstudio/default&contextView=vs-2017).

Zde jsou podrobnější informace o některých z nejvýznamnějších vylepšení a nových funkcí v aplikaci Visual Studio 2017.

## <a name="redefined-fundamentals"></a>Předefinované základy

### <a name="a-new-setup-experience"></a>Nové prostředí instalace

Visual Studio usnadňuje a urychluje instalaci jenom těch funkcí, které potřebujete, a to v případě potřeby. A odinstaluje se i čistě.

Nejdůležitější změnou poznámky při instalaci sady Visual Studio je nové prostředí pro nastavení. Na kartě **úlohy** se zobrazí možnosti instalace, které jsou seskupené tak, aby představovaly běžná rozhraní, jazyky a platformy. Pokrývá vše od vývoje desktopových aplikací .NET C++ až po vývoj aplikací v systémech Windows, Linux a iOS.

Vyberte úlohy, které potřebujete, a v případě potřeby je změňte.

![Dialogové okno instalace sady Visual Studio 2017](../install/media/install-visual-studio-enterprise.png)

A máte možnost doladit instalaci také:

* Chcete místo používání úloh vybrat vlastní komponenty? V instalačním programu vyberte kartu **jednotlivé součásti** .
* Chcete nainstalovat jazykové sady, aniž byste museli měnit možnost jazyka Windows? Vyberte kartu **jazykové sady** instalačního programu.
* **Novinka v 15,7**: Chcete změnit umístění, kde se Visual Studio instaluje? V instalačním programu klikněte na kartu **Možnosti instalace** .

Další informace o novém instalačním prostředí, včetně podrobných pokynů, které vás provedou, najdete na stránce [instalace sady Visual Studio](../install/install-visual-studio.md) .

### <a name="a-focus-on-accessibility"></a>Zaměření na přístupnost

**Novinka v 15,3**, provedli jsme více než 1 700 cílových oprav pro zlepšení kompatibility mezi Visual Studio a technologie pro usnadnění, které mnoho zákazníků používá. Existují spousty scénářů, které jsou kompatibilní s čtečkami obrazovky, motivy s vysokým kontrastem a dalšími technologiemi usnadnění než dřív. Ladicí program, editor a prostředí mají značnou vylepšení.

Další informace najdete v blogovém příspěvku o [vylepšeních dostupnosti v aplikaci Visual Studio 2017 verze 15,3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) .

## <a name="performance-and-productivity"></a>Výkon a produktivita

### <a name="sign-in-across-multiple-accounts"></a>Přihlaste se napříč několika účty

V aplikaci Visual Studio jsme zavedli novou službu identit, která umožňuje sdílet uživatelské účty napříč Team Explorer, nástroji Azure, Microsoft Store publikování a dalšími.

Můžete zůstat přihlášeni i déle. Visual Studio vás nebude požádán, abyste se znovu přihlásili každých 12 hodin. Další informace najdete v příspěvku na blogu o [méně přihlašovacích dotazech sady Visual Studio](https://devblogs.microsoft.com/visualstudio/fewer-visual-studio-sign-in-prompts/) .

### <a name="start-visual-studio-faster"></a>Rychlejší spuštění sady Visual Studio

Nové centrum výkonu sady Visual Studio vám může přispět k optimalizaci času spuštění IDE. Centrum výkonu obsahuje seznam všech rozšíření a oken nástrojů, které mohou zpomalit spuštění rozhraní IDE. Můžete ho použít ke zlepšení výkonu při spuštění, určením, kdy se rozšíření spustí, nebo zda jsou okna nástrojů otevřená při spuštění.

### <a name="faster-on-demand-loading-of-extensions"></a>Rychlejší načítání rozšíření na vyžádání

Visual Studio přesouvá jeho rozšíření (a také pracuje s rozšířeními třetích stran) tak, aby se načetla na vyžádání, nikoli při spuštění IDE. Zajímá o tom, která rozšíření ovlivňují spouštění, načítání řešení a psaní výkonu? Tyto informace můžete zobrazit v **nápovědě** > ke**správě výkonu sady Visual Studio**.

  ![Dialogové okno Možnosti v aplikaci Visual Studio 2017](media/vs2017ide-manage-vs-perf.png)

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Správa rozšíření pomocí Správce rozšíření pro roaming

Při přihlášení do sady Visual Studio je snazší nastavit každé vývojové prostředí s oblíbenými rozšířeními. Nový správce rozšíření pro roaming sleduje všechna vaše oblíbená rozšíření vytvořením synchronizovaného seznamu v cloudu.

Chcete-li zobrazit seznam rozšíření v aplikaci Visual Studio, klikněte na rozšíření **nástroje** >  **& aktualizace**a potom klikněte na **Správce rozšíření pro roaming**.

![Visual Studio 2017 – dialogové okno rozšíření a aktualizace](media/vs2017ide-extensions-and-updates.png)

Správce rozšíření pro roaming sleduje všechna rozšíření, která nainstalujete, ale můžete vybrat, které z nich chcete přidat do svého seznamu roamingu.

![Visual Studio 2017 – dialogové okno rozšíření a aktualizace](media/vs2017ide-RoamingExtensionManager.png)

Pokud používáte Správce rozšíření pro roaming, v seznamu jsou tři typy ikon:

* ![Roamingovaná ikona](media/vs2017ide-roamedicon.png) : Rozšíření, které je součástí tohoto seznamu roamingu, ale není nainstalované na vašem počítači.
  (Můžete je nainstalovat pomocí tlačítka pro **stažení** .)
* ![Ikona](media/vs2017ide-roamedinstalledicon.png) nainstalovaného & s roamingem nainstalovaná **_& nainstalována_** : Všechna rozšíření, která jsou součástí tohoto seznamu roamingu a jsou nainstalovaná ve vašem vývojovém prostředí.
  (Pokud se rozhodnete, že nechcete roaming, můžete je odebrat pomocí tlačítka **zastavit roaming** .)
* ![Nainstalovaná](media/vs2017ide-installedicon.png) ikona nainstalované: Všechna rozšíření, která jsou nainstalovaná v tomto prostředí, ale nejsou součástí vašeho seznamu roamingu.
  (Do seznamu roaming můžete přidat rozšíření pomocí tlačítka **Spustit roaming** .)

Všechna rozšíření, která jste si stáhli během přihlašování, se do seznamu přidají jako **& nainstalovaná**s roamingem. Rozšíření se pak bude nacházet jako součást vašeho seznamu roamingu, který vám umožní přístup k němu z libovolného počítače.

### <a name="experience-live-unit-testing"></a>Prostředí Live Unit Testing

V Visual Studio Enterprise 2017 poskytuje Live Unit Testing průběžné výsledky testování částí a pokrytí kódu v editoru při kódování. Funguje s C# a Visual Basic projekty pro .NET Framework i .NET Core a podporuje tři testovací rozhraní MSTest, XUnit a nunit.

![Live Unit Testing](media/lut-codewindow.png)

Další informace najdete v úvodu [Live Unit Testing](../test/live-unit-testing-intro.md). Seznam nových funkcí přidaných do každé verze Visual Studio Enterprise 2017 najdete v článku [novinky v Live Unit Testing](../test/live-unit-testing-whats-new.md).

### <a name="set-up-a-cicd-pipeline"></a>Nastavení kanálu CI/CD

#### <a name="automated-testing"></a>Automatizované testování

Automatizované testování je klíčovou součástí jakéhokoli DevOps kanálu. Umožňuje konzistentně a spolehlivě testovat a vydávat řešení v mnohem kratších cyklech. Toky CI/CD (průběžná integrace a průběžné doručování) můžou zlepšit efektivitu procesu.

Další informace o automatizovaných testech najdete v tomto blogovém příspěvku [v kanálu CI/CD pro automatizované testy](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/) .

Další informace o tom, co je nového v rozšíření [pro průběžné doručování pro Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) DevLabs, najdete v [článku potvrzení s jistotou: Příspěvek na blogu kvalita](https://devblogs.microsoft.com/visualstudio/committing-with-confidence-getting-code-quality-information-at-commit-time/) kódu pro čas potvrzení

### <a name="visual-studio-ide-enhancements"></a>Vylepšení integrovaného vývojového prostředí sady Visual Studio

#### <a name="multi-caret-editing"></a>Úpravy více blikajících kurzorů

**Novinka v 15,8**: Úpravy více umístění v souboru současně jsou nyní snadné. Začněte tím, že vytvoříte body vložení a výběry na více místech v souboru. Pak pomocí funkce pro úpravy více blikajících kurzorů udělejte stejnou úpravu ve dvou nebo více místech současně.

Další informace naleznete v části [Výběr více blikajících kurzorů](finding-and-replacing-text.md#multi-caret-selection) v [textové stránce najít a nahradit](finding-and-replacing-text.md) .

#### <a name="keep-keybinding-profiles-consistent"></a>Zachování profilů pro vytváření klíčů konzistentně

**Novinka v 15,8**: V současné době můžete své vazby klíčů udržovat v souladu s nástroji pomocí dvou nových profilů klávesnice: Visual Studio Code a reostřejšíer (Visual Studio). Tato schémata najdete v části**Možnosti** >  **nástrojů** > **Obecné** > **klávesnice** a horní rozevírací nabídka.

  ![Nové profily vazeb klíčů pro Visual Studio Code a reostřejší](media/vs-keyboard-mappings-code-resharper.png)

#### <a name="use-new-refactorings"></a>Použití nových refaktoringů

Refaktoring je proces vylepšení kódu po jeho zápisu. Refaktoring změní vnitřní strukturu kódu beze změny jeho chování. Nové refaktoringy se často přidávají; Tady je pár příkladů:

* Přidat parametr (z CallSite.)
* Generovat přepsání
* Přidat pojmenovaný argument
* Přidat kontrolu pro parametry null
* Vložit oddělovače číslic do literálů
* Změnit základ pro číselné literály (například hex na binární)
* Převést if-to-Switch
* Odebrat nepoužitou proměnnou

Další informace najdete v tématu [rychlé akce](common-quick-actions.md).

#### <a name="interact-with-git"></a>Interakce s Git

Když pracujete s projektem v sadě Visual Studio, můžete nastavit a rychle potvrdit a publikovat kód do služby Git. Úložiště Git můžete spravovat také pomocí kliknutí v nabídce v pravém dolním rohu integrovaného vývojového prostředí (IDE).

![Visual Studio 2017 komunikuje s dialogovým oknem Git](media/vsIDE-GitInteraction.png)

#### <a name="experience-improved-navigation-controls"></a>Vylepšené ovládací prvky pro navigaci

Aktualizovali jsme navigační prostředí, abychom vám pomohli získat od A do B větší jistotu a méně odčítání.

* **Novinka v 15,4**: **Přejít k definici** (**CTRL +** +**kliknutí** nebo **F12**) &ndash; uživatelé myši mají jednodušší způsob, jak přejít na definici člena stisknutím **klávesy CTRL** a následným kliknutím na člena. Stisknutí klávesy **CTRL** a najetí myší na symbol kódu se podtrhne a změní se na odkaz. Další informace najdete v tématu [Přechod k definici a náhled definice](go-to-and-peek-definition.md) .

* **Přejít k implementaci** (**CTRL**+**F12** )&ndash; přejděte z libovolného základního typu nebo člena k jeho různým implementům.

* **Přejít na vše** (**CTRL**+**T** neboCTRL+, )&ndash; přejděte přímo k libovolné deklaraci souboru/typu/členu nebo symbolu. Můžete filtrovat seznam výsledků nebo použít syntaxi dotazu (například "f searchTerm" pro soubory, "t searchTerm" pro typy atd.).

  ![Vylepšená funkce Přejít na vše](media/vs2017ide-navigation-go-to.png)

* **Najít všechny odkazy** (**SHIFT**+**F12** )&ndash; se zabarvou syntaxe můžete seskupit výsledky hledání všech odkazů podle kombinace projektu, definice a cesty. Můžete také "uzamknout" výsledky, abyste mohli dál najít další odkazy, aniž byste ztratili původní výsledky.

  ![Nový nástroj najít všechny odkazy](media/vs2017ide-find-all-references.png)

* **Vizualizér struktury** &ndash; Tečkované, šedé svislé čáry (vodítka odsazení) fungují jako orientační body v kódu pro zajištění kontextu v rámci vašeho zobrazení. Můžete je rozpoznat z oblíbených nástrojů pro zvýšení produktivity. Můžete je použít k vizualizaci a zjištění, který blok kódu máte kdykoli, aniž byste museli posouvat. Po najetí myší na tyto řádky se zobrazí popis, který ukazuje otevření tohoto bloku a jeho rodičů. Je k dispozici pro všechny jazyky podporované pomocí gramatik TextMate a také C#Visual Basic a XAML.

  ![Vizualizér struktury sady Visual Studio 2017](media/vsIDE-StructureVisualizer.png)

Další informace o nových funkcích produktivity naleznete v [tématu Visual Studio 2017: Příspěvek na blogu o produktivitě](https://devblogs.microsoft.com/visualstudio/visual-studio-2017-productivity-performance-and-partners/) , výkonu a partnerech

### <a name="visual-c"></a>Visual C++

V aplikaci Visual Studio uvidíte několik vylepšení, jako je například distribuce C++ základních pokynů se sadou Visual Studio, aktualizace kompilátoru přidáním vylepšené podpory pro c++ 11 a C++ funkce a přidání a aktualizace funkcí v C++ Knihovna. Vylepšili jsme také výkon C++ IDE, instalační úlohy a další.

Také jsme opravili více než 250 chyb a nahlásili problémy v kompilátoru a nástrojích, mnoho odeslaných zákazníky prostřednictvím [ C++komunity vývojářů ]pro (https://developercommunity.visualstudio.com/spaces/62/index.html "vývojářskou C++komunitu pro vývojáře ").

Úplné podrobnosti najdete na stránce [co je nového pro vizuál C++ na stránce Visual 2017](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio) .

### <a name="debugging-and-diagnostics"></a>Ladění a diagnostika

#### <a name="run-to-click"></a>Běžet do kliknutí

Nyní můžete snadněji přeskočit před laděním bez nastavení zarážky, která se má zastavit na požadovaném řádku. Když jste v ladicím programu zastavili, stačí kliknout na ikonu, která se zobrazí vedle řádku kódu. Váš kód se spustí a zastaví se na tomto řádku při příštím spuštění v cestě kódu.

![Ladění sady Visual Studio 2017 – spuštění pro kliknutí](media/vs2017ide-RunToClick.png)

#### <a name="the-new-exception-helper"></a>Nová pomocná rutina výjimky

Nový Pomocník pro výjimky vám pomůže rychle zobrazit informace o výjimce. Informace se zobrazí v kompaktní formě s okamžitým přístupem k vnitřním výjimkám. Při diagnostikování NullReferenceException můžete rychle zjistit, co mělo hodnotu null, přímo v Pomocníkovi výjimky.

![Nové dialogové okno pomocníka výjimky v aplikaci Visual Studio](media/vs2017ide-ExceptionHelper.png)

Další informace najdete v příspěvku na blogu o [použití nového pomocníka výjimky v rámci sady Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/) .

#### <a name="snapshots-and-intellitrace-step-back"></a>Snímky a IntelliTrace krok zpátky

**Novinka v 15,5**: Zpětného kroku IntelliTrace automaticky vytvoří snímek vaší aplikace v každé zarážce a ladicí program krok události. Zaznamenané snímky umožňují snadno vrátit k předchozím zarážkám nebo krokům a zobrazit stav aplikace jako v minulosti. IntelliTrace zpětným krokem vám může ušetřit čas při chcete zobrazit předchozí stav aplikace, ale nebudete chtít znovu spusťte ladění nebo znovu vytvořit stav požadované aplikace.

Snímky můžete procházet a zobrazovat pomocí tlačítek **krok zpět** a **krok vpřed** na panelu nástrojů **ladění** . Tato tlačítka přecházejí na události, které se zobrazí na kartě **události** v okně **diagnostické nástroje** . Krok zpět nebo dopředu události automaticky aktivuje historické ladění u vybrané události.

![Nové dialogové okno pomocníka výjimky v aplikaci Visual Studio](../debugger/media/intellitrace-step-back-icons-description.png  "Krokovat tlačítka zpět a dopředu")

Další informace najdete na stránce pro [zobrazení snímků pomocí IntelliTraceho kroku](../debugger/view-historical-application-state.md) .

### <a name="containerization"></a>Rozdělení do kontejnerů

Kontejnery poskytují zvýšenou hustotu aplikací a nižší náklady na nasazení společně s vyšší produktivitou a DevOps flexibilitou.

#### <a name="docker-container-tooling"></a>Nástroje kontejneru Docker

**Novinka v 15,5**:

* Visual Studio obsahuje nástroje pro kontejnery Docker, které teď podporují fázemi s více fázemi, které zjednodušují vytváření optimalizovaných imagí kontejnerů.
* Když otevřete projekt, který podporuje Docker, bude Visual Studio ve výchozím nastavení automaticky vyžadovat, sestavovat a spouštět nezbytné kontejnerové image na pozadí. Tuto funkci můžete vypnout pomocí nastavení **Automaticky spustit kontejnery na pozadí** v sadě Visual Studio.

## <a name="cloud-app-development-with-azure"></a>Vývoj cloudových aplikací v Azure

### <a name="azure-functions-tools"></a>Nástroje Azure Functions

V rámci úlohy "vývoj pro Azure" jsme zahrnuli nástroje, které vám pomůžou s vývojem Azure Functions pomocí předem C# kompilovaných knihoven tříd. Teď můžete vytvářet, spouštět a ladit na místním vývojovém počítači a pak je publikovat přímo do Azure ze sady Visual Studio.

Další informace naleznete na stránce [Azure Functions Tools for Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-develop-vs) .

### <a name="debug-live-aspnet-apps-using-snappoints-and-logpoints-in-live-azure-applications"></a>Ladění živých aplikací ASP.NET pomocí snímkovací body a protokolovacích bodů v živých aplikacích Azure

**Novinka v 15,5**: Snapshot Debugger pořizování snímku vašich aplikací v produkčním prostředí, když máte spuštěný kód. Dáte pokyn, aby ladicí program k vytvoření snímku, můžete nastavit snímkovací a protokolovací body ve vašem kódu. Ladicí program umožňuje zobrazit přesně toho, co nefunguje, aniž by to ovlivnilo provozu aplikace v produkčním prostředí. Snapshot Debugger můžete výrazně zkrátit čas potřebný k vyřešení problémů, ke kterým dochází v produkčním prostředí.

Shromažďování snímků je k dispozici pro následující web apps ve službě Azure App Service:

* Aplikace ASP.NET spuštěné na rozhraní .NET Framework 4.6.1 nebo novější.
* Aplikace ASP.NET Core na .NET Core 2.0 nebo novější na Windows.

Další informace najdete v tématu [ladění živých aplikací ASP.NET pomocí snímkovací body a protokolovacích bodů](../debugger/debug-live-azure-applications.md).

## <a name="windows-app-development"></a>Vývoj aplikací pro systém Windows

### <a name="universal-windows-platform"></a>Univerzální platforma pro Windows

Univerzální platforma Windows (UWP) je aplikační platforma pro Windows 10. Můžete vyvíjet aplikace pro UWP s jenom jednou sadou rozhraní API, jedním balíčkem aplikace a jedním obchodem pro všechna zařízení &ndash; s Windows 10 PC, tablet, telefon, Xbox, HoloLens, Surface Hub a další. UWP podporuje různé velikosti obrazovky a různé modely interakce, ať už se jedná o dotykové ovládání, myš a klávesnici, herní kontroler nebo pero. V jádru aplikací pro UWP je to, že uživatelé chtějí, aby byli mobilními zařízeními na všech svých zařízeních a aby chtějí používat zařízení, které je pro úkol nejpohodlnější nebo produktivní.

![Univerzální platforma pro Windows](../cross-platform/media/uwp_coreextensions.png)

Vyberte preferovaný vývojový jazyk&mdash;z C#, Visual Basic, C++nebo JavaScript&mdash;a vytvořte univerzální platforma Windows aplikaci pro zařízení s Windows 10. Visual Studio 2017 poskytuje šablonu aplikace UWP pro každý jazyk, který umožňuje vytvořit jeden projekt pro všechna zařízení. Po dokončení práce můžete balíček aplikace vyvolat a odeslat ho Microsoft Store ze sady Visual Studio, aby bylo možné aplikaci zákazníkům na jakémkoli zařízení s Windows 10 získat na maximum.

**Novinka v 15,5**: Sada Visual Studio 2017 verze 15,5 poskytuje nejlepší podporu pro Windows 10 (10.0.16299.0). Aktualizace Creators pro Windows 10 přináší také mnoho vylepšení pro vývojáře UWP. Tady jsou některé z největších změn: 

* **Podpora pro .NET Standard 2,0**<br/>Kromě zjednodušeného nasazení aplikace je aktualizace Windows 10 na základě Creators Update první verzí Windows 10, která poskytuje podporu .NET Standard 2,0. Efektivně [.NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/) je referenční implementace základní knihovny tříd, kterou může implementovat jakákoli platforma .NET. Cílem .NET Standard je umožnit vývojářům v rozhraní .NET sdílet kód napříč libovolnou platformou .NET, na které se rozhodne pracovat.
* **Nejlepší z obou UWP i z Win32**<br/>Vylepšili jsme platformu Windows 10 s využitím [stolního mostu](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-root) , aby Windows 10 bylo lépe pro všechny vývojáře v rozhraní .NET, ať už se jedná o aktuální fokus na UWP, WPF, model Windows Forms nebo Xamarin. S novým typem projektu balení aplikace ve Visual Studiu 2017 verze 15,5 můžete vytvářet balíčky aplikací pro Windows pro projekty WPF nebo model Windows Forms, stejně jako u projektů UWP. Po zabalení aplikace získáte všechny výhody nasazení aplikace pro Windows 10 a budete mít možnost distribuovat je prostřednictvím Microsoft Store (u zákaznických aplikací) nebo Microsoft Store pro firmy a vzdělávání. Vzhledem k tomu, že zabalené aplikace mají přístup k plnému povrchu rozhraní API UWP i k rozhraní Win32 API na ploše, teď můžete modernizovat své aplikace WPF a model Windows Forms postupně s rozhraními API UWP a funkcemi Windows 10. Kromě toho můžete zahrnout komponenty Win32 do vašich aplikací pro UWP, které se rozsvítí na ploše se všemi možnostmi Win32.

Další informace o UWP najdete na stránce [vývoj aplikací pro Univerzální platforma Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md) .

## <a name="mobile-app-development"></a>Vývoj mobilních aplikací

### <a name="xamarin"></a>Xamarin

V rámci úlohy "vývoj pro mobilní zařízení v .NET" můžou vývojáři, kteří C#znají, .NET a Visual Studio, poskytovat nativní aplikace pro Android, iOS a Windows pomocí Xamarin. Vývojáři můžou využít stejný výkon a produktivitu při práci s Xamarin pro mobilní aplikace, včetně vzdáleného ladění na zařízeních&mdash;s Androidem, iOS a Windows, aniž by se museli učit jazyky nativního kódování, jako je například cíl-C nebo Java.

Další informace naleznete na stránce sady [Visual Studio a Xamarin](/xamarin/) .

### <a name="entitlements-editor"></a>Editor oprávnění

**Novinka v 15,3**: Pro potřeby vývoje pro iOS jsme přidali samostatného editora oprávnění. Zahrnuje uživatelsky přívětivé uživatelské rozhraní, které lze snadno procházet. Pokud ho chcete spustit, poklikejte na váš soubor s *oprávněním. plist* .

![Editor nároků pro Xamarin](media/xamarin-entitlements-editor.png)

### <a name="visual-studio-tools-for-xamarin"></a>Nástroje sady Visual Studio pro Xamarin

**Novinka v 15,4**: Xamarin Live umožňuje vývojářům nepřetržitě nasazovat, testovat a ladit své aplikace přímo na zařízeních se systémy iOS a Android. Po stažení Xamarin Live Player&mdash;k dispozici v App Storu nebo na Google Play&mdash;můžete spárovat své zařízení se sadou Visual Studio a revolučním způsobem způsob, jak sestavovat mobilní aplikace. Tato funkce je teď zahrnutá v sadě Visual Studio a jde povolit v nabídce **Nástroje** > **Možnosti** > **Xamarin** > **Jiné** > **Povolit Xamarin Live Player**.

![Animace režimů párování Xamarin Live Player, nasazení a živých úprav](media/xamarinliveplayer.gif)

### <a name="support-for-google-android-emulator"></a>Podpora pro Google Android Emulator

**Novinka v 15,8**: Pokud používáte Hyper-V, můžete teď používat Android Emulator Google souběžně s jinými technologiemi, které jsou založené na technologii Hyper-v, jako jsou virtuální počítače Hyper-V, nástroj Docker, emulátor HoloLens a další. (Tato funkce vyžaduje Windows 10 duben 2018 Update nebo novější.)

![Emulátor Google Android na technologiích Hyper-V](media/xamarin-hyperv-android-emulator.png)

#### <a name="xamarinandroid-designer-split-view-editor"></a>Editor s rozděleným zobrazením Xamarin. Android Designer

**Novinka v 15,8**: Výrazně jsme vylepšili možnosti návrháře pro Xamarin. Android. Zvýraznění je nový editor s rozděleným zobrazením, který umožňuje vytvářet, upravovat a zobrazovat náhled rozložení ve stejnou dobu.

![Editor programu Xamarin. Adroid Designer rozděleného – zobrazení](media/android-designer-split-view.png)

Další informace najdete v tématu [hardwarová akcelerace pro výkon emulátoru](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin) .

### <a name="visual-studio-app-center"></a>Visual Studio App Center

**Novinka v 15,5**: Visual Studio App Center&mdash;, která je teď všeobecně dostupná pro aplikace&mdash;pro Android, iOS, MacOS a Windows, má všechno, co potřebujete ke správě životního cyklu aplikací, včetně automatizovaných buildů, testování na skutečných zařízeních v cloudu, distribuce do testerů beta verzí a do obchodů s aplikacemi a monitorování reálného využití prostřednictvím dat o chybách a analýzách. Aplikace napsané v objektivech, které jsou v cíli C#– C, SWIFT, Java,, Xamarin a reagují na nativní, jsou podporované napříč všemi funkcemi.

  ![Visual Studio App Center testovací prostředí](media/app-center-test-env.png)

Další informace najdete v [úvodu App Center: Sestavujte, testujte, distribuujte a sledujte aplikace](https://blogs.msdn.microsoft.com/vsappcenter/introducing-visual-studio-app-center/) v blogovém příspěvku o cloudu.

## <a name="cross-platform-development"></a>Vývoj pro různé platformy

### <a name="redgate-data-tools"></a>Nástroje pro data Redgate

Pro rozšiřování funkcí DevOps na vývoj databází SQL Server jsou nyní dostupné nástroje Redgate Data Tools v aplikaci Visual Studio.

Součástí sady Visual Studio 2017 Enterprise:

* [Redgate ReadyRoll Core](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) vám pomůže s vývojem skriptů migrace, správou změn databáze pomocí správy zdrojového kódu a bezpečnou automatizací nasazení SQL serverch změn databáze společně se změnami aplikací.
* [REDGATE SQL Prompt Core](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) vám pomůže psát SQL rychleji a přesněji pomocí inteligentního dokončování kódu. SQL Prompt automaticky dokončuje databázové a systémové objekty a klíčová slova a během psaní nabízí návrhy sloupců. Výsledkem je čisticí kód a méně chyb, protože nemusíte pamatovat každý název sloupce nebo alias.

Součástí všech edicí sady Visual Studio 2017:

* [REDGATE SQL Search](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) zvyšuje vaši produktivitu tím, že vám pomůže rychle najít fragmenty a objekty SQL napříč více databázemi.

Další informace najdete v blogovém příspěvku [nástroje Redgate Data Tools v aplikaci Visual Studio 2017](https://devblogs.microsoft.com/visualstudio/redgate-data-tools-in-visual-studio-2017/) .

### <a name="net-core"></a>.NET Core

.NET Core je univerzální účelem, modulární, pro více platforem a implementace open source .NET Standard a obsahuje mnoho stejných rozhraní API jako .NET Framework.

Platforma .NET Core se skládá z několika komponent, které zahrnují spravované kompilátory, modul runtime, knihovny základních tříd a řadu modelů aplikací, například ASP.NET Core. .NET Core podporuje tři hlavní operační systémy: Windows, Linux a macOS. .NET Core můžete používat v scénářích zařízení, cloudu a integrovaných a IoT.

A teď zahrnuje podporu Docker.

**Novinka v 15,3**: Visual Studio 2017 verze 15,3 podporuje vývoj pro .NET Core 2,0. Použití .NET Core 2,0 vyžaduje samostatně stažení a instalaci sady .NET Core 2,0 SDK.

Další informace najdete na stránce [Průvodce .NET Core](/dotnet/core/index) .

## <a name="games-development"></a>Vývoj her

### <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity

V rámci úlohy "vývoj her pro Unity" jsme zahrnuli nástroje, které vám pomůžou vyvíjet různé platformy pro vytváření 2D a 3D her a interaktivního obsahu. Pomocí sady Visual Studio 2017 a Unity 5,6 můžete vytvořit jednou a publikovat na 21 platformách, včetně všech mobilních platforem, WebGL, počítačů Mac, počítačů a počítačů se systémem Linux, webu nebo konzol.

Další informace najdete na stránce [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) .

## <a name="ai-development"></a>Vývoj AI

### <a name="visual-studio-tools-for-ai"></a>Visual Studio Tools for AI

**Novinka v 15,5**: Využijte funkce produktivity sady Visual Studio k urychlení inovací AI ještě dnes. Používejte integrované funkce editoru kódu, jako je zvýrazňování syntaxe, IntelliSense a automatické formátování textu. V místním prostředí můžete interaktivně testovat aplikaci hloubkového učení pomocí podrobného ladění místních proměnných a modelů.

  ![IDE pro hloubkové učení](../ai/media/about/ide.png)

Další informace najdete na stránce [Visual Studio Tools for AI](../ai/about-ai-tools.md) .

## <a name="whats-next"></a>Co dál

Visual Studio 2017 aktualizujeme často o nové funkce, které můžou zlepšit vývojové prostředí. Tady je rekapitulace některých našich nejvýznamnějších aktualizací, které jsou v experimentální verzi Preview:

* **[Live Share](https://visualstudio.microsoft.com/services/live-share/)** nový nástroj, který umožňuje sdílet základ kódu a jeho kontext s společník a získat rychlou obousměrnou spolupráci přímo v rámci sady Visual Studio. Pomocí Live Share může společník číst, Procházet, upravovat a ladit projekt, který s nimi sdílíte, a dělat plynule a bezpečně.<br><br>Další informace najdete v části [Nejčastější dotazy k Live Share](/visualstudio/liveshare/faq).<br><br>
* **[IntelliCode](https://visualstudio.microsoft.com/services/intellicode/)** , což je nová funkce, která vylepšuje vývoj softwaru pomocí AI a poskytuje lepší kontextové dokončování kódu, pomáhají vývojářům vytvářet kód ke vzorům a stylům jejich týmu, vyhledávat obtížně zachytávání kódu a soustředit kód. kontroluje oblasti, které jsou ve skutečnosti. <br><br>Další informace najdete v tématu [IntelliCode – Nejčastější dotazy](/visualstudio/intellicode/faq).

Chcete získat další informace o tom, co je jinde v sadě Works for Visual Studio 2017? Podívejte se na stránku s plánem sady [Visual Studio](/visualstudio/productinfo/vs2018-roadmap) .

A nezapomeňte si zaregistrovat naši nejnovější verzi, [Visual Studio 2019](whats-new-visual-studio-2019.md).

## <a name="contact-us"></a>Kontaktujte nás

Proč odeslat zpětnou vazbu týmu sady Visual Studio? Protože jsme vážně trvat zpětné vazby od zákazníků. To zahrnuje mnoho toho, co máme.

Pokud si chcete udělat nějaké informace o tom, jak můžeme vylepšit aplikaci Visual Studio, nebo si přečtěte další informace o možnostech podpory produktu, přečtěte si prosím stránku [poslat nám svůj názor](feedback-options.md) .

### <a name="report-a-problem"></a>Nahlášení problému

V některých případech není zpráva dostatečně velká, aby mohla předávat úplný dopad zjištěného problému. Pokud dojde k zablokování, zhroucení nebo jinému problému s výkonem, můžete s námi snadno sdílet reprodukci kroky a podpůrné soubory (například snímky obrazovky a soubory s výpisem paměti a výpisu haldy) pomocí nástroje **nahlásit problém** . Další informace o tom, jak tento nástroj použít, naleznete na stránce [postup nahlášení problému](how-to-report-a-problem-with-visual-studio.md) .

## <a name="see-also"></a>Viz také:

* [Zpráva k vydání verze pro Visual Studio 2017](/visualstudio/releasenotes/vs2017-relnotes)
* [Novinky v sadě Visual Studio 2017 SDK](/visualstudio/extensibility/what-s-new-in-the-visual-studio-2017-sdk)
* [Co je nového v jazyce VisualC++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Co je nového v jazyce C#](/dotnet/csharp/whats-new)
* [Co je nového pro Team Foundation Server](/tfs/server/whats-new?view=vsts)
* [Co je nového v Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
* [Co je nového v aplikaci Visual Studio 2019](whats-new-visual-studio-2019.md)
