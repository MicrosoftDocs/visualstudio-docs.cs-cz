---
title: Kukátko a Rychlé kukátko Windows | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: b171352475b6c0b3bc916d27ab4ba351e84be42b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791670"
---
# <a name="watch-and-quickwatch-windows"></a>Kukátko a Rychlé kukátko Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít **Watch** (**ladění / Windows / sledovat / sledovat (1, 2, 3, 4)**) a **QuickWatch** (klikněte pravým tlačítkem na proměnnou / **ladění / QuickWatch**) systému windows ke sledování proměnných a výrazů během relace ladění.  Rozdíl je, že **Watch** okno může zobrazit několik proměnných, zatímco **QuickWatch** okně zobrazí najednou jednu proměnnou.  
  
## <a name="observing-a-single-variable-with-quickwatch"></a>Sledování do jedné proměnné s QuickWatch  
 Můžete použít **QuickWatch** okno dodržovat jednu proměnnou. Pokud například máte následující kód:  
  
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
  
 Můžete sledovat proměnnou v okně QuickWatch následujícím způsobem:  
  
1.  Nastavit zarážku na `a = a + b;` řádku.  
  
2.  Spusťte ladění. Provádění zastaví na zarážce.  
  
3.  Otevřít **QuickWatch** okno (klikněte pravým tlačítkem na, klikněte na tlačítko **ladění / QuickWatch**, nebo **SHIFT + F9**). Můžete otevřít okno a přidat proměnnou, která **výraz** okna, klikněte na **přehodnotit**. Měli byste vidět proměnnou v **hodnoty** okno s hodnotou 2.  
  
4.  **QuickWatch** je okno oknem modální dialogové okno, takže nelze pokračovat v ladění, dokud je otevřen. Můžete přidat proměnnou **Watch** okno kliknutím **Přidat kukátko**.  
  
5.  Zavřít **QuickWatch** okna. Teď můžete pokračovat v ladění při sledování hodnotu v **Watch** okna  
  
## <a name="observing-variables-with-the-watch-window"></a>Sledování proměnné okno kukátka  
 Můžete sledovat více proměnných s **Watch** okna. Pokud například máte následující kód:  
  
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
  
 Následujícím způsobem přidejte do okna kukátka hodnoty tří proměnných:  
  
1. Nastavit zarážku na `c = a + b;` řádku.  
  
2. Spustit ladění (**F5**). Provádění zastaví na zarážce.  
  
3. Otevřete okno kukátka (**ladění / Windows / sledovat / sledovat 1**, nebo **CTRL + ALT + W, 1**).  
  
4. Přidat `a` proměnné na první řádek, `b` proměnné na druhém řádku a `c` proměnné na třetí řádek.  
  
5. Pokračujte v ladění.  
  
   Měli byste vidět změny jako iteraci v rámci hodnoty proměnné `for` smyčky.  
  
   Pokud programujete v nativním kódu, můžete někdy potřebovat kvalifikovat kontext názvu proměnné nebo výrazu obsahujícího název proměnné. Kontext je funkce, zdrojový soubor a modul, kde je umístěna proměnná. Pokud je to nutné, můžete použít syntaxi kontextového operátoru. Další informace najdete v tématu výrazy v jazyce C++.  
  
## <a name="observing-expressions-with-the-watch-window"></a>Sledování výrazy s okna kukátka  
 Teď si vyzkoušíme použití výrazu místo. Můžete přidat libovolný platný výraz rozpoznán v ladicím programu.  
  
 Například pokud máte kód uvedený v předchozí části, můžete získat průměrem tří hodnot takto:  
  
 ![WatchExpression](../debugger/media/watchexpression.png "WatchExpression")  
  
 Obecně platí, pravidla pro vyhodnocování výrazů v **Watch** okna jsou stejné jako pravidla pro vyhodnocování výrazů v kódovací jazyk. Pokud výraz obsahuje chybu syntaxe, můžete očekávat stejnou chybu kompilátoru, která se zobrazí v editoru kódu. Tady je příklad:  
  
 ![WatchExpressionError](../debugger/media/watchexpressionerror.png "WatchExpressionError")  
  
##  <a name="bkmk_refreshWatch"></a> Aktualizace hodnot sledování, které jsou zastaralé  
 V některých případech může zobrazit ikona Aktualizovat (kroužek s dvěma šipkami nebo kroužek s dvěma vlnovky) při vyhodnocování výrazu v **Watch** okna.  Například, pokud máte vyhodnocení vlastností vypnout (**nástroje / Možnosti / ladění / povolit vyhodnocování vlastností a jiných implicitních volání funkcí**), a že máte následující kód:  
  
