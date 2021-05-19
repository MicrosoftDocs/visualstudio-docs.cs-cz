---
title: Novinky v sadě Visual Studio 2019
titleSuffix: ''
description: Seznamte se s novými funkcemi v aplikaci Visual Studio 2019.
ms.date: 03/19/2021
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
ms.openlocfilehash: 72b97b87a7edd8fdba46b755b7253af62f6de39f
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973463"
---
# <a name="whats-new-in-visual-studio-2019"></a>Novinky v sadě Visual Studio 2019

**Aktualizováno pro [verzi 16,9](/visualstudio/releases/2019/release-notes/)**

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

   ![Animace nového vyhledávacího prostředí v aplikaci Visual Studio 2019](media/vs-2019/new-search-feature.gif "Nové možnosti vyhledávání v aplikaci Visual Studio 2019.")

Nová logika přibližného vyhledávání bude najít cokoli, co potřebujete, bez ohledu na překlepy. To znamená, že pokud hledáte příkazy, nastavení, dokumentaci nebo jiné užitečné věci, nová funkce vyhledávání usnadňuje hledání, co hledáte.

Další informace najdete v tématu [Použití vyhledávání v aplikaci Visual Studio](visual-studio-search.md).

#### <a name="intelligent-search-service"></a>Služba inteligentního vyhledávání

**Novinka ve službě 16.9:** S využitím technologie využívající cloud, umělé inteligence a strojového učení jsme vylepšili výsledky hledání. Teď nejen že vyhledávání v Visual Studio relevantnější výsledky, ale může vám také pomoct snadněji objevit funkce produktu.

Další informace najdete v blogovém [příspěvku Intelligent Visual Studio Search](https://devblogs.microsoft.com/visualstudio/intelligent-visual-studio-search-service/) Service.

### <a name="refactorings"></a>Refaktoring

V jazyce C# existuje spousta nových a velmi užitečných refaktoringů, které usnadňují uspořádání kódu. Zobrazují se jako návrhy v žárovkě a zahrnují akce, jako je přesun členů do rozhraní nebo základní třídy, úprava oborů názvů tak, aby odpovídaly struktuře složek, převod smyček foreach na dotazy Linq a další.

   ![Animace prostředí refaktoringu v Visual Studio 2019](media/vs-2019/refactorings.gif "Prostředí refaktoringu v aplikaci Visual Studio 2019.")

Refaktoring jednoduše vyvoláte stisknutím **kláves Ctrl+.** a vyberte akci, kterou chcete provést.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) vylepšuje vaše úsilí o vývoj softwaru pomocí umělé inteligence (AI). IntelliCode se na GitHubu trénuje na 2 000 open source projektů s více než &mdash; 100 hvězdičkami, aby &mdash; vygeneroval doporučení.

![Animace IntelliCode v Visual Studio 2019](media/vs-2019/IntelliCode.gif "IntelliCode v aplikaci Visual Studio 2019.")

Tady je několik způsobů, jak Visual Studio IntelliCode může pomoct zvýšit produktivitu:

* Doručování dokončování kódu s kontextem
* Navedení vývojářů na dodržování vzorů a stylů jejich týmu
* Vyhledání problémů s kódem, který se obtížně zachytá
* Zaměřte se na recenze kódu tím, že upoutáte pozornost na oblasti, na kterých skutečně záleží.

Původně jsme podporovali pouze C# při prvním zobrazení náhledu IntelliCode jako rozšíření pro Visual Studio. Nově ve **windows 16.1** jsme přidali podporu pro C# a XAML "in-the-box". (Podpora pro C++ a TypeScript/JavaScript je ale stále ve verzi Preview.)

A pokud používáte jazyk C#, přidali jsme také možnost vytrénovat vlastní model na vašem vlastním kódu.

Další informace o IntelliCode najdete v tématu popisujícím [obecnou dostupnost IntelliCode a také vás zajímá náhled](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) a [Další kód. Posuňte se dál pomocí příspěvků Visual studia IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) na blogu.

### <a name="code-cleanup"></a>Vyčištění kódu

Párování s novým indikátorem stavu dokumentu je nový příkaz pro vyčištění kódu. Pomocí tohoto nového příkazu můžete identifikovat a opravit upozornění i návrhy s jednou akcí (nebo kliknutím na tlačítko).

Vyčištění naformátuje kód a použije všechny opravy kódu navrhované [aktuálním nastavením](code-styles-and-code-cleanup.md) a [soubory. editorconfig](create-portable-custom-editor-options.md).

   ![Snímek obrazovky nového ovládacího prvku pro vyčištění kódu v aplikaci Visual Studio 2019](media/vs-2019/code-cleanup-profile.png "Nový ovládací prvek pro vyčištění kódu v aplikaci Visual Studio 2019.")

