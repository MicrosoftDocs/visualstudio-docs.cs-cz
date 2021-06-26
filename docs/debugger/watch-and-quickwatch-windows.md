---
title: Nastavení sledování proměnných | Microsoft Docs
description: Během ladění si můžete zobrazit proměnné a výrazy v části Watch (Hodinka) a QuickWatch (Rychlé sledování). Sledování může zobrazit několik proměnných, QuickWatch pouze jednu a jen v době přerušení.
ms.custom: SEO-VS-2020
ms.date: 10/11/2018
ms.topic: how-to
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 246f82b2d55e8e15bb5a56afba846a8b5dc8f245
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924900"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Sledování proměnných pomocí oken Watch (Hodinek) a QuickWatch (Rychlé sledování)

Během ladění můžete ke sledování  proměnných a výrazů použít okna Watch (Hodinka) a **QuickWatch** (Rychlé sledování). Okna jsou k dispozici pouze během ladicí relace.

**Okna** sledování mohou během ladění zobrazit několik proměnných najednou. Dialogové **okno QuickWatch** zobrazuje jednu proměnnou najednou a před pokračováním ladění je nutné ji zavřít.

> [!NOTE]
> Pokud jste se pokusili ladit kód poprvé, možná si [](../debugger/debugging-absolute-beginners.md) budete chtít před [](../debugger/write-better-code-with-visual-studio.md) tímto článkem přečíst ladění pro absolutní začátečníky a techniky a nástroje ladění.

## <a name="observe-variables-with-a-watch-window"></a>Sledování proměnných pomocí okno Kukátko

Můžete otevřít více než jedno **okno Watch** (Sledování) a podívat se na více než jednu proměnnou v okně **Watch (Sledování).**

Pokud chcete například nastavit sledování hodnot , a `a` `b` v následujícím `c` kódu:

```C++
int main()
{
    int a, b, c;
    a = 1;
    b = 2;
    c = 0;

    for (int i = 0; i < 10; i++)
    {
        a++;
        b *= 2;
        c = a + b;
    }

    return 0;
}

```

1. Nastavte zarážku na řádku kliknutím na levý okraj, výběrem možnosti Debug `c = a + b;`   >  **Toggle Breakpoint**(Přepnout zarážku) nebo stisknutím **klávesy F9**.

1. Spusťte ladění tak, že vyberete **zelenou šipku Start** nebo **Ladit**  >  **Spustit ladění** nebo stisknete klávesu **F5**. Provádění se pozastaví na zarážce.

1. Otevřete okno **Watch (Sledování)** tak, že **vyberete Ladit**  >  **Windows**  >  **Watch**  >  **Watch 1** nebo **stisknete Ctrl** + **Alt** + **W**  >  **1**.

   Další okna sledování můžete **otevřít** tak, že vyberete Windows **2,** **3** nebo **4.**

1. V okně **Watch (Sledování)** vyberte prázdný řádek a zadejte proměnnou `a` . Totéž proveďte pro `b` a `c` .

   ![Sledování proměnných](../debugger/media/watchvariables.png "WatchVariables")

1. Pokračujte v ladění **výběrem**  >  **možnosti Krok ladění do** nebo stisknutím **klávesy F11** podle potřeby. Hodnoty proměnných v okně **Watch (Sledování)** se při iteraci `for` smyčkou mění.

