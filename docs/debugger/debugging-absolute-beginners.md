---
title: Ladění kódu pro absolutní začátečníky
description: Pokud ladíte poprvé, Projděte si několik principů, které vám pomohou spustit aplikaci v režimu ladění se sadou Visual Studio.
ms.date: 02/14/2020
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6202fa019aed8e6fc9eb9ff93bdb390bf22f2911
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761248"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Postup ladění pro absolutní začátečníky

Aniž by došlo k chybě, kód, který zapisujeme jako vývojáři softwaru, neprovádí vždy to, co očekáváme. V některých případech se něco úplně liší! Pokud k tomu dojde, další krok úkolu je zjistit, proč a i když můžeme zvážit, že se vám v našem kódu bude zobrazovat jenom hodiny, je mnohem jednodušší a efektivní použít ladicí nástroj nebo ladicí program.

Ladicí program, bohužel není něco, co může v našem kódu zobrazit všechny problémy nebo "chyby". Způsob *ladění* pro spuštění kódu krok za krokem v ladicím nástroji, jako je Visual Studio, k nalezení přesného bodu, ve kterém jste provedli programové chyby. Pak pochopíte, jaké opravy potřebujete ve svém kódu, a nástroje pro ladění často umožňují provádět dočasné změny, abyste mohli pokračovat v používání programu.

Použití ladicího programu je efektivně také dovedností, která se učí, ale je nakonec zásadní úlohou pro každého vývojáře softwaru. V tomto článku zavádíme základní principy ladění a poskytneme vám tipy, jak začít.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Vyjasnění problému tím, že si sami požádáte o správné otázky

Pomůže vám objasnit problém, ke kterému jste narazili předtím, než se pokusíte ho opravit. Očekáváme, že už jste narazili na problém ve vašem kódu, jinak jste se nepokoušeli zjistit, jak si ho můžete ladit. Než začnete s laděním, ujistěte se, že jste identifikovali problém, který se snažíte vyřešit:

* Co jste očekávali, že váš kód má dělat?

* Co se stalo?

    Pokud jste při spuštění aplikace narazili na chybu (výjimku), může to být dobré! Výjimkou je neočekávaná událost při spuštění kódu, obvykle došlo k chybě nějakého druhu. Ladicí nástroj vás může přesměrovat na přesné místo v kódu, kde došlo k výjimce, a může vám pomohli prozkoumat možné opravy.

    Pokud došlo k nějakému problému, jaký je příznakem problému? Už máte podezření, že k tomuto problému došlo ve vašem kódu? Například pokud váš kód zobrazuje nějaký text, ale text není správný, víte, že data jsou chybná, nebo kód, který zobrazuje zobrazovaný text, má nějaký druh chyby. Procházením kódu v ladicím programu můžete prozkoumat každou a každou změnu proměnných, abyste zjistili přesně, kdy a jak jsou přiřazeny nesprávné hodnoty.

## <a name="examine-your-assumptions"></a>Kontrola předpokladů

Před vyšetřením chyby nebo chyby si představte předpoklady, které jste očekávali, že jste očekávali určitý výsledek. Skryté nebo neznámé předpoklady můžou získat způsob, jak identifikovat problém, i když se díváte na příčinu problému v ladicím programu. Je možné, že máte dlouhý seznam možných předpokladů. Tady je pár otázek, které vás požádají, abyste mohli své předpoklady vyzvat.

* Používáte správné rozhraní API (tj. správný objekt, funkce, metoda nebo vlastnost)? Rozhraní API, které používáte, nemusí mít za to, co si myslíte. (Po kontrole volání rozhraní API v ladicím programu může být nutné, aby při opravě pro identifikaci správného rozhraní API vyžadovala cestu k dokumentaci.)

* Používáte rozhraní API správně? Možná jste používali správné rozhraní API, ale nepoužili jste správný způsob.

* Obsahuje váš kód překlepy? Některá překlepy, jako je jednoduché chybné zadání názvu proměnné, mohou být obtížné zobrazit, zejména při práci s jazyky, které nevyžadují, aby byly před použitím deklarovány proměnné.

