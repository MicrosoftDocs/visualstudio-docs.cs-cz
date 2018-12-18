---
title: Kontrolovat proměnné - okna Automatické hodnoty a místní hodnoty | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 10/18/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 584704471f9346611f240a3a24e0d45cf2eec364
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068351"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Kontrolovat proměnné v okně Automatické hodnoty a místní hodnoty

**Automatické hodnoty** a **lokální** windows zobrazovat hodnoty proměnných během ladění. Systému windows jsou k dispozici pouze během relace ladění. **Automatické hodnoty** okno zobrazuje proměnné používané kolem aktuálního zarážku. **Lokální** okno zobrazuje proměnné definované v místním rozsahem, což je obvykle aktuální funkci nebo metodu. Pokud je to poprvé, kterou jste se pokusili ladění kódu, můžete chtít číst [opravovat chyby napsáním lépe C# kód](../debugger/write-better-code-with-visual-studio.md) a [ladění pro naprosté začátečníky](../debugger/debugging-absolute-beginners.md) před provedením tohoto článku.

 **Automatické hodnoty** není k dispozici pro interval C#, kód jazyka Visual Basic, C++ a Python, ale ne pro JavaScript nebo F#.
  
Chcete-li otevřít **automatické hodnoty** okně během ladění, **ladění** > **Windows** > **automatické hodnoty**, nebo stisknutím klávesy **Ctrl**+**Alt**+**V** > **A**.  

Otevřete **lokální** okně během ladění, **ladění** > **Windows** > **lokální**, nebo stisknutím klávesy **Alt**+**4**.

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [vizualizace dat v sadě Visual Studio pro Mac](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Použití okna Automatické hodnoty a místní hodnoty

Pole a objekty zobrazit v **automatické hodnoty** a **lokální** windows jako ovládacích prvků strom. Vyberte šipku nalevo od názvu proměnné na Rozbalit zobrazení k zobrazení polí a vlastností. Tady je příklad <xref:System.IO.FileStream?displayProperty=fullName> objekt **místní hodnoty** okno:

![Lokální FileStream](../debugger/media/locals-filestream.png "FileStream místních hodnot")

Červená v **lokální** nebo **automatické hodnoty** okno znamená, že hodnota změnila od posledního vyhodnocení. Tato změna může být z předchozí ladicí relace, nebo proto, že změníte hodnotu v okně.

Výchozí číselného formátu v oknech ladicího programu je desetinné číslo. Chcete-li změnit ji do šestnáctkové soustavy, klikněte pravým tlačítkem **místní hodnoty** nebo **automatické hodnoty** okna a vyberte **hexadecimální zobrazení**. Tato změna ovlivní všechna okna ladicího programu.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Upravit hodnoty v okně Automatické hodnoty a lokální proměnné

K úpravě hodnot většiny proměnných v **automatické hodnoty** nebo **lokální** windows, klikněte dvakrát na hodnotu a zadejte novou hodnotu.

Výraz hodnoty, můžete zadat například `a + b`. Ladicí program přijímá nejvíce platné jazykové výrazy.

V nativním kódu C++ může být potřeba kvalifikovat kontext názvu proměnné. Další informace najdete v tématu [kontextový operátor (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Ujistěte se, že chápete důsledky před změnou hodnoty a výrazy. Jsou nějaké informace o možných problémech:
>
>-   Hodnocení některých výrazů může změnit hodnotu proměnné nebo jinak ovlivnit stav programu. Například vyhodnocení `var1 = ++var2` změní hodnotu obou `var1` a `var2`. Tyto výrazy se říká, že mají [vedlejší účinky](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Vedlejší účinky, může způsobit neočekávané výsledky, pokud si nejste vědomi.
>
>-   Úpravy hodnot s plovoucí desetinnou čárkou mohou díky převodu komponenty zlomku z desítkové do binární soustavy způsobit drobné nepřesnosti. I zdánlivě neškodné úpravy mohou způsobit změny některých bitů v proměnné s plovoucí desetinnou čárkou.

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Změna kontextu pro okno Automatické hodnoty nebo místních hodnot

Můžete použít **umístění ladění** nástrojů a vyberte požadované funkce, vlákna nebo procesu, která změní kontext **automatické hodnoty** a **lokální** systému windows.

Povolit **umístění ladění** nástrojů, klikněte na prázdnou část oblasti nástrojů a vyberte **umístění ladění** z rozevíracího seznamu, nebo vyberte **zobrazení**  >   **Panely nástrojů** > **umístění ladění**.

Nastavte zarážku a spusťte ladění. Při dosažení zarážky, pozastaví provádění zobrazíte umístění v **umístění ladění** nástrojů.

![Panel nástrojů umístění ladění](../debugger/media/debuglocationtoolbar.png "panelu nástrojů umístění ladění")

## <a name="bkmk_whatvariables"></a> Proměnné v okně Automatické hodnoty (C#, C++, Visual Basic, Python)

 Zobrazit jiné proměnné v jazycích různý kód **automatické hodnoty** okna.

 - V C# a Visual Basic **automatické hodnoty** v okně se zobrazí všechny proměnné použité v aktuální nebo předchozí řádku. Například v C# nebo Visual Basic code, deklarujte následující čtyři proměnné:

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

   Nastavit zarážku na řádku `c = 3;`, a spusťte ladicí program. Při pozastavení provádění **automatické hodnoty** okně se zobrazí:

   ![Automatické hodnoty CSharp](../debugger/media/autos-csharp.png "automatické hodnoty CSharp")

   Hodnota `c` je 0, protože řádku `c = 3` ještě nebyla spuštěna.

 - V jazyce C++ **automatické hodnoty** okně zobrazí proměnných použitých ve alespoň tři řádky před aktuálním řádkem, kde je spuštění pozastaveno. Například v kódu jazyka C++ deklarujte šest proměnné:

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

    Nastavit zarážku na řádku `e = 5;` a spustit ladicí program. Když se zastaví provádění **automatické hodnoty** okně se zobrazí:

    ![Automatické hodnoty C++](../debugger/media/autos-cplus.png "C++ automatické hodnoty")

    Proměnná `e` není inicializována, protože řádku `e = 5` ještě nebyla spuštěna.

##  <a name="bkmk_returnValue"></a> Zobrazení návratových hodnot volání metod
 V kódu rozhraní .NET a C++, může Kontrola návratových hodnot v **automatické hodnoty** okno při kroku přes nebo mimo volání metody. Volání metody zobrazení návratové hodnoty mohou být užitečné, když nejsou uloženy v místní proměnné. Metoda může použít jako parametr nebo jako návratové hodnoty metody jiné.

 Například následující C# kód přidá návratové hodnoty dvou funkcí:

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

Chcete-li zobrazit vrácené hodnoty `sumVars()` a `subtractVars()` volá metody v okně Automatické hodnoty:

1. Nastavit zarážku na `int x = sumVars(a, b) + subtractVars(c, d);` řádku.  
   
1. Spustit ladění a při spuštění, pozastavení na zarážce, vyberte **Krokovat s přeskočením** nebo stiskněte klávesu **F10**. Zobrazí se následující návratové hodnoty ve **automatické hodnoty** okno:  
   
  ![Automatické hodnoty vrátí hodnotu C# ](../debugger/media/autosreturnvaluecsharp2.png "automatické hodnoty vrátí hodnotuC#")  
  
## <a name="see-also"></a>Viz také:  
 [Co je ladění?](../debugger/what-is-debugging.md)  
 [Oprava chyb napsáním lépe C# kódu](../debugger/write-better-code-with-visual-studio.md)  
 [Nejdřív se podívejte na ladění](../debugger/debugger-feature-tour.md) [ladicího programu systému windows](../debugger/debugger-windows.md)