>[!NOTE]
>Pouze pro jazyk C++
>- Možná budete muset kvalifikovat kontext názvu proměnné nebo výraz, který používá název proměnné. Kontext je funkce, zdrojový soubor nebo modul, ve kterém je umístěna proměnná. Pokud potřebujete kvalifikovat kontext, použijte syntaxi [operátoru kontextu (C++)](../debugger/context-operator-cpp.md) v **názvu** v okně **Watch (Přehrát).**
>
>- Názvy registrů a proměnných můžete přidat pomocí **$\<register&nbsp;name>** nebo do pole Název v okně Watch **@\<register&nbsp;name>**  **(Hodinka).** Další informace najdete v tématu [Pseudovariables](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Použití výrazů v okno Kukátko

V okně Watch (Sledování) můžete sledovat jakýkoli platný výraz rozpoznaný **ladicím** programem.

Například pro kód v předchozí části můžete získat průměr tří hodnot zadáním `(a + b + c) / 3` v okně Watch **(Hodinka):**

![Výraz watch](../debugger/media/watchexpression.png "Výraz kukátka")

Pravidla pro vyhodnocování výrazů v okně **Watch** (Hodinka) jsou obecně stejná jako pravidla pro vyhodnocování výrazů v jazyce kódu. Pokud výraz obsahuje chybu syntaxe, očekávejte stejnou chybu kompilátoru jako v editoru kódu. Například překlep v předchozím výrazu vyprodukuje tuto chybu v okně **Watch (Hodinka):**

![Chyba výrazu sledování](../debugger/media/watchexpressionerror.png "Chyba kukátka výrazu")

V okně Watch (Sledování) se může zobrazit kruh se dvěma **vlnovkou.** Tato ikona znamená, že ladicí program nevyhodnotí výraz kvůli potenciální závislosti mezi vlákny. Vyhodnocení kódu vyžaduje dočasné spuštění jiných vláken v aplikaci, ale vzhledem k tomu, že jste v režimu pozastavení, jsou všechna vlákna v aplikaci obvykle zastavena. Povolení dočasného spuštění jiných vláken může mít neočekávaný vliv na stav aplikace a ladicí program může ignorovat události, jako jsou zarážky a výjimky v těchto vláknech.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Hledání v okno Kukátko

Klíčová slova můžete hledat ve sloupcích Name (Název), Value (Hodnota) a Type (Typ) okna **Watch** (Sledování) pomocí panelu hledání nad jednotlivými okny. Stisknutím klávesy ENTER nebo výběrem jedné ze šipek spusťte hledání. Pokud chcete probíhající hledání zrušit, vyberte na panelu hledání ikonu "x".

Pomocí šipek vlevo a vpravo (Shift+F3 a F3) můžete přecházet mezi nalezenou shodou.

![Hledání v okně Watch (Přehrát)](../debugger/media/ee-search-watch.png "Hledat v okně kukátka")

Pokud chcete, aby hledání bylo  více nebo méně důkladné,  použijte rozevírací seznam Hledat hlouběji v horní části okna Watch (Sledování) a vyberte, kolik úrovní hloubky chcete prohledat do vnořených objektů. 

## <a name="pin-properties-in-the-watch-window"></a>Připnutí vlastností v okno Kukátko

>[!NOTE]
> Tato funkce je podporovaná v .NET Core 3.0 nebo novějším.

Pomocí nástroje **Pinnable Properties** (Připnutelné vlastnosti) můžete rychle zkontrolovat objekty podle jejich vlastností v okno Kukátko.  Pokud chcete tento nástroj použít, najeďte myší na vlastnost a  vyberte ikonu připínáku, která se zobrazí, nebo klikněte pravým tlačítkem a ve výsledné místní nabídce vyberte možnost Připnout člena jako oblíbený.  Tato bublina tuto vlastnost zobrazí na začátek seznamu vlastností objektu a název vlastnosti a hodnota se zobrazí ve **sloupci** Hodnota.  Pokud chcete odepnout vlastnost, znovu vyberte ikonu připnutí nebo v místní nabídce vyberte možnost Odepnout **člena** jako oblíbený.

![Připnutí vlastností v okno Kukátko](../debugger/media/basic-pin-watch.gif "Připnout vlastnosti v okno Kukátko")

Můžete také přepínat názvy vlastností a odfiltrovat ne připnuté vlastnosti při zobrazení seznamu vlastností objektu v okno Kukátko.  K oběma možnostem se můžete podívat tak, že vyberete tlačítka na panelu nástrojů nad oknem hodinek.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a> Aktualizace hodnot hodinek

Při vyhodnocení výrazu se v  okně Watch (Sledování) může zobrazit ikona aktualizace (kruhová šipka). Ikona aktualizace označuje chybu nebo hodnotu, která je ne aktuální.

Pokud chcete hodnotu aktualizovat, vyberte ikonu aktualizace nebo stiskněte mezerník. Ladicí program se pokusí výraz znovu vyhodnotit. V závislosti na tom, proč se hodnota nevyhodnocila, ale možná nebudete moct výraz znovu vyhodnotit.

Najeďte myší na ikonu aktualizace nebo se podívejte na sloupec **Hodnota** z důvodu, proč se výraz nevyhodnotil. Mezi důvody patří:

- Při vyhodnocení výrazu došlo k chybě jako v předchozím příkladu. Může dojít k časového limitu nebo může být proměnná mimo rozsah.

- Výraz má volání funkce, které by mohlo aktivovat vedlejší efekt v aplikaci. Viz [Vedlejší účinky výrazu](#bkmk_sideEffects).

- Automatické vyhodnocení vlastností a implicitních volání funkce je zakázané.

Pokud se zobrazí ikona aktualizace, protože je zakázané automatické vyhodnocení vlastností  a implicitních volání funkcí, můžete ji povolit výběrem možnosti Povolit vyhodnocení vlastnosti a dalších implicitních volání funkcí v části **Nástroje**  >  **Možnosti**  >  **Ladění**  >  **obecné.**

Předvedení použití ikony aktualizace:

1. V **části**  >  **Nástroje Možnosti**  >  **Ladění**  >  **obecné** zrušte **zaškrtnutí políčka Povolit vyhodnocení** vlastnosti a další implicitní volání funkce.

1. Zadejte následující kód a v okně **Watch** (Sledování) nastavte sledování vlastnosti `list.Count` .

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Spuštění ladění V **okně** Watch (Sledování) se zobrazí zpráva podobná následující zprávě:

   ![Aktualizace hodinek](../debugger/media/refreshwatch.png "Aktualizovat kukátko")

1. Pokud chcete hodnotu aktualizovat, vyberte ikonu aktualizace nebo stiskněte mezerník. Ladicí program výraz znovu vyhodnotí.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a> Vedlejší účinky výrazu

Vyhodnocení některých výrazů může změnit hodnotu proměnné nebo jinak ovlivnit stav vaší aplikace. Například při vyhodnocení následujícího výrazu se změní hodnota `var1` :

```csharp
var1 = var2
```

Tento kód může způsobit [vedlejší efekt](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Vedlejší účinky mohou ztížovat ladění změnou způsobu fungování aplikace.

Výraz s vedlejšími účinky se vyhodnotí jenom jednou, když ho poprvé zadáte. Potom se výraz v okně Watch  (Sledování) zobrazí šedě a další vyhodnocení se deaktivuje. Popisek nebo **sloupec Hodnota** vysvětluje, že výraz způsobuje vedlejší efekt. Opětovné hodnocení můžete vynutit výběrem ikony aktualizace, která se zobrazí vedle hodnoty.

Jedním ze způsob, jak zabránit označení vedlejších účinků, je vypnout automatické vyhodnocení funkce. V **části Nástroje**  >  **Možnosti**  >  **Ladění**  >  **obecné** zrušte výběr možnosti Povolit vyhodnocení vlastnosti a další implicitní volání funkce .

Pokud je vyhodnocování vlastností nebo implicitních volání funkcí vypnuté, můžete vyhodnocení vynutit přidáním modifikátoru formátu **ac** do proměnné **Name** v **okně Watch** (Přehrát). Viz [Specifikátory formátu v jazyce C#.](../debugger/format-specifiers-in-csharp.md)

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a> Použití ID objektů v okno Kukátko (C# a Visual Basic)

Někdy chcete sledovat chování konkrétního objektu. Můžete například chtít sledovat objekt, na který odkazuje místní proměnná poté, co tato proměnná vypadne z oboru. V jazyce C# a Visual Basic můžete vytvořit ID objektů pro konkrétní instance typů  odkazů a použít je v okně Sledování a v podmínkách zarážky. ID objektu je generováno ladicími službami modulu CLR (Common Language Runtime) a přidruženo k objektu .

> [!NOTE]
> ID objektů vytvářejí slabé odkazy, které nezabraňují uvolnění paměti objektu. Jsou platné pouze pro aktuální ladicí relaci.

V následujícím kódu metoda `MakePerson()` vytvoří pomocí místní proměnné `Person` :

```csharp
class Person
{
    public Person(string name)
    {
        Name = name;
    }
    public string Name { get; set; }
}

public class Program
{
    static List<Person> _people = new List<Person>();
    public static void Main(string[] args)
    {
        MakePerson();
        DoSomething();
    }

    private static void MakePerson()
    {
        var p = new Person("Bob");
        _people.Add(p);
    }

    private static void DoSomething()
    {
        // more processing
         Console.WriteLine("done");
    }
}
```

Pokud chcete zjistit název objektu v metodě , můžete přidat odkaz na `Person` ID objektu v okně Watch `DoSomething()` `Person` **(Sledování).**

1. Nastavte zarážku v kódu po `Person` vytvoření objektu.

1. Spuštění ladění

1. Po pozastavení provádění na zarážce otevřete okno **místní** hodnoty výběrem možnosti **ladit**  >  místní hodnoty **systému Windows**  >  .

1. V okně **místní** hodnoty klikněte pravým tlačítkem na `Person` proměnnou a vyberte **vytvořit ID objektu**.

   Měl by se zobrazit znak dolaru ( **$** ) plus číslo v okně **místní** hodnoty, což je ID objektu.

1. Přidejte ID objektu do okna **kukátka** tak, že kliknete pravým tlačítkem na ID objektu a vyberete **Přidat kukátko**.

1. Nastavte jinou zarážku v `DoSomething()` metodě.

1. Pokračovat v ladění. Po pozastavení provádění v metodě se v `DoSomething()` okně **kukátko** zobrazí `Person` objekt.

   > [!NOTE]
   > Pokud chcete zobrazit vlastnosti objektu, například `Person.Name` , je nutné povolit vyhodnocování vlastností výběrem možností **nástroje**  >    >  **ladění**  >  **Obecné**  >  **Povolit vyhodnocování vlastností a jiných implicitních volání funkcí**.

## <a name="dynamic-view-and-the-watch-window"></a>Dynamické zobrazení a okno Kukátko

Některé skriptovací jazyky (například JavaScript nebo Python) používají dynamické nebo [ztracené](https://en.wikipedia.org/wiki/Duck_typing) psaní a rozhraní .net verze 4,0 a novější podporuje objekty, které jsou obtížné v normálním ladicím prostředí sledovat.

Okno **kukátka** zobrazí tyto objekty jako dynamické objekty, které jsou vytvořeny z typů, které implementují <xref:System.Dynamic.IDynamicMetaObjectProvider> rozhraní. Uzly dynamických objektů zobrazují dynamické členy dynamických objektů, ale neumožňují úpravy hodnot členů.

Chcete-li aktualizovat hodnoty **dynamického zobrazení** , vyberte [ikonu aktualizace](#bkmk_refreshWatch) vedle uzlu dynamického objektu.

Chcete-li zobrazit pouze **dynamické zobrazení** pro objekt, přidejte specifikátor **dynamického** formátu za název dynamického objektu v okně **kukátka** :

- Pro jazyk C#: `ObjectName, dynamic`
- Pro Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- Ladicí program jazyka C# při krokování na další řádek kódu automaticky nepřehodnotí hodnoty v **dynamickém zobrazení** .
>- Ladicí program Visual Basic automaticky aktualizuje výrazy přidané prostřednictvím **dynamického zobrazení**.
>- Vyhodnocení členů **dynamického zobrazení** může mít [vedlejší účinky](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)).

**Chcete-li vložit novou proměnnou kukátka, která přetypování objektu na dynamický objekt:**

1. Klikněte pravým tlačítkem na libovolný podřízený uzel **dynamického zobrazení**.
1. Vyberte **Přidat kukátko**. `object.name` `((dynamic) object).name` A zobrazí se v novém okně **kukátka** .

Ladicí program také přidá podřízený uzel **dynamického zobrazení** objektu do okna **Automatické** hodnoty. Chcete-li otevřít okno **Automatické** hodnoty, vyberte během ladění možnost **ladit**  >  **okna**  >  **Automatické** hodnoty.

**Dynamické zobrazení** také vylepšuje ladění pro objekty modelu COM. Když ladicí program získá do objektu COM zabalený v **System.__ComObject**, přidá uzel **dynamického zobrazení** pro objekt.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Sledovat jednu proměnnou nebo výraz pomocí QuickWatch

Pomocí **QuickWatch** můžete sledovat jedinou proměnnou.

Například pro následující kód:

```csharp
static void Main(string[] args)
{
    int a, b;
    a = 1;
    b = 2;
    for (int i = 0; i < 10; i++)
    {
        a = a + b;
    }
}
```

Chcete-li sledovat `a` proměnnou,

1. Nastavte zarážku na `a = a + b;` řádku.

1. Spuštění ladění Spuštění pozastaví na zarážce.

1. Vyberte proměnnou `a` v kódu.

1. Vyberte **Debug**  >  **QuickWatch**, stiskněte **SHIFT** + **F9** nebo klikněte pravým tlačítkem a vyberte **QuickWatch**.

   Zobrazí se dialogové okno **QuickWatch** . `a`Proměnná je v poli **výrazu** s **hodnotou** **1**.

   ![QuickWatch – proměnná](../debugger/media/quickwatchvariable.png "QuickWatch – proměnná")

1. Chcete-li vyhodnotit výraz pomocí proměnné, zadejte výraz `a + b` , například do pole **výraz** , a vyberte možnost znovu **vyhodnotit**.

   ![Výraz QuickWatch](../debugger/media/quickwatchexpression.png "Výraz QuickWatch")

1. Chcete-li přidat proměnnou nebo výraz z **QuickWatch** do okna **kukátka** , vyberte možnost **Přidat kukátko**.

1. Výběrem **Zavřít** zavřete okno **QuickWatch** . (**QuickWatch** je modální dialogové okno, takže nemůžete pokračovat v ladění, dokud je otevřené.)

1. Pokračovat v ladění. Proměnnou můžete sledovat v okně **kukátko** .

## <a name="see-also"></a>Viz také
- [Co je ladění?](../debugger/what-is-debugging.md)
- [Techniky ladění a související nástroje](../debugger/write-better-code-with-visual-studio.md)
- [První pohled na ladění](../debugger/debugger-feature-tour.md)
- [Okna ladicího programu](../debugger/debugger-windows.md)
