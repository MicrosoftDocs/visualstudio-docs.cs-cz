---
title: Vytváření vlastních zobrazení objektů C++
description: Pomocí architektury Natvis můžete přizpůsobit způsob, jakým Visual Studio zobrazuje nativní typy v ladicím programu.
ms.date: 03/02/2020
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
ms.openlocfilehash: 4f8bdd8d26ba450b1aedd790d644c183607c44af
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224508"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Vytvoření vlastních zobrazení objektů jazyka C++ v ladicím programu pomocí architektury Natvis

Visual Studio *Natvis* framework upravuje způsob, jakým se nativní typy zobrazují v oknech proměnných ladicího programu, jako jsou například místní **a** **sledovat** okna, a v **DataTips**. Vizualizace Natvis mohou pomoci zviditelnit typy, které vytvoříte během ladění.

Natvis nahradí soubor *autoexp.dat* v dřívějších verzích sady Visual Studio syntaxí XML, lepší diagnostikou, správu verzí a podporu více souborů.

> [!NOTE]
> Natvis přizpůsobení práce s třídami a struktury, ale ne typedefs.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Vizualizace Natvis

Pomocí architektury Natvis můžete vytvořit pravidla vizualizace pro typy, které vytvoříte, aby je vývojáři mohli snadněji zobrazit během ladění.

Na následujícím obrázku je například znázorněna proměnná typu [Windows::UI::Xaml::Controls::TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) v okně ladicího programu bez použití vlastních vizualizací.

![Výchozí vizualizace textového pole](../debugger/media/dbg_natvis_textbox_default.png "Výchozí vizualizace textového pole")

Zvýrazněný řádek zobrazuje `Text` vlastnost `TextBox` třídy. Komplexní hierarchie tříd ztěžuje nalezení této vlastnosti. Ladicí program neumí interpretovat vlastní typ řetězce, takže není vidět řetězec, který je držen uvnitř textového pole.

Totéž `TextBox` vypadá mnohem jednodušší v okně proměnné při natvis vlastní visualizer pravidla jsou použity. Důležité členy třídy se zobrazí společně a ladicí program zobrazí základní řetězec hodnotu vlastního typu řetězce.

![Data textového pole pomocí vizualizéru](../debugger/media/dbg_natvis_textbox_visualizer.png "Data textového pole pomocí vizualizéru")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>Použití souborů Natvis v projektech jazyka C++

Natvis používá *soubory .natvis* k určení pravidel vizualizace. Soubor *NATVIS* je soubor XML s příponou *NATVIS.* Schéma Natvis je definováno v *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*.

Základní struktura souboru *.natvis* je `Type` jeden nebo více prvků představujících položky vizualizace. Plně kvalifikovaný název `Type` každého prvku je `Name` určen v jeho atributu.

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

Visual Studio poskytuje některé soubory *.natvis* ve složce *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers.* Tyto soubory mají pravidla vizualizace pro mnoho běžných typů a mohou sloužit jako příklady pro psaní vizualizací pro nové typy.

### <a name="add-a-natvis-file-to-a-c-project"></a>Přidání souboru Natvis do projektu Jazyka C++

Soubor *Natvis* můžete přidat do libovolného projektu jazyka C++.

**Přidání nového souboru *Natvis:***

1. V Průzkumníku **řešení**vyberte uzel projektu C++ a vyberte Přidat**novou položku** **aplikace Project** > nebo klepněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte **visual c++** > **soubor** > **vizualizace ladicího programu nástroje (.natvis)**.

1. Pojmenujte soubor a vyberte **Přidat**.

   Nový soubor je přidán do **Průzkumníka řešení**a otevře se v podokně dokumentů sady Visual Studio.

Ladicí program sady Visual Studio načte soubory *Natvis* v projektech jazyka C++ automaticky a ve výchozím nastavení je také zahrne do souboru *PDB* při vytváření projektu. Pokud ladicí program ladicí program načte soubor *Natvis* ze souboru *PDB,* i když nemáte projekt otevřený. Pokud nechcete, aby byl soubor *Natvis* zahrnut do *souboru PDB*, můžete jej vyloučit ze vytvořeného souboru *PDB.*

