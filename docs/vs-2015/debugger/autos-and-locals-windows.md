---
title: Automatické hodnoty a místní hodnoty Windows | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
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
manager: ghogen
ms.openlocfilehash: 51e62df0fb98a9c7b04b09b3e58fb52828e1bd5a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782476"
---
# <a name="autos-and-locals-windows"></a>Automatické hodnoty a místní hodnoty Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Automatické hodnoty** okno (při ladění, **CTRL + ALT + V, A**, nebo **ladění / Windows / auta**) a **lokální** okno (při ladění,  **CTRL + ALT + V, L**, nebo **ladění / Windows / lokální**) jsou velmi užitečné, pokud chcete zobrazit hodnoty proměnných během ladění. **Lokální** okně se zobrazí proměnné, které jsou definovány v místním rozsahem, což je obvykle funkce nebo metoda, která se právě zpracovává. **Automatické hodnoty** okně se zobrazí proměnné používané kolem aktuálního řádku (místo, kde je zastavený ladicím programu). Přesně zobrazí které proměnné se liší v různých jazycích. Zobrazit proměnné, které se zobrazí v okně Automatické hodnoty? níže.  
  
 Pokud potřebujete další informace o základní ladění, naleznete v tématu [Začínáme s ladicím programem](../debugger/getting-started-with-the-debugger.md).  
  