* Provedli jste změnu kódu a předpokládali, že nesouvisí s problémem, který vidíte?

* Očekávali jste, že objekt nebo proměnná obsahují určitou hodnotu (nebo určitý typ hodnoty), která se liší od toho, co se skutečně stalo?

* Znáte záměr kódu? Je často obtížnější ladit kód jiné osoby. Pokud se nejedná o váš kód, je možné, že budete muset věnovat čas učení přesně s tím, jak kód ještě před tím, než ho budete moct efektivně ladit.

    > [!TIP]
    > Při psaní kódu, začněte s malým a začněte kódem, který funguje! (Dobrý vzorový kód je tady užitečný.) V některých případech je snazší opravit velkou nebo složitou sadu kódu, a to od malého kódu, který předvádí základní úlohu, kterou se snažíte dosáhnout. Pak můžete kód přírůstkově upravovat nebo přidávat, testování v každém místě pro chyby.

Podle otázek vašich předpokladů můžete zkrátit dobu potřebnou k nalezení problému v kódu. Můžete také zkrátit dobu potřebnou k vyřešení problému.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Projděte si kód v režimu ladění, abyste zjistili, kde došlo k problému.

Při normálním spuštění aplikace se zobrazí chyby a nesprávné výsledky až po spuštění kódu. Program může také skončit neočekávaně, aniž by vám to řekne.

Spuštění aplikace v rámci ladicího programu, označovaného také jako *režim ladění*, znamená, že ladicí program aktivně monitoruje všechno, co se děje při spuštění programu. Umožňuje také pozastavit aplikaci v jakémkoli bodě, abyste prozkoumali její stav a pak procházeli řádky kódu podle řádku, aby se sledovaly všechny podrobnosti, jak se to stane.

V sadě Visual Studio zadáte režim ladění pomocí **F5** (nebo tlačítko spustit **ladění spustit ladění**  >   na panelu nástrojů ladění  ). ![](../debugger/media/dbg-tour-start-debugging.png "Spustit ladění") Pokud dojde k nějakým výjimkám, Pomocník s výjimkami sady Visual Studio vás přesměruje přesně na místo, kde k výjimce došlo, a poskytuje další užitečné informace. Další informace o tom, jak zpracovávat výjimky v kódu, naleznete v tématu [techniky a nástroje ladění](../debugger/write-better-code-with-visual-studio.md).

Pokud jste neobdrželi výjimku, pravděpodobně máte dobrý nápad, kde můžete vyhledat problém ve vašem kódu. Zde je místo, kde pomocí ladicího programu použijete *zarážky* k tomu, abyste si mohli posuzovat kód pečlivě. Zarážky jsou základní a nejjednodušší funkcí spolehlivého ladění. Zarážka označuje, kde by měla aplikace Visual Studio pozastavit běžící kód, abyste se mohli podívat na hodnoty proměnných nebo chování paměti nebo pořadí, ve kterém kód běží.

V sadě Visual Studio můžete rychle nastavit zarážku kliknutím na levý okraj vedle řádku kódu. Nebo umístěte kurzor na čáru a stiskněte klávesu **F9**.

Abychom vám pomohli objasnění těchto konceptů, provedeme si nějaký ukázkový kód, který už obsahuje několik chyb. Používáme jazyk C#, ale funkce ladění se vztahují na Visual Basic, C++, JavaScript, Python a další podporované jazyky.

### <a name="create-a-sample-app-with-some-bugs"></a>Vytvoření ukázkové aplikace (s některými chybami)

V dalším kroku vytvoříme aplikaci, která bude mít několik chyb.

1. V závislosti na typu aplikace, který chcete vytvořit, musíte mít nainstalovanou aplikaci Visual Studio a nainstalovanou úlohu **vývoj desktopových** aplikací pro .NET nebo **.NET Core pro vývoj pro různé platformy** .

    Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) a nainstalujte si ji zdarma.

    Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, klikněte na **nástroje**  >  **získat nástroje a funkce**. Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoj pro desktopové prostředí .NET** (nebo **.NET Core pro vývoj pro různé platformy**) a pak zvolte **změnit**.