Kolekce analyzérů můžete také ukládat jako profil. Například pokud máte malou sadu cílových analyzérů, kterou použijete často během kódu a pak máte další komplexní sadu analyzérů, která se má použít před revizí kódu, můžete nakonfigurovat profily pro řešení těchto různých úloh.

   ![Snímek obrazovky s ovládacím prvkem pro konfiguraci vyčištění kódu v aplikaci Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png "Konfigurace ovládacího prvku pro vyčištění kódu v aplikaci Visual Studio 2019.")

### <a name="per-monitor-aware-pma-rendering"></a>Vykreslování PMA (per-monitor)

Pokud používáte monitory, které jsou nakonfigurované s různými faktory měřítka zobrazení, nebo se vzdáleně připojit k počítači se zobrazenými faktory škálování, které se liší od vašeho hlavního zařízení, můžete si všimnout, že Visual Studio vypadá rozmazaný nebo vykreslený v nesprávném měřítku.

S vydáním sady Visual Studio 2019 provádíme aplikaci Visual Studio a PMA (per-monitor). Nyní se Visual Studio vykresluje správně bez ohledu na to, jaké faktory škálování displeje používáte.

   ![Vykreslování PMA (per-monitor) v aplikaci Visual Studio 2019](media/vs-2019/pma-dpi-scaling.png "Vykreslování PMA (per-monitor) v aplikaci Visual Studio 2019.")

Další informace najdete v blogovém příspěvku o [lepším prostředí pro více monitorů v rámci sady Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) .

### <a name="test-explorer"></a>Průzkumník testů

**Novinka v 16,2**: Aktualizovali jsme Průzkumníka testů, abychom zajistili lepší zacházení s velkými testovacími sadami, jednodušším filtrováním, více zjistitelnými příkazy, zobrazeními seznamu skladeb na kartách a přizpůsobitelnými sloupci, které vám umožní doladit informace o tom, jaké informace o testu se zobrazují.

   ![Snímek obrazovky, který zobrazuje vylepšení uživatelského rozhraní v Průzkumníku testů](media/vs-2019/test-explorer-ui.png "Vylepšení uživatelského rozhraní v Průzkumníku testů.")

### <a name="net-core"></a>.NET Core

**Novinka ve verzi 16.3:** Zahrneme podporu pro .NET Core 3.0. Mezi platformami, open source &mdash; a plně podporuje Microsoft.

Další informace najdete v blogovém příspěvku o oznámení [.NET Core 3.0.](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/)

## <a name="collaborate"></a>Spolupráce

Podívejte se na následující video, kde najdete další informace o tom, jak se můžete sesoučovat a řešit problémy. <br><br>*Délka videa: 4,22 minuty*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Pracovní postup git-first

Něco, co si všimnete, když otevřete Visual Studio 2019 je jeho nové úvodní okno.

   ![Snímek obrazovky nového úvodního okna v Visual Studio 2019](media/vs-2019/start-window-dark.png "Nové okno Start v aplikaci Visual Studio 2019.")

V úvodním okně se zobrazí několik možností, jak rychle kódovat. Nejprve jsme umístili možnost klonování nebo rezervujení kódu z repo.

   ![Animace prostředí Git-first v roce Visual Studio 2019](media/vs-2019/git-first.gif "Prostředí Git-First v aplikaci Visual Studio 2019.")

Úvodní okno obsahuje také možnosti otevření projektu nebo řešení, otevření místní složky nebo vytvoření nového projektu.

Další informace najdete v blogovém příspěvku Get to code: How we designed the new Visual Studio start window (Získat kód: Jak jsme navrhli nový Visual Studio [úvodním okně).](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/)

### <a name="git-productivity"></a>Produktivita Gitu

**Novinka ve verzi 16.8:** Git je teď výchozím prostředím pro řízení verzí Visual Studio 2019. Tuto sadu funkcí jsme vybudovali a iterovali na základě vaší zpětné vazby v posledních dvou verzích. Nové prostředí je teď ve výchozím nastavení zapnuté pro všechny. V nové nabídce Gitu můžete klonovat, vytvářet nebo otevírat úložiště. Pomocí integrovaných oken nástrojů Git můžete potvrdit a vložit změny do kódu, spravovat větve, mít aktuální vzdálené úložiště a řešit konflikty při slučování.

Další informace najdete v tématu Prostředí [Git na Visual Studio](../version-control/git-with-visual-studio.md) stránce.

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) je služba pro vývojáře, která umožňuje sdílet základ kódu a jeho kontext s společník a získat rychlou obousměrnou spolupráci přímo v rámci sady Visual Studio. Pomocí Live Share může společník číst, Procházet, upravovat a ladit projekt, který s nimi sdílíte, a dělat plynule a bezpečně.

A v rámci sady Visual Studio 2019 je tato služba nainstalována ve výchozím nastavení.

