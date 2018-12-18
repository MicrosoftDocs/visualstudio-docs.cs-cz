---
title: Vytváření vlastních zobrazení nativních objektů | Dokumentace Microsoftu
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
- natvis
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff03e5e07c07b4516009c7606f8a8ea183c57298
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732498"
---
# <a name="create-custom-views-of-native-objects"></a>Vytváření vlastních zobrazení nativních objektů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozhraní Visual Studio Natvis umožňuje přizpůsobit způsob, jakým Visual Studio zobrazuje nativní typy v oknech proměnných ladicího programu (například **Watch**, **lokální**, a **datových tipech** systému windows.  

 Nahrazuje Natvis **autoexp.dat –** soubor, který se používal v dřívějších verzích sady Visual Studio a nabízí syntaxi XML, lepší diagnostiku, správu verzí a podporu více souborů.  

> [!NOTE]
>  Rozhraní Natvis nelze použít pro vizualizace při:  
> 
> - Ladění projektu C++ Windows klasické pracovní plochy s nastaveným typem ladicí program **smíšené**.  
>   -   Provádíte ladění ve smíšeném režimu v aplikaci klasické pracovní plochy Windows v spravovaný režim kompatibility (**nástroje / Možnosti / ladění / obecné / použít spravovaný režim kompatibility**).  
>   -   Ladění aplikací pro stolní počítače Windows v režimu kompatibility nativní (**nástroje / Možnosti / ladění / obecné a použít nativní režim kompatibility**).  

