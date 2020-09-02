---
title: Refaktoring přejmenování (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0db7696268e5e3d24d005fbf35a08b330f2dc849
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667482"
---
# <a name="rename-refactoring-c"></a>Refaktoring pro přejmenování (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Refaktoring **je funkce** refaktoringu v integrovaném vývojovém prostředí (IDE) sady Visual Studio, která poskytuje snadný způsob přejmenování identifikátorů pro symboly kódu, jako jsou pole, lokální proměnné, metody, obory názvů, vlastnosti a typy. **Přejmenování** lze použít ke změně názvů v komentářích a v řetězcích a ke změně deklarací a volání identifikátoru.

> [!NOTE]
> Při použití správy zdrojového kódu pro sadu Visual Studio Získejte nejnovější verzi zdrojů předtím, než se pokusíte provést Refaktoring přejmenování.

 Refaktoring pro přejmenování je k dispozici z následujících funkcí sady Visual Studio:

|Příznak|Chování refaktoringu v integrovaném vývojovém prostředí|
|-------------|----------------------------------------|
|Editor kódu|V editoru kódu je Refaktoring pro přejmenování k dispozici, když umístíte kurzor na určité typy symbolů kódu. Pokud je kurzor na této pozici, můžete vyvolat příkaz **Přejmenovat** zadáním klávesové zkratky (Ctrl + r, Ctrl + r) nebo výběrem příkazu **Přejmenovat** z inteligentní nebo místní nabídky nebo z nabídky **Refaktorovat** .|
|zobrazení tříd|Když vyberete identifikátor v Zobrazení tříd, je refaktoring k dispozici v místní nabídce a v nabídce **Refaktorovat** .|
|prohlížeč objektů|Když vyberete identifikátor v Prohlížeč objektů, refaktoring je k dispozici pouze **z nabídky refaktoring** .|
|Mřížka vlastností Návrhář formulářů|V **mřížce vlastností** Návrhář formulářů se při změně názvu ovládacího prvku inicializuje operace přejmenování tohoto ovládacího prvku. Dialogové okno **Přejmenovat** se nezobrazí.|
|Průzkumník řešení|V **Průzkumník řešení**je v místní nabídce k dispozici příkaz **Přejmenovat** . Pokud vybraný zdrojový soubor obsahuje třídu, jejíž název třídy je stejný jako název souboru, můžete použít tento příkaz pro současné přejmenování zdrojového souboru a provedení refaktoringu přejmenování.<br /><br /> Například pokud vytvoříte výchozí aplikaci založenou na systému Windows a pak přejmenujete Form1.cs na TestForm.cs, název zdrojového souboru Form1.cs se změní na TestForm.cs a na třídu Form1 a všechny odkazy na tuto třídu budou přejmenovány na TestForm. **Poznámka:**  Příkaz **zpět** (CTRL + Z) vrátí zpět Refaktoring přejmenování pouze v kódu a nezmění se název souboru zpátky na původní název. <br /><br /> Pokud vybraný zdrojový soubor neobsahuje třídu, jejíž název je stejný jako název souboru, příkaz **Přejmenovat** v **Průzkumník řešení** bude přejmenován pouze zdrojový soubor a nebude provádět Refaktoring přejmenování.|

## <a name="rename-operations"></a>Operace přejmenování
 Při spuštění **přejmenování**modul refaktoringu provede operaci přejmenování specifickou pro každý symbol kódu, jak je popsáno v následující tabulce.

|Symbol kódu|Operace přejmenování|
|-----------------|----------------------|
|Pole|Změní deklaraci a použití pole na nový název.|
|Lokální proměnná|Změní deklaraci a použití proměnné na nový název.|
|Metoda|Změní název metody a všechny odkazy na tuto metodu na nový název. **Poznámka:**  Při přejmenování metody rozšíření se operace přejmenování rozšíří na všechny instance metody, které jsou v oboru, bez ohledu na to, zda je metoda rozšíření používána jako statická metoda nebo metoda instance. Další informace naleznete v tématu [metody rozšíření](https://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51).|
|Obor názvů|Změní název oboru názvů na nový název v deklaraci, všechny `using` příkazy a plně kvalifikované názvy. **Poznámka:**  Při přejmenování oboru názvů [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] také aktualizuje výchozí vlastnost **oboru názvů** na stránce **aplikace** v **Návrháři projektu**. Tuto vlastnost nelze obnovit výběrem možnosti **zpět** v nabídce **Upravit** . Chcete-li obnovit výchozí hodnotu vlastnosti **oboru názvů** , je nutné upravit vlastnost v **Návrháři projektu**. Další informace najdete na [stránce aplikace](../ide/reference/application-page-project-designer-csharp.md).|
|Vlastnost|Změní deklaraci a použití vlastnosti na nový název.|
|Typ|Změní všechny deklarace a všechna použití typu na nový název, včetně konstruktorů a destruktorů. U částečných typů se operace přejmenování rozšíří na všechny části.|

#### <a name="to-rename-an-identifier"></a>Přejmenování identifikátoru

1. Vytvořte konzolovou aplikaci s názvem `RenameIdentifier` a nahraďte `Program` následující ukázkový kód.

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

2. Umístěte kurzor na `MethodB` , a to buď v deklaraci metody, nebo v volání metody.

3. V nabídce **refaktoring** vyberte **Přejmenovat**. Zobrazí se dialogové okno **Přejmenovat** .

     Můžete také kliknout pravým tlačítkem myši na kurzor, Ukázat na **Refaktorovat** v místní nabídce a potom kliknutím na tlačítko **Přejmenovat** zobrazit dialogové okno **Přejmenovat** .

4. Do pole **nové jméno** zadejte `MethodC` .

5. Zaškrtněte políčko **Hledat v komentářích** .

6. Klikněte na **OK**.

7. V dialogovém okně **Náhled změn** klikněte na **použít**.

#### <a name="to-rename-an-identifier-using-smart-tags"></a>Přejmenování identifikátoru pomocí inteligentních značek

1. Vytvořte konzolovou aplikaci s názvem `RenameIdentifier` a nahraďte `Program` následující ukázkový kód.

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

2. V deklaraci pro `MethodB` Zadejte typ nebo BACKSPACE přes identifikátor metody. Pod tímto identifikátorem se zobrazí výzva k zadání inteligentních značek.

    > [!NOTE]
    > Refaktorování přejmenování lze vyvolat pouze pomocí inteligentních značek v deklaraci identifikátoru.

3. Zadejte klávesovou zkratku SHIFT + ALT + F10 a potom stisknutím šipky dolů zobrazte nabídku inteligentních značek.

     -nebo-

     Chcete-li zobrazit inteligentní značku, přesuňte ukazatel myši na výzvu inteligentních značek. Pak přesuňte ukazatel myši na inteligentní značku a kliknutím na šipku dolů zobrazte nabídku inteligentní značky.

4. Vyberte položku nabídky **Přejmenovat \<identifer1> do \<identifier2> a** vyvolejte Refaktoring přejmenování bez náhledu změn kódu. Všechny odkazy na se **\<identifer1>** automaticky aktualizují na **\<identifier2>** .

     -nebo-

     Vyberte položku nabídky **Přejmenovat s náhledem** pro vyvolání refaktoringu přejmenování s náhledem změn kódu. Zobrazí se dialogové okno **Náhled změn** .

## <a name="remarks"></a>Poznámky

## <a name="renaming-implemented-or-overridden-members"></a>Přejmenování implementovaných nebo přepsaných členů
 Při **přejmenování** člena, který implementuje nebo Přepisuje nebo je implementován/přepsáno členy v jiných typech, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zobrazí dialogové okno s informacemi o tom, že operace přejmenování způsobí kaskádové aktualizace. Pokud kliknete na tlačítko **pokračovat**, modul refaktoringu rekurzivně vyhledá a přejmenuje všechny členy v základních a odvozených typech, které mají implementovány nebo potlačuje vztahy s přejmenovaným členem.

 Následující příklad kódu obsahuje členy s implementací nebo potlačením vztahů.

 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]

 V předchozím příkladu přejmenování `C.Method()` přejmenuje také, `Ibase.Method()` protože `C.Method()` implementuje `Ibase.Method()` . Dále refaktoring Engine rekurzivně uvidí, že `Ibase.Method()` je implementován pomocí `Derived.Method()` a přejmenuje `Derived.Method()` . Refaktoring Engine neprovádí přejmenování `Base.Method()` , protože `Derived.Method()` nepřepisuje `Base.Method()` . Modul refaktoringu se tady zastaví, pokud jste v dialogovém okně **Přejmenovat** nezaškrtli možnost přejmenovat **přetížení** .

 Pokud je zaškrtnuto políčko **Přejmenovat přetížení** , refaktoring Engine přejmenuje `Derived.Method(int i)` , protože přetěžuje, `Derived.Method()` `Base.Method(int i)` protože je přepsáno `Derived.Method(int i)` a `Base.Method()` protože je přetížení `Base.Method(int i)` .

> [!NOTE]
> Při přejmenování člena, který byl definován v odkazovaném sestavení, dialogové okno vysvětluje, že při přejmenování dojde k chybám sestavení.

## <a name="renaming-properties-of-anonymous-types"></a>Přejmenování vlastností anonymních typů
 Při přejmenování vlastnosti v anonymních typech se operace přejmenování rozšíří na vlastnosti v jiných anonymních typech, které mají stejné vlastnosti. Následující příklady ilustrují toto chování.

```csharp
var a = new { ID = 1};
var b = new { ID = 2};
```

 V předchozím kódu `ID` se přejmenování změní `ID` v obou příkazech, protože mají stejný základní anonymní typ.

```csharp
var companyIDs =
    from c in companylist
    select new { ID = c.ID, Name = c.Name};

var orderIDs =
    from o in orderlist
    select new { ID = o.ID, Item = o.Name};
```

 V předchozím kódu přejmenování `ID` bude přejmenován pouze jedna instance, `ID` protože `companyIDs` a nemají `orderIDs` stejné vlastnosti.

## <a name="see-also"></a>Viz také
 [Refaktoring (C#)](../csharp-ide/refactoring-csharp.md) [anonymní typy](https://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b)