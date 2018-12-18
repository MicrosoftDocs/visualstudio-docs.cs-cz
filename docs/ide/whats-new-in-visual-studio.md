---
title: Novinky v sadě Visual Studio 2017
titleSuffix: ''
description: Informace o nových funkcích v sadě Visual Studio 2017.
ms.date: 12/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c490d15f27801dff6bb09f6356ad7c665b09c558
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53160189"
---
# <a name="what39s-new-in-visual-studio-2017"></a>Co&#39;s novou v sadě Visual Studio 2017

**Aktualizováno pro [verzi 15.9](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)**

Pokud chcete upgradovat z předchozí verze sady Visual Studio? Zde je, co Visual Studio 2017 můžete nabídnout: Nebývalá produktivita pro všechny vývojáře, aplikace a jakoukoli platformu. Pomocí sady Visual Studio 2017 můžete vyvíjet aplikace pro Android, iOS, Windows, Linux, web a cloud. Svůj kód můžete rychle psát, snadno ladit a diagnostikovat, často testovat a bez obav vydávat. Navíc si můžete sadu Visual Studio rozšířit a přizpůsobit pomocí svých vlastních rozšíření. Používejte správu verzí, agilita a efektivní spolupráce v této vydané verzi!

Tady je podrobný rekapitulace toho, změny provedené od předchozích verzí sady Visual Studio 2015:

