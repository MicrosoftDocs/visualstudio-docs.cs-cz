---
title: Okna Automatické hodnoty a místní hodnoty | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.autos
- vs.debug.locals
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 261c0c0bd8b48634c8d24d56ee4df7ea3bbcf135
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161765"
---
# <a name="autos-and-locals-windows"></a>Okna automatických a místních hodnot
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno **Automatické** hodnoty (při ladění, **CTRL + ALT + v, a**nebo **Debug/Windows/Autos**) a okno **místních** hodnot (při ladění, **CTRL + ALT + v, L**nebo **Debug/Windows**) jsou poměrně užitečné, pokud chcete při ladění zobrazit hodnoty proměnných. V okně **místní** hodnoty jsou zobrazeny proměnné, které jsou definovány v místním oboru, což je obvykle funkce nebo metoda, která je právě prováděna. Okno **Automatické** hodnoty zobrazuje proměnné používané kolem aktuálního řádku (místo, kde je ladicí program zastavený). Přesně zobrazené proměnné se liší v různých jazycích. Podívejte se, jaké proměnné se zobrazí v okně Automatické hodnoty? psán.  
  
 Pokud potřebujete další informace o základním ladění, přečtěte si téma [Začínáme s ladicím programem](../debugger/getting-started-with-the-debugger.md).  
  
