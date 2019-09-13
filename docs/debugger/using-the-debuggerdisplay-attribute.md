---
title: Zobrazit vlastní informace pomocí DebuggerDisplay | Microsoft Docs
ms.date: 01/09/2019
ms.topic: conceptual
helpviewer_keywords:
- attributes, debugger
- DebuggerDisplay attribute
- DebuggerDisplayAttribute class
ms.assetid: f4eb7c76-af4e-493b-9ab6-9cb05949d9b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fbe3ff31d00945ef462c5c20eb1c4b33c250f97
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887747"
---
# <a name="tell-the-debugger-what-to-show-using-the-debuggerdisplay-attribute-c-visual-basic-f-ccli"></a>Sdělte ladicímu programu, co se má zobrazit pomocí atributuC#DebuggerDisplay (, F#Visual Basic C++,,/CLI).
Určuje <xref:System.Diagnostics.DebuggerDisplayAttribute> , jak se objekt, vlastnost nebo pole zobrazí v oknech proměnných ladicího programu. Tento atribut lze použít pro typy, delegáty, vlastnosti, pole a sestavení. Pokud se použije na základní typ, atribut se vztahuje také na podtřídu.

`DebuggerDisplay` Atribut má jeden argument, což je řetězec, který se zobrazí ve sloupci value pro instance daného typu. Tento řetězec může obsahovat složené závorky`{` ( `}`a). Text v páru složených závorek je vyhodnocen jako pole, vlastnost nebo metoda.

Pokud má třída potlačenou `ToString()` metodu, ladicí program použije potlačenou metodu namísto výchozího. `{<typeName>}` Proto, pokud jste přepsali `ToString()` metodu, ladicí program použije přepsanou metodu namísto výchozího`{<typeName>}`a nemusíte ji používat `DebuggerDisplay`. Použijete-li obojí, `DebuggerDisplay` má atribut přednost před potlačenou `ToString()` metodou. Atribut má také přednost před potlačenou `ToString()` metodou v podtříde. `DebuggerDisplay`

Bez ohledu na to, zda ladicí `ToString()` program vyhodnocuje Toto implicitní volání, závisí na nastavení uživatele v dialogovém okně **Nástroje/možnosti/ladění** . Visual Basic neimplementuje Toto implicitní `ToString()` vyhodnocení.

> [!IMPORTANT]
> Pokud je zaškrtnuté políčko **Zobrazit nezpracovanou strukturu objektů v proměnných** v dialogovém okně **nástroje/Options/ladění** `DebuggerDisplay` , je atribut ignorován.

> [!NOTE]
> Pro nativní kód je tento atribut podporován pouze v C++kódu/CLI.

V následující tabulce jsou uvedeny některé možné způsoby použití `DebuggerDisplay` atributů a ukázkových výstupů.

|Atribut|Výstup se zobrazuje ve sloupci hodnota.|
|---------------| - |
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> Používá se pro typ s poli `x` a `y`.|`x = 5 y = 18`|
|`[DebuggerDisplay("String value is {getString()}")]`Syntaxe parametru se může mezi jazyky lišit. Proto je používejte opatrně.|`String value is [5, 6, 6]`|

`DebuggerDisplay`může také přijmout pojmenované parametry.

|Parametry|Účel|
|----------------|-------------|
|`Name`, `Type`|Tyto parametry ovlivňují sloupce **název** a **typ** v oknech proměnných. (Mohou být nastaveny na řetězce pomocí stejné syntaxe jako konstruktor.) Tyto parametry jsou převedené nebo nesprávně používané, můžou způsobit matoucí výstup.|
|`Target`, `TargetTypeName`|Určuje cílový typ, pokud je atribut použit na úrovni sestavení.|

Soubor autoexp.cs používá atribut DebuggerDisplay na úrovni sestavení. Soubor autoexp.cs určuje výchozí rozšíření, které Visual Studio používá pro objekty .NET. Můžete si prohlédnout soubor autoexp.cs, kde najdete příklady použití atributu DebuggerDisplay, nebo můžete upravit a zkompilovat soubor autoexp.cs pro změnu výchozích rozšíření. Nezapomeňte soubor autoexp.cs před úpravou zálohovat.

Pokud chcete sestavit autoexp.cs, otevřete Developer Command Prompt pro VS2015 a spusťte následující příkazy.

```cmd
cd <directory containing autoexp.cs>
csc /t:library autoexp.cs
```

Změny v souboru autoexp. dll budou vyzvednuty v další relaci ladění.

## <a name="using-expressions-in-debuggerdisplay"></a>Použití výrazů v DebuggerDisplay
I když můžete použít obecný výraz mezi závorkami v atributu DebuggerDisplay, tento postup se nedoporučuje.

