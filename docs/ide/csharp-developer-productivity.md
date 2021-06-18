---
title: Zvýšení produktivity při vývoji v .NET
description: Přehled navigace, analýzy kódu, testování částí a dalších funkcí, které vám pomůžou rychleji psát lepší kód .NET.
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 6de31ed1b649f226ac47161fdadfe44d434289b9
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308516"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>Visual Studio produktivity pro vývojáře v jazyce C#

Zjistěte, Visual Studio vývojáři produktivnější než kdy dřív. Využijte naše vylepšení výkonu a produktivity, jako je navigace na dekompilovaná sestavení, návrhy názvů proměnných při psaní, hierarchické zobrazení v Průzkumníku **testů,** Přejít na vše (**Ctrl** T ) a přejít na deklarace + souboru/typu/člena/symbolu, inteligentního pomocníka pro výjimky, konfiguraci stylu kódu a vynucení a mnoho refaktoringů a oprav kódu. 

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>Používám klávesové zkratky z jiného editoru

::: moniker range="vs-2017"

**Novinka v Visual Studio 2017 verze 15.8**

::: moniker-end

Pokud pocházíte z jiného integrovaného vývojového prostředí (IDE) nebo prostředí pro kódování, můžete změnit schéma klávesnice *na Visual Studio Code* nebo *ReSharper (Visual Studio):*

![Schémata klávesnice v Visual Studio](../ide/media/VS2017Guide-Keyboard.png)

Některá rozšíření také nabízejí schémata klávesnice:

