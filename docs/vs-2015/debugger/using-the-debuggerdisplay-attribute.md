---
title: Použití atributu DebuggerDisplay | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerDisplay attribute
- DebuggerDisplayAttribute class
ms.assetid: f4eb7c76-af4e-493b-9ab6-9cb05949d9b3
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aba6feb17a4e7bd4cabfe40bd45480a0f7a9f552
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683927"
---
# <a name="using-the-debuggerdisplay-attribute"></a>Používání atributu DebuggerDisplay
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Diagnostics.DebuggerDisplayAttribute>Určuje, jak se objekt, vlastnost nebo pole zobrazí v oknech proměnných ladicího programu. Tento atribut lze použít pro typy, delegáty, vlastnosti, pole a sestavení.  
  
 `DebuggerDisplay`Atribut má jeden argument, což je řetězec, který se zobrazí ve sloupci value pro instance daného typu. Tento řetězec může obsahovat složené závorky ( `{` a `}` ). Text v páru složených závorek je vyhodnocen jako pole, vlastnost nebo metoda.  
  
 Pokud má třída potlačenou `ToString()` metodu, ladicí program použije potlačenou metodu namísto výchozího `{<typeName>}` . Proto, pokud jste přepsali `ToString()` metodu, ladicí program použije přepsanou metodu namísto výchozího `{<typeName>}` a nemusíte ji používat `DebuggerDisplay` . Použijete-li obojí, má `DebuggerDisplay` atribut přednost před potlačenou `ToString()` metodou.  
  
 Bez ohledu na to, zda ladicí program vyhodnocuje Toto implicitní `ToString()` volání, závisí na nastavení uživatele v dialogovém okně **Nástroje/možnosti/ladění** . Visual Basic neimplementuje Toto implicitní `ToString()` vyhodnocení.  
  
> [!IMPORTANT]
> Pokud je zaškrtnuté políčko **Zobrazit nezpracovanou strukturu objektů v proměnných** v dialogovém okně **nástroje/Options/ladění** , `DebuggerDisplay` je atribut ignorován.  
  
 V následující tabulce jsou uvedeny některé možné způsoby použití `DebuggerDisplay` atributů a ukázkových výstupů.  
  
|Atribut|Výstup se zobrazuje ve sloupci **hodnota** ).|  
|---------------|------------------------------------------------|  
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> Používá se pro typ s poli `x` a `y` .|`x = 5 y = 18`|  
|`[DebuggerDisplay("String value is {getString()}")]`Syntaxe parametru se může mezi jazyky lišit. Proto je používejte opatrně.|`String value is [5, 6, 6]`|  
  
 `DebuggerDisplay` může také přijmout pojmenované parametry.  
  
|Parametry|Účel|  
|----------------|-------------|  
|`Name`, `Type`|Tyto parametry ovlivňují sloupce **název** a **typ** v oknech proměnných. (Mohou být nastaveny na řetězce pomocí stejné syntaxe jako konstruktor.) Tyto parametry jsou převedené nebo nesprávně používané, můžou způsobit matoucí výstup.|  
|`Target`, `TargetTypeName`|Určuje cílový typ, pokud je atribut použit na úrovni sestavení.|  
  
 Soubor autoexp.cs používá atribut DebuggerDisplay na úrovni sestavení. Soubor autoexp.cs určuje výchozí rozšíření, které Visual Studio používá pro objekty .NET. Můžete si prohlédnout soubor autoexp.cs, kde najdete příklady použití atributu DebuggerDisplay, nebo můžete upravit a zkompilovat soubor autoexp.cs pro změnu výchozích rozšíření. Nezapomeňte soubor autoexp.cs před úpravou zálohovat.  
  
 Pokud chcete sestavit autoexp.cs, otevřete Developer Command Prompt pro VS2015 a spusťte následující příkazy.  
  
```  
cd <directory containing autoexp.cs>  
csc /t:library autoexp.cs  
```  
  
 Změny autoexp.dll budou v další relaci ladění vyzvednuty.  
  
## <a name="using-expressions-in-debuggerdisplay"></a>Použití výrazů v DebuggerDisplay  
 I když můžete použít obecný výraz mezi závorkami v atributu DebuggerDisplay, tento postup se nedoporučuje.  
  
 Obecný výraz v DebuggerDisplay má implicitní přístup k `this` ukazateli pro aktuální instanci cílového typu. Výraz nemá přístup k aliasům, místním hodnotám nebo ukazatelům. Pokud výraz odkazuje na vlastnosti, atributy těchto vlastností nejsou zpracovány. Kód jazyka C# se například `[DebuggerDisplay("Object {count - 2}"`  zobrazí, `Object 6` Pokud bylo pole `count` 8.  
  
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
             return string.Format("("Object {0}", count - 2);  
        }      
    }  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak použít `DebuggerDisplay` spolu s `DebuggerBrowseable` a `DebuggerTypeProxy` . Při zobrazení v okně proměnných ladicího programu, jako je například okno **kukátka** , vytvoří rozšíření, které vypadá takto:  
  
|**Name**|**Hodnota**|**Typ**|  
|--------------|---------------|--------------|  
|Klíč|3|objekt {String}|  
|Hodnota|3|objekt {int}|  
  
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
    }    private string DebuggerDisplay    {        get { return "Count = " + hashtable.Count); }    }  
  
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
 [Použití používání DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md) atributů [vylepšení ladění pomocí atributů zobrazení ladicího programu](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)
