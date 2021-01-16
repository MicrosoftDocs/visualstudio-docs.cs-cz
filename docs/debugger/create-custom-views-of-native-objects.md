---
title: Vytváření vlastních zobrazení objektů C++
description: Použití rozhraní Natvis k přizpůsobení způsobu, jakým Visual Studio zobrazuje nativní typy v ladicím programu
ms.date: 03/02/2020
ms.topic: how-to
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
ms.openlocfilehash: 60d817c3600eaa82eb7f67489d5dadadaba3932f
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533963"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Vytváření vlastních zobrazení objektů C++ v ladicím programu pomocí architektury Natvis

Rozhraní Visual Studio *Natvis* přizpůsobuje způsob, jakým se v oknech proměnných ladicího programu zobrazují nativní typy, jako jsou **místní** a **sledovací** okna a v části **datatipů**. Vizualizace Natvis mohou přispět k vytváření lépe viditelných typů během ladění.

Natvis nahrazuje soubor *autoexp. dat* v dřívějších verzích sady Visual Studio se syntaxí XML, lepší diagnostikou, správou verzí a podporou více souborů.

> [!NOTE]
> Přizpůsobení Natvis pracují s třídami a strukturami, ale ne definice typedef.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Vizualizace Natvis

Pomocí architektury Natvis vytvoříte pravidla vizualizace pro typy, které vytvoříte, aby se vývojáři mohli snadněji zobrazit během ladění.

Například následující ilustrace ukazuje proměnnou typu [Windows:: UI:: XAML:: Controls:: TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) v okně ladicího programu, aniž by byly aplikovány vlastní vizualizace.

![Výchozí vizualizace textového pole](../debugger/media/dbg_natvis_textbox_default.png "Výchozí vizualizace textového pole")

Zvýrazněný řádek zobrazuje `Text` vlastnost `TextBox` třídy. Složitá hierarchie tříd usnadňuje vyhledání této vlastnosti. Ladicí program neví, jak interpretovat typ vlastního řetězce, takže se nezobrazuje řetězec umístěný uvnitř textového pole.

`TextBox`Při použití vlastních pravidel Vizualizátoru Natvis se v okně proměnných bude mnohem jednodušší. Důležité členy třídy se zobrazí společně a ladicí program zobrazí základní řetězcovou hodnotu vlastního typu řetězce.

![Data textového pole používající Vizualizér](../debugger/media/dbg_natvis_textbox_visualizer.png "Data textového pole používající Vizualizér")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>Použití souborů. Natvis v projektech C++

Natvis používá k určení pravidel vizualizací soubory *. Natvis* . Soubor *. Natvis* je soubor XML s příponou *. Natvis* . Schéma natvis je definováno v *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*.

Základní strukturou souboru *. Natvis* je jeden nebo více `Type` prvků reprezentujících položky vizualizace. `Type`Ve svém atributu je určen plně kvalifikovaný název každého prvku `Name` .

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

### <a name="add-a-natvis-file-to-a-c-project"></a>Přidání souboru. Natvis do projektu C++

Soubor *. Natvis* můžete přidat do jakéhokoli projektu jazyka C++.

**Postup přidání nového souboru *Natvis* :**

1. Vyberte uzel projektu C++ v **Průzkumník řešení**, vyberte **projekt**  >  **Přidat novou položku** nebo klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat**  >  **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte   >    >  **soubor vizualizace ladicího programu nástroje Visual C++ Utility (. Natvis)**.

1. Zadejte název souboru a vyberte **Přidat**.

   Nový soubor se přidá do **Průzkumník řešení** a otevře se v podokně dokumentu sady Visual Studio.

Ladicí program sady Visual Studio načte soubory *. Natvis* v projektech C++ automaticky a ve výchozím nastavení je také zahrne do souboru *. pdb* při sestavení projektu. Pokud ladíte sestavenou aplikaci, ladicí program načte soubor *. Natvis* ze souboru *. pdb* , i když projekt ještě nemáte otevřený. Pokud nechcete, aby soubor *. Natvis* byl součástí souboru. *PDB*, můžete ho vyloučit z vytvořeného souboru *. pdb* .