**Vyloučení souboru *Natvis* z *databáze .pdb*:**

1. Vprůzkumníka **řešení**vyberte soubor *Natvis* a vyberte ikonu **Vlastnosti** nebo na něj klepněte pravým tlačítkem myši a vyberte **Vlastnosti**.

1. Rozbalte šipku vedle **položky Vyloučeno ze sestavení** a vyberte **Ano**a pak vyberte **OK**.

>[!NOTE]
>Pro ladění spustitelných projektů použijte položky řešení k přidání všech souborů *Natvis,* které nejsou v *databázi .pdb*, protože není k dispozici žádný projekt Jazyka C++.

>[!NOTE]
>Pravidla Natvis načtená z *souboru .pdb* se vztahují pouze na typy v modulech, na které odkazuje *.pdb.* Například pokud *Module1.pdb* má položku Natvis `Test`pro typ s `Test` názvem , platí pouze pro třídu v *Module1.dll*. Pokud jiný modul také definuje `Test`třídu s názvem , *položka Module1.pdb* Natvis se na ni nevztahuje.

**Instalace a registrace souboru *.natvis* pomocí balíčku VSIX:**

Balíček VSIX lze nainstalovat a zaregistrovat *.natvis* soubory. Bez ohledu na to, kde jsou nainstalovány, všechny registrované *.natvis* soubory jsou automaticky zvedl během ladění.

1. Zahrňte soubor *.natvis* do balíčku VSIX. Například pro následující soubor projektu:
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. Zaregistrujte soubor *.natvis* v souboru *source.extension.vsixmanifest:*
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a>Umístění souborů Natvis

Soubory *Natvis* můžete přidat do adresáře uživatelů nebo do systémového adresáře, pokud chcete, aby se vztahovaly na více projektů.

Soubory *.natvis* jsou vyhodnocovány v následujícím pořadí:

1. Všechny soubory *Natvis,* které jsou vloženy do *databáze .pdb,* kterou ladíte, pokud v načteném projektu neexistuje soubor se stejným názvem.

2. Všechny soubory *.natvis,* které jsou v načtené množiny projektu C++ nebo řešení nejvyšší úrovně. Tato skupina zahrnuje všechny načtené projekty jazyka C++, včetně knihoven tříd, ale ne projekty v jiných jazycích.

3. Všechny *.natvis* soubory nainstalované a registrované prostřednictvím balíčku VSIX.

::: moniker range="vs-2017"

