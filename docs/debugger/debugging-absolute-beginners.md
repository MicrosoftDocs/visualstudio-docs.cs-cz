---
title: Ladění kódu pro naprosté začátečníky
description: Pokud ladíte poprvé, přečtěte si několik zásad pro pomoc při spouštění vaší aplikace v režimu ladění pomocí sady Visual Studio
ms.custom: ''
ms.date: 07/06/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31b6812ec41aedd4e33eb0d043476365d3938767
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53160020"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Ladění pro naprosté začátečníky

Bez selžou kód, který jsme napsali jako vývojáři softwaru vždy neumí, co očekávali jsme na práci. Někdy se něco úplně jiného. Pokud k tomu dojde, dalším krokem je zjistit, proč a i když budeme mít tendenci získat jenom zachovat rovnou začít na náš kód pro hodiny, je mnohem jednodušší a efektivnější použijte ladicí nástroj a ladicího programu.

Ladicí program se bohužel něco, co může kouzelného odhalit všechny problémy nebo "chyby" v našem kódu. *Ladění* způsob, jak spustit kód krok za krokem v ladicí nástroj, jako je Visual Studio vyhledat přesný okamžik, kde jste udělali programování. Potom pochopit, jaké opravy, budete muset udělat ve vašem kódu a ladicí nástroje často bylo možné provést dočasné změny, takže můžete pokračovat v provádění programu.

Efektivní použití ladicího programu je také dovednost, která přebírá čas a cvičení se dozvíte, ale v konečném důsledku je základní úlohy pro každý softwarový vývojář. V tomto článku se potom jsme zavést základními principy ladění a poskytuje tipy vám pomůžou začít.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Zpřehlednit problém tím, že sami klást ty pravé otázky

Pomáhá vysvětlení problému, který jste narazili před pokusem o jeho řešení. Očekáváme, že jste už narazili na problém ve vašem kódu, jinak by se tady snažíte zjistit, jak ho ladit! Ano před zahájením ladění, ujistěte se, že identifikujete problém, který se snažíte vyřešit:

* Co očekáváte, že váš kód provést?

* Co se stalo místo?

    Pokud narazili na chybu (výjimek) při spouštění vaší aplikace, která může být dobrá věc! Výjimkou je při spuštění kódu, obvykle chybu určitého druhu došlo k neočekávané události. Ladicí nástroj může trvat přesné místo v kódu, ve kterém k výjimce došlo a můžete pomáhají s prošetřením možné opravy.

    Pokud se něco stalo, co je tento problém projevuje? Máte už podezření kde došlo k tomuto problému v kódu? Například pokud váš kód zobrazí text, ale text je nesprávná, víte, že vaše data jsou chybné nebo kód, který nastavení textu zobrazovaného má nějaký druh chyby. Krokování kódem v ladicí program, můžete zkontrolovat každého změn do proměnných ke zjištění přesně, kdy a jak jsou přiřazeny nesprávné hodnoty.

## <a name="examine-your-assumptions"></a>Prozkoumejte předpokladů

Předtím, než byste prozkoumat chybu nebo chybu, si můžete Představte předpokladů, které můžete očekávat, že některé výsledek provedli. Skrytý nebo Neznámý předpoklady mohou bránit identifikace problému i v případě, že chcete přímo na příčinu problému ve ladicího programu. Může být dlouhý seznam možných předpoklady! Tady je pár otázek se ptát na ověřovací předpokladů.

* Používáte správné rozhraní API (to znamená, správný objekt, funkce, metoda nebo vlastnost)? Rozhraní API, které používáte nebudete dělat, co si myslíte, že dělá. (Po kontrole volání rozhraní API v ladicím programu, její opravu může vyžadovat postoupí do dokumentace vám pomůže identifikovat správné rozhraní API.)

* Používáte rozhraní API správně? Možná používá vpravo rozhraní API, ale neměli používat v správným způsobem.

* Obsahuje kód jakékoli překlepy? Některé překlepy, jako jsou jednoduché jistá pravopisnou chybou názvu proměnné může být obtížné zjistit, zejména při práci s jazyky, které nevyžadují proměnné deklarovat před jejich použití.

* Provést změnu kódu a Předpokládejme, že je nemá vztah k problému, který se vám zobrazuje?

