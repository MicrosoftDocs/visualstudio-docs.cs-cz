---
title: Ladicí kód pro úplné začátečníky
description: Pokud ladíte poprvé, naučte se několik zásad, které vám pomohou spustit aplikaci v režimu ladění s Visual Studio
ms.date: 02/14/2020
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c3cf9d5e4d72ed316344d1bda930d0416e9efe5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77416391"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Jak ladit pro absolutní začátečníky

Kód, který napíšeme jako vývojáři softwaru, nemusí vždy dělat to, co jsme očekávali. Někdy to dělá něco úplně jiného! Když k tomu dojde, dalším úkolem je zjistit, proč, a přestože bychom mohli být v pokušení jen držet zíral na náš kód hodiny, je to mnohem jednodušší a efektivní použít ladicí nástroj, nebo ladicí program.

Ladicí program, bohužel, není něco, co může magicky odhalit všechny problémy nebo "chyby" v našem kódu. *Ladění* znamená spustit kód krok za krokem v ladicím nástroji, jako je Visual Studio, chcete-li najít přesný bod, kde jste udělali chybu programování. Pak pochopit, jaké opravy je třeba provést v kódu a ladění nástroje často umožňují provádět dočasné změny, takže můžete pokračovat v běhu programu.

Efektivní používání ladicího programu je také dovednost, která vyžaduje čas a praxi, aby se naučila, ale je v konečném důsledku základním úkolem pro každého vývojáře softwaru. V tomto článku pak představíme základní principy ladění a poskytneme tipy, které vám pomohou začít.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Vyjasněte problém tím, že si položíte správné otázky

Pomáhá objasnit problém, na který jste narazili, než se ho pokusíte opravit. Očekáváme, že jste již narazili na problém ve vašem kódu, jinak byste se tady nesnažili přijít na to, jak ho ladit! Takže než začnete ladit, ujistěte se, že jste identifikovali problém, který se pokoušíte vyřešit:

* Co jste čekali, že váš kód udělat?

* Co se místo toho stalo?

    Pokud jste narazili na chybu (výjimku) při spuštění aplikace, může to být dobrá věc! Výjimkou je neočekávaná událost zjištěná při spuštění kódu, obvykle chyba nějakého druhu. Ladicí nástroj vás může převést na přesné místo v kódu, kde došlo k výjimce, a může vám pomoci prozkoumat možné opravy.

    Pokud se stalo něco jiného, jaký je příznak problému? Máte již podezření, kde k tomuto problému došlo ve vašem kódu? Pokud například kód zobrazuje nějaký text, ale text je nesprávný, víte, že data jsou chybná nebo kód, který nastavil zobrazovaný text, má nějakou chybu. Krokování kódu v ladicím programu, můžete prozkoumat každou změnu proměnných přesně zjistit, kdy a jak jsou přiřazeny nesprávné hodnoty.

## <a name="examine-your-assumptions"></a>Prozkoumejte své předpoklady

Než začnete vyšetřovat chybu nebo chybu, představte si předpoklady, které vás donutily očekávat určitý výsledek. Skryté nebo neznámé předpoklady mohou stát v cestě identifikaci problému i v případě, že se díváte přímo na příčinu problému v ladicím programu. Můžete mít dlouhý seznam možných předpokladů! Zde je několik otázek, zeptejte se sami sebe napadnout své předpoklady.

* Používáte správné rozhraní API (to znamená správný objekt, funkci, metodu nebo vlastnost)? Rozhraní API, které používáte, nemusí dělat to, co si myslíte, že dělá. (Po kontrole volání rozhraní API v ladicím programu může oprava vyžadovat cestu do dokumentace, která vám pomůže identifikovat správné rozhraní API.)

* Používáte rozhraní API správně? Možná jste použili správné API, ale nepoužívali jste ho správným způsobem.

