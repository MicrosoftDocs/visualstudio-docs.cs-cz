---
title: Kontrola proměnných – okna auto a místní hodnoty | Microsoft Docs
description: Prozkoumejte proměnné v oknech automatické hodnoty a místní hodnoty při ladění v aplikaci Visual Studio. Okna Automatické hodnoty a místní hodnoty zobrazují hodnoty proměnných při ladění.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/18/2018
ms.topic: how-to
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b57c27d038193a5c73bee48814a2aa457a94b6a6
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/24/2020
ms.locfileid: "97760910"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Kontrola proměnných v oknech automatické hodnoty a místní hodnoty

Okna **Automatické** hodnoty a **místní** hodnoty zobrazují hodnoty proměnných při ladění. Okna jsou k dispozici pouze během relace ladění. Okno **Automatické** hodnoty zobrazuje proměnné používané kolem aktuální zarážky. Okno **místní** hodnoty zobrazuje proměnné definované v místním oboru, což je obvykle aktuální funkce nebo metoda.

> [!NOTE]
> Pokud se jedná o první pokus o ladění kódu, můžete si před tím, než projdete Tento článek, přečíst [ladění pro naprostou začátečníky](../debugger/debugging-absolute-beginners.md) a [techniky a nástroje pro ladění](../debugger/write-better-code-with-visual-studio.md) .

 Okno **Automatické** hodnoty je k dispozici pro kód C#, Visual Basic, C++ a Python, ale ne pro JavaScript nebo F #.

Chcete-li otevřít okno **Automatické** hodnoty, vyberte možnost **ladit**  >  **Windows**  >  **Autos** nebo stiskněte kombinaci kláves **CTRL** + **ALT** + **V**  >  **a**.