## <a name="looking-at-objects-in-the-autos-and-locals-windows"></a>Prohlížení objektů v oknech automatické hodnoty a místní hodnoty  
 Pole a objekty se zobrazí v oknech automatické hodnoty a místní hodnoty jako stromové ovládací prvky. Kliknutím na šipku nalevo od názvu proměnné rozbalíte zobrazení a zobrazíte pole a vlastnosti. Tady je příklad <xref:System.IO.FileStream> objektu v okně **místních** hodnot:  
  
 ![Místní&#45;FileStream](../debugger/media/locals-filestream.png "Lokální hodnoty – FileStream")  
  
## <a name="what-variables-appear-in-the-autos-window"></a>Jaké proměnné se zobrazí v okně Automatické hodnoty?  
 Můžete použít okno **Automatické** hodnoty v kódu C#, Visual Basic a C++. Okno **Automatické** hodnoty nepodporuje jazyk JavaScript ani F #.  
  
 V jazyce C# a Visual Basic okno **Automatické** hodnoty zobrazuje jakoukoli proměnnou použitou na aktuálním nebo předchozím řádku. Například pokud deklarujete čtyři proměnné a nastavíte je takto:  
  
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
  
 Pokud nastavíte zarážku na řádku `c = 3` a spustíte ladicí program, dojde při spuštění k zastavení okna **Automatické** hodnoty takto:  
  
 ![Automatické&#45;CSharp](../debugger/media/autos-csharp.png "Automatické hodnoty – CSharp")  
  
 Všimněte si, že hodnota `c` je 0, protože řádek `c = 3` ještě nebyl spuštěn.  
  
 V jazyce C++ okno **Automatické** hodnoty zobrazuje proměnné použité alespoň tři řádky před aktuálním řádkem (řádek, ve kterém je spuštění zastaveno). Pokud deklarujete šest proměnných:  
  
```cpp  
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
  
 Pokud nastavíte zarážku na řádku `e = 5;` a spustíte ladicí program, bude při spuštění zastaveno okno **Automatické** hodnoty, které bude vypadat takto:  
  
 ![Automatické&#45;cplus](../debugger/media/autos-cplus.png "Automatické hodnoty – cplus")  
  
 Všimněte si, že proměnná e je neinicializovaná, protože kód na řádku `e = 5;` ještě nebyl spuštěn.  
  
 V některých případech můžete také zobrazit vrácené hodnoty funkcí a metod. Viz [zobrazení návratových hodnot volání metody](#bkmk_returnValue) níže.  
  
## <a name="view-return-values-of-method-calls"></a><a name="bkmk_returnValue"></a> Zobrazit návratové hodnoty volání metody  
 V kódu .NET a C++ lze kontrolovat návratové hodnoty při krokování nebo volání metody. Tato funkce je užitečná v případě, že výsledek volání metody není uložen v místní proměnné, například když je metoda použita jako parametr nebo jako návratová hodnota jiné metody.  
  
 Následující kód jazyka C# přidá návratové hodnoty dvou funkcí:  
  
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
  
 Nastavte zarážku na řádku int `x = sumVars(a, b) + subtractVars(c, d);` .  
  
 Spustit ladění a po přerušení provádění na první zarážce stiskněte klávesu **F10 (krok za krokem)**. V okně **Automatické** hodnoty by se měla zobrazit následující:  
  
 ![AutosReturnValueCSharp2](../debugger/media/autosreturnvaluecsharp2.png "AutosReturnValueCSharp2")  
  
## <a name="why-are-variable-values-sometimes-red-in-locals-and-autos-windows"></a>Proč jsou proměnné hodnoty někdy červené v lokálních hodnotách a oknech automatické hodnoty?  
 Můžete si všimnout, že hodnota proměnné je někdy červená v oknech **místní** hodnoty a **Automatické** hodnoty. Jedná se o proměnné hodnoty, které byly od posledního vyhodnocení změněny. Tato změna může být z předchozí relace ladění, nebo vzhledem k tomu, že se hodnota v okně změnila.  
  
## <a name="changing-the-numeric-format-of-a-variable-window"></a>Změna číselného formátu okna proměnné  
 Výchozí číselný formát je Decimal, ale můžete ho změnit na hexadecimální. Klikněte pravým tlačítkem myši do okna **místní** nebo **Automatické** hodnoty a vyberte **hexadecimální zobrazení**. Tato změna ovlivní všechna okna ladicího programu.  
  
## <a name="editing-a-value-in-a-variable-window"></a>Úprava hodnoty v okně proměnných  
 Hodnoty většiny proměnných, které se zobrazí v oknech **Automatické**hodnoty, **místní**hodnoty, **kukátko**a **QuickWatch** , můžete upravit. Informace o oknech **kukátka** a **QuickWatch** naleznete v tématu [Watch and QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md). Stačí dvakrát kliknout na hodnotu, kterou chcete změnit, a přidat novou hodnotu.  
  
 Můžete například zadat výraz pro hodnotu `a + b` . Ladicí program přijímá nejvíce platné jazykové výrazy.  
  
 V nativním kódu jazyka C++ bude pravděpodobně nutné kvalifikovat kontext názvu proměnné. Další informace naleznete v tématu [kontext operátoru (C++)](../debugger/context-operator-cpp.md).  
  
 Při změně hodnot byste však měli postupovat opatrně. Mohlo dojít k některému z následujících problémů:  
  
- Hodnocení některých výrazů může změnit hodnotu proměnné nebo jinak ovlivnit stav programu. Například vyhodnocení `var1 = ++var2` změn hodnoty `var1` a `var2` .  
  
     Výrazy, které mění data jsou označovány jako [vedlejší účinky](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)), což může způsobit neočekávané výsledky, pokud je neznáte. Ujistěte se, že rozumíte důsledkům takové změny, než je uděláte.  
  
- Úpravy hodnot s plovoucí desetinnou čárkou mohou díky převodu komponenty zlomku z desítkové do binární soustavy způsobit drobné nepřesnosti. I zdánlivě neškodné úpravy mohou v proměnné s plovoucí desetinnou čárkou způsobit změny některých nejméně významných bitů.  
  
## <a name="debug-location-toolbar"></a>panel nástrojů Ladit umístění  
 Pomocí panelu nástrojů **umístění ladění** můžete vybrat požadovanou funkci, vlákno nebo proces. Nastavte zarážku a spusťte ladění. (Pokud tento panel nástrojů nevidíte, můžete ho povolit kliknutím do prázdné části oblasti panelu nástrojů. Měl by se zobrazit seznam panelů nástrojů. Vyberte **umístění ladění**. Při dosažení zarážky se spuštění zastaví a uvidíte panel nástrojů umístění ladění, což je dolní řádek následujícího obrázku:  
  
 ![DebugLocationToolbar](../debugger/media/debuglocationtoolbar.png "DebugLocationToolbar")  
  
 Můžete také změnit kontext na různá volání funkcí, vlákna nebo procesy dvojitým kliknutím na prvek v okně **zásobník volání** , v okně **vlákna** nebo v okně **procesy** .  
  
## <a name="see-also"></a>Viz také  
 [Okna ladicího programu](../debugger/debugger-windows.md)