![Animace, která zobrazuje funkci Live Share spolupráci v aplikaci Visual Studio 2019](media/vs-2019/live-share.gif "Funkce spolupráce Live Share v aplikaci Visual Studio 2019.")

Další informace najdete v příspěvku na blogu [Visual Studio Live Share pro revize kódu v reálném čase a](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) v příspěvku na blogu o interaktivním vzdělávání a v příspěvku na blogu [Live Share sady Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) .

### <a name="integrated-code-reviews"></a>Integrované revize kódu

Zavádíme nové rozšíření, které můžete stáhnout pro použití se sadou Visual Studio 2019. S tímto novým rozšířením můžete kontrolovat, spouštět a dokonce ladit žádosti o přijetí změn od týmu bez nutnosti opustit Visual Studio. Podporujeme kód v úložištích GitHub a Azure DevOps.

   ![Snímek obrazovky s novými rozšířeními žádostí o přijetí změn v aplikaci Visual Studio 2019](media/vs-2019/pr-experience.png "Nové rozšíření žádosti o přijetí změn v aplikaci Visual Studio 2019.")

Další informace najdete v příspěvku na blogu o [revizích kódu pomocí rozšíření pro žádosti o získání dat v aplikaci Visual Studio](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) .

## <a name="debug"></a>Ladění

Podívejte se na následující video, kde se dozvíte víc o tom, jak můžete s přesným cílem v průběhu ladění vynulovat. <br><br>*Délka videa: 3,54 minut*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Nárůst výkonu

Provedli jsme stejné zarážky dat C++ a přizpůsobovat je pro aplikace .NET Core.

   ![Animace, která zobrazuje zarážky dat ladění v aplikaci Visual Studio 2019](media/vs-2019/debug-data-breakpoints.gif "Zarážky ladicích dat v aplikaci Visual Studio 2019.")

Takže pokud píšete v jazyce C++ nebo .NET Core, mohou být datové zarážky dobrým alternativou pouze při umísťování běžných zarážek. Datové zarážky jsou také skvělé pro scénáře, jako je například hledání, kde se v seznamu mění nebo přidávají nebo odebírají globální objekty.

A pokud jste vývojář C++, který vyvíjí velké aplikace, sady Visual Studio 2019 převedly symboly mimo proces, což vám umožní ladit tyto aplikace bez potíží souvisejících s pamětí.

### <a name="search-while-debugging"></a>Hledat během ladění

Pravděpodobně jste to předtím, a to v okno Kukátko pro řetězec mezi sadou hodnot. V aplikaci Visual Studio 2019 jsme přidali hledání v oknech kukátko, místní hodnoty a automatické hodnoty, které vám pomůžou najít objekty a hodnoty, které hledáte.

   ![Animace, která zobrazuje okno hledání ladění v aplikaci Visual Studio 2019](media/vs-2019/debug-window-search.gif "Okno hledání ladění v Visual Studio 2019.")

Můžete také formátovat, jak se hodnota zobrazuje v oknech kukátko, místní hodnoty a automatické hodnoty. Vyberte (dvojitým kliknutím) jednu z položek v některém z oken a přidejte čárku (",") pro přístup k rozevíracímu seznamu možných specifikátorů formátu, z nichž každý obsahuje popis zamýšleného efektu.

   ![Funkce New okno Kukátko a Format Values v aplikaci Visual Studio 2019](media/search-watch-window.png "Nová funkce okno Kukátko a formátování hodnot v Visual Studio 2019.")

Další informace najdete v tématu [Vylepšená v aplikaci Visual Studio 2019: hledání objektů a vlastností v příspěvku na blogu sledování, automatické hodnoty a místní hodnoty v systému Windows](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) .

### <a name="snapshot-debugger"></a>Ladicí program snímků

Získejte snímek provádění vaší aplikace v cloudu, abyste viděli přesně to, co se děje. (Tato funkce je k dispozici pouze v Visual Studio Enterprise.)

   ![Animace, která zobrazuje Snapshot Debugger v aplikaci Visual Studio 2019 Enterprise](media/vs-2019/snapshot-debugger.gif "The Snapshot Debugger in Visual Studio 2019 Enterprise.")

Přidali jsme podporu pro cílení aplikací ASP.NET (základní a desktopové), které běží na virtuálním počítači Azure. A přidali jsme podporu pro aplikace, které běží ve službě Azure Kubernetes. Snapshot Debugger vám může výrazně zkrátit dobu potřebnou k vyřešení problémů, ke kterým dochází v produkčních prostředích.

Další informace najdete v článku [ladění živých ASP.NET aplikací Azure pomocí stránky Snapshot Debugger](../debugger/debug-live-azure-applications.md) a na blogovém příspěvku [pro Visual Studio Enterprise 2019 s časem zavedení](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) .