##  <a name="BKMK_Why_create_visualizations_"></a> Proč vytvářet vizualizace Natvis?  
 Můžete použít rozhraní Natvis vytvořit pravidla vizualizace pro typy, že které vytvoříte, takže vývojáři mohou zobrazit snadno během ladění.  

 Například následující obrázek ukazuje proměnné typu [Windows::UI::Xaml::Controls::TextBox](http://go.microsoft.com/fwlink/?LinkId=258422) , která se zobrazí v ladicím programu bez jakékoli vlastní vizualizace.  

 ![Textové pole Výchozí vizualizace](../debugger/media/dbg-natvis-textbox-default.png "DBG_NATVIS_TextBox_Default")  

 Zvýrazněný řádek ukazuje `Text` vlastnost `TextBox` třídy. Komplexní hierarchii tříd ztěžuje vyhledání tuto hodnotu; ladicí program navíc neví, jak interpretovat typ vlastního řetězce používané tímto objektem, takže nevidíme řetězec uvnitř textového pole nelze zobrazit.  

 Stejné `TextBox` vypadá mnohem jednodušší n v okně proměnné, když se použijí vlastní pravidla vizualizace. Současně lze zobrazit důležité členy třídy a ladicí program ukazuje základní hodnotu řetězce typu vlastního řetězce.  

 ![Textové pole dat pomocí vizualizéru](../debugger/media/dbg-natvis-textbox-visualizer.png "DBG_NATVIS_TextBox_Visualizer")  

##  <a name="BKMK_Using_Natvis_files"></a> Použití souborů Natvis  
 .natvis soubory jsou soubory XML s příponou .natvis. Schéma je definována v **%VSINSTALLDIR%\Xml\Schemas\natvis.xsd**.  

 Základní struktura souboru .natvis je jeden nebo více `Type` prvků, kde každý `Type` představuje zadání vizualizace pro typ, jehož plně kvalifikovaný název je zadán v elementu `Name` atribut.  

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

 Visual Studio obsahuje některé soubory .natvis ve **%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers** složky. Tyto soubory obsahují pravidla vizualizace pro mnoho běžných typů a může sloužit jako příklady při psaní vizualizací pro nové typy.  

## <a name="adding-natvis-files-to-your-projects"></a>Přidávají se soubory .natvis do projektů  
 Soubory .natvis můžete přidat do jakéhokoli projektu C++.  

 Chcete-li přidat nový soubor .natvis, s otevřít projekt C++ vyberte uzel projektu v **Průzkumníku řešení**a klikněte na tlačítko **přidat / nové položky / Visual C++ / Utility / ladicího programu soubor vizualizace (.natvis)**. Ladicí program načte soubory Natvis automaticky z projektů v jazyce C++. Ve výchozím nastavení jsou soubory Natvis ve vašem projektu také vložit do souboru PDB sestavené projektem. To znamená, že pokud ladíte binární sestavené tímto projektem, ladicí program načte soubor Natvis z PDB i v případě, že nemáte otevřený projekt. Pokud nechcete, aby soubor .natvis, které mají být zahrnuty do pdb, klikněte pravým tlačítkem na soubor .natvis ve **Průzkumníka řešení**a **vlastnosti konfigurace** okno sady **vyloučeno ze sestavení**  k **Ano**.  

 Doporučujeme, abyste upravili pomocí Visual Studio změn provedené během ladění se projeví automaticky při ukládání souboru soubory Natvis. Také získat lepší prostředí pro úpravy z technologie IntelliSense.  

 Soubory Natvis, které jsou načteny z příponou .pdb platí pouze pro typy z modulu, na který odkazuje do souboru pdb. Například, pokud Module1.pdb definuje položku pro typ s názvem `Test`, tato položka jedině pro **Test** třídy v Module1.dll. Pokud se jiný modul také definuje třídu s názvem **Test**, Module1.pdb vaší položky natvis se nevztahuje k němu.  

##  <a name="BKMK_natvis_location"></a> Nasazení .natvis soubory  
 Pokud váš soubor .natvis platí pouze pro typy, které vytvoříte v projektu sady Visual Studio, nemusíte dělat nic; .natvis je součástí pdb. Můžete, ale přidat soubory .natvis uživatelský adresář nebo systémový adresář Pokud chcete použít pro více projektů.  

 Pořadí, ve které .natvis soubory jsou vyhodnocovány vypadá takto:  

1.  soubory .natvis vložený do pdb, který ladíte (pokud existuje soubor stejného názvu v načteném projektu)  

2.  soubory .natvis, které jsou součástí načtené projekty C++ nebo položku nejvyšší úrovně řešení. To zahrnuje všechny načtené projekty C++, včetně knihoven tříd, ale nezahrnuje projekty jazyků (například nelze načíst soubor .natvis z projektu v jazyce C#). Položky řešení spustitelné projekty, používejte k hostování soubory .natvis, které ještě nejsou k dispozici v .pdb, protože není k dispozici žádný projekt C++.  

3.  Adresář uživatelská natvis (**%USERPROFILE%\My 2015\Visualizers Documents\Visual Studio**  

4.  Adresář systémová Natvis (**%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers**). To je, kde se zkopírují soubory .natvis, které jsou nainstalované s Visual Studio. Do tohoto adresáře také můžete přidat další soubory, pokud máte oprávnění správce.  

## <a name="modifying-natvis-files-while-debugging"></a>Úprava .natvis soubory během ladění  
 Při ladění projektu, ve které je součástí můžete upravit soubor .natvis v integrovaném vývojovém prostředí. Otevřete soubor v integrovaném vývojovém prostředí (pomocí stejné instance sady Visual Studio, který právě ladíte s), upravte ho a uložte ho. Poté, co je soubor uložen, **Watch** a **lokální** windows by aktualizovat tak, aby odrážely změny. Pokud upravíte soubor .natvis mimo rozhraní IDE, změny se projeví automaticky. Aktualizace systému windows, můžete si vyzkoušet **.natvisreload** v příkaz **Watch** okna. To způsobí, že změny se projeví bez restartování relace ladění.  

 Můžete také přidávat a odstraňovat soubory .natvis do řešení pro ladění a sady Visual Studio přidá nebo odebere relevantní vizualizace.  

 Souboru .natvis nelze upravovat při probíhajícím ladění, pokud je součástí pdb.  

 Použití **.natvisreload** příkaz když souboru natvis provádíte upgrade na novější verzi (například pokud se změnami do správy zdrojového kódu a chcete se získaly nejnovější změny tohoto někdo jinak provedené v souboru). Doporučujeme, abyste upravili soubory natvis xml editoru sady Visual Studio.  

##  <a name="BKMK_Expressions_and_formatting"></a> Výrazy a formátování  
 Vizualizace Natvis používají výrazy jazyka C++ k určení položek dat k zobrazení. Kromě vylepšení a omezení výrazů jazyka C++ v ladicím programu, které jsou popsány v [kontextu – operátor (C++)](../debugger/context-operator-cpp.md), je třeba si uvědomit následující rozdíly:  

- Výrazy Natvis jsou vyhodnocovány v kontextu objektu, který je právě vizualizován, není aktuální rámec zásobníku. Například, pokud používáte `x` v rámci výrazu Natvis, to se vztahuje na pole s názvem `x` v objektu, který je právě vizualizován, nikoli na místní proměnnou s názvem `x` ve funkci právě probíhá. Lokální proměnné ve výrazech Natvis, nelze přistupovat, i když můžete přístup ke globálním proměnným.  

- Výrazy Natvis neumožňují vyhodnocování funkcí nebo vedlejší účinky. To znamená, že volání funkce a operátory přiřazení jsou ignorovány. Protože [vnitřní funkce ladicího programu](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) jsou bez vedlejších účinků, lze je volně volat z libovolného výrazu Natvis, i když ostatní volání funkce jsou zakázána.  

  K ovládání zobrazení výrazu v okně proměnné, můžete použít některý z formátů specifikátoru, které jsou popsány v [specifikátory formátu](../debugger/format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) část [specifikátory formátu v jazyce C++](../debugger/format-specifiers-in-cpp.md) tématu. Všimněte si, že specifikátory formátu jsou ignorovány, pokud je vstup virtualizace použit interně souborem Natvis, jako `Size` výrazu v rozšíření ArrayItems.  

## <a name="natvis-views"></a>Zobrazení Natvis  
 Zobrazení Natvis umožňují zobrazit libovolného typu více než jedním způsobem. Například můžete definovat zobrazení s názvem **jednoduché** , který umožňuje zjednodušené zobrazení typu. Například tady je vizualizaci `std::vector`:  

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

 `DisplayString` a `ArrayItems` elementy se používají ve výchozím zobrazením a jednoduchého zobrazení, zatímco `[size]` a `[capacity]` položky jsou vyloučeny z jednoduchého zobrazení. Můžete použít **, zobrazení** specifikátor formátu pro určit alternativní zobrazení. V **Watch** okno, zadejte jednoduché zobrazení jako **vec,view(simple)**:  

 ![Okno kukátka s jednoduchým](../debugger/media/watch-simpleview.png "Watch SimpleView")  

##  <a name="BKMK_Diagnosing_Natvis_errors"></a> Diagnostikování chyb Natvis  
 Diagnostika Natvis můžete použít k řešení potíží s syntaxe a chyby analýzy. Pokud ladicí program narazí na chyby v položce vizualizace, ignoruje chyby a buď zobrazí typ v syrové podobě nebo zvolí jinou vhodnou vizualizaci. Abyste pochopili, proč některá položka vizualizace je ignorována a zjistit, jaké jsou základní chyby, můžete zapnout Diagnostika Natvis **nástroje / Možnosti / ladění / výstupní okno / Diagnostika Natvis zprávy (pouze C++)** možnost. Chyby se zobrazují v **výstup** okna.  

##  <a name="BKMK_Syntax_reference"></a> Referenční příručka syntaxe Natvis  

###  <a name="BKMK_AutoVisualizer"></a> AutoVisualizer – element  
 `AutoVisualizer` Element je kořenový uzel souboru .natvis a obsahuje obor názvů `xmlns:` atribut.  

```xml  
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

###  <a name="BKMK_Type"></a> Type element  
 Základní typ vypadá takto:  

```xml  
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  

```  

 Určuje:  

1. Jaký typ této vizualizace má být použita pro ( `Type Name` atributu).  

2. Hodnota objektu tohoto typu by měl vypadat ( `DisplayString` element).  

3. Členy typu by měla vypadat podobně jako když je uživatel rozbalí v okně proměnné ( `Expand` uzlu).  

   **Šablony tříd** `Name` atribut `Type` element přijímá hvězdičku `*` jako zástupný znak, který lze použít pro názvy tříd šablon:  

```xml  
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  

```  

 V tomto příkladu se používá stejné vizualizace, zda je objekt `CAtlArray<int>` nebo `CAtlArray<float>`. Pokud existuje konkrétní položka vizualizace pro `CAtlArray<float>` , má přednost před obecnou položkou.  

 Všimněte si, že parametry šablony lze odkazovat v položce vizualizace pomocí maker $t1, $t2 a tak dále. Příklady těchto maker naleznete v tématu .natvis soubory dodané s aplikací Visual Studio.  

####  <a name="BKMK_Visualizer_type_matching"></a> Porovnávání typu vizualizéru  
 Pokud záznam vizualizace selže k ověření, použije se další dostupná vizualizace.  

#### <a name="inheritable-attribute"></a>Odvoditelný atribut  
 Můžete určit, jestli vizualizace platí pouze pro základní typ nebo základního typu a všechny odvozené typy s nepovinným `Inheritable` atribut. V následujícím příkladu platí vizualizace pouze `BaseClass` typu:  

```xml  
<Type Name="Namespace::BaseClass" Inheritable="true">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

 Výchozí hodnota `Inheritable` je `true`.  

#### <a name="priority-attribute"></a>Atribut priority  
 `Priority` Atribut určuje pořadí, ve kterém jsou použity alternativní definice, pokud se nepodaří analyzovat definici. Možné hodnoty `Priority` jsou: `Low`, `MediumLow`,`Medium`, `MediumHigh`, a `High`, a výchozí hodnota je `Medium`.  

 Atribut priority by měla sloužit pouze k rozlišení mezi priority ve stejném souboru .natvis, ne mezi různé soubory.  

 V následujícím příkladu jsme nejprve provede analýzu položku, která odpovídá 2015 STL, a pokud selže analyzovat, budeme používat alternativní vstupní verzi 2013 STL:  

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

####  <a name="BKMK_Versioning"></a> Version element  
 Použití `Version` můžete – element pro určení rozsahu vizualizace určitých modulů a jejich verzí, tak aby byly kolize názvů minimalizovány a různé vizualizace lze použít pro různé verze typů. Příklad:  

```xml  
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

 V tomto příkladu vizualizace je možné použít pouze `DirectUI::Border` typ nalezen v `Windows.UI.Xaml.dll` z verze 1.0 do 1.5. Všimněte si, že přidávání prvků verze obory položky vizualizace na konkrétní modul a verzi a snižuje zvyšuje ochranu před nechtěnými neshody, ale pokud je typ definován ve společný soubor hlaviček, který je používán různými moduly, vizualizace označená čísly verzí není použije, když typ není uvedený modul.  

#### <a name="optional-attribute"></a>Volitelný atribut  
 `Optional` Může atribut objevit na libovolný uzel. Pokud žádné dílčí výraz uvnitř volitelné uzlu se nepodaří analyzovat, tento uzel se ignoruje, ale zbývající typ prvku je stále platný. V následující typ `[State]` je povinný, ale `[Exception]` je volitelný.  To znamená, že pokud `MyNamespace::MyClass` obsahuje pole s názvem _`M_exceptionHolder`, budete pořád obě `[State]` uzlu a `[Exception]` uzlu, ale pokud `_M_exceptionHolder` chybí, zobrazí se pouze `[State]` uzlu.  

```xml  
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

###  <a name="BKMK_Condition_attribute"></a> Atribut podmínky  
 Volitelný `Condition` atribut je k dispozici pro mnoho prvků vizualizace a určuje, kdy se použije pravidlo vizualizace. Pokud má výraz uvnitř atributu podmínky se překládá na `false`, pak pravidlo vizualizace určené elementem nebude použito. Pokud je vyhodnocen jako true, nebo pokud neexistuje žádné `Condition` pak použijí pravidla vizualizace pro typ atributu. Můžete použít tento atribut pro `if-else` logiku v položkách vizualizace. Například následující vizualizace má dvě `DisplayString` prvky pro typ inteligentního ukazatele:  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 Když `_Myptr` člen je `null`, podmínka prvního `DisplayString` element se překládá na `true`, takže se zobrazí formulář. Když `_Myptr` člen není `null`, bude podmínka vyhodnocena jako `false`a druhá `DisplayString` element se zobrazuje.  

### <a name="includeview-and-excludeview-attributes"></a>Atributy IncludeView a ExcludeView  
 Tyto atributy určují prvky, které jsou zobrazeny, nebo se nezobrazí v zobrazení. Mějme například specifikaci Natvis `std::vector`:  

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

 Jednoduché zobrazení nezobrazuje [velikost] a [kapacity] položky v režimu jednoduchého zobrazení. Pokud jsme použili `IncludeView="simple"` místo `ExcludeView`, `[size]` a `[capacity]` položky by zobrazený v jednoduché zobrazení, nikoli ve výchozím zobrazení.  

 Můžete použít `IncludeView` a `ExcludeView` atributy u typů, stejně jako u jednotlivých členů.  

###  <a name="BKMK_DisplayString"></a> Element DisplayString  
 A `DisplayString` prvek určuje řetězec zobrazený jako hodnotu proměnné. Přijímá libovolné řetězce smíšené s výrazy. Vše uvnitř složených závorek je interpretováno jako výraz. Například `DisplayString` položky jako je tato:  

```xml  
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  

```  

 Prostředky této proměnné typu `CPoint` se zobrazí takto:  

 ![Pomocí elementu DisplayString](../debugger/media/dbg-natvis-cpoint-displaystring.png "DBG_NATVIS_CPoint_DisplayString")  

 V `DisplayString` výrazu, `x` a `y`, které jsou členy objektu `CPoint`, jsou uvnitř složených závorek a jejich hodnoty jsou vyhodnocovány. Výraz také ukazuje, jak může uniknout složenou závorku pomocí dvojitých složených závorek ( `{{` nebo `}}` ).  

> [!NOTE]
>  `DisplayString` Element je jediným prvkem, který přijímá libovolné řetězce a syntaxi složených závorek. Všechny ostatní prvky vizualizace přijímají pouze výrazy, které jsou vyhodnocovány pomocí ladicího programu.  

###  <a name="BKMK_StringView"></a> StringView  
 `StringView` Element definuje výraz, jehož hodnota bude zaslána zabudovanému vizualizátoru textu. Předpokládejme například, že máme následující vizualizaci `ATL::CStringT` typu:  

```xml  
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>  

```  

 `CStringT` Objektu bude vypadat takto:  

 ![Element CStringT DisplayString](../debugger/media/dbg-natvis-displaystring-cstringt.png "DBG_NATVIS_DisplayString_CStringT")  

 Zobrazí vizualizaci `CStringT` objekt v okně proměnné následujícím způsobem:  

 Přidání `StringView` element označí ladicímu programu, že tato hodnota může být zobrazena vizualizací textu:  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

 Všimněte si ikony lupy vedle hodnoty níže. Kliknete na ikonu se spustí vizualizátor textu, který zobrazí řetězec, který `m_pszData` odkazuje na.  

 ![CStringT dat se vizualizér StringView](../debugger/media/dbg-natvis-stringview-cstringt.png "DBG_NATVIS_StringView_CStringT")  

> [!NOTE]
>  Všimněte si, že výraz `{m_pszData,su}` obsahuje specifikátor formátu jazyka C++ `su` k zobrazení hodnoty jako řetězce Unicode. Zobrazit [specifikátory formátu v jazyce C++](../debugger/format-specifiers-in-cpp.md) Další informace.  

###  <a name="BKMK_Expand"></a> Rozbalte položku  
 `Expand` Uzel slouží k úpravě dceřiných vizualizovaných typů když je uživatel rozbalí v oknech proměnných. Přijímá seznam podřízených uzlů, které určují podřízené prvky.  

 `Expand` Uzel je volitelné.  

-   Pokud `Expand` uzel není zadané v položce vizualizace, se používají výchozí pravidla rozšíření sady Visual Studio.  

-   Pokud `Expand` uzel, který je zadán bez podřízených uzlů pod ním, typ nesmí být v oknech ladicího programu rozšiřitelný.  

####  <a name="BKMK_Item_expansion"></a> Rozšiřovací bod  
 `Item` Element je nejzákladnější a nejběžnější prvek, který se má použít v `Expand` uzlu. `Item` definuje jeden podřízený prvek. Předpokládejme například, že máte `CRect` třídy s `top`, `left`, `right`, a `bottom` jako polí a následující položku vizualizace:  

```xml  
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  

```  

 `CRect` Typ bude vypadat například takto:  

 ![Crect – pomocí rozšíření elementu položky](../debugger/media/dbg-natvis-expand-item-crect1.png "DBG_NATVIS_Expand_Item_CRect1")  

 Výrazy uvedené v `Width` a `Height` prvky jsou vyhodnoceny a zobrazena ve sloupci hodnota. `[Raw View]` Uzlu je automaticky vytvořen aplikací ladicího programu pokaždé, když se používá vlastní rozšíření. Je rozbalen na snímku obrazovky výše ukazují, jak se liší od jeho vizualizaci nezpracovaným zobrazením objektu. Výchozí rozšíření sady Visual Studio vytvoří podstrom pro základní třídu a jsou uvedeny všechny datové členy základní třídy jako podřízené objekty.  

> [!NOTE]
>  Pokud výraz prvku položky odkazuje na komplexní typ, `Item` samotný uzel je rozšiřitelné.  

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

 ![pomocí rozšíření ArrayItems std::Vector](../debugger/media/dbg-natvis-expand-arrayitems-stdvector.png "DBG_NATVIS_Expand_ArrayItems_StdVector")  

 Minimálně `ArrayItems` uzel musí mít:  

1. A `Size` výraz (který se musí vyhodnotit na celé číslo) pro ladicí program pro pochopení délky pole  

2. A `ValuePointer` výraz, který musí ukazovat na první prvek (který musí být ukazatelem typu prvku, který není `void*`).  

   Výchozí hodnota je dolní mez pole je 0. Hodnotu lze přepsat pomocí `LowerBound` – element (příklady lze nalézt v souborech .natvis dodaných s aplikací Visual Studio).  

   Teď můžete použít `[]` operátorem `ArrayItems` rozšíření, například `vector[i]`. [] – Operátor je možné s jakoukoli vizualizaci jednorozměrné pole, které používá `ArrayItems` nebo `IndexListItems`, i když tento operátor není povolena samotného typu (například `CATLArray`).  

   Vícerozměrná pole lze také zadat. Ladicí program potřebuje jen trochu více informací ke správnému zobrazení podřízených prvků v takovém případě:  

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

 `Direction` Určuje, zda je pole pořadí preferujícím řádek nebo sloupec hlavní. `Rank` Určuje pořadí v poli. `Size` Element přijímá implicitní `$i` parametr, který nahradí rozměrem indexu pro vyhledání délky pole v dané dimenzi. Například v předchozím příkladu výše výraz `_M_extent.M_base[0]` by měl uvádět délku 0 dimenze `_M_extent._M_base[1]` 1. a tak dále.  

 Zde uvádíme, jak multidimenzionálním `Concurrency::array` vyhledá objekt v ladicím programu:  

 ![Dvě jednorozměrná pole s rozšíření ArrayItems](../debugger/media/dbg-natvis-expand-arrayitems-2d.png "DBG_NATVIS_Expand_ArrayItems_2D")  

####  <a name="BKMK_IndexListItems_expansion"></a> Rozšíření IndexListItems  
 Můžete použít `ArrayItems` rozšíření, pouze pokud jsou prvky pole rozloženy souvisle v paměti. Ladicí program získá další prvek jednoduchým zvýšením jeho ukazatele na aktuální prvek. Na podporu případů, kdy potřebujete pracovat s indexem na uzel hodnoty `IndexListItems` uzly můžete použít. Zde je vizualizace pomocí `IndexListItems` uzlu:  

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

 Teď můžete použít `[]` operátorem `IndexListItems` rozšíření, například `vector[i]`. `[]` Operátor lze použít s jakoukoli vizualizaci jednorozměrné pole, které používá `ArrayItems` nebo `IndexListItems`, i když tento operátor není povolena samotného typu (například `CATLArray`).  

 Jediným rozdílem mezi `ArrayItems` a `IndexListItems` je, že `ValueNode` očekává úplný výraz, který i<sup>th</sup> element s implicitním `$i` parametru.  

####  <a name="BKMK_LinkedListItems_expansion"></a> Rozšíření LinkedListItems  
 Pokud vizualizovaný typ představuje propojený seznam, ladicí program může zobrazit jeho podřízené položky pomocí `LinkedListItems` uzlu. Zde je vizualizace pro `CAtlList` zadejte pomocí této funkce:  

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

-   `NextPointer` a `ValueNode` výrazy jsou vyhodnocovány v kontextu uzlu prvku propojeného seznamu a nikoli typu nadřazeného seznamu. V příkladu výše `CAtlList` má `CNode` třídy (součástí `atlcoll.h`), který představuje uzel propojeného seznamu. `m_pNext` a `m_element` jsou pole této `CNode` třídy a ne `CAtlList` třídy.  

-   `ValueNode` Může být ponechán prázdný nebo obsahovat `this` odkazovat na samotný uzel propojeného seznamu.  

#### <a name="customlistitems-expansion"></a>CustomListItems rozšíření  
 `CustomListItems` Rozšíření umožňuje psát vlastní logiku procházení datové struktury, jako například zatřiďovací tabulku. Měli byste použít `CustomListItems` k vizualizaci dat lze vyjádřit pomocí výrazů C++ struktury, které všechno, co potřebujete k vyhodnocení, ale nehodí poměrně tvaru pro `ArrayItems`, `TreeItems`, nebo `LinkedListItems.`  

 Vizualizér pro catlmap – je vynikajícím příkladem where `CustomListItems` je vhodné.  

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

####  <a name="BKMK_TreeItems_expansion"></a> Rozšíření TreeItems  
 Pokud vizualizovaný typ představuje strom, ladicí program může strom procházet a zobrazit jeho podřízené položky pomocí `TreeItems` uzlu. Zde je vizualizace pro `std::map` zadejte pomocí této funkce:  

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

 Syntaxe je velmi podobný `LinkedListItems` uzlu. `LeftPointer`, `RightPointer`, a `ValueNode` jsou vyhodnocovány v kontextu třídy uzlu stromu a `ValueNode` může být ponechán prázdný nebo obsahovat `this` odkazovat na samotný uzel stromu.  

####  <a name="BKMK_ExpandedItem_expansion"></a> Rozšíření ExpandedItem  
 `ExpandedItem` Elementu lze použít ke generování agregovaných podřízených zobrazení zobrazením vlastností základních tříd nebo datových členů, jako kdyby byly podřízené prvky typu visualized. Zadaný výraz je vyhodnocen a podřízené uzly výsledku jsou připojeny k seznamu podřízených vizualizovaného typu. Předpokládejme například, že máme typ inteligentního ukazatele `auto_ptr<vector<int>>` což obvykle se zobrazí jako:  

 ![Automatické&#95;ptr&#60;vektoru&#60;int&#62; &#62; výchozí rozšíření](../debugger/media/dbg-natvis-expand-expandeditem-default.png "DBG_NATVIS_Expand_ExpandedItem_Default")  

 Chcete-li zobrazit hodnoty vektoru, máte dvě úrovně v okně proměnných prostřednictvím člena _Myptr. Tak, že přidáte `ExpandedItem` element, můžete eliminovat `_Myptr` proměnné z hierarchie a přímo zobrazit prvky vektoru::  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 ![Automatické&#95;ptr&#60;vektoru&#60;int&#62; &#62; rozšíření ExpandedItem](../debugger/media/dbg-natvis-expand-expandeditem-visualized.png "DBG_NATVIS_Expand_ExpandedItem_Visualized")  

 Následující příklad ukazuje, jak se spojují vlastnosti ze základní třídy v odvozené třídě. Předpokládejme, `CPanel` třída odvozena z `CFrameworkElement`. Namísto opakování vlastností, které pocházejí ze základní `CFrameworkElement` třídy, `ExpandedItem` uzel umožňuje tyto vlastnosti, které se mají připojit k seznamu podřízených třídy `CPanel` třídy. **Nd** formátovací řetězec, který vypne odpovídající vizualizace pro odvozenou třídu, je nutný zde. V opačném případě výraz `*(CFrameworkElement*)this` způsobí, že `CPanel` vizualizaci. tím bude znovu použita, protože typ odpovídajících pravidel vizualizace výchozí považuje za nejvhodnější. Použití **nd** specifikátor formátu dává pokyn ladicímu programu používat vizualizaci základní třídy nebo rozšíření výchozí základní třídy, pokud výchozí třída neobsahuje vizualizaci.  

```xml  
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  

```  

####  <a name="BKMK_Synthetic_Item_expansion"></a> Syntetické rozšíření položky  
 Kde `ExpandedItem` element obsahuje plošší zobrazení dat odstraněním hierarchií, `Synthetic` uzel provádí opak. Umožňuje vytvořit umělý podřízený prvek (tedy podřízený element, který není výsledkem výrazu). Tento podřízený element může obsahovat vlastní podřízené prvky. V následujícím příkladu vizualizace pro `Concurrency::array` typ používá `Synthetic` uzel k zobrazení diagnostické zprávy uživateli:  

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

 ![Concurrency::Array s Sythentic element expansio](../debugger/media/dbg-natvis-expand-synthetic.png "DBG_NATVIS_Expand_Synthetic")  

###  <a name="BKMK_HResult"></a> Hodnota HResult  
 `HResult` Element umožňuje přizpůsobit informace, které se zobrazí pro HRESULT v oknech ladicího programu. `HRValue` Element musí obsahovat 32bitovou hodnotu HRESULT, kterou chcete upravit. `HRDescription` Prvek obsahuje informace, které se zobrazí v ladicím programu.  

```  

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

###  <a name="BKMK_UIVisualizer"></a> UIVisualizer  
 A `UIVisualizer` prvek registruje modul plug-in grafického vizualizéru s ladicím programem. Modul plug-in grafického vizualizéru vytvoří dialogové okno nebo jiné rozhraní pro zobrazení proměnné nebo objektu způsobem, který je vhodný k jeho datovému typu. Modul plug-in vizualizéru musí být vytvořen jako [VSPackage](../extensibility/internals/vspackages.md) a je třeba zpřístupnit služby, které mohou být spotřebovány ladicím programem. Soubor .natvis obsahuje registrační informace pro modul plug-in, například jeho název, identifikátor GUID, vystavené služby a také typy, které lze vizualizovat.  

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

 A `UIVisualizer` je identifikován `ServiceId`  -  `Id` atribut pár. `ServiceId` je identifikátor GUID služby, vystavený balíčkem vizualizéru `Id` je jedinečný identifikátor, který slouží k odlišení vizualizérů, pokud služba poskytuje více než jeden vizualizér. V předchozím příkladu poskytuje jedna služba vizualizéru dva vizualizéry.  

 `MenuName` Atribut je, co uživatelé uvidí jako název vizualizéru když otevřou rozevírací nabídku vedle ikony lupy v oknech proměnných ladicího programu, například:  

 ![Místní nabídky UIVisualizer](../debugger/media/dbg-natvis-vectorvisualizer.png "DBG_NATVIS_VectorVisualizer")  

 Každý typ definovaný v souboru .natvis musí explicitně uvádět vizualizéry uživatelského rozhraní, které je mohou zobrazit. Ladicí program odpovídá odkazům vizualizéru v položkách typu odpovídajících typům s registrovanými vizualizéry. Například následující typ položky pro `std::vector` reference na UIVisualizer v našem příkladu výše.  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 Vidíte příklad UIVisualizer v rozšíření Image Watch použít k zobrazení rastrové obrázky v paměti: [ImageWatch](https://visualstudiogallery.msdn.microsoft.com/e682d542-7ef3-402c-b857-bbfba714f78d)  

### <a name="customvisualizer-element"></a>CustomVisualizer – element  
 `CustomVisualizer` je bod rozšíření, která určuje příponu VSIX, který píšete pro řízení vizualizaci v kódu, který běží v sadě Visual Studio. Další informace o psaní rozšíření VSIX, naleznete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Zápis vlastního vizualizéru je mnohem více práce než psaní definice natvis XML, ale můžete libovolně z omezení, o jaké natvis podporuje nebo nepodporuje. Vlastní vizualizátory mají přístup k úplné sadě rozšiřitelností ladicího programu rozhraní API, která slouží k dotazování a upravit laděném procesu nebo komunikaci s jinými částmi sady Visual Studio.  

 Můžete použít `Condition`, `IncludeView`, a `ExcludeView` atributy u elementů CustomVisualizer.



