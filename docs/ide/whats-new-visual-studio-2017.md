---
title: Novinky v sadě Visual Studio 2017
titleSuffix: ''
description: Přečtěte si o nových funkcích visual studia 2017.
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
ms.openlocfilehash: de26054894783df283d38223a59741c0500d0bc5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74955033"
---
# <a name="whats-new-in-visual-studio-2017"></a>Novinky v sadě Visual Studio 2017

**Aktualizováno pro [verzi 15.9](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)**

Chcete upgradovat z předchozí verze sady Visual Studio? Tady je to, co vám Visual Studio 2017 může nabídnout: Bezkonkurenční produktivita pro všechny dva problémy s aplikací, jakoukoli aplikací a jakoukoli platformou. Visual Studio 2017 slouží k vývoji aplikací pro Android, iOS, Windows, Linux, web a cloud. Svůj kód můžete rychle psát, snadno ladit a diagnostikovat, často testovat a bez obav vydávat. Navíc si můžete sadu Visual Studio rozšířit a přizpůsobit pomocí svých vlastních rozšíření. Používejte správu verzí, buďte agilní a efektivně spolupracujte s touto verzí!

>[!div class="button"]
>[Stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

Tady je rekapitulace změn, které byly provedeny od předchozí verze Visual Studia 2015:

* **[Předefinované základy](#redefined-fundamentals)**. Nové prostředí instalace znamená, že můžete instalovat rychleji a nainstalovat, co chcete, když to potřebujete.
* **[Výkon a produktivita](#performance-and-productivity)**. Zaměřili jsme se na nové a moderní funkce pro vývoj mobilních zařízení, cloudu a stolních počítačů. A Visual Studio se spustí rychleji, je citlivější a používá méně paměti než dříve.
* **[Vývoj cloudových aplikací s Azure](#cloud-app-development-with-azure)**. Integrovaná sada nástrojů Azure vám umožní snadno vytvářet aplikace na prvním místě v cloudu využívající Microsoft Azure. Visual Studio usnadňuje konfiguraci, sestavení, ladění, balení a nasazení aplikací a služeb v Azure.
* **[Vývoj aplikací pro Windows](#windows-app-development)**. Pomocí šablon UPW ve Visual Studiu 2017 můžete vytvořit jeden &ndash; projekt pro všechna zařízení s Windows 10, počítačem, tabletem, telefonem, Konzolí Xbox, HoloLens, Surface Huba a dalšími.
* **[Vývoj mobilních aplikací](#mobile-app-development)**. Inovujte a získejte rychle výsledky s Xamarinem, který sjednocuje vaše mobilní požadavky na více platformách na jeden základní základ kódu a sadu dovedností.
* **[Vývoj napříč platformami](#cross-platform-development)**. Bezproblémově doručujte software na libovolnou cílovou platformu. Rozšiřte procesy DevOps na SQL Server prostřednictvím redgate datových nástrojů a bezpečně automatizujte nasazení databází z visual studia. Nebo použijte .NET Core k zápisu aplikací a knihoven, které běží nezměněné v operačních systémech Windows, Linux a macOS.
* **[Vývoj her](#games-development)**. Pomocí Visual Studio Tools for Unity (VSTU) můžete pomocí Visual Studia psát skripty her a editorů v jazyce C# a pak použít jeho výkonný ladicí program k vyhledání a opravě chyb.
* **[Vývoj umělá ai](#ai-development)**. Pomocí nástrojů Visual Studio pro umělou přípravu můžete pomocí funkcí pro zvýšení produktivity sady Visual Studio urychlit inovace ai. Vytvářejte, testujte a nasazujte řešení deep learningu / AI, která se bezproblémově integrují s Azure Machine Learning a vytvářejí robustní experimentální funkce.

> [!NOTE]
> Úplný seznam nových funkcí a funkcí v Sadě Visual Studio 2017 najdete v [aktuálních poznámkách k verzi](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017). A podívejte se na budoucí nabídky funkcí, podívejte se na [poznámky k verzi Preview](/visualstudio/releasenotes/vs2017-preview-relnotes?context=visualstudio/default&contextView=vs-2017).

Tady najdete podrobnější informace o některých nejdůležitějších vylepšeních a nových funkcích visual studia 2017.

## <a name="redefined-fundamentals"></a>Nově definované základy

### <a name="a-new-setup-experience"></a>Nové prostředí nastavení

Visual Studio usnadňuje a zrychluje instalaci pouze funkcí, které potřebujete, když je potřebujete. A odinstaluje se také čistě.

Nejdůležitější změnou, kterou je třeba si uvědomit při instalaci sady Visual Studio, je nové prostředí instalace. Na kartě **Úlohy** uvidíte možnosti instalace, které jsou seskupeny tak, aby představovaly běžné architektury, jazyky a platformy. Pokrývá vše od vývoje desktopů .NET až po vývoj aplikací Jazyka C++ ve Windows, Linuxu a iOS.

Vyberte úlohy, které potřebujete, a změňte je, když potřebujete.

![Dialogové okno nastavení Visual Studia 2017](../install/media/install-visual-studio-enterprise.png)

A máte také možnosti doladění instalace:

* Chcete si vybrat vlastní součásti místo použití úloh? V instalačním programu **vyberte** kartu Jednotlivé součásti.
* Chcete nainstalovat jazykové sady, aniž byste museli měnit možnost jazyka Windows? Zvolte kartu **Jazykové balíčky** instalačního programu.
* **Novinka v 15.7**: Chcete změnit umístění, kde se visual studio instaluje? Zvolte kartu **Možnosti instalace** instalačního programu.

Další informace o novém prostředí instalace, včetně podrobných pokynů, které vás provedou, najdete na stránce [Instalace sady Visual Studio.](../install/install-visual-studio.md)

### <a name="a-focus-on-accessibility"></a>Zaměření na přístupnost

**Novinkou v 15.3**jsme provedli více než 1 700 cílených oprav, abychom zlepšili kompatibilitu mezi visual studio a asistenčními technologiemi, které používá mnoho zákazníků. Existují desítky scénářů, které jsou více kompatibilní s programy pro čtení z obrazovky, motivy s vysokým kontrastem a dalšími asistenčními technologiemi než kdykoli předtím. Ladicí program, editor a shell mají také významné zlepšení.

Další informace najdete [ve zlepšení usnadnění v visual studiu 2017 verze 15.3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) blogu.

## <a name="performance-and-productivity"></a>Výkon a produktivita

### <a name="sign-in-across-multiple-accounts"></a>Přihlášení na více účtech

Ve Visual Studiu jsme zavedli novou službu identit, která umožňuje sdílet uživatelské účty napříč Průzkumníkem týmu, nástroji Azure, publikováním v Microsoft Storu a dalšími akcemi.

Můžete zůstat přihlášeni i déle. Visual Studio vás nebude žádat o přihlášení každých 12 hodin. Další informace najdete v tématu [Méně přihlášení Visual Studio výzvy k zobrazení](https://devblogs.microsoft.com/visualstudio/fewer-visual-studio-sign-in-prompts/) blogu.

### <a name="start-visual-studio-faster"></a>Rychlejší spuštění sady Visual Studio

Nové Visual Studio Performance Center vám může pomoci optimalizovat čas spuštění ide. Centrum výkonnosti obsahuje seznam všech rozšíření a oken nástrojů, které mohou zpomalit spuštění prostředí IDE. Můžete ji použít ke zlepšení výkonu při spuštění určením, kdy rozšíření start nebo zda jsou okna nástrojů otevřena při spuštění.

### <a name="faster-on-demand-loading-of-extensions"></a>Rychlejší načítání rozšíření na vyžádání

Visual Studio přesouvá jeho rozšíření (a práce s rozšířeními třetích stran příliš) tak, aby načítat na vyžádání, nikoli při spuštění ide. Zajímá vás, která rozšíření ovlivňují výkon při spuštění, zatížení řešení a psaní? Tyto informace naleznete v **nápovědě ke** > **správě výkonu sady Visual Studio**.

  ![Dialogové okno Možnosti v Sadě Visual Studio 2017](media/vs2017ide-manage-vs-perf.png)

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Správa rozšíření pomocí Správce roamingových rozšíření

Je jednodušší nastavit každé vývojové prostředí s oblíbenými rozšířeními při přihlášení k sadě Visual Studio. Nový Správce roamingových rozšíření sleduje všechna vaše oblíbená rozšíření vytvořením synchronizovaného seznamu v cloudu.

Pokud chcete zobrazit seznam rozšíření v sadě Visual Studio, klikněte na **Položku Rozšíření o nástroje** > **& aktualizace**a potom klikněte na Správce **roamingových rozšíření**.

![Visual Studio 2017 – dialogové okno Rozšíření a aktualizace](media/vs2017ide-extensions-and-updates.png)

Správce roamingových rozšíření sleduje všechna rozšíření, která nainstalujete, ale můžete si vybrat, která z nich chcete přidat do seznamu roamingu.

![Visual Studio 2017 – dialogové okno Rozšíření a aktualizace](media/vs2017ide-RoamingExtensionManager.png)

Při použití Správce roamingových rozšíření jsou v seznamu tři typy ikon:

* ![Ikona roamingu](media/vs2017ide-roamedicon.png) **_:_** Rozšíření, které je součástí tohoto seznamu roamingu, ale není v počítači nainstalováno.
  (Můžete je nainstalovat pomocí tlačítka **Stáhnout.)**
* ![Roaming & Nainstalované](media/vs2017ide-roamedinstalledicon.png) ikony **_se & nainstalován:_** Všechna rozšíření, která jsou součástí tohoto seznamu roamingu a nainstalována ve vašem prostředí pro vlastní prostředí.
  (Pokud se rozhodnete, že se nechcete toulat, můžete je odebrat pomocí tlačítka **Zastavit roaming.)**
* ![Nainstalovaná](media/vs2017ide-installedicon.png) **_Installed_** ikona : Všechna rozšíření, která jsou nainstalována v tomto prostředí, ale nejsou součástí seznamu roamingu.
  (Rozšíření do seznamu roamingu můžete přidat pomocí tlačítka **Spustit roaming.)**

Všechna rozšíření, která stáhnete při přihlášení, budou přidána do seznamu jako **přebujel & nainstalována**. Rozšíření se pak stane součástí seznamu roamingu, který vám umožní přístup k němu z libovolného počítače.

### <a name="experience-live-unit-testing"></a>Vyzkoušejte živé testování částí

V sadě Visual Studio Enterprise 2017 živé testování částí poskytuje výsledky testů živých částí a pokrytí kódu v editoru při kódování. Pracuje s c# a visual basic projekty pro rozhraní .NET Framework a .NET Core a podporuje tři testovací architektury MSTest, xUnit a NUnit.

![Live Unit Testing](media/lut-codewindow.png)

Další informace naleznete [v tématu Introducing Live Unit Testing](../test/live-unit-testing-intro.md). Seznam nových funkcí přidaných v každé verzi Visual Studia Enterprise 2017 najdete v tématu [Co je nového v živém testování částí](../test/live-unit-testing-whats-new.md).

### <a name="set-up-a-cicd-pipeline"></a>Nastavení kanálu CI/CD

#### <a name="automated-testing"></a>Automatizované testování

Automatizované testování je klíčovou součástí každého kanálu DevOps. To vám umožní důsledně a spolehlivě testovat a uvolňovat řešení v mnohem kratších cyklech. Toky CI/CD (Průběžná integrace a průběžné doručování) mohou pomoci zefektivnit proces.

Další informace o automatizovaných testech najdete v [kanálu CI/CD pro automatizované testy v blogu DevOps.](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/)

A další informace o tom, co je nového v [průběžném doručování nástroje pro Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) DevLabs rozšíření, najdete v tématu Potvrzení s [jistotou: Potvrzení kódu času kvalitní](https://devblogs.microsoft.com/visualstudio/committing-with-confidence-getting-code-quality-information-at-commit-time/) blog post.

### <a name="visual-studio-ide-enhancements"></a>Vylepšení ide sady Visual Studio

#### <a name="multi-caret-editing"></a>Úpravy s více kurzory

**Novinka v 15.8**: Úprava více míst v souboru, současně, je nyní snadné. Začněte vytvořením kurzorových bodů a výběrů na více místech v souboru. Potom použijte funkci úprav více stříšky, abyste stejnou úpravu upravili na dvou nebo více místech současně.

Další informace naleznete v části [Výběr více stříšky](finding-and-replacing-text.md#multi-caret-selection) na textové stránce [Najít a nahradit.](finding-and-replacing-text.md)

#### <a name="keep-keybinding-profiles-consistent"></a>Udržujte profily vazby kláves konzistentní

**Novinka v 15.8**: Nyní můžete udržovat své klíče konzistentní napříč nástroji se dvěma novými profily klávesnice: Visual Studio Code a ReSharper (Visual Studio). Tato schémata najdete v části Obecné**klávesnice** **General** > **s možnostmi** >  **nástrojů** > a v hlavní rozevírací nabídce.

  ![Nové profily keybinding pro Visual Studio Code a ReSharper](media/vs-keyboard-mappings-code-resharper.png)

#### <a name="use-new-refactorings"></a>Použití nových refaktoringů

Refaktoring je proces zlepšení kódu po jeho napsání. Refaktoring změní vnitřní strukturu kódu beze změny jeho chování. Často přidáváme nové refaktoringy; Zde je jen několik:

* Přidat parametr (z CallSite)
* Generovat lokální změny
* Přidat pojmenovaný argument
* Přidat kontrolu null parametrů
* Vložení oddělovačů číslic do literál
* Změnit základ pro číselné literály (například hex na binární)
* Převést přepnutí
* Odebrat nepoužitou proměnnou

Další informace naleznete v tématu [Rychlé akce](common-quick-actions.md).

#### <a name="interact-with-git"></a>Interakce s Gitem

Při práci s projektem v sadě Visual Studio můžete nastavit a rychle potvrdit a publikovat kód do služby Git. Úložiště Git můžete také spravovat pomocí kliknutí na nabídku z tlačítek v pravém dolním rohu rozhraní IDE.

![Visual Studio 2017 spolupracuje s dialogem Git](media/vsIDE-GitInteraction.png)

#### <a name="experience-improved-navigation-controls"></a>Zlepšené navigační ovládací prvky

Aktualizovali jsme navigační prostředí, které vám pomůže dostat se z a do b s větší jistotou a menším rozptylováním.

* **Novinka v 15.4**: **Přejít na definici** **(Ctrl**+**click** nebo **F12)** &ndash; Uživatelé myši mají jednodušší způsob, jak přejít na definici člena stisknutím **klávesy Ctrl** a následným kliknutím na člen. Stisknutím **klávesy Ctrl** a najetím na symbol kódu jej podtrhnete a převedete na odkaz. Další informace najdete [v tématu Přejít na definici a náhled.](go-to-and-peek-definition.md)

* **Přejít na implementaci** **(Ctrl**+**F12**) &ndash; Přejděte z libovolného základního typu nebo člena na jeho různé implementace.

* **Přejít na vše** **(Ctrl**+ &ndash; **T** nebo **Ctrl**+**,**) Přejděte přímo na libovolnou deklaraci souboru/typu/člena/symbolu. Můžete filtrovat seznam výsledků nebo použít syntaxi dotazu (například "f searchTerm" pro soubory, "t searchTerm" pro typy atd.).

  ![Vylepšené přejít na všechny](media/vs2017ide-navigation-go-to.png)

* **Najít všechny odkazy** **(Shift**+**F12)** &ndash; Pomocí zbarvení syntaxe můžete seskupit výsledky hledání všech odkazů podle kombinace projektu, definice a cesty. Můžete také "zamknout" výsledky, takže můžete pokračovat v hledání dalších odkazů bez ztráty původních výsledků.

  ![Nový nástroj Najít všechny reference](media/vs2017ide-find-all-references.png)

* **Struktura Vizualizér** &ndash; Tečkované, šedé svislé čáry (odsazení vodítka) fungují jako orientační body v kódu, aby poskytly kontext v rámci vašeho pohledu. Můžete je poznat z populárních nástrojů pro zvýšení produktivity. Můžete je použít k vizualizaci a zjištění, v jakém bloku kódu se právě vizujete, aniž byste museli posouvat. Když nařádky najedete přes řádky, zobrazí se popisek, který zobrazuje otevření tohoto bloku a jeho nadřazených položek. Je k dispozici pro všechny jazyky podporované prostřednictvím gramatikY TextMate, stejně jako C#, Visual Basic a XAML.

  ![Vizualizér struktury Visual Studio 2017](media/vsIDE-StructureVisualizer.png)

Další informace o nových funkcích produktivity najdete v příspěvku na blogu [Visual Studia 2017: Produktivita, Výkon a Partneři.](https://devblogs.microsoft.com/visualstudio/visual-studio-2017-productivity-performance-and-partners/)

### <a name="visual-c"></a>Visual C++

V sadě Visual Studio uvidíte několik vylepšení, jako je distribuce základních pokynů pro C++ s Visual Studio, aktualizace kompilátoru přidáním rozšířené podpory pro funkce C++ 11 a C++ a přidání a aktualizace funkcí v knihovnách C++. Také jsme vylepšili výkon prostředí C++ IDE, instalačníúlohy a další.

Také jsme opravili více než 250 chyb a hlásili problémy v kompilátoru a nástrojích, mnoho odeslaných zákazníky prostřednictvím [komunity vývojářů pro C++](https://developercommunity.visualstudio.com/spaces/62/index.html "Komunita vývojářů pro C++").

Úplné podrobnosti najdete na stránce [Co je nového pro Visual C++ ve Visualu 2017.](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)

### <a name="debugging-and-diagnostics"></a>Ladění a diagnostika

#### <a name="run-to-click"></a>Běžet do kliknutí

Nyní můžete snadněji přeskočit dopředu během ladění bez nastavení zarážky zastavit na řádku, který chcete. Když jste zastaveni v ladicím programu, stačí kliknout na ikonu, která se zobrazí vedle řádku kódu. Váš kód se spustí a zastaví na tomto řádku při příštím přístupu v cestě kódu.

![Visual Studio 2017 ladění - Spustit klikněte](media/vs2017ide-RunToClick.png)

#### <a name="the-new-exception-helper"></a>Nový pomocník pro výjimky

Nový pomocník pro výjimky vám pomůže zobrazit informace o výjimce na první pohled. Informace jsou prezentovány v kompaktní podobě s okamžitým přístupem k vnitřním výjimkám. Při diagnostice NullReferenceException, můžete rychle zobrazit, co bylo null přímo uvnitř pomocníka pro výjimky.

![Dialogové okno Nová pomocná pomoc výjimek v sadě Visual Studio](media/vs2017ide-ExceptionHelper.png)

Další informace najdete v [tématu Použití nového pomocníka pro výjimky v](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/) blogu Visual Studia.

#### <a name="snapshots-and-intellitrace-step-back"></a>Snímky a krok zpět intelliTrace

**Novinka v 15.5**: IntelliTrace krok-back automaticky pořídí snímek vaší aplikace na každé události zarážky a ladicího programu krok. Zaznamenané snímky umožňují vrátit se k předchozím zarážky nebo kroky a zobrazit stav aplikace, jak tomu bylo v minulosti. IntelliTrace krok-back můžete ušetřit čas, když chcete zobrazit předchozí stav aplikace, ale nechcete restartovat ladění nebo znovu vytvořit požadovaný stav aplikace.

Snímky můžete procházet a zobrazovat pomocí tlačítek **Krok vpřed** a **Krok vpřed** na panelu nástrojů **Ladění.** Tato tlačítka procházet události, které se zobrazí na kartě **Události** v okně **Diagnostické nástroje.** Krokování zpět nebo vpřed na událost automaticky aktivuje historické ladění vybrané události.

![Dialogové okno Nová pomocná pomoc výjimek v sadě Visual Studio](../debugger/media/intellitrace-step-back-icons-description.png  "Krok vpřed a vpřed")

Další informace naleznete [v zobrazení snímků pomocí intelliTrace krok zpět](../debugger/view-historical-application-state.md) stránku.

### <a name="containerization"></a>Rozdělení do kontejnerů

Kontejnery poskytují vyšší hustotu aplikací a nižší náklady na nasazení spolu s vyšší produktivitou a flexibilitou DevOps.

#### <a name="docker-container-tooling"></a>Nástroje pro kontejnery Docker

**Novinka v 15.5**:

* Visual Studio obsahuje nástroje pro kontejnery Dockeru, které teď podporují vícestupňové soubory Dockerfiles, které zjednodušují vytváření optimalizovaných ibi kontejnerů.
* Když otevřete projekt, který podporuje Docker, bude Visual Studio ve výchozím nastavení automaticky vyžadovat, sestavovat a spouštět nezbytné kontejnerové image na pozadí. Tuto funkci můžete vypnout pomocí nastavení **Automaticky spustit kontejnery na pozadí** v sadě Visual Studio.

## <a name="cloud-app-development-with-azure"></a>Vývoj cloudových aplikací s Azure

### <a name="azure-functions-tools"></a>Nástroje Azure Functions

Jako součást úlohy "vývoj Azure" jsme zahrnuli nástroje, které vám pomohou vyvíjet funkce Azure pomocí předkompilovaných knihoven tříd C#. Teď můžete vytvářet, spouštět a ladit v místním vývojovém počítači a pak publikovat přímo do Azure z Visual Studia.

Další informace najdete na stránce [Nástroje Azure Functions pro Visual Studio.](/azure/azure-functions/functions-develop-vs)

### <a name="debug-live-aspnet-apps-using-snappoints-and-logpoints-in-live-azure-applications"></a>Ladění živých ASP.NET aplikací pomocí rychlých bodů a protokolů v živých aplikacích Azure

**Novinka v 15.5:** Ladicí program snímek snímku pořídí snímek vašich produkčních aplikací při spuštění kódu, který vás zajímá. Chcete-li pokyn ladicí program pořídit snímek, nastavte snappoints a logpoints v kódu. Ladicí program umožňuje přesně zobrazit, co se pokazilo, aniž by to mělo vliv na provoz produkční aplikace. Ladicí program snímek vám může pomoci výrazně zkrátit dobu potřebný k vyřešení problémů, ke kterým dochází v produkčním prostředí.

Kolekce snímků je dostupná pro následující webové aplikace spuštěné ve službě Azure App Service:

* ASP.NET aplikace spuštěné v rozhraní .NET Framework 4.6.1 nebo novější.
* ASP.NET základní aplikace spuštěné v systému Windows .NET Core 2.0 nebo novějším.

Další informace naleznete v [tématu Ladění živých ASP.NET aplikací pomocí snappointů a protokolů](../debugger/debug-live-azure-applications.md).

## <a name="windows-app-development"></a>Vývoj aplikací pro systém Windows

### <a name="universal-windows-platform"></a>Univerzální platforma Windows

Univerzální platforma Windows (UPW) je platforma aplikací pro Windows 10. Aplikace pro UPW můžete vyvíjet pouze s jednou sadou rozhraní API, jedním &ndash; balíčkem aplikací a jedním obchodem, abyste se dostali ke všem zařízením s Windows 10, pc, tabletu, telefonu, Xboxu, HoloLens, Surface Hubu a dalším. UWP podporuje různé velikosti obrazovky a různé modely interakce, ať už se jedná o dotykové ovládání, myš a klávesnici, herní ovladač nebo pero. Jádrem aplikací UPW je myšlenka, že uživatelé chtějí, aby jejich zkušenosti byly mobilní na všech svých zařízeních a že chtějí používat jakékoli zařízení, které je pro daný úkol nejvhodnější nebo nejproduktivnější.

![Univerzální platforma Windows](../cross-platform/media/uwp_coreextensions.png)

Vyberte si&mdash;preferovaný vývojový jazyk z C#, Visual&mdash;Basic, C++ nebo JavaScripta a vytvořte aplikaci pro univerzální platformu Windows pro zařízení s Windows 10. Visual Studio 2017 poskytuje šablonu aplikace UPW pro každý jazyk, který umožňuje vytvořit jeden projekt pro všechna zařízení. Po dokončení práce můžete vytvořit balíček aplikace a odeslat ho do Microsoft Storu z Visual Studia, abyste aplikaci dostali zákazníkům na jakémkoli zařízení s Windows 10.

**Novinka v sadě 15.5**: Visual Studio 2017 verze 15.5 poskytuje nejlepší podporu pro windows 10 Fall Creators Update SDK (10.0.16299.0). Aktualizace Windows 10 Fall Creators také přináší mnoho vylepšení pro vývojáře UPW. Zde jsou některé z největších změn: 

* **Podpora pro standard .NET 2.0**<br/>Kromě zjednodušeného nasazení aplikací je aktualizace Windows 10 Fall Creators Update první verzí systému Windows 10, která poskytuje podporu rozhraní .NET Standard 2.0. Standard [.NET Je](https://devblogs.microsoft.com/dotnet/introducing-net-standard/) referenční implementace knihovny základních tříd, kterou může implementovat libovolná platforma .NET. Cílem rozhraní .NET Standard je co nejvíce usnadnit vývojářům rozhraní .NET sdílení kódu na libovolné platformě .NET, na které se rozhodnou pracovat.
* **To nejlepší z obou UWP a Win32**<br/>Vylepšili jsme platformu Windows 10 s [desktopovým mostem,](/windows/uwp/porting/desktop-to-uwp-root) aby byl systém Windows 10 lepší pro všechny vývojáře .NET, ať už se jejich aktuální zaměření zaměřuje na UPW, WPF, Windows Forms nebo Xamarin. S novým typem projektu Balení aplikací ve Visual Studiu 2017 verze 15.5 můžete vytvářet balíčky aplikací pro Windows pro vaše projekty WPF nebo Windows Forms, stejně jako u projektů UPW. Po zabalení aplikace získáte všechny výhody nasazení aplikací pro Windows 10 a máte možnost distribuovat prostřednictvím Microsoft Storu (pro spotřebitelské aplikace) nebo Microsoft Storu pro firmy a vzdělávání. Vzhledem k tomu, že zabalené aplikace mají přístup k úplnému povrchu rozhraní API UWP i rozhraním API Win32 na ploše, můžete nyní postupně modernizovat aplikace WPF a Windows Forms pomocí rozhraní API UPW a funkcí systému Windows 10. Kromě toho můžete zahrnout vaše komponenty Win32 do aplikací UPW, které se rozsvítí na ploše se všemi funkcemi Win32.

Další informace o programu UPW najdete na stránce [Vývoj aplikací pro univerzální platformu Windows (UPW).](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)

## <a name="mobile-app-development"></a>Vývoj mobilních aplikací

### <a name="xamarin"></a>Xamarin

Jako součást úlohy "Mobilní vývoj s rozhraním .NET" mohou vývojáři obeznámení s C#, .NET a Visual Studio poskytovat nativní aplikace pro Android, iOS a Windows pomocí Xamarinu. Vývojáři se mohou těšit na stejnou výkon a produktivitu při práci s Xamarinem pro mobilní aplikace, včetně vzdáleného ladění na zařízeních&mdash;se systémem Android, iOS a Windows, aniž by se museli učit nativní kódovací jazyky, jako je Objective-C nebo Java.

Další informace naleznete na stránce [Visual Studio a Xamarin.](/xamarin/)

### <a name="entitlements-editor"></a>Editor nároků

**Novinka v 15.3**: Pro vaše potřeby vývoje iOS jsme přidali samostatný editor Oprávnění. Obsahuje uživatelsky přívětivé uživatelské rozhraní, které lze snadno procházet. Chcete-li jej spustit, poklepejte na soubor *entitlements.plist.*

![Editor nároků pro Xamarin](media/xamarin-entitlements-editor.png)

### <a name="visual-studio-tools-for-xamarin"></a>Nástroje sady Visual Studio pro Xamarin

**Novinka v 15.4**: Xamarin Live umožňuje vývojářům neustále nasazovat, testovat a ladit své aplikace přímo na zařízeních se systémem iOS a Android. Po stažení živého přehrávače&mdash;Xamarin dostupného v&mdash;App Storu nebo na Google Play můžete zařízení spárovat s Visual Studio a změnit způsob vytváření mobilních aplikací. Tato funkce je nyní součástí sady Visual Studio a lze ji povolit tak, že přejdete na**možnosti** >  **nástroje** > **Xamarin** > **Další** > **povolit Xamarin Live Player**.

![Animace dvojice živých přehrávačů Xamarin, nasazení a režimy živých úprav](media/xamarinliveplayer.gif)

### <a name="support-for-google-android-emulator"></a>Podpora emulátoru Google Android

**Novinka v 15.8**: Když používáte Hyper-V, můžete nyní používat emulátor Android společnosti Google vedle sebe s dalšími technologiemi, které jsou založeny na technologii Hyper-V, jako jsou virtuální počítače Hyper-V, nástroje Dockeru, emulátor HoloLens a další. (Tato funkce vyžaduje aktualizaci windows 10 z dubna 2018 nebo novější.)

![Google Android emulátor na Technologie Hyper-V](media/xamarin-hyperv-android-emulator.png)

#### <a name="xamarinandroid-designer-split-view-editor"></a>Xamarin.Android Designer split-view editor

Také **novinka v 15.8**: Udělali jsme významné vylepšení návrháře prostředí pro Xamarin.Android. Zvýraznění je nový editor rozděleného zobrazení, který umožňuje vytvářet, upravovat a zobrazovat náhled rozvržení současně.

![Editor rozděleného zobrazení Xamarin.Adroid Designer](media/android-designer-split-view.png)

Další informace naleznete [v tématu Hardwarová akcelerace pro výkon emulátoru](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)

### <a name="visual-studio-app-center"></a>Visual Studio App Center

**Novinka v 15.5:** Visual&mdash;Studio App Center, které je teď obecně dostupné pro&mdash;aplikace pro Android, iOS, macOS a Windows, má vše, co potřebujete ke správě životního cyklu vašich aplikací, včetně automatizovaných sestavení, testování na reálných zařízeních v cloudu, distribuce beta testerům a obchodům s aplikacemi a sledování reálného využití prostřednictvím crash a analytických dat. Aplikace napsané v Objective-C, Swift, Java, C#, Xamarin a React Native jsou podporovány ve všech funkcích.

  ![Testovací prostředí Centra aplikací Visual Studio](media/app-center-test-env.png)

Další informace najdete [v tématu Introducing App Center: Build, test, distribute and monitor apps in the cloud](https://blogs.msdn.microsoft.com/vsappcenter/introducing-visual-studio-app-center/) blog post.

## <a name="cross-platform-development"></a>Vývoj pro různé platformy

### <a name="redgate-data-tools"></a>Datové nástroje Redgate

Chcete-li rozšířit funkce DevOps na vývoj databáze serveru SQL Server, jsou nyní v sadě Visual Studio k dispozici nástroje Redgate Data Tools.

Součástí sady Visual Studio 2017 Enterprise:

* [Redgate ReadyRoll Core](https://www.red-gate.com/products/sql-development/sql-change-automation/?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) vám pomáhá vyvíjet migrační skripty, spravovat změny databáze pomocí správy zdrojového kódu a bezpečně automatizovat nasazení změn databáze serveru SQL Server spolu se změnami aplikací.
* [Redgate SQL Prompt Core](https://www.red-gate.com/products/sql-development/sql-prompt/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) vám pomůže psát SQL rychleji a přesněji s pomocí inteligentního dokončování kódu. SQL Prompt automaticky dokončuje databázové a systémové objekty a klíčová slova a během psaní nabízí návrhy sloupců. Výsledkem je čistší kód a méně chyb, protože si nemusíte pamatovat každý název sloupce nebo alias.

Součástí všech edic Visual Studia 2017:

* [Redgate SQL Search](https://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) zvyšuje vaši produktivitu tím, že vám pomůže rychle najít fragmenty sql a objekty ve více databázích.

Další informace najdete v příspěvku na blogu [Redgate Data Tools v Visual Studiu 2017.](https://devblogs.microsoft.com/visualstudio/redgate-data-tools-in-visual-studio-2017/)

### <a name="net-core"></a>.NET Core

.NET Core je implementace .NET Standard pro obecné účely, modulární, napříč platformami a otevřeným zdrojovým kódem a obsahuje mnoho stejných rozhraní API jako rozhraní .NET Framework.

Platforma .NET Core je tvořena několika součástmi, které zahrnují spravované kompilátory, runtime, knihovny základních tříd a mnoho aplikačních modelů, jako je ASP.NET Core. .NET Core podporuje tři hlavní operační systémy: Windows, Linux a macOS. Jádro .NET můžete použít ve scénářích zařízení, cloudu a vložené/IoT.

A nyní obsahuje podporu Dockeru.

**Novinka v 15.3**: Visual Studio 2017 verze 15.3 podporuje vývoj .NET Core 2.0. Použití rozhraní .NET Core 2.0 vyžaduje stažení a instalaci sady .NET Core 2.0 SDK samostatně.

Další informace naleznete na stránce [průvodce .NET Core.](/dotnet/core/index)

## <a name="games-development"></a>Vývoj her

### <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity

V rámci pracovnízátěže "Vývoj her pro jednotu" jsme zahrnuli nástroje, které vám pomohou vyvíjet různé platformy pro vytváření 2D a 3D her a interaktivního obsahu. Vytvořte jednou a publikujte na 21 platformách, včetně všech mobilních platforem, WebGL, Mac, PC a Linuxdesktop, web nebo konzole pomocí Visual Studia 2017 a Unity 5.6.

Další informace naleznete na stránce [Nástroje visual studia pro jednotu.](../cross-platform/visual-studio-tools-for-unity.md)

## <a name="ai-development"></a>Vývoj umělá ai

### <a name="visual-studio-tools-for-ai"></a>Visual Studio Tools pro AI

**Novinka v 15.5**: Využijte funkce produktivity visual studia k urychlení inovací ai dnes. Používejte vestavěné funkce editoru kódu, jako je zvýraznění syntaxe, technologie IntelliSense a automatické formátování textu. Můžete interaktivně otestovat aplikaci hlubokého učení v místním prostředí pomocí podrobnéladění na místní proměnné a modely.

  ![IDE hlubokého učení](../ai/media/about/ide.png)

Další informace najdete na stránce [Nástroje visual studia pro umělou přípravu.](../ai/about-ai-tools.md)

## <a name="whats-next"></a>Kam dál

Visual Studio 2017 často aktualizujeme o nové funkce, které mohou vaše vývojové prostředí ještě vylepšit. Zde je rekapitulace některých z našich nejvýznamnějších aktualizací, které jsou v experimentální verzi preview:

* **[Live Share](https://visualstudio.microsoft.com/services/live-share/)**, nový nástroj, který umožňuje sdílet základ kódu a jeho kontext se spoluhráčem a získat okamžitou obousměrnou spolupráci přímo z visual studia. Díky živému sdílení může spoluhráč číst, procházet, upravovat a ladit projekt, který jste s nimi sdíleli, a to bez problémů a bezpečně.<br><br>Další informace naleznete v [nejčastějších dotazech](/visualstudio/liveshare/faq)ke sdílení živého vysílání .<br><br>
* **[IntelliCode](https://visualstudio.microsoft.com/services/intellicode/)**, nová funkce, která vylepšuje vývoj softwaru pomocí ai poskytovat lepší kontextové dokončování kódu, průvodce vývojáři kód vzory a styly jejich týmu, najít obtížné zachytit problémy kódu a zaměřit revize kódu na oblasti, které opravdu záleží. <br><br>Další informace naleznete [v nejčastějších dotazech k intelliCode](/visualstudio/intellicode/faq).

Chcete se dozvědět více o tom, co dalšího je v pracích pro Visual Studio 2017? Podívejte se na stránku [Plán sady Visual Studio.](/visualstudio/productinfo/vs2018-roadmap)

A nezapomeňte se podívat na naši nejnovější verzi, [Visual Studio 2019](whats-new-visual-studio-2019.md).

## <a name="contact-us"></a>Kontaktujte nás

Proč odesílat zpětnou vazbu týmu sady Visual Studio? Protože bereme zpětnou vazbu od zákazníků vážně. Řídí to hodně z toho, co děláme.

Pokud chcete něco navrhnout, jak můžeme Visual Studio vylepšit, nebo získat další informace o možnostech podpory produktů, podívejte se na stránku [Poslat nám zpětnou vazbu.](feedback-options.md)

### <a name="report-a-problem"></a>Nahlášení problému

Někdy zpráva nestačí k vyjádření úplného dopadu problému, se kterým jste se setkali. Pokud se setkáte s problémem s zablokováním, selháním nebo jiným problémem s výkonem, můžete s námi snadno sdílet kroky reprodukci a podpůrné soubory (například snímky obrazovky a soubory se sledováním a výpisem haldy) pomocí nástroje **Nahlásit problém.** Další informace o použití tohoto nástroje naleznete na stránce [Jak nahlásit problém.](how-to-report-a-problem-with-visual-studio.md)

## <a name="see-also"></a>Viz také

* [Poznámky k verzi Visual Studia 2017](/visualstudio/releasenotes/vs2017-relnotes)
* [Novinky v sadě Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)
* [Co je nového ve Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Co je nového v C #](/dotnet/csharp/whats-new)
* [Co je nového pro Team Foundation Server](/azure/devops/server/whats-new)
* [Co je nového ve Visual Studiu pro Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
* [Novinky v sadě Visual Studio 2019](whats-new-visual-studio-2019.md)
