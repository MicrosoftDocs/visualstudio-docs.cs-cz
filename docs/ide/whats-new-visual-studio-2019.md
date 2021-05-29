---
title: Novinky v sadě Visual Studio 2019
titleSuffix: ''
description: Seznamte se s novými funkcemi v Visual Studio 2019.
ms.date: 05/28/2021
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
ms.openlocfilehash: 8664606877f5393a98a78e32c6d396e1a5bcf4c1
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687696"
---
# <a name="whats-new-in-visual-studio-2019"></a>Novinky v sadě Visual Studio 2019

**Aktualizace pro [verzi 16.10](/visualstudio/releases/2019/release-notes/)**

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

   ![Animace nového vyhledávacího prostředí v Visual Studio 2019](media/vs-2019/new-search-feature.gif "Nové možnosti vyhledávání v aplikaci Visual Studio 2019.")

Nová logika vyhledávání přibližných shod najde vše, co potřebujete, bez ohledu na překlepy. Takže bez ohledu na to, jestli hledáte příkazy, nastavení, dokumentaci nebo jiné užitečné věci, vám nová funkce vyhledávání usnadní hledání hledané funkce.

Další informace najdete v tématu [Použití Visual Studio vyhledávání.](visual-studio-search.md)

#### <a name="intelligent-search-service"></a>Inteligentní vyhledávací služba

**Novinka v 16,9**: pomocí technologie založené na cloudu, umělé Intelligence a strojového učení jsme vylepšili výsledky hledání. V aplikaci Visual Studio teď není k dismnožější výsledky, ale je možné, že vám také umožní snadněji zjistit funkce produktu.

Další informace najdete v příspěvku na blogu [inteligentní vyhledávací služba sady Visual Studio](https://devblogs.microsoft.com/visualstudio/intelligent-visual-studio-search-service/) .

### <a name="refactorings"></a>Refaktoring

V jazyce C# existuje spousta nových a velmi užitečných refaktoringů, které usnadňují uspořádání kódu. Zobrazují se jako návrhy v žárovkě a zahrnují akce jako přesunutí členů do rozhraní nebo základní třídy, úpravy oborů názvů tak, aby odpovídaly struktuře složek, převedení smyček foreach na dotazy LINQ a další.

   ![Animace prostředí refaktoringu v aplikaci Visual Studio 2019](media/vs-2019/refactorings.gif "Prostředí refaktoringu v aplikaci Visual Studio 2019.")

Jednoduše volejte refaktoring stisknutím **kombinace kláves CTRL +.** a vyberte akci, kterou chcete provést.

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) vylepšuje úsilí při vývoji softwaru pomocí umělé Intelligence (AI). IntelliCode vlaky napříč 2 000 open source projektů na GitHubu &mdash; každý s více než 100 hvězdičkami &mdash; , aby vygenerovala doporučení.

![Animace IntelliCode ve Visual Studiu 2019](media/vs-2019/IntelliCode.gif "IntelliCode v aplikaci Visual Studio 2019.")

Tady je několik způsobů, jak může Visual Studio IntelliCode přispět k lepší produktivitě:

* Doručovat dokončování kódu s ohledem na kontext
* Příručka pro vývojáře, aby dodržovala vzory a styly jejich týmu
* Hledání problémů s kódem, který se špatně zachytí
* Zaměřte se na revize kódu tím, že vykreslíte pozornost oblastí, které skutečně jsou

Po prvním zobrazení IntelliCode jako rozšíření pro Visual Studio jsme původně podporovali jenom C#. **Novinka v 16,1** jsme přidali podporu pro C# a XAML "in-the-box". (Podpora pro C++ a TypeScript/JavaScript je však stále ve verzi Preview.)

A pokud používáte jazyk C#, Přidali jsme také možnost naučit se vlastní model ve vlastním kódu.

Další informace o IntelliCode najdete v blogových příspěvku Oznamování obecné dostupnosti [IntelliCode a](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) náhledu kódu a Dalších kódů. Pomocí blogových příspěvků [Visual Studio IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) se posuňte méně.

### <a name="code-cleanup"></a>Vyčištění kódu

Spárované s novým indikátorem stavu dokumentu je nový příkaz pro vyčištění kódu. Tento nový příkaz můžete použít k identifikaci a opravě upozornění i návrhů jedinou akcí (nebo kliknutím na tlačítko).

Vyčištěním se kód naformátuje a použijí se všechny opravy kódu podle aktuálního nastavení [a](code-styles-and-code-cleanup.md) [souborů .editorconfig](create-portable-custom-editor-options.md).

   ![Snímek obrazovky nového ovládacího prvku vyčištění kódu v Visual Studio 2019](media/vs-2019/code-cleanup-profile.png "Nový ovládací prvek pro vyčištění kódu v aplikaci Visual Studio 2019.")