* Nebyla očekáváte, že objekt nebo proměnnou, která obsahují určitou hodnotou (nebo typu hodnoty), který není totéž co se skutečně stalo?

* Víte, záměru kódu? Často je obtížné ladit někdo v kódu. Pokud není kód, je možné, že možná budete muset ztrácet čas zjišťováním informací přesně co kód dělá předtím, než ho můžete efektivně ladit.

    > [!TIP]
    > Při psaní kódu, začněte v malém a spustit s kódem, který funguje! (Dobrý vzorek kódu je užitečné zde.) V některých případech je snazší opravit velký nebo komplikovaný sadu kód začněte s malou část kódu, který ukazuje základní úkol, který se snažíte dosáhnout. Potom můžete upravit nebo přidejte kód postupně testování u každého bodu chyby.

Pomocí označování předpokladů, můžete snížit čas potřebný k vyhledání problém ve vašem kódu. Může také snížit čas potřebný k vyřešení problému.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Procházet kódem v režimu najít, kde došlo k problému ladění

Když normálně spustí aplikaci, se zobrazí chyby a nesprávné výsledky pouze po spuštění kódu. Program může být také dojde k neočekávanému ukončení bez odůvodněním.

Spuštění aplikace v rámci ladicího programu, také nazývané *režim ladění*, znamená to, že ladicí program aktivně sleduje vše, co se děje jako program se spustí. Také umožňuje pozastavení aplikace kdykoli zkontrolovat jeho stav a poté krokovat kód řádek po řádku a sledujte všechny podrobnosti o jejím průběhu.

V sadě Visual Studio, zadejte režim ladění pomocí **F5** (nebo **ladění** > **spustit ladění** příkaz nabídky nebo **spustit ladění**  tlačítko ![spustit ladění](../debugger/media/dbg-tour-start-debugging.png "spustit ladění") v panelu nástrojů ladění). Pokud dojde k jakékoli výjimky, pomocníka výjimky v sadě Visual Studio přejde na přesný okamžik, kdy výjimky došlo k a poskytuje další užitečné informace.

Pokud jste nedostali výjimku, je pravděpodobně vhodné, kde hledat problému v kódu. To kdy používat *zarážky* pomocí ladicího programu, abyste měli příležitost dobře se více pečlivě prozkoumat kód. Zarážky jsou základní a nejjednodušší funkcí spolehlivého ladění. Zarážky označuje, kde by měl Visual Studio pozastavit spuštěním kódu, se můžete podívat na hodnoty proměnných, nebo chování paměti nebo pořadí, ve kterém kód běží.

V sadě Visual Studio můžete rychle nastavit zarážku kliknutím na levém okraji vedle řádku kódu. Nebo umístěte kurzor na řádku a stisknutím klávesy **F9**.

Pro lepší tyto koncepty, budeme vás provedou některé ukázkový kód, který už má několik chyb. Používáme C#, ale funkce ladění platí pro Visual Basic, C++, JavaScript, Python a ostatní podporované jazyky.

### <a name="create-a-sample-app-with-some-bugs"></a>Vytvořte ukázkovou aplikaci (s některé chyby)

V dalším kroku vytvoříme aplikaci, která má několik chyb.

1. Musíte mít nainstalovanou sadu Visual Studio a buď **vývoj desktopových aplikací .NET** úlohy nebo **.NET Core pro vývoj napříč platformami** nainstalovaná úloha, v závislosti na typu aplikace, které chcete vytvořit.

    Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stránku a nainstalovat zdarma.

    Pokud je potřeba, nainstalujte úlohu, ale už máte sadu Visual Studio, klikněte na tlačítko **nástroje** > **stažení nástrojů a funkcí**. Spustí se instalační program pro Visual Studio. Zvolte **vývoj desktopových aplikací .NET** (nebo **.NET Core pro vývoj napříč platformami**) úloh, klikněte na tlačítko **změnit**.

1. Otevřít Visual Studio a klikněte na tlačítko **souboru** > **nový** > **projektu**.

1. Vyberte šablonu pro kód aplikace.

    Pro rozhraní .NET Framework v **nový projekt** dialogového okna zvolte **Visual C#**, **Windows Desktop** z části nainstalovaných šablon a potom v prostředním podokně vyberte  **Aplikace konzoly (.NET Framework)**.

    Pro .NET Core v **nový projekt** dialogového okna zvolte **Visual C#**, **.NET Core** z části nainstalovaných šablon a potom v prostředním podokně vyberte  **Aplikace (.NET Core) konzoly**.

    Pokud nevidíte tyto šablony, je nutné nainstalovat příslušnou úlohu (viz předchozí kroky).

