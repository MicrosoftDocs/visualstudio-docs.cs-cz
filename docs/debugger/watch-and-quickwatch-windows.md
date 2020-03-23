---
title: Nastavení hodinek na proměnné | Dokumenty společnosti Microsoft
ms.custom: seodec18
ms.date: 10/11/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea3d2a1e82e92473859fef29754fbb831cf3685b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302005"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Sledování proměnných pomocí oken Watch a QuickWatch

Při ladění můžete ke sledování proměnných a výrazů použít **okna a** **hodinky QuickWatch.** Okna jsou k dispozici pouze během relace ladění.

**Okna sledování** můžete zobrazit několik proměnných najednou při ladění. Dialogové okno **Rychlé sledování** zobrazuje jednu proměnnou najednou a před pokračováním ladění musí být uzavřeno.

Pokud je to poprvé, co jste se pokusili ladit kód, můžete si přečíst [ladění pro absolutní začátečníky](../debugger/debugging-absolute-beginners.md) a ladění [techniky a nástroje](../debugger/write-better-code-with-visual-studio.md) před procházením tohoto článku.

## <a name="observe-variables-with-a-watch-window"></a>Sledování proměnných pomocí okna Kukátka

Můžete otevřít více než jedno okno **kukátka** a sledovat více než jednu proměnnou v okně **kukátka.**

Chcete-li například nastavit sledování `a`hodnot `b`, `c` , a v následujícím kódu:

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

1. Nastavte zarážku `c = a + b;` na řádku klepnutím na levý okraj, výběrem **možnosti Ladění** > **přepínací zarážky nebo**stisknutím **klávesy F9**.

1. Ladění můžete spustit výběrem zelené šipky **Start** nebo **Ladění** > **počátečního ladění**nebo stisknutím **klávesy F5**. Spuštění pozastaví na zarážky.

1. Otevřete okno **Kukátka** výběrem **možnosti Ladění** > sledování**ve službách Windows** > **Watch** > **1**nebo stisknutím **klávesy Ctrl**+**Alt**+**W** > **1**.

   Další okna **kukátku** můžete otevřít výběrem oken **2**, **3**nebo **4**.

1. V okně **Kukátko** vyberte prázdný `a`řádek a zadejte proměnnou . Proveďte totéž pro `b` a `c`.

   ![Sledování proměnných](../debugger/media/watchvariables.png "Sledovat proměnné")

1. Pokračujte v ladění výběrem **ladění** > **kroku do** nebo stisknutím **klávesy F11** podle potřeby k postupu. Hodnoty proměnných v okně **Kukátko** se `for` při itetování ve smyčce mění.