Kolekce fixerů můžete také uložit jako profil. Pokud máte například malou sadu cílených fixerů, které často používáte při práci s kódem, a pak máte další komplexní sadu oprav, které se mají použít před revizemi kódu, můžete nakonfigurovat profily pro řešení těchto různých úloh.

   ![Snímek obrazovky s konfigurací ovládacího prvku pro vyčištění kódu Visual Studio 2019](media/vs-2019/code-cleanup-profile-configure.png "Konfigurace ovládacího prvku pro vyčištění kódu v aplikaci Visual Studio 2019.")

### <a name="per-monitor-aware-pma-rendering"></a>Vykreslování pma (per-monitor aware)

Pokud používáte monitory nakonfigurované s různými faktory škálování zobrazení nebo se vzdáleně připojíte k počítači s faktory měřítka zobrazení, které se liší od hlavního zařízení, můžete si všimnout, že Visual Studio vypadá rozmazaně nebo se vykresluje ve špatném měřítku.

S vydáním Visual Studio 2019 jsme aplikaci pma Visual Studio pro monitorování. Nyní se Visual Studio správně bez ohledu na faktory měřítka zobrazení, které používáte.

   ![Vykreslování pma (per-monitor aware) v Visual Studio 2019](media/vs-2019/pma-dpi-scaling.png "Vykreslování PMA (per-monitor) v aplikaci Visual Studio 2019.")

Další informace najdete v blogovém příspěvku [Better multi-monitor experience with Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) .

### <a name="test-explorer"></a>Průzkumník testů

Novinka ve verzi **16.2:** Aktualizovali jsme Průzkumníka testů tak, aby poskytoval lepší zpracování velkých testovacích sad, snadnější filtrování, zjistitelnější příkazy, zobrazení seznamu stop s kartami a přizpůsobitelné sloupce, které umožňují doladit zobrazené informace o testování.

   ![Snímek obrazovky znázorňuje vylepšení uživatelského rozhraní v Průzkumníku testů](media/vs-2019/test-explorer-ui.png "Vylepšení uživatelského rozhraní v Průzkumníku testů.")

### <a name="net-core"></a>.NET Core

**Novinka v 16,3**: zahrnuli jsme podporu pro .net Core 3,0. Pro různé platformy, open source &mdash; a plně podporované Microsoftem.

Další informace najdete v příspěvku na blogu o [.NET Core 3,0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/) .

## <a name="collaborate"></a>Spolupráce

Podívejte se na následující video, kde se dozvíte víc o tom, jak se dá tým seskupit a vyřešit problémy. <br><br>*Délka videa: 4,22 minut*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Pracovní postup Git – první

Něco, co si všimnete při otevření sady Visual Studio 2019, je nové úvodní okno.

   ![Snímek obrazovky s novým oknem Start v aplikaci Visual Studio 2019](media/vs-2019/start-window-dark.png "Nové okno Start v aplikaci Visual Studio 2019.")

Okno Start nabízí několik možností, jak rychle získat kód. Umístili jsme možnost klonovat nebo rezervovat kód z úložiště, nejdřív.

   ![Animace prostředí Git-First v aplikaci Visual Studio 2019](media/vs-2019/git-first.gif "Prostředí Git-First v aplikaci Visual Studio 2019.")

Okno Start také obsahuje možnosti pro otevření projektu nebo řešení, otevření místní složky nebo vytvoření nového projektu.

Další informace najdete v tématu [získání kódu: jak jsme navrhli nový Blogový příspěvek pro úvodní okno sady Visual Studio](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) .

### <a name="git-productivity"></a>Produktivita Git

**Novinka ve verzi 16,8**: Git je teď výchozím prostředím pro řízení verzí v aplikaci Visual Studio 2019. Sestavili jsme sadu funkcí a na ni jste na základě vašich názorů za poslední dvě verze zavedli iteraci. Nové prostředí je teď ve výchozím nastavení zapnuté pro všechny. Z nové nabídky Git můžete klonovat, vytvářet nebo otevírat úložiště. Pomocí integrovaných oken nástroje Git můžete zapsat a doručovat změny kódu, spravovat větve, udržovat aktuální úložiště pomocí vzdálených úložišť a vyřešit konflikty sloučení.

Další informace najdete na stránce věnované [prostředí Git](../version-control/git-with-visual-studio.md) na stránce sady Visual Studio.

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) je vývojářská služba, která umožňuje sdílet základní kód a jeho kontext s kolegou týmu a získat okamžitou obousměrnou spolupráci přímo z Visual Studio. Díky Live Share může kolega z týmu číst, procházet, upravovat a ladit projekt, který s ním sdílíte, a bez problémů a bezpečně.