1. V **název** zadejte **ConsoleApp FirstApp** a klikněte na tlačítko **OK**.

    Visual Studio vytvoří projekt konzoly, která se zobrazí v Průzkumníku řešení v pravém podokně.

1. V *Program.cs*, nahraďte výchozí kód následujícím kódem:

    ```csharp
    using System;
    using System.Collections.Generic;
    
    namespace ConsoleApp_FirstApp
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Welcome to Galaxy News!");
                IterateThroughList();
                Console.ReadKey();
            }
    
            private static void IterateThroughList()
            {
                var theGalaxies = new List<Galaxy>
            {
                new Galaxy() { Name="Tadpole", MegaLightYears=400, GalaxyType=new GType('S')},
                new Galaxy() { Name="Pinwheel", MegaLightYears=25, GalaxyType=new GType('S')},
                new Galaxy() { Name="Cartwheel", MegaLightYears=500, GalaxyType=new GType('L')},
                new Galaxy() { Name="Small Magellanic Cloud", MegaLightYears=.2, GalaxyType=new GType('I')},
                new Galaxy() { Name="Andromeda", MegaLightYears=3, GalaxyType=new GType('S')},
                new Galaxy() { Name="Maffei 1", MegaLightYears=11, GalaxyType=new GType('E')}
            };
    
                foreach (Galaxy theGalaxy in theGalaxies)
                {
                    Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
                }
    
                // Expected Output:  
                //  Tadpole  400,  Spiral 
                //  Pinwheel  25,  Spiral 
                //  Cartwheel, 500,  Lenticular
                //  Small Magellanic Cloud .2,  Irregular
                //  Andromeda  3,  Spiral
                //  Maffei 1,  11,  Elliptical
            }
        }
    
        public class Galaxy
        {
            public string Name { get; set; }
    
            public double MegaLightYears { get; set; }
            public object GalaxyType { get; set; }
    
        }
    
        public class GType
        { 
            public GType(char type)
            {
                switch(type)
                {
                    case 'S':
                        MyGType = Type.Spiral;
                        break;
                    case 'E':
                        MyGType = Type.Elliptical;
                        break;
                    case 'l':
                        MyGType = Type.Irregular;
                        break;
                    case 'L':
                        MyGType = Type.Lenticular;
                        break;
                    default:
                        break;
                }
            }
            public object MyGType { get; set; }
            private enum Type { Spiral, Elliptical, Irregular, Lenticular}
        }
    }
    ```

    Naším záměrem pro tento kód je zobrazované jméno galaxy, vzdálenost galaxy a typ galaxy všechno v seznamu. Chcete-li ladit, je důležité k porozumění záměru kódu. Tady je formát pro jeden řádek ze seznamu, který má být zobrazena ve výstupu:

    *Název Galaxy*, *vzdálenost*, *galaxy typ*.

### <a name="run-the-app"></a>Spuštění aplikace

1. Stisknutím klávesy **F5** nebo **spustit ladění** tlačítko ![spustit ladění](../debugger/media/dbg-tour-start-debugging.png "spustit ladění") na panelu nástrojů ladění umístěné nad editoru kódu.

    Aplikace se spustí a neexistují žádné výjimky uvedené nám ladicím programem. Výstupem, který se zobrazí v okně konzoly je však nesplňuje vaše očekávání. Tady je očekávaný výstup:

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Ale to uvidíme místo:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType 
    Pinwheel  25,  ConsoleApp_FirstApp.GType 
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Hledání v výstup a náš kód, víme, že `GType` je název třídy, která ukládá galaxy typu. Můžeme se pokoušíte zobrazit galaxy skutečný typ (například "něco jako Spirála"), ne název třídy!

### <a name="debug-the-app"></a>Ladění aplikace

