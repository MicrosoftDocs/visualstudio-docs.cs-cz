---
title: Novinky v sadě Visual Studio 2019
titleSuffix: ''
description: seznamte se s novými funkcemi v Visual Studio 2019.
ms.date: 07/15/2021
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
ms.openlocfilehash: 76513e23b22c5903da780dd9029e41804c5b6052
ms.sourcegitcommit: d856c46d78638be609e7045621ed1bd7521a6dcc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2021
ms.locfileid: "114283857"
---
# <a name="whats-new-in-visual-studio-2019"></a>Novinky v sadě Visual Studio 2019

**Aktualizováno pro verzi 16,10.** Zobrazit [úplné poznámky k verzi](/visualstudio/releases/2019/release-notes/) | Zobrazit [Plán produktu](/visualstudio/productinfo/vs2019-roadmap)

>[!div class="button"]
>[Stáhněte si Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)

s Visual Studio 2019 získáte nejlepší nástroje a služby pro všechny vývojáře, aplikace a platformy. bez ohledu na to, jestli používáte Visual Studio poprvé nebo jste ji používali po dobu let, je v naší aktuální verzi hodně.

Tady je rekapitulace, co je nového, vše na nejvyšší úrovni:

* **[Vývoj](#develop)**: zlepšení výkonu, okamžitého vyčištění kódu a lepších výsledků hledání díky lepšímu vývoji a produktivitě.
* **[Spolupráce](#collaborate)**: Využijte výhod přirozené spolupráce prostřednictvím pracovního postupu Git-First, úpravy a ladění v reálném čase a revize kódu přímo v Visual Studio.
* **[Ladění](#debug)**: zvýrazněte a přejděte na konkrétní hodnoty, optimalizujte využití paměti a proveďte automatické snímky provádění vaší aplikace.

Úplný seznam všeho, co je v této verzi nové, najdete v [poznámkách k verzi](/visualstudio/releases/2019/release-notes/).

## <a name="develop"></a>Vývoj

Podívejte se na následující video, kde se dozvíte víc o tom, jak můžete ušetřit čas pomocí nových funkcí. <br><br>*Délka videa: 3,00 minut*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Vylepšené vyhledávání

Dříve označované jako rychlé spuštění je naše nové vyhledávání rychlejší a efektivnější. Nyní se při psaní zobrazí výsledky hledání dynamicky. Výsledky hledání mohou často zahrnovat klávesové zkratky pro příkazy, takže je můžete nepamatují pro budoucí použití.

   ![animace nového vyhledávacího prostředí v Visual Studio 2019](media/vs-2019/new-search-feature.gif "nové možnosti vyhledávání v Visual Studio 2019.")

Nová logika přibližného vyhledávání bude najít cokoli, co potřebujete, bez ohledu na překlepy. To znamená, že pokud hledáte příkazy, nastavení, dokumentaci nebo jiné užitečné věci, nová funkce vyhledávání usnadňuje hledání, co hledáte.

další informace najdete v tématu [použití Visual Studio search](visual-studio-search.md).

#### <a name="intelligent-search-service"></a>Služba inteligentního vyhledávání

**Novinka v 16,9**: pomocí technologie založené na cloudu, umělé Intelligence a strojového učení jsme vylepšili výsledky hledání. v současné době nestačí hledat v Visual Studio získáte relevantnější výsledky, ale může vám také usnadnit rychlejší zjišťování funkcí produktu.

další informace najdete v příspěvku blogu [služby inteligentního Visual Studio search](https://devblogs.microsoft.com/visualstudio/intelligent-visual-studio-search-service/) .

### <a name="refactorings"></a>Refaktoring

V jazyce C# existuje spousta nových a velmi užitečných refaktoringů, které usnadňují uspořádání kódu. Zobrazují se jako návrhy v žárovkě a zahrnují akce jako přesunutí členů do rozhraní nebo základní třídy, úpravy oborů názvů tak, aby odpovídaly struktuře složek, převedení smyček foreach na dotazy LINQ a další.

   ![animace prostředí refaktoringu v Visual Studio 2019](media/vs-2019/refactorings.gif "prostředí refaktoringu v Visual Studio 2019.")

Jednoduše volejte refaktoring stisknutím **kombinace kláves CTRL +.** a vyberte akci, kterou chcete provést.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) vylepšuje úsilí při vývoji softwaru pomocí umělé intelligence (AI). IntelliCode vlaky napříč 2 000 open source projektů na GitHub &mdash; každý s více než 100 hvězdičkami &mdash; , aby vygenerovala doporučení.

![animace IntelliCode ve Visual Studio 2019](media/vs-2019/IntelliCode.gif "IntelliCode v Visual Studio 2019.")

tady je několik způsobů, jak Visual Studio IntelliCode může přispět k lepší produktivitě:

* Doručovat dokončování kódu s ohledem na kontext
* Příručka pro vývojáře, aby dodržovala vzory a styly jejich týmu
* Hledání problémů s kódem, který se špatně zachytí
* Zaměřte se na revize kódu tím, že vykreslíte pozornost oblastí, které skutečně jsou

Původně jsme podporovali jenom C#, když jsme IntelliCode jako rozšíření pro Visual Studio. **Novinka v 16,1** jsme přidali podporu pro C# a XAML "in-the-box". (Podpora pro C++ a TypeScript/JavaScript je však stále ve verzi Preview.)

A pokud používáte jazyk C#, Přidali jsme také možnost naučit se vlastní model ve vlastním kódu.

další informace o IntelliCode najdete v části [oznamuje obecnou dostupnost IntelliCode a také vás zajímá náhled](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) a [další kód. posuňte se Visual Studio IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) blogových příspěvků.

### <a name="code-cleanup"></a>Vyčištění kódu

Párování s novým indikátorem stavu dokumentu je nový příkaz pro vyčištění kódu. Pomocí tohoto nového příkazu můžete identifikovat a opravit upozornění i návrhy s jednou akcí (nebo kliknutím na tlačítko).

Vyčištění naformátuje kód a použije všechny opravy kódu navrhované [aktuálním nastavením](code-styles-and-code-cleanup.md) a [soubory. editorconfig](create-portable-custom-editor-options.md).

   ![snímek obrazovky nového ovládacího prvku pro vyčištění kódu v Visual Studio 2019](media/vs-2019/code-cleanup-profile.png "nový ovládací prvek pro vyčištění kódu v Visual Studio 2019.")

Kolekce analyzérů můžete také ukládat jako profil. Například pokud máte malou sadu cílových analyzérů, kterou použijete často během kódu a pak máte další komplexní sadu analyzérů, která se má použít před revizí kódu, můžete nakonfigurovat profily pro řešení těchto různých úloh.

   ![snímek obrazovky s ovládacím prvkem pro konfiguraci vyčištění kódu v Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png "nakonfigurujte ovládací prvek pro vyčištění kódu v Visual Studio 2019.")

### <a name="per-monitor-aware-pma-rendering"></a>Vykreslování PMA (per-monitor)

pokud používáte monitory, které jsou nakonfigurované s různými faktory měřítka zobrazení, nebo se vzdáleně připojit k počítači se zobrazenými faktory škálování, které se liší od vašeho hlavního zařízení, můžete si všimnout, že Visual Studio vypadá rozmazaný nebo vykreslený v nesprávném měřítku.

s vydáním Visual Studio 2019 provádíme Visual Studio aplikace PMA (per-monitor). nyní se Visual Studio správně vykresluje bez ohledu na to, jaké faktory škálování displeje používáte.

   ![vykreslování PMA (Per-monitor) v Visual Studio 2019](media/vs-2019/pma-dpi-scaling.png "vykreslování PMA (Per-monitor) v Visual Studio 2019.")

další informace najdete v blogovém příspěvku o [lepším prostředí pro více monitorů s Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) .

### <a name="test-explorer"></a>Průzkumník testů

**Novinka v 16,2**: Aktualizovali jsme Průzkumníka testů, abychom zajistili lepší zacházení s velkými testovacími sadami, jednodušším filtrováním, více zjistitelnými příkazy, zobrazeními seznamu skladeb na kartách a přizpůsobitelnými sloupci, které vám umožní doladit informace o tom, jaké informace o testu se zobrazují.

   ![Snímek obrazovky, který zobrazuje vylepšení uživatelského rozhraní v Průzkumníku testů](media/vs-2019/test-explorer-ui.png "Vylepšení uživatelského rozhraní v Průzkumníku testů.")

### <a name="net-core"></a>.NET Core

**Novinka v 16,3**: zahrnuli jsme podporu pro .net Core 3,0. Pro různé platformy, open source &mdash; a plně podporované Microsoftem.

Další informace najdete v příspěvku na blogu o [.NET Core 3,0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/) .

## <a name="collaborate"></a>Spolupráce

Podívejte se na následující video, kde se dozvíte víc o tom, jak se dá tým seskupit a vyřešit problémy. <br><br>*Délka videa: 4,22 minut*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Pracovní postup Git – první

něco, co si všimnete, když otevřete Visual Studio 2019 je jeho novým úvodním oknem.

   ![snímek obrazovky nového okna start v Visual Studio 2019](media/vs-2019/start-window-dark.png "nové okno start v Visual Studio 2019.")

Okno Start nabízí několik možností, jak rychle získat kód. Umístili jsme možnost klonovat nebo rezervovat kód z úložiště, nejdřív.

   ![animace možnosti Git-first v Visual Studio 2019](media/vs-2019/git-first.gif "prostředí Git-first v Visual Studio 2019.")

Okno Start také obsahuje možnosti pro otevření projektu nebo řešení, otevření místní složky nebo vytvoření nového projektu.

další informace najdete v tématu [získání kódu: jak jsme navrhli nový příspěvek blogu Visual Studio úvodní okno](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) .

### <a name="git-productivity"></a>Produktivita Git

**novinka ve verzi 16,8**: Git je teď výchozím prostředím pro řízení verzí v Visual Studio 2019. Sestavili jsme sadu funkcí a na ni jste na základě vašich názorů za poslední dvě verze zavedli iteraci. Nové prostředí je teď ve výchozím nastavení zapnuté pro všechny. Z nové nabídky Git můžete klonovat, vytvářet nebo otevírat úložiště. Pomocí integrovaných oken nástroje Git můžete zapsat a doručovat změny kódu, spravovat větve, udržovat aktuální úložiště pomocí vzdálených úložišť a vyřešit konflikty sloučení.

další informace najdete na stránce věnované [prostředí Git na Visual Studio](../version-control/git-with-visual-studio.md) .

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) je služba pro vývojáře, která umožňuje sdílet základ kódu a jeho kontext s společník a získat rychlou obousměrnou spolupráci přímo v rámci Visual Studio. pomocí Live Share může společník číst, procházet, upravovat a ladit projekt, který s nimi sdílíte, a dělat plynule a bezpečně.

a s Visual Studio 2019 je tato služba ve výchozím nastavení nainstalovaná.

![animace, která zobrazuje funkci Live Share spolupráci v Visual Studio 2019](media/vs-2019/live-share.gif "funkce spolupráce Live Share v Visual Studio 2019.")

další informace najdete na blogu [Visual Studio Live Share pro revize kódu v reálném čase a interaktivní vzdělávání](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) a [Live Share nyní obsahuje](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) blogový příspěvek Visual Studio 2019.

### <a name="integrated-code-reviews"></a>Integrované revize kódu

zavádíme nové rozšíření, které můžete stáhnout pro použití s Visual Studio 2019. S tímto novým rozšířením můžete zkontrolovat, spustit a dokonce ladit žádosti o přijetí změn od týmu, aniž byste museli opustit Visual Studio. podporujeme kód v úložištích GitHub i Azure DevOps.

   ![snímek obrazovky s novým rozšířením žádostí o přijetí změn v Visual Studio 2019](media/vs-2019/pr-experience.png "nové rozšíření žádosti o přijetí změn v Visual Studio 2019.")

další informace najdete v příspěvku na blogu o [rozšířeních žádostí o přijetí změn pomocí Visual Studio](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) .

## <a name="debug"></a>Ladění

Podívejte se na následující video, kde se dozvíte víc o tom, jak můžete s přesným cílem v průběhu ladění vynulovat. <br><br>*Délka videa: 3,54 minut*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Nárůst výkonu

Provedli jsme stejné zarážky dat C++ a přizpůsobovat je pro aplikace .NET Core.

   ![animace, která zobrazuje zarážky dat ladění v Visual Studio 2019](media/vs-2019/debug-data-breakpoints.gif "zarážky ladicích dat v Visual Studio 2019.")

Takže pokud píšete v jazyce C++ nebo .NET Core, mohou být datové zarážky dobrým alternativou pouze při umísťování běžných zarážek. Datové zarážky jsou také skvělé pro scénáře, jako je například hledání, kde se v seznamu mění nebo přidávají nebo odebírají globální objekty.

a, pokud jste vývojář jazyka C++, který vyvíjí velké aplikace, Visual Studio 2019 převedl symboly mimo proces, což vám umožní ladit tyto aplikace bez potíží souvisejících s pamětí.

### <a name="search-while-debugging"></a>Hledat během ladění

Pravděpodobně jste to předtím, a to v okno Kukátko pro řetězec mezi sadou hodnot. v Visual Studio 2019 jsme přidali hledání v oknech kukátko, místní hodnoty a automatické hodnoty, které vám pomůžou najít objekty a hodnoty, které hledáte.

   ![animace, která zobrazuje okno hledání ladění v Visual Studio 2019](media/vs-2019/debug-window-search.gif "okno hledání ladění v Visual Studio 2019.")

Můžete také formátovat, jak se hodnota zobrazuje v oknech kukátko, místní hodnoty a automatické hodnoty. Vyberte (dvojitým kliknutím) jednu z položek v některém z oken a přidejte čárku (",") pro přístup k rozevíracímu seznamu možných specifikátorů formátu, z nichž každý obsahuje popis zamýšleného efektu.

   ![funkce new okno Kukátko a format values v Visual Studio 2019](media/search-watch-window.png "funkce new okno Kukátko a format hodnoty v Visual Studio 2019.")

další informace najdete v tématu [vylepšená v Visual Studio 2019: hledání objektů a vlastností v příspěvku sledování, automatické hodnoty a místní hodnoty Windows](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) na blogu.

### <a name="snapshot-debugger"></a>Ladicí program snímků

Získejte snímek provádění vaší aplikace v cloudu, abyste viděli přesně to, co se děje. (tato funkce je k dispozici pouze v Visual Studio Enterprise.)

   ![animace, která zobrazuje Snapshot Debugger v Visual Studio 2019 Enterprise](media/vs-2019/snapshot-debugger.gif "Snapshot Debugger v Visual Studio 2019 Enterprise.")

přidali jsme podporu pro cílení aplikací ASP.NET (základní a desktopové), které běží na virtuálním počítači Azure. A přidali jsme podporu pro aplikace, které běží ve službě Azure Kubernetes. Snapshot Debugger vám může výrazně zkrátit dobu potřebnou k vyřešení problémů, ke kterým dochází v produkčních prostředích.

další informace najdete v blogovém příspěvku [ladění živých ASP.NET aplikací Azure pomocí Snapshot Debugger](../debugger/debug-live-azure-applications.md) stránky a [zavedení času pro cestovní ladění pro Visual Studio Enterprise 2019](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) .

### <a name="microsoft-edge-insider-support"></a>Podpora prohlížeče Microsoft Edge Insider

**novinka v 16,2**: můžete nastavit zarážku v aplikaci javascriptu a spustit relaci ladění pomocí prohlížeče [Microsoft Edge Insider](https://www.microsoftedgeinsider.com/) . když to uděláte, Visual Studio otevře nové okno prohlížeče s povoleným laděním, které pak můžete použít ke krokování v aplikaci JavaScript aplikace v rámci Visual Studio.

   ![Snímek obrazovky, který zobrazuje vykreslování kódu JavaScriptu v prohlížeči](media/vs-2019/edge-chromium-breakpoint.png "Vykreslování kódu JavaScriptu v prohlížeči")

### <a name="pinnable-properties-tool"></a>Nástroj Pinnable Properties

**Novinka v 16,4**: teď je snazší identifikovat objekty podle jejich vlastností při ladění pomocí nového nástroje Pinnable Properties. Stačí umístit ukazatel myši na vlastnost, kterou chcete zobrazit v okně ladicího programu okna Kukátko, automatické hodnoty a místní hodnoty, vyberte ikonu připnutí a okamžitě zobrazte informace, které hledáte v horní části okna.

   ![animace, která ukazuje, jak připnout vlastnosti v ladicím programu Visual Studio pomocí nástroje vlastnosti Pinnable](media/vs-2019/debugger-pinnable-properties.gif "vlastnosti Pin kódu v ladicím programu Visual Studio pomocí nástroje Pinnable properties tool.")

Další informace najdete v tématu [vlastnosti Pinnable: Debug & zobrazit spravované objekty podle svého příspěvku na](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/) blogu.

## <a name="whats-next"></a>Kam dál

Visual Studio často aktualizujeme novými funkcemi, které můžou zlepšit vývojové prostředí. další informace o našich nejnovějších inovacích najdete na [blogu Visual Studio](https://devblogs.microsoft.com/visualstudio/). Záznam o tom, co jsme vydali v předběžné verzi Preview, najdete v [poznámkách k verzi Preview](/visualstudio/releases/2019/release-notes-preview/). seznam toho, co plánujeme vydávat dál, najdete v tématu [přehled Visual Studio](/visualstudio/productinfo/vs-roadmap).

V současné době teď co je v sadě Works:

- **vylepšené prostředí pro Git v Visual Studio 2019 (Preview)**

   i když je nástroj pro správu verzí Git výchozím prostředím v Visual Studio 2019 [verze 16,8](/visualstudio/releases/2019/release-notes-history/) nebo novější, pořád ještě přidáváme funkce pro vylepšení prostředí verze preview Visual Studio 2019, [verze 16,11](/visualstudio/releases/2019/release-notes-preview/).

   další informace naleznete v tématu [správa verzí na stránce Visual Studio](/visualstudio/version-control/) .

- **k dispozici je teď Visual Studio 2022 (Preview).**

    naše nejnovější verze, [Visual Studio 2022 (Preview)](/visualstudio/releases/2022/release-notes-preview/) , je rychlejší, mnohem jednodušší a jednodušší. a v první době je Visual Studio 64-bit.

    odkaz na stažení a další informace najdete v příspěvku blogu **[Visual Studio 2022 vision](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/)** .

## <a name="give-us-feedback"></a>Sdělte nám svůj názor

proč odesílat zpětnou vazbu týmu Visual Studio? Vzhledem k tomu, že povedeme zpětnou vazbu zákazníků. To zahrnuje mnoho toho, co máme.

* pokud chcete udělat nějaký návrh, jak můžeme vylepšit Visual Studio, můžete to udělat pomocí nástroje [navrhnout funkci](suggest-a-feature.md) .

* pokud dojde k potížím, když Visual Studio přestane reagovat, dojde k selhání nebo k jinému problému s výkonem, můžete pomocí nástroje [nahlásit problém](how-to-report-a-problem-with-visual-studio.md) snadno sdílet reprodukci kroky a podpůrné soubory s námi.

## <a name="see-also"></a>Viz také

* [co je nového v Visual Studio docs](whats-new-visual-studio-docs.md)
* [zpráva k vydání verze Visual Studio 2019](/visualstudio/releases/2019/release-notes/)
* [poznámky k verzi Visual Studio 2019 pro Mac](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [co je nového v sadě Visual Studio 2019 SDK](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Novinky v jazyce C++ v sadě Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio/)
* [Co je nového v jazyce C# 9,0](/dotnet/csharp/whats-new/csharp-9)
* [Co je nového v .NET 5](/dotnet/core/dotnet-five)
* [Co je nového v .NET Framework](/dotnet/framework/whats-new/)
* [Konference Microsoftu o sestavení](https://www.microsoft.com/build)
* [Microsoft Ignite conference](https://www.microsoft.com/ignite)
