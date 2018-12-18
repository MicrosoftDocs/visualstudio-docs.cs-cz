---
title: Nastavení sledování u proměnných | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 10/11/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 898c79f3985e24f52620f12dc25ad6044d05ac64
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059480"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Podívejte se na proměnných s oknech kukátka a Rychlé kukátko 

Při ladění, můžete použít **Watch** windows a **QuickWatch** sledovat proměnné a výrazy. Systému windows jsou k dispozici pouze během relace ladění.

**Sledování** windows můžete zobrazit několika proměnných v době během ladění. **QuickWatch** dialogové okno zobrazí jednu proměnnou najednou a musí být uzavřeny předtím, než můžete pokračovat v ladění.

Pokud je to poprvé, kterou jste se pokusili ladění kódu, můžete chtít číst [opravovat chyby napsáním lépe C# kód](../debugger/write-better-code-with-visual-studio.md) a [ladění pro naprosté začátečníky](../debugger/debugging-absolute-beginners.md) před provedením tohoto článku.

## <a name="observe-variables-with-a-watch-window"></a>Sledujte proměnné okno kukátka

Můžete otevřít více než jeden **Watch** okna a sledovat více než jednu proměnnou v **Watch** okna. 

Například nastavení sledování u hodnot typu `a`, `b`, a `c` v následujícím kódu:

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

1. Nastavit zarážku na `c = a + b;` řádek kliknutím na levý okraj výběru **ladění** > **Přepnout zarážku**, nebo stisknutím klávesy **F9**.
   
1. Spuštění ladění tak, že vyberete zelené **Start** šipku nebo **ladění** > **spustit ladění**, nebo stiskněte klávesu **F5**. Pozastaví spuštění na zarážce.
   
1. Otevřít **Watch** okna tak, že vyberete **ladění** > **Windows** > **Watch**  >   **Podívejte se na 1**, nebo stisknutím klávesy **Ctrl**+**Alt**+**W** > **1**.
   
   Můžete otevřít další **Watch** windows tak, že vyberete windows **2**, **3**, nebo **4**.
   
1. V **Watch** okna, vyberte prázdný řádek a proměnné typu `a`. Totéž proveďte pro `b` a `c`.
   
   ![Sledujte proměnné](../debugger/media/watchvariables.png "WatchVariables")
   
1. Pokračovat v ladění tak, že vyberete **ladění** > **Krokovat s vnořením** nebo stiskněte **F11** podle potřeby k přechodu. Hodnoty proměnné ve **Watch** okno změnit, protože iteraci `for` smyčky.
   
>[!NOTE]
>Pouze jazyka c++ 
>- Budete muset kvalifikovat kontext názvu proměnné nebo výraz, který používá název proměnné. Kontext je funkce, zdrojový soubor nebo modul, kde je umístěna proměnná. Pokud máte kvalifikovat kontext, použijte [kontextový operátor (C++)](../debugger/context-operator-cpp.md) syntaxe v poznámce **název** v **Watch** okna. 
>  
>- Můžete přidat názvy registrů a názvy proměnných pomocí  **$ \<zaregistrovat&nbsp;název >** nebo  **@ \<zaregistrovat&nbsp;name >** k **název** v **Watch** okna. Další informace najdete v tématu [Pseudoproměnné](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Použití výrazů v okně kukátko

Libovolný platný výraz rozpoznán v ladicím programu v můžete sledovat **Watch** okna.

Například kód v předchozí části, můžete získat průměrem tří hodnot tak, že zadáte `(a + b + c) / 3` v **Watch** okno:

![Výraz Watch](../debugger/media/watchexpression.png "výraz Watch")

Pravidla pro vyhodnocování výrazů v **Watch** okna jsou obvykle stejné jako pravidla pro vyhodnocování výrazů v kódu jazyka. Pokud výraz obsahuje chybu syntaxe, očekávejte ke stejné chybě kompilátoru stejně jako v editoru kódu. Například máte překlep v předcházejícího výrazu vytváří tuto chybu **Watch** okno:

![Podívejte se na Chyba výrazu](../debugger/media/watchexpressionerror.png "sledovat Chyba výrazu")

Kruh s ikonou dvě vlnovky se může vyskytovat **Watch** okno. Tato ikona znamená, že ladicí program nevyhodnocuje výraz z důvodu možných závislosti mezi vlákny. Vyhodnocení kódu vyžaduje další vlákna ve vaší aplikaci dočasně spustit, ale vzhledem k tomu, že jste v režimu přerušení, jsou obvykle Zastavit všechna vlákna ve vaší aplikaci. Umožňuje spustit dočasně jiných vláken může mít neočekávané účinky na stav aplikace a ladicí program může ignorovat události, například zarážky a výjimky na tato vlákna.

### <a name="bkmk_refreshWatch"></a> Aktualizace hodnot sledování

Ikona Aktualizovat (kruhovou šipku) se může objevit **Watch** okno při vyhodnocování výrazu. Ikona aktualizace označuje chybu nebo hodnotu, která je zastaralá. 

Pokud chcete aktualizovat hodnotu, vyberte ikonu aktualizace nebo stisknutím klávesy MEZERNÍK. Ladicí program se pokusí o opětovné vyhodnocení výrazu. Ale nechcete nebo moct opětovné vyhodnocení výrazu, v závislosti na tom, proč nebyl vyhodnocen hodnotu. 

Najeďte myší na ikonu aktualizace nebo se podívejte **hodnotu** sloupce z důvodu výraz nebyl vyhodnocen. Mezi důvody patří:

- Došlo k chybě, protože se právě vyhodnotit výraz, stejně jako v předchozím příkladu. Může dojít k vypršení časového limitu nebo proměnná může být mimo rozsah.
  
- Má výraz volání funkce, které může způsobit vedlejší účinek v aplikaci. Zobrazit [výraz vedlejší účinky](#bkmk_sideEffects).
  
- Je zakázané automatické hodnocení vlastností a implicitních volání funkcí. 
  
Pokud na ikonu aktualizace se zobrazí, protože automatické hodnocení vlastností a volání implicitní funkce je zakázaná, můžete ji povolit tak, že vyberete **povolit vyhodnocování vlastností a jiných implicitních volání funkcí** v **nástroje**   >  **Možnosti** > **ladění** > **Obecné**.

Demonstruje použití na ikonu aktualizace:

1. V **nástroje** > **možnosti** > **ladění** > **Obecné**, zrušte **Povolit vyhodnocování vlastností a jiných implicitních volání funkcí** zaškrtávací políčko. 
   
1. Zadejte následující kód a **Watch** okně Nastavení sledování u `list.Count` vlastnost. 
   
   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```
   
1. Spusťte ladění. **Watch** okno zobrazuje něco jako následující zpráva:
   
   ![Aktualizovat Watch](../debugger/media/refreshwatch.png "aktualizovat Watch")
   
1. Pokud chcete aktualizovat hodnotu, vyberte ikonu aktualizace nebo stisknutím klávesy MEZERNÍK. Ladicí program přehodnotí výraz. 

### <a name="bkmk_sideEffects"></a> Výraz vedlejší účinky 

Hodnocení některých výrazů může změnit hodnotu proměnné nebo jinak ovlivnit stav vaší aplikace. Například vyhodnocení následujícího výrazu změní hodnotu `var1`:

```csharp
var1 = var2
```

Tento kód může způsobit, že [vedlejší účinek](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Vedlejší efekty můžou ztížit ladění tak, že změníte způsob, jakým vaše aplikace funguje.

Výraz s vedlejšími účinky se vyhodnotí pouze jednou, při prvním zadání. Potom výraz se zobrazí šedě ve **Watch** okna a další hodnocení jsou zakázána. Popisek nebo **hodnotu** sloupec vysvětluje, že výraz způsobuje vedlejší účinek. Opětovného hodnocení můžete vynutit tak, že vyberete ikonu aktualizace, které se zobrazí vedle hodnoty.

Chcete-li vypnout automatické vyhodnocování funkcí je jedním ze způsobů, aby se zabránilo označení vedlejší účinky. V **nástroje** > **možnosti** > **ladění** > **Obecné**, zrušte zaškrtnutí možnosti **Povolit vyhodnocování vlastností a jiných implicitních volání funkcí**.

Pro C# pouze při hodnocení vlastnosti nebo implicitních volání funkcí je vypnutý, můžete vynutit hodnocení tak, že přidáte **ac** modifikátor formátu proměnné **název** v **Watch**  okna. Zobrazit [v jazyce C# specifikátory formátu](../debugger/format-specifiers-in-csharp.md).

## <a name="bkmk_objectIds"></a> Pomocí ID objektů v okně kukátko (C# a Visual Basic)

Někdy budete chtít sledovat chování s určitým objektem. Můžete například chtít sledovat objekt odkazuje místní proměnné po této proměnné je nepřejdou mimo rozsah. V C# a Visual Basic, můžete vytvořit ID objektů pro konkrétní instance typů odkazů a používat **Watch** okno a podmínky zarážky. ID objektu je generována modulem common language runtime (CLR) ladění služeb a přidružená k objektu.

> [!NOTE]
> ID objektů vytvořit slabé odkazy, které není brání objekt uvolněn z paměti. Jsou platné pouze pro aktuální relaci ladění.

V následujícím kódu `MakePerson()` metoda vytvoří `Person` pomocí lokální proměnné: 

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

Chcete zjistit název `Person` v `DoSomething()` metodu, můžete přidat odkaz na `Person` ID objektu v **Watch** okna.

1. Nastavte zarážku v kódu po `Person` objekt se vytvořil.
   
1. Spusťte ladění.
   
1. Při spuštění, pozastavení na zarážce, otevřete **lokální** okno výběrem **ladění** > **Windows** > **místníchhodnot**.
   
1. V **lokální** okna, klikněte pravým tlačítkem na `Person` proměnné a vyberte **Ujistěte se, ID objektu**.
   
   Měli byste vidět znak dolaru (**$**) plus číslo v **lokální** okna, která je ID objektu.
   
1. Přidat ID objektu **Watch** okna tak, že kliknete pravým tlačítkem ID objektu a vyberete **Přidat kukátko**.
   
1. Nastavte další zarážku `DoSomething()` metody.
   
1. Pokračujte v ladění. Při pozastavení provádění v `DoSomething()` metody **Watch** v okně se zobrazí `Person` objektu.
   
   > [!NOTE]
   > Pokud chcete zobrazit vlastnosti objektu, například `Person.Name`, je nutné povolit vyhodnocování vlastností tak, že vyberete **nástroje** > **možnosti**  >   **Ladění** > **Obecné** > **povolit vyhodnocování vlastností a jiných implicitních volání funkcí**.

## <a name="dynamic-view-and-the-watch-window"></a>Dynamické zobrazení a okno kukátka

Použít dynamické některé skriptovací jazyky (například JavaScript nebo Python) nebo [duck](https://en.wikipedia.org/wiki/Duck_typing) zadáním a rozhraní .NET verze 4.0 a novější podporuje objekty, které je obtížné sledovat v normální ladění systému windows.

**Watch** okno zobrazí tyto objekty dynamických objektů, které jsou vytvořeny z typů, které implementují <xref:System.Dynamic.IDynamicMetaObjectProvider> rozhraní. Dynamický objekt zobrazit dynamičtí členové dynamické objekty, ale nepovolit úpravy hodnot členů. 

Chcete-li aktualizovat **dynamického zobrazení** hodnot, vyberte [ikonu aktualizace](#bkmk_refreshWatch) vedle uzlu dynamický objekt. 

K zobrazení pouze **dynamického zobrazení** objektu, přidejte **dynamické** specifikátor formátu za názvem dynamický objekt v **Watch** okno:

- Pro jazyk C#: `ObjectName, dynamic`
- V jazyce Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- C# Ladicí program nebude automaticky přehodnotit hodnoty **dynamického zobrazení** po kroku na další řádek kódu. 
>- Visual Basic ladicí program automaticky aktualizuje výrazy přidané prostřednictvím **dynamického zobrazení**.
>- Vyhodnocování členů **dynamického zobrazení** může mít [vedlejší účinky](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). 

**Vložit nové kukátko. proměnné, která přetypovává objekt na dynamický objekt:**
  
1. Klikněte pravým tlačítkem na podřízený uzel **dynamického zobrazení**.
1. Zvolte **Přidat kukátko**. `object.name` Stane `((dynamic) object).name` a zobrazí se v novém **Watch** okna.

Ladicí program se taky přidaly **dynamického zobrazení** podřízený uzel objekt, který má **automatické hodnoty** okna. Chcete-li otevřít **automatické hodnoty** okně během ladění, **ladění** > **Windows** > **automatické hodnoty**. 

**Dynamické zobrazení** také zlepšuje ladění pro objekty COM. Pokud ladicí program získá objekt modelu COM, který je obalen **System.__ComObject**, přidá **dynamického zobrazení** uzlu pro objekt.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Podívejte se jednu proměnnou nebo výraz s QuickWatch

Můžete použít **QuickWatch** dodržovat jednu proměnnou. 

Například následující kód:

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

Sledovat `a` proměnné 
   
1. Nastavit zarážku na `a = a + b;` řádku.
   
1. Spusťte ladění. Pozastaví spuštění na zarážce.
   
1. Vyberte proměnnou `a` v kódu.
   
1. Vyberte **ladění** > **QuickWatch**, stiskněte klávesu **Shift**+**F9**, nebo klikněte pravým tlačítkem a vyberte **QuickWatch**. 
   
   **QuickWatch** se zobrazí dialogové okno. `a` Proměnná je v **výraz** pole s **hodnotu** z **1**.
   
   ![Rychlé kukátko proměnné](../debugger/media/quickwatchvariable.png "proměnné QuickWatch")
   
1. Vyhodnotit výraz, který používá proměnné, zadejte výraz `a + b` v **výraz** a vyberte **přehodnotit**.
   
   ![Výraz QuickWatch](../debugger/media/quickwatchexpression.png "výrazu v QuickWatch")
   
1. Přidání proměnné nebo výrazu z **QuickWatch** k **Watch** okně **Přidat kukátko**.
   
1. Vyberte **zavřete** zavřete **QuickWatch** okna. (**QuickWatch** je modální dialogové okno, takže nemůže pokračovat, ladění, jako je otevřený.)
   
1. Pokračujte v ladění. Můžete sledovat v proměnné **Watch** okna.

## <a name="see-also"></a>Viz také:
 [Co je ladění?](../debugger/what-is-debugging.md)  
 [Oprava chyb napsáním lépe C# kódu](../debugger/write-better-code-with-visual-studio.md)  
 [Nejdřív se podívejte na ladění](../debugger/debugger-feature-tour.md) [ladicího programu systému windows](../debugger/debugger-windows.md)
