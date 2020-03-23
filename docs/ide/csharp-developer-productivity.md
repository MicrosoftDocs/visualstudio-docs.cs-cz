---
title: Zvyšte svou produktivitu pro vývoj rozhraní .NET
description: Přehled navigace, analýzy kódu, testování částí a dalších funkcí, které vám pomohou rychleji psát kód .NET.
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 0aa8e19f2be78671587dd1d9bc6254306c82a78c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567499"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>Visual Studio produktivity průvodce pro vývojáře C#

Zjistěte, jak Visual Studio dělá vývojáře produktivnějšími než kdy dřív. Využijte našich vylepšení výkonu a produktivity, jako je navigace do dekompilovaných sestavení, návrhy názvů proměnných při psaní, zobrazení hierarchie v **Průzkumníku testů**, Přechod na vše **(Ctrl**+**T)** pro navigaci na deklarace souboru/typu/člena/symbolu, inteligentní pomocník pro **výjimky**, konfiguraci a vynucení stylu kódu a mnoho refaktoringů a oprav kódu.

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>Jsem zvyklý na klávesové zkratky z jiného editoru

::: moniker range="vs-2017"

**Novinka ve Visual Studiu 2017 verze 15.8**

::: moniker-end

Pokud pocházíte z jiného prostředí IDE nebo kódování, můžete změnit schéma klávesnice na *Visual Studio Code* nebo *ReSharper (Visual Studio)*:

![Schémata klávesnice v sadě Visual Studio](../ide/media/VS2017Guide-Keyboard.png)

Některá rozšíření také nabízejí schémata klávesnice:

- [Klávesové zkratky pro visual studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emulace Emacsu](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Následují oblíbené klávesové zkratky sady Visual Studio:

| Zástupce (všechny profily) | Příkaz | Popis |
|-|-|-|
| **Ctrl**+**T** | Přejít na vše | Přechod na libovolnou deklaraci souboru, typu, člena nebo symbolu |
| **F12** (také **Ctrl**+**Klikněte)** | Přejít na definici | Přechod na místo, kde je definován symbol |
| **Ctrl**+**F12** | Přejít na implementaci | Přechod ze základního typu nebo člena na jeho různé implementace |
| **Posun**+**F12** | Najít všechny odkazy | Zobrazit všechny symboly nebo literálové odkazy |
| **Alt**+**domů** | Přejít na základní typ | Navigace v řetězci dědičnosti nahoru |
| **Sklávesa Ctrl**+**.** (také **Alt**+**Enter** v c# profilu) | Rychlé akce a refaktoringy | Podívejte se, jaké opravy kódu, akce generování kódu, refaktoringy nebo jiné rychlé akce jsou k dispozici na pozici kurzoru nebo výběru kódu |
| **Ctrl**+**D** | Duplicitní řádek | Duplikuje řádek kódu, ve které se kurzor nachází (k dispozici ve **Visual Studiu 2017 verze 15.6** a novějších). |
| **Posuntovat**+**s alternativním**+**+**/**-** | Rozbalit/Vybrat smlouvu | Rozbalí nebo uvedne aktuální výběr v editoru (k dispozici ve **Visual Studiu 2017 verze 15.5** a novější) |
| **Shift** + **Alt** + **.** | Vložit další odpovídající stříšku | Přidá výběr a stříšku na další umístění, které odpovídá aktuální výběr (k dispozici v **Visual Studio 2017 verze 15.8** a novější) |
| **Ctrl**+**Q** | Search | Hledat všechna nastavení sady Visual Studio |
| **F5** | Spustit ladění | Spuštění ladění aplikace |
| **Ctrl**+**F5** | Spustit bez ladění | Spuštění aplikace místně bez ladění |
| **Ctrl**+**K**,**D** (výchozí profil) nebo **Ctrl**+**E**,**D** (C# Profil) | Formátovat dokument | Vyčistí porušení formátování v souboru na základě nastavení nového řádku, mezer a odsazení. |
| **Ctrl**+**Ctrl**+**E** **E** +**W** **Ctrl**, Ctrl E (výchozí profil) nebo Ctrl W , E (C# Profil)**\\** | Zobrazit seznam chyb | Zobrazení všech chyb v dokumentu, projektu nebo řešení |
| **Alt** + **PgUp/PgDn** | Přejít na další/předchozí problém | Přechod na předchozí/další chybu, upozornění a návrh v dokumentu (k dispozici ve **Visual Studiu 2017 verze 15.8** a novějších) |
| **Ctrl**+**K**,**/** | Přepnout komentář/komentář na jeden řádek | Tento příkaz přidá nebo odebere komentář jednoho řádku v závislosti na tom, zda je váš výběr již komentován. |
| **Posun kláves ctrl**+**Shift**+**/** | Přepnout blok komentáře nebo odkomentáře | Tento příkaz přidá nebo odebere blokové komentáře v závislosti na tom, co jste vybrali. |

> [!NOTE]
> Některá rozšíření zrušit vazbu výchozí visual studio keybindings. Chcete-li použít výše uvedené příkazy, obnovte své klíče do výchozích hodnot sady Visual Studio tak, že přejdete na **položku Nástroje** > **pro import a export nastavení** > **Obnovit všechna nastavení** nebo Obnovit**Keyboard** > **klávesnici****možnosti** >  **nástroje** > .

Další informace o klávesových zkratkách a příkazech naleznete v [tématu Pracovní zkratky](../ide/productivity-shortcuts.md) a [Oblíbené klávesové zkratky](default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md).

## <a name="navigate-quickly-to-files-or-types"></a>Rychlé procházení souborů nebo typů

Visual Studio má funkci s názvem **Přejít na vše** **(Ctrl**+**T).** **Možnost Přejít na vše** umožňuje rychle přejít na libovolnou deklaraci souboru, typu, člena nebo symbolu.

- Změňte umístění tohoto vyhledávacího panelu nebo vypněte náhled živé navigace pomocí ikony **ozubeného kola.**
- Filtruje výsledky pomocí `t mytype`syntaxe, například .
- Rozsah hledání pouze aktuální dokument.
- Porovnávání camelů je podporováno.

![Přejít na vše ve Visual Studiu](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules"></a>Vynucení pravidel stylu kódu

Soubor EditorConfig můžete použít ke kodifikaci konvencí kódování a nechat je cestovat se zdrojem.

![Vynucení stylu kódu v sadě Visual Studio](../ide/media/VSGuide_CodeStyle.png)

- Přidejte výchozí nebo . NET-style EditorConfig soubor do projektu výběrem **Přidat** > **novou položku**. V dialogovém okně **Přidat novou položku** vyhledejte "editorconfig". Vyberte některou ze šablon položek **editorconfig File** a pak zvolte **Přidat**.

   ![Šablony položek EditorConfig v sadě Visual Studio](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- Automaticky vytvořte soubor *.editorconfig* na základě nastavení stylu kódu **v** > **Options** > **textovém editoru nástrojů** > **C#** > **Styl kódu**.

   ![Generovat soubor .editorconfig z nastavení ve VS 2019](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- [Funkce odvození kódu](/visualstudio/intellicode/code-style-inference) IntelliCode pro Visual Studio odvodí styly kódu z existujícího kódu. Potom vytvoří neprázdný soubor EditorConfig s předvolbami stylu kódu, které jsou již definovány.

- Nakonfigurujte úroveň závažnosti pravidla stylu kódu přímo prostřednictvím editoru. Pokud aktuálně nemáte soubor .editorconfig, bude vygenerován za vás. Umístěte kurzor na chybu, upozornění nebo návrh a zadejte **ctrl**+**.** otevřete nabídku Rychlé akce a Refaktorings. Vyberte **Konfigurovat nebo potlačit problémy**. Potom vyberte pravidlo a zvolte úroveň závažnosti, kterou chcete pro toto pravidlo nakonfigurovat. Tím se aktualizuje stávající EditorConfig novou závažností pravidla.

   ![Konfigurace úrovně závažnosti pravidla stylu kódu přímo v editoru](../ide/media/configure-severity-level.png)

Prohlédněte si dokumentaci k [možnostem konvence kódování .NET,](editorconfig-code-style-settings-reference.md) která také obsahuje příklad úplného souboru EditorConfig.

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>Vyčištění kódu

Visual Studio poskytuje formátování souboru kódu na vyžádání, včetně předvoleb stylu kódu, prostřednictvím funkce **Vyčištění kódu.** Chcete-li spustit vyčištění kódu, klepněte na ikonu koště v dolní části editoru nebo stiskněte **kombinaci kláves Ctrl**+**K**, **Ctrl**+**E**.

![Tlačítko Vyčištění kódu v Visual Studiu 2019](media/execute-code-cleanup.png)

Můžete také spustit vyčištění kódu v celém projektu nebo řešení. Klikněte pravým tlačítkem myši na název projektu nebo řešení v **Průzkumníku řešení**, vyberte **analyzovat a vyčistit kód**a pak vyberte Spustit vyčištění **kódu**.

![Spuštění vyčištění kódu napříč celým projektem nebo řešením](media/run-code-cleanup-project-solution.png)

Kromě formátování souboru pro mezery, odsazení a tak dále, **Vyčištění kódu** také použije vybrané styly kódu. Vaše předvolby pro každý styl kódu jsou čteny ze [souboru EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files), pokud máte jeden pro projekt nebo z [nastavení stylu kódu](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) v dialogovém okně **Možnosti.**

::: moniker-end

## <a name="refactorings-and-code-fixes"></a>Refaktoringy a opravy kódu

Visual Studio je dodáván s mnoha refaktorings, akce generování kódu a opravy kódu. Červené vlnovky představují chyby, zelené vlnovky představují upozornění a tři šedé tečky představují návrhy kódu. Ke opravám kódu se dostanete kliknutím na ikonu žárovky nebo šroubováku nebo stisknutím **klávesy Ctrl**+**.** nebo **Alt**+**Enter**. Každá oprava je dodávána s oknem náhledu, které zobrazuje rozdíl živého kódu o tom, jak oprava funguje.

Mezi oblíbené rychlé opravy a refaktoringy patří:

- Přejmenovat
- extrahování metody
- Změnit podpis metody
- Generovat konstruktor
- Generovat metodu
- Přesunout text do souboru
- Přidat kontrolu null
- Přidat parametr
- Odebrání nepotřebných použití
- Foreach Loop na LINQ query nebo linq metoda
- Vytáhnout členy nahoru

Další informace naleznete v [tématu funkce generování kódu](code-generation-in-visual-studio.md).

Můžete [nainstalovat analyzátory FxCop,](../code-quality/install-fxcop-analyzers.md) které označují problémy s kódem. Nebo napište vlastní refaktoring nebo opravu kódu pomocí [analyzátorů Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix).

Několik členů komunity napsalo bezplatná rozšíření, která přidávají další kontroly kódu:

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [SonarLint pro Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StylCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [KódCracker](https://www.nuget.org/packages/codecracker.CSharp/)

![Refaktoringy v sadě Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Najít použití, přejít na implementaci a přejít na dekompilovaná sestavení

Visual Studio má mnoho funkcí, které vám pomohou vyhledávat a [procházet váš kód](../ide/navigating-code.md).

| Funkce | Zástupce | Podrobnosti/vylepšení |
|- | - | -|
| Najít všechny odkazy | **Posun**+**F12**| Výsledky jsou obarveny a mohou být seskupeny podle typu projektu, definice a typu odkazu, například pro čtení nebo zápis. Můžete také "zamknout" výsledky. |
| Přejít na implementaci | **Ctrl**+**F12** | Pomocí klíčového slova Přejít na definici `override` můžete přejít na potlačený člen. |
| Přejít na definici | **F12** nebo **Ctrl**+**klikněte**| Stisknutím **klávesy Ctrl** při kliknutí přejdete na definici. |
| Náhled definice | **Alt**+**F12** | Vstěhovavé zobrazení definice |
| Vizualizér struktury | Šedé, tečkované čáry mezi závorkami | Najeďte na to, abyste viděli strukturu kódu. |
| Navigace do dekompilovaných sestavení | **F12** nebo **Ctrl**+**klikněte** | Přejděte na externí zdroj (dekompilovaný s ILSpy) povolením funkce:**Možnosti** >  **nástroje** > **Textový editor** > **C#** > **Upřesnit** > **Povolit navigaci na dekompilované zdroje**. |

![Přejít na vše a najít všechny odkazy](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>Vylepšená technologie IntelliSense

Použití IntelliCode pro Visual Studio získat [dokončování kódu s ohledem na kontext](/visualstudio/intellicode/intellicode-visual-studio) namísto pouze abecední seznam. Můžete také trénovat [vlastní model IntelliSense](/visualstudio/intellicode/custom-model-faq) na základě vlastních knihoven specifických pro doménu.

## <a name="unit-testing"></a>Testování částí

Počínaje Visual Studio 2017, existuje mnoho vylepšení testování. Můžete testovat pomocí testovacích rámců MSTest v1, MSTest v2, NUnit nebo XUnit.

- Zjišťování testů **průzkumníka testů** je rychlé.

- Uspořádejte testy v **Průzkumníku testů** pomocí *hierarchického řazení*.

   ![Zobrazení hierarchie pro Průzkumníka textu v sadě Visual Studio](../ide/media/VSGuide_Testing.png)

- [Testování živých částí](../test/live-unit-testing.md) průběžně spouští testy ovlivněné změnami kódu a aktualizacemi vřádíkových editorů, abyste věděli o stavu testů. Zahrňte nebo vylučte konkrétní testy nebo testovací projekty ze sady živých testů. (Pouze edice Visual Studio Enterprise.)

## <a name="debugging"></a>ladění

Mezi možnosti ladění sady Visual Studio patří:

::: moniker range=">=vs-2019"

- Možnost hledání řetězce v oknech **Watch**, **Autos**a **Locals.**
- *Spustit klikněte*na tlačítko , který vám umožní najet vedle řádku kódu, klikněte na zelenou ikonu 'přehrát', která se zobrazí, a spusťte program, dokud nedosáhne tohoto řádku.
- **Pomocník pro výjimky**, který umístí nejdůležitější informace na nejvyšší úroveň v `null` dialogovém `NullReferenceException`okně, například proměnná je v .
- [Krok zpět ladění](../debugger/view-historical-application-state.md), který umožňuje přejít zpět na předchozí zarážky nebo kroky a zobrazit stav aplikace, jak tomu bylo v minulosti.
- [Ladění snímků](/azure/application-insights/app-insights-snapshot-debugger), které umožňuje prozkoumat stav živé webové aplikace v okamžiku, kdy byla vyvolána výjimka (musí být v Azure).

::: moniker-end

::: moniker range="vs-2017"

- *Spustit klikněte*na tlačítko , který vám umožní najet vedle řádku kódu, klikněte na zelenou ikonu 'přehrát', která se zobrazí, a spusťte program, dokud nedosáhne tohoto řádku.
- **Pomocník pro výjimky**, který umístí nejdůležitější informace na nejvyšší úroveň v `null` dialogovém `NullReferenceException`okně, například proměnná je v .
- [Krok zpět ladění](../debugger/view-historical-application-state.md), který umožňuje přejít zpět na předchozí zarážky nebo kroky a zobrazit stav aplikace, jak tomu bylo v minulosti.
- [Ladění snímků](/azure/application-insights/app-insights-snapshot-debugger), které umožňuje prozkoumat stav živé webové aplikace v okamžiku, kdy byla vyvolána výjimka (musí být v Azure).

::: moniker-end

![Pomocník pro výjimky v sadě Visual Studio](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>Správa verzí

Můžete použít git nebo TFVC k ukládání a aktualizaci kódu v sadě Visual Studio.

::: moniker range=">=vs-2019"

- Nainstalujte [žádosti o přijetí vyžádat pro Visual Studio](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs) k vytvoření, kontrole, rezervování a spuštění žádostí o přijetí vyžádat bez opuštění sady Visual Studio.

::: moniker-end

- Uspořádejte místní změny v [Průzkumníkovi týmu](reference/team-explorer-reference.md) a pomocí stavového řádku můžete sledovat čekající potvrzení a změny.

- Nastavte průběžnou integraci a doručování pro vaše projekty ASP.NET uvnitř sady Visual Studio pomocí [nástrojů nepřetržitého doručování pro](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) rozšíření Visual Studio.

![Ovládací prvek zdroj v sadě Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>O jakých dalších funkcích bych měl vědět?

Zde je seznam editoru a produktivity funkce, aby se psaní kódu efektivnější. Některé funkce může být nutné povolit, protože jsou ve výchozím nastavení vypnuté (mohou indexovat věci v počítači, jsou kontroverzní nebo jsou aktuálně experimentální).

| Funkce | Podrobnosti | Jak povolit |
|-|-|-|
| Hledání souboru v Průzkumníku řešení | Zvýraznění aktivního souboru v **Průzkumníku řešení** | **Možnosti** >  > nástrojů**Projekty a řešení** > **sledovat aktivní položku v Průzkumníku řešení** **Options** |
| Přidání použití pro typy v referenčních sestaveních a balíčcích NuGet | Zobrazuje chybovou žárovku s opravou kódu pro instalaci balíčku NuGet pro neodkazovaný typ. | **Možnosti** > **Options** > **Advanced** > **Text Editor** > **C#****Suggest usings for types in reference assemblies** **Suggest usings for types in NuGet packages** nástrojů Textový editor C# Rozšířené Navrhnout použití pro typy v referenčních sestaveních a Navrhnout použití pro typy v balíčcích NuGet >  |
| Povolení úplné analýzy řešení | Zobrazit všechny chyby v řešení v **seznamu chyb** | **Možnosti** > **Options** >  >  > **Advanced****Text Editor****C#****Enable full solution analysis** nástrojů Textový editor C# Upřesnit Povolit úplnou analýzu řešení >  |
| Povolit navigaci pro dekompilované zdroje | Povolit přejít na definici typů/členů z externích zdrojů a použít dekompilátor ILSpy k zobrazení těl metod | **Možnosti** > **Options** >  >  > **Advanced****Text Editor****C#****Enable navigation to decompiled sources** nástrojů Textový editor C# Upřesnit Povolit navigaci do dekompilovaných zdrojů >  |
| Režim dokončení/návrhu | Změní chování dokončení v intelliSense. Vývojáři se pozadím IntelliJ zde obvykle používají jiné než výchozí nastavení. | **Nabídka** > **Upravit** > **režim dokončování technologie** **IntelliSense** >  |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Zobrazí informace o odkazech na kód a historii změn v editoru. (Indikátory CodeLens správy zdrojového kódu nejsou k dispozici v edici Visual Studio Community.) | **Možnosti** >  > nástroje**Textový editor** > **všech jazyků** > **CodeLens** **Options** |
| [Fragmenty kódu](../ide/visual-csharp-code-snippets.md) | Pomoc se zakázaným inzerováním běžného standardního kódu | Zadejte název úryvku a dvakrát stiskněte **klávesu Tab.** |
