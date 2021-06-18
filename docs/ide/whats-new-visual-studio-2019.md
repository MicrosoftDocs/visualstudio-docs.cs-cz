---
title: Novinky v sadě Visual Studio 2019
titleSuffix: ''
description: Seznamte se s novými funkcemi v Visual Studio 2019.
ms.date: 06/17/2021
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 2f571860d08d16d85e53148bc1023cb08a1c36d2
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307775"
---
# <a name="whats-new-in-visual-studio-2019"></a>Novinky v sadě Visual Studio 2019

**Aktualizace pro verzi 16.10** Viz [úplné poznámky k verzi](/visualstudio/releases/2019/release-notes/) | Zobrazení [plánu produktu](/visualstudio/productinfo/vs-roadmap)

>[!div class="button"]
>[Stáhněte si Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

S Visual Studio 2019 získáte nejlepší nástroje a služby pro všechny vývojáře, aplikace a libovolné platformy. Ať už tento Visual Studio používáte poprvé, nebo ho už roky používáte, je v naší nejnovější verzi spousta věcí, které se vám líbí!

Tady je rekapitulace všech novinek:

* **[Vývoj:](#develop)** Díky lepšímu výkonu, okamžitému vyčištění kódu a lepším výsledkům hledání můžete zůstat soustředění a produktivní.
* **[Spolupráce:](#collaborate)** Užívejte si přirozenou spolupráci prostřednictvím pracovního postupu git-first, úprav a ladění v reálném čase a rešerše kódu přímo Visual Studio.
* **[Ladění:](#debug)** Zvýrazněte a přejděte na konkrétní hodnoty, optimalizujte využití paměti a pořizujte automatické snímky provádění vaší aplikace.

Úplný seznam všech novinek v této verzi najdete v [poznámkách k verzi](/visualstudio/releases/2019/release-notes/).

## <a name="develop"></a>Vývoj

Další informace o tom, jak ušetřit čas s novými funkcemi, najdete v následujícím videu. <br><br>*Délka videa: 3,00 minut*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Vylepšené vyhledávání

Naše nové vyhledávací Snadné spuštění, které se dříve označované jako Snadné spuštění, je rychlejší a efektivnější. Teď se výsledky hledání zobrazují dynamicky při psaní. A výsledky hledání mohou často obsahovat klávesové zkratky pro příkazy, abyste si je mohli zapamatovat pro budoucí použití.

   ![Animace nového vyhledávacího prostředí v Visual Studio 2019](media/vs-2019/new-search-feature.gif "Nové vyhledávací prostředí v Visual Studio 2019.")

Nová logika vyhledávání přibližných shod najde vše, co potřebujete, bez ohledu na překlepy. Takže bez ohledu na to, jestli hledáte příkazy, nastavení, dokumentaci nebo jiné užitečné věci, vám nová funkce vyhledávání usnadní hledání hledané funkce.

Další informace najdete v tématu [Použití Visual Studio vyhledávání.](visual-studio-search.md)

#### <a name="intelligent-search-service"></a>Inteligentní vyhledávací služba

**Novinka ve službě 16.9:** Díky použití technologie využívající cloud, umělé inteligence a strojového učení jsme vylepšili výsledky hledání. Teď nejen, že vyhledávání v Visual Studio relevantnější výsledky, ale může vám také pomoct snadněji objevit funkce produktu.

Další informace najdete v blogovém [příspěvku Intelligent Visual Studio Search](https://devblogs.microsoft.com/visualstudio/intelligent-visual-studio-search-service/) Service.

### <a name="refactorings"></a>Refaktoring

V jazyce C# existuje spousta nových a velmi užitečných refaktoringů, které usnadňují uspořádání kódu. Zobrazují se jako návrhy v žárovkě a zahrnují akce, jako je přesun členů do rozhraní nebo základní třídy, úprava oborů názvů tak, aby odpovídaly struktuře složek, převod smyček foreach na dotazy Linq a další.

   ![Animace prostředí refaktoringu v Visual Studio 2019](media/vs-2019/refactorings.gif "Prostředí refaktoringu v Visual Studio 2019.")

Refaktoringy jednoduše vyvoláte stisknutím **kláves Ctrl+.** a vyberte akci, kterou chcete provést.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) vylepšuje vaše úsilí o vývoj softwaru pomocí umělé inteligence (AI). IntelliCode trénuje na 2 000 open source projektů na GitHubu s více než &mdash; 100 hvězdičkami, aby &mdash; vygeneroval doporučení.

![Animace IntelliCode v Visual Studio 2019](media/vs-2019/IntelliCode.gif "IntelliCode v Visual Studio 2019.")

Tady je několik způsobů, jak Visual Studio IntelliCode pomůže zvýšit produktivitu:

* Doručování dokončování kódu s kontextem
* Navedení vývojářů, aby dodržovali vzory a styly svého týmu
* Vyhledání problémů s kódem, který se obtížně zachytá
* Zaměřte se na recenze kódu tím, že upoutáte pozornost na oblasti, které jsou skutečně důležité.

Původně jsme podporovali pouze C# při prvním zobrazení náhledu IntelliCode jako rozšíření pro Visual Studio. Nyní, **novinka ve windows 16.1,** jsme přidali podporu pro C# a XAML "in-the-box". (Podpora pro C++ a TypeScript/JavaScript je ale stále ve verzi Preview.)

A pokud používáte jazyk C#, přidali jsme také možnost vytrénovat vlastní model na vašem vlastním kódu.

Další informace o IntelliCode najdete v blogových příspěvku Oznamování obecné dostupnosti [IntelliCode a](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) náhledu kódu a Dalších kódů. Pomocí blogových příspěvků [Visual Studio IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) se posuňte méně.

### <a name="code-cleanup"></a>Vyčištění kódu

Spárované s novým indikátorem stavu dokumentu je nový příkaz pro vyčištění kódu. Tento nový příkaz můžete použít k identifikaci a opravě upozornění i návrhů jedinou akcí (nebo kliknutím na tlačítko).

Vyčištěním se kód naformátuje a použijí se všechny opravy kódu podle aktuálního nastavení [a](code-styles-and-code-cleanup.md) [souborů .editorconfig](create-portable-custom-editor-options.md).

   ![Snímek obrazovky nového ovládacího prvku vyčištění kódu v Visual Studio 2019](media/vs-2019/code-cleanup-profile.png "Nový ovládací prvek vyčištění kódu v Visual Studio 2019.")

Kolekce fixerů můžete také uložit jako profil. Pokud máte například malou sadu cílených fixerů, které často používáte při práci s kódem, a pak máte další komplexní sadu oprav, které se mají použít před revizemi kódu, můžete nakonfigurovat profily pro řešení těchto různých úloh.

   ![Snímek obrazovky s konfigurací ovládacího prvku pro vyčištění kódu Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png "Ovládací prvek konfigurace čištění kódu v Visual Studio 2019.")

### <a name="per-monitor-aware-pma-rendering"></a>Vykreslování pma (per-monitor aware)

Pokud používáte monitory nakonfigurované s různými faktory škálování zobrazení nebo se vzdáleně připojíte k počítači s faktory měřítka zobrazení, které se liší od hlavního zařízení, můžete si všimnout, že Visual Studio vypadá rozmazaně nebo se vykresluje ve špatném měřítku.

S vydáním Visual Studio 2019 jsme aplikaci pma Visual Studio pro monitorování. Nyní se Visual Studio správně bez ohledu na faktory měřítka zobrazení, které používáte.

   ![Vykreslování pma (per-monitor aware) v Visual Studio 2019](media/vs-2019/pma-dpi-scaling.png "Vykreslování pma (per-monitor aware) v Visual Studio 2019")

Další informace najdete v blogovém příspěvku [Better multi-monitor experience with Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) .

### <a name="test-explorer"></a>Průzkumník testů

Novinka ve verzi **16.2:** Aktualizovali jsme Průzkumníka testů tak, aby poskytoval lepší zpracování velkých testovacích sad, snadnější filtrování, zjistitelnější příkazy, zobrazení seznamu stop s kartami a přizpůsobitelné sloupce, které umožňují doladit zobrazené informace o testování.

   ![Snímek obrazovky znázorňuje vylepšení uživatelského rozhraní v Průzkumníku testů](media/vs-2019/test-explorer-ui.png "Vylepšení uživatelského rozhraní v Průzkumníku testů")

### <a name="net-core"></a>.NET Core

**Novinka ve verzi 16.3:** Zahrneme podporu pro .NET Core 3.0. Mezi platformami, open source &mdash; a plně podporuje Microsoft.

Další informace najdete v blogovém příspěvku [Oznamující .NET Core 3.0.](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/)

## <a name="collaborate"></a>Spolupráce

V následujícím videu se dozvíte další informace o tom, jak můžete problémy vyřešit pomocí týmu. <br><br>*Délka videa: 4,22 minuty*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Pracovní postup git-first

Něco, co si všimnete, když otevřete Visual Studio 2019 je jeho nové úvodní okno.

   ![Snímek obrazovky nového úvodního okna v Visual Studio 2019](media/vs-2019/start-window-dark.png "Nové úvodní okno v Visual Studio 2019.")

V úvodním okně se zobrazí několik možností, jak rychle kódovat. Nejprve jsme umístili možnost klonování nebo rezervujení kódu z repo.

   ![Animace prostředí Git-first v roce Visual Studio 2019](media/vs-2019/git-first.gif "Prostředí Git-first ve Visual Studio 2019")

V úvodním okně jsou také možnosti otevření projektu nebo řešení, otevření místní složky nebo vytvoření nového projektu.

Další informace najdete v blogovém příspěvku Get to code: How we designed the new Visual Studio start window (Získat kód: Jak jsme navrhli nový Visual Studio [úvodním okně).](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/)

### <a name="git-productivity"></a>Produktivita Gitu

**Novinka ve verzi 16.8:** Git je teď výchozím prostředím pro řízení verzí Visual Studio 2019. Tuto sadu funkcí jsme na základě vaší zpětné vazby v posledních dvou verzích vybudovali a iterovali na ní. Nové prostředí je teď ve výchozím nastavení zapnuté pro všechny. V nové nabídce Gitu můžete klonovat, vytvářet nebo otevírat úložiště. Pomocí integrovaných oken nástrojů Git můžete potvrdit a vložit změny do kódu, spravovat větve, mít aktuální vzdálená úložiště a řešit konflikty při slučování.

Další informace najdete v tématu Prostředí [Git na Visual Studio](../version-control/git-with-visual-studio.md) stránce.

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) je vývojářská služba, která umožňuje sdílet základní kód a jeho kontext s kolegou týmu a získat okamžitou obousměrnou spolupráci přímo z Visual Studio. Díky Live Share může kolega z týmu číst, procházet, upravovat a ladit projekt, který s ním sdílíte, a bez problémů a bezpečně.

A s Visual Studio 2019 se tato služba nainstaluje ve výchozím nastavení.

![Animace, která znázorňuje funkci Live Share spolupráce v Visual Studio 2019](media/vs-2019/live-share.gif "Funkce Live Share spolupráce v Visual Studio 2019.")

Další informace najdete v blogovém [příspěvku o](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) Visual Studio Live Share pro recenze kódu v reálném čase a interaktivním příspěvku o vzdělávání a v blogovém příspěvku Live Share, který je Visual Studio [2019.](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/)

### <a name="integrated-code-reviews"></a>Integrované recenze kódu

Představujeme nové rozšíření, které si můžete stáhnout pro použití s Visual Studio 2019. S tímto novým rozšířením můžete zkontrolovat, spustit a dokonce i ladit žádosti o přístup od týmu, aniž byste Visual Studio. Podporujeme kód jak v GitHubu, tak Azure DevOps úložištích.

   ![Snímek obrazovky s novým rozšířením Pull Requests v Visual Studio 2019](media/vs-2019/pr-experience.png "Nové rozšíření Pull Requests v roce Visual Studio 2019.")

Další informace najdete v blogovém příspěvku [o rozšíření Code reviews using the Visual Studio Pull Requests.](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/)

## <a name="debug"></a>Ladění

Podívejte se na následující video, kde najdete další informace o tom, jak se při ladění můžete zaměřit na nulu s přesným cílením. <br><br>*Délka videa: 3,54 minuty*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Zvýšení výkonu

Vzali jsme jednou exkluzivní datové zarážky C++ a přizpůsobili je pro aplikace .NET Core.

   ![Animace znázorňující zarážky dat ladění v Visual Studio 2019](media/vs-2019/debug-data-breakpoints.gif "Ladicí datové zarážky v Visual Studio 2019.")

Takže bez ohledu na to, jestli kód pracujete v jazyce C++ nebo .NET Core, mohou být datové zarážky dobrou alternativou k umísťování běžných zarážek. Datové zarážky jsou také skvělé pro scénáře, jako je hledání místa, kde se globální objekt upravuje nebo přidává nebo odebral ze seznamu.

A pokud jste vývojář v jazyce C++, který vyvíjí velké aplikace, vytvořil Visual Studio 2019 symboly z proc, což vám umožní ladit tyto aplikace bez problémů souvisejících s pamětí.

### <a name="search-while-debugging"></a>Hledání při ladění

Pravděpodobně jste tam už dříve byli a v okno Kukátko hledání řetězce mezi sadami hodnot. V Visual Studio 2019 jsme přidali vyhledávání do oken Sledovat, Místní hodnoty a Automatické hodnoty, které vám pomůžou najít hledaný objekty a hodnoty.

   ![Animace, která zobrazuje okno hledání ladění v Visual Studio 2019](media/vs-2019/debug-window-search.gif "Okno hledání ladění v Visual Studio 2019.")

Můžete také naformátovat, jak se hodnota zobrazuje v oknech Sledovat, Místní hodnoty a Automatické hodnoty. Vyberte (dvojím kliknutím) jednu z položek v libovolném okně a přidejte čárku (",") pro přístup k rozevíracímu seznamu možných specifikátorů formátu, z nichž každá obsahuje popis zamýšleného účinku.

   ![Nová funkce okno Kukátko a formátování hodnot v Visual Studio 2019](media/search-watch-window.png "Nová funkce okno Kukátko a formátování hodnot v Visual Studio 2019.")

Další informace najdete v blogovém příspěvku o sledování, automatických nastaveních a místních Visual Studio [2019:](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) Hledání objektů a vlastností ve Windows.

### <a name="snapshot-debugger"></a>Ladicí program snímků

Získejte snímek spuštění aplikace v cloudu, abyste přesně viděli, co se děje. (Tato funkce je dostupná pouze Visual Studio Enterprise systému.)

   ![Animace znázorňuje Snapshot Debugger Visual Studio 2019 Enterprise](media/vs-2019/snapshot-debugger.gif "The Snapshot Debugger in Visual Studio 2019 Enterprise.")

Přidali jsme podporu cílení na ASP.NET (základní a desktopové) aplikace, které běží na virtuálním počítači Azure. Přidali jsme také podporu pro aplikace, které běží v Azure Kubernetes Service. Tento Snapshot Debugger vám může pomoct výrazně zkrátit dobu vyřešit problémy, ke kterým dochází v produkčních prostředích.

Další informace najdete v blogovém příspěvku Ladění živého ASP.NET Azure pomocí [Snapshot Debugger](../debugger/debug-live-azure-applications.md) a v blogovém příspěvku Představujeme ladění cest v čase pro [Visual Studio Enterprise 2019.](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/)

### <a name="microsoft-edge-insider-support"></a>Podpora prohlížeče Microsoft Edge Insider

**Novinka ve verzi 16.2:** Zarážku můžete nastavit v javascriptové aplikaci a spustit relaci ladění pomocí prohlížeče [Microsoft Edge Insider.](https://www.microsoftedgeinsider.com/) Když to provedete, Visual Studio okno prohlížeče s povoleným laděním, které pak můžete použít k krokování JavaScriptu aplikace v Visual Studio.

   ![Snímek obrazovky znázorňuje vykreslování kódu JavaScriptu v prohlížeči](media/vs-2019/edge-chromium-breakpoint.png "Vykreslování kódu JavaScriptu v prohlížeči")

### <a name="pinnable-properties-tool"></a>Nástroj Pinnable Properties (Připnutelné vlastnosti)

**Novinka ve verzi 16.4:** Nyní je snazší identifikovat objekty podle jejich vlastností při ladění pomocí nového nástroje Připnoutelné vlastnosti. Stačí najet myší na vlastnost, kterou chcete zobrazit v okně ladicího programu oken Sledovat, Automatické hodnoty a Místní hodnoty, vybrat ikonu připínáčky a okamžitě zobrazit informace, které hledáte v horní části okna.

   ![Animace, která ukazuje, jak připnout vlastnosti v ladicím Visual Studio pomocí nástroje Připnoutelné vlastnosti](media/vs-2019/debugger-pinnable-properties.gif "Připnutí vlastností v Visual Studio ladicím programu pomocí nástroje Připnoutelné vlastnosti.")

Další informace najdete v blogovém příspěvku [Pinnable Properties: Debug & Display Managed Objects YOUR Way (Připnoutelné vlastnosti:](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/) Ladění spravovaných objektů ve vašem způsobu).

## <a name="whats-next"></a>Kam dál

Často aktualizujeme Visual Studio novými funkcemi, které mohou vaše vývojové prostředí ještě zlepšit. Další informace o našich nejnovějších inovacích najdete na Visual Studio [Blog.](https://devblogs.microsoft.com/visualstudio/) Záznam toho, co jsme dote doby vydali ve verzi Preview, si můžete prohlédnout ve zprávě k [vydání verze Preview.](/visualstudio/releases/2019/release-notes-preview/) A seznam toho, co plánujeme vydat jako další, najdete na [Visual Studio plán.](/visualstudio/productinfo/vs-roadmap)

Mezitím se v současnosti pracuje s těmito funkcemi:

- **Vylepšené prostředí Gitu v Visual Studio 2019 (Preview)**

   I když je nástroj pro správu verzí Git výchozím prostředím ve verzi Visual Studio 2019 [verze 16.8](/visualstudio/releases/2019/release-notes-history/) a novější, nadále přidávají funkce, které vylepšují prostředí v nejnovější verzi Visual Studio 2019 Preview verze [16.11.](/visualstudio/releases/2019/release-notes-preview/)

   Další informace najdete v tématu [o řízení verzí na Visual Studio.](/visualstudio/version-control/)

- **K dispozici je první veřejná verze Visual Studio 2022 (Preview).**

    Veřejná verze Preview naší další hlavní verze, [Visual Studio 2022,](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/)je nyní k dispozici. Nová verze je rychlejší, přístupnější a zjednodušenější. A vůbec poprvé je Visual Studio 64 bitů. Odkaz ke stažení a další informace najdete v blogovém **[příspěvku Visual Studio 2022 Preview 1.](https://devblogs.microsoft.com/visualstudio/?p=232975&preview=true)**

## <a name="give-us-feedback"></a>Sdělte nám svůj názor

Proč posílat zpětnou vazbu Visual Studio týmu? Protože zpětnou vazbu zákazníků bereme vážně. Řídí velkou část toho, co děláme.

* Pokud chcete navrhnout, jak můžeme vylepšit Visual Studio, můžete to udělat pomocí nástroje [Navrhnout](suggest-a-feature.md) funkci.

* Pokud nastane problém, kdy Visual Studio přestane reagovat, dojde k chybě nebo jiný problém s výkonem, můžete s námi snadno sdílet kroky pro reprodukci a podpůrné soubory pomocí nástroje [pro](how-to-report-a-problem-with-visual-studio.md) hlášení problémů.

## <a name="see-also"></a>Viz také

* [Co je nového v Visual Studio docs](whats-new-visual-studio-docs.md)
* [Visual Studio k vydání verze 2019](/visualstudio/releases/2019/release-notes/)
* [Visual Studio k vydání verze pro Mac verze 2019](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [Co je nového v sadě Visual Studio 2019 SDK](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Novinky v jazyce C++ v sadě Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio/)
* [Co je nového v jazyce C# 9.0](/dotnet/csharp/whats-new/csharp-9)
* [Co je nového v .NET 5](/dotnet/core/dotnet-five)
* [Co je nového v .NET Framework](/dotnet/framework/whats-new/)
* [Konference Microsoft Build](https://www.microsoft.com/build)
* [Microsoft Ignite conference](https://www.microsoft.com/ignite)