* Obsahuje váš kód nějaké překlepy? Některé překlepy, jako je jednoduchý překlep názvu proměnné, může být obtížné zobrazit, zejména při práci s jazyky, které nevyžadují proměnné, které mají být deklarovány před jejich použitím.

* Provedli jste změnu kódu a předpokládali jste, že nesouvisí s problémem, který vidíte?

* Očekávali jste, že objekt nebo proměnná bude obsahovat určitou hodnotu (nebo určitý typ hodnoty), která se liší od toho, co se skutečně stalo?

* Znáte záměr kódu? Je často obtížnější ladit kód někoho jiného. Pokud to není váš kód, je možné, že budete muset trávit čas učení přesně to, co kód dělá, než můžete ladit efektivně.

    > [!TIP]
    > Při psaní kódu začněte v malém a začněte s kódem, který funguje! (Dobrý ukázkový kód je užitečné zde.) Někdy je jednodušší opravit velkou nebo složitou sadu kódu spuštěním s malou část kódu, která ukazuje základní úkol, který se pokoušíte dosáhnout. Potom můžete upravit nebo přidat kód postupně, testování v každém bodě chyby.

Tím, že zpochybňuje vaše předpoklady, můžete zkrátit čas potřebný k nalezení problému v kódu. Můžete také zkrátit dobu potřebný k vyřešení problému.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Krokovat kód v režimu ladění a zjistit, kde k problému došlo

Při normálním spuštění aplikace se zobrazí chyby a nesprávné výsledky až po spuštění kódu. Program může také neočekávaně ukončit, aniž by vám řekl proč.

Spuštění aplikace v ladicím programu, nazývaném také *režim ladění*, znamená, že ladicí program aktivně sleduje vše, co se děje při spuštění programu. Umožňuje také pozastavit aplikaci v libovolném bodě, abyste prozkoumali její stav a pak krokovat kód řádek po řádku a sledovat každý detail, jak se to stane.

V sadě Visual Studio zadáte režim ladění **Debug** > pomocí **klávesy F5** (nebo příkazu nabídky**Ladění start ladění** nebo tlačítka Start **ladění** ![spustit ladění](../debugger/media/dbg-tour-start-debugging.png "Spustit ladění") na panelu nástrojů ladění). Pokud dojde k nějaké výjimky, Visual Studio výjimka Helper přejde do přesného bodu, kde došlo k výjimce a poskytuje další užitečné informace. Další informace o tom, jak zpracovat výjimky v kódu, naleznete v [tématu](../debugger/write-better-code-with-visual-studio.md)ladění techniky a nástroje .

Pokud jste nezískali výjimku, pravděpodobně máte dobrou představu, kde hledat problém v kódu. Toto je místo, kde můžete použít *zarážky* s ladicím programem, abyste měli možnost prozkoumat váš kód pečlivěji. Zarážky jsou základní a nejjednodušší funkcí spolehlivého ladění. Zarážka označuje, kde visual studio by měl pozastavit spuštěný kód, takže se můžete podívat na hodnoty proměnných nebo chování paměti nebo pořadí, ve kterém je kód spuštěn.

V sadě Visual Studio můžete rychle nastavit zarážku kliknutím na levý okraj vedle řádku kódu. Nebo umístěte kurzor na řádek a stiskněte **klávesu F9**.

Chcete-li ilustrovat tyto koncepty, provedeme vás prostřednictvím některého ukázkového kódu, který již má několik chyb. Používáme C#, ale ladicí funkce platí pro visual basic, C++, JavaScript, Python a další podporované jazyky.

### <a name="create-a-sample-app-with-some-bugs"></a>Vytvoření ukázkové aplikace (s některými chybami)

Dále vytvoříme aplikaci, která má několik chyb.

