---
title: Vytváření vlastních zobrazení objektů C++
description: Použití rozhraní Natvis k přizpůsobení způsobu, jakým Visual Studio zobrazuje nativní typy v ladicím programu
ms.date: 10/31/2018
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: c38ff2fcc762ccc202e2a02ecd36e942db75ad3d
ms.sourcegitcommit: ab18c9d850192fc9ccec10961f1126e8b0cba8da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73061083"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Vytváření vlastních zobrazení C++ objektů v ladicím programu pomocí architektury Natvis

Rozhraní Visual Studio *Natvis* přizpůsobuje způsob, jakým se v oknech proměnných ladicího programu zobrazují nativní typy, jako jsou **místní** a **sledovací** okna a v části **datatipů**. Vizualizace Natvis mohou přispět k vytváření lépe viditelných typů během ladění.

Natvis nahrazuje soubor *autoexp. dat* v dřívějších verzích sady Visual Studio se syntaxí XML, lepší diagnostikou, správou verzí a podporou více souborů.

## <a name="BKMK_Why_create_visualizations_"></a>Vizualizace Natvis

Pomocí architektury Natvis vytvoříte pravidla vizualizace pro typy, které vytvoříte, aby se vývojáři mohli snadněji zobrazit během ladění.

Například následující ilustrace ukazuje proměnnou typu [Windows:: UI:: XAML:: Controls:: TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) v okně ladicího programu, aniž by byly aplikovány vlastní vizualizace.

![Výchozí vizualizace textového pole](../debugger/media/dbg_natvis_textbox_default.png "Výchozí vizualizace textového pole")

Zvýrazněný řádek zobrazuje vlastnost `Text` třídy `TextBox`. Složitá hierarchie tříd usnadňuje vyhledání této vlastnosti. Ladicí program neví, jak interpretovat typ vlastního řetězce, takže se nezobrazuje řetězec umístěný uvnitř textového pole.

Stejný `TextBox` v okně proměnných vypadá mnohem jednodušší, když se používají pravidla vlastního Vizualizátoru pro Natvis. Důležité členy třídy se zobrazí společně a ladicí program zobrazí základní řetězcovou hodnotu vlastního typu řetězce.

![Data textového pole používající Vizualizér](../debugger/media/dbg_natvis_textbox_visualizer.png "Data textového pole používající Vizualizér")

## <a name="BKMK_Using_Natvis_files"></a>Použití souborů. Natvis v C++ projektech

Natvis používá k určení pravidel vizualizací soubory *. Natvis* . Soubor *. Natvis* je soubor XML s příponou *. Natvis* . Schéma natvis je definováno v *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*.

Základní strukturou souboru *. Natvis* je jeden nebo více `Type` prvků představujících položky vizualizace. Plně kvalifikovaný název každého prvku `Type` je určen v atributu `Name`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
  <Type Name="MyNamespace::CFoo">
    .
    .
  </Type>

  <Type Name="...">
    .
    .
  </Type>