Chcete-li otevřít okno **místních** hodnot, při ladění vyberte možnost **ladit**  >    >  **místní prostředí** systému Windows nebo stiskněte klávesu **ALT** + **4**.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [vizualizace dat v Visual Studio pro Mac](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Použití oken automatické hodnoty a místní hodnoty

Pole a objekty se zobrazí v oknech **Automatické** hodnoty a **místní** hodnoty jako stromové ovládací prvky. Výběrem šipky vlevo od názvu proměnné rozbalíte zobrazení a zobrazíte pole a vlastnosti. Tady je příklad <xref:System.IO.FileStream?displayProperty=fullName> objektu v okně **místních** hodnot:

![Snímek obrazovky okna místních hodnot se souborem nastaveným na hodnotu System. IO. FileStream.](../debugger/media/locals-filestream.png)

Červená hodnota v okně **místní** hodnoty nebo **Automatické** hodnoty znamená, že se od posledního vyhodnocení změnila hodnota. Tato změna může být z předchozí relace ladění, nebo vzhledem k tomu, že jste změnili hodnotu v okně.

Výchozí číselný formát v oknech ladicího programu je Decimal. Pokud ho chcete změnit na hexadecimální, klikněte pravým tlačítkem myši v okně **místní** hodnoty nebo **Automatické** hodnoty a vyberte **hexadecimální zobrazení**. Tato změna ovlivní všechna okna ladicího programu.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Upravit hodnoty proměnných v okně Automatické hodnoty nebo místní hodnoty

Chcete-li upravit hodnoty většiny proměnných v oknech **Automatické** hodnoty nebo **místní** hodnoty, dvakrát klikněte na hodnotu a zadejte novou hodnotu.

Můžete například zadat výraz pro hodnotu `a + b` . Ladicí program přijímá nejvíce platné jazykové výrazy.

V nativním kódu jazyka C++ bude pravděpodobně nutné kvalifikovat kontext názvu proměnné. Další informace naleznete v tématu [kontext operátoru (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Před změnou hodnot a výrazů se ujistěte, že rozumíte důsledkům. Mezi možné problémy patří:
>
>- Hodnocení některých výrazů může změnit hodnotu proměnné nebo jinak ovlivnit stav programu. Například vyhodnocení `var1 = ++var2` změn hodnoty `var1` a `var2` . Tyto výrazy jsou označeny tak, aby měly [vedlejší účinky](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Vedlejší účinky můžou způsobit neočekávané výsledky, pokud je neznáte.
>
>- Úpravy hodnot s plovoucí desetinnou čárkou mohou díky převodu komponenty zlomku z desítkové do binární soustavy způsobit drobné nepřesnosti. I zdánlivě neškodné úpravy můžou způsobit změny některých bitů v proměnné s plovoucí desetinnou čárkou.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-autos-or-locals-window"></a>Hledání v okně Automatické hodnoty nebo místní hodnoty

Klíčová slova můžete vyhledat ve sloupcích název, hodnota a typ okna **Automatické** hodnoty nebo **místní** hodnoty pomocí panelu hledání nad jednotlivými oknem. Pro spuštění hledání stiskněte klávesu ENTER nebo vyberte jednu ze šipek. Probíhající hledání zrušíte tak, že na panelu hledání vyberete ikonu "x".

Použijte šipky vlevo a vpravo (SHIFT + F3 a F3) k navigaci mezi nalezenými shodami.

![Hledat v okně místních hodnot](../debugger/media/ee-search-locals.png "Hledat v okně místních hodnot")

Chcete-li prohledávat více nebo méně důkladné výsledky, použijte rozevírací seznam **Hledat** v horní části okna **Automatické** hodnoty nebo **místní** okno a vyberte, kolik úrovní hloubky chcete vyhledat ve vnořených objektech. 

## <a name="pin-properties-in-the-autos-or-locals-window"></a>Vlastnosti PIN kódu v okně Automatické hodnoty nebo místní hodnoty

> [!NOTE]
> Tato funkce je podporovaná pro .NET Core 3,0 nebo vyšší.

Pomocí nástroje **Pinnable Properties** můžete rychle zkontrolovat objekty podle jejich vlastností v oknech automatické hodnoty a místní hodnoty.  Chcete-li použít tento nástroj, najeďte myší na vlastnost a vyberte ikonu připnutí, která se zobrazí, nebo klikněte pravým tlačítkem myši a v výsledné místní nabídce vyberte možnost **připnout člena jako oblíbenou** .  Tato vlastnost se zobrazí v horní části seznamu vlastností objektu a název vlastnosti a hodnota se zobrazí ve sloupci **hodnota** .  Chcete-li odebrat vlastnost, vyberte ikonu připnutí znovu nebo v místní nabídce vyberte možnost **odepnout člen jako oblíbenou** .

![Připnutí vlastností v okně místních hodnot](../debugger/media/basic-pin.gif "Připnutí vlastností v okně místních hodnot")

Při zobrazení seznamu vlastností objektu v oknech automatické hodnoty nebo místní hodnoty můžete také přepínat názvy vlastností a odfiltrovat připnuté vlastnosti.  Jednotlivé možnosti získáte tak, že vyberete tlačítka na panelu nástrojů nad okny automatické hodnoty nebo místní okna.

![Filtrovat oblíbené vlastnosti](../debugger/media/filter-pinned-properties-locals.png "Filtrovat oblíbené vlastnosti") 
 ![Přepnout názvy vlastností](../debugger/media/toggle-property-names.gif "Přepnout názvy vlastností")

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Změna kontextu okna Automatické hodnoty nebo místní hodnoty

Můžete použít panel nástrojů **umístění ladění** k výběru požadované funkce, vlákna nebo procesu, který změní kontext pro okna **Automatické** hodnoty a **místní** hodnoty.

Chcete-li povolit panel nástrojů **umístění ladění** , klikněte do prázdné části oblasti panelu nástrojů a vyberte možnost **umístění ladění** z rozevíracího seznamu nebo vyberte možnost **Zobrazit**  >  **panely nástrojů**  >  **umístění ladění**.

Nastavte zarážku a spusťte ladění. Při dosažení zarážky se spuštění pozastaví a uvidíte umístění na panelu nástrojů **umístění ladění** .

![panel nástrojů Ladit umístění](../debugger/media/debuglocationtoolbar.png "panel nástrojů Ladit umístění")

## <a name="variables-in-the-autos-window-c-c-visual-basic-python"></a><a name="bkmk_whatvariables"></a> Proměnné v okně Automatické hodnoty (C#, C++, Visual Basic, Python)

Různé jazyky kódu zobrazují různé proměnné v okně **Automatické** hodnoty.

- V jazyce C# a Visual Basic okno **Automatické** hodnoty zobrazuje jakoukoli proměnnou použitou na aktuálním nebo předchozím řádku. Například v kódu C# nebo Visual Basic deklarujte následující čtyři proměnné:

   ```csharp
       public static void Main()
       {
          int a, b, c, d;
          a = 1;
          b = 2;
          c = 3;
          d = 4;
       }
   ```

   Nastavte zarážku na řádku `c = 3;` a spusťte ladicí program. Po pozastavení provádění se zobrazí okno **Automatické** hodnoty:

   ![Snímek obrazovky okna Automatické hodnoty s hodnotou c nastavenou na 0.](../debugger/media/autos-csharp.png)

   Hodnota `c` je 0, protože řádek `c = 3` ještě nebyl spuštěn.

- V jazyce C++ okno **Automatické** hodnoty zobrazuje proměnné používané v alespoň třech řádcích před aktuálním řádkem, kde je provádění pozastaveno. Například v kódu jazyka C++ deklarujte šest proměnných:

   ```C++
       void main() {
           int a, b, c, d, e, f;
           a = 1;
           b = 2;
           c = 3;
           d = 4;
           e = 5;
           f = 6;
       }
   ```

    Nastavte zarážku na řádku `e = 5;` a spusťte ladicí program. Po zastavení spuštění se zobrazí okno **Automatické** hodnoty:

    ![Snímek obrazovky okna Automatické hodnoty se zvýrazněným řádkem, který zobrazuje int c s hodnotou 3](../debugger/media/autos-cplus.png)

    Proměnná `e` není inicializovaná, protože řádek `e = 5` ještě nebyl spuštěn.

## <a name="view-return-values-of-method-calls"></a><a name="bkmk_returnValue"></a> Zobrazit návratové hodnoty volání metody
 V kódu .NET a C++ můžete v okně **Automatické** hodnoty kontrolovat návratové hodnoty při krokování nebo odvolání metody. Návratové hodnoty volání metody mohou být užitečné, pokud nejsou uloženy v místních proměnných. Metodu lze použít jako parametr nebo jako návratovou hodnotu jiné metody.

 Například následující kód jazyka C# přidá návratové hodnoty dvou funkcí:

```csharp
static void Main(string[] args)
{
    int a, b, c, d;
    a = 1;
    b = 2;
    c = 3;
    d = 4;
    int x = sumVars(a, b) + subtractVars(c, d);
}

private static int sumVars(int i, int j)
{
    return i + j;
}

private static int subtractVars(int i, int j)
{
    return j - i;
}
```

Chcete-li zobrazit návratové hodnoty `sumVars()` `subtractVars()` volání metody a v okně Automatické hodnoty:

1. Nastavte zarážku na `int x = sumVars(a, b) + subtractVars(c, d);` řádku.

1. Spustit ladění a když se spuštění pozastaví na zarážce, vyberte **Krok přes** nebo stiskněte **F10**. V okně **Automatické** hodnoty by se měly zobrazit následující návratové hodnoty:

  ![Automatické návratové hodnoty v jazyce C #](../debugger/media/autosreturnvaluecsharp2.png "Automatické návratové hodnoty v jazyce C #")

## <a name="see-also"></a>Viz také

- [Co je ladění?](../debugger/what-is-debugging.md)
- [Techniky ladění a související nástroje](../debugger/write-better-code-with-visual-studio.md)
- [První pohled na ladění](../debugger/debugger-feature-tour.md)
- [Okna ladicího programu](../debugger/debugger-windows.md)