1. Musíte mít nainstalovanou Visual Studio a buď **zatížení vývoje plochy .NET** nebo vývojové úlohy **.NET Core napříč** platformami, v závislosti na typu aplikace, kterou chcete vytvořit.

    Pokud jste visual studio ještě nenainstalovali, přejděte na stránku ke stažení sady Visual [Studio](https://visualstudio.microsoft.com/downloads/)a nainstalujte ji zdarma.

    Pokud potřebujete nainstalovat úlohy, ale už máte Visual Studio, klikněte na **nástroje** > **získat nástroje a funkce**. Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje plochy .NET** (nebo **vývoj napříč platformami .NET Core)** a pak zvolte **Změnit**.

1. Otevřete sadu Visual Studio.

    ::: moniker range=">=vs-2019"
    V počátečním okně zvolte **Vytvořit nový projekt**. Do vyhledávacího pole zadejte **konzolu** a pak zvolte **Console App (.NET Core)** nebo **Console App (.NET Framework).** Zvolte **Další**. Zadejte název projektu, jako **je ConsoleApp-FirstApp,** a klepněte na **tlačítko Vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **nového** > **projektu**. V levém podokně dialogového okna **Nový projekt** v části **Visual C#** zvolte **Console App**a potom v prostředním podokně zvolte **buď Konzolovou aplikaci (.NET Framework)** nebo **Konzolovou aplikaci (.NET Core)**. Zadejte název jako **ConsoleApp-FirstApp** a klepněte na **tlačítko OK**.
    ::: moniker-end

    Pokud nevidíte šablonu projektu **Konzola aplikace (.NET Framework)** nebo **Console App (.NET Core),** přejděte na **nástroje** > **získat nástroje a funkce**, který otevře Instalační službu Sady Visual Studio. Zvolte **vývoj napříč platformami .NET Core** nebo pracovní vytížení **pro vývoj pracovních ploch .NET** a pak zvolte **Změnit**.

    Visual Studio vytvoří projekt konzoly, který se zobrazí v Průzkumníku řešení v pravém podokně.

1. V *Program.cs*nahraďte veškerý výchozí kód následujícím kódem:

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

    Naším záměrem pro tento kód je zobrazit název galaxie, vzdálenost k galaxii, a galaxie typu vše v seznamu. Chcete-li ladit, je důležité pochopit záměr kódu. Zde je formát pro jeden řádek ze seznamu, který chceme zobrazit ve výstupu:

    *název galaxie*, *vzdálenost*, *typ galaxie*.

### <a name="run-the-app"></a>Spuštění aplikace

1. Stiskněte **klávesu F5** nebo tlačítko **Start Ladění** Spustit ![ladění](../debugger/media/dbg-tour-start-debugging.png "Spustit ladění") na panelu nástrojů Ladění, který se nachází nad editorem kódu.

    Aplikace se spustí a debugger nám nezobrazí žádné výjimky. Výstup, který vidíte v okně konzoly, však není to, co očekáváte. Zde je očekávaný výstup:

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Ale vidíme to tomísto:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType
    Pinwheel  25,  ConsoleApp_FirstApp.GType
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Při pohledu na výstup a na `GType` náš kód víme, že je název třídy, která ukládá typ galaxie. Snažíme se ukázat skutečný typ galaxie (například "Spirála"), nikoli název třídy!

### <a name="debug-the-app"></a>Ladění aplikace

1. Pokud je aplikace stále spuštěná, nastavte zarážku `Console.WriteLine` kliknutím na levý okraj vedle volání metody v tomto řádku kódu.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }
    ```

    Když nastavíte zarážku, zobrazí se na levém okraji červená tečka.

    Protože vidíme problém ve výstupu, začneme ladění při pohledu na předchozí kód, který nastaví výstup v ladicím programu.

1. Klepněte na tlačítko **Restartovat** ![aplikaci](../debugger/media/dbg-tour-restart.png "Restartovat aplikaci") na panelu nástrojů Ladění **(Ctrl** + **Shift** + **F5).**

    Aplikace se pozastaví na zarážky, kterou nastavíte. Žluté zvýraznění označuje, kde je ladicí program pozastaven (žlutý řádek kódu ještě nebyl proveden).

1. Najeďte `GalaxyType` nad proměnnou vpravo a potom nalevo od ikony `theGalaxy.GalaxyType`klíče rozbalte . Uvidíte, `GalaxyType` že `MyGType`obsahuje vlastnost a hodnota `Spiral`vlastnosti je nastavena na .

    ![Kontrola proměnné](../debugger/media/beginners-inspect-variable.png)

    "Spirála" je vlastně správná hodnota, kterou jste očekávali vytisknout do konzole! Takže je to dobrý začátek, že můžete přistupovat k této hodnotě v tomto kódu při spuštění aplikace. V tomto scénáři používáme nesprávné rozhraní API. Uvidíme, jestli můžeme opravit při spuštění kódu v ladicím programu.

1. Ve stejném kódu, zatímco ještě ladění, dát kurzor `theGalaxy.GalaxyType` na konci `theGalaxy.GalaxyType.MyGType`a změnit na . I když můžete provést tuto změnu, editor kódu zobrazí chybu označující, že nelze zkompilovat tento kód.

    ![Chyba syntaxe](../debugger/media/beginners-edit.png)

1. V poli **Upravit a pokračovat ve** zprávě klikněte na **Upravit.** V okně **Seznam chyb** se nyní zobrazí chybová zpráva. Chyba označuje, `'object'` že neobsahuje definici `MyGType`pro .

    ![Chyba syntaxe](../debugger/media/beginners-no-definition.png)

    I když jsme nastavili každou `GType` galaxii s `MyGType` objektem typu (který má `theGalaxy` vlastnost), ladicí program nerozpozná objekt jako objekt typu `GType`. Co se děje? Chcete se podívat na jakýkoli kód, který nastavuje typ galaxie. Když toto uděláte, `GType` uvidíte, že `MyGType`třída má určitě vlastnost , ale něco není v pořádku. Chybová zpráva `object` o ukáže být vodítkem; interpretu jazyka, typ se jeví jako `object` objekt typu namísto objektu typu `GType`.

1. Při pohledu na kód související s nastavením typu galaxie zjistíte, že `GalaxyType` vlastnost `Galaxy` třídy je určena jako `object` místo `GType`.

    ```csharp
    public object GalaxyType { get; set; }
    ```

1. Změňte předchozí kód na toto:

    ```csharp
    public GType GalaxyType { get; set; }
    ```

1. Chcete-li znovu zkompilovat kód**Ctrl** + a restartovat, klepněte na tlačítko **Restartovat** ![aplikaci na](../debugger/media/dbg-tour-restart.png "Restartovat aplikaci") panelu nástrojů Ladění ( Ctrl**Shift** + **F5).**

    Nyní, když ladicí program `Console.WriteLine`pozastaví na `theGalaxy.GalaxyType.MyGType`, můžete najet myší a uvidíte, že hodnota je správně nastavena.

1. Odstraňte zarážku kliknutím na kruh zarážky v levém okraji (nebo klikněte pravým tlačítkem myši a zvolte **Odstranit** > **zarážku**) a pak pokračujte stisknutím **klávesy F5.**

    Aplikace se spustí a zobrazí výstup. Vypadá to docela dobře teď, ale všimni si jednu věc; Očekávali jste, že se galaxie Malého Magellanova oblaku objeví jako nepravidelná galaxie ve výstupu konzole, ale nezobrazuje vůbec žádný typ galaxie.

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

    Tento kód je místo, kde je nastaven typ galaxie, takže se na něj chceme podívat zblízka.

1. Restartujte **Restart** restartování ![aplikace](../debugger/media/dbg-tour-restart.png "Restartovat aplikaci") na panelu nástrojů Ladění (**Ctrl** + **Shift** + **F5).**

    Ladicí program pozastaví na řádku kódu, kde nastavíte zarážku.

1. Najeďte `type` nad proměnnou. Zobrazí se hodnota `S` (následující kód znaku). Máte zájem o hodnotu `I`, protože víte, že je nepravidelný typ galaxie.

1. Stiskněte **klávesu F5** `type` a znovu najeďte na proměnnou. Tento krok opakujte, dokud `I` se `type` v proměnné nezobrazí hodnota.

    ![Kontrola proměnné](../debugger/media/beginners-inspecting-data.png)

1. Nyní stiskněte **klávesu F11** (**Ladění** > **kroku do** nebo tlačítko Krok **do** v panelu nástrojů ladění).

    **F11** předem ladicí program (a spustí kód) jeden příkaz najednou. **F10** (**Krok přes)** je podobný příkaz a oba jsou velmi užitečné při učení, jak používat ladicí program.

1. Stiskněte **klávesu F11,** dokud nezastavíte na řádku kódu v příkazu `switch` pro hodnotu "I". Zde vidíte jasný problém vyplývající z překlepu. Očekávali jste, že kód `MyGType` předem, kde se nastaví jako typ nepravidelné galaxie, ale `default` ladicí `switch` program místo toho přeskočí tento kód úplně a pozastaví na části příkazu.

    ![Najít překlep](../debugger/media/beginners-typo.png)

    Při pohledu na kód, vidíte `case 'l'` překlep v příkazu. Mělo by to být `case 'I'`.

1. Klikněte na `case 'l'` kód pro `case 'I'`a nahraďte jej .

1. Odeberte zarážku a kliknutím na tlačítko **Restartovat** aplikaci restartujte.

    Chyby jsou nyní opraveny a zobrazí se výstup, který očekáváte!

    Aplikací můžete dokončit stisknutím libovolné klávesy.

## <a name="summary"></a>Souhrn

Když uvidíte problém, použijte ladicí program a [příkazy kroku,](../debugger/navigating-through-code-with-the-debugger.md) jako jsou **F10** a **F11,** k nalezení oblasti kódu s problémem.

> [!NOTE]
> Pokud je obtížné identifikovat oblast kódu, kde k problému dochází, nastavte zarážku v kódu, který běží před výskytem problému a potom použijte příkazy kroku, dokud se nezobrazí manifest problému. Body [trasování](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) můžete také použít k protokolování zpráv do okna **Výstup.** Při pohledu na protokolované zprávy (a všímat si, které zprávy ještě nebyly zaznamenány!), Můžete často izolovat oblast kódu s problémem. Možná budete muset tento proces několikrát zopakovat, abyste jej zúžili.

Když najdete oblast kódu s problémem, použijte ladicí program prozkoumat. Příčinu problému najdete v kódu problému při spuštění aplikace v ladicím programu:

* [Zkontrolujte proměnné](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) a zkontrolujte, zda obsahují typ hodnot, které by měly obsahovat. Pokud najdete chybnou hodnotu, zjistěte, kde byla chybná hodnota nastavena (chcete-li zjistit, kde byla hodnota nastavena, bude pravděpodobně nutné buď restartovat ladicí program, podívat se na [zásobník volání](../debugger/how-to-use-the-call-stack-window.md)nebo obojí).

* Zkontrolujte, zda aplikace provádí kód, který očekáváte. (Například v ukázkové aplikaci jsme očekávali, že kód příkazu switch nastaví typ galaxie na Nepravidelný, ale aplikace přeskočí kód kvůli překlepu.)

> [!TIP]
> Pomocí ladicího programu, který vám pomůže najít chyby. Ladicí nástroj můžete najít chyby *pro vás* pouze v případě, že zná záměr vašeho kódu. Nástroj může znát záměr vašeho kódu pouze v případě, že vy, vývojář, vyjádřit tento záměr. Psaní [testů částí](../test/improve-code-quality.md) je, jak to udělat.

## <a name="next-steps"></a>Další kroky

V tomto článku jste se naučili několik obecných konceptů ladění. Dále se můžete začít učit více o ladicím programu.

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