</AutoVisualizer>
```

Visual Studio poskytuje některé soubory *. Natvis* ve složce *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers* . Tyto soubory mají pravidla vizualizace pro mnoho běžných typů a můžou sloužit jako příklady pro psaní vizualizací pro nové typy.

### <a name="add-a-natvis-file-to-a-c-project"></a>Přidání souboru. Natvis do C++ projektu

Do libovolného C++ projektu můžete přidat soubor *. Natvis* .

**Postup přidání nového souboru *Natvis* :**

1. Vyberte uzel C++ projektu v **Průzkumník řešení**a vyberte **projekt**  > **Přidat novou položku**nebo klikněte pravým tlačítkem myši na projekt a vyberte **Přidat**  > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte **Visual C++**   > **Utility**  > **soubor vizualizace ladicího programu (. Natvis)** .

1. Zadejte název souboru a vyberte **Přidat**.

   Nový soubor se přidá do **Průzkumník řešení**a otevře se v podokně dokumentu sady Visual Studio.

Ladicí program sady Visual Studio načítá soubory *. Natvis* v C++ projektech automaticky a ve výchozím nastavení je obsahuje také v souboru *. pdb* při sestavení projektu. Pokud ladíte sestavenou aplikaci, ladicí program načte soubor *. Natvis* ze souboru *. pdb* , i když projekt ještě nemáte otevřený. Pokud nechcete, aby soubor *. Natvis* byl součástí souboru. *PDB*, můžete ho vyloučit z vytvořeného souboru *. pdb* .

**Vyloučení souboru *. Natvis* z *PDB*:**

1. V **Průzkumník řešení**vyberte soubor *. Natvis* a vyberte ikonu **vlastnosti** , nebo klikněte pravým tlačítkem na soubor a vyberte **vlastnosti**.

1. Přetáhněte šipku vedle seznamu **vyloučené ze sestavení** a vyberte možnost **Ano**a pak vyberte **OK**.

>[!NOTE]
>Pro ladění spustitelných projektů použijte položky řešení k přidání jakýchkoli souborů *. Natvis* , které nejsou v souboru *. pdb*, protože není k dispozici C++ žádný projekt.

>[!NOTE]
>Pravidla Natvis načtená ze souboru *. pdb* se vztahují pouze na typy v modulech, na které odkazuje soubor *. pdb* . Například pokud má *Module1. pdb* položku Natvis pro typ s názvem `Test`, vztahuje se pouze na třídu `Test` v souboru *Module1. dll*. Pokud jiný modul definuje také třídu s názvem `Test`, položka Natvis pro *Module1. pdb* se na ni nevztahuje.

### <a name="BKMK_natvis_location"></a>Umístění souborů Natvis

Pokud chcete, aby se soubory *. Natvis* mohly použít pro více projektů, můžete je přidat do adresáře uživatelů nebo do systémového adresáře.

Soubory *. Natvis* jsou vyhodnocovány v následujícím pořadí:

1. Všechny soubory *. Natvis* , které jsou vloženy do souboru *. pdb* , který ladíte, pokud soubor se stejným názvem v načteném projektu neexistuje.

2. Všechny soubory *. Natvis* , které jsou v načteném C++ projektu nebo řešení nejvyšší úrovně. Tato skupina zahrnuje všechny načtené C++ projekty, včetně knihoven tříd, ale ne projektů v jiných jazycích.

::: moniker range="vs-2017"

3. Adresář Natvis konkrétního uživatele (například *%UserProfile%\Documents\Visual Studio 2017 \ vizualizujes*).

::: moniker-end

::: moniker range=">= vs-2019"

3. Adresář Natvis konkrétního uživatele (například *%UserProfile%\Documents\Visual Studio 2019 \ vizualizujes*).

::: moniker-end

4. Adresář Natvis pro systém v rámci systému ( *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Tento adresář obsahuje soubory *. Natvis* , které jsou nainstalovány se sadou Visual Studio. Pokud máte oprávnění správce, můžete do tohoto adresáře přidat soubory.

## <a name="modify-natvis-files-while-debugging"></a>Upravovat soubory. Natvis během ladění

Během ladění projektu můžete upravit soubor *. Natvis* v integrovaném vývojovém prostředí (IDE). Otevřete soubor ve stejné instanci aplikace Visual Studio, kterou ladíte, upravte a uložte. Jakmile se soubor uloží, Windows Update **sledování** a **místní** aktualizace projeví změnu.

Můžete také přidat nebo odstranit soubory *. Natvis* v řešení, které ladíte, a Visual Studio přidá nebo odebere příslušné vizualizace.

Při ladění nemůžete aktualizovat soubory *. Natvis* vložené do souborů *. pdb* .

Pokud upravíte soubor *. Natvis* mimo sadu Visual Studio, změny se neprojeví automaticky. Chcete-li aktualizovat okna ladicího programu, můžete znovu vyhodnotit příkaz **. natvisreload** v okně **kukátko** . Změny se projeví i bez restartování ladicí relace.

K upgradu souboru *. Natvis* na novější verzi použijte taky příkaz **. natvisreload** . Například soubor *. Natvis* může být zkontrolován do správy zdrojového kódu a chcete si vybrat poslední změny, které udělal někdo jiný.

## <a name="BKMK_Expressions_and_formatting"></a>Výrazy a formátování
Vizualizace Natvis používají C++ výrazy k určení datových položek, které se mají zobrazit. Kromě vylepšení a omezení C++ výrazů v ladicím programu, které jsou popsány v [kontextovém operátoruC++()](../debugger/context-operator-cpp.md), je třeba mít na paměti následující:

- Výrazy Natvis jsou vyhodnocovány v kontextu objektu, který je vizuálů, nikoli aktuálního rámce zásobníku. Například `x` ve výrazu Natvis odkazuje na pole s názvem **x** v objektu, který je vizuálů, nikoli na místní proměnnou s názvem **x** v aktuální funkci. K místním proměnným ve výrazech Natvis nemůžete přistupovat, i když máte přístup k globálním proměnným.

- Výrazy Natvis nepovolují vyhodnocení funkce ani vedlejší účinky. Volání funkce a operátory přiřazení jsou ignorovány. Vzhledem k tomu, že [vnitřní funkce ladicího programu](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) mají volné vedlejší účinky, mohou být volně volány z jakéhokoli výrazu Natvis, i když nejsou povolena jiná volání funkcí.

- Chcete-li určit, jak se výraz zobrazí, můžete použít libovolný specifikátor formátu popsaný v [specifikátorech formátu v C++ ](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Specifikátory formátu jsou ignorovány, pokud je položka používána interně pomocí Natvis, jako je například výraz `Size` v [rozšíření ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

## <a name="natvis-views"></a>Zobrazení Natvis

Můžete definovat různá zobrazení Natvis pro zobrazení typů různými způsoby. Například zde je vizualizace `std::vector` definující zjednodušené zobrazení s názvem `simple`. `DisplayString` a `ArrayItems` prvky se zobrazí ve výchozím zobrazení a v zobrazení `simple`, zatímco položky `[size]` a `[capacity]` se v zobrazení `simple` nezobrazují.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

V okně **kukátko** použijte specifikátor formátu **zobrazení** k určení alternativního zobrazení. Jednoduché zobrazení se zobrazí jako **vec, zobrazení (jednoduché)** :

![okno Kukátko s jednoduchým zobrazením](../debugger/media/watch-simpleview.png "okno Kukátko s jednoduchým zobrazením")

## <a name="BKMK_Diagnosing_Natvis_errors"></a>Chyby Natvis

Když ladicí program narazí na chyby v položce vizualizace, ignoruje je. Buď zobrazí typ v nezpracované podobě, nebo vybere jinou vhodnou vizualizaci. Pomocí diagnostiky Natvis můžete zjistit, proč ladicí program ignoroval položku vizualizace, a zobrazit základní syntaxi a chyby při analýze.

**Zapnutí diagnostiky Natvis:**

- V **nabídce nástroje**  > **Možnosti** (nebo **ladění** **možností** > ) > **ladění**  > **okno výstup**, nastavte **diagnostické zprávy NatvisC++ (pouze)** na **Chyba**, **Upozornění** nebo **verbose**a pak vyberte **OK**.

Chyby se zobrazí v okně **výstup** .

## <a name="BKMK_Syntax_reference"></a>Odkaz syntaxe Natvis

### <a name="BKMK_AutoVisualizer"></a>Element autovizualizuje
Element `AutoVisualizer` je kořenovým uzlem souboru *. Natvis* a obsahuje atribut namespace `xmlns:`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

Element `AutoVisualizer` může mít podřízené položky [Type](#BKMK_Type), [HRESULT](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer)a [CustomVisualizer](#BKMK_CustomVisualizer) .

### <a name="BKMK_Type"></a>Element Type

Základní `Type` vypadá jako v tomto příkladu:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 Element `Type` určuje:

1. Jaký typ vizualizace má být použit pro (atribut `Name`).

2. Jak hodnota objektu tohoto typu by měla vypadat (`DisplayString` element).

3. Jak by měly členové typu vypadat, když uživatel rozbalí typ v okně proměnné (`Expand` uzel).

#### <a name="templated-classes"></a>Třídy šablon
Atribut `Name` elementu `Type` přijímá hvězdičku `*` jako zástupný znak, který lze použít pro názvy tříd šablon.

V následujícím příkladu je použita stejná vizualizace, je-li objekt `CAtlArray<int>` nebo `CAtlArray<float>`. Pokud existuje určitá položka vizualizace pro `CAtlArray<float>`, má přednost před obecným.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Můžete odkazovat na parametry šablony v položce vizualizace pomocí maker $T 1, $T 2 a tak dále. Příklady těchto maker naleznete v souborech *. Natvis* dodaných se sadou Visual Studio.

#### <a name="BKMK_Visualizer_type_matching"></a>Shoda typu Vizualizátor
Pokud se položka vizualizace nedokáže ověřit, použije se další dostupná vizualizace.

#### <a name="inheritable-attribute"></a>Dědičný atribut
Volitelný atribut `Inheritable` určuje, zda vizualizace platí pouze pro základní typ, nebo na základní typ a všechny odvozené typy. Výchozí hodnota `Inheritable` je `true`.

V následujícím příkladu se vizualizace vztahuje pouze na typ `BaseClass`:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Priorita – atribut

Nepovinný `Priority` atribut určuje pořadí, ve kterém se mají použít alternativní definice, pokud se definice nedokáže analyzovat. Možné hodnoty `Priority` jsou: `Low`, `MediumLow`, `Medium`, `MediumHigh` a `High`. Výchozí hodnota je `Medium`. Atribut `Priority` rozlišuje pouze priority v rámci stejného souboru *Natvis* .

Následující příklad nejprve analyzuje položku, která se shoduje s 2015 STL. Pokud se to nepovede analyzovat, používá alternativní položku pro verzi 2013 STL:

```xml
<!-- VC 2013 -->
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">
     <DisplayString>{_Callee}</DisplayString>
    <Expand>
        <ExpandedItem>_Callee</ExpandedItem>
    </Expand>
