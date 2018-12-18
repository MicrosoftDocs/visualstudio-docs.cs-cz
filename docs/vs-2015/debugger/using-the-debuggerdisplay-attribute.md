---
title: Používání atributu DebuggerDisplay | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 9637bd2d2a057615fd758ecec80a914931822b64
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736875"
---
# <a name="using-the-debuggerdisplay-attribute"></a>Používání atributu DebuggerDisplay
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Diagnostics.DebuggerDisplayAttribute> Ovládací prvky zobrazení objektu, vlastnost nebo pole v oknech proměnných ladicího programu. Tento atribut lze použít pro typy delegátů, vlastnosti, pole a sestavení.  
  
 `DebuggerDisplay` Atribut má jeden argument, což je řetězec, který se zobrazí ve sloupci Hodnota pro instance daného typu. Tento řetězec může obsahovat složené závorky (`{` a `}`). Text v rámci dvojici závorek je vyhodnocen jako pole, vlastnosti nebo metody.  
  
 Pokud má třída překryté `ToString()` metoda, ladicí program používá metodu přepsané místo výchozího `{<typeName>}`. To znamená pokud mají přepsat `ToString()` metoda, ladicí program používá metodu přepsané místo výchozího`{<typeName>}`, a není nutné používat `DebuggerDisplay`. Pokud používáte obě, `DebuggerDisplay` atribut má přednost před přepsané `ToString()` metody.  
  
 Určuje, zda ladicí program vyhodnotí tomto implicitní `ToString()` volání závisí nastavení hlavního názvu uživatele v **nástroje / Možnosti / ladění** dialogové okno. Visual Basic neimplementuje tomto implicitní `ToString()` hodnocení.  
  
> [!IMPORTANT]
>  Pokud **zobrazit nezpracovanou strukturu objektů v oknech proměnných** zaškrtněte políčko v **nástroje/Možnosti / ladění** dialogové okno, pak bude `DebuggerDisplay` atribut se ignoruje.  
  
 V následující tabulce jsou uvedeny některé možné způsoby použití `DebuggerDisplay` atribut a příklad výstupy.  
  
|Atribut|Povolí, nebude výstup **hodnotu** sloupec)|  
|---------------|------------------------------------------------|  
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> Použít u typu s poli `x` a `y`.|`x = 5 y = 18`|  
|`[DebuggerDisplay("String value is {getString()}")]`Syntaxe parametru se může lišit mezi jazyky. Proto je používejte obezřetně.|`String value is [5, 6, 6]`|  
  
 `DebuggerDisplay` Můžete také přijmout pojmenované parametry.  
  
|Parametry|Účel|  
|----------------|-------------|  
|`Name`, `Type`|Tyto parametry mají vliv **název** a **typ** sloupce oknech proměnných. (To můžete udělat na řetězce pomocí stejné syntaxe jako konstruktor.) Matoucí výstup může způsobit nadměrné tyto parametry, nebo je nesprávně, používají.|  
|`Target`, `TargetTypeName`|Určuje cílový typ, když je atribut použit na úrovni sestavení.|  
  
 Soubor autoexp.cs používá atributu DebuggerDisplay na úrovni sestavení. Soubor autoexp.cs Určuje výchozí rozšíření, které Visual Studio používá pro objekty .NET. Můžete zkontrolovat soubor autoexp.cs příklady toho, jak pomocí atributu DebuggerDisplay, nebo můžete upravit a zkompilujte soubor autoexp.cs, chcete-li změnit výchozí rozšíření. Ujistěte se, že zálohování souboru autoexp.cs před zahájením úprav.  
  
 K vytvoření autoexp.cs, otevřete si příkazový řádek pro vývojáře pro VS2015 a spusťte následující příkazy  
  
```  
cd <directory containing autoexp.cs>  
csc /t:library autoexp.cs  
```  
  
 Aby se změny autoexp.dll neexistoval, použije v příští relaci ladění.  
  
## <a name="using-expressions-in-debuggerdisplay"></a>Použití výrazů v DebuggerDisplay  
 Přestože lze použít obecné výraz mezi závorkami v atributu DebuggerDisplay, tato praxe se nedoporučuje.  
  
 Obecné výrazu v DebuggerDisplay má implicitní přístup k `this` ukazatele pro aktuální instanci pouze cílového typu. Výraz nemá přístup k aliasy, místní hodnoty nebo ukazatele. Pokud výraz odkazuje na vlastnosti, atributy na tyto vlastnosti nejsou zpracovány. Například kód jazyka C# `[DebuggerDisplay("Object {count - 2}"` zobrazí `Object 6` Pokud pole `count` se 8.  
  
 Použití výrazů v DebuggerDisplay může vést k následujícím problémům:  
  
- Vyhodnocování výrazů je nejvíce náročná operace v ladicím programu a tento výraz je vyhodnocen pokaždé, když se zobrazí. To může způsobit problémy s výkonem v krokování kódu. Složitý výraz, který se používá k zobrazení hodnoty v kolekci nebo seznam například může být velmi pomalé. když je velký počet prvků.  
  
- Chyba při vyhodnocování výrazu jazyka aktuální rámec zásobníku a ne vyhodnocení jazyk, ve kterém byla vytvořená výraz jsou výrazy vyhodnocovány. To může způsobit nepředvídatelné výsledky, když jsou různé jazyky.  
  
- Vyhodnocení výrazu můžete změnit stav aplikace. Například výraz, který nastaví hodnotu vlastnosti mění hodnotu vlastnosti v provádění kódu.  
  
  Jeden způsob, jak snížit možné potíže vyhodnocení výrazu je tak, že vytvoříte privátní vlastnost, která provádí operace a vrátí hodnotu typu string. Atributu DebuggerDisplay lze následně zobrazí hodnota této vlastnosti privátní. Následující příklad implementuje tento model:  
  
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
 Následující příklad kódu ukazuje, jak používat `DebuggerDisplay`společně s `DebuggerBrowseable` a `DebuggerTypeProxy`. Při zobrazení v okně proměnné ladicího programu, například **Watch** okna, vyvolá rozšíření, který vypadá takto:  
  
|**Jméno**|**Hodnota**|**Typ**|  
|--------------|---------------|--------------|  
|Key|"tři"|objekt {string}|  
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
 [Používání atributu DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md) [rozšíření ladění pomocí atributů zobrazení ladicího programu](http://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)



