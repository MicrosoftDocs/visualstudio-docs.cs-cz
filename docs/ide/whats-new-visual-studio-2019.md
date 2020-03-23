---
title: Novinky v sadě Visual Studio 2019
titleSuffix: ''
description: Přečtěte si o nových funkcích visual studia 2019.
ms.date: 03/16/2020
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: bf251ade250a466cefe02db6f5cc709a0c18837b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79437742"
---
# <a name="whats-new-in-visual-studio-2019"></a>Novinky v sadě Visual Studio 2019

**Aktualizováno pro [verzi 16.5](/visualstudio/releases/2019/release-notes/)**

>[!div class="button"]
>[Stáhněte si Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

S Visual Studio 2019 získáte nejlepší nástroje a služby ve své třídě pro všechny vývojáře, libovolné aplikace a jakoukoli platformu. Ať už používáte Visual Studio poprvé nebo jste používali po celá léta, je tu hodně líbí v této nové verzi!

Zde je rekapitulace na vysoké úrovni o tom, co je nového:

* **[Vývoj](#develop)**: Buďte soustředění a produktivní díky vylepšenému výkonu, okamžitému vyčištění kódu a lepším výsledkům vyhledávání.
* **[Spolupráce](#collaborate)**: Užijte si přirozenou spolupráci prostřednictvím pracovního postupu gitu, úprav a ladění v reálném čase a kontrol kódu přímo v sadě Visual Studio.
* **[Ladění](#debug)**: Zvýrazněte a přejděte na konkrétní hodnoty, optimalizujte využití paměti a pořizujte automatické snímky spuštění aplikace.

Úplný seznam všeho, co je v této verzi nové, naleznete v [poznámkách k verzi](/visualstudio/releases/2019/release-notes/).

## <a name="develop"></a>Vývoj

V následujícím videu najdete další informace o tom, jak můžete ušetřit čas díky novým funkcím. <br><br>*Délka videa: 3,00 minuty*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Vylepšené vyhledávání

Dříve známé jako Rychlé spuštění, naše nové vyhledávání je rychlejší a efektivnější. Výsledky hledání se nyní při psaní zobrazují dynamicky. A výsledky hledání mohou často obsahovat klávesové zkratky pro příkazy, takže si je můžete snadněji zapamatovat pro budoucí použití.

   ![Animace nového prostředí pro vyhledávání ve Visual Studiu 2019](media/vs-2019/new-search-feature.gif)

Nová logika fuzzy vyhledávání najde vše, co potřebujete, bez ohledu na překlepy. Ať už tedy hledáte příkazy, nastavení, dokumentaci nebo jiné užitečné věci, nová funkce vyhledávání usnadňuje nalezení toho, co hledáte.

### <a name="refactorings"></a>Refaktoringy

Existuje spousta nových a velmi užitečné refaktorings v C# které usnadňují uspořádání kódu. Zobrazují se jako návrhy v žárovce a zahrnují akce, jako je přesunutí členů do rozhraní nebo základní třídy, úprava jmenných prostorů tak, aby odpovídaly struktuře složek, převod foreach-smyčky na linq dotazy a další.

   ![Animace prostředí refaktoringu ve Visual Studiu 2019](media/vs-2019/refactorings.gif)

Jednoduše vyvolat refaktorings stisknutím **Ctrl +.** a výběrem akce, kterou chcete provést.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) vylepšuje vaše úsilí o vývoj softwaru pomocí umělé inteligence (AI). IntelliCode trénuje na 2 000 open&mdash;source projektech na&mdash;GitHubu s více než 100 hvězdičkami, aby vygeneroval svá doporučení.

![Animace IntelliCode v Visual Studiu 2019](media/vs-2019/IntelliCode.gif)

Tady je několik způsobů, jak visual studio IntelliCode může pomoci zvýšit vaši produktivitu:

* Doručení dokončování kontextusonzovaného kódu
* Průvodce vývojáři dodržovat vzory a styly svého týmu
* Najít problémy s kódem obtížně zachytita
* Zaměření revize kódu tím, že upozorní na oblasti, které jsou opravdu důležité

Původně jsme podporovali pouze C# při prvním náhledu IntelliCode jako rozšíření pro Visual Studio. Nyní, **nové v 16.1**, jsme přidali podporu pro C# a XAML "in-the-box". (Podpora pro C++ a TypeScript/JavaScript jsou však stále ve verzi preview.)

A pokud používáte C#, přidali jsme také možnost trénovat vlastní model na vlastní kód.

Další informace o IntelliCode [najdete v tématu oznámení obecné dostupnosti IntelliCode plus náhled a](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) [kód více, posunméně s Visual Studio IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) blogu.

### <a name="code-cleanup"></a>Vyčištění kódu

Spárován s novým indikátorem stavu dokumentu je nový příkaz vyčištění kódu. Pomocí tohoto nového příkazu můžete identifikovat a poté opravit upozornění i návrhy kliknutím na tlačítko.

Vyčištění bude formátovat kód a použít všechny opravy kódu, jak je navrženo [aktuální nastavení](code-styles-and-code-cleanup.md) a [.editorconfig soubory](create-portable-custom-editor-options.md).

   ![Snímek obrazovky s novým ovládacím prvkem vyčištění kódu v Sadě Visual Studio 2019](media/vs-2019/code-cleanup-profile.png)

Můžete také uložit kolekce fixerů jako profil. Například pokud máte malou sadu cílených fixers, které často platí při kódu a pak máte další komplexní sadu fixers použít před kontrolou kódu, můžete nakonfigurovat profily k řešení těchto různých úkolů.

   ![Snímek obrazovky s ovládacím prvkem konfigurace vyčištění kódu v Sadě Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png)

### <a name="per-monitor-aware-pma-rendering"></a>Vykreslování s vědomím na monitor (PMA)

Pokud používáte monitory, které jsou nakonfigurovány s různými faktory měřítka zobrazení nebo vzdáleně připojit k počítači s faktory škálování zobrazení, které se liší od hlavního zařízení, můžete si všimnout, že Visual Studio vypadá rozmazaný nebo vykreslení v nesprávném měřítku.

S vydáním Visual Studia 2019, děláme Visual Studio aplikace pro monitorování vědomi (PMA). Visual Studio se nyní vykresluje správně bez ohledu na faktory měřítka zobrazení, které používáte.

   ![Vykreslování s ohledem na monitor (PMA) ve Visual Studiu 2019](media/vs-2019/pma-dpi-scaling.png)

Další informace najdete v [tématu lepší multi-monitor zkušenosti s Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) blogu.

### <a name="test-explorer"></a>Průzkumník testů

**Novinka v 16.2**: Aktualizovali jsme Průzkumníka testů, abychom zajistili lepší zpracování velkých testovacích sad, snadnější filtrování, více zjistitelné příkazy, zobrazení seznamu stop s kartami a přizpůsobitelné sloupce, které umožňují doladit, jaké informace o testu se zobrazí.

   ![Snímek obrazovky, který zobrazuje vylepšení uživatelského rozhraní v Průzkumníkovi testů](media/vs-2019/test-explorer-ui.png)

### <a name="net-core"></a>.NET Core

**Novinka v 16.3**: Zahrnuli jsme podporu pro .NET Core 3.0. Cross-platformní,&mdash;open source a plně podporované společností Microsoft.

Další informace naleznete [v příspěvku blogu Oznámení jádra .NET 3.0.](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/)

## <a name="collaborate"></a>Spolupráce

V následujícím videu najdete další informace o tom, jak se můžete spojit a řešit problémy. <br><br>*Délka videa: 4,22 minuty*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Pracovní postup git-first

Něco, co si všimnete při otevření Visual Studia 2019, je jeho nové počáteční okno.

   ![Snímek obrazovky s novým počátečním oknem ve Visual Studiu 2019](media/vs-2019/start-window-dark.png)

Počáteční okno vám nabídne několik možností, jak rychle zakódovat kód. Umístili jsme možnost klonovat nebo rezervovat kód z repo, první.

   ![Animace prostředí "Git-first" ve Visual Studiu 2019](media/vs-2019/git-first.gif)

Počáteční okno obsahuje také možnosti otevření projektu nebo řešení, otevření místní složky nebo vytvoření nového projektu.

Další informace najdete v [tématu Přístup ke kódu: Jak jsme navrhli nový](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) příspěvek blogu počáteční okno Sady Visual Studio.

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) je vývojářská služba, která umožňuje sdílet základ kódu a jeho kontext se spoluhráčem a získat okamžitou obousměrnou spolupráci přímo z visual studia. Díky živému sdílení může spoluhráč číst, procházet, upravovat a ladit projekt, který jste s nimi sdíleli, a to bez problémů a bezpečně.

A s Visual Studio 2019 je tato služba nainstalována ve výchozím nastavení.

![Animace, která zobrazuje funkci live share spolupráce ve Visual Studiu 2019](media/vs-2019/live-share.gif)

Další informace najdete v [tématu Visual Studio Live Share pro real-time revize kódu a interaktivní vzdělávání](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) blogu a Live Share nyní součástí Visual Studio [2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) blogu.

### <a name="integrated-code-reviews"></a>Integrované revize kódu

Představujeme nové rozšíření, které si můžete stáhnout pro použití s Visual Studio 2019. Pomocí tohoto nového rozšíření můžete zkontrolovat, spustit a dokonce i ladit žádosti o přijetí informací z vašeho týmu bez opuštění sady Visual Studio. Podporujeme kód v úložištích GitHub i Azure DevOps.

   ![Snímek obrazovky s novým počátečním oknem ve Visual Studiu 2019](media/vs-2019/pr-experience.png)

Další informace najdete v [tématu revize kódu pomocí rozšíření visual studio žádosti o přijetí dat](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) blogu blogu.

## <a name="debug"></a>Ladění

V následujícím videu se dozvíte více o tom, jak můžete při ladění zaměřit na nulu pomocí přesného cílení. <br><br>*Délka videa: 3,54 minuty*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Zvýšení výkonu

Vzali jsme jednou výhradní c++ zarážky dat a přizpůsobit je pro aplikace .NET Core.

   ![Animace, která zobrazuje zarážky ladicích dat v Sadě Visual Studio 2019](media/vs-2019/debug-data-breakpoints.gif)

Takže ať už kódujete v jazyce C++ nebo .NET Core, zarážky dat mohou být dobrou alternativou k pouhému umístění pravidelných zarážek. Zarážky dat jsou také skvělé pro scénáře, jako je například zjištění, kde je globální objekt upravován nebo přidáván nebo odebírán ze seznamu.

A pokud jste vývojář jazyka C++, který vyvíjí velké aplikace, Visual Studio 2019 vytvořilsymboly z proc, což umožňuje ladit tyto aplikace bez problémů souvisejících s pamětí.

### <a name="search-while-debugging"></a>Hledání při ladění

Pravděpodobně jste tam byli předtím, když jste hledali v okně Watch řetězec mezi sadou hodnot. Ve Visual Studiu 2019 jsme přidali hledání do oken Hodinky, Místní a Autos, které vám pomůže najít objekty a hodnoty, které hledáte.

   ![Animace, která zobrazuje okno hledání ladění v Sadě Visual Studio 2019](media/vs-2019/debug-window-search.gif)

Můžete také formátovat, jak se hodnota zobrazuje v oknech Sledovat, Místní a Automatické.  Poklepejte na některou z položek v libovolném systému a přidejte čárku (",") pro přístup k rozevíracímu seznamu možných specifikátorů formátu, z nichž každá obsahuje popis zamýšleného účinku.

   ![Nové okno kukátka a funkce formátových hodnot v Sadě Visual Studio 2019](media/search-watch-window.png)

Další informace najdete v tématu [Rozšířené v Visual Studiu 2019: Hledání objektů a vlastností v hodinkách, autos a locals Windows](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) blogu.

### <a name="snapshot-debugger"></a>Ladicí program snímků

Získejte snímek spouštění aplikace v cloudu a podívejte se, co se přesně děje. (Tato funkce je k dispozici pouze v sadě Visual Studio Enterprise.)

   ![Animace, která zobrazuje ladicí program snímek v Sadě Visual Studio 2019 Enterprise](media/vs-2019/snapshot-debugger.gif)

Přidali jsme podporu pro cílení ASP.NET (core a desktop) aplikace, které běží na virtuálním počítači Azure. A přidali jsme podporu pro aplikace, které běží ve službě Azure Kubernetes. Ladicí program snímek vám může pomoci výrazně zkrátit dobu potřebný k vyřešení problémů, ke kterým dochází v produkčním prostředí.

Další informace najdete v tématu ladění živých ASP.NET aplikací Azure pomocí stránky [Debugger snímků](../debugger/debug-live-azure-applications.md) a [v příspěvku blogu Introducing Time Travel Debugging for Visual Studio Enterprise 2019.](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/)

### <a name="microsoft-edge-insider-support"></a>Podpora prohlížeče Microsoft Edge Insider

**Novinka v 16.2**: Můžete nastavit zarážku v aplikaci JavaScript a spustit relaci ladění pomocí prohlížeče [Microsoft Edge Insider.](https://www.microsoftedgeinsider.com/) Když tak učiníte, Visual Studio otevře nové okno prohlížeče s povoleným laděním, které pak můžete použít k krokování aplikace JavaScript v rámci sady Visual Studio.

   ![Snímek obrazovky s vykreslováním kódu JavaScriptu v prohlížeči](media/vs-2019/edge-chromium-breakpoint.png)

### <a name="pinnable-properties-tool"></a>Připnuté vlastnosti, nástroj

**Novinka v 16.4**: Nyní je snazší identifikovat objekty podle jejich vlastností při ladění pomocí nového nástroje Pinnable Properties. Stačí najet kurzorem na vlastnost, kterou chcete zobrazit v okně ladicího programu v oknech Hodinky, Auta a Místní, vyberte ikonu špendlíku a okamžitě uvidíte informace, které hledáte v horní části okna!

   ![Animace, která ukazuje, jak připnout vlastnosti v ladicím programu Sady Visual Studio pomocí nástroje Pinnable Properties](media/vs-2019/debugger-pinnable-properties.gif)

Další informace naleznete v [tématu Pinnable Properties: Debug & Display Managed Objects YOUR Way](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/) blog post.

## <a name="whats-next"></a>Kam dál

Visual Studio 2019 často aktualizujeme o nové funkce, které mohou vaše vývojové prostředí ještě vylepšit. Další informace o našich nejnovějších inovacích najdete na [blogu visual studia](https://devblogs.microsoft.com/visualstudio/). Chcete-li zaznamenat, co jsme dosud vydali ve verzi Preview, podívejte se na [poznámky k verzi Preview](/visualstudio/releases/2019/release-notes-preview/). A seznam toho, co plánujeme vydat dále, najdete v [plánu Visual Studio Plán](/visualstudio/productinfo/vs-roadmap).

Chcete se dozvědět více o tom, co dalšího je v pracích pro Visual Studio 2019? Podívejte se na [plán sady Visual Studio](/visualstudio/productinfo/vs-roadmap/).

## <a name="give-us-feedback"></a>Sdělte nám svůj názor

Proč odesílat zpětnou vazbu týmu sady Visual Studio? Protože bereme zpětnou vazbu od zákazníků vážně. Řídí to hodně z toho, co děláme.

* Pokud chcete vytvořit návrh o tom, jak můžeme vylepšit Visual Studio, můžete tak učinit pomocí [nástroje Navrhnout funkce.](suggest-a-feature.md)

* Pokud se setkáte s problémem s zablokováním, selháním nebo jiným problémem s výkonem, můžete s námi snadno sdílet kroky reprodukci a podpůrné soubory pomocí nástroje [Nahlásit problém.](how-to-report-a-problem-with-visual-studio.md)

## <a name="see-also"></a>Viz také

* [Poznámky k verzi Visual Studia 2019](/visualstudio/releases/2019/release-notes/)
* [Poznámky k verzi Visual Studia 2019 pro Mac](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [Co je nového v sadě Visual Studio 2019 SDK](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Konference Microsoft Build](https://www.microsoft.com/build)
* [Microsoft Ignite conference](https://www.microsoft.com/ignite)
