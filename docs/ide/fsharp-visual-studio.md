---
title: Nástroje jazyka F#
description: Seznamte se s funkcemi sady Visual Studio, F#které se podporují v nástroji.
ms.date: 07/11/2018
ms.topic: reference
helpviewer_keywords:
- F# features [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fef50748942aaa800cf1181e4c8f8b8a030f99ee
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211312"
---
# <a name="develop-with-visual-f-in-visual-studio"></a>Vývoj s využitím vizuálu F# v aplikaci Visual Studio

Tento článek obsahuje informace o funkcích sady Visual Studio F# pro vývoj.

## <a name="install-f-support"></a>Instalace F# podpory

Pro vývoj v F# nástroji v aplikaci Visual Studio nejprve nainstalujte úlohu **vývoj pro desktopy .NET** , pokud jste to ještě neudělali. Úlohy sady Visual Studio nainstalujete prostřednictvím instalační program pro Visual Studio, které můžete otevřít tak, že vyberete **nástroje** > **získat nástroje a funkce**.

![Úloha vývoj desktopových aplikací .NET v aplikaci Visual Studio](media/dotnet-desktop-development-workload.png)

## <a name="f-project-features"></a>F#funkce projektu

F# V aplikaci Visual Studio jsou k dispozici různé šablony projektů a položek. Následující obrázek ukazuje některé šablony F# projektu pro .NET Core a .NET Standard:

![F#šablony projektů v aplikaci Visual Studio](media/fsharp-project-templates.png)

Následující obrázek ukazuje některé šablony F# položek:

![F#šablony položek v aplikaci Visual Studio](media/fsharp-item-templates.png)

Další informace o šablonách položek pro přístup k datům naleznete v tématu [ F# Poskytovatelé typů](/dotnet/fsharp/tutorials/type-providers/index).

Následující tabulka shrnuje funkce ve vlastnostech projektu pro F#:

|Nastavení projektu|Podporuje se F#v?|Poznámky|
|---------------|----------------|-----|
|Soubory prostředků|Ano||
|Nastavení sestavení, ladění a odkazů|Ano||
|Cílení na více verzí|Ano||
|Ikona a manifest|Ne|K dispozici prostřednictvím možností příkazového řádku kompilátoru.|
|ASP.NET klientské služby|Ne||
|ClickOnce|Ne|Použijte projekt klienta v jiném jazyce rozhraní .NET (je-li k dispozici).|
|Vytváření silných názvů|Ne|K dispozici prostřednictvím možností příkazového řádku kompilátoru.|
|Publikování sestavení a správa verzí|Ne||
|Analýza kódu|Ne|Nástroje pro analýzu kódu lze spustit ručně nebo jako součást příkazu po sestavení.|
|Zabezpečení (změna úrovní důvěryhodnosti)|Ne||

## <a name="project-designer"></a>návrhář projektu

**Návrhář projektu** se skládá z několika stránek vlastností projektu seskupených podle souvisejících funkcí. Stránky dostupné pro F# projekty jsou většinou podmnožinou dostupných pro jiné jazyky a jsou popsány v následující tabulce. Odkazy jsou k dispozici na C# odpovídající stránce **Návrháře projektu** .

|Stránka Návrháře projektu|Související odkazy|Popis|
| - |-------------|-----------|
|Aplikace|[Stránka aplikace, Návrhář projektu](reference/application-page-project-designer-csharp.md)|Umožňuje zadat nastavení a vlastnosti na úrovni aplikace, například zda vytváříte knihovnu nebo spustitelný soubor, jakou verzi rozhraní .NET aplikace cílí, a informace o tom, kde jsou uloženy soubory prostředků, které aplikace používá.|
|Sestavení|[Stránka sestavení, Návrhář projektu](reference/build-page-project-designer-csharp.md)|Umožňuje řídit způsob kompilování kódu.|
|Události sestavení|[Stránka události sestavení, Návrhář projektu](reference/build-events-page-project-designer-csharp.md)|Umožňuje zadat příkazy, které se spustí před nebo po kompilaci.|
|Ladit|[Stránka Ladění, Návrhář projektu](reference/debug-page-project-designer.md)|Umožňuje řídit, jak aplikace běží během ladění. To zahrnuje příkazy, které se mají použít, a informace o tom, co je spouštěcí adresář vaší aplikace, a všechny speciální režimy ladění, které chcete povolit, jako je například nativní kód a SQL.|
|Balíček (jenom .NET SDK)|Není k dispozici|Umožňuje definovat metadata balíčku NuGet při publikování jako balíček NuGet.|
|Cesty odkazů|[Správa odkazů v projektu](managing-references-in-a-project.md)|Umožňuje určit, kde se mají hledat sestavení, na kterých závisí kód.|
|Prostředky (pouze sada .NET SDK)|Není k dispozici|Umožňuje generovat a spravovat výchozí soubor prostředků.|

### <a name="f-specific-settings"></a>F#-specifické nastavení

Následující tabulka shrnuje nastavení specifická pro F#:

|Stránka Návrháře projektu|Nastavení|Popis|
| - |-------|-----------|
|Sestavení|Generovat volání funkce tail|Pokud je tato možnost vybrána, umožňuje použití instrukce koncového jazyka MSIL (Microsoft Intermediate Language). To způsobí, že bude rámec zásobníku znovu použit pro funkce tail. Ekvivalent možnosti kompilátoru `--tailcalls` .|
|Sestavení|Další příznaky|Umožňuje zadat další možnosti příkazového řádku kompilátoru.|

## <a name="code-and-text-editor-features"></a>Funkce kódu a textového editoru

V F#nástroji jsou podporovány následující funkce editoru kódu a textu sady Visual Studio:

|Funkce|Popis|Podporuje se F#v?|
|-------|-----------|----------------|
|Automaticky komentovat|Umožňuje komentovat nebo odkomentovat oddíly kódu.|Ano|
|Automaticky formátovat|Přeformátuje kód pomocí standardního odsazení a stylu.|Ne|
|Záložky|Umožňuje ukládat místa v editoru.|Ano|
|Změnit odsazení|Odsadí nebo zruší odsazení vybraných řádků.|Ano|
|Inteligentní odsazení|Automaticky odsadí a odsadí kurzor podle pravidel určení F# rozsahu.|Ano|
|[Vyhledání a nahrazení textu](finding-and-replacing-text.md)|Umožňuje vyhledávat v souboru, projektu nebo řešení a potenciálně měnit text.|Ano|
|Přejít k definici rozhraní .NET API|Když je kurzor umístěný na rozhraní .NET API, zobrazuje kód vygenerovaný z metadat .NET.|Ne|
|Přejít k definici pro uživatelsky definované rozhraní API|Když se ukazatel myši nachází na entitě programu, kterou jste definovali, přesune kurzor do umístění ve vašem kódu, kde je entita definovaná.|Ano|
|Přechod na řádek|Umožňuje přejít na konkrétní řádek v souboru podle čísla řádku.|Ano|
|Navigační panely v horní části souboru|Umožňuje přejít do umístění v kódu, například jako název funkce.|Ano|
|Pokyny ke strukturám bloků|Zobrazuje pokyny, které F# označují obory, u kterých je možné najetí myší na verzi Preview.|Ano|
|[Sbalení](outlining.md)|Umožňuje sbalit části kódu a vytvořit tak kompaktnější zobrazení.|Ano|
|Převést na tabulátory|Převede mezery na tabulátory.|Ano|
|Zabarvení typu|Zobrazuje názvy definovaných typů ve speciální barvě.|Ano|
|Rychlé hledání. Viz okno rychlé hledání, najít a nahradit.|Umožňuje vyhledávat v souboru nebo v projektu.|Ano|
|+Přejít na definici**kliknutím** CTRL|Umožňuje podržet **klávesu CTRL** a kliknout na F# symbol a vyvolat přejít k definici.|Ano|
|Přejít k definici z QuickInfo|Klikněte na symboly v popiscích, které vyvolávají přejít k definici.|Ano|
|Přejít na vše|Umožňuje globální, přibližné a navigační navigace pro všechny F# konstrukce prostřednictvím **CTRL**+**T**.|Ano|
|Přejmenování na řádku|Přejmenuje všechny výskyty vloženého symbolu.|Ano|
|Najít všechny odkazy|Vyhledá všechny výskyty symbolu v základu kódu.|Ano|
|Zjednodušení opravy názvu kódu|Odebere nepotřebné kvalifikátory F# pro symboly.|Ano|
|Odebrat opravu `open` nepoužívaného kódu příkazu|Odebere všechny nepotřebné `open` příkazy v dokumentu.|Ano|
|Oprava kódu nepoužité hodnoty|Navrhuje přejmenovat nepoužitý identifikátor na podtržítko.|Ano|

Obecné informace o úpravách kódu v aplikaci Visual Studio a funkcích textového editoru naleznete [v tématu Write code in the Editor](writing-code-in-the-code-and-text-editor.md).

## <a name="intellisense-features"></a>Funkce IntelliSense

Následující tabulka shrnuje podporované funkce IntelliSense a nepodporuje je F#:

|Funkce|Popis|Podporuje se F#v?|
|-------|-----------|----------------|
|Automaticky implementovat rozhraní|Generuje zástupné kódy kódu pro metody rozhraní.|Ano|
|Fragmenty kódu|Vloží kód z knihovny běžných kódových konstrukcí do témat.|Ne|
|Dokončit slovo|Ukládá text tak, že při psaní dokončí slova a jména.|Ano|
|Automatické dokončování|Když je tato možnost povolená, způsobí, že při psaní se při psaní slova vybere první shoda, a ne čekání na výběr jednoho nebo**více kláves** **CTRL**+.|Ano|
|Nabídka dokončování symbolů v neotevřených oborech názvů|Při automatickém dokončení je navržen odpovídající symbol, který je umístěn v neotevřeném oboru názvů, nabídka k dokončení s odpovídajícím `open` příkazem, pokud je vybrána možnost.|Ano|
|Generovat elementy kódu|Umožňuje generovat kód zástupné procedury pro nejrůznější konstrukce.|Ne|
|Vypsat členy|Když zadáte operátor přístupu ke členu (.), zobrazí se členové pro typ.|Ano|
|Uspořádat pomocí/otevřít|Uspořádá obory názvů odkazované příkazy **pomocí** příkazů C# nebo direktiv **Open** v F#.|Ne|
|Informace o parametrech|Zobrazuje užitečné informace o parametrech při psaní volání funkce.|Ano|
|Rychlé informace|Zobrazí úplnou deklaraci pro libovolný identifikátor ve vašem kódu.|Ano|
|Automatické dokončování složených závorek|Automaticky dokončuje F# konstruktory syntaxe podobné závorce transakčním způsobem.|Ano|

Obecné informace o technologii IntelliSense najdete v tématu [použití technologie IntelliSense](using-intellisense.md).

## <a name="debugging-features"></a>Funkce ladění

Následující tabulka shrnuje funkce, které jsou k dispozici při ladění F# kódu:

|Funkce|Popis|Podporuje se F#v?|
|-------|-----------|----------------|
|Automatické hodnoty – okno|Zobrazuje automatické nebo dočasné proměnné.|Ne|
|Zarážky|Umožňuje pozastavit provádění kódu v určitých okamžicích během ladění.|Ano|
|Podmíněné zarážky|Povoluje zarážky, které testují podmínku, která určuje, zda se má spuštění pozastavit.|Ano|
|Upravit a pokračovat|Umožňuje upravovat a kompilovat kód při ladění spuštěného programu bez zastavení a restartování ladicího programu.|Ne|
|Vyhodnocení výrazu|Vyhodnotí a spustí kód v době běhu.|Ne, můžete však C# použít vyhodnocovací filtr výrazů, i když je nutné použít C# syntaxi.|
|Historické ladění|Umožňuje Krokovat s dřív provedeným kódem.|Ano|
|Místní hodnoty – okno|Zobrazuje místně definované hodnoty a proměnné.|Ano|
|Spustit ke kurzoru|Umožňuje spustit kód až do chvíle, kdy je dosaženo řádku obsahujícího kurzor.|Ano|
|Krokovat s vnořením|Umožňuje pokračovat v provádění a přesun do libovolného volání funkce.|Ano|
|Krok přes|Umožňuje provést předběžné spuštění v aktuálním bloku zásobníku a přesunout minulé volání funkce.|Ano|

Obecné informace o ladicím programu sady Visual Studio naleznete [v tématu ladění v aplikaci Visual Studio](../debugger/index.yml).

## <a name="additional-tools"></a>Další nástroje

Následující tabulka shrnuje podporu nástroje F# v nástrojích sady Visual Studio.

|Nástroj|Popis|Podporuje se F#v?|
|----|-----------|----------------|
|Hierarchie volání|Zobrazuje vnořenou strukturu volání funkce ve vašem kódu.|Ne|
|Metriky kódu|Shromažďuje informace o kódu, například počty řádků.|Ne|
|zobrazení tříd|Poskytuje zobrazení kódu v projektu podle typu.|Ne|
|[Seznam chyb okno](reference/error-list-window.md)|Zobrazuje seznam chyb v kódu.|Ano|
|[F# Interactive](/dotnet/fsharp/tutorials/fsharp-interactive/)|Umožňuje napsat (nebo zkopírovat a vložit) F# kód a okamžitě ho spustit, nezávisle na sestavování projektu. F# Interaktivní okno je čtení, vyhodnocení, tisková smyčka (REPL).|Ano|
|prohlížeč objektů|Umožňuje zobrazit typy v sestavení.|F#typy, které se zobrazují v kompilovaných sestaveních, se neobjeví přesně tak, jak je vytváříte. Můžete procházet zkompilované reprezentace F# typů, ale nemůžete zobrazit typy, jak jsou uvedeny v. F#|
|[Okno výstup](reference/output-window.md)|Zobrazí výstup sestavení.|Ano|
|Analýza výkonu|Poskytuje nástroje pro měření výkonu kódu.|Ano|
|Vlastnosti – okno|Zobrazí a povolí úpravy vlastností objektu ve vývojovém prostředí, které má fokus.|Ano|
|Průzkumník serveru|Poskytuje možnosti pro interakci s nejrůznějšími prostředky serveru.|Ano|
|Průzkumník řešení|Umožňuje zobrazit a spravovat projekty a soubory.|Ano|
|Seznam úkolů|Umožňuje spravovat pracovní položky, které se vztahují k vašemu kódu.|Ne|
|Projekty testů|Poskytuje funkce, které vám pomůžou otestovat váš kód.|Ne|
|Sada nástrojů|Zobrazí karty, které obsahují přetažené objekty, jako jsou například ovládací prvky a oddíly textu nebo kódu.|Ano|

## <a name="see-also"></a>Viz také:

- [F#Průvodce (.NET Framework)](/dotnet/fsharp/)
- [Začínáme s nástrojem F# v aplikaci Visual Studio](/dotnet/fsharp/get-started/get-started-visual-studio)