1. Otevřete sadu Visual Studio.

    ::: moniker range=">=vs-2019"
    V okně Start vyberte možnost **vytvořit nový projekt**. Do vyhledávacího pole zadejte **Console** a pak zvolte buď **Konzolová aplikace (.NET Core)** , nebo **aplikace konzoly (.NET Framework)**. Zvolte **Další**. Zadejte název projektu, například **ConsoleApp-FirstApp** , a klikněte na **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt**. V levém podokně dialogového okna **Nový projekt** , v části **Visual C#** zvolte **Konzolová aplikace** a pak v prostředním podokně zvolte buď **Konzolová aplikace (.NET Framework)** nebo **aplikace konzoly (.NET Core)**. Zadejte název jako **ConsoleApp-FirstApp** a klikněte na **OK**.
    ::: moniker-end

    Pokud nevidíte šablonu projektu **Konzolová aplikace (.NET Framework)** nebo **Konzolová aplikace (.NET Core)** , přejděte do části **nástroje**  >  **získat nástroje a funkce**, které otevřou instalační program pro Visual Studio. Zvolte buď možnost **vývoj pro různé platformy .NET Core** , nebo **desktopový vývoj** pro platformu .NET a pak zvolte možnost **Upravit**.

    Visual Studio vytvoří projekt konzoly, který se zobrazí v Průzkumník řešení v pravém podokně.

1. V *program.cs* nahraďte veškerý výchozí kód následujícím kódem:

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

    Naším záměrem tohoto kódu je zobrazit název Galaxy, vzdálenost k Galaxy a typ Galaxy vše v seznamu. Pro ladění je důležité pochopit záměr kódu. Tady je formát jednoho řádku ze seznamu, který chceme zobrazit ve výstupu:

    *Galaxy název*, *vzdálenost*, *typ Galaxy*.

### <a name="run-the-app"></a>Spuštění aplikace

1. Stiskněte klávesu **F5** nebo tlačítko **Spustit ladění** ![Spustit ladění](../debugger/media/dbg-tour-start-debugging.png "Spustit ladění") na panelu nástrojů ladění, které se nachází nad editorem kódu.

    Aplikace se spustí a ladicí program nezobrazuje žádné výjimky. Výstup zobrazený v okně konzoly ale není to, co očekáváte. Tady je očekávaný výstup:

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Ale zobrazuje se místo toho:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType
    Pinwheel  25,  ConsoleApp_FirstApp.GType
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Při prohlížení výstupu a v našem kódu víme, že `GType` je název třídy, která ukládá typ Galaxy. Snažíme se zobrazit skutečný typ Galaxy (například "spirála"), ne název třídy!

### <a name="debug-the-app"></a>Ladění aplikace

