---
title: Vytváření vlastních pohledů nativních objektů
description: Pomocí rozhraní Natvis přizpůsobit tak, že Visual Studio zobrazuje nativní typy v ladicím programu
ms.custom: ''
ms.date: 10/31/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 937692f11cbd642da823d6f7d13bcd90de59b388
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000858"
---
# <a name="create-custom-views-of-native-objects-in-the-debugger"></a>Vytváření vlastních zobrazení nativních objektů v ladicím programu

Visual Studio *Natvis* framework přizpůsobí tak, jak zobrazit nativní typy v oknech proměnných ladicího programu, třeba **lokální** a **Watch** windows a v **DataTips**. Vizualizace Natvis můžou pomoct typy, které můžete vytvořit více viditelné během ladění. 

Nahradí Natvis *autoexp.dat –* soubor v dřívějších verzích sady Visual Studio pomocí syntaxe jazyka XML, lepší diagnostiku, správu verzí a podpoře více souborů.  

Natvis nefunguje pro:

- Projekty C++ Windows desktop s **typ ladicího programu** nastavena na **smíšený** pod **vlastnosti konfigurace** > **ladění**. 
- [Ladění ve smíšeném režimu](how-to-debug-in-mixed-mode.md) pro desktopové aplikace Windows na spravovaný režim kompatibility (**nástroje** > **možnosti** > **ladění**  >  **Obecné** > **použít spravovaný režim kompatibility**).

## <a name="BKMK_Why_create_visualizations_"></a>Vizualizace Natvis

Pomocí rozhraní Natvis vytvořit pravidla vizualizace pro typy, že které vytvoříte, aby vývojáři mohou zobrazit je mnohem snazší během ladění.  