1. Pomocí aplikace pořád běží, nastavte zarážku kliknutím do levého okraje vedle možnosti `Console.WriteLine` volání metody v tomto řádku kódu.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }    
    ```

    Pokud nastavíte zarážku, zobrazí se červená tečka na levém okraji.

    Protože vidíme problém ve výstupu, začneme ladění pohledem na předchozí kód, který nastaví výstup v ladicím programu.

1. Klikněte na tlačítko **restartovat** ![restartovat aplikaci](../debugger/media/dbg-tour-restart.png "RestartApp") tlačítko na panelu nástrojů ladění (**Ctrl** + **Shift**   +  **F5**).

    Aplikace pozastavení na zarážce, kterou jste nastavili. Žluté zvýraznění označuje, kde je pozastavena ladicím programu (žlutá čára kód ještě neprovedlo).

1. Najeďte myší `GalaxyType` rozbalit proměnnou na pravé straně a pak na levé straně na ikonu klíče `theGalaxy.GalaxyType`. Uvidíte, že `GalaxyType` obsahuje vlastnost `MyGType`, a hodnota vlastnosti je nastavená na `Spiral`.

    ![Kontrolovat proměnné](../debugger/media/beginners-inspect-variable.png)

    "Něco jako Spirála" je ve skutečnosti správnou hodnotu, kterou jste čekali vypíše do konzoly. To je dobrý začátek, dostanete tuto hodnotu v tomto kódu při spuštění aplikace. V tomto scénáři se používá nesprávný rozhraní API. Uvidíme, pokud nám to vyřešit při spouštění kódu v ladicím programu.

1. Ve stejném kódu během ladění stále, umístěte kurzor na konci `theGalaxy.GalaxyType` a změňte ho na `theGalaxy.GalaxyType.MyGType`. I když provedete tuto změnu, editor kódu ukazuje, chyba s upozorněním, že tento kód nelze zkompilovat.

    ![Chyba syntaxe](../debugger/media/beginners-edit.png)

1. Klikněte na tlačítko **upravit** v **upravit a pokračovat** okno se zprávou. Zobrazí chybovou zprávu nyní ve **seznam chyb** okna. Chyba udává, `'object'` neobsahuje definici pro `MyGType`.

    ![Chyba syntaxe](../debugger/media/beginners-no-definition.png)

    I když jsme si nastavili každý galaxy s objektem typu `GType` (který má `MyGType` vlastnost), ladicí program nemůže rozpoznat `theGalaxy` objekt jako objekt typu `GType`. Co se děje? Budete chtít projít veškerý kód, který nastaví typ galaxy. Když toto provedete, uvidíte, že `GType` třídy jednoznačně má vlastnost `MyGType`, ale něco není správný. Chybová zpráva týkající se `object` naznačuje; se ukázalo k interpretu jazyk zdá být objekt typu typ `object` místo objektu typu `GType`.

1. Procházení kódu související s galaxy typ nastavení, najdete `GalaxyType` vlastnost `Galaxy` třída zadaná jako `object` místo `GType`.

    ```csharp
    public object GalaxyType { get; set; }     
    ```

1. Změna předcházející kód:

    ```csharp
    public GType GalaxyType { get; set; }     
    ```

1. Klikněte na tlačítko **restartovat** ![restartovat aplikaci](../debugger/media/dbg-tour-restart.png "RestartApp") tlačítko na panelu nástrojů ladění (**Ctrl** + **Shift**   +  **F5**) znovu zkompilovat kód a znovu spusťte.

    Teď, když ladicí program pozastaví na `Console.WriteLine`, najedete myší `theGalaxy.GalaxyType.MyGType`a, že je hodnota nastavena správně.

1. Odebrat zarážku kliknutím na kruh zarážku na levém okraji (nebo klikněte pravým tlačítkem a zvolte **zarážku** > **odstranění zarážky**) a potom stiskněte klávesu **F5** pokračujte.

    Aplikace se spustí a zobrazí výstup. Vypadá to docela kvalitní nyní, ale Všimněte si jednu věc; očekáváte malé Magellanic cloudu galaxy zobrazí jako nestandardní galaxy ve výstupu konzoly, ale žádný typ galaxy vůbec zobrazí.

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. Nastavení zarážky na tento řádek kódu.

    ```csharp
    public GType(char type)
    ```

    Tento kód je, kde je typ galaxy nastaven, tak, že chceme, aby se na ně podívat.

1. Klikněte na tlačítko **restartovat** ![restartovat aplikaci](../debugger/media/dbg-tour-restart.png "RestartApp") tlačítko na panelu nástrojů ladění (**Ctrl** + **Shift**   +  **F5**) k restartování.

    Ladicí program pozastaví na řádek kódu, kde nastavit zarážku.  

1. Najeďte myší `type` proměnné. Zobrazí hodnotu `S` (následující kód znaku). Máte zájem hodnotu `I`, protože víte, který je nestandardní galaxy typu.

1. Stisknutím klávesy **F5** a najeďte myší `type` proměnné znovu. Tento krok opakujte, dokud se nezobrazí hodnota `I` v `type` proměnné.

    ![Kontrolovat proměnné](../debugger/media/beginners-inspecting-data.png)

1. Nyní, stiskněte klávesu **F11** (**ladění** > **Krokovat s vnořením** nebo **Krokovat s vnořením** tlačítko na panelu nástrojů ladění).

    **F11** přejde ladicí program (a spustí kód) jeden příkaz v čase. **F10** (**Krokovat s přeskočením**) je podobná příkazu a oba jsou velmi užitečné při studiu používání ladicího programu.

1. Stisknutím klávesy **F11** až po ukončení na řádek kódu `switch` příkazem pro hodnotu "I". Tady vidíte vymazat problém výsledkem překlep. Byl očekáván kód pro přechod na kde nastaví `MyGType` jako nepravidelné galaxy typu, ale ladicí program místo zcela vynechat tento kód a pozastaví na `default` část `switch` příkazu.

    ![Najít překlep](../debugger/media/beginners-typo.png)

    Vyhledávání v kódu, uvidíte překlep v `case 'l'` příkazu. Měla by být `case 'I'`.

1. Klikněte na tlačítko v kódu pro `case 'l'` a nahraďte ho hodnotou `case 'I'`.

1. Odebrat zarážku a poté klikněte na tlačítko **restartovat** tlačítko k restartování aplikace.

    Nyní opravě chyby a zobrazí se výstup očekáváte, že!

    Stisknutím jakékoli klávesy dokončete aplikaci.

## <a name="summary"></a>Souhrn

Až se problém, použijte ladicí program a [krok příkazy](../debugger/navigating-through-code-with-the-debugger.md) například **F10** a **F11** se najít oblast s problémem, který kód.

> [!NOTE]
> Pokud je obtížné určit oblasti kódu, kde k problému dochází, nastavte zarážku v kódu, který se spustí před výskytem problému a pak používat krokových příkazů, dokud se zobrazí problém manifestu. Můžete také použít [zarážky s trasováním](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) k protokolování zprávy **výstup** okna. Tím, že prohlížení zprávy zaznamenané dříve (a řadí zprávy, které ještě nebyly zaznamenány!), můžete izolovat oblasti kódu s problémem, který často. Budete muset tento proces opakovat několikrát omezit.

Když najdete oblasti kódu s problémem, který pomocí ladicího programu k prozkoumání. Chcete-li zjistit příčinu problému, zkontrolujte kód problému při spuštění aplikace v ladicím programu:

* [Kontrolovat proměnné](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) a zkontrolujte, zda neobsahují typu hodnoty, které by měl obsahovat. Pokud zjistíte chybná hodnota, zjistěte, ve kterém byla nastavena chybná hodnota (najít, kde byla nastavena hodnotu, může být nutné restartovat ladicí program, podívejte se na [zásobníku volání](../debugger/how-to-use-the-call-stack-window.md), nebo obojí).

* Zkontrolujte, jestli vaše aplikace spouští kód, který očekáváte. (Například v ukázkové aplikaci očekávali jsme kód pro příkaz switch postup nastavení typu galaxy nestandardní, ale aplikace přeskočeno kódu z důvodu překlep.)

> [!TIP]
> Pomocí ladicího programu můžete najít chyby. Ladicí nástroj pomůže hledat chyby *za vás* pouze v případě, že zná záměru kódu. Nástroj lze pouze vědět záměru kódu, pokud vás jako na vývojáři express tohoto záměru. Zápis [testování částí](../test/improve-code-quality.md) je, jak to udělat. 

## <a name="next-steps"></a>Další kroky

V tomto článku jste se seznámili s několika koncepty obecné ladění. V dalším kroku můžete začít dostávat další informace o ladicím programu.

> [!div class="nextstepaction"]
> [Další informace k ladění pomocí sady Visual Studio](../debugger/getting-started-with-the-debugger.md)