</Type>

<!-- VC 2015 -->
<Type Name="std::reference_wrapper&lt;*&gt;">
    <DisplayString>{*_Ptr}</DisplayString>
    <Expand>
        <Item Name="[ptr]">_Ptr</Item>
    </Expand>
</Type>
```

### <a name="optional-attribute"></a>Volitelný atribut
Atribut `Optional` můžete umístit na libovolný uzel. Pokud se dílčí výraz uvnitř volitelného uzlu nedokáže analyzovat, ladicí program tento uzel ignoruje, ale použije zbývající pravidla `Type`. V následujícím typu `[State]` není nepovinný, ale `[Exception]` je volitelná.  Pokud `MyNamespace::MyClass` obsahuje pole s názvem _`M_exceptionHolder`, zobrazí se uzel `[State]` i uzel `[Exception]`, ale pokud není k dispozici žádné `_M_exceptionHolder` pole, zobrazí se pouze uzel `[State]`.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="BKMK_Condition_attribute"></a>Atribut Condition

Volitelný atribut `Condition` je k dispozici pro mnoho prvků vizualizace a určuje, kdy použít pravidlo vizualizace. Pokud se výraz uvnitř atributu Condition přeloží na `false`, pravidlo vizualizace se nepoužije. Pokud se vyhodnotí jako `true` nebo neexistuje žádný `Condition` atribut, vizualizace se použije. Tento atribut lze použít pro logiku if-else v položkách vizualizace.

Například následující vizualizace má dva prvky `DisplayString` pro typ inteligentního ukazatele. Pokud je člen `_Myptr` prázdný, je podmínka prvního prvku `DisplayString` překládána na `true`, takže se formulář zobrazí. Pokud člen `_Myptr` není prázdný, je podmínka vyhodnocena jako `false`a druhý `DisplayString` prvek zobrazí.

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

### <a name="includeview-and-excludeview-attributes"></a>Atributy IncludeView a ExcludeView

Atributy `IncludeView` a `ExcludeView` určují prvky pro zobrazení nebo zobrazení v konkrétních zobrazeních. Například v následující specifikaci Natvis `std::vector``simple` zobrazení nezobrazí `[size]` a `[capacity]` položky.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

Můžete použít atributy `IncludeView` a `ExcludeView` na typech a na jednotlivých členech.

### <a name="BKMK_Versioning"></a>Element Version
Element `Version` Oboruje položku vizualizace na určitý modul a verzi. Element `Version` pomáhá předcházet kolizím názvů, omezuje neúmyslné neshody a umožňuje různé vizualizace pro různé verze typu.

Pokud společný hlavičkový soubor, který používá jiné moduly, definuje typ, vizualizace se správou verzí se zobrazí pouze v případě, že je typ v zadané verzi modulu.

V následujícím příkladu je vizualizace platná jenom pro `DirectUI::Border` typ, který najdete v `Windows.UI.Xaml.dll` od verze 1,0 do 1,5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Nepotřebujete `Min` i `Max`. Jsou to volitelné atributy. Nejsou podporovány žádné zástupné znaky.

Atribut `Name` má formát *filename. ext*, například *Hello. exe* nebo *nějaké. dll*. Nejsou povoleny žádné názvy cest.

### <a name="BKMK_DisplayString"></a>Element DisplayString
Element `DisplayString` určuje řetězec, který se zobrazí jako hodnota proměnné. Přijímá libovolné řetězce smíšené s výrazy. Vše uvnitř složených závorek je interpretováno jako výraz. Například následující `DisplayString` položku:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Znamená, že proměnné typu `CPoint` zobrazit jako na tomto obrázku:

 ![Použít element DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "Použít element DisplayString")

Ve výrazu `DisplayString` `x` a `y`, které jsou členy `CPoint`, jsou uvnitř složených závorek, takže jejich hodnoty jsou vyhodnocovány. Příklad také ukazuje, jak lze pomocí dvojitých složených závorek (`{{` nebo `}}`) uniknout složené závorky.

> [!NOTE]
> Element `DisplayString` je jediným prvkem, který přijímá libovolné řetězce a syntaxi složených závorek. Všechny ostatní prvky vizualizace přijímají pouze výrazy, které může ladicí program vyhodnotit.

### <a name="BKMK_StringView"></a>Element StringView

Element `StringView` definuje hodnotu, kterou může ladicí program odeslat do integrovaného Vizualizér textu. Například s ohledem na následující vizualizaci `ATL::CStringT` typ:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

Objekt `CStringT` se zobrazí v okně proměnné jako v tomto příkladu:

![CStringt – element DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringt – element DisplayString")

Přidání prvku `StringView` říká ladicímu programu, že může zobrazit hodnotu jako vizualizaci textu.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Během ladění můžete vybrat ikonu lupy vedle proměnné a pak vybrat **Vizualizér textu** pro zobrazení řetězce, na který odkazuje **m_pszData** .

 ![Data CStringt pomocí Vizualizér StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "Data CStringt pomocí Vizualizér StringView")

Výraz `{m_pszData,su}` obsahuje specifikátor C++ formátu **Su**pro zobrazení hodnoty jako řetězce Unicode. Další informace naleznete v tématu [specifikátory formátu v C++ ](../debugger/format-specifiers-in-cpp.md).

### <a name="BKMK_Expand"></a>Rozbalit element

Volitelný `Expand` uzel upravuje podřízené prvky vizuálního typu, když rozbalíte typ v okně proměnné. Uzel `Expand` přijímá seznam podřízených uzlů, které definují podřízené prvky.

- Pokud v položce vizualizace není zadán uzel `Expand`, podřízené položky použijí výchozí pravidla rozšíření.

- Pokud je uzel `Expand` zadán bez podřízených uzlů, nelze tento typ rozšířit v oknech ladicího programu.

#### <a name="BKMK_Item_expansion"></a>Rozšíření položky

 Element `Item` je nejzákladnější a společný prvek v uzlu `Expand`. `Item` definuje jeden podřízený element. Například třída `CRect` s poli `top`, `left`, `right` a `bottom` má následující položku vizualizace:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

V okně ladicího programu vypadá `CRect` typ jako v tomto příkladu:

![CRect s rozšířením elementu Item](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect s rozšířením elementu Item")

Ladicí program vyhodnotí výrazy zadané v prvcích `Width` a `Height` a zobrazí hodnoty ve sloupci **hodnota** v okně proměnné.

Ladicí program automaticky vytvoří uzel **[RAW View]** pro každé vlastní rozšíření. Předchozí snímek obrazovky zobrazuje rozbalený uzel **[nezpracované zobrazení]** , který ukazuje, jak se výchozí nezpracovaná zobrazení objektu liší od jeho vizualizace Natvis. Výchozí rozšíření vytvoří podstrom pro základní třídu a seznam všech datových členů základní třídy jako podřízených objektů.

> [!NOTE]
> Pokud se výraz elementu Item odkazuje na komplexní typ, lze uzel **položky** sám rozšířit.

#### <a name="BKMK_ArrayItems_expansion"></a>Rozšíření ArrayItems
Uzel `ArrayItems` použijte, pokud chcete, aby ladicí program sady Visual Studio interpretoval typ jako pole a zobrazil jeho jednotlivé prvky. Vizualizace pro `std::vector` je dobrým příkladem:

```xml
<Type Name="std::vector&lt;*&gt;">
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mylast - _Myfirst</Item>
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>
    <ArrayItems>
      <Size>_Mylast - _Myfirst</Size>
      <ValuePointer>_Myfirst</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