Například následující obrázek znázorňuje proměnnou typu [Windows::UI::Xaml::Controls::TextBox](http://go.microsoft.com/fwlink/?LinkId=258422) v okně ladicího programu bez jakékoli vlastní vizualizace.  

![Textové pole Výchozí vizualizace](../debugger/media/dbg_natvis_textbox_default.png "vizualizace výchozí textové pole")  

Zvýrazněný řádek ukazuje `Text` vlastnost `TextBox` třídy. Komplexní hierarchii tříd ztěžuje vyhledání této vlastnosti. Ladicí program nebude vědět, jak interpretovat typ vlastního řetězce, takže nevidíme řetězec uvnitř textového pole nelze zobrazit.  

Stejné `TextBox` vypadá mnohem jednodušší v okně proměnné, když jsou použita pravidla Natvis vlastní vizualizér. Společně zobrazit důležité členy třídy a ladicí program ukazuje základní hodnotu řetězce typu vlastního řetězce.  

![Textové pole dat pomocí vizualizéru](../debugger/media/dbg_natvis_textbox_visualizer.png "textového pole dat pomocí vizualizéru")  

##  <a name="BKMK_Using_Natvis_files"></a>Použít soubory .natvis v projektech C++  

Používá Natvis *.natvis* soubory lze určit pravidla vizualizace. A *.natvis* soubor je soubor XML s *.natvis* rozšíření. Schéma Natvis je definována v *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*.  

Základní struktura *.natvis* souboru je nejmíň jeden `Type` prvky představující položky vizualizace. Plně kvalifikovaný název každého `Type` prvek je zadán v jeho `Name` atribut.  

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

Visual Studio obsahuje některé *.natvis* soubory *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers* složky. Tyto soubory jsou pravidla vizualizace pro mnoho běžných typů a může sloužit jako příklady při psaní vizualizací pro nové typy.  

### <a name="add-a-natvis-file-to-a-c-project"></a>Přidání souboru .natvis do projektu jazyka C++  

Můžete přidat *.natvis* souboru do jakéhokoli projektu C++.  

**Chcete-li přidat nový *.natvis* souboru:**

1. Vyberte uzel projektu C++ ve **Průzkumníka řešení**a vyberte **projektu** > **přidat novou položku**, nebo klikněte pravým tlačítkem na projekt a vyberte **přidat**   >  **Nová položka**.
   
1. V **přidat novou položku** dialogového okna, vyberte **Visual C++** > **nástroj** > **soubor vizualizace ladicího programu (.natvis)**. 
   
1. Název souboru a vyberte **přidat**.
   
   Přidá nový soubor **Průzkumníka řešení**a otevře se v podokně dokumentu sady Visual Studio. 

Ladicí program sady Visual Studio načte *.natvis* soubory v projektech C++ automaticky a ve výchozím nastavení, také zahrnuje je do *PDB* souboru při sestavení projektu. Pokud ladíte sestavené aplikace, ladicí program načte *.natvis* soubor *PDB* souborů, i když nemáte otevřený projekt. Pokud nechcete, aby *.natvis* zahrnuté v souboru *PDB*, se můžete vyloučit z předdefinovaných *PDB* souboru.

**K vyloučení *.natvis* soubor *PDB*:**

1. Vyberte *.natvis* ve **Průzkumníka řešení**a vyberte **vlastnosti** ikonu, nebo klikněte pravým tlačítkem na soubor a vyberte **vlastnosti**.
   
1. Rozevírací šipku vedle položky **vyloučeno ze sestavení** a vyberte **Ano**a pak vyberte **OK**.  

>[!NOTE]
>Pro ladění spustitelného souboru projektů, použijte položky řešení a přidejte některý *.natvis* soubory, které nejsou *PDB*, protože není k dispozici žádný projekt C++.  

>[!NOTE]
>Natvis pravidla byla načtena z *PDB* platí pouze pro typy v modulech, které *PDB* odkazuje na. Například pokud *Module1.pdb* má položku Natvis pro typ s názvem `Test`, platí jenom pro `Test` třídy v *Module1.dll*. Pokud se jiný modul také definuje třídu s názvem `Test`, *Module1.pdb* položky Natvis se nevztahuje na ni.  

### <a name="BKMK_natvis_location"></a> Umístění souborů Natvis  

Můžete přidat *.natvis* soubory do svého adresáře uživatel nebo systémový adresář, pokud chcete použít pro více projektů.  

*.Natvis* soubory jsou vyhodnocovány v následujícím pořadí:  

1. Všechny *.natvis* soubory, které jsou vložené *PDB* ladění, pokud existuje soubor stejného názvu v načtený projekt.  

1. Žádné *.natvis* soubory, které jsou v načtený projekt C++ nebo nejvyšší úrovně řešení. Tato skupina obsahuje všechny načtené projekty C++, včetně knihoven tříd, ale ne projekty v jiných jazycích. 

1.  Adresář Natvis konkrétního uživatele (například *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*).  

1.  Adresář systémová Natvis (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Tento adresář je *.natvis* soubory, které jsou nainstalované s Visual Studio. Pokud máte oprávnění správce, můžete přidat soubory do tohoto adresáře.  

## <a name="modify-natvis-files-while-debugging"></a>Upravte soubory .natvis při ladění  

Můžete upravit *.natvis* soubor v integrovaném vývojovém prostředí při ladění svůj projekt. Otevřete soubor ve stejné instanci sady Visual Studio, kterou ladíte s, upravte ho a uložte ho. Poté, co je soubor uložen, **Watch** a **lokální** windows aktualizujte tak, aby odrážely změny. 

Můžete také přidat nebo odstranit *.natvis* souborů do řešení, který ladíte, a sady Visual Studio přidá nebo odebere relevantní vizualizace.  

Nelze aktualizovat *.natvis* soubory, které jsou součástí *PDB* soubory během ladění.  

Pokud změníte *.natvis* souboru mimo sadu Visual Studio, změny se projeví automaticky. Aktualizovat oknech ladicího programu, přehodnotit **.natvisreload** v příkaz **Watch** okna. Následně pak změny budou účinné bez restartování relace ladění.  

Použít také **.natvisreload** příkaz pro upgrade *.natvis* souboru na novější verzi. Například *.natvis* soubor může být zařazeno do správy zdrojového kódu a chcete vyzvednutí poslední změny této někdo udělali jinak. 

##  <a name="BKMK_Expressions_and_formatting"></a> Výrazy a formátování  
Vizualizace Natvis používají výrazy jazyka C++ k určení položek dat k zobrazení. Kromě vylepšení a omezení výrazů jazyka C++ v ladicím programu, které jsou popsány v [kontextový operátor (C++)](../debugger/context-operator-cpp.md), mějte na paměti z následujících akcí:  

- Výrazy Natvis jsou vyhodnocovány v kontextu objektu, který je právě vizualizován, není aktuální rámec zásobníku. Například `x` v Natvis výraz odkazuje na pole s názvem **x** v objektu, který je právě vizualizován, nikoli na místní proměnnou s názvem **x** v aktuální funkci. Lokální proměnné ve výrazech Natvis, nelze přistupovat, i když můžete přístup ke globálním proměnným.  

- Výrazy Natvis neumožňují vyhodnocování funkcí nebo vedlejší účinky. Volání funkce a operátory přiřazení jsou ignorovány. Protože [vnitřní funkce ladicího programu](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) jsou bez vedlejších účinků, lze je volně volat z libovolného výrazu Natvis, i když ostatní volání funkce jsou zakázána.  

- Pokud chcete řídit způsob, jakým zobrazuje výrazu, můžete použít některý z formátů specifikátoru, je popsáno v [v jazyce C++ specifikátory formátu](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Specifikátory formátu jsou ignorovány, pokud položka je použit interně souborem Natvis, jako `Size` výrazu v [rozšíření ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).  

## <a name="natvis-views"></a>Zobrazení Natvis  

Můžete definovat různá zobrazení Natvis, chcete-li zobrazit typy různými způsoby. Zde je vizualizace z například `std::vector` , který definuje zjednodušené zobrazení s názvem `simple`. `DisplayString` a `ArrayItems` elementy zobrazí ve výchozím zobrazení a `simple` zobrazení, zatímco `[size]` a `[capacity]` položek nezobrazovat v `simple` zobrazení. 

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


V **Watch** okno, použijte **, zobrazení** specifikátor formátu pro určit alternativní zobrazení. Jednoduché zobrazení se zobrazí jako **vec,view(simple)**:  

![Okno kukátka s jednoduchým](../debugger/media/watch-simpleview.png "okna kukátka s jednoduché zobrazení")  

##  <a name="BKMK_Diagnosing_Natvis_errors"></a> Chyb Natvis  

Pokud ladicí program narazí na chyby v položce vizualizace, se ignoruje. Je buď zobrazí typ v syrové podobě nebo zvolí jinou vhodnou vizualizaci. Diagnostika Natvis můžete pochopit, proč ladicí program ignoruje záznamu vizualizace nebo můžete zobrazit výchozí syntaxi a chyby analýzy. 

**Chcete-li na Diagnostika Natvis:**

- V části **nástroje** > **možnosti** (nebo **ladění** > **možnosti**) > **ladění**  >  **Okno výstup**, nastavte **diagnostické zprávy Natvis (pouze C++)** k **chyba**, **upozornění**, nebo  **Podrobné**a pak vyberte **OK**. 

Chyby se zobrazí v **výstup** okna.  

##  <a name="BKMK_Syntax_reference"></a> Referenční příručka syntaxe Natvis  

###  <a name="BKMK_AutoVisualizer"></a> AutoVisualizer – element  
`AutoVisualizer` Element je kořenový uzel *.natvis* souboru a obsahuje obor názvů `xmlns:` atribut. 

```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

`AutoVisualizer` Prvek může mít [typ](#BKMK_Type), [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer), a [CustomVisualizer](#BKMK_CustomVisualizer) podřízené položky. 

###  <a name="BKMK_Type"></a> Type element  

Základní `Type` vypadá podobně jako v tomto příkladu:  

```xml
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  
```  

 `Type` Prvek určuje:  

1. Jaký typ vizualizace má být použita pro ( `Name` atributu).  
   
2. Hodnota objektu tohoto typu by měl vypadat ( `DisplayString` element).  
   
3. Členy typu by měla vypadat podobně jako když je uživatel rozbalí v okně proměnné typu ( `Expand` uzlu).  
   
#### <a name="templated-classes"></a>Šablony tříd
`Name` Atribut `Type` element přijímá hvězdičku `*` jako zástupný znak, který lze použít pro názvy tříd šablon.  

V následujícím příkladu se používá stejné vizualizace, zda je objekt `CAtlArray<int>` nebo `CAtlArray<float>`. Pokud existuje konkrétní položka vizualizace pro `CAtlArray<float>`, má přednost před obecnou položkou.  

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

Můžete odkazovat na parametry šablony v položce vizualizace pomocí maker $t1, $t2 a tak dále. Chcete-li najít příklady těchto maker, přečtěte si téma *.natvis* soubory, které jsou součástí sady Visual Studio.  

####  <a name="BKMK_Visualizer_type_matching"></a> Porovnávání typu vizualizéru  
Pokud záznam vizualizace selže k ověření, použije se další dostupná vizualizace.  

#### <a name="inheritable-attribute"></a>Odvoditelný atribut  
Volitelný `Inheritable` atribut určuje, zda platí pouze pro základní typ vizualizace, nebo pro základní typ a všechny odvozené typy. Výchozí hodnota `Inheritable` je `true`.  

V následujícím příkladu platí vizualizace pouze `BaseClass` typu:  

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

#### <a name="priority-attribute"></a>Atribut priority  

Volitelný `Priority` atribut určuje pořadí, ve kterých se má použít alternativní definice, pokud se nepodaří analyzovat definici. Možné hodnoty `Priority` jsou: `Low`, `MediumLow`,`Medium`, `MediumHigh`, a `High`. Výchozí hodnota je `Medium`. `Priority` Atribut odlišuje pouze mezi priorit v rámci stejného *.natvis* souboru.  

Následující příklad analyzuje první položku, která odpovídá 2015 STL. Pokud se to nepodaří analyzovat, používá alternativní vstupní verze 2013 STL:  

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
Můžete umístit `Optional` atribut na libovolný uzel. Pokud dílčí výraz uvnitř volitelné uzlu se nepodaří analyzovat, ladicí program ignoruje tohoto uzlu, ale zbývající část se vztahuje `Type` pravidla. V následující typ `[State]` je povinný, ale `[Exception]` je volitelný.  Pokud `MyNamespace::MyClass` má pole s názvem _`M_exceptionHolder`, i `[State]` uzlu a `[Exception]` uzel se zobrazí, ale pokud se žádné `_M_exceptionHolder` pole pouze `[State]` uzel se zobrazí.

```xml
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

###  <a name="BKMK_Condition_attribute"></a> Atribut podmínky  

Volitelný `Condition` atribut je k dispozici pro mnoho prvků vizualizace a určuje, kdy použít pravidlo vizualizace. Pokud má výraz uvnitř atributu podmínky se překládá na `false`, neplatí pravidlo vizualizace. Pokud je vyhodnocen jako `true`, nebo neexistuje žádný `Condition` atributu, platí vizualizace. Tento atribut slouží pro logiku if-else v položkách vizualizace. 

Například následující vizualizace má dvě `DisplayString` prvky pro typ inteligentního ukazatele. Když `_Myptr` člena je prázdný, podmínka prvního `DisplayString` element se překládá na `true`, takže se zobrazí, které tvoří. Když `_Myptr` člen není prázdná, bude podmínka vyhodnocena jako `false`a druhá `DisplayString` zobrazí element.  

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

`IncludeView` a `ExcludeView` atributy určují prvky pro zobrazení nebo se nezobrazí v konkrétní zobrazení. Například v následující specifikaci Natvis `std::vector`, `simple` zobrazení nezobrazuje `[size]` a `[capacity]` položky.

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

Můžete použít `IncludeView` a `ExcludeView` atributy na typy a na jednotlivých členů.  

###  <a name="BKMK_Versioning"></a> Version element  
`Version` Element obory položky vizualizace na konkrétní modul a verzi. `Version` Element pomáhá zabránit kolize názvů, snižuje zvyšuje ochranu před nechtěnými neshody a umožňuje různé vizualizace pro jiný typ verze.  

Pokud společný soubor hlaviček, který je používán různými moduly definuje typ, vizualizace označená čísly verzí se zobrazí pouze v případě, že typ je ve verzi zadaný modul.  

V následujícím příkladu vizualizace je možné použít pouze `DirectUI::Border` typ nalezen v `Windows.UI.Xaml.dll` z verze 1.0 do 1.5. 

```xml
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

###  <a name="BKMK_DisplayString"></a> DisplayString element 
`DisplayString` Prvek určuje řetězec k zobrazení jako hodnotu proměnné. Přijímá libovolné řetězce smíšené s výrazy. Vše uvnitř složených závorek je interpretováno jako výraz. Například následující `DisplayString` položky:  

```xml
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  
```  

Prostředky této proměnné typu `CPoint` zobrazení jako v tomto obrázku:  

 ![Použití elementu DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "použití elementu DisplayString")  

V `DisplayString` výrazu, `x` a `y`, které jsou členy objektu `CPoint`, jsou uvnitř složených závorek, takže jejich hodnoty jsou vyhodnocovány. Tento příklad také ukazuje, jak může uniknout složenou závorku pomocí dvojitých složených závorek ( `{{` nebo `}}` ).  

> [!NOTE]
> `DisplayString` Element je jediným prvkem, který přijímá libovolné řetězce a syntaxi složených závorek. Všechny ostatní prvky vizualizace přijímají pouze výrazy, které můžou vyhodnocovat ladicí program.  

###  <a name="BKMK_StringView"></a> StringView – element 

`StringView` Element definuje hodnotu, která se ladicí program může odesílat do zabudovanému vizualizátoru textu. Mějme například následující vizualizaci `ATL::CStringT` typu:  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>
```  

`CStringT` Objektu se zobrazí v okně proměnné jako v tomto příkladu:   

![Element CStringT DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "elementu CStringT DisplayString")  

Přidání `StringView` element sdělí ladicímu programu, můžete zobrazení hodnoty jako vizualizací textu.  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

Během ladění, můžete vybrat ikonu lupy vedle proměnné a pak vyberte **Vizualizátor textu** k zobrazení řetězce, který **m_pszData** odkazuje na.  

 ![CStringT dat se vizualizér StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "CStringT data pomocí StringView vizualizéru")  

Výraz `{m_pszData,su}` obsahuje specifikátor formátu jazyka C++ **su**, aby se zobrazil hodnotu jako řetězec znaků Unicode. Další informace najdete v tématu [v jazyce C++ specifikátory formátu](../debugger/format-specifiers-in-cpp.md).  

###  <a name="BKMK_Expand"></a> Rozbalte – element 

Volitelný `Expand` uzel přizpůsobí podřízené objekty vizualizačního typu při rozšiřování typu v okně proměnné. `Expand` Uzlu přijímá seznam podřízených uzlů, které určují podřízené prvky.  

- Pokud `Expand` uzel není zadané v položce vizualizace, podřízené položky použít výchozí pravidla rozšíření.  
  
- Pokud `Expand` uzel, který je zadán bez podřízených uzlů pod ním, typ není v oknech ladicího programu rozšiřitelný.  

####  <a name="BKMK_Item_expansion"></a> Rozšiřovací bod  

 `Item` Element je nejvíce basic a společný element `Expand` uzlu. `Item` definuje jeden podřízený prvek. Například `CRect` třídy s poli `top`, `left`, `right`, a `bottom` má následující položku vizualizace:  

```xml
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  
```  

V okně ladicího programu `CRect` typ bude vypadat jako v tomto příkladu:  

![Crect – pomocí rozšíření elementu položky](../debugger/media/dbg_natvis_expand_item_crect1.png "crect – s rozšiřovací bod elementu")  

Ladicí program vyhodnotí výrazy určené v `Width` a `Height` elementy a zobrazuje hodnoty v **hodnotu** sloupci okna proměnných. 

Ladicí program automaticky vytvoří **[Raw View]** uzel pro každý vlastní rozšíření. Na předchozím snímku obrazovky se zobrazí **[Raw View]** rozbalení uzlu, chcete-li zobrazit, jak se liší od jeho vizualizace Natvis výchozí nezpracovaným zobrazením objektu. Výchozí rozšíření vytvoří podstrom pro základní třídu a jsou uvedeny všechny datové členy základní třídy jako podřízené objekty.  

> [!NOTE]
> Pokud výraz prvku položky odkazuje na komplexní typ, **položky** samotný uzel je rozšiřitelné.  

####  <a name="BKMK_ArrayItems_expansion"></a> Rozšíření ArrayItems  
Použití `ArrayItems` uzel ladicí program sady Visual Studio při interpretaci typu jako pole a zobrazení jeho jednotlivých prvků. Vizualizace pro `std::vector` je typickým příkladem:  

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

A `std::vector` ukazuje jeho jednotlivé prvky při rozbalení v okně proměnné:  

![pomocí rozšíření ArrayItems std::Vector](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector pomocí rozšíření ArrayItems")  

`ArrayItems` Uzel musí mít:  

- A `Size` výraz (který se musí vyhodnotit na celé číslo) pro ladicí program pro pochopení délky pole.  
- A `ValuePointer` výraz, který odkazuje na první prvek (který musí být ukazatelem typu prvku, který není `void*`).  

Výchozí hodnota je dolní mez pole je 0. Chcete-li přepsat hodnotu, použijte `LowerBound` elementu. *.Natvis* soubory dodané s aplikací Visual Studio obsahují příklady.  

>[!NOTE]
>Můžete použít `[]` operátoru, například `vector[i]`, se všechny vizualizace jednorozměrné pole, která používá `ArrayItems`i v případě samotného typu (například `CATLArray`) neumožňuje tento operátor.  

Vícerozměrná pole můžete také zadat. V takovém případě ladicí program potřebuje něco více informací ke správnému zobrazení podřízených prvků:  

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

- `Direction` Určuje, zda je v pořadí preferujícím řádek nebo sloupcové pole. 
- `Rank` Určuje pořadí v poli. 
- `Size` Element přijímá implicitní `$i` parametr, který nahradí rozměrem indexu pro vyhledání délky pole v dané dimenzi. V předchozím příkladu výraz `_M_extent.M_base[0]` by měl uvádět délku 0 dimenze `_M_extent._M_base[1]` 1. a tak dále.  

Tady je způsob, jakým dvourozměrném `Concurrency::array` objekt hledá v okně ladicího programu:  

![Dvourozměrné pole s rozšíření ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "dvojrozměrné pole s rozšíření ArrayItems")  

####  <a name="BKMK_IndexListItems_expansion"></a> Rozšíření IndexListItems  

Můžete použít `ArrayItems` rozšíření jenom v případě, že jsou prvky pole rozloženy souvisle v paměti. Ladicí program získá další prvek jednoduchým zvýšením jeho ukazatele. Pokud potřebujete pracovat s indexem na uzel hodnoty, použijte `IndexListItems` uzly. Zde je vizualizace s využitím `IndexListItems` uzlu:  

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

Jediným rozdílem mezi `ArrayItems` a `IndexListItems` je `ValueNode`, která očekává úplný výraz, který i<sup>th</sup> element s implicitním `$i` parametru.  

>[!NOTE]
>Můžete použít `[]` operátoru, například `vector[i]`, se všechny vizualizace jednorozměrné pole, která používá `IndexListItems`i v případě samotného typu (například `CATLArray`) neumožňuje tento operátor.  

####  <a name="BKMK_LinkedListItems_expansion"></a> Rozšíření LinkedListItems  

Pokud vizualizovaný typ představuje propojený seznam, ladicí program může zobrazit jeho podřízené položky pomocí `LinkedListItems` uzlu. Následující vizualizaci `CAtlList` zadejte používá `LinkedListItems`:  

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

`Size` Element označuje délku seznamu. `HeadPointer` odkazuje na první prvek `NextPointer` odkazuje na další prvek a `ValueNode` odkazuje na hodnotu položky.  

Ladicí program vyhodnotí `NextPointer` a `ValueNode` výrazy v kontextu `LinkedListItems` uzlu elementu, nikoli typu nadřazeného seznamu. V předchozím příkladu `CAtlList` má `CNode` třídy (součástí `atlcoll.h`), který je uzel propojeného seznamu. `m_pNext` a `m_element` jsou pole této `CNode` třídy, ne `CAtlList` třídy.  

`ValueNode` může být ponechán prázdný nebo použijte `this` k odkazování `LinkedListItems` samotný uzel.  

#### <a name="customlistitems-expansion"></a>CustomListItems rozšíření  
`CustomListItems` Rozšíření umožňuje psát vlastní logiku procházení datové struktury, jako například zatřiďovací tabulku. Použít `CustomListItems` vizualizovat datové struktury, které můžete použít výrazy jazyka C++ pro všechno, co potřebujete k vyhodnocení, ale není úplně přizpůsobit tvaru pro `ArrayItems`, `IndexListItems`, nebo `LinkedListItems`.  

Následující vizualizér pro `CAtlMap` je vynikajícím příkladem kde `CustomListItems` je vhodné.  

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

Můžete použít `Exec` k provádění kódu uvnitř `CustomListItems` rozšíření použití proměnných a objektů definovaných v rozšíření. Můžete použít logické operátory, aritmetické operátory a operátory přiřazení s `Exec`. Nemůžete použít `Exec` k vyhodnocení funkce.

`CustomListItems` podporuje následující vnitřní funkce:

- `strlen`, `wcslen`, `strnlen`, `wcsnlen`, `strcmp`, `wcscmp`, `_stricmp`, `_strcmpi`, `_wcsicmp`, `strncmp`, `wcsncmp`, `_strnicmp`, `_wcsnicmp`, `memcmp`, `memicmp`, `wmemcmp`, `strchr`, `wcschr`, `memchr`, `wmemchr`, `strstr`, `wcsstr`, `__log2`, `__findNonNull`
- `GetLastError`, `TlsGetValue`, `DecodeHString`, `WindowsGetStringLen`, `WindowsGetStringRawBuffer`, `WindowsCompareStringOrdinal`, `RoInspectCapturedStackBackTrace`, `CoDecodeProxy`, `GetEnvBlockLength`, `DecodeWinRTRestrictedException`, `DynamicMemberLookup`, `DecodePointer`, `DynamicCast`
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

####  <a name="BKMK_TreeItems_expansion"></a> Rozšíření TreeItems  
 Pokud vizualizovaný typ představuje strom, ladicí program může strom procházet a zobrazit jeho podřízené položky pomocí `TreeItems` uzlu. Zde je vizualizace pro `std::map` zadejte pomocí `TreeItems` uzlu:  

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

Syntaxe je podobná `LinkedListItems` uzlu. `LeftPointer`, `RightPointer`, a `ValueNode` jsou vyhodnocovány v kontextu třídy uzlu stromu. `ValueNode` může být ponechán prázdný nebo použijte `this` k odkazování `TreeItems` samotný uzel.  

####  <a name="BKMK_ExpandedItem_expansion"></a> Rozšíření ExpandedItem  
 `ExpandedItem` Element generuje agregovaných podřízených zobrazení zobrazením vlastností základních tříd nebo datových členů, jako kdyby byly podřízené prvky typu visualized. Ladicí program vyhodnotí zadaný výraz a připojí podřízené uzly výsledku do seznamu podřízených vizualizovaného typu. 

Například typ inteligentního ukazatele `auto_ptr<vector<int>>` obvykle zobrazí jako:  

 ![Automatické&#95;ptr&#60;vektoru&#60;int&#62; &#62; výchozí rozšíření](../debugger/media/dbg_natvis_expand_expandeditem_default.png "výchozí rozšíření")  

 Chcete-li zobrazit hodnoty vektoru, máte dvě úrovně níž v okně proměnné, prochází k podrobnostem `_Myptr` člena. Tak, že přidáte `ExpandedItem` element, můžete eliminovat `_Myptr` proměnné z hierarchie a přímo zobrazit prvky vektoru:  

```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
```  

 ![Automatické&#95;ptr&#60;vektoru&#60;int&#62; &#62; rozšíření ExpandedItem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "rozšíření ExpandedItem")  

Následující příklad ukazuje, jak se spojují vlastnosti ze základní třídy v odvozené třídě. Předpokládejme, `CPanel` třída odvozena z `CFrameworkElement`. Namísto opakování vlastností, které pocházejí ze základní `CFrameworkElement` třídy, `ExpandedItem` vizualizace uzel připojí k seznamu podřízených třídy tyto vlastnosti `CPanel` třídy. 

```xml
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  
```  

**Nd** specifikátor formátu, který vypne odpovídající pro odvozenou třídu vizualizace, je nutný zde. V opačném případě výraz `*(CFrameworkElement*)this` by způsobilo `CPanel` vizualizaci znovu použít, protože typ odpovídajících pravidel vizualizace výchozí považuje za nejvhodnější. Použít **nd** specifikátor formátu pro pokyn ladicímu programu používat vizualizaci základní třídy nebo výchozí rozšíření, pokud základní třída nemá žádné vizualizace.  

####  <a name="BKMK_Synthetic_Item_expansion"></a> Syntetické rozšiřovací bod  
 Zatímco `ExpandedItem` element obsahuje plošší zobrazení dat odstraněním hierarchií, `Synthetic` uzel provádí opak. Umožňuje vytvořit umělý podřízený prvek, který není výsledkem výrazu. Umělé prvek může mít svůj vlastní podřízené prvky. V následujícím příkladu vizualizace pro `Concurrency::array` typ používá `Synthetic` uzel k zobrazení diagnostické zprávy uživateli:  

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

 ![Concurrency::Array pomocí syntetických element rozšíření](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency::Array pomocí syntetických element rozšíření")  

###  <a name="BKMK_HResult"></a> HResult – element 
 `HResult` Element umožňuje přizpůsobit informace zobrazené pro **HRESULT** v oknech ladicího programu. `HRValue` Element musí obsahovat hodnotu 32-bit **HRESULT** , který je možné přizpůsobit. `HRDescription` Prvek obsahuje informace, které se zobrazí v okně ladicího programu.  

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

###  <a name="BKMK_UIVisualizer"></a> UIVisualizer – element 
A `UIVisualizer` prvek registruje modul plug-in grafického vizualizéru s ladicím programem. Grafického vizualizéru vytvoří dialogové okno nebo jiné rozhraní, které zobrazuje proměnné nebo objektu způsobem konzistentní s jeho datového typu. Modul plug-in vizualizéru musí být vytvořen jako [VSPackage](../extensibility/internals/vspackages.md)a je třeba zpřístupnit služby, které využívají ladicí program. *.Natvis* soubor obsahuje registrační informace pro modul plug-in, například jeho název, identifikátor GUID, vystavené služby a typy lze vizualizovat.  

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

- A `ServiceId`  -  `Id` identifikuje dvojice atributů `UIVisualizer`. `ServiceId` Je identifikátor GUID služby vizualizéru zpřístupňuje balíčku. `Id` je jedinečný identifikátor, který odlišuje vizualizérů, pokud služba poskytuje více než jeden. V předchozím příkladu poskytuje jedna služba vizualizéru dva vizualizéry.  
  
- `MenuName` Atribut definuje název vizualizéru má být zobrazen v rozevíracím seznamu vedle ikony lupy v ladicím programu. Příklad:  

  ![Místní nabídky UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "UIVisualizer místní nabídky")  

Každý typ definovaný v *.natvis* souboru musí explicitně uvádět žádné vizualizéry uživatelského rozhraní, které se bude zobrazovat. Ladicí program odpovídá odkazům vizualizéru v položkách typu s registrovanými vizualizéry. Například následující typ položky pro `std::vector` odkazy `UIVisualizer` v předchozím příkladu.  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 Vidíte příklad `UIVisualizer` v [Image Watch](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.ImageWatch2017) rozšíření zobrazíte rastrové obrázky v paměti. 

### <a name="BKMK_CustomVisualizer"></a>CustomVisualizer – element  
 `CustomVisualizer` je bod rozšíření, která určuje příponu VSIX, který píšete pro ovládací prvek vizualizace ve Visual Studio code. Další informace o psaní rozšíření VSIX, najdete v článku [Visual Studio SDK](../extensibility/visual-studio-sdk.md). 

Je mnohem více práce napsat vlastní vizualizér než definici rozhraní XML Natvis, ale budete bez omezení, o co Natvis nepodporuje ani nepodporuje. Vlastní vizualizátory mají přístup k úplné sadě rozšiřitelností ladicího programu rozhraní API, které můžete zadat dotaz a upravit laděném procesu nebo komunikaci s jinými částmi sady Visual Studio.  

 Můžete použít `Condition`, `IncludeView`, a `ExcludeView` atributy na `CustomVisualizer` elementy.