## <a name="looking-at-objects-in-the-autos-and-locals-windows"></a>Hledání v objektech v oknech pro automatické hodnoty a místní hodnoty  
 Pole a objekty jsou zobrazeny v okně Automatické hodnoty a místní hodnoty jako ovládacích prvků strom. Klikněte na šipku nalevo od názvu proměnné na Rozbalit zobrazení k zobrazení polí a vlastností. Tady je příklad <xref:System.IO.FileStream> objekt **místní hodnoty** okno:  
  
 ![Locals&#45;FileStream](../debugger/media/locals-filestream.png "Locals-FileStream")  
  
## <a name="what-variables-appear-in-the-autos-window"></a>Jaké proměnné zobrazí v okně Automatické hodnoty?  
 Můžete použít **automatické hodnoty** okna v kódu jazyka C#, Visual Basic a C++. **Automatické hodnoty** okno nepodporuje jazyk JavaScript nebo F#.  
  
 V jazyce C# a Visual Basic **automatické hodnoty** v okně se zobrazí všechny proměnné použité v aktuální nebo předchozí řádku. Například pokud deklarace čtyři proměnné a jejich nastavení následujícím způsobem:  
  
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
  
 Pokud nastavíte zarážku na řádku `c = 3`; a spustit ladicí program, když se zastaví provádění **automatické hodnoty** bude okno vypadat například takto:  
  
 ![Autos&#45;CSharp](../debugger/media/autos-csharp.png "Autos-CSharp")  
  
 Všimněte si, že hodnota `c` je 0, protože řádku `c = 3` ještě nebyla spuštěna.  
  
 V jazyce C++ **automatické hodnoty** v okně se zobrazí proměnné používané alespoň tři řádky před aktuální řádek (řádku zastavením spuštění). Pokud deklarujete šest proměnné:  
  
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
  
 Pokud nastavíte zarážku na řádku `e = 5;` a spustit ladicí program, když se zastaví provádění **automatické hodnoty** bude okno vypadat například takto:  
  
 ![Autos&#45;Cplus](../debugger/media/autos-cplus.png "Autos-Cplus")  
  
 Všimněte si, že proměnná e není inicializovaná, protože kód na řádku `e = 5;` ještě nebyla spuštěna.  
  
 Můžete také zobrazit návratové hodnoty funkce a metody v některých případech. Zobrazit [zobrazení návratových hodnot volání metod](#bkmk_returnValue) níže.  
  
##  <a name="bkmk_returnValue"></a> Zobrazení návratových hodnot volání metod  
 V kódu rozhraní .NET a C++ může Kontrola návratových hodnot při kroku přes nebo mimo volání metody. Tato funkce je užitečná, když výsledek volání metody není uložen v místní proměnné, například při použití metody jako parametr nebo návratovou hodnotu metody jiné.  
  
 Následující kód jazyka C# přidává návratové hodnoty dvou funkcí:  
  
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
  
 Nastavit zarážku na int `x = sumVars(a, b) + subtractVars(c, d);` řádku.  
  
 Spustit ladění a při provádění přeruší v k první zarážce, stiskněte klávesu **F10 (Krokovat s přeskočením)**. Měli byste vidět v následující **automatické hodnoty** okno:  
  
 ![AutosReturnValueCSharp2](../debugger/media/autosreturnvaluecsharp2.png "AutosReturnValueCSharp2")  
  
## <a name="why-are-variable-values-sometimes-red-in-locals-and-autos-windows"></a>Proč jsou hodnoty proměnných někdy červená barva v oknech místní hodnoty a automatické hodnoty?  
 Můžete si všimnout, že hodnota proměnné je někdy červeně v **lokální** a **automatické hodnoty** systému windows. Toto jsou hodnoty proměnných, které se změnily od posledního vyhodnocení. Tato změna může být z předchozí ladicí relace, nebo proto, že hodnota se změnila v okně.  
  
## <a name="changing-the-numeric-format-of-a-variable-window"></a>Změna číselného formátu okně proměnných  
 Je výchozí číselný formát desetinné číslo, ale můžete ho změnit na šestnáctkové. Klepněte pravým tlačítkem myši **lokální** nebo **automatické hodnoty** okna a vyberte **hexadecimální zobrazení**. Změna ovlivní všechna okna ladicího programu.  
  
## <a name="editing-a-value-in-a-variable-window"></a>Úprava hodnoty v okně proměnné  
 Můžete upravit hodnot většiny proměnných, které se zobrazují v **automatické hodnoty**, **lokální**, **Watch**, a **QuickWatch** systému windows. Informace o **Watch** a **QuickWatch** naleznete zde [kukátko a Rychlé kukátko Windows](../debugger/watch-and-quickwatch-windows.md). Poklepejte na hodnotu, kterou chcete změnit a přidejte novou hodnotu.  
  
 Výraz hodnoty, můžete zadat například `a + b`. Ladicí program přijímá nejvíce platné jazykové výrazy.  
  
 V nativním kódu C++ může být potřeba kvalifikovat kontext názvu proměnné. Další informace najdete v tématu [kontextu – operátor (C++)](../debugger/context-operator-cpp.md).  
  
 Však opatrně při změně hodnoty. Mohlo dojít k některému z následujících problémů:  
  
-   Hodnocení některých výrazů může změnit hodnotu proměnné nebo jinak ovlivnit stav programu. Například vyhodnocení `var1 = ++var2` změní hodnotu `var1` a `var2`.  
  
     Výrazy, které mění data mají často [vedlejší účinky](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)), které mohou způsobit neočekávané výsledky, pokud si nejste vědomi. Ujistěte se, že chápete důsledky takové změny, před jeho provedením.  
  
-   Úpravy hodnot s plovoucí desetinnou čárkou mohou díky převodu komponenty zlomku z desítkové do binární soustavy způsobit drobné nepřesnosti. I zdánlivě neškodné úpravy mohou v proměnné s plovoucí desetinnou čárkou způsobit změny některých nejméně významných bitů.  
  
## <a name="debug-location-toolbar"></a>panel nástrojů Ladit umístění  
 Můžete použít **umístění ladění** nástrojů a vyberte požadované funkce, vlákna nebo procesu. Nastavte zarážku a spusťte ladění. (Pokud nevidíte tento panel nástrojů, můžete ji povolit kliknutím na prázdnou část oblasti panelu nástrojů. Zobrazí se seznam panely nástrojů; Vyberte **umístění ladění**). Při dosažení zarážky zastaví provádění zobrazíte panelu nástrojů umístění ladění, což je dolní řádek na následujícím obrázku:  
  
 ![DebugLocationToolbar](../debugger/media/debuglocationtoolbar.png "DebugLocationToolbar")  
  
 Můžete také změnit kontext na jiné funkce volání, vláknech či procesy dvojitým kliknutím na prvek v **zásobník volání** okně **vlákna** okna, nebo **procesy** okna.  
  
## <a name="see-also"></a>Viz také  
 [Okna ladicího programu](../debugger/debugger-windows.md)