`std::vector` zobrazuje jeho jednotlivé prvky při rozbalení v okně proměnné:

![std:: Vector s použitím rozšíření ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std:: Vector s použitím rozšíření ArrayItems")

Uzel `ArrayItems` musí mít:

- Výraz `Size` (který se musí vyhodnotit na celé číslo) pro ladicí program pro pochopení délky pole.
- Výraz `ValuePointer`, který odkazuje na první prvek (který musí být ukazatelem typu elementu, který není `void*`).

Výchozí hodnota dolní meze pole je 0. Pro přepsání hodnoty použijte `LowerBound` element. Příklady jsou soubory *. Natvis* dodávané se sadou Visual Studio.

>[!NOTE]
>Operátor `[]`, například `vector[i]`, lze použít jako libovolnou jednoduchou vizualizaci pole, která používá `ArrayItems`, a to i v případě, že samotný typ (například `CATLArray`) nepovoluje Tento operátor.

Můžete také zadat multidimenzionální pole. V takovém případě ladicí program potřebuje poněkud více informací, aby správně zobrazoval podřízené prvky:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Direction>Forward</Direction>
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

- `Direction` určuje, zda je pole v pořadí podle řádků nebo hlavní verze sloupce.
- `Rank` určuje rozměr pole.
- Element `Size` přijímá implicitní parametr `$i`, který nahradí index dimenze, aby bylo možné najít délku pole v dané dimenzi. V předchozím příkladu by výraz `_M_extent.M_base[0]` měl poskytnout délku dimenze 0th, `_M_extent._M_base[1]` 1. a tak dále.

Tady je postup, jak v okně ladicího programu vypadá dvourozměrný `Concurrency::array` objekt:

![Dvourozměrné pole s rozšířením ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Dvourozměrné pole s rozšířením ArrayItems")

#### <a name="BKMK_IndexListItems_expansion"></a>Rozšíření IndexListItems

Rozšíření `ArrayItems` lze použít pouze v případě, že jsou prvky pole rozloženy souvisle v paměti. Ladicí program se dostane k dalšímu prvku jednoduchým zvýšením jeho ukazatele. Pokud potřebujete manipulovat s indexem na uzel hodnoty, použijte `IndexListItems` uzly. Tady je vizualizace s `IndexListItems`m uzlem:

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_M_vector._M_index</Item>
    <IndexListItems>
      <Size>_M_vector._M_index</Size>
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>
    </IndexListItems>
  </Expand>
</Type>
```

Jediným rozdílem mezi `ArrayItems` a `IndexListItems` je `ValueNode`, což očekává úplný výraz pro i<sup>th</sup> elementu s implicitním `$i`m parametrem.

>[!NOTE]
>Operátor `[]`, například `vector[i]`, lze použít jako libovolnou jednoduchou vizualizaci pole, která používá `IndexListItems`, a to i v případě, že samotný typ (například `CATLArray`) nepovoluje Tento operátor.

#### <a name="BKMK_LinkedListItems_expansion"></a>Rozšíření LinkedListItems

Pokud vizuální typ představuje propojený seznam, ladicí program může zobrazit jeho podřízené položky pomocí uzlu `LinkedListItems`. Následující vizualizace pro `CAtlList` typ používá `LinkedListItems`:

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>
  <Expand>
    <Item Name="Count">m_nElements</Item>
    <LinkedListItems>
      <Size>m_nElements</Size>
      <HeadPointer>m_pHead</HeadPointer>
      <NextPointer>m_pNext</NextPointer>
      <ValueNode>m_element</ValueNode>
    </LinkedListItems>
  </Expand>
</Type>
```

Element `Size` odkazuje na délku seznamu. `HeadPointer` odkazuje na první prvek, `NextPointer` odkazuje na další prvek a `ValueNode` odkazuje na hodnotu položky.

Ladicí program vyhodnocuje `NextPointer` a `ValueNode` výrazy v kontextu prvku `LinkedListItems` uzel, nikoli typu nadřazeného seznamu. V předchozím příkladu `CAtlList` má `CNode` třídu (nalezeno v `atlcoll.h`), která je uzlem propojeného seznamu. `m_pNext` a `m_element` jsou pole této `CNode` třídy, nikoli třída `CAtlList`.

`ValueNode` může být ponecháno prázdné nebo pomocí `this` odkazovat na samotný uzel `LinkedListItems`.

#### <a name="customlistitems-expansion"></a>Rozšíření CustomListItems
Rozšíření `CustomListItems` umožňuje napsat vlastní logiku pro procházení datové struktury, jako je například zatřiďovací tabulka. Pomocí `CustomListItems` Vizualizujte datové struktury, které mohou používat C++ výrazy pro všechno, co potřebujete k vyhodnocení, ale nedělejte si tvarovat pro `ArrayItems`, `IndexListItems` nebo `LinkedListItems`.

Následující Vizualizér pro `CAtlMap` je skvělým příkladem, kde je `CustomListItems` vhodný.

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>
    <Expand>
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">
        <Variable Name="iBucket" InitialValue="-1" />
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />
        <Variable Name="iBucketIncrement" InitialValue="-1" />

        <Size>m_nElements</Size>
        <Exec>pBucket = nullptr</Exec>
        <Loop>
          <If Condition="pBucket == nullptr">
            <Exec>iBucket++</Exec>
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>
            <Break Condition="iBucketIncrement == -1" />
            <Exec>iBucket += iBucketIncrement</Exec>
            <Exec>pBucket = m_ppBins[iBucket]</Exec>
          </If>
          <Item>pBucket,na</Item>
          <Exec>pBucket = pBucket->m_pNext</Exec>
        </Loop>
      </CustomListItems>
    </Expand>
</Type>
```

Můžete použít `Exec` k provedení kódu v rozšíření `CustomListItems` pomocí proměnných a objektů definovaných v rozšíření. Pomocí `Exec` můžete použít logické operátory, aritmetické operátory a operátory přiřazení. K vyhodnocení funkcí se nedá použít `Exec`.

`CustomListItems` podporuje následující vnitřní funkce:

- `strlen`, `wcslen`, `strnlen`, `wcsnlen`, `strcmp`, `wcscmp`, `_stricmp`, `_strcmpi`, `_wcsicmp`, `strncmp`, `wcsncmp`, `_strnicmp`, `_wcsnicmp`, `memcmp`, `memicmp`, `wmemcmp`, `strchr`, `wcschr`, `memchr`, `wmemchr`, `strstr`, `wcsstr`, `__log2`, `__findNonNull`
- `GetLastError`, `TlsGetValue`, `DecodeHString`, `WindowsGetStringLen`, `WindowsGetStringRawBuffer`, `WindowsCompareStringOrdinal`, `RoInspectCapturedStackBackTrace`, `CoDecodeProxy`, `GetEnvBlockLength`, `DecodeWinRTRestrictedException`, 0, 1, 2
- `ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)`
- `ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)`
- `ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `Stdext_HashMap_Int_OperatorBracket_idx`
- `Std_UnorderedMap_Int_OperatorBracket_idx`
- `TreeTraverse_Init // Initializes a new tree traversal`
- `TreeTraverse_Next // Returns nodes in a tree`
- `TreeTraverse_Skip // Skips nodes in a pending tree traversal`

