---
title: Pokud chcete zvýšit produktivitu pro vývoj v .NET
description: Přehled analýzy kódu, navigace jednotky testování a další funkce, které vám usnadní vytváření kódu .NET lepší rychleji.
author: kuhlenh
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.date: 06/14/2018
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 5a2158663defe02dc51e91e888d47f325db7226a
ms.sourcegitcommit: 20d1b9a5bf041bb28453501eb63bc0537a8e4f54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2018
ms.locfileid: "51645143"
---
# <a name="visual-studio-2017-c-productivity-guide"></a>Průvodce produktivitou Visual Studio 2017 C#

Zjistěte, jak [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) zajišťuje vývojářům vyšší produktivitu, než kdy dřív. Využijte výhod našich vylepšení výkonu a produktivity jako je navigace na dekompilované sestavení, název proměnné návrhy při psaní, hierarchické zobrazení v **Průzkumník testů**, přejít na všechno (**Ctrl** + **T**) přejděte k souboru/typu/členu/symbolu deklarace, inteligentní **pomocníka výjimky**, styl konfigurace a vynucení a mnoho refaktoring kódu a opravy kódu.

## <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>Jsem zvyklý / zvyklá Moje klávesových zkratek z jiné rozšíření nebo editoru nebo prostředí IDE

**Novinka v sadě Visual Studio 2017 verze 15.8** Pokud přecházíte z jiného integrovaného vývojového prostředí nebo prostředí pro psaní kódu, můžete změnit na schéma klávesnice *Visual Studio Code* nebo *ReSharper (Visual Studio)*:

![Schémata klávesnice v sadě Visual Studio](../ide/media/VS2017Guide-Keyboard.png)

Některá rozšíření nabízí také schémata klávesnice:

- [Klávesové zkratky pro Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emulace (emacs)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Tady jsou oblíbené klávesové zkratky sady Visual Studio:

| Místní (všechny profily) | Příkaz | Popis |
|-|-|-|
| **Ctrl**+**T** | Přejít na vše | Přejděte do souboru/typu/členu/symbolu deklaraci |
| **F12** (také **Ctrl**+**klikněte na tlačítko**) | Přejít k definici | Přejděte na kterém je definován symbol |
| **Ctrl**+**F12** | Přejít k implementaci | Přejděte do jeho různé implementace ze základní typ nebo člena |
| **SHIFT**+**F12** | Najít všechny odkazy | Zobrazí všechny symbol nebo literál odkazy |
| **CTRL**+**.** (také **Alt**+**zadejte** v profil jazyka C#) | Rychlé akce a refaktoringy | Zobrazit, jaký kód opravy, jsou k dispozici na ukazatel pozice nebo kód výběr akce pro generování kódu, refaktoring nebo jiných rychlé akce |
| **Ctrl**+**D** | Duplicitní řádek | Duplikuje řádku kódu, který se kurzor nachází (k dispozici v **Visual Studio 2017 verze 15.6** a novější) |
| **SHIFT**+**Alt**+**+**/**-** | Rozbalit/Sbalit výběr | Rozbalíte nebo sbalíte aktuální výběr v editoru (k dispozici v **Visual Studio 2017 verze 15.5** a novější) |
| **SHIFT** + **Alt** + **.** | Vložit další odpovídající blikajícího kurzoru | Přidá výběr a blikající kurzor na dalším místě, která odpovídá aktuální výběr (k dispozici v **Visual Studio 2017 verze 15.8** a novější) |
| **Ctrl**+**Q** | Snadné spuštění | Hledat všechna nastavení sady Visual Studio |
| **F5** | Spustit ladění | Spuštění ladění aplikace |
| **Ctrl**+**F5** | Spustit bez ladění | Místní spuštění aplikace bez ladění |
| **CTRL**+**K**,**D** (výchozí profil) nebo **Ctrl**+**E**,**D**  (Profil jazyka C#) | [Formátovat dokument](code-styles-and-quick-actions.md#format-document-command) | Vyčistí formátování narušení v souboru na základě nového řádku, mezery a nastavení odsazení |
| **CTRL**+**\\**,**Ctrl**+**E** (výchozí profil) nebo **Ctrl** + **W**,**E** (profil jazyka C#) | Zobrazení seznamu chyb | Zobrazit všechny chyby v dokumentu, projekt nebo řešení |
| **ALT** + **Page Up nebo PAGE DOWN** | Přejít na další/předchozí problém | Přejít na předchozí nebo další chyba, upozornění, návrh v dokumentu (k dispozici v **Visual Studio 2017 verze 15.8** a novější) |

> [!NOTE]
> Některá rozšíření odpojit klávesové zkratky sady Visual Studio výchozí. Použití výše uvedené příkazy, obnovit vaše klávesové zkratky nastavení sady Visual Studio tak, že přejdete do **nástroje** > **nastavení importu a exportu** > **obnovit všechna nastavení**  nebo **nástroje** > **možnosti** > **klávesnice** > **resetování**.

Další informace klávesové zkratky a příkazy v sadě Visual Studio [naši dokumentaci](../ide/tips-and-tricks-for-visual-studio.md).

## <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>Budu potřebovat způsob, jak rychle přejít na soubory nebo typy

Visual Studio 2017 obsahuje funkci s názvem **přejít na vše** (**Ctrl**+**T**). **Přejít na vše** umožňuje rychle přejít na soubor, typ, člen nebo deklaraci symbolu.

- Změnit umístění tohoto panelu hledání nebo vypnutí náhled živého navigace **ozubené kolečko** ikonu.
- Filtrování výsledků pomocí našich syntaxe dotazu (například "mytype t"). Můžete také omezit rozsah hledání pouze na aktuální dokument.
- odpovídající camelCase je podporován!

![Přejít na vše v sadě Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>Můj tým vynucuje pravidel stylu kódu na náš základ kódu

Můžete použít *.editorconfig* souboru kodifikovat konvence kódování a mít je přenášet společně s vaším zdrojem.

- Můžete nainstalovat [služba jazyka EditorConfig rozšíření](https://aka.ms/editorconfig), což usnadňuje přidávání a úprava *.editorconfig* souboru v sadě Visual Studio.
- Vyzkoušejte si [IntelliCode rozšíření pro Visual Studio](/visualstudio/intellicode/intellicode-visual-studio). Tento experimentální rozšíření odvodí z něj styl kódu z existujícího kódu a pak vytvoří neprázdný *.editorconfig* soubor s předvolby stylu kódu již definována.
- Podívejte se [možnosti konvence psaní kódu .NET](https://aka.ms/editorconfigDocs) dokumentaci.
- Zobrazit [tento gist](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) příklad *.editorconfig* souboru.

![Vynucení stylu kódu v sadě Visual Studio](../ide/media/VSGuide_CodeStyle.png)

## <a name="i-need-more-refactorings-and-code-fixes"></a>Potřebuji další opravy refaktoringů a kódu

Visual Studio 2017 se dodává s velké množství refaktoringů, akcí generování kódu a opravy kódu. Chyby představují červenou vlnovkou, zelenou vlnovkou představují upozornění a tři šedé tečky představují návrhy kódu. Přístupový kód opravy můžete kliknutím na ikonu žárovky/šroubovák nebo stisknutím klávesy **Ctrl**+**.** nebo **Alt**+**zadejte**. Jednotlivé opravy se dodává s oknem Náhled, který ukazuje rozdíl živého kódu fungování opravy.

- Oblíbené rychlých oprav a refaktoringy patří:
  - *Přejmenovat*
  - *Extrahování metody*
  - *Podpis změny metod*
  - *Generování konstruktoru*
  - *Generování metody*
  - *Přesun typu do souboru*
  - *Přidat kontrolu hodnoty Null*
  - *Přidat parametr*
  - *Odebrat nepotřebné direktivy using*
  - Zobrazit více v našich [dokumentace](https://aka.ms/refactorings)
- Napsat vlastní kód nebo refaktoring opravy s [analyzátory Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix).
- Několik členů komunity napsali bezplatné rozšíření, které přidávají další kód kontroly:
  - [FXCop Analyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/)
  - [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
  - [SonarLint for Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
  - [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)

![Refaktoring v sadě Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>Potřebuji najít použití, přejít k implementaci, přejděte na Dekompilované sestavení

Visual Studio 2017 obsahuje mnoho funkcí pro usnadnění hledání a navigaci vašeho základu kódu. Přečtěte si více o funkcích [Navigace kódu](../ide/navigating-code.md)

| Funkce | Zástupce | Podrobnosti a vylepšení |
|- | - | -|
| Najít všechny odkazy | **SHIFT**+**F12**| Výsledky jsou zabarvené a lze seskupovat podle projektu, definice, atd. Je také možné "zamknout" výsledky. |
| Přejít k implementaci | **Ctrl**+**F12** | Chcete-li přejít na přepsaného člena, můžete použít klíčové slovo `override` k přechodu na klíč |
| Přejít k definici | **F12** nebo **Ctrl**+**Klikni**| Může obsahovat **Ctrl** při kliknutí na navgiate k definici |
| Náhled definice | **Alt**+**F12** | Zobrazit vložené definice |
| Vizualizér struktur | Šedé, tečkami čáry mezi složené závorky | Najetím myši zobrazíte struktury kódu |
| Navigace do dekompilovaných sestav | **F12** nebo **Ctrl**+**Klikni** | Přejděte do externího zdroje (decompiled s ILSpy) tím, že tuto funkci: **nástroje** > **možnosti** > **textový Editor**  >  **Jazyka C#** > **Upřesnit** > **povolit navigaci na dekompilované zdroje**. |

![Přejít na vše a najít všechny odkazy](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="i-want-to-run-and-see-my-unit-tests"></a>Chci spustit a Zobrazit Moje testy jednotek

V sadě Visual Studio 2017 jsme provedli spoustu vylepšení testování. Použijte některou z našich testování prostředí pomocí MSTest v1, MSTest v2, NUnit nebo XUnit rozhraních pro testování.

- **Průzkumník testů** zjišťování testů je rychle ve verzi 15.6 (pro dosažení nejlepších výsledků, upgradujte na nejnovější verzi testovací adaptér).
- Uspořádání testů v aplikaci Průzkumník testů díky nové *řazení hierarchických* ve verzi 15.6.
- [Živé testování částí](../test/live-unit-testing.md) nepřetržitě spouští testy vliv změny kódu a aktualizuje vložené editor ikon s oznámením stav testů. Zahrnout nebo vyloučit určité testy nebo testování projektů z vaší *Live Test nastavit*.

![Hierarchické zobrazení pro Text Explorer v sadě Visual Studio](../ide/media/VSGuide_Testing.png)

## <a name="i-want-to-debug-my-code"></a>Budu chtít ladit můj kód

V sadě Visual Studio 2017 jsme přidali spoustu nových funkcí ladění:

- *Běžet do kliknutí* umožňuje při najetí myší vedle řádku kódu, stiskněte zelená ikona "play", který se zobrazí, a spusťte svůj program, dokud nedosáhne tento řádek.
- Nové **pomocníka výjimky** vloží nejdůležitější informace, jako jsou proměnné, která je null v NullReferenceException, na nejvyšší úrovni v dialogovém okně.
- [Zastav](../debugger/how-to-use-intellitrace-step-back.md) ladění můžete přejít zpět k předchozím zarážkám nebo krokům a zobrazit stav aplikace, jako v minulosti.
- [Ladění snímků](/azure/application-insights/app-insights-snapshot-debugger) umožňuje pátrejte po stavu živé webové aplikace v tuto chvíli došlo k výjimce (musí být v Azure).

![Nového pomocníka výjimky v sadě Visual Studio 2017](../ide/media/VSGuide_Debugging.png)

## <a name="i-want-to-use-version-control-with-my-projects"></a>Chci používat správu verzí s projekty

Úložiště git nebo TFVC můžete použít k ukládání a aktualizujte svůj kód v sadě Visual Studio.

- Uspořádání místní změny s **Team Exploreru** a sledovat probíhající potvrzení a změny pomocí stavového řádku.
- Nastavte průběžnou integraci a doručování pro projekty v aplikaci Visual Studio s naší [nástrojů Continuous delivery tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) rozšíření a přijmout pracovní postup agile pro vývojáře.

![Správa zdrojového kódu v sadě Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-do-i-need-to-know-about"></a>Jaké další funkce je třeba vědět o?

Tady je seznam editoru a produktivitu funkcí pro zajištění efektivnějšího psaní kódu. Některé funkce možná muset povolit, protože jsou vypnutí výchozím (může indexování věci na svém počítači, jsou kontroverzním nebo jsou aktuálně experimentální).

| Funkce | Podrobnosti | Jak povolit |
|-|-|-|
| Vyhledejte soubor v Průzkumníku řešení | Zvýrazní aktivní soubor v **Průzkumníka řešení** | **Nástroje** > **možnosti** > **projekty a řešení** > **sledovat aktivní položku v Průzkumníku řešení** |
| Přidání direktivy using pro typy v referenční sestavení a balíčky NuGet | Zobrazí žárovka s opravu kódu se nainstalovat balíček NuGet pro neodkazovaný typ. | **Nástroje** > **možnosti** > **textový Editor** > **jazyka C#** > **Advanced**   >  **Navrhnout použití typů v sestaveních reference** a **navrhnout použití typů v balíčcích NuGet** |
| Povolení úplné analýzy řešení | Zobrazit všechny chyby ve vašem řešení v **seznam chyb** | **Nástroje** > **možnosti** > **textový Editor** > **jazyka C#** > **Advanced**   >  **Povolení úplné analýzy řešení** |
| Povolit navigaci na dekompilované zdroje | Povolit přejít k definici pro typy nebo členy z externích zdrojů a ILSpy decompiler znázornit těl metod. | **Nástroje** > **možnosti** > **textový Editor** > **jazyka C#** > **Advanced**   >  **Povolit navigaci na dekompilované zdroje** |
| Režim dokončování a návrhu | Změny chování při dokončování IntelliSense--vývojářům IntelliJ pozadí mají tendenci se měnit nastavení zde z výchozího | **Nabídka** > **upravit** > **IntelliSense** > **přepnout režim dokončení** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Zobrazí odkaz na informace o kódu a změnit historii v editoru | **Nástroje** > **možnosti** > **textový Editor** > **všechny jazyky**  >   **Funkce CodeLens** |
| [Fragmenty kódu](../ide/visual-csharp-code-snippets.md) | Nápověda zástupných procedur na běžné často používaný text | Zadejte název fragmentu kódu a stiskněte klávesu **kartu** dvakrát. |

## <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>Chybějící funkce, která vám umožňuje být produktivní nebo právě probíhá nízký výkon?

Existuje několik způsobů, jak odeslat nám názor:

- Žádosti o funkce .NET může zaznamenaná v našich [úložiště GitHub se vzorovými](https://github.com/dotnet/roslyn/issues).
- Visual Studio žádosti o funkce, chyby a problémy s výkonem můžete podává pomocí **odeslat zpětnou vazbu** ikonu v pravém horním rohu okna sady Visual Studio.
