---
title: Nastavení sledování proměnných | Microsoft Docs
ms.custom: seodec18
ms.date: 10/11/2018
ms.topic: how-to
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
ms.openlocfilehash: d7e2a05fe84b023a60ef75f0cb262a08fc02587a
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727421"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Sledujte proměnné pomocí oken kukátka a QuickWatch

Při ladění můžete ke sledování proměnných a výrazů použít **kukátka** Windows a **QuickWatch** . Okna jsou k dispozici pouze během relace ladění.

Okna **kukátka** může během ladění zobrazit několik proměnných současně. Dialog **QuickWatch** zobrazuje jednu proměnnou najednou a před pokračováním ladění musí být zavřen.

> [!NOTE]
> Pokud se jedná o první pokus o ladění kódu, můžete si před tím, než projdete Tento článek, přečíst [ladění pro naprostou začátečníky](../debugger/debugging-absolute-beginners.md) a [techniky a nástroje pro ladění](../debugger/write-better-code-with-visual-studio.md) .

## <a name="observe-variables-with-a-watch-window"></a>Sledování proměnných pomocí okno Kukátko

Můžete otevřít více než jedno okno **kukátka** a sledovat více než jednu proměnnou v okně **kukátko** .

Například pro nastavení kukátka pro hodnoty `a` , `b` a `c` v následujícím kódu:

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

1. Nastavte zarážku na `c = a + b;` řádku kliknutím na levý okraj, výběrem možnosti **ladit**  >  **přepínací zarážku** nebo stisknutím klávesy **F9**.

1. **Spusťte ladění** tak, že vyberete zelenou šipku **Start** nebo  >  **spustíte ladění**, nebo stisknete klávesu **F5**. Spuštění pozastaví na zarážce.

1. Otevřete okno **kukátka** výběrem možnosti **ladit**  >    >  **kukátko** kukátko  >  **1** nebo stisknutím **kombinace kláves CTRL** + **+** + **W**  >  **1**.

   Můžete otevřít další okna **kukátka** tak, že vyberete Windows **2**, **3** nebo **4**.

1. V okně **kukátko** vyberte prázdný řádek a zadejte proměnnou `a` . Proveďte stejné pro `b` a `c` .

   ![Sledování proměnných](../debugger/media/watchvariables.png "WatchVariables")

1. Pokračujte v ladění výběrem možnosti **ladit**  >  **Krok do** nebo stisknutím klávesy **F11** podle potřeby. Hodnoty proměnných v okně **kukátka** se při iteraci `for` smyčkou mění.