### <a name="microsoft-edge-insider-support"></a>Podpora prohlížeče Microsoft Edge Insider

**Novinka v 16,2**: můžete nastavit zarážku v aplikaci JavaScriptu a spustit ladicí relaci pomocí prohlížeče [Microsoft Edge Insider](https://www.microsoftedgeinsider.com/) . Když to uděláte, Visual Studio otevře nové okno prohlížeče s povoleným laděním, které pak můžete použít ke krokování v aplikaci JavaScript aplikace v sadě Visual Studio.

   ![Snímek obrazovky znázorňuje vykreslování kódu JavaScriptu v prohlížeči](media/vs-2019/edge-chromium-breakpoint.png "Vykreslování kódu JavaScriptu v prohlížeči")

### <a name="pinnable-properties-tool"></a>Nástroj Pinnable Properties (Připnutelné vlastnosti)

**Novinka ve verzi 16.4:** Nyní je snazší identifikovat objekty podle jejich vlastností při ladění pomocí nového nástroje Připnoutelné vlastnosti. Stačí najet myší na vlastnost, kterou chcete zobrazit v okně ladicího programu oken Sledovat, Automatické hodnoty a Místní hodnoty, vybrat ikonu připínáčky a okamžitě zobrazit informace, které hledáte v horní části okna.

   ![Animace, která ukazuje, jak připnout vlastnosti v ladicím Visual Studio pomocí nástroje Připnoutelné vlastnosti](media/vs-2019/debugger-pinnable-properties.gif "Připnutí vlastností v Visual Studio ladicím programu pomocí nástroje Připnoutelné vlastnosti.")

Další informace najdete v blogovém [příspěvku Pinnable Properties: Debug & Display Managed Objects YOUR Way (Připnoutelné vlastnosti:](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/) Ladit spravované objekty ve vašem způsobu).

## <a name="whats-next"></a>Kam dál

Často aktualizujeme Visual Studio 2019 o nové funkce, které vám posouží ještě lepší vývojové prostředí. Další informace o našich nejnovějších inovacích najdete na Visual Studio [Blog.](https://devblogs.microsoft.com/visualstudio/) Záznam toho, co jsme dote doby vydali ve verzi Preview, si můžete prohlédnout ve zprávě k [vydání verze Preview.](/visualstudio/releases/2019/release-notes-preview/) A seznam toho, co plánujeme vydat jako další, najdete na [Visual Studio plán.](/visualstudio/productinfo/vs-roadmap)

Mezitím je tu nová funkce, která v současnosti funguje.

- **Vylepšené prostředí Gitu v Visual Studio 2019 (Preview)**

   I když je nové prostředí pro řízení verzí Git ve výchozím nastavení ve verzi [16.8](/visualstudio/releases/2019/release-notes/)Visual Studio 2019, nadále přidávají funkce, které vylepšují prostředí v nejnovější verzi Preview.

   Další informace najdete v tématu [o řízení verzí na Visual Studio.](/visualstudio/version-control/)

Další informace o verzi Preview a odkaz ke stažení, pokud si ho chcete vyzkoušet, najdete na &mdash; &mdash; **[Visual Studio Preview](https://aka.ms/vspreview/)** stránky.

## <a name="give-us-feedback"></a>Sdělte nám svůj názor

Proč posílat zpětnou vazbu Visual Studio týmu? Protože zpětnou vazbu zákazníků bereme vážně. Řídí velkou část toho, co děláme.

* Pokud chcete navrhnout, jak můžeme vylepšit Visual Studio, můžete to udělat pomocí nástroje [Navrhnout](suggest-a-feature.md) funkci.

* Pokud dojde k problému, kdy aplikace Visual Studio přestane reagovat, dojde k selhání nebo k jinému problému s výkonem, můžete snadno sdílet reprodukci kroky a podpůrné soubory s námi pomocí nástroje [nahlásit problém](how-to-report-a-problem-with-visual-studio.md) .

## <a name="see-also"></a>Viz také

* [Novinky v dokumentaci k aplikaci Visual Studio](whats-new-visual-studio-docs.md)
* [Zpráva k vydání verze pro Visual Studio 2019](/visualstudio/releases/2019/release-notes/)
* [Zpráva k vydání verze pro Visual Studio 2019 for Mac](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [Co je nového v sadě Visual Studio 2019 SDK](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Novinky v jazyce C++ v sadě Visual Studio](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio/)
* [Co je nového v jazyce C# 9,0](/dotnet/csharp/whats-new/csharp-9)
* [Co je nového v .NET 5](/dotnet/core/dotnet-five)
* [Co je nového v .NET Framework](/dotnet/framework/whats-new/)
* [Konference Microsoftu o sestavení](https://www.microsoft.com/build)
* [Microsoft Ignite conference](https://www.microsoft.com/ignite)