1. V případě, že je aplikace stále spuštěná, nastavte zarážku kliknutím na levý okraj vedle `Console.WriteLine` volání metody v tomto řádku kódu.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }
    ```

    Při nastavení zarážky se na levém okraji zobrazí červená tečka.

    Vzhledem k tomu, že se ve výstupu zobrazuje problém, začneme ladit tím, že si vyhledáme předchozí kód, který nastaví výstup v ladicím programu.

1. Klikněte na tlačítko **restartovat** ![aplikaci](../debugger/media/dbg-tour-restart.png "RestartApp") na panelu nástrojů ladění (**CTRL**  +  **SHIFT**  +  **F5**).

    Aplikace se pozastaví na zarážce, kterou jste nastavili. Žluté zvýraznění indikuje, kde je ladicí program pozastaven (žlutá čára kódu ještě neproběhla).

1. Najeďte myší na `GalaxyType` proměnnou vpravo a pak na levou stranu ikony klíče rozbalte `theGalaxy.GalaxyType` . Uvidíte, že `GalaxyType` obsahuje vlastnost `MyGType` a hodnota vlastnosti je nastavena na `Spiral` .

    ![Snímek obrazovky ladicího programu sady Visual Studio s řádkem kódu žlutou a rozbalenou nabídkou pod vlastností theGalaxy. GalaxyType na konci řádku](../debugger/media/beginners-inspect-variable.png)

    "Spirála" je ve skutečnosti správná hodnota, kterou jste čekali v tisku do konzoly. Proto je dobré začít mít k této hodnotě v tomto kódu přístup při spuštění aplikace. V tomto scénáři používáme nesprávné rozhraní API. Uvidíme, že to můžeme při spouštění kódu v ladicím programu opravit.

1. Ve stejném kódu, zatímco pořád ladění, umístěte kurzor na konec `theGalaxy.GalaxyType` a změňte jej na `theGalaxy.GalaxyType.MyGType` . I když lze tuto změnu provést, Editor kódu zobrazí chybu oznamující, že nemůže kompilovat tento kód.

    ![Snímek obrazovky ladicího programu sady Visual Studio se zvýrazněným řádkem kódu, který je zvýrazněný červeně, a polem pro úpravu a pokračování s vybraným tlačítkem Upravit.](../debugger/media/beginners-edit.png)

1. V okně zpráva **Upravit a pokračovat** klikněte na **Upravit** . V okně **Seznam chyb** se teď zobrazí chybová zpráva. Chyba indikuje, že `'object'` neobsahuje definici pro `MyGType` .

    ![Snímek obrazovky ladicího programu sady Visual Studio s řádkem kódu zvýrazněným červenou a Seznam chybovým oknem se dvěma uvedenými chybami.](../debugger/media/beginners-no-definition.png)

    I když nastavíme každý Galaxy s objektem typu `GType` (který má `MyGType` vlastnost), ladicí program nerozpozná `theGalaxy` objekt jako objekt typu `GType` . Co se děje? Chcete si projít libovolným kódem, který nastaví typ Galaxy. Když to uděláte, uvidíte, že `GType` Třída má jednoznačně vlastnost `MyGType` , ale něco není napravo. Chybová zpráva o tom, že se `object` zapíná jako na objekt Interpret jazyka, se zdá, že typ je objekt typu `object` místo objektu typu `GType` .

1. Hledáním kódu, který souvisí s nastavením typu Galaxy, najdete `GalaxyType` vlastnost třídy, která `Galaxy` je zadána jako `object` místo `GType` .

    ```csharp
    public object GalaxyType { get; set; }
    ```

1. Změňte předchozí kód na toto:

    ```csharp
    public GType GalaxyType { get; set; }
    ```

1. Kliknutím na tlačítko **restartovat** ![restart aplikace](../debugger/media/dbg-tour-restart.png "RestartApp") na panelu nástrojů ladění (**CTRL**  +  **SHIFT**  +  **F5**) znovu zkompilujte kód a restartujte.

    Teď, když se ladicí program zastaví `Console.WriteLine` , můžete ukazatel myši najeďte `theGalaxy.GalaxyType.MyGType` a podívat se, že hodnota je správně nastavená.

1. Odstraňte zarážku kliknutím na kroužek zarážky na levém okraji (nebo klikněte pravým tlačítkem myši a zvolte **zarážku**  >  **Odstranit zarážku**) a pokračujte stisknutím klávesy **F5** .

    Aplikace se spustí a zobrazí výstup. Vypadá to poměrně dobrým, ale můžete si všimnout, že se vám zobrazí jedna věc. očekávali jsme, že malý Magellanic Cloud Galaxy se zobrazí jako nepravidelný Galaxy ve výstupu konzoly, ale nezobrazuje vůbec žádný typ Galaxy.

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. Nastavte zarážku na tomto řádku kódu.

    ```csharp
    public GType(char type)
    ```

    Tento kód je, kde je nastaven typ Galaxy, takže chceme se na něj podívat podrobněji.

1. Kliknutím na tlačítko **restartovat** ![restart aplikace](../debugger/media/dbg-tour-restart.png "RestartApp") na panelu nástrojů ladění (**CTRL**  +  **SHIFT**  +  **F5**) restartujte počítač.

    Ladicí program se pozastaví na řádku kódu, kde jste nastavili zarážku.

1. Najeďte myší na `type` proměnnou. Zobrazí se hodnota `S` (za kódem znaku). Máte zájem o hodnotu `I` , protože víte, že se jedná o nepravidelný Galaxy typ.

1. Stiskněte klávesu **F5** a najeďte na `type` proměnnou znovu. Opakujte tento krok, dokud neuvidíte hodnotu `I` v `type` proměnné.

    ![Snímek obrazovky ladicího programu sady Visual Studio s řádkem kódu žlutým a malým oknem zobrazujícím hodnotu proměnné typu jako 73 ' I '.](../debugger/media/beginners-inspecting-data.png)

1. Nyní stiskněte klávesu **F11** (krok **ladění**  >  **do** nebo **Krok do** tlačítka na panelu nástrojů ladění).

    **F11** posune ladicí program (a spustí kód) v jednom okamžiku. **F10** (**krok za krokem**) je podobný příkaz a obě jsou velmi užitečné při učení, jak použít ladicí program.

1. Stiskněte klávesu **F11** , dokud nezastavíte řádek kódu v `switch` příkazu pro hodnotu I. Tady vidíte jasný problém, který je výsledkem překlepu. Očekávali jste, že kód se má posunout na místo, kde se nastaví `MyGType` jako nepravidelný typ Galaxy, ale ladicí program tento kód kompletně přeskočí a pozastaví se v `default` části `switch` příkazu.

    ![Najít překlep](../debugger/media/beginners-typo.png)

    Při prohlížení kódu se v příkazu zobrazí překlep `case 'l'` . Měla by mít hodnotu `case 'I'`.

1. Klikněte na kód pro `case 'l'` a nahraďte ho `case 'I'` .

1. Odeberte zarážku a potom kliknutím na tlačítko **restartovat** aplikaci restartujte.

    Chyby se teď opravily a zobrazí se očekávaný výstup.

    Dokončete aplikaci stisknutím libovolné klávesy.

## <a name="summary"></a>Shrnutí

Po zobrazení problému použijte příkazy ladicího programu a [Krok](../debugger/navigating-through-code-with-the-debugger.md) , jako je například **F10** a **F11** , a Najděte oblast kódu s problémem.

> [!NOTE]
> Pokud je obtížné identifikovat oblast kódu, kde dochází k problému, nastavte zarážku v kódu, který se spustí před výskytem problému, a pak použijte příkazy kroku, dokud se nezobrazí manifest problému. Pomocí [trasováním](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) můžete také Protokolovat zprávy do okna **výstup** . Když prohlížíte zaznamenané zprávy (a všímáte, které zprávy ještě nejsou zaprotokolované!), můžete často izolovat oblast kódu k problému. Tento proces bude pravděpodobně nutné opakovat několikrát, abyste ho mohli zúžit.

Když najdete oblast kódu s problémem, prozkoumejte ho pomocí ladicího programu. Chcete-li zjistit příčinu problému, zkontrolujte kód problému a spusťte aplikaci v ladicím programu:

* Zkontrolujte [proměnné](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) a ověřte, zda obsahují typy hodnot, které by měly obsahovat. Zjistíte-li chybnou hodnotu, zjistíte, kde byla nastavena chybná hodnota (Chcete-li zjistit, kde byla hodnota nastavena, může být nutné buď restartovat ladicí program, prohlédnout si [zásobník volání](../debugger/how-to-use-the-call-stack-window.md)nebo obojí).

* Ověřte, zda aplikace spouští očekávaný kód. (Například v ukázkové aplikaci jsme očekávali, že kód pro příkaz switch nastaví typ Galaxy na nepravidelný, ale aplikace přeskočila kód z důvodu překlepu.)

> [!TIP]
> Pomocí ladicího programu můžete najít chyby. Ladicí nástroj může chyby najít pouze *v* případě, že zná záměr vašeho kódu. Nástroj může znát účel kódu pouze v případě, že je to vývojář, který tento záměr vyjadřuje. To, jak to uděláte, je psaní [testů jednotek](../test/improve-code-quality.md) .

## <a name="next-steps"></a>Další kroky

V tomto článku jste se dozvěděli o několika obecných konceptech ladění. V dalším kroku můžete začít učit se o ladicím programu.

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