>[!NOTE]
>Pouze pro C++,
>- Možná budete muset kvalifikovat kontext názvu proměnné nebo výrazu, který používá název proměnné. Kontext je funkce, zdrojový soubor nebo modul, kde je umístěna proměnná. Pokud je nutné kvalifikovat kontext, použijte syntaxi [operátoru Context (C++)](../debugger/context-operator-cpp.md) v **názvu** v okně **kukátko** .
>
>- Názvy registrů a názvy proměnných můžete přidat pomocí **$\<register&nbsp;name>** nebo **@\<register&nbsp;name>** k **názvu** v okně **kukátka** . Další informace najdete v tématu [Pseudoproměnné](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Použití výrazů v okno Kukátko

Můžete sledovat libovolný platný výraz rozpoznaný ladicím programem v okně **kukátka** .

Například pro kód v předchozí části můžete získat průměr tří hodnot zadáním `(a + b + c) / 3` v okně **kukátko** :

![Výraz kukátka](../debugger/media/watchexpression.png "Výraz kukátka")

Pravidla pro vyhodnocování výrazů v okně **kukátka** jsou obecně stejná jako pravidla pro vyhodnocení výrazů v jazyce kódu. Pokud má výraz syntaktickou chybu, očekávat stejnou chybu kompilátoru jako v editoru kódu. Například překlep v předchozím výrazu vytvoří tuto chybu v okně **kukátko** :

![Chyba kukátka výrazu](../debugger/media/watchexpressionerror.png "Chyba kukátka výrazu")

V okně **kukátka** se může zobrazit kolečko se dvěma ikonami vlnité čáry. Tato ikona znamená, že ladicí program nevyhodnotí výraz z důvodu potenciální závislosti mezi vlákny. Vyhodnocení kódu vyžaduje, aby další vlákna ve vaší aplikaci běžela dočasně, ale vzhledem k tomu, že jste v režimu přerušení, jsou obvykle zastavena všechna vlákna ve vaší aplikaci. Umožnění dočasného spuštění jiných vláken může mít neočekávané účinky na stav aplikace a ladicí program může ignorovat události, jako jsou zarážky a výjimky v těchto vláknech.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Hledat v okno Kukátko

Klíčová slova můžete hledat ve sloupcích název, hodnota a typ okna **kukátka** pomocí panelu hledání nad každým oknem. Pro spuštění hledání stiskněte klávesu ENTER nebo vyberte jednu ze šipek. Probíhající hledání zrušíte tak, že na panelu hledání vyberete ikonu "x".

Použijte šipky vlevo a vpravo (SHIFT + F3 a F3) k navigaci mezi nalezenými shodami.

![Hledat v okně kukátka](../debugger/media/ee-search-watch.png "Hledat v okně kukátka")

Chcete-li prohledávat více nebo méně důkladné výsledky, použijte rozevírací seznam **Hledat** v horní části okna **kukátka** a vyberte, kolik úrovní na hloubku chcete prohledávat vnořené objekty. 

## <a name="pin-properties-in-the-watch-window"></a>Připnout vlastnosti v okno Kukátko

>[!NOTE]
> Tato funkce je podporována v rozhraní .NET Core 3,0 nebo vyšším.

Pomocí nástroje **Pinnable Properties** můžete rychle zkontrolovat objekty podle jejich vlastností v okno kukátko.  Chcete-li použít tento nástroj, najeďte myší na vlastnost a vyberte ikonu připnutí, která se zobrazí, nebo klikněte pravým tlačítkem myši a v výsledné místní nabídce vyberte možnost **připnout člena jako oblíbenou** .  Tato vlastnost se zobrazí v horní části seznamu vlastností objektu a název vlastnosti a hodnota se zobrazí ve sloupci **hodnota** .  Chcete-li odebrat vlastnost, vyberte ikonu připnutí znovu nebo v místní nabídce vyberte možnost **odepnout člen jako oblíbenou** .

![Připnout vlastnosti v okno Kukátko](../debugger/media/basic-pin-watch.gif "Připnout vlastnosti v okno Kukátko")

Můžete také přepínat názvy vlastností a odfiltrovat připnuté vlastnosti při zobrazení seznamu vlastností objektu v okno kukátko.  Obě možnosti získáte tak, že vyberete tlačítka na panelu nástrojů nad oknem kukátko.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a> Aktualizovat hodnoty sledování

Když se vyhodnotí výraz, může se v okně **kukátka** zobrazit ikona aktualizace (KRUHOVÁ ŠIPKA). Ikona aktualizovat označuje chybu nebo neaktuální hodnotu.

Chcete-li aktualizovat hodnotu, vyberte ikonu aktualizace nebo stiskněte klávesu MEZERNÍK. Ladicí program se pokusí znovu vyhodnotit výraz. V závislosti na tom, proč nebyla hodnota vyhodnocena, však pravděpodobně nebudete chtít nebo nebude možné výraz vyhodnotit.

Najeďte myší na ikonu aktualizace nebo zobrazte sloupec **hodnota** pro důvod, proč výraz nebyl vyhodnocen. Důvody zahrnují:

- Při vyhodnocování výrazu, jako v předchozím příkladu, došlo k chybě. Může dojít k vypršení časového limitu nebo může být proměnná mimo rozsah.

- Výraz obsahuje volání funkce, které může aktivovat vedlejší efekt v aplikaci. Podívejte se na [vedlejší účinky výrazu](#bkmk_sideEffects).

- Automatické vyhodnocení vlastností a volání implicitních funkcí je zakázáno.

Pokud se zobrazí ikona aktualizace, protože automatické vyhodnocení vlastností a volání implicitních funkcí je zakázané, můžete je povolit výběrem **možnosti Povolit vyhodnocování vlastností a jiných implicitních volání funkcí** v části **nástroje**  >    >  **ladění**–  >  **Obecné**.

Ukázka použití ikony aktualizace:

1. V části **nástroje**  >  **Možnosti**  >  **ladění**  >  **Obecné** zrušte zaškrtnutí políčka **Povolit vyhodnocování vlastností a další implicitní volání funkce** .

1. Zadejte následující kód a v okně **kukátko** nastavte kukátko pro `list.Count` vlastnost.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Spuštění ladění Okno **kukátka** zobrazuje něco podobného jako následující zpráva:

   ![Aktualizovat kukátko](../debugger/media/refreshwatch.png "Aktualizovat kukátko")

1. Chcete-li aktualizovat hodnotu, vyberte ikonu aktualizace nebo stiskněte klávesu MEZERNÍK. Ladicí program znovu vyhodnotí výraz.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a> Vedlejší efekty výrazu

Hodnocení některých výrazů může změnit hodnotu proměnné nebo jinak ovlivnit stav aplikace. Například vyhodnocení následujícího výrazu změní hodnotu `var1` :

```csharp
var1 = var2
```

Tento kód může způsobit [vedlejší efekt](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Vedlejší účinky můžou ztížit ladění změnou způsobu, jakým vaše aplikace funguje.

Výraz s vedlejšími účinky je vyhodnocen pouze jednou při prvním zadání. Po tomto výrazu se výraz zobrazí šedě v okně **kukátka** a další hodnocení jsou zakázána. Sloupec ToolTip nebo **Value** vysvětluje, že výraz způsobuje vedlejší efekt. Opětovné vyhodnocení můžete vynutit tak, že vyberete ikonu aktualizace, která se zobrazí vedle hodnoty.

Jedním ze způsobů, jak zabránit označení vedlejších účinků, je vypnout automatické vyhodnocení funkcí. V **nabídce nástroje**  >  **Možnosti**  >  **ladění**  >  **Obecné**, zrušte zaškrtnutí políčka **Povolit vyhodnocování vlastností a dalších implicitních volání funkcí**.

Pouze pro C#, pokud je vyhodnocování vlastností nebo implicitních volání funkcí vypnuto, můžete vynutit vyhodnocení přidáním modifikátoru formátu **AC** k **názvu** proměnné v okně **kukátko** . Viz [specifikátory formátu v jazyce C#](../debugger/format-specifiers-in-csharp.md).

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a> Použití ID objektů v okno Kukátko (C# a Visual Basic)

Někdy budete chtít pozorovat chování určitého objektu. Například můžete chtít sledovat objekt, na který odkazuje místní proměnná poté, co tato proměnná dokončí mimo rozsah. V jazyce C# a Visual Basic můžete vytvořit ID objektů pro konkrétní instance odkazů a použít je v okně **kukátka** a v podmínkách zarážek. ID objektu je vygenerováno službami ladění modulu CLR (Common Language Runtime) a přidruženy k objektu.

> [!NOTE]
> ID objektů vytvářejí slabé odkazy, které nebrání vyshromažďování paměti objektu. Jsou platné pouze pro aktuální relaci ladění.

V následujícím kódu `MakePerson()` Metoda vytvoří `Person` pomocí místní proměnné:

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

Chcete-li zjistit název `Person` v `DoSomething()` metodě, můžete přidat odkaz na `Person` ID objektu v okně **kukátko** .

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