4. Adresář Natvis specifický pro uživatele (například *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

4. Adresář Natvis specifický pro uživatele (například *%USERPROFILE%\Documents\Visual Studio 2019\Visualizers*).

::: moniker-end

5. Celosystémový adresář Natvis (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Tento adresář obsahuje soubory *Natvis* nainstalované v sadě Visual Studio. Pokud máte oprávnění správce, můžete do tohoto adresáře přidat soubory.

## <a name="modify-natvis-files-while-debugging"></a>Úprava souborů Natvis při ladění

Soubor *NaTVIS* můžete upravit v ide při ladění jeho projektu. Otevřete soubor ve stejné instanci sady Visual Studio, kterou ladíte, upravte ho a uložte. Jakmile je soubor uložen, **služba Watch** a **Locals** windows update tak, aby odrážela změnu.

Soubory *Natvis* můžete také přidat nebo odstranit v ladicím řešení a Visual Studio přidá nebo odebere příslušné vizualizace.

Soubory *NatvIS,* které jsou vloženy do souborů *PDB* při ladění, nelze aktualizovat.

Pokud změníte soubor *Natvis* mimo Visual Studio, změny se neprojeví automaticky. Chcete-li aktualizovat okna ladicího programu, můžete znovu vyhodnotit příkaz **.natvisreload** v okně **Okamžité.** Změny se pak projeví bez restartování relace ladění.

Pomocí příkazu **.natvisreload** můžete také upgradovat soubor *Natvis* na novější verzi. Soubor *Natvis* může být například zařazován do správy zdrojového kódu a chcete vyzvednout poslední změny, které provedl někdo jiný.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a>Výrazy a formátování
Vizualizace Natvis používají výrazy Jazyka C++ k určení datových položek, které se mají zobrazit. Kromě vylepšení a omezení výrazů jazyka C++ v ladicím programu, které jsou popsány v [operátoru Context (C++),](../debugger/context-operator-cpp.md)mějte na paměti následující skutečnosti:

- Natvis výrazy jsou vyhodnocovány v kontextu objektu, který je vizualizován, nikoli aktuální hostoři. Například `x` ve výrazu Natvis odkazuje na pole s názvem **x** v objektu, který je vizualizován, nikoli na místní proměnnou s názvem **x** v aktuální funkci. V výrazech Natvis nelze přistupovat k místním proměnným, i když můžete přistupovat ke globálním proměnným.

- Natvis výrazy neumožňují vyhodnocení funkce nebo vedlejší účinky. Volání funkcí a operátory přiřazení jsou ignorovány. Vzhledem k tomu, [že ladicí program vnitřní funkce](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) jsou bez vedlejších účinků, mohou být volně volány z libovolného výrazu Natvis, i když ostatní volání funkcí jsou zakázána.

- Chcete-li určit způsob zobrazení výrazu, můžete použít libovolný specifikátor formátu popsaný v [specifikátorech formátu v jazyce C++](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Specifikátory formátu jsou ignorovány, pokud je položka interně `Size` používána natvis, například výraz v [rozšíření ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

## <a name="natvis-views"></a>Natvis pohledy

Můžete definovat různé pohledy Natvis pro zobrazení typů různými způsoby. Zde je například `std::vector` vizualizace, která definuje zjednodušené zobrazení s názvem `simple`. `ArrayItems` Prvky `DisplayString` a se zobrazují ve `simple` výchozím zobrazení `[size]` a `[capacity]` v zobrazení, zatímco `simple` položky a se v zobrazení nezobrazují.

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

V okně **Kukátka** můžete pomocí specifikátoru formátu **zobrazení** zadat alternativní zobrazení. Jednoduché zobrazení se zobrazí jako **vec,view(simple)**:

![Okno kukátka s jednoduchým zobrazením](../debugger/media/watch-simpleview.png "Okno kukátka s jednoduchým zobrazením")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a>Natvis chyby

Když ladicí program narazí na chyby v položce vizualizace, ignoruje je. Buď zobrazí typ v jeho nezpracované podobě, nebo vybere jinou vhodnou vizualizaci. Pomocí diagnostiky Natvis můžete pochopit, proč ladicí program ignoroval položku vizualizace a zobrazit základní syntaxe a analýzy chyb.

**Zapnutí diagnostiky Natvis:**

- V části**Možnosti** **nástroje** > (nebo**Možnosti** **ladění)** >  **>** > **okno Ladění výstupu**nastavte diagnostické zprávy **Natvis (pouze C++)** na **Chyba**, **Upozornění**nebo **Verbose**a pak vyberte **OK**.

Chyby se zobrazí v okně **Výstup.**

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a>Odkaz na syntaxi Natvis

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a>Element automatického vizualizace
Prvek `AutoVisualizer` je kořenovým uzlem souboru *Natvis* a `xmlns:` obsahuje atribut oboru názvů.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

Prvek `AutoVisualizer` může mít [Type](#BKMK_Type), [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer)a [CustomVisualizer](#BKMK_CustomVisualizer) podřízené objekty.

### <a name="type-element"></a><a name="BKMK_Type"></a>Typový prvek

Základní `Type` vypadá jako tento příklad:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 Prvek `Type` určuje:

1. Pro jaký typ by měla být `Name` vizualizace použita (atribut).

2. Jak by měla vypadat hodnota objektu tohoto `DisplayString` typu (prvek).

3. Co členové typu by měl vypadat, když uživatel rozbalí typ `Expand` v okně proměnné (uzel).

#### <a name="templated-classes"></a>Šablony tříd
Atribut `Name` `Type` prvku přijímá hvězdičku `*` jako zástupný znak, který lze použít pro názvy předělaných tříd.

V následujícím příkladu se používá stejná vizualizace, zda je objekt nebo `CAtlArray<int>` `CAtlArray<float>`. Pokud existuje konkrétní položka vizualizace `CAtlArray<float>`pro , pak má přednost před obecnou.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Parametry šablony můžete v položce vizualizace odkazovat pomocí maker $T1, $T2 atd. Příklady těchto maker najdete v tématu *.natvis* files shipped with Visual Studio.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a>Porovnávání typů vizualizéru
Pokud se položka vizualizace nepodaří ověřit, použije se další dostupná vizualizace.

#### <a name="inheritable-attribute"></a>Dědičný atribut
Volitelný `Inheritable` atribut určuje, zda se vizualizace vztahuje pouze na základní typ nebo na základní typ a všechny odvozené typy. Výchozí hodnota `Inheritable` je `true`.

V následujícím příkladu se vizualizace vztahuje `BaseClass` pouze na typ:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Atribut priority

Volitelný `Priority` atribut určuje pořadí, ve kterém se mají používat alternativní definice, pokud se definici nepodaří analyzovat. Možné hodnoty `Priority` jsou: `Low` `MediumLow`,`Medium` `MediumHigh`, `High`, a . Výchozí hodnota je `Medium`. Atribut `Priority` rozlišuje pouze mezi prioritami v rámci stejného souboru *.natvis.*

Následující příklad nejprve analyzuje položku, která odpovídá 2015 STL. Pokud se to nepodaří analyzovat, použije alternativní položku pro verzi STL pro rok 2013:

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
Atribut můžete `Optional` umístit na libovolný uzel. Pokud dílčí výraz uvnitř volitelného uzlu se nezdaří analyzovat, ladicí program ignoruje tento `Type` uzel, ale použije zbytek pravidel. V následujícím typu `[State]` je nevolitelné, `[Exception]` ale je volitelné.  Pokud `MyNamespace::MyClass` má pole`M_exceptionHolder`s názvem `[State]` _ , `[Exception]` zobrazí se uzel i uzel, ale pokud žádné `_M_exceptionHolder` pole neexistuje, zobrazí se pouze `[State]` uzel.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a>Atribut Podmínka

Volitelný `Condition` atribut je k dispozici pro mnoho vizualizačních prvků a určuje, kdy se má použít pravidlo vizualizace. Pokud se výraz uvnitř atributu `false`podmínky přelože na , pravidlo vizualizace se nepoužije. Pokud je vyhodnocena `true`na `Condition` , nebo neexistuje žádný atribut, platí vizualizace. Tento atribut můžete použít pro logiku if-else v položkách vizualizace.

Například následující vizualizace má `DisplayString` dva prvky pro inteligentní typ ukazatele. Když `_Myptr` je člen prázdný, podmínka `DisplayString` prvního prvku `true`se překládá na , aby se formulář zoánkem. Pokud `_Myptr` člen není prázdný, podmínka vyhodnotí `false`a `DisplayString` druhý prvek zobrazí.

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

`IncludeView` Atributy `ExcludeView` a určují prvky, které se mají zobrazit nebo nebudou zobrazeny v určitých pohledech. Například v následující specifikaci `std::vector`Natvis v , `simple` `[size]` zobrazení `[capacity]` nezobrazuje a položky.

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

Atributy `IncludeView` a `ExcludeView` můžete použít na typy a na jednotlivých členech.

### <a name="version-element"></a><a name="BKMK_Versioning"></a>Prvek verze
Element `Version` obory vizualizace položky na konkrétní modul a verzi. Prvek `Version` pomáhá vyhnout se kolizím názvů, snižuje neúmyslné neshody a umožňuje různé vizualizace pro různé verze typu.

Pokud společný soubor záhlaví, který je používán různými moduly definuje typ, vizualizace s verzí se zobrazí pouze v případě, že typ je v zadané verzi modulu.

V následujícím příkladu je vizualizace použitelná pouze pro `DirectUI::Border` typ nalezený v `Windows.UI.Xaml.dll` verzi 1.0 až 1.5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Nepotřebujete obojí `Min` a `Max`. Jedná se o volitelné atributy. Nejsou podporovány žádné zástupné znaky.

Atribut `Name` je ve formátu *filename.ext*, například *hello.exe* nebo *some.dll*. Nejsou povoleny žádné názvy cest.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a>Element DisplayString
Prvek `DisplayString` určuje řetězec, který se má zobrazit jako hodnota proměnné. Přijímá libovolné řetězce smíchané s výrazy. Vše uvnitř složených závorek je interpretováno jako výraz. Například následující `DisplayString` položka:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Znamená, že proměnné `CPoint` typu se zobrazují jako na tomto obrázku:

 ![Použití elementu DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "Použití elementu DisplayString")

Ve `DisplayString` výrazu `x` `y`a , které `CPoint`jsou členy , jsou uvnitř složené závorky, takže jejich hodnoty jsou vyhodnoceny. Příklad také ukazuje, jak můžete uniknout složené závorky `{{` pomocí `}}` dvojité složené závorky ( nebo ).

> [!NOTE]
> Prvek `DisplayString` je jediný prvek, který přijímá libovolné řetězce a složených složených složených zlechcsyntax. Všechny ostatní prvky vizualizace přijmout pouze výrazy, které ladicí program může vyhodnotit.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a>Element StringView

Prvek `StringView` definuje hodnotu, kterou ladicí program může odeslat do předdefinovaného vizualizéru textu. Například s ohledem na následující `ATL::CStringT` vizualizaci pro typ:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

Objekt `CStringT` se zobrazí v okně proměnné, jako je tento příklad:

![CStringT DisplayString element](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT DisplayString element")

Přidání `StringView` prvku říká ladicímu programu, že může zobrazit hodnotu jako vizualizaci textu.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Během ladění můžete vybrat ikonu lupy vedle proměnné a pak vybrat **Vizualizér textu,** chcete-li zobrazit řetězec, na který **m_pszData** odkazuje.

 ![CStringT data s StringView vizualizér](../debugger/media/dbg_natvis_stringview_cstringt.png "CStringT data s StringView vizualizér")

Výraz `{m_pszData,su}` obsahuje specifikátor formátu C++ **su**, který zobrazí hodnotu jako řetězec Unicode. Další informace naleznete [v tématu Format specifiers in C++](../debugger/format-specifiers-in-cpp.md).

### <a name="expand-element"></a><a name="BKMK_Expand"></a>Rozbalit element

Volitelný `Expand` uzel přizpůsobí podřízené položky vizualizovaného typu při rozbalení typu v okně proměnné. Uzel `Expand` přijímá seznam podřízených uzlů, které definují podřízené prvky.

- Pokud `Expand` uzel není zadán v položce vizualizace, podřízené objekty používají výchozí pravidla rozšíření.

- `Expand` Pokud je uzel zadán bez podřízených uzlů pod ním, typ není rozbalitelný v oknech ladicího programu.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a>Rozšíření položky

 Prvek `Item` je nejzákladnější a nejběžnější `Expand` prvek v uzlu. `Item`definuje jeden podřízený prvek. Například `CRect` třída s `top`poli `left` `right`, `bottom` , a má následující položku vizualizace:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

V okně ladicího `CRect` programu vypadá typ takto:

![CRect s rozšířením prvku položky](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect s rozšířením prvku položky")

Ladicí program vyhodnotí výrazy `Width` `Height` zadané v elementech a zobrazí hodnoty ve sloupci **Hodnota** okna proměnné.

Ladicí program automaticky vytvoří uzel **[Raw View]** pro každé vlastní rozšíření. Předchozí snímek obrazovky zobrazí rozbalený uzel **[Raw View],** který ukazuje, jak se výchozí nezpracované zobrazení objektu liší od vizualizace Natvis. Výchozí rozšíření vytvoří podstrom pro základní třídu a zobrazí všechny datové členy základní třídy jako podřízené položky.

> [!NOTE]
> Pokud výraz prvku položky odkazuje na komplexní typ, uzel **Item** sám je rozbalitelný.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a>Rozšíření ArrayItems
Pomocí `ArrayItems` uzlu mít ladicí program Sady Visual Studio interpretovat typ jako pole a zobrazit jeho jednotlivé prvky. Vizualizace pro `std::vector` je dobrým příkladem:

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

A `std::vector` zobrazí své jednotlivé prvky při rozbalení v okně proměnné:

![std::vektor pomocí rozšíření ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vektor pomocí rozšíření ArrayItems")

Uzel `ArrayItems` musí mít:

- Výraz `Size` (který musí vyhodnotit na celé číslo) pro ladicí program pochopit délku pole.
- Výraz, `ValuePointer` který odkazuje na první prvek (který musí být ukazatelem typu prvku, který není `void*`).

Výchozí hodnota dolní meze pole je 0. Chcete-li hodnotu přepsat, použijte `LowerBound` prvek. Soubory *Natvis* dodávané se souborem Visual Studio mají příklady.

>[!NOTE]
>`[]` Operátor můžete použít například `vector[i]`u libovolné jednorozměrné vizualizace `ArrayItems`pole , která používá `CATLArray`, i když samotný typ (například ) tento operátor neumožňuje.

Můžete také určit vícerozměrná pole. V takovém případě ladicí program potřebuje o něco více informací, aby správně zobrazit podřízené prvky:

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

- `Direction`určuje, zda je pole v pořadí řádek hlavní nebo sloupec hlavní.
- `Rank`určuje pořadí pole.
- Prvek `Size` přijímá implicitní `$i` parametr, který nahradí indexem dimenze, aby našel délku pole v této dimenzi. V předchozím příkladu `_M_extent.M_base[0]` by měl výraz udávat délku 0. `_M_extent._M_base[1]`

Dvourozměrný `Concurrency::array` objekt vypadá v okně ladicího programu takto:

![Dvojrozměrné pole s rozšířením ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Dvojrozměrné pole s rozšířením ArrayItems")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a>Rozšíření indexových položek

Rozšíření lze `ArrayItems` použít pouze v případě, že prvky pole jsou rozloženy souvisle v paměti. Ladicí program se dostane k dalšímu prvku pouhým zvýšením ukazatele. Pokud potřebujete manipulovat s indexem na uzel `IndexListItems` hodnoty, použijte uzly. Tady je vizualizace s `IndexListItems` uzlem:

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

Jediný rozdíl `ArrayItems` mezi `IndexListItems` a `ValueNode`je , který očekává, že úplný výraz `$i` i<sup>th</sup> element s implicitní parametr.

>[!NOTE]
>`[]` Operátor můžete použít například `vector[i]`u libovolné jednorozměrné vizualizace `IndexListItems`pole , která používá `CATLArray`, i když samotný typ (například ) tento operátor neumožňuje.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a>Rozšíření LinkedListItems

Pokud vizualizovaný typ představuje propojený seznam, ladicí program `LinkedListItems` může zobrazit své podřízené prvky pomocí uzlu. Následující vizualizace pro `CAtlList` typ `LinkedListItems`používá :

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

Prvek `Size` odkazuje na délku seznamu. `HeadPointer`odkazuje na první `NextPointer` prvek, odkazuje na další `ValueNode` prvek a odkazuje na hodnotu položky.

Ladicí program vyhodnotí výrazy `NextPointer` a `ValueNode` `LinkedListItems` v kontextu prvku uzlu, nikoli nadřazeného typu seznamu. V předchozím příkladu `CAtlList` má `CNode` třídu `atlcoll.h`(nalezenou v ) která je uzem propojeného seznamu. `m_pNext`a `m_element` jsou pole `CNode` této třídy, nikoli třídy. `CAtlList`

`ValueNode`může být ponecháno `this` prázdné nebo `LinkedListItems` použít k odkazování na samotný uzel.

#### <a name="customlistitems-expansion"></a>Rozšíření CustomListItems

Rozšíření `CustomListItems` umožňuje psát vlastní logiku pro procházení datové struktury, jako je například hashtable. Slouží `CustomListItems` k vizualizaci datových struktur, které mohou používat výrazy jazyka C++ pro vše, `ArrayItems`co `IndexListItems`potřebujete `LinkedListItems`vyhodnotit, ale nevejdou se zcela do formy pro aplikace , nebo .

Můžete použít `Exec` ke spuštění kódu `CustomListItems` uvnitř rozšíření pomocí proměnných a objektů definovaných v rozšíření. Můžete použít logické operátory, aritmetické operátory a operátory přiřazení s `Exec`. Nelze použít `Exec` k vyhodnocení funkcí, s výjimkou [ladicího programu vnitřní funkce](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) podporované vyhodnocení výrazu C++.

Následující vizualizér `CAtlMap` pro `CustomListItems` je vynikajícípříklad, kde je to vhodné.

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

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a>Rozšíření položek stromu
 Pokud vizualizovaný typ představuje strom, ladicí program může chodit `TreeItems` stromu a zobrazit jeho podřízené prvky pomocí uzlu. Tady je vizualizace pro `std::map` typ `TreeItems` používající uzel:

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

Syntaxe je podobná `LinkedListItems` uzlu. `LeftPointer`, `RightPointer`a `ValueNode` jsou vyhodnocovány v kontextu třídy uzlu stromu. `ValueNode`může být ponechána `this` prázdná `TreeItems` nebo použít k odkazování na samotný uzel.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a>Rozšíření rozbalovací položky
 Prvek `ExpandedItem` generuje agregované podřízené zobrazení zobrazením vlastností základních tříd nebo datových členů, jako by byly podřízené objekty vizualizovaného typu. Ladicí program vyhodnotí zadaný výraz a připojí podřízené uzly výsledku do podřízeného seznamu vizualizovaného typu.

Například inteligentní ukazatel `auto_ptr<vector<int>>` typ obvykle zobrazí jako:

 ![automatické&#95;ptr&#60;vektorové&#60;int&#62;&#62; výchozí rozšíření](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Výchozí rozšíření")

 Chcete-li zobrazit hodnoty vektoru, musíte přejít k podrobnostem o `_Myptr` dvou úrovních v okně proměnné a projít členem. Přidáním `ExpandedItem` prvku můžete vyloučit `_Myptr` proměnnou z hierarchie a přímo zobrazit vektorové prvky:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![auto&#95;ptr&#60;vektorové&#60;int&#62;&#62; rozšíření expandeditem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Rozšíření rozbalovací položky")

Následující příklad ukazuje, jak agregovat vlastnosti ze základní třídy v odvozené třídě. Předpokládejme, `CPanel` že `CFrameworkElement`třída je odvozena z . Namísto opakování vlastností, které `CFrameworkElement` pocházejí `ExpandedItem` ze základní třídy, vizualizace uzlu připojí `CPanel` tyto vlastnosti k podřízenému seznamu třídy.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Specifikátor formátu **ND,** který vypne porovnávání vizualizací pro odvozenou třídu, je zde nezbytný. V opačném `*(CFrameworkElement*)this` případě by `CPanel` výraz způsobit vizualizaci, která má být použita znovu, protože výchozí pravidla přizpůsobení typu vizualizace považují za nejvhodnější. Pomocí specifikátoru formátu **ND** můžete debuggeru dát pokyn k použití vizualizace základní třídy nebo výchozího rozšíření, pokud základní třída nemá žádnou vizualizaci.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a>Rozšíření syntetických položek
 Zatímco `ExpandedItem` prvek poskytuje plošší zobrazení dat odstraněním `Synthetic` hierarchií, uzel dělá opak. Umožňuje vytvořit umělý podřízený prvek, který není výsledkem výrazu. Umělý prvek může mít vlastní podřízené prvky. V následujícím příkladu vizualizace `Concurrency::array` pro typ `Synthetic` používá uzel k zobrazení diagnostické zprávy uživateli:

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

 ![Souběžnost::Pole s rozšířením syntetického prvku](../debugger/media/dbg_natvis_expand_synthetic.png "Souběžnost::Pole s rozšířením syntetického prvku")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a>HResult prvek
 Prvek `HResult` umožňuje přizpůsobit informace zobrazené pro **HRESULT** v oknech ladicího programu. Prvek `HRValue` musí obsahovat 32bitovou hodnotu **HRESULT,** která má být přizpůsobena. Prvek `HRDescription` obsahuje informace, které se mají zobrazit v okně ladicího programu.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a>Prvek UIVisualizer
Prvek `UIVisualizer` zaregistruje modul plug-in grafického vizualizéru s ladicím programem. Grafický vizualizér vytvoří dialogové okno nebo jiné rozhraní, které zobrazuje proměnnou nebo objekt způsobem konzistentním s jeho datovým typem. Modul plug-in vizualizéru musí být vytvořen jako [VSPackage](../extensibility/internals/vspackages.md)a musí vystavit službu, kterou ladicí program může využívat. Soubor *.natvis* obsahuje registrační informace pro modul plug-in, jako je například jeho název, IDENTIFIKÁTOR GUID exponované služby a typy, které může vizualizovat.

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

- `ServiceId`  -  Dvojice `Id` atributů identifikuje `UIVisualizer`. Je `ServiceId` identifikátor GUID služby, kterou zpřístupňuje balíček vizualizéru. `Id`je jedinečný identifikátor, který rozlišuje vizualizéry, pokud služba poskytuje více než jeden. V předchozím příkladu poskytuje stejná služba vizualizéru dva vizualizéry.

- Atribut `MenuName` definuje název vizualizéru, který se má zobrazit v rozevíracím souboru vedle ikony lupy v ladicím programu. Příklad:

  ![Místní nabídka nabídky UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "Místní nabídka nabídky UIVisualizer")

Každý typ definovaný v souboru *Natvis* musí explicitně uvádět všechny vizualizéry ui, které jej mohou zobrazit. Ladicí program odpovídá odkazy vizualizéru v položkách typu s registrovanými vizualizéry. Například následující položka typu `std::vector` pro `UIVisualizer` odkazy v předchozím příkladu.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Příklad a můžete zobrazit `UIVisualizer` v rozšíření [Sledování obrázků,](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) které slouží k zobrazení bitmap v paměti.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>Prvek CustomVisualizer
 `CustomVisualizer`je bod rozšiřitelnosti, který určuje rozšíření VSIX, které píšete pro řízení vizualizací v kódu sady Visual Studio. Další informace o psaní rozšíření VSIX naleznete v [sadě Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Je to mnohem více práce napsat vlastní vizualizér, než definice XML Natvis, ale jste bez omezení o tom, co Natvis dělá nebo nepodporuje. Vlastní vizualizéry mají přístup k úplné sadě rozšíření ladění rozšiřitelnosti API, které můžete dotazovat a upravovat proces ladění nebo komunikovat s jinými částmi sady Visual Studio.

 Můžete použít `Condition`, `IncludeView`a `ExcludeView` atributy `CustomVisualizer` na prvky.

 ## <a name="limitations"></a>Omezení

Natvis přizpůsobení práce s třídami a struktury, ale ne typedefs.

Natvis nepodporuje vizualizéry pro primitivní `int` `bool`typy (například , ) nebo pro ukazatele na primitivní typy. V tomto scénáři je jednou z možností použití [specifikátoru formátu](../debugger/format-specifiers-in-cpp.md) odpovídající případu použití. Pokud například použijete `double* mydoublearray` v kódu, můžete použít specifikátor formátu pole v okně **Sledování** ladicího `mydoublearray, [100]`programu, například výraz , který zobrazuje prvních 100 prvků.