**Vyloučení souboru *. Natvis* z *PDB*:**

1. V **Průzkumník řešení** vyberte soubor *. Natvis* a vyberte ikonu **vlastnosti** , nebo klikněte pravým tlačítkem na soubor a vyberte **vlastnosti**.

1. Přetáhněte šipku vedle seznamu **vyloučené ze sestavení** a vyberte možnost **Ano** a pak vyberte **OK**.

>[!NOTE]
>Pro ladění spustitelných projektů použijte položky řešení k přidání jakýchkoli souborů *. Natvis* , které nejsou v souboru *. pdb*, protože není k dispozici žádný projekt C++.

>[!NOTE]
>Pravidla Natvis načtená ze souboru *. pdb* se vztahují pouze na typy v modulech, na které odkazuje soubor *. pdb* . Například pokud má *Module1. pdb* položku Natvis pro typ s názvem `Test` , vztahuje se pouze na `Test` třídu v *Module1.dll*. Pokud jiný modul také definuje třídu s názvem `Test` , položka Natvis pro *Module1. pdb* se na ni nevztahuje.

**Instalace a registrace souboru *. Natvis* prostřednictvím balíčku VSIX:**

VSIX balíček může nainstalovat a zaregistrovat soubory *. Natvis* . Bez ohledu na to, kde jsou nainstalovány, jsou všechny registrované soubory *Natvis* automaticky vyzvednuty během ladění.

1. Do balíčku VSIX zahrňte soubor *. Natvis* . Například pro následující soubor projektu:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. Zaregistrujte soubor *. Natvis* v souboru *source. extension. vsixmanifest* :

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a> Umístění souborů Natvis

Pokud chcete, aby se soubory *. Natvis* mohly použít pro více projektů, můžete je přidat do adresáře uživatelů nebo do systémového adresáře.

Soubory *. Natvis* jsou vyhodnocovány v následujícím pořadí:

1. Všechny soubory *. Natvis* , které jsou vloženy do souboru *. pdb* , který ladíte, pokud soubor se stejným názvem v načteném projektu neexistuje.

2. Všechny soubory *. Natvis* , které jsou v načteném projektu C++ nebo v řešení nejvyšší úrovně. Tato skupina zahrnuje všechny načtené projekty C++, včetně knihoven tříd, ale ne projektů v jiných jazycích.

3. Všechny soubory *. Natvis* nainstalované a registrované prostřednictvím balíčku VSIX

::: moniker range="vs-2017"

4. Adresář Natvis konkrétního uživatele (například *%UserProfile%\Documents\Visual Studio 2017 \ vizualizujes*).

::: moniker-end

::: moniker range=">= vs-2019"

4. Adresář Natvis konkrétního uživatele (například *%UserProfile%\Documents\Visual Studio 2019 \ vizualizujes*).

::: moniker-end

