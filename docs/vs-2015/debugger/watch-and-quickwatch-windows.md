---
title: Sledujte a QuickWatch Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
ms.assetid: d5c18377-2a0e-4819-a645-407e24ccc58c
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3f79e492440f98f733488afb241fa6f86e220b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780240"
---
# <a name="watch-and-quickwatch-windows"></a>Okna Kukátko a Rychlé kukátko
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít **kukátko** (**ladění/Windows/sledovat/sledovat (1, 2, 3, 4)**) a **QuickWatch** (klikněte pravým tlačítkem myši na proměnnou/ **ladit/QuickWatch**) a sledujte proměnné a výrazy během ladicí relace.  Rozdíl je v tom, že okno **kukátka** může zobrazit několik proměnných, zatímco okno **QuickWatch** zobrazuje jednu proměnnou v jednom okamžiku.  
  
## <a name="observing-a-single-variable-with-quickwatch"></a>Pozorování jedné proměnné s QuickWatch  
 Pomocí okna **QuickWatch** můžete sledovat jedinou proměnnou. Například pokud máte následující kód:  
  
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
  
 V okně QuickWatch můžete sledovat proměnnou, jak je znázorněno níže:  
  
1. Nastavte zarážku na `a = a + b;` řádku.  
  
2. Spuštění ladění Spuštění se zastaví na zarážce.  
  
3. Otevřete okno **QuickWatch** (klikněte pravým tlačítkem myši na a pak zvolte **ladit/QuickWatch**nebo **SHIFT + F9**). Můžete otevřít okno a přidat proměnnou do okna **výrazu** a pak kliknout na znovu **vyhodnotit**. V okně **hodnoty** by se měla zobrazit proměnná a s hodnotou 2.  
  
4. Okno **QuickWatch** je modální dialogové okno, takže nemůžete pokračovat v ladění, dokud je otevřené. Proměnnou můžete přidat do okna **kukátka** kliknutím na **Přidat kukátko**.  
  
5. Zavřete okno **QuickWatch** . Nyní můžete pokračovat v ladění a přitom sledovat hodnotu v okně **kukátko** .  
  
## <a name="observing-variables-with-the-watch-window"></a>Pozorování proměnných s okno Kukátko  
 Můžete sledovat více proměnných v okně **kukátko** . Například pokud máte následující kód:  
  
```csharp  
static void Main(string[] args)  
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
}  
  
```  
  
 Přidejte hodnoty tří proměnných do okno Kukátko následujícím způsobem:  
  
1. Nastavte zarážku na `c = a + b;` řádku.  
  
2. Spustit ladění (**F5**). Spuštění se zastaví na zarážce.  
  
3. Otevřete okno Kukátko (**ladění/okna/Kukátko/kukátko 1**nebo **CTRL + ALT + W, 1**).  
  
4. Přidejte `a` proměnnou do prvního řádku, `b` proměnnou do druhého řádku a `c` proměnnou na třetí řádek.  
  
5. Pokračovat v ladění.  
  
   Při iteraci smyčky by se měly zobrazit hodnoty proměnných `for` .  
  
   Pokud programujete v nativním kódu, může být někdy nutné kvalifikovat kontext názvu proměnné nebo výrazu obsahujícího název proměnné. Kontext je funkce, zdrojový soubor a modul, kde je umístěna proměnná. Pokud je to nutné, můžete použít syntaxi kontextového operátoru. Další informace naleznete v tématu výrazy v jazyce C++.  
  
## <a name="observing-expressions-with-the-watch-window"></a>Pozorování výrazů s okno Kukátko  
 Nyní zkusíme místo toho použít výraz. Můžete přidat libovolný platný výraz rozpoznávaný ladicím programem.  
  
 Například pokud máte kód uvedený v předchozí části, můžete získat průměr tří hodnot takto:  
  
 ![WatchExpression](../debugger/media/watchexpression.png "WatchExpression")  
  
 Obecně platí, že pravidla pro vyhodnocování výrazů v okně **kukátka** jsou stejná jako pravidla pro vyhodnocování výrazů v jazyce kódování. Pokud má výraz syntaktickou chybu, můžete očekávat stejnou chybu kompilátoru, kterou byste viděli v editoru kódu. Zde naleznete příklad:  
  
 ![WatchExpressionError](../debugger/media/watchexpressionerror.png "WatchExpressionError")  
  