A s Visual Studio 2019 se tato služba nainstaluje ve výchozím nastavení.

![Animace, která znázorňuje funkci Live Share spolupráce v Visual Studio 2019](media/vs-2019/live-share.gif "Funkce spolupráce Live Share v aplikaci Visual Studio 2019.")

Další informace najdete v blogovém [příspěvku o](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) Visual Studio Live Share pro recenze kódu v reálném čase a interaktivním příspěvku o vzdělávání a v blogovém příspěvku Live Share, který je Visual Studio [2019.](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/)

### <a name="integrated-code-reviews"></a>Integrované recenze kódu

Představujeme nové rozšíření, které si můžete stáhnout pro použití s Visual Studio 2019. S tímto novým rozšířením můžete zkontrolovat, spustit a dokonce i ladit žádosti o přístup od týmu, aniž byste Visual Studio. Podporujeme kód jak v GitHubu, tak Azure DevOps úložištích.

   ![Snímek obrazovky s novým rozšířením Pull Requests v Visual Studio 2019](media/vs-2019/pr-experience.png "Nové rozšíření žádosti o přijetí změn v aplikaci Visual Studio 2019.")

Další informace najdete v blogovém příspěvku [o rozšíření Code reviews using the Visual Studio Pull Requests.](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/)

## <a name="debug"></a>Ladění

Podívejte se na následující video, kde najdete další informace o tom, jak se při ladění můžete zaměřit na nulu s přesným cílením. <br><br>*Délka videa: 3,54 minuty*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>Zvýšení výkonu

Vzali jsme jednou exkluzivní datové zarážky C++ a přizpůsobili je pro aplikace .NET Core.

   ![Animace znázorňující zarážky dat ladění v Visual Studio 2019](media/vs-2019/debug-data-breakpoints.gif "Ladicí datové zarážky v Visual Studio 2019.")

Takže bez ohledu na to, jestli kód pracujete v jazyce C++ nebo .NET Core, mohou být datové zarážky dobrou alternativou k umísťování běžných zarážek. Datové zarážky jsou také skvělé pro scénáře, jako je hledání místa, kde se globální objekt upravuje nebo přidává nebo odebral ze seznamu.

A pokud jste vývojář v jazyce C++, který vyvíjí velké aplikace, vytvořil Visual Studio 2019 symboly z proc, což vám umožní ladit tyto aplikace bez problémů souvisejících s pamětí.

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

Další informace najdete v blogovém příspěvku [Pinnable Properties: Debug & Display Managed Objects YOUR Way (Připnoutelné vlastnosti:](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/) Ladění spravovaných objektů ve vašem způsobu).

## <a name="whats-next"></a>Kam dál

Často aktualizujeme Visual Studio 2019 o nové funkce, které vám posouží ještě lepší vývojové prostředí. Další informace o našich nejnovějších inovacích najdete na Visual Studio [Blog.](https://devblogs.microsoft.com/visualstudio/) Záznam toho, co jsme dote doby vydali ve verzi Preview, si můžete prohlédnout ve zprávě k [vydání verze Preview.](/visualstudio/releases/2019/release-notes-preview/) A seznam toho, co plánujeme vydat jako další, najdete na [Visual Studio plán.](/visualstudio/productinfo/vs-roadmap)

Mezitím je tu nová funkce, která je aktuálně v práci.

- **Vylepšené prostředí Gitu v Visual Studio 2019 (Preview)**

   I když je nové prostředí pro řízení verzí Git ve výchozím nastavení ve verzi [16.8](/visualstudio/releases/2019/release-notes/)Visual Studio 2019, nadále přidávají funkce, které vylepšují prostředí v nejnovější verzi Preview.

   Další informace najdete v tématu [o řízení verzí na Visual Studio.](/visualstudio/version-control/)

Další informace o verzi Preview verze Visual Studio 2019 a odkaz ke stažení, pokud si ho chcete vyzkoušet, najdete na &mdash; &mdash; **[Visual Studio Preview](https://aka.ms/vspreview/)** stránky.

> [!TIP]
> Další informace o naší další verzi najdete v **[blogovém příspěvku Visual Studio 2022.](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/)**

## <a name="give-us-feedback"></a>Sdělte nám svůj názor

Proč posílat zpětnou vazbu Visual Studio týmu? Protože zpětnou vazbu zákazníků bereme vážně. Řídí velkou část toho, co děláme.

* Pokud si chcete udělat nějaký návrh, jak můžeme vylepšit aplikaci Visual Studio, můžete k tomu použít nástroj [navrhnout funkci](suggest-a-feature.md) .

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