- [Klávesové zkratky pro Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emulace Emacs](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Oblíbené jsou následující Visual Studio zkratky:

| Zástupce (všechny profily) | Příkaz | Popis |
|-|-|-|
| **Ctrl** + **T** | Přejít na vše | Přejděte k libovolné deklaraci souboru, typu, člena nebo symbolu. |
| **F12** (také **Ctrl** + **Click**) | Přejít k definici | Přechod na místo, kde je definován symbol |
| **Ctrl** + **F12** | Přejít k implementaci | Přechod ze základního typu nebo členu na jeho různé implementace |
| **Shift (Posun)** + **F12** | Najít všechny odkazy | Zobrazení všech symbolů nebo literálových odkazů |
| **Alt** + **Domovská stránka** | Přejít na základní typ | Procházení řetězu dědičnosti nahoru |
| **Ctrl** + **.** (také **Alt** + **Zadejte** do profilu C#. | Rychlé akce a refaktoringy | Podívejte se, jaké opravy kódu, akce generování kódu, refaktoring nebo jiné rychlé akce jsou k dispozici na pozici kurzoru nebo na výběru kódu. |
| **Ctrl** + **D** | Duplicitní řádek | Duplikuje řádek kódu, ve které je kurzor (k dispozici **v Visual Studio 2017 verze 15.6** a novější). |
| **Shift (Posun)** + **Alt**+**+**/**-** | Výběr možnosti Rozbalit/Kontrakt | Rozbalí nebo z kontraktů aktuální výběr v editoru (k dispozici **v Visual Studio 2017 verze 15.5** a novější). |
| **Shift (Posun)**  +  **Alt**  +  **.** | Vložení další odpovídající tečky | Přidá do dalšího umístění výběr a caret, který odpovídá aktuálnímu výběru (k dispozici ve **verzi Visual Studio 2017 verze 15.8** a novější). |
| **Ctrl** + **Otázka** | Hledat | Prohledat všechna Visual Studio nastavení |
| **F5** | Spuštění ladění | Spuštění ladění aplikace |
| **Ctrl** + **F5** | Spuštění bez ladění | Místní spuštění aplikace bez ladění |
| **Ctrl** + **K**,**D** (výchozí profil) nebo **Ctrl** + **E**,**D** (profil C#) | Formátovat dokument | Vyčistí porušení formátování v souboru na základě nového řádku, mezer a nastavení odsazení. |
| **Ctrl** + **\\** ,**Ctrl** + **E** (výchozí profil) nebo **Ctrl** + **W**,**E** (profil C#) | Zobrazit Seznam chyb | Zobrazení všech chyb v dokumentu, projektu nebo řešení |
| **Alt**  +  **PgUp/PgDn** | Přejít k dalšímu nebo předchozímu problému | Přejít na předchozí nebo další chybu, upozornění, návrh v dokumentu (k dispozici v **Visual Studio 2017 verze 15.8** a novější) |
| **Ctrl** + **K**,**/** | Přepnutí jednoho řádkového komentáře nebo zrušení komentáře | Tento příkaz přidá nebo odebere jeden řádek komentáře v závislosti na tom, jestli už je váš výběr okomentovaný. |
| **Ctrl** + **Shift (Posun)**+**/** | Přepnutí blokového komentáře nebo zrušení komentáře | Tento příkaz přidá nebo odebere blokové komentáře podle toho, co jste vybrali. |

> [!NOTE]
> Některá rozšíření zrušit vazbu výchozích Visual Studio klávesovou zkratkou. Pokud chcete použít výše uvedené příkazy, obnovte klávesové zkratky Visual Studio výchozí nastavení nástroje tak, že přejdeme na Nástroje Import a export nastavení Resetování všech nastavení  >    >   nebo **Nástroje**  >  **Možnosti**  >    >  **Resetování klávesnice.**

Další informace o klávesových zkratkách a příkazech najdete v tématu [Klávesové zkratky pro produktivitu](../ide/productivity-shortcuts.md) a [Oblíbené klávesové zkratky.](default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)

## <a name="navigate-quickly-to-files-or-types"></a>Rychlé procházení k souborům nebo typům

Visual Studio má funkci s názvem **Přejít na vše** (**Ctrl** + **T**). **Funkce Přejít na** vše umožňuje rychle přejít na libovolný soubor, typ, člen nebo deklaraci symbolu.

- Změňte umístění tohoto panelu hledání nebo vypněte náhled živé navigace pomocí ikony **ozubeného** kola.
- Filtrování výsledků pomocí syntaxe, jako je `t mytype` .
- Vymezit obor hledání pouze na aktuální dokument.
- Podporuje se porovnávání camel case.

![Přejít na vše v Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules"></a>Vynucení pravidel stylu kódu

Soubor EditorConfig můžete použít ke kodifikování konvencí kódování a k jejich přenosu se zdrojem.

![Vynucení stylu kódu v Visual Studio](../ide/media/VSGuide_CodeStyle.png)

- Přidejte výchozí nebo . Soubor EditorConfig ve stylu NET pro váš projekt výběrem **možnosti Přidat**  >  **novou položku.** V **dialogovém okně Přidat novou** položku vyhledejte editorconfig. Vyberte některou z **editorconfig Šablony položek** souborů a pak zvolte **Přidat.**

   ![Šablony položek EditorConfig v Visual Studio](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- Automaticky vytvořte soubor *.editorconfig* na základě nastavení stylu kódu v **části** Nástroje > **Možnosti** > **Textový editor** > **Styl kódu** > **C#.**

   ![Generování souboru .editorconfig z nastavení ve VS 2019](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- Funkce [odvozování kódu](/visualstudio/intellicode/code-style-inference) IntelliCode pro Visual Studio odvodí styly kódu z existujícího kódu. Pak vytvoří neprázdný soubor EditorConfig s již definovanými předvolbou stylu kódu.

- Nakonfigurujte úroveň závažnosti pravidla stylu kódu přímo prostřednictvím editoru. Pokud momentálně nemáte soubor .editorconfig, vygeneruje se vám. Umístěte kurzor na chybu, upozornění nebo návrh a zadejte **Ctrl** + **.** otevřete nabídku Rychlé akce a refaktoring. Vyberte **Konfigurovat nebo potlačit problémy.** Potom vyberte pravidlo a zvolte úroveň závažnosti, kterou chcete pro toto pravidlo nakonfigurovat. Tím se aktualizuje stávající EditorConfig novou závažností pravidla.

   ![Konfigurace úrovně závažnosti pravidla stylu kódu přímo v editoru](../ide/media/configure-severity-level.png)

Podívejte se na [dokumentaci k možnostem konvence kódování .NET,](/dotnet/fundamentals/code-analysis/code-style-rule-options) která obsahuje také příklad kompletního souboru EditorConfig.

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>Vyčištění kódu

Visual Studio poskytuje formátování souboru kódu na vyžádání, včetně předvoleb stylu kódu, prostřednictvím funkce **Vyčištění** kódu. Vyčištění kódu spustíte tak, že kliknete na ikonu koštěte v dolní části editoru nebo **stisknete Ctrl** + **K**, **Ctrl** + **E**.

![Tlačítko Vyčištění kódu v Visual Studio 2019](media/execute-code-cleanup.png)

Můžete také spustit vyčištění kódu napříč celým projektem nebo řešením. Klikněte pravým tlačítkem na název projektu nebo řešení **v Průzkumník řešení,** vyberte Analyzovat a **Vyčištění** kódu a pak vyberte Spustit **vyčištění kódu.**

![Spuštění vyčištění kódu napříč celým projektem nebo řešením](media/run-code-cleanup-project-solution.png)

Kromě formátování souboru pro mezery, odsazení a další  funkce čištění kódu platí také vybrané styly kódu. Předvolby pro jednotlivé styly kódu se načtou ze souboru [EditorConfig,](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files)pokud ho máte pro projekt, nebo z nastavení stylu kódu v **dialogovém okně** Možnosti. [](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box)

::: moniker-end

## <a name="refactorings-and-code-fixes"></a>Refaktoring a opravy kódu

Visual Studio se dodává s mnoha refaktoringy, akcemi generování kódu a opravami kódu. Červenéquiggles představují chyby, zelené squiggles představují upozornění a tři šedé tečky představují návrhy kódu. K opravě kódu se můžete přistupovat kliknutím na ikonu žárovky nebodriveru nebo stisknutím **klávesy Ctrl** + **.** nebo **Alt** + **Zadejte**. Každá oprava se dodává s oknem náhledu, ve které je vidět rozdíl živého kódu, jak tato oprava funguje.

Mezi oblíbené rychlé opravy a refaktoring patří:

- přejmenování
- extrahování metody
- Změna podpisu metody
- Generování konstruktoru
- Generate – metoda
- Přesunutí typu do souboru
- Přidání Null-Check
- Přidat parametr
- Odebrání nepotřebných použití
- Smyčka Foreach pro dotaz LINQ nebo metodu LINQ
- Pull Members Up

Další informace najdete v tématu [funkce generování kódu.](code-generation-in-visual-studio.md)

Pokud chcete [označit problémy s kódem, můžete](../code-quality/install-fxcop-analyzers.md) nainstalovat analyzátory FxCop. Nebo pomocí analyzátorů Roslyn napište vlastní refaktoring [nebo opravu kódu.](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix.md)

Několik členů komunity napsalo bezplatná rozšíření, která přidávají další kontroly kódu:

::: moniker range="vs-2017"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [SonarLint pro Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeSoučáteč](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

::: moniker range=">=vs-2019"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2019)
- [SonarLint pro Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2019)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeSoučáteč](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

![Refaktoring v Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Vyhledání využití, přechod na implementaci a přechod na dekompilovaná sestavení

Visual Studio mnoho funkcí, které vám pomůžou prohledávat [a procházet kód](../ide/navigating-code.md).

| Funkce | Zástupce | Podrobnosti a vylepšení |
|- | - | -|
| Najít všechny odkazy | **Shift (Posun)** + **F12**| Výsledky jsou barevně zabarizovány a lze je seskupit podle projektu, definice a typu odkazu, jako je čtení nebo zápis. Můžete také "zamknout" výsledky. |
| Přejít k implementaci | **Ctrl** + **F12** | Pomocí možnosti Přejít k definici u `override` klíčového slova můžete přejít na přepsaného člena. |
| Přejít k definici | **F12 nebo** **ctrl** + **kliknutí**| Stisknutím **klávesy Ctrl** při kliknutí přejděte k definici. |
| Náhled definice | **Alt** + **F12** | Vložené zobrazení definice |
| Vizualizér struktur | Šedé tečkované čáry mezi složených závorek | Zobrazení struktury kódu najetím myší |
| Navigace na dekompilovaná sestavení | **F12 nebo** **ctrl** + **kliknutí** | Povolením této funkce přejděte k externímu zdroji (dekompilované pomocí ILSpy): **Nástroje** Možnosti Textový editor C# Upřesnit Povolení navigace  >    >    >    >    >  **na dekompilované zdroje**. |

![Přejít na vše a najít všechny odkazy](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>Vylepšená technologie IntelliSense

Pomocí IntelliCode Visual Studio k získání [dokončování](/visualstudio/intellicode/intellicode-visual-studio) kódu s kontextem namísto pouze abecedního seznamu. Můžete také vytrénovat [vlastní model IntelliSense](/visualstudio/intellicode/custom-model-faq) na základě vlastních knihoven specifických pro doménu.

## <a name="unit-testing"></a>Testování jednotek

Počínaje Visual Studio 2017 existuje řada vylepšení prostředí pro testování. Testovat můžete pomocí testovacích architektur MSTest v1, MSTest v2, NUnit nebo XUnit.

- **Zjišťování testů v Průzkumníku** testů je rychlé.

- Uspořádejte testy v **Průzkumníku testů pomocí** *hierarchického řazení*.

   ![Zobrazení hierarchie pro Průzkumník textu v Visual Studio](../ide/media/VSGuide_Testing.png)

- [Živé testování částí](../test/live-unit-testing.md) průběžně spouští testy ovlivněné změnami kódu a aktualizacemi ikon v vloženém editoru, abyste věděli stav testů. Zahrnutí nebo vyloučení konkrétních testů nebo testovacích projektů ze sady živých testů (Visual Studio Enterprise edice.)

## <a name="debugging"></a>Ladění

Mezi možnosti Visual Studio ladění patří:

::: moniker range=">=vs-2019"

- Možnost hledat řetězec v oknech **Sledovat**, Automatické **hodnoty** a **Místní** hodnoty.
- *Spusťte příkaz a* klikněte na , který umožňuje najet myší na řádek kódu, kliknout na zelenou ikonu přehrávání, která se zobrazí, a spustit program, dokud nedosáhne tohoto řádku.
- Pomocník **pro výjimky**, který do dialogového okna zasune nejdůležitější informace na nejvyšší úrovni, například proměnnou v `null` objektu `NullReferenceException` .
- [Krok zpět ladění](../debugger/view-historical-application-state.md), který umožňuje vrátit se k předchozím zarážkám nebo krokům a zobrazit stav aplikace tak, jak byl v minulosti.
- [Ladění snímků](/azure/application-insights/app-insights-snapshot-debugger), které umožňuje prozkoumat stav živé webové aplikace v okamžiku vyvolání výjimky (musí být v Azure).

::: moniker-end

::: moniker range="vs-2017"

- *Spusťte příkaz a* klikněte na , který umožňuje najet myší na řádek kódu, kliknout na zelenou ikonu přehrávání, která se zobrazí, a spustit program, dokud nedosáhne tohoto řádku.
- Pomocník **pro výjimky**, který do dialogového okna zasune nejdůležitější informace na nejvyšší úrovni, například proměnnou v `null` objektu `NullReferenceException` .
- [Krok zpět ladění](../debugger/view-historical-application-state.md), který umožňuje vrátit se k předchozím zarážkám nebo krokům a zobrazit stav aplikace tak, jak byl v minulosti.
- [Ladění snímků](/azure/application-insights/app-insights-snapshot-debugger), které umožňuje prozkoumat stav živé webové aplikace v okamžiku vyvolání výjimky (musí být v Azure).

::: moniker-end

![Pomocník pro výjimky v Visual Studio](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>Správa verzí

K ukládání a aktualizaci kódu v nástroji můžete použít Git nebo TFVC Visual Studio.

::: moniker range=">=vs-2019"

- Nainstalujte [si žádosti o Visual Studio,](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs) abyste vytvořili, kontrolujte, rezervovat a spouštěl žádosti o Visual Studio.

::: moniker-end

- Uspořádejte místní změny [do Team Explorer](reference/team-explorer-reference.md) a pomocí stavového řádku sledujte probíhající potvrzení a změny.

- Nastavte průběžnou integraci a doručování pro ASP.NET projektů uvnitř Visual Studio pomocí nástrojů pro průběžné doručování [pro Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) rozšíření.

![Source control in Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>O jakých dalších funkcích mám vědět?

Tady je seznam editorů a funkcí pro produktivitu, aby psaní kódu bylo efektivnější. Některé funkce může být potřeba povolit, protože jsou ve výchozím nastavení vypnuté (mohou indexovat věci na vašem počítači, jsou kontroverzní nebo jsou aktuálně experimentální).

| Funkce | Podrobnosti | Jak povolit |
|-|-|-|
| Najít soubor v Průzkumník řešení | Zvýrazní aktivní soubor v **Průzkumník řešení** | **Nástroje**  >  **Možnosti**  >  **Projekty a řešení**  >  **Sledovat aktivní položku v Průzkumník řešení** |
| Přidat použití pro typy v referenčních sestaveních a balíčcích NuGet | Zobrazuje žárovku chyby s opravou kódu pro instalaci balíčku NuGet pro neodkazový typ. | **Nástroje**  >  **Možnosti**  >  **Textový editor**  >  **Jazyk C#**  >  **Rozšířené možnosti**  >  **Navrhnout použití typů v referenčních sestaveních** a **navrhovat použití pro typy v balíčcích NuGet** |
| Povolení úplné analýzy řešení | Zobrazit všechny chyby ve vašem řešení v **Seznam chyb** | **Nástroje**  >  **Možnosti**  >  **Textový editor**  >  **Jazyk C#**  >  **Rozšířené možnosti**  >  **Povolit úplnou analýzu řešení** |
| Povolit navigaci na dekompilované zdroje | Umožňuje přejít na definici typů/členů z externích zdrojů a použít Decompiler ILSpy k zobrazení těla metody. | **Nástroje**  >  **Možnosti**  >  **Textový editor**  >  **Jazyk C#**  >  **Rozšířené možnosti**  >  **Povolit navigaci na dekompilované zdroje** |
| Režim dokončení/návrhu | Změní chování při dokončování v IntelliSense. Vývojáři, kteří IntelliJ pozadí, obvykle používají jiné než výchozí nastavení. | **Nabídka**  >  **Upravit**  >  **IntelliSense**  >  **Přepnout režim dokončování** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Zobrazí referenční informace o kódu a historii změn v editoru. (Indikátory CodeLens správy zdrojového kódu nejsou k dispozici v edici Visual Studio Community Edition.) | **Nástroje**  >  **Možnosti**  >  **Textový editor**  >  **Všechny jazyky**  >  **CodeLens** |
| [Fragmenty kódu](../ide/visual-csharp-code-snippets.md) | Běžný často používaný kód s kódem Help unstub | Zadejte název fragmentu a dvakrát stiskněte klávesu **TAB** . |