* **[Předefinovaná Základy](#redefined-fundamentals)**. Nové prostředí instalace znamená, že můžete nainstalovat rychleji a nainstalovat, co chcete, když je potřebujete.
* **[Výkon a produktivitu](#performance-and-productivity)**. Jsme se zaměřili na nový a moderní mobilní, cloudové a funkcí vývoj desktopových aplikací. A Visual Studio spouští rychleji, je rychlejší reakce a využívá méně paměti než dřív.
* **[Vývoj aplikace s Azure v cloudu](#cloud-app-development-with-azure)**. Integrovaná sada nástrojů Azure, které umožňují snadno vytvářet cloudové aplikace s využitím Microsoft Azure. Visual Studio zjednodušuje konfiguraci, sestavení, ladění, zabalení a nasazení aplikací a služeb v Azure.
* **[Vývoj aplikací pro Windows](#windows-app-development)**. Použití šablon UWP v sadě Visual Studio 2017 k vytvoření jednoho projektu pro všechna zařízení s Windows 10 &ndash; počítač, tablet, telefon, Xbox, HoloLens, Surface Hub a další.
* **[Vývoj mobilních aplikací](#mobile-app-development)**. Inovace a získání výsledků rychle s využitím kódu Xamarin, což sjednocuje vaše multiplatformní mobilní požadavky na jedno jádro základu kódu a sady dovedností.
* **[Vývoj pro různé platformy](#cross-platform-development)**. Můžete bez potíží doručovat software na libovolnou cílovou platformu. Rozšiřte procesy DevOps na SQL Server pomocí nástroje Redgate Data Tools a bezpečně Automatizujte nasazování databází ze sady Visual Studio. Nebo můžete použít k tvorbě aplikací a knihoven, které poběží na Windows, Linuxu a macOS operačních systémů bez úprav .NET Core.
* **[Vývoj hry](#games-development)**. S Visual Studio Tools pro Unity (VSTU) můžete použít Visual Studio napsat hru a editor skriptů v jazyce C# a pak použijte jeho výkonný ladicí program najít a opravit chyby.
* **[Vývoj AI](#ai-development)**. Pomocí Visual Studio Tools for AI můžete použít pro zvýšení produktivity sady Visual Studio k urychlení inovace AI. Vytvářet, testovat a nasazovat obsáhlý Learning / řešení AI, který se snadno integrují s Azure Machine Learning pro experimentování ve službě robustní možnosti.

> [!NOTE]
> Úplný seznam nových funkcí a funkcí v sadě Visual Studio 2017, najdete v článku [aktuální zpráva k vydání verze](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017). A náhled na budoucí verze nabídky, najdete v článku [poznámky k verzi Preview](/visualstudio/releasenotes/vs2017-preview-relnotes?context=visualstudio/default&contextView=vs-2017).

Tady je podrobnější informace o některých nejvíce významná vylepšení a nových funkcí v sadě Visual Studio 2017.

## <a name="redefined-fundamentals"></a>Předefinované základy

### <a name="a-new-setup-experience"></a>Nové prostředí instalace

[Stáhnout Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) nebo [Visual Studio Zkontrolujte požadavky na systém](/visualstudio/productinfo/vs2017-system-requirements-vs?context=visualstudio/default&contextView=vs-2017)

 Visual Studio umožňuje jednodušší a rychlejší instalace jen těch funkcí, které potřebujete, když je potřebujete. A odinstalace proběhne čistě, příliš.

 Nejdůležitější změny mějte na paměti při instalaci sady Visual Studio je její nové prostředí instalace. Na **úlohy** kartě, zobrazí se vám možnosti instalace, které jsou seskupeny představující běžných architektur, jazyků a platforem. Zahrnuje všechno od vývoj desktopových aplikací .NET do C++ vývoj aplikací pro iOS, Windows a Linux.

Vyberte úlohy, které potřebujete a změnit, pokud je potřeba.

 ![Dialogové okno nastavení aplikace Visual Studio 2017](../install/media/install-visual-studio-enterprise.png)

A máte spoustu možností a systém doladit instalace, příliš:

* Chcete si vybrat vlastní komponenty, ne pomocí úloh? Vyberte **jednotlivé komponenty** kartu z instalačního programu.
* Chcete nainstalovat jazykové sady bez nutnosti měnit výběrem jazyka Windows? Zvolte **jazykových sad** kartu Instalační služby.
* **Nové ve verzi 15.7**: Chcete změnit umístění, kam se nainstaluje Visual Studio? Zvolte **možnosti instalace** kartu Instalační služby.

Další informace o nové prostředí instalace, včetně podrobných pokynů, které vám ukážou, najdete v článku [instalace sady Visual Studio](../install/install-visual-studio.md) stránky.

### <a name="a-focus-on-accessibility"></a>Zaměřením na usnadnění přístupu

**Novinka v 15.3**, jsme provedli přes 1,700 cílová opravy pro zlepšení kompatibility mezi verzemi sady Visual Studio a technologiemi pro usnadnění, které mnozí uživatelé používají. Existují desítky scénáře, které se čtečkami obrazovky, vysoký kontrast – motivy a dalšími technologiemi přístupnosti kompatibilní více než kdy dřív. Ladicí program, editor a prostředí mají gotten významná vylepšení, příliš.

Další informace najdete v tématu [vylepšení přístupnosti v sadě Visual Studio 2017 verze 15.3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) blogový příspěvek.

## <a name="performance-and-productivity"></a>Výkon a produktivitu

### <a name="sign-in-across-multiple-accounts"></a>Přihlaste se napříč několika účty

Zavedli jsme novou službu identit v sadě Visual Studio, která umožňuje sdílet uživatelské účty napříč Průzkumník týmových projektů, nástrojů Azure, publikování Microsoft Store a další.

Abyste mohli zůstat přihlášeni, příliš. Visual Studio nevyžaduje, abyste se přihlásili znovu každých 12 hodin. Další informace najdete v tématu [přihlášení méně Visual Studio vyzve](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/) blogový příspěvek.

### <a name="start-visual-studio-faster"></a>Rychlejší spuštění aplikace Visual Studio

Nové centrum sledování výkonu Visual Studio vám umožňují optimalizovat čas spuštění integrovaného vývojového prostředí. Centrum sledování výkonu zobrazují všechny rozšíření a okna nástrojů, které může zpomalit spuštění integrovaného vývojového prostředí. Slouží ke zlepšení výkonu spouštění tak, že určíte při spuštění rozšíření, nebo určuje, zda jsou otevřené při spuštění nástroje systému windows.

### <a name="faster-on-demand-loading-of-extensions"></a>Rychlejší načítání rozšíření na vyžádání

Visual Studio je přesun jeho rozšíření (a práci s rozšíření třetích stran příliš) tak, aby se načítají na vyžádání, spíše než při spuštění integrovaného vývojového prostředí. Zajímá vás o tom, které rozšíření ovlivnit spouštění, načítání řešení a zadáním výkonu? Může zobrazit tyto informace v **pomáhají** > **spravovat výkon sady Visual Studio**.

  ![Dialogové okno Možnosti v sadě Visual Studio 2017](../ide/media/vs2017ide-manage-vs-perf.png)

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Spravovat rozšíření pomocí Správce rozšíření pro Roaming

Je snazší nastavení jednotlivých vývojového prostředí obsahovala vaše oblíbená rozšíření při přihlášení k sadě Visual Studio. Nový Správce rozšíření pro Roaming uchovává informace o všechna vaše oblíbená rozšíření vytvořením synchronizovaného seznamu v cloudu.

Pokud chcete zobrazit seznam rozšíření v sadě Visual Studio, klikněte na tlačítko **nástroje** > **rozšíření a aktualizace**a potom klikněte na tlačítko **Správce rozšíření pro Roaming**.

![Visual Studio 2017 – dialogové okno rozšíření a aktualizace](../ide/media/vs2017ide-extensions-and-updates.png)

Správce rozšíření pro Roaming sleduje všechna rozšíření, které nainstalujete, ale můžete vybrat ty, které chcete přidat do vašeho seznamu roamingu.

![Visual Studio 2017 – dialogové okno rozšíření a aktualizace](../ide/media/vs2017ide-RoamingExtensionManager.png)

Při použití Správce rozšíření pro Roaming, existují tři typy ikon na seznamu:

* ![Ikona s roamingem](../ide/media/vs2017ide-roamedicon.png)  **_ikona s roamingem_**: Rozšíření, která je součástí tohoto seznamu roamingu, ale není nainstalované na vašem počítači.
  (Je můžete nainstalovat pomocí **Stáhnout** tlačítko.)
* ![Ikona s roamingem a nainstalováno](../ide/media/vs2017ide-roamedinstalledicon.png)  **_s roamingem a nainstalováno_**: Všechna rozšíření, které jsou součástí tohoto seznamu roamingu a nainstalované ve vývojovém prostředí.
  (Pokud nechcete přesouvat, můžete je odebrat pomocí **zastavit Roaming** tlačítko.)
* ![Ikona nainstalováno](../ide/media/vs2017ide-installedicon.png)  **_nainstalováno_**: Všechna rozšíření, která jsou nainstalovaná v tomto prostředí, ale nejsou součástí vašeho seznamu roamingu.
  (Rozšíření můžete přidat do seznamu roamingu pomocí **Start Roaming** tlačítko.)

Všechna rozšíření, který stahujete, když se přihlásíte se přidá do seznamu jako **s roamingem a nainstalováno**. Rozšíření se pak stane součástí vašeho seznamu roamingu, která umožňuje přístup k němu z libovolného počítače.

### <a name="experience-live-unit-testing"></a>Živé testování částí prostředí

V sadě Visual Studio Enterprise 2017 živé testování vám umožní žijete výsledky testování částí a pokrytí kódu v editoru během psaní kódu. Funguje s projekty C# a Visual Basic pro rozhraní .NET Framework a .NET Core a podporuje tři testovací architektury: MSTest, xUnit a NUnit.

![Live Unit Testing](../ide/media/lut-codewindow.png)

Další informace najdete v tématu [Představujeme Live Unit Testing](../test/live-unit-testing-intro.md). Seznam nových funkcí v jednotlivých verzích sady Visual Studio Enterprise 2017 najdete v tématu [co je nového v Live Unit Testing](../test/live-unit-testing-whats-new.md).

### <a name="set-up-a-cicd-pipeline"></a>Nastavení kanálu CI/CD

#### <a name="automated-testing"></a>Automatizované testování

Automatizované testování je klíčovou součástí libovolného kanálu DevOps. Umožňuje konzistentně a spolehlivě testování a vydání řešení v mnohem kratší cykly. Toky CI/CD (průběžná integrace a průběžného doručování) může pomoct zjednodušit proces efektivnější.

Další informace o automatických testů, najdete v článku [kanálu CI/CD pro automatizované testování v DevOps](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/) blogový příspěvek.

A další informace o tom, co je nového [nástrojů Continuous delivery tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) rozšíření devlabs s názvem, najdete v článku [potvrzení s jistotou: Potvrdit kvalitu kódu čas](https://blogs.msdn.microsoft.com/visualstudio/2017/08/21/committing-with-confidence-commit-time-code-quality-information-updated/) blogový příspěvek.

### <a name="visual-studio-ide-enhancements"></a>Vylepšení Visual Studio IDE

#### <a name="multi-caret-editing"></a>Blikající kurzor o víc úpravy

**Novinka v 15.8**: Úprava více míst v souboru, současně, je teď snadné. Začněte vytvořením vložení body a výběr na víc místech v souboru. Potom použijte funkci úpravy více blikající kurzor o provádět stejné úpravy ve dvou nebo více míst ve stejnou dobu.

Další informace najdete v tématu [více blikající kurzor o výběr](finding-and-replacing-text.md#multi-caret-selection) část z [najít a nahradit text](finding-and-replacing-text.md) stránky.

#### <a name="keep-keybinding-profiles-consistent"></a>Zachování konzistence keybinding – profily

**Novinka v 15.8**: Teď můžete zachovat vaše klávesové zkratky konzistentní napříč nástroji dva nové profily klávesnice: Visual Studio Code a ReSharper (Visual Studio). Můžete najít v těchto schématech **nástroje** > **možnosti** > **Obecné** > **klávesnice**a horní rozevírací nabídky.

  ![Nové profily klávesové zkratky pro Visual Studio Code a ReSharper](../ide/media/vs-keyboard-mappings-code-resharper.png)

#### <a name="use-new-refactorings"></a>Použít nové refaktoringy

Refaktoring je proces zlepšit váš kód poté, co bylo zapsáno. Refaktoring změní interní strukturu kódu beze změny jeho chování. Často, přidáme nové refaktoringy Tady je pár:

* Přidání parametru (z CallSite.)
* Generovat přepsání
* Přidat pojmenovaného argumentu.
* Přidat kontrolu hodnoty null pro parametry
* Oddělovače číslic: příkaz Insert literály
* Změnit základ pro numerických literálech (například hexadecimální do binárního souboru)
* Převést if na switch
* Odebrat nepoužívanou proměnnou

Další informace najdete v tématu [rychlé akce](../ide/common-quick-actions.md).

#### <a name="interact-with-git"></a>Při práci s Gitem

Při práci s projektem v sadě Visual Studio, můžete nastavit a rychle potvrzení a publikujte kód do služby Git. Můžete také spravovat vaše úložiště Git s použitím klikne na tlačítko nabídky z tlačítka v pravém dolním rohu integrovaného vývojového prostředí.

![Visual Studio 2017 komunikuje se službou Git dialogového okna](../ide/media/vsIDE-GitInteraction.png)

#### <a name="experience-improved-navigation-controls"></a>Vylepšená navigace ovládací prvky prostředí

Aktualizovali jsme navigační prostředí, se kterými získáte od A do B s větší jistotou a méně rozptýlení.

* **Nové ve verzi 15.4**: **Přejít k definici** (**Ctrl**+**klikněte na tlačítko** nebo **F12**) &ndash; myši uživatelé mají snadný způsob, jak přejít k definici člen stisknutím kombinace kláves **Ctrl** a pak levým na člen. Stisknutím klávesy **Ctrl** a najede myší symbol v kódu se podtržení ho a znovu je zapnout na odkaz. Zobrazit [přejít k definici a náhled definice](../ide/go-to-and-peek-definition.md) Další informace.

* **Přejít k implementaci** (**Ctrl**+**F12**) &ndash; přejít z jakéhokoli základního typu nebo člena na její různé implementace.

* **Přejít ke všem** (**Ctrl**+**T** nebo **Ctrl**+**,**) &ndash; přejděte přímo do souboru/typu/členu/symbolu deklaraci. Můžete filtrovat seznam výsledků nebo použijte syntaxi dotazu (například "f searchTerm" pro soubory.), "t searchTerm" pro typy, atd.

  ![Vylepšené přejít na vše](../ide/media/vs2017ide-navigation-go-to.png)

* **Najít všechny odkazy** (**Shift**+**F12**) &ndash; s barevné zvýrazňování syntaxe, můžete seskupovat podle kombinace projektu, definice, výsledky vyhledání všech odkazů a cestu. Je také možné "zamknout" výsledky tak, že můžete pokračovat v hledání dalších odkazů na původním původní výsledky.

  ![Nový nástroj Najít všechny odkazy](../ide/media/vs2017ide-find-all-references.png)

* **Vizualizér struktur** &ndash; tečkami, šedé svislé čáry (vodítka pro odsazení) fungují jako památek v kódu k zajištění kontextu v rámci rámce zobrazení. Je si možná pamatujete z oblíbených nástrojů Productivity Power Tools. Můžete využít k vizualizaci a zjistit, jaké bloku kódu je v kdykoli bez nutnosti přejít. Ukazatel myši řádky zobrazí popis tlačítka, které vám poskytnou otevírání tohoto bloku a jejích nadřazených tříd. Je k dispozici pro všechny jazyky podporované prostřednictvím gramatik TextMate, jakož i jazyka C#, Visual Basic a XAML.

  ![Vizualizér struktur Visual Studio 2017](../ide/media/vsIDE-StructureVisualizer.png)

Další informace o nových funkcích produktivity, najdete v článku [produktivitu v sadě Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/productivity-in-visual-studio-2017-rc/) blogový příspěvek označit Wilson-Thomase.

### <a name="visual-c"></a>Visual C++

Zobrazí se vám několik vylepšení v sadě Visual Studio, jako je například distribuci podle dokumentu C++ Core Guidelines pomocí sady Visual Studio, kompilátor aktualizuje tak, že přidáte rozšířenou podporu pro C ++ 11 a C++ funkce a přidávání a aktualizaci funkce v knihovnách jazyka C++. Vylepšili jsme také výkon prostředí IDE jazyka C++, úlohy instalace a další.

Také jsme opravili víc než 250 chyb a nahlášených problémů v kompilátoru a nástrojů, řadu z nich odeslali zákazníci přes [komunity vývojářů v jazyce c++](https://developercommunity.visualstudio.com/spaces/62/index.html "komunity vývojářů v jazyce c++").

Úplné podrobnosti najdete v tématu [co je nového pro Visual C++ 2017 vizuál](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio) stránky.

### <a name="debugging-and-diagnostics"></a>Ladění a Diagnostika

#### <a name="run-to-click"></a>Běžet do kliknutí

Teď můžete snadněji přeskočit během ladění bez nastavení zarážku pro zastavení na požadovaném řádku. Po zastavení v ladicím programu stačí kliknout na ikonu, která se zobrazí vedle řádku kódu. Váš kód se spustí a zastaví se na tomto řádku, které se dosažení v kódové cestě.

![Ladění jazyka Visual Studio 2017 – běžet do kliknutí](../ide/media/vs2017ide-RunToClick.png)

#### <a name="the-new-exception-helper"></a>Nového pomocníka výjimky

Nového pomocníka výjimky umožňuje zobrazit vaše výjimka informace na přehledem. Informace jsou uvedeny v kompaktním formátu s okamžitým přístupem k vnitřním výjimkám. Když diagnostiky NullReferenceException můžete rychle zjistit, co mělo hodnotu null, přímo v Pomocníkovi výjimky.

![Dialog nového pomocníka výjimky v sadě Visual Studio](../ide/media/vs2017ide-ExceptionHelper.png)

Další informace najdete v tématu [pomocí nového pomocníka výjimky v sadě Visual Studio](https://blogs.msdn.microsoft.com/devops/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) blogový příspěvek.

#### <a name="snapshots-and-intellitrace-step-back"></a>Snímky a zpětného kroku IntelliTrace

**Nové ve verzi 15.5**: Zpětného kroku IntelliTrace automaticky vytvoří snímek vaší aplikace v každé zarážce a ladicí program krok události. Zaznamenané snímky umožňují snadno vrátit k předchozím zarážkám nebo krokům a zobrazit stav aplikace jako v minulosti. IntelliTrace zpětným krokem vám může ušetřit čas při chcete zobrazit předchozí stav aplikace, ale nebudete chtít znovu spusťte ladění nebo znovu vytvořit stav požadované aplikace.

Můžete procházet a zobrazit snímky pomocí **krok zpět** a **krok vpřed** tlačítka v **ladění** nástrojů. Tato tlačítka Procházet události, které se zobrazují v **události** kartu **diagnostické nástroje** okna. Automaticky krokování zpět nebo vpřed na událost aktivuje historické ladění na vybrané události.

![Dialog nového pomocníka výjimky v sadě Visual Studio](../debugger/media/intellitrace-step-back-icons-description.png  "krok zpět a vpřed tlačítka")

Další informace najdete v tématu [zobrazení snímků pomocí zpětného kroku IntelliTrace](../debugger/how-to-use-intellitrace-step-back.md) stránky.

### <a name="containerization"></a>Kontejnerizace

Kontejnery umožňují aplikace vyšší hustota a nižší náklady na nasazení společně s zvýšení produktivity a flexibility DevOps.

#### <a name="docker-container-tooling"></a>Nástroje pro kontejnery docker

**Nové ve verzi 15.5**:

* Visual Studio obsahuje nástroje pro kontejnery Dockeru, které teď podporují vícefázové soubory Dockerfile, který tak zjednodušit vytváření optimalizovaných imagí kontejnerů.
* Když otevřete projekt, který podporuje Docker, bude Visual Studio ve výchozím nastavení automaticky vyžadovat, sestavovat a spouštět nezbytné kontejnerové image na pozadí. Tuto funkci můžete vypnout pomocí nastavení **Automaticky spustit kontejnery na pozadí** v sadě Visual Studio.

## <a name="cloud-app-development-with-azure"></a>Vývoj cloudových aplikací s Azure

### <a name="azure-functions-tools"></a>Nástroje Azure Functions

Jako součást sady funkcí vývoj v Azure. "zahrnuli jsme nástroje můžete vyvíjet funkce Azure s použitím předem kompilovaných knihoven tříd C#. Teď můžete vytvářet, spouštět a ladění na svém místním vývojovém počítači a potom publikovat přímo do Azure ze sady Visual Studio.

Další informace najdete v tématu [Azure Functions tools for Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-develop-vs) stránky.

### <a name="debug-live-aspnet-apps-using-snappoints-and-logpoints-in-live-azure-applications"></a>Ladění živé aplikace ASP.NET pomocí snímkovací a protokolovací body v živé aplikace Azure

**Nové ve verzi 15.5**: Snapshot Debugger pořídí snímek vaší aplikace do produkčního prostředí, když spustí kód, který vás zajímá. Dáte pokyn, aby ladicí program k vytvoření snímku, můžete nastavit snímkovací a protokolovací body ve vašem kódu. Ladicí program umožňuje zobrazit přesně toho, co nefunguje, aniž by to ovlivnilo provozu aplikace v produkčním prostředí. Snapshot Debugger můžete výrazně zkrátit čas potřebný k vyřešení problémů, ke kterým dochází v produkčním prostředí.

Shromažďování snímků je k dispozici pro následující web apps ve službě Azure App Service:

* Aplikace ASP.NET spuštěné na rozhraní .NET Framework 4.6.1 nebo novější.
* Aplikace ASP.NET Core na .NET Core 2.0 nebo novější na Windows.

Další informace najdete v tématu [ladit živé aplikace ASP.NET pomocí snímkovací a protokolovací body](../debugger/debug-live-azure-applications.md).

## <a name="windows-app-development"></a>Vývoj aplikací pro systém Windows

### <a name="universal-windows-platform"></a>Univerzální platforma pro Windows

Univerzální platforma Windows (UPW) je platforma aplikací pro Windows 10. Můžete vyvíjet aplikace pro UPW s jen jedna sada rozhraní API a jeden balíček, jeden obchod pro všechna zařízení s Windows 10 &ndash; počítač, tablet, telefon, Xbox, HoloLens, Surface Hub a další. UPW podporuje jiné velikosti obrazovky a různé modely interakce, ať to dotykového ovládání, myš a klávesnici, herní zařízení nebo pera. V jádru služby aplikací pro UPW je myšlenkou, že uživatelé chtějí své prostředí, abyste na všech jejich zařízeních využívat mobilní zařízení a chtějí používat jakékoli zařízení je pro daný úkol nejvíce vhodné nebo produktivitu.

 ![Univerzální platforma pro Windows](../cross-platform/media/uwp_coreextensions.png)

Zvolte si jazyk oblíbeným vývojovým&mdash;z jazyka C#, Visual Basic, C++ nebo JavaScript&mdash;k vytvoření aplikace pro univerzální platformu Windows pro zařízení s Windows 10. Visual Studio 2017 obsahuje šablony aplikace UPW pro každý jazyk, který umožňuje vytvořit jeden projekt pro všechna zařízení. Po dokončení práce můžete vytvořit balíček aplikace a odeslat ji na Microsoft Store ze sady Visual Studio k aplikaci dostat k zákazníkům na všechna zařízení s Windows 10.

**Nové ve verzi 15.5**: Visual Studio 2017 verze 15.5 poskytuje nejlepší podpora pro Windows 10 Fall Creators Update SDK (10.0.16299.0). Windows 10 Fall Creators Update přináší také celou řadu vylepšení pro vývojáře na UPW. Tady jsou některé z největších změn: 

* **Podpora pro .NET Standard 2.0**<br/>Kromě zjednodušené aplikace nasazení Windows 10 Fall Creators Update je první verze Windows 10 k zajištění podpory .NET Standard 2.0. Efektivně [.NET Standard](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/) je referenční implementace v knihovně základních tříd, které můžete implementovat libovolnou platformu .NET. Cílem .NET Standard je k tomu, aby co nejrychleji pro vývojáře na platformě .NET a sdílejte kód na libovolné platformě .NET, kterou si pro práci na.
* **To nejlepší z UPW a prostředí Win32**<br/>Vylepšili jsme platformu Windows 10 s [přemostění na Desktop](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-root) Chcete vylepšit Windows 10 pro všechny vývojáře na platformě .NET, zda je jejich aktuální fokus na UPW, WPF, Windows Forms nebo Xamarin. Pomocí nového typu aplikace balení projektu v sadě Visual Studio 2017 verze 15.5 můžete vytvořit balíčky aplikací pro Windows pro projekty WPF nebo Windows Forms, stejně jako pro projekty UWP. Po aplikaci zabalit, všechny aplikace pro Windows 10, získáte výhody nasazení a mít možnost distribuovat přes Microsoft Store (pro zákaznické aplikace) nebo Microsoft Store pro firmy a vzdělávání. Protože zabalené aplikace mají přístup k úplné surface UPW rozhraní API a rozhraní API systému Win32 ve stolním počítači, můžete nyní modernizovat aplikace WPF a Windows Forms postupně pomocí funkcí rozhraní API pro UPW a Windows 10. Kromě toho může obsahovat vaše komponenty Win32 ve svých aplikacích UPW, které bylo možné ve stolním počítači se všemi funkcemi Win32.

Další informace o UPW, najdete v článku [vývoj aplikací pro univerzální platformu Windows (UPW)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md) stránky.

## <a name="mobile-app-development"></a>Vývoj mobilních aplikací

### <a name="xamarin"></a>Xamarin

Jako součást úlohy "Vývoj mobilních aplikací pomocí .NET" mohou vývojáři, kteří znají C#, .NET a Visual Studio vytvářejte nativní aplikace pro Android, iOS a Windows pomocí Xamarinu. Vývojáři můžou využívat stejné výkon a produktivitu při práci s využitím kódu Xamarin pro mobile apps, včetně vzdáleného ladění na zařízení s Androidem, iOS a Windows&mdash;bez nutnosti učit nativní kódování jazycích Objective-C nebo Java.

Další informace najdete v tématu [Visual Studio a Xamarin](../cross-platform/visual-studio-and-xamarin.md) stránky.

### <a name="entitlements-editor"></a>Editor oprávnění

**Novinka v 15.3**: Pro vaše potřeby vývoje s Iosem přidali jsme samostatný editor oprávnění. To zahrnuje uživatelsky přívětivou UI, které lze snadno procházet. Spusťte ho, klikněte dvakrát na vaše *do souboru entitlements.plist* souboru.

![Editor oprávnění pro Xamarin](../ide/media/xamarin-entitlements-editor.png)

### <a name="visual-studio-tools-for-xamarin"></a>Nástroje sady Visual Studio pro Xamarin

**Nové ve verzi 15.4**: Xamarin Live umožňuje vývojářům nepřetržitě nasazovat, testovat a ladit své aplikace přímo na zařízeních se systémy iOS a Android. Po stažení Xamarin Live Player&mdash;k dispozici v App Store nebo Google Play&mdash;můžete spárovat své zařízení se sadou Visual Studio a zásadně zlepšit způsob, jak sestavovat mobilní aplikace. Tato funkce je teď zahrnutá v sadě Visual Studio a jde povolit v nabídce **Nástroje** > **Možnosti** > **Xamarin** > **Jiné** > **Povolit Xamarin Live Player**.

![Animace dvojice v Xamarin Live Playeru, nasazení a režimů živých úprav](../ide/media/xamarinliveplayer.gif)

### <a name="support-for-google-android-emulator"></a>Podpora pro emulátor Google Android

**Novinka v 15.8**: Při použití technologie Hyper-V teď můžete použít Googlu emulátoru Androidu – souběžně s jinými technologiemi, které jsou založeny na technologii Hyper-V, jako Hyper-V virtuální počítače, Docker nástroje, HoloLens emulátor a další. (Tato funkce vyžaduje operační systém Windows 10. dubna 2018 Update nebo novější.)

![Emulátor Google Android na technologie Hyper-V](../ide/media/xamarin-hyperv-android-emulator.png)

#### <a name="xamarinandroid-designer-split-view-editor"></a>Editor rozděleného zobrazení návrháře Xamarin.Android

Také **novinkou 15.8**: Provedli jsme významné vylepšení návrháře pro Xamarin.Android. Zvýraznění je nový editor rozdělené zobrazení, která umožňuje vytváření, úprav a náhledu vašich rozložení ve stejnou dobu.

![Editor návrháře Xamarin.Adroid rozdělené zobrazení](../ide/media/android-designer-split-view.png)

Další informace najdete v tématu [hardwarovou akceleraci emulátoru výkonu](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)

### <a name="visual-studio-app-center"></a>Visual Studio App Center

**Nové ve verzi 15.5**: Visual Studio App Center&mdash;která je teď obecně dostupná pro aplikace pro Android, iOS, macOS a Windows&mdash;obsahuje všechno, co potřebujete ke správě životního cyklu aplikací, včetně automatizovaného sestavení, testování na skutečných zařízeních v cloudu, distribuce testerům beta verzí a obchodů s aplikacemi a sledování využití z reálného světa pomocí o chybách a analytickým datům. Aplikace napsané v jazyce Objective-C, Swift, Java, C#, Xamarin a React Native jsou podporovány v rámci všech funkcí.

  ![Visual Studio App Center testovacího prostředí](../ide/media/app-center-test-env.png)

Další informace najdete v tématu [Introducing App Center: Vytvářejte, testujte, distribuujte a monitorování aplikací v cloudu](https://blogs.msdn.microsoft.com/vsappcenter/introducing-visual-studio-app-center/) blogový příspěvek.

## <a name="cross-platform-development"></a>Vývoj pro různé platformy

### <a name="redgate-data-tools"></a>Datové nástroje Redgate

Abychom rozšířili možnosti DevOps na vývoj databází SQL serveru, jsou teď Redgate Data Tools v sadě Visual Studio k dispozici.

Součástí sady Visual Studio 2017 Enterprise:

* [Redgate ReadyRoll Core](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) pomáhá vývojem skriptů migrace, správou změn databáze pomocí správy zdrojového kódu a bezpečnou automatizací nasazení systému SQL Server databáze změny společně se změnami aplikací.
* [Redgate SQL Prompt Core](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) pomáhá můžete psát kód SQL rychleji a přesněji pomocí inteligentního dokončování kódu. SQL Prompt automaticky dokončuje databázové a systémové objekty a klíčová slova a během psaní nabízí návrhy sloupců. V důsledku čistější kód a menší množství chyb vzhledem k tomu, že nebudou muset pamatovat každý sloupec název nebo alias.

Součást všech edicí sady Visual Studio 2017:

* [Redgate SQL Search](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) zvyšuje vaši produktivitu tím, že pomáhá rychle najít fragmenty a objekty SQL ve více databázích.

Další informace najdete v tématu [Redgate Data Tools v sadě Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2017/03/07/redgate-data-tools-in-visual-studio-2017/) blogový příspěvek.

### <a name="net-core"></a>.NET Core

.NET core je obecný, modulární, napříč platformami a opensourcová implementace .NET Standard a obsahuje mnoho stejných rozhraní API jako rozhraní .NET Framework.

Platformy .NET Core je tvořeno několika komponent, které zahrnují spravované kompilátory, modul runtime, knihovny základních tříd a mnoho aplikačních modelů, jako je ASP.NET Core. .NET core podporuje tři hlavní operační systémy: Windows, Linux a macOS. Použití .NET Core v zařízení, cloud a scénáře vložené a IoT.

A teď zahrnuje podporu Dockeru.

**Novinka v 15.3**: Visual Studio 2017 verze 15.3 podporuje vývoj pro .NET Core 2.0. Použití .NET Core 2.0 vyžaduje stažení a instalaci sadu .NET Core 2.0 SDK odděleně.

Další informace najdete v tématu [.NET Core průvodce](/dotnet/core/index) stránky.

## <a name="games-development"></a>Vývoj her

### <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity

Jako součást úlohy "Vývoj her pro Unity" zahrnuli jsme nástrojů pro vývoj pro různé platformy pro vytváření 2D a 3D her a interaktivního obsahu. Stačí je vytvořit jednou a publikujte na 21 platformách, včetně všechny mobilní platformy, WebGL, Mac, PC a Linux desktopu, web nebo konzoly pomocí sady Visual Studio 2017 a Unity 5.6.

Další informace najdete v tématu [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) stránky.

## <a name="ai-development"></a>Vývoj AI

### <a name="visual-studio-tools-for-ai"></a>Visual Studio Tools for AI

**Nové ve verzi 15.5**: Použijte funkce produktivitu sady Visual Studio k urychlení inovace AI ještě dnes. Použití funkce editoru integrovanou kódu, jako jsou zvýraznění syntaxe, IntelliSense a automatické formátování. Testovat váš hloubkového učení aplikace v místním prostředí pomocí krokové ladění na lokálních proměnných a modely.

  ![Hloubkové učení integrovaného vývojového prostředí](../ai/media/about/ide.png)

Další informace najdete v tématu [Visual Studio Tools for AI](../ai/about-ai-tools.md) stránky.

## <a name="whats-next"></a>Co se chystá

Díky novým funkcím, které můžete provádět vývoj ještě lepší prostředí často aktualizujeme Visual Studio 2017. Tady je rekapitulace toho některé z našich nejdůležitější aktualizace, které jsou v experimentální verzi preview:

* **[Live sdílenou složku](https://visualstudio.microsoft.com/services/live-share/)**, nový nástroj, který vám umožní sdílet základ kódu a jeho kontextu s programujete a získat rychlé obousměrné spolupráci přímo z Visual Studia. S Live Share programujete můžete přečíst, přejděte, upravit a ladit projekt, který jste sdíleli s nimi a učinit snadno a bezpečně.<br><br>Další informace najdete v tématu [Live nejčastější dotazy k sdílení](/visualstudio/liveshare/faq).<br><br>
* **[IntelliCode](https://visualstudio.microsoft.com/services/intellicode/)**, novou funkci, která vylepšuje vývoje softwaru pomocí AI k zajištění lepší s ohledem na kontext kódu dokončování, Průvodce vývojářům kód pro vzory a styly svého týmu, najít problémy s kódu obtížné catch , a revize kódu zaměření na oblasti, které jsou opravdu důležité. <br><br>Další informace najdete v tématu [nejčastější dotazy k IntelliCode](../ide/not-in-toc/intellicode-faq.md).

Chcete vědět více o tom, co jiného se připravuje pro Visual Studio 2017? Zobrazit [Visual Studio Roadmap](/visualstudio/productinfo/vs2018-roadmap) stránky.

## <a name="contact-us"></a>Kontaktujte nás

 Proč odeslat zpětnou vazbu týmu sady Visual Studio? Protože jsme vážně trvat zpětné vazby od zákazníků. To vede velkou část co děláme.

Pokud chcete provést návrh, o jak jsme vylepšení sady Visual Studio, nebo Další informace o možnostech podpory produktu, naleznete [kontaktujte nás](../ide/talk-to-us.md) stránky.

### <a name="report-a-problem"></a>Nahlášení problému

 V některých případech zprávy nestačí k předání celkový dopad problému, který jste se setkali. Pokud dochází k zablokování, při selhání nebo jiné problémy s výkonem, můžete jednoduše sdílet kroky pro reprodukci a podpůrné soubory (například snímky obrazovky a trasování a haldy soubory s výpisem paměti) s námi pomocí **nahlásit problém** nástroj. Další informace o tom, jak tento nástroj použít, najdete v článku [jak ohlásit problém](how-to-report-a-problem-with-visual-studio-2017.md) stránky.

## <a name="see-also"></a>Viz také:

* [Zpráva k vydání verze Visual Studio 2017](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)
* [Co je nového v jazyce Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Co je nového v jazyce C#](/dotnet/csharp/whats-new)
* [Co je nového v Team Foundation Server](/tfs/server/whats-new?view=vsts)
* [Co je nového v sadě Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
* [Co je nového ve Visual Studio 2019](whats-new-visual-studio-2019.md)