```csharp  
static void Main(string[] args)  
{  
    List<string> list = new List<string>();  
    list.Add("hello");  
    list.Add("goodbye");  
}  
  
```  
  
 Pokud nastavení sledování u `Count` vlastnost seznamu, by měl vypadat přibližně takto:  
  
 ![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")  
  
 To znamená chybu nebo hodnotu, která je zastaralá. Hodnota je obecně aktualizovat kliknutím na ikonu, ale v některých případech může být nechcete ho aktualizovat. Nejdřív je potřeba vědět, proč nebyl vyhodnocen hodnotu.  
  
 Pokud přejdete na ikonu, popisek obsahuje informace o proč výraz nebyl vyhodnocen.  Pokud se zobrazí circling šipky, výraz nebyl vyhodnocen pro jednu z následujících důvodů:  
  
- • Chybu došlo k chybě, jako jsou vyhodnocovalo výraz. Například pravděpodobně došlo k vypršení časového limitu nebo mohly být proměnná mimo rozsah.  
  
- • Výraz obsahuje volání funkce, které může způsobit vedlejší účinek v aplikaci (viz [vedlejší efekty a výrazy](#bkmk_sideEffects)).  
  
- Je vypnuto automatické vyhodnocování vlastností a volání implicitní funkce ladicím programem (**nástroje / Možnosti / ladění / povolit vyhodnocování vlastností a jiných implicitních volání funkcí**), a potom nemůže být výraz automaticky vyhodnocena.  
  
  Pokud chcete aktualizovat hodnotu, klikněte na ikonu aktualizace nebo stisknutím klávesy MEZERNÍK. Ladicí program se pokusí opětovné vyhodnocení výrazu. Pokud se objevila ikona aktualizace, protože bylo vypnuto automatické hodnocení vlastností a implicitní vedlejší účinky, může být vyhodnocen výraz.  
  
  Pokud se zobrazí ikona, která je kroužek s dvěma vlnovkou řádky, které se podobají vlákna, výraz nebyl vyhodnocen z důvodu možných závislosti mezi vlákny. Jinými slovy vyhodnocování kód vyžaduje ostatní vlákna v aplikaci dočasně spustit. Pokud jste v režimu přerušení, zastaví se obvykle všechna vlákna ve vaší aplikaci. Umožňuje spustit dočasně jiných vláken může mít neočekávané účinky na stav programu a způsobí, že se ladicí program ignorovat události, například zarážky a výjimky vyvolané na tato vlákna.  
  
##  <a name="bkmk_sideEffects"></a> Vedlejší efekty a výrazy  
 Hodnocení některých výrazů může změnit hodnotu proměnné nebo jinak ovlivnit stav programu. Například vyhodnocení následujícího výrazu změní hodnotu `var1`:  
  
```  
var1 = var2  
```  
  
 Jedná se [vedlejší účinek](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Vedlejší efekty můžou ztížit ladění tak, že změníte způsob, jakým pracuje váš program.  
  
 Vyhodnocování výrazu, které jsou známy vedlejší účinky pouze jednou, při prvním zadání. Následné hodnocení jsou zakázána. Toto chování můžete přepsat ručně kliknutím na ikonu aktualizace, které se zobrazí vedle hodnoty.  
  
 Chcete-li vypnout automatické vyhodnocování funkcí je jedním ze způsobů, aby všechny vedlejší účinky (**nástroje / Možnosti / ladění / povolit vyhodnocování vlastností a jiných implicitních volání funkcí**).  
  
 Při hodnocení vlastnosti nebo implicitních volání funkcí je vypnutý, můžete vynutit pomocí vyhodnocení **ac** modifikátor formátu (pro jenom v C#). Zobrazit [v jazyce C# specifikátory formátu](../debugger/format-specifiers-in-csharp.md).  
  
## <a name="using-object-ids-in-the-watch-window-c-and-visual-basic"></a>Pomocí ID objektů v okně kukátko (C# a Visual Basic)  
 Existují situace, kdy budete chtít sledovat chování konkrétního objektu. Můžete například chtít sledovat objekt odkazuje místní proměnné po této proměnné je nepřejdou mimo rozsah. V jazyce C# a Visual Basic můžete vytvořit ID pro určité instance odkazové typy objektů a jejich použití v okně kukátka a podmínky zarážky. ID objektu je generována modulem common language runtime (CLR) ladění služeb a přidružená k objektu.  
  
> [!NOTE]
>  ID objektů vytvořit slabé odkazy a nezabrání objektu je uvolněna z paměti. Jsou platné pouze pro aktuální relaci ladění.  
  
 Následující kód vytvoří jednu metodu `Person` pomocí místní proměnné, ale chcete zjistit, co `Person`jeho název je v jiné metody:  
  
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
  
 Můžete přidat odkaz na daný `Person` objekt **Watch** okno následujícím způsobem:  
  
1.  Nastavte zarážku v kódu nějakou dobu, po vytvoření objektu.  
  
2.  Spustit ladění a v zarážky zastaví provádění, najdete v proměnné **lokální** okně pravým tlačítkem myši a vyberte **Ujistěte se, ID objektu**.  
  
3.  Měli byste vidět **$** plus číslo v **místní hodnoty** okna. To je ID objektu.  
  
4.  Přidáte ID objektu k oknu kukátka.  
  
5.  Nastavte zarážku, ve které chcete sledovat chování objektu.  Ve výše uvedeném kódu, která by byla `DoSomething()` metody.  
  
6.  Pokračovat v ladění, a při provádění zastaví v `DoSomething()` metody **Watch** v okně se zobrazí `Person` objektu.  
  
> [!NOTE]
>  Pokud chcete zobrazit vlastnosti objektu, například `Person.Name` v předchozím příkladu musí mít povoleno vyhodnocování vlastnosti.  
  
## <a name="using-registers-in-the-watch-window-c-only"></a>Pomocí registry v okně kukátko (pouze C++)  
 Pokud ladíte nativní kód, můžete přidat názvy registrů, jakož i názvy proměnných pomocí  **$ \<zaregistrovat název >** nebo  **@ \<zaregistrovat název >**.  Další informace najdete v tématu [Pseudoproměnné](../debugger/pseudovariables.md).  
  
## <a name="dynamicview-and-the-watch-window"></a>DynamicView a okno kukátka  
 Použít dynamické některé skriptovacích jazyků (např. JavaScript nebo Python) nebo [duck zadáním](https://en.wikipedia.org/wiki/Duck_typing), a objekty, které je obtížné sledovat v oknech ladění normální, protože mohou mít podporu jazyků .NET (ve verzi 4.0 a novější) modul runtime vlastnosti a metody, které nelze zobrazit.  
  
 Když zobrazí okno kukátka nebo objekt vytvořený z typu, který implementuje <xref:System.Dynamic.IDynamicMetaObjectProvider>, přidá ladicí program speciální **dynamického zobrazení** uzlu **automatické hodnoty** zobrazení. Tento uzel zobrazuje dynamické členy dynamického objektu, ale neumožňuje úpravy hodnot členů.  
  
 Pokud kliknete pravým tlačítkem na podřízený uzel **dynamického zobrazení** a zvolte **Přidat kukátko**, vloží ladicí program novou proměnnou kukátka, která přetypovává objekt na dynamický objekt. Jinými slovy **název objektu** stane (**(dynamických) objektů). Název**.  
  
 Vyhodnocování členů **dynamického zobrazení** může mít vedlejší účinky. Vysvětlení, jaké jsou vedlejší účinky, najdete v článku [vedlejší efekty a výrazy](#bkmk_sideEffects). Pro jazyk C#, ladicí program automaticky nepřehodnocuje hodnoty zobrazené **dynamického zobrazení** po kroku na nový řádek kódu. V jazyce Visual Basic přidávají výrazy **dynamického zobrazení** se automaticky aktualizují.  
  
 Pokyny o tom, jak aktualizovat hodnoty dynamického zobrazení najdete v tématu [hodnot aktualizace sledování, které jsou zastaralé](#bkmk_refreshWatch).  
  
 Pokud chcete zobrazit pouze **dynamického zobrazení** pro objekt, můžete použít **dynamické** specifikátor formátu:  
  
- C#: **ObjectName dynamické**  
  
- Visual Basic:: **$dynamic ObjectName**  
  
  **Dynamického zobrazení** také rozšiřuje možnosti ladění pro objekty COM. Pokud ladicí program nalezne objekt modelu COM, který je obalen **System.__ComObject**, přidá **dynamického zobrazení** uzlu pro objekt.  
  
## <a name="see-also"></a>Viz také  
 [Okna ladicího programu](../debugger/debugger-windows.md)