#### <a name="BKMK_TreeItems_expansion"></a>Rozšíření TreeItems
 Pokud vizuální typ představuje strom, ladicí program může projít stromovou strukturou a zobrazit jeho podřízené položky pomocí uzlu `TreeItems`. Tady je vizualizace `std::map`ho typu pomocí uzlu `TreeItems`:

```xml
<Type Name="std::map&lt;*&gt;">
  <DisplayString>{{size = {_Mysize}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mysize</Item>
    <Item Name="[comp]">comp</Item>
    <TreeItems>
      <Size>_Mysize</Size>
      <HeadPointer>_Myhead->_Parent</HeadPointer>
      <LeftPointer>_Left</LeftPointer>
      <RightPointer>_Right</RightPointer>
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>
    </TreeItems>
  </Expand>
</Type>
```

Syntaxe je podobná `LinkedListItems` uzlu. `LeftPointer`, `RightPointer` a `ValueNode` jsou vyhodnocovány v kontextu třídy uzlu stromu. `ValueNode` může být ponecháno prázdné nebo pomocí `this` odkazovat na samotný uzel `TreeItems`.

#### <a name="BKMK_ExpandedItem_expansion"></a>Rozšíření ExpandedItem
 Element `ExpandedItem` generuje agregované podřízené zobrazení zobrazením vlastností základních tříd nebo datových členů, jako kdyby byly podřízenými objekty typu vizuálu. Ladicí program vyhodnotí zadaný výraz a připojí podřízené uzly výsledku do podřízeného seznamu vizuálního typu.