>[!NOTE]
>Pouze pro C++
>- Možná budete muset kvalifikovat kontext názvu proměnné nebo výraz, který používá název proměnné. Kontext je funkce, zdrojový soubor nebo modul, kde je proměnná umístěna. Pokud máte kvalifikovat kontext, použijte syntaxi [operátoru kontextu (C++)](../debugger/context-operator-cpp.md) v **name** v okně **Kukátka.**
>
>- Názvy registrů a proměnných můžete přidat pomocí ** $ \<názvu registru&nbsp;>** nebo ** @ \<název registru&nbsp;>** do okna **Název** v okně **Kukátko.** Další informace naleznete v tématu [Pseudovariables](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Použití výrazů v okně Kukátka

Můžete sledovat libovolný platný výraz rozpoznaný ladicím programem v okně **Kukátka.**

Například pro kód v předchozí části můžete získat průměr ze tří `(a + b + c) / 3` hodnot zadáním do okna **Kukátko:**

![Sledovat výraz](../debugger/media/watchexpression.png "Sledovat výraz")

Pravidla pro vyhodnocení výrazů v okně **Kukátko** jsou obecně stejné jako pravidla pro vyhodnocení výrazů v jazyce kódu. Pokud výraz obsahuje syntaktickou chybu, očekávejte stejnou chybu kompilátoru jako v editoru kódu. Například překlep v předchozím výrazu způsobí tuto chybu v okně **Kukátko:**

![Chyba výrazu sledování](../debugger/media/watchexpressionerror.png "Chyba výrazu sledování")

V okně **Kukátko** se může zobrazit kruh se dvěma ikonami vlnovky. Tato ikona znamená, že ladicí program nevyhodnocuje výraz z důvodu potenciální závislosti mezi vlákny. Vyhodnocení kódu vyžaduje, aby se dočasně spouštěla další vlákna ve vaší aplikaci, ale protože jste v režimu přerušení, jsou všechna vlákna ve vaší aplikaci obvykle zastavena. Povolení dočasného spuštění jiných vláken může mít neočekávané účinky na stav aplikace a ladicí program může ignorovat události, jako jsou zarážky a výjimky v těchto vláknech.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Hledání v okně Kukátka

Klíčová slova můžete vyhledat ve sloupcích Název, Hodnota a Typ okna **Kukátka** pomocí vyhledávacího panelu nad každým oknem. Stiskněte klávesu ENTER nebo vyberte jednu ze šipek, která provede hledání. Chcete-li zrušit probíhající hledání, vyberte na panelu hledání ikonu "x".

Pomocí levé a pravé šipky (Shift + F3, respektive) pro navigaci mezi nalezenými shodami.

![Hledání v okně kukátka](../debugger/media/ee-search-watch.png "Hledání v okně kukátka")

Chcete-li, aby vaše hledání bylo více či méně důkladné, použijte rozbalovací okno **Hledat hlouběji** v horní části okna **Kukátka** a vyberte, kolik úrovní hluboko chcete prohledávat do vnořených objektů. 

## <a name="pin-properties-in-the-watch-window"></a>Vlastnosti připnutí v okně Kukátka

>[!NOTE]
> Tato funkce je podporována v rozhraní .NET Core 3.0 nebo vyšší.

Pomocí nástroje **Pinnable Properties** můžete rychle kontrolovat objekty podle jejich vlastností v okně Kukátka.  Chcete-li použít tento nástroj, najeďte na položku vlastnost a vyberte ikonu špendlíku, která se zobrazí nebo klepnete pravým tlačítkem myši, a ve výsledné kontextové nabídce vyberte možnost **Připnout člena jako oblíbenou.**  Tím se tato vlastnost probublává na začátek seznamu vlastností objektu a název a hodnota vlastnosti se zobrazí ve sloupci **Hodnota.**  Chcete-li vlastnost odepnout, vyberte ikonu špendlíku znovu nebo v místní nabídce vyberte volbu **Odepnout jako oblíbené.**

![Vlastnosti připnutí v okně Kukátka](../debugger/media/basic-pin-watch.gif "Vlastnosti připnutí v okně Kukátka")

Můžete také přepínat názvy vlastností a odfiltrovat nepřipnuté vlastnosti při prohlížení seznamu vlastností objektu v okně Kukátka.  K oběma možnostem můžete přistupovat výběrem tlačítek na panelu nástrojů nad oknem kukátka.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a>Aktualizovat hodnoty sledování

Při vyhodnocení výrazu se může v okně **Kukátko** zobrazit ikona aktualizace (kruhová šipka). Ikona aktualizace označuje chybu nebo hodnotu, která je zastaralá.

Chcete-li hodnotu aktualizovat, vyberte ikonu aktualizace nebo stiskněte mezerník. Ladicí program se pokusí přehodnocení výrazu. Však nemusí chtít nebo být schopen přehodnotit výraz, v závislosti na tom, proč hodnota nebyla vyhodnocena.

Najeďte na ikonu aktualizace nebo z tohoto důvodu se podívejte do sloupce **Hodnota,** proč výraz nebyl vyhodnocen. Důvody zahrnují:

- Při vyhodnocování výrazu, stejně jako v předchozím příkladu, došlo k chybě. Může dojít k časovému rámci nebo proměnná může být mimo rozsah.

- Výraz má volání funkce, které by mohlo vyvolat vedlejší účinek v aplikaci. Viz [Výraz vedlejší účinky](#bkmk_sideEffects).

- Automatické vyhodnocení vlastností a volání implicitních funkcí je zakázáno.

Pokud se ikona aktualizace zobrazí, protože je zakázáno automatické vyhodnocení vlastností a volání implicitních funkcí, můžete ji povolit výběrem **možnosti Povolit vyhodnocení vlastností a dalších implicitních volání funkcí** v**části Obecné****ladění** > **možností** >  **nástrojů** > .

Chcete-li demonstrovat pomocí ikony aktualizace:

1. V části**Možnosti** >  **nástrojů** > **Ladění** > **obecné**, zrušte zaškrtnutí políčka **Povolit vyhodnocení vlastností a další implicitní volání funkce.**

1. Zadejte následující kód a v okně **Kukátko** nastavte hodinky na `list.Count` vlastnost.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Začněte ladit. Okno **Kukátko** zobrazuje něco jako následující zprávu:

   ![Aktualizovat sledování](../debugger/media/refreshwatch.png "Aktualizovat sledování")

1. Chcete-li hodnotu aktualizovat, vyberte ikonu aktualizace nebo stiskněte mezerník. Ladicí program přehodnotí výraz.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a>Vedlejší účinky výrazu

Vyhodnocení některých výrazů může změnit hodnotu proměnné nebo jinak ovlivnit stav aplikace. Například vyhodnocení následujícího výrazu změní `var1`hodnotu :

```csharp
var1 = var2
```

Tento kód může způsobit [nežádoucí účinek](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Vedlejší účinky mohou ztížit ladění změnou způsobu, jakým vaše aplikace funguje.

Výraz s vedlejšími účinky je vyhodnocen pouze jednou, když jej poprvé zadáte. Poté se výraz zobrazí šedě v okně **kukátka** a další hodnocení jsou zakázána. Sloupec s popisem nebo **hodnotou** vysvětluje, že výraz způsobuje vedlejší účinek. Přehodnocení můžete vynutit výběrem ikony aktualizace, která se zobrazí vedle hodnoty.

Jedním ze způsobů, jak zabránit označení vedlejších účinků, je vypnout automatické vyhodnocení funkce. V části**Možnosti** >  **nástrojů** > **Ladění** > **obecné**, odznačte **Povolit vyhodnocení vlastností a další implicitní volání funkce**.

Pouze pro C# při vyhodnocení vlastností nebo volání implicitní funkce je vypnuto, můžete vynutit vyhodnocení přidáním modifikátor **formátu ac** do proměnné **Název** v okně **watch.** Viz [Formát specifikátorů v c#](../debugger/format-specifiers-in-csharp.md).

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a>Použití ID objektů v okně Kukátka (C# a Visual Basic)

Někdy chcete sledovat chování určitého objektu. Můžete například sledovat objekt, na který odkazuje místní proměnná poté, co tato proměnná překročila rozsah. V jazyce C# a visual basicu můžete vytvořit ID objektů pro konkrétní instance typů odkazů a použít je v okně **Kukátka** a za podmínek zarážky. ID objektu je generováno služby ladění clr (COMMON Language runtime) a je přidruženo k objektu.

> [!NOTE]
> ID objektů vytvořit slabé odkazy, které nebrání objektu z uvolňování paměti. Jsou platné pouze pro aktuální relaci ladění.

V následujícím kódu `MakePerson()` metoda vytvoří `Person` pomocí místní proměnné:

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

Chcete-li zjistit název `Person` v `DoSomething()` metodě, můžete přidat `Person` odkaz na ID objektu v okně **Kukátka.**

1. Nastavte zarážku v `Person` kódu po vytvoření objektu.

1. Začněte ladit.

1. Při pozastavení provádění na zarážky otevřete okno **Locals** výběrem **ladění** > **windows** > **locals**.

1. V okně **Locals** klepněte `Person` pravým tlačítkem myši na proměnnou a vyberte **příkaz Vytvořit ID objektu**.

   V okně **Locals,** **$** což je ID objektu, by se měl zobrazit znak dolaru ( ) plus číslo.

1. Přidejte ID objektu do okna **Kukátko** tak, že kliknete pravým tlačítkem myši na ID objektu a vyberete **přidat hodinky**.

1. Nastavte další zarážku v metodě. `DoSomething()`

1. Pokračujte v ladění. Při pozastaví spuštění `DoSomething()` v metodě, `Person` okno **Watch** zobrazí objekt.

   > [!NOTE]
   > Pokud chcete zobrazit vlastnosti objektu, `Person.Name`například , musíte povolit vyhodnocení vlastností výběrem**možnosti** >  **nástroje** > **ladění** > **obecné** > **povolit vyhodnocení vlastnosti a další implicitní volání funkcí**.

## <a name="dynamic-view-and-the-watch-window"></a>Dynamické zobrazení a okno Kukátka

Některé skriptovací jazyky (například JavaScript nebo Python) používají dynamické nebo [kachní](https://en.wikipedia.org/wiki/Duck_typing) psaní a .NET verze 4.0 a novější podporuje objekty, které je obtížné sledovat v normálních ladicích oknech.

Okno **Kukátko** zobrazí tyto objekty jako dynamické <xref:System.Dynamic.IDynamicMetaObjectProvider> objekty, které jsou vytvořeny z typů, které implementují rozhraní. Uzly dynamických objektů zobrazují dynamické členy dynamických objektů, ale neumožňují úpravy hodnot členů.

Chcete-li aktualizovat hodnoty **dynamického zobrazení,** vyberte [ikonu aktualizace](#bkmk_refreshWatch) vedle uzlu dynamického objektu.

Chcete-li zobrazit pouze **dynamické zobrazení** objektu, přidejte za název dynamického objektu v okně **Kukátko** specifikátor **dynamického** formátu:

- Pro C#:`ObjectName, dynamic`
- Pro visual basic:`$dynamic, ObjectName`

>[!NOTE]
>- Ladicí program Jazyka C# automaticky nepřehodnotí hodnoty v **dynamickém zobrazení,** když přejdete na další řádek kódu.
>- Ladicí program jazyka Visual Basic automaticky aktualizuje výrazy přidané prostřednictvím **dynamického zobrazení**.
>- Vyhodnocení členů **dynamického zobrazení** může mít [vedlejší účinky](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)).

**Vložení nové proměnné sledování, která přetypuje objekt na dynamický objekt:**

1. Klepněte pravým tlačítkem myši na libovolnou podřízenou položku **dynamického zobrazení**.
1. Zvolte **Přidat hodinky**. Stane `object.name` `((dynamic) object).name` se a zobrazí v novém okně **Kukátko.**

Ladicí program také přidá podřízený uzel **dynamického zobrazení** objektu do okna **Autos.** Chcete-li otevřít okno **Autos,** vyberte během ladění **možnost Ladění** > **automatických užitků****systému Windows** > .

**Dynamické zobrazení** také vylepšuje ladění objektů MODELU COM. Když ladicí program získá objekt COM zabalený v **souboru System.__ComObject**, přidá uzel **dynamického zobrazení** pro objekt.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Sledování jedné proměnné nebo výrazu pomocí funkce QuickWatch

**Pomocí funkce QuickWatch** můžete sledovat jednu proměnnou.

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

Chcete-li `a` pozorovat proměnnou,

1. Nastavte zarážku `a = a + b;` na řádku.

1. Začněte ladit. Spuštění pozastaví na zarážky.

1. Vyberte `a` proměnnou v kódu.

1. Vyberte **Možnost Ladění hodinek** > **Rychlé sledování ,** stiskněte **shift**+**F9**nebo klepněte pravým tlačítkem myši a vyberte **quickwatch**.

   Zobrazí se dialogové okno **Rychlé sledování.** Proměnná `a` je v poli **Výraz** s **hodnotou** **1**.

   ![Proměnná QuickWatch](../debugger/media/quickwatchvariable.png "Proměnná QuickWatch")

1. Chcete-li výraz vyhodnotit pomocí proměnné, `a + b` zadejte výraz, například do pole **Výraz,** a vyberte **Přehodnoťte**.

   ![Výraz QuickWatch](../debugger/media/quickwatchexpression.png "Výraz QuickWatch")

1. Chcete-li přidat proměnnou nebo výraz z **hodinek QuickWatch** do okna **Kukátko,** vyberte **Přidat hodinky**.

1. Vyberte **Zavřít,** chcete-li zavřít okno **QuickWatch.** **(QuickWatch** je modální dialog, takže nemůžete pokračovat v ladění, pokud je otevřen.)

1. Pokračujte v ladění. Můžete sledovat proměnnou v okně **kukátko.**

## <a name="see-also"></a>Viz také
- [Co je ladění?](../debugger/what-is-debugging.md)
- [Techniky ladění a související nástroje](../debugger/write-better-code-with-visual-studio.md)
- [První pohled na ladění](../debugger/debugger-feature-tour.md)
- [Okna ladicího programu](../debugger/debugger-windows.md)
