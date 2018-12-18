---
title: Refaktoring pro přejmenování (C#) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d88cf6d88f23a3a079d5f9a556c316a204c9ef27
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49274960"
---
# <a name="rename-refactoring-c"></a>Refaktoring pro přejmenování (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Přejmenovat** je refaktoringu funkce v sadě Visual Studio integrovaného vývojového prostředí (IDE), která poskytuje snadný způsob, jak přejmenovat identifikátory pro symboly kód například pole, lokálních proměnných, metod, obory názvů, vlastností a typy. **Přejmenovat** lze použít, chcete-li změnit názvy v komentářích a v řetězcích a ke změně deklarace a volání identifikátoru.  
  
> [!NOTE]
>  Při použití správy zdrojového kódu pro Visual Studio, získejte nejnovější verzi zdroje předtím, než se pokusíte provést refaktoring pro přejmenování.  
  
 Refaktoring pro přejmenování je k dispozici následující funkce sady Visual Studio:  
  
|Funkce|Chování refaktoring v prostředí IDE|  
|-------------|----------------------------------------|  
|Editor kódu|V editoru kódu, refaktoring pro přejmenování je k dispozici při umístění kurzoru na určitých typech kódu symboly. Když je ukazatel myši na této pozici, můžete vyvolat **přejmenovat** příkaz tak, že zadáte klávesové zkratky (CTRL + R, CTRL + R), nebo tak, že vyberete **přejmenovat** z inteligentních značek, místní nabídce nebo  **Refaktorovat** nabídky.|  
|zobrazení tříd|Když vyberete identifikátor v zobrazení tříd, refaktoring pro přejmenování je k dispozici v místní nabídce a **Refaktorovat** nabídky.|  
|prohlížeč objektů|Když vyberete identifikátor v prohlížeči objektů, refaktoring pro přejmenování je k dispozici jen **Refaktorovat** nabídky.|  
|Mřížky vlastností návrháře formulářů Windows|V **mřížky vlastností** Návrháře formulářů Windows, mění se název ovládacího prvku opraví, zahájí se operace přejmenování pro tento ovládací prvek. **Přejmenovat** dialogové okno se nezobrazí.|  
|Průzkumník řešení|V **Průzkumníka řešení**, **přejmenovat** příkaz je k dispozici v místní nabídce. Vybraný zdrojový soubor obsahuje třídy, jejíž název třídy je stejný jako název souboru, můžete tento příkaz současně přejmenování zdrojového souboru a provést refaktoring pro přejmenování.<br /><br /> Například pokud vytvoříte výchozí aplikace založené na Windows a potom přejmenujte soubor Form1.cs na TestForm.cs, název zdrojového souboru Form1.cs se změní na TestForm.cs a class Form1 a všechny odkazy na třídu, se přejmenují na TestForm. **Poznámka:** **zpět** pouze zruší, refaktoring pro přejmenování v kódu a se nezměnil název souboru zpět na původní název příkazu (CTRL + Z). <br /><br /> Pokud vybraný zdrojový soubor neobsahuje třídu, jejíž název je stejný jako název souboru **přejmenovat** v **Průzkumníka řešení** pouze přejmenuje zdrojový soubor a přejmenování nebude spuštěno. refaktoring.|  
  
## <a name="rename-operations"></a>Operace přejmenování  
 Při spuštění **přejmenovat**, refaktoringu modul provádí konkrétní operace přejmenování pro každý kód symbol, jak je popsáno v následující tabulce.  
  
|Symbol v kódu|Operace přejmenování|  
|-----------------|----------------------|  
|Pole|Deklarace a použití tohoto pole se změní na nový název.|  
|Lokální proměnná|Deklarace a použití proměnné se změní na nový název.|  
|Metoda|Název metody a všechny odkazy na metody změní na nový název. **Poznámka:** při přejmenování rozšiřující metoda operaci přejmenování šíří do všech instancí metody, které jsou v oboru, bez ohledu na to, zda rozšiřující metoda se používá jako statickou metodu nebo metodu instance. Další informace najdete v tématu [rozšiřující metody](http://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51).|  
|Obor názvů|Název oboru názvů se změní na nový název v deklaraci všech `using` příkazy a plně kvalifikované názvy. **Poznámka:** při přejmenování obor názvů, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rovněž aktualizuje **výchozí Namespace** vlastnost **aplikace** stránku **Návrháře projektu**. Tuto vlastnost nelze obnovit tak, že vyberete **zpět** z **upravit** nabídky. Chcete-li obnovit **výchozí Namespace** hodnotu vlastnosti, je třeba upravit vlastnosti v **Návrháře projektu**. Další informace najdete v tématu [stránky aplikace](../ide/reference/application-page-project-designer-csharp.md).|  
|Vlastnost|Deklarace a použití vlastnost se změní na nový název.|  
|Typ|Všechny deklarace a použití všech typu se změní na nový název, včetně konstruktorů a destruktorů. Pro částečné typy operace přejmenování rozšíří do všech částí.|  
  
#### <a name="to-rename-an-identifier"></a>Chcete-li přejmenovat identifikátor  
  
1.  Vytvořte konzolovou aplikaci s názvem `RenameIdentifier`a potom nahraďte `Program` pomocí následujícího ukázkového kódu.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Umístěte kurzor na `MethodB`, buď v deklaraci metody nebo volání metody.  
  
3.  Z **Refaktorovat** nabídce vyberte možnost **přejmenovat**. **Přejmenovat** zobrazí se dialogové okno.  
  
     Můžete také kliknout pravým tlačítkem kurzor, přejděte na **Refaktorovat** na místní nabídku a pak klikněte na tlačítko **přejmenovat** zobrazíte **přejmenovat** dialogové okno.  
  
4.  V **nový název** zadejte `MethodC`.  
  
5.  Vyberte **vyhledávání v komentářích** zaškrtávací políčko.  
  
6.  Klikněte na tlačítko **OK**.  
  
7.  V **náhled změn** dialogové okno, klikněte na tlačítko **použít**.  
  
#### <a name="to-rename-an-identifier-using-smart-tags"></a>Chcete-li přejmenovat identifikátor pomocí inteligentních značek  
  
1.  Vytvořte konzolovou aplikaci s názvem `RenameIdentifier`a potom nahraďte `Program` pomocí následujícího ukázkového kódu.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  V deklaraci pro `MethodB`, typ nebo smažte vše přes metoda identifikátor. Inteligentní značky řádku se zobrazí pod tento identifikátor.  
  
    > [!NOTE]
    >  Lze vyvolat pouze refaktoring pro přejmenování pomocí inteligentních značek v deklaraci identifikátoru.  
  
3.  Zadejte klávesovou zkratku SHIFT + ALT + F10 a stiskněte klávesu šipka dolů k zobrazení v nabídce inteligentních značek.  
  
     -nebo-  
  
     Přesuňte ukazatel myši nad inteligentní značky řádku zobrazíte inteligentních značek. Potom přesuňte ukazatel myši nad inteligentních značek a klikněte na šipku dolů a zobrazit v nabídce inteligentních značek.  
  
4.  Vyberte **přejmenovat '\<identifer1 >' k '\<identifier2 >'** položku nabídky, která se má vyvolat, refaktoring pro přejmenování bez změny kódu ve verzi preview. Všechny odkazy na  **\<identifer1 >** se automaticky aktualizují na  **\<identifier2 >**.  
  
     -nebo-  
  
     Vyberte **přejmenujte je tak ve verzi preview** položku nabídky, která se má vyvolat, refaktoring pro přejmenování se náhled změn kódu. **Náhled změn** se zobrazí dialogové okno.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="renaming-implemented-or-overridden-members"></a>Přejmenování členů neimplementovala nebo je přepsaná  
 Když jste **přejmenovat** člena, který implementuje/přepsání nebo je implementováno/přepsat členy v jiných typech [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zobrazí dialogové okno s upozorněním, způsobí, že operace přejmenování kaskádové aktualizace. Vyberete-li **pokračovat**, refaktoringu rekurzivně modul najde a přejmenuje všechny členy v základní a odvozené typy, které mají implementuje/přepsání vztahy s členem se přejmenovat.  
  
 Následující příklad kódu obsahuje členy implementuje/přepsání relace.  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]  
  
 V předchozím příkladu přejmenování `C.Method()` také přejmenuje `Ibase.Method()` protože `C.Method()` implementuje `Ibase.Method()`. V dalším kroku se zobrazí rekurzivně Refaktorujte modul, který `Ibase.Method()` je implementováno `Derived.Method()` a přejmenuje `Derived.Method()`. Modul Refaktorujte nedojde k přejmenování `Base.Method()`, protože `Derived.Method()` nepřepisuje `Base.Method()`. Modul refaktoringu se tady zastaví pokud nemáte **přejmenovat přetížení** vráceny se změnami **přejmenovat** dialogové okno.  
  
 Pokud **přejmenovat přetížení** je zaškrtnuto, přejmenuje modul Refaktorujte `Derived.Method(int i)` protože přetěžuje `Derived.Method()`, `Base.Method(int i)` vzhledem k tomu, že je přepsána `Derived.Method(int i)`, a `Base.Method()` vzhledem k tomu, že je přetížení `Base.Method(int i)`.  
  
> [!NOTE]
>  Při přejmenování člena, který byl definován v odkazovaném sestavení dialogové okno vysvětluje, že se přejmenování způsobit chyby buildu.  
  
## <a name="renaming-properties-of-anonymous-types"></a>Přejmenování vlastností anonymních typů  
 Při přejmenování vlastností anonymních typů operaci přejmenování rozšíří na vlastnosti v jiných anonymní typy, které mají stejné vlastnosti. Toto chování ilustrují následující příklady.  
  
```csharp  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 V předchozím kódu přejmenování `ID` změní `ID` v obou příkazů protože mají stejný základní anonymního typu.  
  
```csharp  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 V předchozím kódu přejmenování `ID` přejmenuje pouze jedna instance `ID` protože `companyIDs` a `orderIDs` nemají stejné vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 [Refaktoring (C#)](../csharp-ide/refactoring-csharp.md)   
 [Anonymní typy](http://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b)