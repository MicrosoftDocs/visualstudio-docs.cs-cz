---
title: Co je nového v sadě Visual Studio. 2019 Preview
titleSuffix: ''
description: Další informace o nové funkce ve verzi preview sady Visual Studio 2019.
ms.date: 12/04/2018
ms.prod: visual-studio-dev16
ms.technology: vs-acquisition
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 06e3966703d95f897706eec8c46c2cd78fda859f
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159747"
---
# <a name="what39s-new-in-visual-studio-2019-preview"></a>Co&#39;s novinkou ve verzi Preview. 2019 Visual Studio

**Aktualizováno pro [16.0 1 verze Preview](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)**

Visual Studio 2019 Preview zahrnuje mnoho Obecná vylepšení spolu s novými funkcemi, které optimalizovat produktivitu a spolupráci mezi týmy. Ať už používáte Visual Studio poprvé nebo jste dosud používali ho let, budete moct využívat jeho funkce pro všechny aspekty životního cyklu vývoje&mdash;z zjednodušené vytváření a kód stavu řízení projektů, tým – a spolupráci pracovní postupy open source.

Tady je podrobný rekapitulace toho, co má Visual Studio nabízí:

* **[Osobní a zvýšení produktivity týmu](#personal-and-team-productivity)**. Produktivita pro všechny uživatele, kde jsou nejvíc.
* **[Podpora moderního vývoje](#modern-development-support)**. Podpora pro projekty aktuální a budoucí řešení.
* **[Průběžné inovace](#continuous-innovation)**. Kód inteligentní s podporou inteligentní, s využitím cloudu.

> [!NOTE]
> Úplný seznam nových funkcí a funkcí v sadě Visual Studio. 2019 Preview, najdete v článku [poznámky k verzi](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017).

## <a name="personal-and-team-productivity"></a>Osobní a produktivitu týmu

Je že jsou vylepšení výkonu nejvyšší prioritu v každé verzi sady Visual Studio, ale vpravo se tam s ní se zvyšuje vaši produktivitu. Zde je, jak můžeme pomoct s ním.

### <a name="new-start-window"></a>Nový časový interval pro spuštění

První věc, kterou zjistíte, když spustíte Visual Studio 2019 je její nové okno start.

   ![Nové okno start v aplikaci Visual Studio 2019](../ide/media/start-window.png)

Toto nové okno start vám nabídne možnosti, jak klonovat nebo podívejte se na kód, otevřete projekt nebo řešení, otevřít místní složku nebo vytvořte nový projekt. Tyto možnosti se zobrazí v dialogovém okně jednoduché pomůže obou začátečníky a získat kód rychle Pokročilí uživatelé sady Visual Studio.

### <a name="better-search"></a>Lepší vyhledávání

Dříve označované jako Snadné spuštění, naše nové rozhraní pro hledání je rychlejší a efektivnější. Nyní výsledky hledání zobrazeny dynamicky během psaní. A výsledky hledání obsahují klávesové zkratky pro příkazy, takže můžete snadno pamatovat pro budoucí použití.

   ![Nové funkce hledání v aplikaci Visual Studio 2019](../ide/media/search-feature.png)

Jestli chcete pro příkazy a nastavení nebo další užitečné věci, nová funkce vyhledávání je snazší najít, co hledáte.

### <a name="one-click-code-cleanup"></a>Vyčištění kódu jedním kliknutím

Spárovat s nový indikátor stavu dokumentu je nový příkaz vyčištění kódu. Tento nový příkaz slouží k identifikaci a potom opravit upozornění a návrhy kliknutím na tlačítko.

   ![Nové funkce vyčištění kódu v aplikaci Visual Studio 2019](../ide/media/code-cleanup.png)

Čištění formátovat kód, který se použije všechny opravy kódu jak navrhovaly [aktuální nastavení](../ide/code-styles-and-quick-actions.md), [soubory .editorconfig](../ide/create-portable-custom-editor-options.md), nebo [analyzátory Roslyn](../code-quality/roslyn-analyzers-overview.md).

### <a name="debugger-improvements"></a>Vylepšení ladicího programu

#### <a name="search-within-a-watch-window-and-format-watch-values"></a>Vyhledávání v rámci okna kukátka a formátování hodnot sledování

Pravděpodobně jste došlo před, hledání v okně kukátko pro řetězec ze sady hodnot. Ve Visual Studiu 2019 Preview jsme přidali vyhledávání v oknech sledovat, místní hodnoty a automatické hodnoty a umožňují najít objekty a hodnoty, které hledáte.

Můžete také formátovat, jak se zobrazí hodnota v oknech sledovat, místní hodnoty a automatické hodnoty.  Dvakrát klikněte na jednu z položek v některém z windows a přidejte čárku (",") pro přístup k seznamu rozevírací seznam specifikátorů formátu je to možné, z nichž každý obsahuje popis jeho zamýšlený efekt.

   ![Nové kukátko okno Formát hodnoty funkci a ve Visual Studio 2019](../ide/media/search-watch-window.png)

### <a name="visual-studio-live-share"></a>Visual Studio za sdílené složky

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) je služba pro vývojáře, která umožňuje sdílet základ kódu a jeho kontextu s programujete a získat rychlé obousměrné spolupráci přímo z Visual Studia. S Live Share programujete můžete přečíst, přejděte, upravit a ladit projekt, který jste sdíleli s nimi a učinit snadno a bezpečně.

A sadou Visual Studio 2019 Preview, tato služba nainstaluje ve výchozím nastavení.

## <a name="modern-development-support"></a>Podpora moderního vývoje

### <a name="manage-pull-requests-prs-from-the-ide"></a>Správa žádostí o přijetí změn (žádosti o přijetí změn) v prostředí IDE

Zavádíme nové rozšíření, které si můžete stáhnout pomocí Visual Studio 2019 Preview. Pomocí této nové rozšíření, můžete zkontrolovat, spustit a dokonce i ladění žádosti o přijetí změn od týmu, aniž byste museli opustit integrované vývojové prostředí sady Visual Studio [(integrované vývojové prostředí)](../get-started/visual-studio-ide.md). Jsme podporu kódu v úložišti Azure ještě dnes, ale rozšiřují podporu Githubu a zdokonalovat celkové prostředí.

Abyste mohli hned začít, stáhněte si [žádosti o přijetí změn pro sadu Visual Studio](https://aka.ms/pr4vs) rozšíření z Visual Studio Marketplace.

### <a name="develop-with-net-core-3-preview-1"></a>Vývoj s využitím .NET Core 3 Preview 1

Ve verzi preview verze sady Visual Studio 2019 podporuje vytváření [.NET Core 3](http://aka.ms/netcore3preview1) aplikací pro libovolnou platformu. Budeme nadále podporovat a zlepšit multiplatformní vývoj v jazyce C++ a .NET vývoj mobilních aplikací pro iOS a Android pomocí Xamarinu.

   ![Vývoj aplikací pomocí .NET Core 3 Preview 1 v Visual Studio 2019](../ide/media/dot-net-core-three-dev.png)

## <a name="continuous-innovation"></a>Průběžné inovace

### <a name="per-monitor-aware-pma-rendering"></a>Clustery vykreslování (PMA) na monitorování

Pokud používáte monitorování, které jsou nakonfigurovány s jiným zobrazením měřítko nebo vzdáleně připojit k počítači s použitím zobrazení škálování faktorů, které se liší od hlavní zařízení, můžete všimnout, že Visual Studio rozmazaný nebo vykreslí nesprávné měřítko.

S vydáním sady Visual Studio. 2019 ve verzi Preview 1 jsme se rozhodli první kroky k zabezpečení aplikace Visual Studio (PMA) aplikace pracující s za monitorování. Pokládáme základní práce, které vám umožní sadě Visual Studio správně vykreslit, bez ohledu na to, co zobrazí měřítko, které používáte.

   ![Clustery vykreslování (PMA) v aplikaci Visual Studio 2019 za monitorování](../ide/media/per-monitor-aware-dpi-scaling.png)

### <a name="visual-studio-intellicode"></a>Visual Studio IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) je rozšíření, která vylepšuje své úsilí vývoje softwaru pomocí umělé inteligence (AI). IntelliCode železniční napříč 2 000 open-source projektů na Githubu&mdash;každý s více než 100 hvězdiček&mdash;ke generování doporučení.

Tady je několik způsobů, jak Visual Studio IntelliCode může pomoct zvýšit produktivitu práce:

* Doručování dokončování s ohledem na kontext kódu
* Příručka pro vývojáře dodržovat vzory a styly jejich tým
* Najít problémy s kódu obtížné catch
* Revize kódu fokus kreslením upozornit na oblasti, které jsou opravdu důležité.

Zpočátku podporujeme pouze C# když jsme první předběžně IntelliCode rozšíření pro Visual Studio. Nyní přidali jsme podporu pro C++ a XAML v sadě Visual Studio, příliš.

A pokud používáte C#, přidali jsme také možnost pro trénování modelu vlastní na váš vlastní kód.

Další informace o rozšíření a kde ji můžete stáhnout, najdete v článku [Visual Studio IntelliCode - Preview](https://go.microsoft.com/fwlink/?linkid=872707) stránce Microsoft DevLabs.

## <a name="give-us-feedback"></a>Sdělte nám svůj názor

Proč odeslat zpětnou vazbu týmu sady Visual Studio? Protože jsme vážně trvat zpětné vazby od zákazníků. To vede velkou část co děláme.

* Pokud chcete provést návrh o tom, jak můžeme vylepšit sady Visual Studio, můžete to provést pomocí [poslat návrh](../ide/talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features) nástroj.

* Pokud dochází k zablokování, při selhání nebo jiné problémy s výkonem, můžete jednoduše sdílet kroky pro reprodukci a podpůrné soubory s námi pomocí [nahlásit problém](../ide/talk-to-us.md#i-want-to-report-a-problem-with-visual-studio) nástroj.

## <a name="see-also"></a>Viz také:

* [Zpráva k vydání verze Visual Studio 2019](/visualstudio/releases/2019/release-notes-preview?context=visualstudio/default&contextView=vs-2017)
* [Co je nového v sadě Visual Studio 2017](whats-new-in-visual-studio.md)