5. Adresář Natvis pro systém v rámci systému (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Tento adresář obsahuje soubory *. Natvis* , které jsou nainstalovány se sadou Visual Studio. Pokud máte oprávnění správce, můžete do tohoto adresáře přidat soubory.

## <a name="modify-natvis-files-while-debugging"></a>Upravovat soubory. Natvis během ladění

Během ladění projektu můžete upravit soubor *. Natvis* v integrovaném vývojovém prostředí (IDE). Otevřete soubor ve stejné instanci aplikace Visual Studio, kterou ladíte, upravte a uložte. Jakmile se soubor uloží, Windows Update **sledování** a **místní** aktualizace projeví změnu.

Můžete také přidat nebo odstranit soubory *. Natvis* v řešení, které ladíte, a Visual Studio přidá nebo odebere příslušné vizualizace.

Při ladění nemůžete aktualizovat soubory *. Natvis* vložené do souborů *. pdb* .

Pokud upravíte soubor *. Natvis* mimo sadu Visual Studio, změny se neprojeví automaticky. Chcete-li aktualizovat okna ladicího programu, můžete znovu vyhodnotit příkaz **. natvisreload** v **příkazovém** okně. Změny se projeví i bez restartování ladicí relace.

K upgradu souboru *. Natvis* na novější verzi použijte taky příkaz **. natvisreload** . Například soubor *. Natvis* může být zkontrolován do správy zdrojového kódu a chcete si vybrat poslední změny, které udělal někdo jiný.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> Výrazy a formátování
Vizualizace Natvis používají výrazy jazyka C++ k určení datových položek, které se mají zobrazit. Kromě vylepšení a omezení výrazů jazyka C++ v ladicím programu, které jsou popsány v [kontextovém operátoru (C++)](../debugger/context-operator-cpp.md), je třeba mít na paměti následující:

- Výrazy Natvis jsou vyhodnocovány v kontextu objektu, který je vizuálů, nikoli aktuálního rámce zásobníku. Například `x` ve výrazu Natvis odkazuje na pole s názvem **x** v objektu, který je vizuálů, nikoli na místní proměnnou s názvem **x** v aktuální funkci. K místním proměnným ve výrazech Natvis nemůžete přistupovat, i když máte přístup k globálním proměnným.

- Výrazy Natvis nepovolují vyhodnocení funkce ani vedlejší účinky. Volání funkce a operátory přiřazení jsou ignorovány. Vzhledem k tomu, že [vnitřní funkce ladicího programu](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) mají volné vedlejší účinky, mohou být volně volány z jakéhokoli výrazu Natvis, i když nejsou povolena jiná volání funkcí.

- Chcete-li určit, jak se výraz zobrazí, můžete použít libovolný specifikátor formátu popsaný v tématu [specifikátory formátu v jazyce C++](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Specifikátory formátu jsou ignorovány, pokud je položka používána interně pomocí Natvis, jako je například `Size` výraz v [rozšíření ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

>[!NOTE]
> Vzhledem k tomu, že dokument natvis je XML, nemohou vaše výrazy přímo používat operátory ampersand, větší než, menší než nebo Shift. Tyto znaky je nutné vystavit v těle položky i v příkazech podmínky. Příklad:<br>
> \<Item Name="HiByte"\>bytové (_flags \& gt; \& gt 24), x\</Item\><br>
> \<Item Name="HiByteStatus" Condition="(_flags \&amp; 0xFF000000) == 0"\>NTato\</Item\><br>
> \<Item Name="HiByteStatus" Condition="(_flags \&amp; 0xFF000000) != 0"\>Nějaký\</Item\>

## <a name="natvis-views"></a>Zobrazení Natvis

Můžete definovat různá zobrazení Natvis pro zobrazení typů různými způsoby. Například zde je vizualizace `std::vector` , která definuje zjednodušené zobrazení s názvem `simple` . `DisplayString`Prvky a se `ArrayItems` zobrazí ve výchozím zobrazení a `simple` zobrazení, zatímco `[size]` položky a se `[capacity]` nezobrazují v `simple` zobrazení.

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

V okně **kukátko** použijte specifikátor formátu **zobrazení** k určení alternativního zobrazení. Jednoduché zobrazení se zobrazí jako **vec, zobrazení (jednoduché)**:

![okno Kukátko s jednoduchým zobrazením](../debugger/media/watch-simpleview.png "okno Kukátko s jednoduchým zobrazením")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a> Chyby Natvis

Když ladicí program narazí na chyby v položce vizualizace, ignoruje je. Buď zobrazí typ v nezpracované podobě, nebo vybere jinou vhodnou vizualizaci. Pomocí diagnostiky Natvis můžete zjistit, proč ladicí program ignoroval položku vizualizace, a zobrazit základní syntaxi a chyby při analýze.

**Zapnutí diagnostiky Natvis:**

- V nabídce  >  **Možnosti** nástrojů (nebo   >  **Možnosti** ladění) >  >  **okno výstup** ladění nastavte chyby a **diagnostické zprávy Natvis (jenom C++)** na **Error**, **Warning** nebo **verbose** a pak vyberte **OK**.

Chyby se zobrazí v okně **výstup** .

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a> Odkaz syntaxe Natvis

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a> Element autovizualizuje
`AutoVisualizer`Element je kořenovým uzlem souboru *. Natvis* a obsahuje `xmlns:` atribut namespace.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

`AutoVisualizer`Element může mít podřízené položky [Type](#BKMK_Type), [HRESULT](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer)a [CustomVisualizer](#BKMK_CustomVisualizer) .

### <a name="type-element"></a><a name="BKMK_Type"></a> Element Type

Základní `Type` vypadá jako v tomto příkladu:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 `Type`Element určuje:

1. Jaký typ vizualizace má být použit pro ( `Name` atribut).

2. Jak hodnota objektu tohoto typu by měla vypadat ( `DisplayString` element).

3. Jak by měly členové typu vypadat, když uživatel rozbalí typ v okně proměnné ( `Expand` uzel).

#### <a name="templated-classes"></a>Třídy šablon
`Name`Atribut `Type` elementu přijímá hvězdičku `*` jako zástupný znak, který lze použít pro názvy tříd šablon.

V následujícím příkladu je použita stejná vizualizace, je-li objekt typu `CAtlArray<int>` nebo `CAtlArray<float>` . Pokud existuje konkrétní položka vizualizace pro a `CAtlArray<float>` , má přednost před obecným.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Můžete odkazovat na parametry šablony v položce vizualizace pomocí maker $T 1, $T 2 a tak dále. Příklady těchto maker naleznete v souborech *. Natvis* dodaných se sadou Visual Studio.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> Shoda typu Vizualizátor
Pokud se položka vizualizace nedokáže ověřit, použije se další dostupná vizualizace.

#### <a name="inheritable-attribute"></a>Dědičný atribut
Volitelný `Inheritable` atribut určuje, zda vizualizace platí pouze pro základní typ nebo základní typ a všechny odvozené typy. Výchozí hodnota `Inheritable` je `true` .

V následujícím příkladu vizualizace platí pouze pro tento `BaseClass` Typ:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Priorita – atribut

Nepovinný `Priority` atribut určuje pořadí, ve kterém se mají použít alternativní definice, pokud se definice nedokáže analyzovat. Možné hodnoty `Priority` jsou: `Low` , `MediumLow` , `Medium` , `MediumHigh` a `High` . Výchozí hodnota je `Medium`. `Priority`Atribut rozlišuje pouze priority mezi stejným souborem *. Natvis* .

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
Atribut můžete umístit `Optional` na libovolný uzel. Pokud se dílčí výraz uvnitř volitelného uzlu nedokáže analyzovat, ladicí program tento uzel ignoruje, ale použije zbytek `Type` pravidel. V následujícím typu `[State]` není volitelná, ale `[Exception]` je volitelný.  Pokud `MyNamespace::MyClass` obsahuje pole s názvem _ `M_exceptionHolder` , zobrazí se `[State]` uzel i `[Exception]` uzel, ale pokud není k dispozici žádné `_M_exceptionHolder` pole, `[State]` zobrazí se pouze uzel.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> Atribut Condition

Volitelný `Condition` atribut je k dispozici pro mnoho prvků vizualizace a určuje, kdy použít pravidlo vizualizace. Pokud se výraz uvnitř atributu Condition přeloží na `false` , pravidlo vizualizace se nepoužije. Pokud se vyhodnotí jako `true` , nebo neexistuje žádný `Condition` atribut, vizualizace se použije. Tento atribut lze použít pro logiku if-else v položkách vizualizace.

Například následující vizualizace má dva `DisplayString` prvky pro typ inteligentního ukazatele. Když `_Myptr` je člen prázdný, je podmínka prvního `DisplayString` prvku překládána na `true` , takže se formulář zobrazí. Pokud `_Myptr` člen není prázdný, podmínka se vyhodnotí jako `false` a druhý prvek se `DisplayString` zobrazí.

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

`IncludeView`Atributy a `ExcludeView` určují prvky pro zobrazení nebo nezobrazení v konkrétních zobrazeních. Například v následující specifikaci Natvis se v zobrazení nezobrazí `std::vector` `simple` `[size]` `[capacity]` položky a.

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

Můžete použít `IncludeView` `ExcludeView` atributy a u typů a u jednotlivých členů.

### <a name="version-element"></a><a name="BKMK_Versioning"></a> Element Version
Element seskupuje `Version` položku vizualizace na určitý modul a verzi. `Version`Prvek pomáhá předcházet kolizím názvů, omezuje neúmyslné neshody a umožňuje různé vizualizace pro různé verze typu.

Pokud společný hlavičkový soubor, který používá jiné moduly, definuje typ, vizualizace se správou verzí se zobrazí pouze v případě, že je typ v zadané verzi modulu.

V následujícím příkladu je vizualizace platná pouze pro `DirectUI::Border` typ nalezený v `Windows.UI.Xaml.dll` z verze 1,0 na 1,5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Nepotřebujete obojí `Min` a `Max` . Jsou to volitelné atributy. Nejsou podporovány žádné zástupné znaky.

`Name`Atribut má formát *filename. ext*, například *hello.exe* nebo *some.dll*. Nejsou povoleny žádné názvy cest.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a> Element DisplayString
`DisplayString`Element určuje řetězec, který má být zobrazen jako hodnota proměnné. Přijímá libovolné řetězce smíšené s výrazy. Vše uvnitř složených závorek je interpretováno jako výraz. Například následující `DisplayString` položku:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Znamená, že proměnné typu `CPoint` se zobrazí jako na tomto obrázku:

 ![Použít element DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "Použít element DisplayString")

Ve `DisplayString` výrazu `x` a `y` , které jsou členy `CPoint` , jsou uvnitř složených závorek, takže jejich hodnoty jsou vyhodnocovány. Příklad také ukazuje, jak lze vytvořit složenou závorku pomocí dvojitých složených závorek ( `{{` nebo `}}` ).

> [!NOTE]
> `DisplayString`Element je jediným prvkem, který přijímá libovolné řetězce a syntaxi složených závorek. Všechny ostatní prvky vizualizace přijímají pouze výrazy, které může ladicí program vyhodnotit.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a> Element StringView

`StringView`Prvek definuje hodnotu, kterou může ladicí program odeslat do integrovaného Vizualizér textu. Například s ohledem na následující vizualizaci pro `ATL::CStringT` Typ:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

`CStringT`Objekt se zobrazí v okně proměnné jako v tomto příkladu:

![CStringt – element DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringt – element DisplayString")

Přidáním `StringView` prvku říká ladicímu programu, že může zobrazit hodnotu jako vizualizaci textu.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Během ladění můžete vybrat ikonu lupy vedle proměnné a pak vybrat **Vizualizér textu** pro zobrazení řetězce, na který **m_pszData** odkazuje.

 ![Data CStringt pomocí Vizualizér StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "Data CStringt pomocí Vizualizér StringView")

Výraz `{m_pszData,su}` obsahuje specifikátor formátu v jazyce C++ pro zobrazení hodnoty jako řetězce Unicode. Další informace naleznete v tématu [specifikátory formátu v jazyce C++](../debugger/format-specifiers-in-cpp.md).

### <a name="expand-element"></a><a name="BKMK_Expand"></a> Rozbalit element

Volitelný `Expand` uzel přizpůsobuje podřízené prvky vizuálního typu, když rozbalíte typ v okně proměnné. `Expand`Uzel přijímá seznam podřízených uzlů, které definují podřízené prvky.

- Pokud `Expand` uzel není specifikován v položce vizualizace, podřízené položky použijí výchozí pravidla rozšíření.

- Pokud `Expand` je v uzlu určen uzel bez podřízených uzlů, nelze tento typ rozšířit v oknech ladicího programu.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> Rozšíření položky

 Element je nejzákladnější `Item` a společný prvek v `Expand` uzlu. `Item` definuje jeden podřízený element. Například `CRect` Třída s poli `top` , `left` , `right` a `bottom` má následující položku vizualizace:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

V okně ladicího programu `CRect` vypadá typ jako v tomto příkladu:

![CRect s rozšířením elementu Item](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect s rozšířením elementu Item")

Ladicí program vyhodnocuje výrazy zadané v `Width` prvcích a a `Height` zobrazuje hodnoty ve sloupci **Value (hodnota** ) v okně proměnné.

Ladicí program automaticky vytvoří uzel **[RAW View]** pro každé vlastní rozšíření. Předchozí snímek obrazovky zobrazuje rozbalený uzel **[nezpracované zobrazení]** , který ukazuje, jak se výchozí nezpracovaná zobrazení objektu liší od jeho vizualizace Natvis. Výchozí rozšíření vytvoří podstrom pro základní třídu a seznam všech datových členů základní třídy jako podřízených objektů.

> [!NOTE]
> Pokud se výraz elementu Item odkazuje na komplexní typ, lze uzel **položky** sám rozšířit.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a> Rozšíření ArrayItems
Použijte `ArrayItems` uzel, aby ladicí program sady Visual Studio interpretoval typ jako pole a zobrazil jeho jednotlivé prvky. Vizualizace pro `std::vector` je dobrý příklad:

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

A `std::vector` zobrazuje jeho jednotlivé prvky při rozbalení v okně proměnné:

![std:: Vector s použitím rozšíření ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std:: Vector s použitím rozšíření ArrayItems")

`ArrayItems`Uzel musí mít:

- `Size`Výraz (který musí být vyhodnocen jako celé číslo) pro ladicí program pro pochopení délky pole.
- `ValuePointer`Výraz, který odkazuje na první prvek (který musí být ukazatelem typu elementu, který není `void*` ).

Výchozí hodnota dolní meze pole je 0. Chcete-li přepsat hodnotu, použijte `LowerBound` element. Příklady jsou soubory *. Natvis* dodávané se sadou Visual Studio.

>[!NOTE]
>Operátor můžete použít `[]` například `vector[i]` s libovolnou vizualizací pole, která používá `ArrayItems` , i v případě, že samotný typ (například `CATLArray` ) nepovoluje Tento operátor.

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

- `Direction` Určuje, zda je pole v pořadí podle řádků nebo hlavní verze sloupce.
- `Rank` Určuje rozměr pole.
- `Size`Prvek přijímá implicitní `$i` parametr, který nahradí index dimenze, aby bylo možné zjistit délku pole v dané dimenzi. V předchozím příkladu `_M_extent.M_base[0]` by měl výraz poskytovat délku 0th dimenze, `_M_extent._M_base[1]` 1. a tak dále.

Tady je postup, jak dvourozměrný `Concurrency::array` objekt vypadá v okně ladicího programu:

![Dvourozměrné pole s rozšířením ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Dvourozměrné pole s rozšířením ArrayItems")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> Rozšíření IndexListItems

Rozšíření lze použít `ArrayItems` pouze v případě, že jsou prvky pole rozloženy souvisle v paměti. Ladicí program se dostane k dalšímu prvku jednoduchým zvýšením jeho ukazatele. Pokud potřebujete manipulovat s indexem na uzel hodnoty, použijte `IndexListItems` uzly. Tady je vizualizace s `IndexListItems` uzlem:

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

Jediný rozdíl mezi `ArrayItems` a `IndexListItems` je `ValueNode` , který očekává úplný výraz pro i<sup>th</sup> elementu s implicitním `$i` parametrem.

>[!NOTE]
>Operátor můžete použít `[]` například `vector[i]` s libovolnou vizualizací pole, která používá `IndexListItems` , i v případě, že samotný typ (například `CATLArray` ) nepovoluje Tento operátor.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> Rozšíření LinkedListItems

Pokud vizuální typ představuje propojený seznam, ladicí program může zobrazit jeho podřízené položky pomocí `LinkedListItems` uzlu. Následující vizualizace `CAtlList` typu používá `LinkedListItems` :

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

`Size`Prvek odkazuje na délku seznamu. `HeadPointer` odkazuje na první prvek, `NextPointer` odkazuje na další prvek a `ValueNode` odkazuje na hodnotu položky.

Ladicí program vyhodnocuje `NextPointer` výrazy a `ValueNode` v kontextu `LinkedListItems` elementu Node, nikoli typu nadřazeného seznamu. V předchozím příkladu `CAtlList` má `CNode` třída (nalezen v `atlcoll.h` ), která je uzlem propojeného seznamu. `m_pNext` a `m_element` jsou pole této `CNode` třídy, nikoli `CAtlList` Třída.

`ValueNode` může být ponecháno prázdné, nebo použijte `this` pro odkazování na `LinkedListItems` samotný uzel.

#### <a name="customlistitems-expansion"></a>Rozšíření CustomListItems

`CustomListItems`Rozšíření umožňuje napsat vlastní logiku pro procházení datové struktury, jako je například zatřiďovací tabulka. Slouží `CustomListItems` k vizualizaci datových struktur, které mohou používat výrazy jazyka C++ pro všechno, co potřebujete k vyhodnocení, ale nemusíte mít dost tvarovat pro `ArrayItems` , `IndexListItems` nebo `LinkedListItems` .

Můžete použít `Exec` ke spuštění kódu uvnitř `CustomListItems` rozšíření s použitím proměnných a objektů definovaných v rozšíření. Můžete použít logické operátory, aritmetické operátory a operátory přiřazení s `Exec` . Nemůžete použít `Exec` k vyhodnocení funkcí, s výjimkou [vnitřních funkcí ladicího programu](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) , které podporuje vyhodnocovací filtr výrazů jazyka C++.

Následující Vizualizér pro `CAtlMap` je vynikající příklad, kde `CustomListItems` je to vhodné.

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

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a> Rozšíření TreeItems
 Pokud vizuální typ představuje strom, ladicí program může projít stromovou strukturou a zobrazit jeho podřízené položky pomocí `TreeItems` uzlu. Tady je vizualizace pro `std::map` typ pomocí `TreeItems` uzlu:

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

Syntaxe je podobná `LinkedListItems` uzlu. `LeftPointer`, `RightPointer` , a `ValueNode` jsou vyhodnocovány v kontextu třídy uzlu stromu. `ValueNode` může být ponecháno prázdné nebo použít `this` pro odkazování na `TreeItems` samotný uzel.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> Rozšíření ExpandedItem
 `ExpandedItem`Prvek generuje agregované podřízené zobrazení zobrazením vlastností základních tříd nebo datových členů, jako kdyby byly podřízenými prvky vizuálního typu. Ladicí program vyhodnotí zadaný výraz a připojí podřízené uzly výsledku do podřízeného seznamu vizuálního typu.

Například typ inteligentního ukazatele `auto_ptr<vector<int>>` obvykle zobrazuje:

 ![Automatické&#95;PTR&#60;Vector&#60;int&#62;&#62; výchozí rozšíření](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Výchozí rozšíření")

 Chcete-li zobrazit hodnoty vektoru, je nutné procházet dvě úrovně v okně proměnné a procházející `_Myptr` členem. Přidáním `ExpandedItem` elementu můžete odstranit `_Myptr` proměnnou z hierarchie a přímo zobrazit prvky Vector:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![Automatické&#95;PTR&#60;Vector&#60;int&#62;&#62; rozšíření ExpandedItem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Rozšíření ExpandedItem")

Následující příklad ukazuje, jak agregovat vlastnosti ze základní třídy v odvozené třídě. Předpokládejme, že `CPanel` Třída je odvozena z `CFrameworkElement` . Namísto opakování vlastností, které pocházejí ze základní `CFrameworkElement` třídy, `ExpandedItem` vizualizace uzlu tyto vlastnosti připojí do podřízeného seznamu `CPanel` třídy.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Zde je nutný specifikátor formátu **ND** , který vypne porovnání vizualizace pro odvozenou třídu. V opačném případě by výraz způsobil, že se `*(CFrameworkElement*)this` `CPanel` vizualizace znovu použila, protože výchozí typy vizualizace, které odpovídají pravidlům, považují za nejvhodnější. Použijte specifikátor formátu **ND** pro instruování ladicího programu, aby používal vizualizaci základní třídy, nebo výchozí rozšíření, pokud základní třída nemá žádnou vizualizaci.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a> Rozšíření syntetické položky
 I když `ExpandedItem` element poskytuje plošší zobrazení dat odstraněním hierarchií, `Synthetic` uzel provede opak. Umožňuje vytvořit umělý podřízený prvek, který není výsledkem výrazu. Umělý prvek může mít vlastní podřízené prvky. V následujícím příkladu vizualizace pro `Concurrency::array` typ používá `Synthetic` uzel k zobrazení diagnostické zprávy uživateli:

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

### <a name="hresult-element"></a><a name="BKMK_HResult"></a> HResult – element
 `HResult`Element umožňuje přizpůsobit informace, které jsou zobrazeny pro **HRESULT** v oknech ladicího programu. `HRValue`Element musí obsahovat 32 hodnotu **HRESULT** , kterou chcete přizpůsobit. `HRDescription`Element obsahuje informace, které se zobrazí v okně ladicího programu.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a> Element UIVisualizer
`UIVisualizer`Prvek zaregistruje modul plug-in pro grafický Vizualizér pomocí ladicího programu. Grafický Vizualizér vytvoří dialogové okno nebo jiné rozhraní, které zobrazí proměnnou nebo objekt způsobem konzistentním s datovým typem. Modul plug-in Vizualizér musí být vytvořen jako [VSPackage](../extensibility/internals/vspackages.md)a musí vystavit službu, kterou může ladicí program spotřebovat. Soubor *. Natvis* obsahuje registrační informace pro modul plug-in, jako je jeho název, identifikátor GUID služby vystavené službě a typy, které může vizualizovat.

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

- `ServiceId`  -  `Id` Dvojice atributů identifikuje `UIVisualizer` . `ServiceId`Je identifikátor GUID služby, kterou balíček Vizualizér zpřístupňuje. `Id` je jedinečný identifikátor, který odlišuje vizualizace, pokud služba poskytuje více než jeden. V předchozím příkladu má stejná služba Vizualizér dva nástroje pro vizualizaci.

- `MenuName`Atribut definuje název Vizualizátoru, který se má zobrazit v rozevíracím seznamu vedle ikony lupy v ladicím programu. Příklad:

  ![Místní nabídka nabídky UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "Místní nabídka nabídky UIVisualizer")

Každý typ definovaný v souboru *. Natvis* musí explicitně uvést jakékoli vizualizace uživatelského rozhraní, které je možné zobrazit. Ladicí program odpovídá odkazům na Vizualizér v záznamech typu s registrovanými vizualizacemi. Například následující položka typu pro `std::vector` odkazuje `UIVisualizer` v předchozím příkladu.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Můžete vidět příklad `UIVisualizer` v rozšíření pro [sledování obrázků](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) , který slouží k zobrazení rastrových obrázků v paměti.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>Element CustomVisualizer
 `CustomVisualizer` je bod rozšiřitelnosti, který určuje rozšíření VSIX, které zapisujete do ovládacích prvků vizualizace v aplikaci Visual Studio Code. Další informace o zápisu rozšíření VSIX naleznete v sadě [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Je to mnohem více práce na zápis vlastního Vizualizátoru, než je definice XML Natvis, ale nejste omezeni omezeními na to, co Natvis nebo nepodporují. Vlastní vizualizace mají přístup k plné sadě rozhraní API rozšiřitelnosti ladicího programu, které mohou dotazovat a upravovat proces laděného procesu nebo komunikovat s jinými částmi sady Visual Studio.

 Můžete použít `Condition` `IncludeView` atributy, a `ExcludeView` u `CustomVisualizer` elementů.

## <a name="limitations"></a>Omezení

Přizpůsobení Natvis pracují s třídami a strukturami, ale ne definice typedef.

Natvis nepodporuje vizualizace pro primitivní typy (například `int` , `bool` ) nebo pro ukazatele na primitivní typy. V tomto scénáři je jednou z možností použití [specifikátoru formátu](../debugger/format-specifiers-in-cpp.md) vhodného pro váš případ použití. Například pokud používáte `double* mydoublearray` ve svém kódu, pak můžete použít specifikátor formátu pole v okně **kukátka** ladicího programu, jako je například výraz `mydoublearray, [100]` , který zobrazuje prvních 100 prvků.