Obecný výraz v DebuggerDisplay má implicitní přístup k `this` ukazateli pro aktuální instanci cílového typu. Výraz nemá přístup k aliasům, místním hodnotám nebo ukazatelům. Pokud výraz odkazuje na vlastnosti, atributy těchto vlastností nejsou zpracovány. Kód C# `[DebuggerDisplay("Object {count - 2}")]` se například zobrazí `Object 6` , pokud bylo pole `count` 8.

Použití výrazů v DebuggerDisplay může vést k následujícím problémům:

- Vyhodnocování výrazů je nejlevnější operace v ladicím programu a výraz je vyhodnocen pokaždé, když je zobrazen. To může způsobit problémy s výkonem při procházení kódu. Například složitý výraz, který se používá k zobrazení hodnot v kolekci nebo seznamu, může být velmi pomalý, pokud je počet prvků velký.

- Výrazy jsou vyhodnocovány vyhodnocovacím filtrem výrazu jazyka aktuálního rámce zásobníku a nikoli vyhodnocovacím filtrem jazyka, ve kterém byl výraz napsán. To může vést k nepředvídatelným výsledkům, pokud se jazyky liší.

- Vyhodnocení výrazu může změnit stav aplikace. Například výraz, který nastaví hodnotu vlastnosti, je obdobou hodnoty vlastnosti ve spuštěném kódu.

  Jedním ze způsobů, jak omezit možné problémy při vyhodnocování výrazů, je vytvoření soukromé vlastnosti, která provede operaci a vrátí řetězec. Atribut DebuggerDisplay pak může zobrazit hodnotu této soukromé vlastnosti. Následující příklad implementuje tento model:

```csharp
[DebuggerDisplay("{DebuggerDisplay,nq}")]
public sealed class MyClass
{
    public int count { get; set; }
    public bool flag { get; set; }
    private string DebuggerDisplay
    {
        get
        {
            return string.Format("Object {0}", count - 2);
        }
    }
}
```

Přípona ", NQ" oznamuje vyhodnocení výrazu, aby při zobrazení konečné hodnoty (NQ = bez uvozovek) odebrala uvozovky.

## <a name="example"></a>Příklad
Následující příklad kódu ukazuje, jak použít `DebuggerDisplay`spolu s `DebuggerBrowseable` a `DebuggerTypeProxy`. Při zobrazení v okně proměnných ladicího programu, jako je například okno **kukátka** , vytvoří rozšíření, které vypadá takto:

|**Název**|**Hodnota**|**Typ**|
|--------------|---------------|--------------|
|Key|3|objekt {String}|
|Value|3|objekt {int}|

```csharp
[DebuggerDisplay("{value}", Name = "{key}")]
internal class KeyValuePairs
{
    private IDictionary dictionary;
    private object key;
    private object value;
    public KeyValuePairs(IDictionary dictionary, object key, object value)
    {
        this.value = value;
        this.key = key;
        this.dictionary = dictionary;
    }

    public object Key
    {
        get { return key; }
        set
        {
            object tempValue = dictionary[key];
            dictionary.Remove(key);
            key = value;
            dictionary.Add(key, tempValue);
        }
    }

    public object Value
    {
        get { return this.value; }
        set
        {
            this.value = value;
            dictionary[key] = this.value;
        }
    }
}

[DebuggerDisplay("{DebuggerDisplay,nq}")]
[DebuggerTypeProxy(typeof(HashtableDebugView))]
class MyHashtable
{
    public Hashtable hashtable;

    public MyHashtable()
    {
        hashtable = new Hashtable();
    }

    private string DebuggerDisplay { get { return "Count = " + hashtable.Count; } }

    private class HashtableDebugView
    {
        private MyHashtable myhashtable;
        public HashtableDebugView(MyHashtable myhashtable)
        {
            this.myhashtable = myhashtable;
        }

        [DebuggerBrowsable(DebuggerBrowsableState.RootHidden)]
        public KeyValuePairs[] Keys
        {
            get
            {
                KeyValuePairs[] keys = new KeyValuePairs[myhashtable.hashtable.Count];

                int i = 0;
                foreach (object key in myhashtable.hashtable.Keys)
                {
                    keys[i] = new KeyValuePairs(myhashtable.hashtable, key, myhashtable.hashtable[key]);
                    i++;
                }
                return keys;
            }
        }
    }
}
```

## <a name="see-also"></a>Viz také

- [Používání atributu DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Vytváření vlastních zobrazení spravovaných objektů](../debugger/create-custom-views-of-dot-managed-objects.md)
- [Specifikátory formátu v jazyce C#](../debugger/format-specifiers-in-csharp.md)
- [Rozšíření ladění pomocí atributů zobrazení ladicího programu](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