## <a name="refreshing-watch-values-that-are-out-of-date"></a><a name="bkmk_refreshWatch"></a> Aktualizují se hodnoty sledování, které nejsou aktuální.  
 V některých případech se může zobrazit ikona aktualizace (kruh se dvěma šipkami nebo kruh se dvěma vlnovými čarami), když se výraz vyhodnotí v okně **kukátka** .  Například pokud máte vyhodnocování vlastností vypnuté (**Nástroje/možnosti/ladění/povolit vyhodnocování vlastností a další implicitní volání funkcí**) a máte následující kód:  
  
```csharp  
static void Main(string[] args)  
{  
    List<string> list = new List<string>();  
    list.Add("hello");  
    list.Add("goodbye");  
}  
  
```  
  
 Pokud nastavili kukátko pro `Count` vlastnost seznamu, měla by se zobrazit něco podobného jako následující:  
  
 ![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")  
  
 To označuje chybu nebo hodnotu, která je neaktuální. Tuto hodnotu můžete obecně aktualizovat tak, že kliknete na ikonu, ale v některých případech můžete chtít, abyste ji neaktualizovali. Nejdřív potřebujete zjistit, proč nebyla hodnota vyhodnocena.  
  
 Pokud nakážete na ikonu, popis tlačítka poskytuje informace o tom, proč výraz nebyl vyhodnocen.  Pokud se zobrazí šipky směřující, výraz nebyl vyhodnocen z některého z následujících důvodů:  
  
- • Při vyhodnocování výrazu došlo k chybě. Například může dojít k vypršení časového limitu nebo je proměnná pravděpodobně mimo rozsah.  
  
- • Výraz obsahuje volání funkce, které může aktivovat vedlejší efekt v aplikaci (viz [vedlejší efekty a výrazy](#bkmk_sideEffects)).  
  
- Automatické vyhodnocení vlastností a volání implicitních funkcí ladicího programu je vypnuté (**Nástroje/možnosti/ladění/povolení vyhodnocení vlastností a další implicitní volání funkce**) a pak výraz nejde automaticky vyhodnotit.  
  
  Pokud chcete hodnotu aktualizovat, klikněte na ikonu aktualizace nebo stiskněte mezerník. Ladicí program se pokusí znovu vyhodnotit výraz. Pokud se zobrazila ikona aktualizace, protože bylo vypnuto automatické vyhodnocení vlastností a implicitní vedlejší účinky, lze výraz vyhodnotit.  
  
  Pokud se zobrazí ikona, která je kolečkem se dvěma vlnovými čarami podobnými vláknům, výraz nebyl vyhodnocen z důvodu potenciální závislosti mezi vlákny. Jinými slovy, vyhodnocení kódu vyžaduje dočasné spuštění jiných vláken ve vaší aplikaci. Když jste v režimu pozastavení, všechna vlákna v aplikaci jsou obvykle zastavena. Umožnění dočasného spuštění jiných vláken může mít neočekávané účinky na stav programu a způsobí, že ladicí program ignoruje události, jako jsou zarážky a výjimky vyvolané v těchto vláknech.  
  
## <a name="side-effects-and-expressions"></a><a name="bkmk_sideEffects"></a> Vedlejší efekty a výrazy  
 Hodnocení některých výrazů může změnit hodnotu proměnné nebo jinak ovlivnit stav programu. Například vyhodnocení následujícího výrazu změní hodnotu `var1` :  
  
```  
var1 = var2  
```  
  
 Nazývá se to [vedlejší efekt](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Vedlejší účinky můžou ztížit ladění změnou způsobu, jakým program pracuje.  
  
 Výraz, u kterého se říká vedlejší účinky, je vyhodnocen pouze jednou při prvním zadání. Následná hodnocení jsou zakázaná. Toto chování můžete přepsat ručně tak, že kliknete na ikonu aktualizace, která se zobrazí vedle hodnoty.  
  
 Jedním ze způsobů, jak se vyhnout všem vedlejším účinkům, je vypnout automatické vyhodnocení funkcí (**Nástroje/možnosti/ladění/povolit vyhodnocování vlastností a další implicitní volání funkce**).  
  
 Když je vyhodnocování vlastností nebo implicitních volání funkcí vypnuto, můžete vynutit vyhodnocování pomocí modifikátoru formátu **AC** (pouze pro jazyk C#). Viz [specifikátory formátu v jazyce C#](../debugger/format-specifiers-in-csharp.md).  
  
## <a name="using-object-ids-in-the-watch-window-c-and-visual-basic"></a>Použití ID objektů v okno Kukátko (C# a Visual Basic)  
 Existují situace, kdy chcete sledovat chování určitého objektu; Například můžete chtít sledovat objekt, na který odkazuje místní proměnná poté, co tato proměnná dokončí mimo rozsah. V jazyce C# a Visual Basic můžete vytvořit ID objektů pro konkrétní instance odkazových typů a použít je v okno Kukátko a v podmínkách zarážek. ID objektu je vygenerováno službami ladění modulu CLR (Common Language Runtime) a přidruženy k objektu.  
  
> [!NOTE]
> ID objektů vytvářejí slabé odkazy a nebrání v uvolňování paměti objektu. Jsou platné pouze pro aktuální relaci ladění.  
  
 V následujícím kódu je jedna metoda vytvořena `Person` pomocí místní proměnné, ale chcete zjistit, co `Person` je název v jiné metodě:  
  
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
    List<Person> _people = new List<Person>();  
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
  
 Odkaz na tento objekt můžete přidat `Person` v okně **kukátka** následujícím způsobem:  
  
1. Nastavte zarážku v kódu nějakým časem po vytvoření objektu.  
  
2. Spusťte ladění a když se spuštění zastaví na zarážce, najděte proměnnou v okně **místní** hodnoty, klikněte na ni pravým tlačítkem myši a vyberte **vytvořit ID objektu**.  
  
3. **$** V okně **místní** hodnoty by se měla zobrazit znaménko plus. Toto je ID objektu.  
  
4. Přidejte ID objektu do okno Kukátko.  
  
5. Nastavte zarážku, kde chcete sledovat chování objektu.  Ve výše uvedeném kódu, který by byl v `DoSomething()` metodě.  
  
6. Pokračovat v ladění a v případě, že se provádění zastaví v `DoSomething()` metodě, okno **kukátko** zobrazí `Person` objekt.  
  
> [!NOTE]
> Chcete-li zobrazit vlastnosti objektu, například `Person.Name` v předchozím příkladu, je nutné povolit vyhodnocování vlastností.  
  
## <a name="using-registers-in-the-watch-window-c-only"></a>Použití registrů v okno Kukátko (pouze C++)  
 Pokud ladíte nativní kód, můžete přidat názvy registrů i názvy proměnných pomocí **$\<register name>** nebo **@\<register name>** .  Další informace najdete v tématu [Pseudoproměnné](../debugger/pseudovariables.md).  
  
## <a name="dynamicview-and-the-watch-window"></a>DynamicView a okno Kukátko  
 Některé skriptovací jazyky (například JavaScript nebo Python) využívají dynamické nebo [ztracené psaní](https://en.wikipedia.org/wiki/Duck_typing)a jazyky .NET (ve verzi 4,0 a novější) podporují objekty, které jsou obtížné sledovat pomocí normálního ladicího okna, protože mohou mít běhové vlastnosti a metody, které nelze zobrazit.  
  
 Když okno Kukátko zobrazí objekt, který byl vytvořen z typu, který implementuje <xref:System.Dynamic.IDynamicMetaObjectProvider> , ladicí program přidá speciální uzel **dynamického zobrazení**  do zobrazení **Automatické** hodnoty. Tento uzel zobrazuje dynamické členy dynamického objektu, ale neumožňuje úpravy hodnot členů.  
  
 Kliknete-li pravým tlačítkem myši na libovolný podřízený uzel **dynamického zobrazení** a zvolíte možnost **Přidat kukátko**, ladicí program vloží novou proměnnou kukátka, která přetypování objektu na dynamický objekt. Jinými slovy, **název objektu** se bude (**(dynamický) objekt). Název**.  
  
 Vyhodnocení členů **dynamického zobrazení** může mít vedlejší účinky. Vysvětlení vedlejších účinků naleznete v tématu [vedlejší účinky a výrazy](#bkmk_sideEffects). V jazyce C# ladicí program automaticky nehodnotí hodnoty zobrazené v **dynamickém zobrazení** , když jste provedli krok na nový řádek kódu. Pro Visual Basic výrazy přidané prostřednictvím **dynamického zobrazení** se automaticky aktualizují.  
  
 Pokyny k aktualizaci hodnot dynamického zobrazení najdete v tématu [aktualizace hodnot sledování, které jsou zastaralé](#bkmk_refreshWatch).  
  
 Chcete-li zobrazit pouze **dynamické zobrazení** objektu, můžete použít specifikátor **dynamického** formátu:  
  
- C#: **ObjectName, dynamický**  
  
- Visual Basic:: **$Dynamic, ObjectName**  
  
  **Dynamické zobrazení** také vylepšuje možnosti ladění pro objekty modelu COM. Když ladicí program narazí na objekt modelu COM zabalený v **System. __ComObject**, přidá uzel **dynamického zobrazení** pro objekt.  
  
## <a name="see-also"></a>Viz také  
 [Okna ladicího programu](../debugger/debugger-windows.md)
