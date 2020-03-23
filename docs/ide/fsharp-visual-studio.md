---
title: Nástroje jazyka F#
description: Zjistěte, které funkce sady Visual Studio jsou podporovány v jazyce F#.
ms.date: 07/11/2018
ms.topic: reference
helpviewer_keywords:
- F# features [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 75ebee68bf76a4dd5419942f79a3207c29673134
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565237"
---
# <a name="develop-with-visual-f-in-visual-studio"></a>Vývoj s Visual F# v sadě Visual Studio

Tento článek obsahuje informace o funkcích sady Visual Studio pro vývoj F#.

## <a name="install-f-support"></a>Podpora instalace Jazyka F#

Chcete-li vyvíjet s F# v sadě Visual Studio, nejprve nainstalujte **úlohu vývoje plochy .NET,** pokud jste tak ještě neučinili. Úlohy sady Visual Studio nainstalujete prostřednictvím Instalační služby sady Visual Studio, kterou můžete otevřít výběrem **možnosti Nástroje** > **získat nástroje a funkce**.

![Úloha vývoje pracovních prostředí .NET v sadě Visual Studio](media/dotnet-desktop-development-workload.png)

## <a name="f-project-features"></a>Funkce projektu F#

Různé šablony projektů a položek jsou k dispozici pro F# v sadě Visual Studio. Následující obrázek znázorňuje některé šablony projektu F# pro rozhraní .NET Core a .NET Standard:

![Šablony projektů F# v sadě Visual Studio](media/fsharp-project-templates.png)

Následující obrázek znázorňuje některé šablony položek F#:

![Šablony položek Jazyka F# v sadě Visual Studio](media/fsharp-item-templates.png)

Další informace o šablonách položek pro přístup k datům naleznete v [tématu Zprostředkovatelé typu F#](/dotnet/fsharp/tutorials/type-providers/index).

Následující tabulka shrnuje funkce ve vlastnostech projektu pro F#:

|Nastavení projektu|Podporováno v F#?|Poznámky|
|---------------|----------------|-----|
|Soubory prostředků|Ano||
|Nastavení sestavení, ladění a odkazu|Ano||
|Cílení na více verzí|Ano||
|Ikona a manifest|Ne|K dispozici prostřednictvím možností příkazového řádku kompilátoru.|
|ASP.NET klientské služby|Ne||
|ClickOnce|Ne|Pokud je k dispozici, použijte klientský projekt v jiném jazyce .NET.|
|Vytváření silných názvů|Ne|K dispozici prostřednictvím možností příkazového řádku kompilátoru.|
|Publikování a správa verzí sestavení|Ne||
|Analýza kódu|Ne|Nástroje pro analýzu kódu lze spustit ručně nebo jako součást příkazu po sestavení.|
|Zabezpečení (změna úrovně důvěryhodnosti)|Ne||

## <a name="project-designer"></a>návrhář projektu

**Návrhář projektu** se skládá z několika stránek vlastností projektu seskupených podle souvisejících funkcí. Stránky, které jsou k dispozici pro projekty F# jsou většinou podmnožinou stránek, které jsou k dispozici pro jiné jazyky, a jsou popsány v následující tabulce. Odkazy jsou k dispozici na odpovídající c# **návrháře projektu** stránky.

|Stránka Návrháře projektu|Související odkazy|Popis|
| - |-------------|-----------|
|Aplikace|[Stránka aplikace, Návrhář projektu](reference/application-page-project-designer-csharp.md)|Umožňuje zadat nastavení a vlastnosti na úrovni aplikace, například zda vytváříte knihovnu nebo spustitelný soubor, jakou verzi rozhraní .NET cíle aplikace a informace o tom, kde jsou uloženy soubory prostředků, které aplikace používá.|
|Sestavení|[Stránka sestavení, Návrhář projektu](reference/build-page-project-designer-csharp.md)|Umožňuje řídit, jak je kód kompilován.|
|Události sestavení|[Stránka Události sestavení, Návrhář projektu](reference/build-events-page-project-designer-csharp.md)|Umožňuje zadat příkazy, které mají být spuštěny před nebo po kompilaci.|
|Ladění|[Stránka Ladění, návrhář projektu](reference/debug-page-project-designer.md)|Umožňuje řídit, jak bude aplikace spuštěna během ladění. To zahrnuje, jaké příkazy použít a jaký je počáteční adresář vaší aplikace a všechny speciální režimy ladění, které chcete povolit, jako je nativní kód a SQL.|
|Balíček (pouze sada SDK.NET)|Není dostupné.|Umožňuje definovat metadata balíčku NuGet při publikování jako balíček NuGet.|
|Referenční cesty|[Správa odkazů v projektu](managing-references-in-a-project.md)|Umožňuje určit, kde hledat sestavení, na kterých kód závisí.|
|Prostředky (pouze sada SDK.NET)|Není dostupné.|Umožňuje generovat a spravovat výchozí soubor prostředků.|

### <a name="f-specific-settings"></a>Nastavení specifická pro F#

Následující tabulka shrnuje nastavení, která jsou specifická pro F#:

|Stránka Návrháře projektu|Nastavení|Popis|
| - |-------|-----------|
|Sestavení|Generovat volání ocasu|Pokud je tato možnost vybrána, umožňuje použití příkazu Microsoft Intermediate Language (MSIL). To způsobí, že rámec zásobníku znovu použít pro funkce rekurzivní ocas. Ekvivalentní možnost `--tailcalls` kompilátoru.|
|Sestavení|Další příznaky|Umožňuje zadat další možnosti příkazového řádku kompilátoru.|

## <a name="code-and-text-editor-features"></a>Funkce kódového a textového editoru

Následující funkce kódu sady Visual Studio a textové editory jsou podporovány v jazyce F#:

|Funkce|Popis|Podporováno v F#?|
|-------|-----------|----------------|
|Automaticky komentovat|Umožňuje komentovat nebo odkomentovat části kódu.|Ano|
|Automatické formátování|Přeformátuje kód se standardním odsazením a stylem.|Ne|
|Záložky|Umožňuje ukládat místa v editoru.|Ano|
|Odsazení změny|Odsazení nebo odsazení vybraných řádků.|Ano|
|Inteligentní odsazení|Automaticky odsaze a de-odsaze kurzor podle f# oboru pravidla.|Ano|
|[Vyhledání a nahrazení textu](finding-and-replacing-text.md)|Umožňuje vyhledávat v souboru, projektu nebo řešení a potenciálně měnit text.|Ano|
|Přejít na definici rozhraní .NET API|Když je kurzor umístěn v rozhraní .NET API, zobrazí kód generovaný z metadat rozhraní .NET.|Ne|
|Přejít na definici uživatelem definovaného rozhraní API|Pokud je kurzor na entitě programu, kterou jste definovali, přesune kurzor do umístění v kódu, kde je entita definována.|Ano|
|Přechod na řádek|Umožňuje přejít na určitý řádek v souboru podle čísla řádku.|Ano|
|Navigační panely v horní části souboru|Umožňuje přejít na umístění v kódu, například podle názvu funkce.|Ano|
|Pokyny pro strukturu bloků|Zobrazuje pokyny, které označují f# obory, které lze najet přes pro náhled.|Ano|
|[Sbalování](outlining.md)|Umožňuje sbalit části kódu a vytvořit tak kompaktnější zobrazení.|Ano|
|Tabify|Převede mezery na tabulátory.|Ano|
|Zabarvení typu|Zobrazí definované názvy typů ve speciální barvě.|Ano|
|Rychlé hledání. Viz Okno Rychlé hledání, hledání a nahrazování.|Umožňuje vyhledávat v souboru nebo projektu.|Ano|
|**Ctrl**+**klikněte** na Přejít na definici|Umožňuje podržet **klávesu Ctrl** a kliknout na symbol F# pro vyvolání funkce Přejít na definici.|Ano|
|Přejít na definici z quickinfo|Klikací symboly uvnitř popisků, které vyvolávají Přejít na definici.|Ano|
|Přejít na Vše|Umožňuje globální, fuzzy odpovídající navigaci pro všechny konstrukce F# přes **Ctrl**+**T**.|Ano|
|Vřádkové přejmenování|Přejmenuje všechny výskyty symbolu v řádku.|Ano|
|Najít všechny reference|Vyhledá všechny výskyty symbolu v základu kódu.|Ano|
|Zjednodušit opravu kódu názvu|Odebere zbytečné kvalifikátory pro symboly F#.|Ano|
|Odebrat `open` opravu nepoužívaného kódu výpisu|Odebere všechny `open` nepotřebné příkazy v dokumentu.|Ano|
|Oprava nevyužité hodnoty|Navrhuje přejmenování nepoužívaného identifikátoru tak, aby podtržítka.|Ano|

Obecné informace o úpravách kódu v sadě Visual Studio a funkcích textového editoru naleznete [v tématu Zápis kódu v editoru](writing-code-in-the-code-and-text-editor.md).

## <a name="intellisense-features"></a>Funkce technologie IntelliSense

Následující tabulka shrnuje funkce Technologie IntelliSense, které jsou podporovány a nejsou podporovány v f#:

|Funkce|Popis|Podporováno v F#?|
|-------|-----------|----------------|
|Automatická implementace rozhraní|Generuje zástupné procedury kódu pro metody rozhraní.|Ano|
|Fragmenty kódu|Vloží kód z knihovny běžných kódování konstrukce do témat.|Ne|
|Dokončit slovo|Ukládá psaní vyplněním slov a jmen při psaní.|Ano|
|Automatické dokončování|Pokud je tato možnost povolena, způsobí, že dokončení slova vybere při psaní první shodu, místo aby čekalo na jednu z nich nebo stisknutí **klávesy Ctrl**+**Space**.|Ano|
|Nabídka dokončení symbolů v neotevřených oborech názvů|Při automatickém dokončování je navržen odpovídající symbol, který se nachází `open` v neotevřeném oboru názvů, který nabízí dokončení odpovídajícího příkazu, pokud je vybrán.|Ano|
|Generovat prvky kódu|Umožňuje generovat kód se zakázaným inzerováním pro různé konstrukce.|Ne|
|Vypsat členy|Při zadání operátoru přístupu člena (.), zobrazí členy pro typ.|Ano|
|Uspořádání použití/otevření|Uspořádá obory názvů, na které se odkazuje **pomocí** příkazů v c# nebo **otevřených** direktiv v F#.|Ne|
|Informace o parametrech|Zobrazuje užitečné informace o parametrech při psaní volání funkce.|Ano|
|Rychlé informace|Zobrazí úplnou deklaraci libovolného identifikátoru v kódu.|Ano|
|Automatické dokončení ortézy|Automaticky dokončí syntaxe podobné syntaxi f# transakčním způsobem.|Ano|

Obecné informace o technologie IntelliSense naleznete v [tématu Use IntelliSense](using-intellisense.md).

## <a name="debugging-features"></a>Ladění funkcí

Následující tabulka shrnuje funkce, které jsou k dispozici při ladění kódu F#:

|Funkce|Popis|Podporováno v F#?|
|-------|-----------|----------------|
|Automatické hodnoty – okno|Zobrazuje automatické nebo dočasné proměnné.|Ne|
|Zarážky|Umožňuje pozastavit provádění kódu v určitých bodech během ladění.|Ano|
|Podmíněné zarážky|Umožňuje zarážky, které testují podmínku, která určuje, zda má být spuštění pozastaveno.|Ano|
|Upravit a pokračovat|Umožňuje kód upravit a zkompilovat při ladění spuštěného programu bez zastavení a restartování ladicího programu.|Ne|
|Vyhodnocení výrazu|Vyhodnocuje a spouští kód za běhu.|Ne, ale lze použít vyhodnocení výrazu C#, i když je nutné použít syntaxi jazyka C#.|
|Historické ladění|Umožňuje krokovat do dříve spuštěný kód.|Ano|
|Místní hodnoty – okno|Zobrazuje místně definované hodnoty a proměnné.|Ano|
|Spustit kurzor|Umožňuje spustit kód, dokud není dosaženo řádku, který obsahuje kurzor.|Ano|
|Krok do|Umožňuje předem spuštění a přesunout do libovolného volání funkce.|Ano|
|Krok přes|Umožňuje předem spuštění v aktuálním rámci zásobníku a přesunout kolem jakékoli volání funkce.|Ano|

Obecné informace o ladicím programu sady Visual Studio naleznete v tématu [Ladění v sadě Visual Studio](../debugger/index.yml).

## <a name="additional-tools"></a>Další nástroje

Následující tabulka shrnuje podporu pro F# v nástrojích sady Visual Studio.

|Nástroj|Popis|Podporováno v F#?|
|----|-----------|----------------|
|Hierarchie volání|Zobrazí vnořenou strukturu volání funkce v kódu.|Ne|
|Metriky kódu|Shromažďuje informace o kódu, například počty řádků.|Ne|
|zobrazení tříd|Poskytuje zobrazení kódu v projektu na základě typu.|Ne|
|[Okno Seznam chyb](reference/error-list-window.md)|Zobrazí seznam chyb v kódu.|Ano|
|[F# Interactive](/dotnet/fsharp/tutorials/fsharp-interactive/)|Umožňuje zadat (nebo zkopírovat a vložit) kód F# a spustit jej okamžitě, nezávisle na sestavení projektu. Interaktivní okno Jazyka F# je čtecí, vyhodnotit, tisková smyčka (REPL).|Ano|
|prohlížeč objektů|Umožňuje zobrazit typy v sestavení.|F# typy, jak se zobrazují v kompilovaných sestaveních nezobrazují přesně tak, jak je vytvářet. Můžete procházet zkompilované reprezentace F# typy, ale nelze zobrazit typy, jak se zobrazují z F#.|
|[Okno Výstup](reference/output-window.md)|Zobrazí výstup sestavení.|Ano|
|Analýza výkonu|Poskytuje nástroje pro měření výkonu kódu.|Ano|
|Vlastnosti – okno|Zobrazí a povolí úpravy vlastností objektu ve vývojovém prostředí, které má fokus.|Ano|
|Průzkumník serveru|Poskytuje způsoby interakce s různými serverovými prostředky.|Ano|
|Průzkumník řešení|Umožňuje zobrazit a spravovat projekty a soubory.|Ano|
|Seznam úkolů|Umožňuje spravovat pracovní položky týkající se vašeho kódu.|Ne|
|Testovací projekty|Poskytuje funkce, které vám pomohou otestovat kód.|Ne|
|Sada nástrojů|Zobrazí karty, které obsahují přetažené objekty, jako jsou ovládací prvky a části textu nebo kódu.|Ano|

## <a name="see-also"></a>Viz také

- [Příručka F# (rozhraní.NET Framework)](/dotnet/fsharp/)
- [Začínáme s F# ve Visual Studiu](/dotnet/fsharp/get-started/get-started-visual-studio)
