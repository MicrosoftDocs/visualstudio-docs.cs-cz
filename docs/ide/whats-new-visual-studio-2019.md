---
title: Novinky v sadě Visual Studio 2019
titleSuffix: ''
description: Seznamte se s novými funkcemi v aplikaci Visual Studio 2019.
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
ms.openlocfilehash: d34c3a3b4d808b1f4e24051763f1c0876a175a3a
ms.sourcegitcommit: a9526ab1556c47570286c7a7d3314af67fd1dcf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2021
ms.locfileid: "112365466"
---
# <a name="whats-new-in-visual-studio-2019"></a>Novinky v sadě Visual Studio 2019

**Aktualizováno pro verzi 16,10.** Zobrazit [úplné poznámky k verzi](/visualstudio/releases/2019/release-notes/) | Zobrazit [Plán produktu](/visualstudio/productinfo/vs-roadmap)

>[!div class="button"]
>[Stáhněte si Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

V rámci sady Visual Studio 2019 získáte špičkové nástroje a služby pro všechny vývojáře, aplikace a platformy. Bez ohledu na to, jestli používáte aplikaci Visual Studio poprvé nebo jste ji používali pro roky, máme v naší nejnovější verzi spoustu.

Tady je rekapitulace, co je nového, vše na nejvyšší úrovni:

* **[Vývoj](#develop)**: zlepšení výkonu, okamžitého vyčištění kódu a lepších výsledků hledání díky lepšímu vývoji a produktivitě.
* **[Spolupráce](#collaborate)**: Využijte přirozenou spolupráci pomocí pracovního postupu Git-First, úpravy a ladění v reálném čase a revize kódu přímo v aplikaci Visual Studio.
* **[Ladění](#debug)**: zvýrazněte a přejděte na konkrétní hodnoty, optimalizujte využití paměti a proveďte automatické snímky provádění vaší aplikace.

Úplný seznam všeho, co je v této verzi nové, najdete v [poznámkách k verzi](/visualstudio/releases/2019/release-notes/).

## <a name="develop"></a>Vývoj

Podívejte se na následující video, kde se dozvíte víc o tom, jak můžete ušetřit čas pomocí nových funkcí. <br><br>*Délka videa: 3,00 minut*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>Vylepšené vyhledávání

Dříve označované jako rychlé spuštění je naše nové vyhledávání rychlejší a efektivnější. Nyní se při psaní zobrazí výsledky hledání dynamicky. Výsledky hledání mohou často zahrnovat klávesové zkratky pro příkazy, takže je můžete nepamatují pro budoucí použití.

   ![Animace nového vyhledávacího prostředí v aplikaci Visual Studio 2019](media/vs-2019/new-search-feature.gif "Nové vyhledávací prostředí v Visual Studio 2019.")

Nová logika přibližného vyhledávání bude najít cokoli, co potřebujete, bez ohledu na překlepy. To znamená, že pokud hledáte příkazy, nastavení, dokumentaci nebo jiné užitečné věci, nová funkce vyhledávání usnadňuje hledání, co hledáte.

Další informace najdete v tématu [Použití vyhledávání v aplikaci Visual Studio](visual-studio-search.md).

#### <a name="intelligent-search-service"></a>Služba inteligentního vyhledávání

**Novinka v 16,9**: pomocí technologie založené na cloudu, umělé Intelligence a strojového učení jsme vylepšili výsledky hledání. V aplikaci Visual Studio teď není k dismnožější výsledky, ale je možné, že vám také umožní snadněji zjistit funkce produktu.

Další informace najdete v příspěvku na blogu [inteligentní vyhledávací služba sady Visual Studio](https://devblogs.microsoft.com/visualstudio/intelligent-visual-studio-search-service/) .

### <a name="refactorings"></a>Refaktoring

V jazyce C# existuje spousta nových a velmi užitečných refaktoringů, které usnadňují uspořádání kódu. Zobrazují se jako návrhy v žárovkě a zahrnují akce jako přesunutí členů do rozhraní nebo základní třídy, úpravy oborů názvů tak, aby odpovídaly struktuře složek, převedení smyček foreach na dotazy LINQ a další.

   ![Animace prostředí refaktoringu v aplikaci Visual Studio 2019](media/vs-2019/refactorings.gif "Prostředí refaktoringu v Visual Studio 2019.")

Jednoduše volejte refaktoring stisknutím **kombinace kláves CTRL +.** a vyberte akci, kterou chcete provést.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) vylepšuje úsilí při vývoji softwaru pomocí umělé Intelligence (AI). IntelliCode vlaky napříč 2 000 open source projektů na GitHubu &mdash; každý s více než 100 hvězdičkami &mdash; , aby vygenerovala doporučení.

![Animace IntelliCode ve Visual Studiu 2019](media/vs-2019/IntelliCode.gif "IntelliCode v Visual Studio 2019.")

Tady je několik způsobů, jak může Visual Studio IntelliCode přispět k lepší produktivitě:

* Doručovat dokončování kódu s ohledem na kontext
* Příručka pro vývojáře, aby dodržovala vzory a styly jejich týmu
* Hledání problémů s kódem, který se špatně zachytí
* Zaměřte se na revize kódu tím, že vykreslíte pozornost oblastí, které skutečně jsou

Po prvním zobrazení IntelliCode jako rozšíření pro Visual Studio jsme původně podporovali jenom C#. **Novinka v 16,1** jsme přidali podporu pro C# a XAML "in-the-box". (Podpora pro C++ a TypeScript/JavaScript je však stále ve verzi Preview.)

A pokud používáte jazyk C#, Přidali jsme také možnost naučit se vlastní model ve vlastním kódu.

Další informace o IntelliCode najdete v tématu popisujícím [obecnou dostupnost IntelliCode a také vás zajímá náhled](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) a [Další kód. Posuňte se dál pomocí příspěvků Visual studia IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) na blogu.

### <a name="code-cleanup"></a>Vyčištění kódu

Párování s novým indikátorem stavu dokumentu je nový příkaz pro vyčištění kódu. Pomocí tohoto nového příkazu můžete identifikovat a opravit upozornění i návrhy s jednou akcí (nebo kliknutím na tlačítko).

Vyčištění naformátuje kód a použije všechny opravy kódu navrhované [aktuálním nastavením](code-styles-and-code-cleanup.md) a [soubory. editorconfig](create-portable-custom-editor-options.md).

   ![Snímek obrazovky nového ovládacího prvku pro vyčištění kódu v aplikaci Visual Studio 2019](media/vs-2019/code-cleanup-profile.png "Nový ovládací prvek vyčištění kódu v Visual Studio 2019.")

Kolekce analyzérů můžete také ukládat jako profil. Například pokud máte malou sadu cílových analyzérů, kterou použijete často během kódu a pak máte další komplexní sadu analyzérů, která se má použít před revizí kódu, můžete nakonfigurovat profily pro řešení těchto různých úloh.

   ![Snímek obrazovky s ovládacím prvkem pro konfiguraci vyčištění kódu v aplikaci Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png "Ovládací prvek konfigurace čištění kódu v Visual Studio 2019.")

### <a name="per-monitor-aware-pma-rendering"></a>Vykreslování PMA (per-monitor)

Pokud používáte monitory, které jsou nakonfigurované s různými faktory měřítka zobrazení, nebo se vzdáleně připojit k počítači se zobrazenými faktory škálování, které se liší od vašeho hlavního zařízení, můžete si všimnout, že Visual Studio vypadá rozmazaný nebo vykreslený v nesprávném měřítku.

S vydáním sady Visual Studio 2019 provádíme aplikaci Visual Studio a PMA (per-monitor). Nyní se Visual Studio vykresluje správně bez ohledu na to, jaké faktory škálování displeje používáte.

   ![Vykreslování PMA (per-monitor) v aplikaci Visual Studio 2019](media/vs-2019/pma-dpi-scaling.png "Vykreslování pma (per-monitor aware) v Visual Studio 2019")

Další informace najdete v blogovém příspěvku o [lepším prostředí pro více monitorů v rámci sady Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) .

### <a name="test-explorer"></a>Průzkumník testů

**Novinka v 16,2**: Aktualizovali jsme Průzkumníka testů, abychom zajistili lepší zacházení s velkými testovacími sadami, jednodušším filtrováním, více zjistitelnými příkazy, zobrazeními seznamu skladeb na kartách a přizpůsobitelnými sloupci, které vám umožní doladit informace o tom, jaké informace o testu se zobrazují.

   ![Snímek obrazovky, který zobrazuje vylepšení uživatelského rozhraní v Průzkumníku testů](media/vs-2019/test-explorer-ui.png "Vylepšení uživatelského rozhraní v Průzkumníku testů")

### <a name="net-core"></a>.NET Core

**Novinka v 16,3**: zahrnuli jsme podporu pro .net Core 3,0. Pro různé platformy, open source &mdash; a plně podporované Microsoftem.

Další informace najdete v příspěvku na blogu o [.NET Core 3,0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/) .

## <a name="collaborate"></a>Spolupráce

Podívejte se na následující video, kde se dozvíte víc o tom, jak se dá tým seskupit a vyřešit problémy. <br><br>*Délka videa: 4,22 minut*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Pracovní postup Git – první

Něco, co si všimnete při otevření sady Visual Studio 2019, je nové úvodní okno.

   ![Snímek obrazovky s novým oknem Start v aplikaci Visual Studio 2019](media/vs-2019/start-window-dark.png "Nové úvodní okno v Visual Studio 2019.")

Okno Start nabízí několik možností, jak rychle získat kód. Umístili jsme možnost klonovat nebo rezervovat kód z úložiště, nejdřív.

   ![Animace prostředí Git-First v aplikaci Visual Studio 2019](media/vs-2019/git-first.gif "Prostředí Git-first ve Visual Studio 2019")

Okno Start také obsahuje možnosti pro otevření projektu nebo řešení, otevření místní složky nebo vytvoření nového projektu.

Další informace najdete v tématu [získání kódu: jak jsme navrhli nový Blogový příspěvek pro úvodní okno sady Visual Studio](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) .

### <a name="git-productivity"></a>Produktivita Git

**Novinka ve verzi 16,8**: Git je teď výchozím prostředím pro řízení verzí v aplikaci Visual Studio 2019. Sestavili jsme sadu funkcí a na ni jste na základě vašich názorů za poslední dvě verze zavedli iteraci. Nové prostředí je teď ve výchozím nastavení zapnuté pro všechny. Z nové nabídky Git můžete klonovat, vytvářet nebo otevírat úložiště. Pomocí integrovaných oken nástroje Git můžete zapsat a doručovat změny kódu, spravovat větve, udržovat aktuální úložiště pomocí vzdálených úložišť a vyřešit konflikty sloučení.

Další informace najdete na stránce věnované [prostředí Git](../version-control/git-with-visual-studio.md) na stránce sady Visual Studio.

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) je služba pro vývojáře, která umožňuje sdílet základ kódu a jeho kontext s společník a získat rychlou obousměrnou spolupráci přímo v rámci sady Visual Studio. Pomocí Live Share může společník číst, Procházet, upravovat a ladit projekt, který s nimi sdílíte, a dělat plynule a bezpečně.

A v rámci sady Visual Studio 2019 je tato služba nainstalována ve výchozím nastavení.

![Animace, která zobrazuje funkci Live Share spolupráci v aplikaci Visual Studio 2019](media/vs-2019/live-share.gif "Funkce Live Share spolupráce v Visual Studio 2019.")

Další informace najdete v příspěvku na blogu [Visual Studio Live Share pro revize kódu v reálném čase a](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) v příspěvku na blogu o interaktivním vzdělávání a v příspěvku na blogu [Live Share sady Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) .

### <a name="integrated-code-reviews"></a>Integrované revize kódu

Zavádíme nové rozšíření, které můžete stáhnout pro použití se sadou Visual Studio 2019. S tímto novým rozšířením můžete kontrolovat, spouštět a dokonce ladit žádosti o přijetí změn od týmu bez nutnosti opustit Visual Studio. Podporujeme kód v úložištích GitHub a Azure DevOps.

   ![Snímek obrazovky s novými rozšířeními žádostí o přijetí změn v aplikaci Visual Studio 2019](media/vs-2019/pr-experience.png "Nové rozšíření Pull Requests v roce Visual Studio 2019.")

Další informace najdete v příspěvku na blogu o [revizích kódu pomocí rozšíření pro žádosti o získání dat v aplikaci Visual Studio](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) .

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

    Veřejná verze Preview naší další hlavní verze, [Visual Studio 2022,](/visualstudio/releases/2022/release-notes-preview/)je nyní k dispozici. Nová verze je rychlejší, přístupnější a zjednodušenější. A vůbec poprvé je Visual Studio 64 bitů. Odkaz ke stažení a další informace najdete na Visual Studio **[2022 Preview 1.](https://devblogs.microsoft.com/visualstudio/visual-studio-2022-preview-1-now-available/)** Blogu.

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