Například typ inteligentního ukazatele `auto_ptr<vector<int>>` obvykle zobrazuje:

 ![výchozí&#95;rozšíření&#60;auto&#60;PTR&#62; &#62; Vector int](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Výchozí rozšíření")

 Chcete-li zobrazit hodnoty vektoru, je nutné přejít na dvě úrovně v okně proměnné a procházející členem `_Myptr`. Přidáním prvku `ExpandedItem` můžete eliminovat `_Myptr` proměnnou z hierarchie a přímo zobrazit prvky Vector:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![ExpandedItem&#95;rozšíření&#60;auto&#60;PTR&#62; &#62; Vector int](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Rozšíření ExpandedItem")

Následující příklad ukazuje, jak agregovat vlastnosti ze základní třídy v odvozené třídě. Předpokládejme, `CPanel` třída je odvozena z `CFrameworkElement`. Namísto opakování vlastností, které pocházejí ze základní `CFrameworkElement` třídy, vizualizace `ExpandedItem` uzel tyto vlastnosti připojí do podřízeného seznamu třídy `CPanel`.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Zde je nutný specifikátor formátu **ND** , který vypne porovnání vizualizace pro odvozenou třídu. V opačném případě by výraz `*(CFrameworkElement*)this` způsobil, že se znovu použila vizualizace `CPanel`, protože výchozí typy vizualizace, které odpovídají pravidlům, považují za nejvhodnější. Použijte specifikátor formátu **ND** pro instruování ladicího programu, aby používal vizualizaci základní třídy, nebo výchozí rozšíření, pokud základní třída nemá žádnou vizualizaci.

#### <a name="BKMK_Synthetic_Item_expansion"></a>Rozšíření syntetické položky
 Zatímco `ExpandedItem` element poskytuje plošší zobrazení dat odstraněním hierarchií, `Synthetic` uzel v opačném případě. Umožňuje vytvořit umělý podřízený prvek, který není výsledkem výrazu. Umělý prvek může mít vlastní podřízené prvky. V následujícím příkladu vizualizace typu `Concurrency::array` používá `Synthetic` uzel k zobrazení diagnostické zprávy uživateli:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>
    </Synthetic>
  </Expand>
</Type>
```

 ![Concurrency:: Array s rozšířením syntetického elementu](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency:: Array s rozšířením syntetického elementu")

### <a name="BKMK_HResult"></a>HResult – element
 Element `HResult` umožňuje přizpůsobit informace, které se zobrazí v oknech ladicího programu pro **HRESULT** . Element `HRValue` musí obsahovat 32 hodnotu **HRESULT** , kterou chcete přizpůsobit. Element `HRDescription` obsahuje informace, které se zobrazí v okně ladicího programu.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="BKMK_UIVisualizer"></a>Element UIVisualizer
Element `UIVisualizer` registruje modul plug-in pro grafický Vizualizér pomocí ladicího programu. Grafický Vizualizér vytvoří dialogové okno nebo jiné rozhraní, které zobrazí proměnnou nebo objekt způsobem konzistentním s datovým typem. Modul plug-in Vizualizér musí být vytvořen jako [VSPackage](../extensibility/internals/vspackages.md)a musí vystavit službu, kterou může ladicí program spotřebovat. Soubor *. Natvis* obsahuje registrační informace pro modul plug-in, jako je jeho název, identifikátor GUID služby vystavené službě a typy, které může vizualizovat.

Tady je příklad prvku UIVisualizer:

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="1" MenuName="Vector Visualizer"/>
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="2" MenuName="List Visualizer"/>
.
.
</AutoVisualizer>
```

- Dvojice atributů `ServiceId`  -  `Id` identifikuje `UIVisualizer`. `ServiceId` je identifikátor GUID služby, kterou balíček Vizualizér zpřístupňuje. `Id` je jedinečný identifikátor, který odlišuje vizualizace, pokud služba poskytuje více než jednu. V předchozím příkladu má stejná služba Vizualizér dva nástroje pro vizualizaci.

- Atribut `MenuName` definuje název Vizualizátoru, který se zobrazí v rozevíracím seznamu vedle ikony lupy v ladicím programu. Příklad:

  ![Místní nabídka nabídky UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "Místní nabídka nabídky UIVisualizer")

Každý typ definovaný v souboru *. Natvis* musí explicitně uvést jakékoli vizualizace uživatelského rozhraní, které je možné zobrazit. Ladicí program odpovídá odkazům na Vizualizér v záznamech typu s registrovanými vizualizacemi. Například následující položka typu pro `std::vector` odkazuje na `UIVisualizer` v předchozím příkladu.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Můžete vidět příklad `UIVisualizer` v rozšíření pro [sledování obrázků](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.ImageWatch2017) , který slouží k zobrazení rastrových obrázků v paměti.

### <a name="BKMK_CustomVisualizer"></a>Element CustomVisualizer
 `CustomVisualizer` je bod rozšíření, který určuje rozšíření VSIX, které zapisujete do ovládacích prvků vizualizace v aplikaci Visual Studio Code. Další informace o zápisu rozšíření VSIX naleznete v sadě [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Je to mnohem více práce na zápis vlastního Vizualizátoru, než je definice XML Natvis, ale nejste omezeni omezeními na to, co Natvis nebo nepodporují. Vlastní vizualizace mají přístup k plné sadě rozhraní API rozšiřitelnosti ladicího programu, které mohou dotazovat a upravovat proces laděného procesu nebo komunikovat s jinými částmi sady Visual Studio.

 Pro prvky `CustomVisualizer` lze použít atributy `Condition`, `IncludeView` a `ExcludeView`.