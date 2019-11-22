---
title: Vytváření vlastních zobrazení nativních objektů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: a510c522723cf991c7a3fff21542a069a3de000a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299492"
---
# <a name="create-custom-views-of-native-objects"></a>Vytváření vlastních zobrazení nativních objektů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozhraní Visual Studio Natvis umožňuje přizpůsobit způsob, jakým Visual Studio zobrazuje nativní typy v oknech proměnných ladicího programu (například okna **kukátko**, **místní**hodnoty a **tipy pro data** ).  

 Natvis nahrazuje soubor **autoexp. dat** , který byl použit v dřívějších verzích sady Visual Studio, a nabízí syntaxi kódu XML, lepší diagnostiku, správu verzí a podporu více souborů.  

> [!NOTE]
> Architekturu Natvis nelze použít pro vizualizace v těchto případech:  
> 
> - Ladíte desktopový C++ projekt Windows s typem ladicího programu nastaveným na **Mixed**.  
>   - Provádíte ladění smíšeného režimu v desktopové aplikaci pro Windows ve spravovaném režimu kompatibility (**Nástroje/možnosti/ladění/obecné/použití spravovaného režimu kompatibility**).  
>   - Ladíte v desktopové aplikaci pro Windows v nativním režimu kompatibility (**Nástroje/možnosti/ladění/obecné/použití nativního režimu kompatibility**).  

## <a name="BKMK_Why_create_visualizations_"></a>Proč vytvářet vizualizace Natvis?  
 Pomocí architektury Natvis můžete vytvořit pravidla vizualizace pro typy, které vytvoříte, aby je vývojáři mohli snadno zobrazit během ladění.  

 Například obrázek níže ukazuje proměnnou typu [Windows:: UI:: XAML:: Controls:: TextBox](https://go.microsoft.com/fwlink/?LinkId=258422) , který se zobrazí v ladicím programu bez použití vlastních vizualizací.  

 ![Výchozí vizualizace textového pole](../debugger/media/dbg-natvis-textbox-default.png "DBG_NATVIS_TextBox_Default")  

 Zvýrazněný řádek zobrazuje vlastnost `Text` třídy `TextBox`. Složitá hierarchie tříd ztěžuje nalezení této hodnoty; ladicí program navíc neví, jak interpretovat typ vlastního řetězce používaného objektem, takže nemůžete vidět řetězec umístěný v textovém poli.  

 Stejný `TextBox` při použití vlastních pravidel vizualizace vypadá mnohem jednodušší n okno proměnné. Důležité členy třídy lze zobrazit společně a ladicí program zobrazuje základní řetězcovou hodnotu vlastního typu řetězce.  

 ![Data textového pole používající Vizualizér](../debugger/media/dbg-natvis-textbox-visualizer.png "DBG_NATVIS_TextBox_Visualizer")  

## <a name="BKMK_Using_Natvis_files"></a>Použití souborů Natvis  
 soubory. Natvis jsou soubory XML s příponou. Natvis. Schéma je definováno v **%VSINSTALLDIR%\Xml\Schemas\natvis.xsd**.  

 Základní struktura souboru. natvis je jeden nebo více `Type` prvků, kde každý `Type` prvek představuje položku vizualizace pro typ, jehož plně kvalifikovaný název je zadán v atributu `Name`.  

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

 Visual Studio poskytuje některé soubory. Natvis ve složce **%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers** . Tyto soubory obsahují pravidla vizualizace pro mnoho běžných typů a můžou sloužit jako příklady při psaní vizualizací pro nové typy.  

## <a name="adding-natvis-files-to-your-projects"></a>Přidávání souborů. Natvis do projektů  
 Soubory. Natvis můžete přidat do libovolného C++ projektu.  

 Chcete-li přidat nový soubor. Natvis s otevřeným C++ projektem, vyberte uzel projektu v **Průzkumník řešení**a klikněte na tlačítko **Přidat/nový položku/ C++ vizuální/soubor vizualizace/ladicí program (. Natvis)** . Ladicí program načte soubory Natvis z C++ projektů automaticky. Ve výchozím nastavení jsou soubory Natvis v projektu také vloženy do souboru PDB sestaveného projektem. To znamená, že pokud provedete ladění binárního sestavení vytvořeného tímto projektem, ladicí program načte soubor Natvis z. pdb, a to i v případě, že projekt není otevřen. Pokud nechcete, aby se soubor. Natvis zahrnul do souboru. pdb, klikněte pravým tlačítkem na soubor. Natvis v **Průzkumník řešení**a v okně **Vlastnosti konfigurace** **vyloučené z možnosti sestavení** na **Ano**.  

 Doporučuje se upravovat soubory Natvis pomocí sady Visual Studio, přičemž všechny změny, které provedete při automatickém ladění, se projeví automaticky při uložení souboru. Z IntelliSense taky získáte vylepšené možnosti úprav.  

 Soubory Natvis, které jsou načteny ze souboru. pdb, se vztahují pouze na typy v modulu, na který odkazuje soubor PDB. Například pokud Module1. pdb definuje položku pro typ s názvem `Test`, tato položka se aplikuje pouze na **testovací** třídu v souboru Module1. dll. Pokud jiný modul také definuje třídu s názvem **test**, položka Natvis pro Module1. pdb se na ni nevztahuje.  

## <a name="BKMK_natvis_location"></a>Nasazování souborů. Natvis  
 Pokud se soubor. Natvis vztahuje pouze na typy, které vytváříte v projektu sady Visual Studio, nemusíte dělat nic. soubor. natvis je součástí souboru. pdb. Můžete však přidat soubory. Natvis do adresáře uživatele nebo do systémového adresáře, pokud chcete, aby byly použity pro více projektů.  

 Pořadí, ve kterém jsou soubory. Natvis vyhodnocovány, je následující:  

1. soubory. Natvis vložené do souboru. pdb, který ladíte (Pokud v načteném projektu neexistuje soubor se stejným názvem)  

2. soubory. Natvis, které jsou součástí načtených C++ projektů nebo položky řešení na nejvyšší úrovni. To zahrnuje všechny načtené C++ projekty, včetně knihoven tříd, ale neobsahují projekty jiných jazyků (například nelze načíst soubor. Natvis z C# projektu). U spustitelných projektů byste měli použít položky řešení k hostování všech souborů. Natvis, které ještě nejsou přítomny v souboru. pdb, protože není k dispozici žádný C++ projekt.  

3. Adresář Natvis konkrétního uživatele ( **%USERPROFILE%\My Documents\Visual Studio 2015 \ vizualizujes**  

4. Adresář Natvis pro systém v rámci systému ( **%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers**). Tady se zkopírují soubory. Natvis, které se instalují se sadou Visual Studio. Do tohoto adresáře můžete přidat další soubory i v případě, že máte oprávnění správce.  

## <a name="modifying-natvis-files-while-debugging"></a>Úprava souborů. Natvis během ladění  
 Během ladění projektu, ve kterém je zahrnutý, můžete upravit soubor. Natvis v integrovaném vývojovém prostředí. Otevřete soubor v integrovaném vývojovém prostředí (pomocí stejné instance sady Visual Studio, kterou ladíte pomocí), upravte ho a uložte. Jakmile se soubor uloží, okna **kukátka** a **místní** hodnoty by se měla aktualizovat tak, aby odrážela změnu. Pokud upravíte soubor. Natvis mimo rozhraní IDE, změny se neprojeví automaticky. Chcete-li aktualizovat okna, můžete vyhodnotit příkaz **. natvisreload** v okně **kukátko** . To způsobí, že se změny projeví bez restartování ladicí relace.  

 Můžete také přidat nebo odstranit soubory. Natvis do řešení, které ladíte, a Visual Studio bude přidávat nebo odebírat příslušné vizualizace.  

 Soubor. Natvis nelze upravovat, pokud probíhá ladění, pokud je vložen do souboru. pdb.  

 Použijte příkaz **. natvisreload** při upgradu souboru Natvis na novější verzi (například pokud se vrátí do správy zdrojových kódů a chcete si vybrat poslední změny, které někdo jiný v souboru udělal). Doporučuje se upravovat soubory Natvis pomocí editoru XML sady Visual Studio.  

## <a name="BKMK_Expressions_and_formatting"></a>Výrazy a formátování  
 Vizualizace Natvis používají C++ výrazy k určení datových položek, které se mají zobrazit. Kromě vylepšení a omezení C++ výrazů v ladicím programu, které jsou popsány v [kontextu operátoruC++()](../debugger/context-operator-cpp.md), byste měli být vědomi následujících rozdílů:  

- Výrazy Natvis jsou vyhodnocovány v kontextu objektu, který je vizuálů, nikoli aktuálního rámce zásobníku. Například pokud použijete `x` ve výrazu Natvis, odkazuje na pole s názvem `x` v objektu, který je vizuálů, nikoli na místní proměnnou s názvem `x` v aktuálně vykonávané funkci. Nemůžete získat přístup k místním proměnným ve výrazech Natvis, i když máte přístup k globálním proměnným.  

- Výrazy Natvis nepovolují vyhodnocení funkce ani vedlejší účinky. To znamená, že volání funkce a operátory přiřazení jsou ignorovány. Vzhledem k tomu, že [vnitřní funkce ladicího programu](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) mají volné vedlejší účinky, mohou být volně volány z jakéhokoli výrazu Natvis, i když nejsou povolena jiná volání funkcí.  

  Chcete-li určit, jak se má výraz zobrazit v okně proměnné, můžete použít libovolný specifikátor formátu, který je popsán v oddílu [specifikátory formátu](../debugger/format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) [specifikátorů formátu v C++ ](../debugger/format-specifiers-in-cpp.md) tématu. Všimněte si, že specifikátory formátu jsou ignorovány, pokud je položka virtualizace používána interně pomocí Natvis, jako je například výraz `Size` v rozšíření ArrayItems.  

## <a name="natvis-views"></a>Zobrazení Natvis  
 Zobrazení Natvis umožňují zobrazit libovolný typ více než jedním způsobem. Můžete například definovat zobrazení s názvem **jednoduchý** , které poskytuje zjednodušený pohled na typ. Například tady je vizualizace `std::vector`:  

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

 `DisplayString` a prvky `ArrayItems` jsou používány ve výchozím zobrazení a v jednoduchém zobrazení, zatímco `[size]` a `[capacity]` položky jsou vyloučeny z jednoduchého zobrazení. Pomocí specifikátoru formátu **zobrazení** můžete zadat alternativní zobrazení. V okně **kukátka** zadáte jednoduché zobrazení jako **vec, zobrazení (jednoduché)** :  

 ![okno Kukátko s jednoduchým zobrazením](../debugger/media/watch-simpleview.png "Kukátko – SimpleView")  

## <a name="BKMK_Diagnosing_Natvis_errors"></a>Diagnostikování chyb Natvis  
 K řešení chyb syntaxe a analýzy můžete použít diagnostiku Natvis. Pokud ladicí program zjistí chyby v položce vizualizace, ignoruje chyby a buď zobrazí typ v jeho nezpracované podobě, nebo vybere jinou vhodnou vizualizaci. Chcete-li zjistit, proč je určitá položka vizualizace ignorována a zjistit, jaké jsou příslušné chyby, můžete zapnout možnost nástroje pro diagnostiku Natvis **/možnosti/ladění/okno výstup/C++ Natvis diagnostické zprávy (pouze)** . Chyby se zobrazí v okně **výstup** .  

## <a name="BKMK_Syntax_reference"></a>Odkaz syntaxe Natvis  

### <a name="BKMK_AutoVisualizer"></a>Element autovizualizuje  
 Element `AutoVisualizer` je kořenovým uzlem souboru. Natvis a obsahuje atribut namespace `xmlns:`.  

```xml  
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

### <a name="BKMK_Type"></a>Element Type  
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

1. Jaký typ této vizualizace má být použit pro (atribut `Type Name`).  

2. Jak hodnota objektu tohoto typu by měla vypadat (`DisplayString` element).  

3. Jak by měly členové typu vypadat, když ho uživatel rozbalí v okně proměnné (`Expand` uzel).  

   **Třídy šablon** Atribut `Name` elementu `Type` přijímá hvězdičku `*` jako zástupný znak, který lze použít pro názvy tříd šablon:  

```xml  
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  

```  

 V tomto příkladu se použije stejná vizualizace bez ohledu na to, jestli je objekt `CAtlArray<int>` nebo `CAtlArray<float>`. Pokud pro `CAtlArray<float>` existuje určitá položka vizualizace, má přednost před obecným.  

 Všimněte si, že parametry šablony lze v položce vizualizace odkazovat pomocí maker $T 1, $T 2 a tak dále. Příklady těchto maker naleznete v souborech. Natvis dodaných se sadou Visual Studio.  

#### <a name="BKMK_Visualizer_type_matching"></a>Shoda typu Vizualizátor  
 Pokud se položka vizualizace nedokáže ověřit, použije se další dostupná vizualizace.  

#### <a name="inheritable-attribute"></a>Dědičný atribut  
 Můžete určit, zda vizualizace platí pouze pro základní typ nebo na základní typ a všechny odvozené typy s volitelným atributem `Inheritable`. V následujících případech se vizualizace používá jenom pro `BaseClass` typ:  

```xml  
<Type Name="Namespace::BaseClass" Inheritable="true">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

 Výchozí hodnota `Inheritable` je `true`.  

#### <a name="priority-attribute"></a>Priorita – atribut  
 Atribut `Priority` určuje pořadí, ve kterém se použijí alternativní definice v případě, že se definice nedokáže analyzovat. Možné hodnoty `Priority` jsou: `Low`, `MediumLow`,`Medium`, `MediumHigh`a `High`a výchozí hodnota je `Medium`.  

 Atribut priority by měl být použit pouze k rozlišení mezi prioritami v rámci stejného souboru. Natvis, nikoli mezi různými soubory.  

 V následujícím příkladu budeme nejprve analyzovat položku, která odpovídá 2015 STL, a pokud se to nepodaří analyzovat, použijeme alternativní položku pro verzi standardu STL pro 2013:  

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

#### <a name="BKMK_Versioning"></a>Element Version  
 Pomocí elementu `Version` můžete oborovat vizualizace na konkrétní moduly a jejich verze, aby kolize názvů mohly být minimalizovány, a různé vizualizace lze použít pro různé verze těchto typů. Příklad:  

```xml  
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

 V tomto příkladu je vizualizace platná jenom pro `DirectUI::Border` typ, který najdete v `Windows.UI.Xaml.dll` od verze 1,0 do 1,5. Všimněte si, že přidání elementů verze do rozsahu položky vizualizace na určitý modul a verzi a zkracuje neúmyslné neshody, ale pokud je typ definován v běžném hlavičkovém souboru, který je používán různými moduly, vizualizace s verzí se nepoužije, když typ není v zadaném modulu.  

#### <a name="optional-attribute"></a>Volitelný atribut  
 Atribut `Optional` se může objevit na jakémkoli uzlu. Pokud se nepodaří analyzovat jakýkoliv dílčí výraz uvnitř volitelného uzlu, bude tento uzel ignorován, ale zbytek elementu Type je stále platný. V následujícím typu `[State]` není nepovinný, ale `[Exception]` je volitelná.  To znamená, že pokud `MyNamespace::MyClass` obsahuje pole s názvem _`M_exceptionHolder`, bude stále `[State]` i uzel `[Exception]`, ale pokud chybí `_M_exceptionHolder`, zobrazí se pouze uzel `[State]`.  

```xml  
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

### <a name="BKMK_Condition_attribute"></a>Atribut Condition  
 Volitelný atribut `Condition` je k dispozici pro mnoho elementů vizualizace a určuje, kdy by mělo být použito pravidlo vizualizace. Pokud se výraz uvnitř atributu Condition přeloží na `false`, pravidlo vizualizace určené elementem se nepoužije. Pokud se vyhodnotí jako true, nebo pokud neexistuje žádný `Condition` atribut, použije se pro tento typ pravidlo vizualizace. Tento atribut lze použít pro `if-else` logiky v položkách vizualizace. Například následující vizualizace obsahuje dva prvky `DisplayString` pro typ inteligentního ukazatele:  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 Když je člen `_Myptr` `null`, podmínka prvního `DisplayString` elementu se přeloží na `true`, takže se zobrazí formulář. Pokud není člen `_Myptr` `null`, je podmínka vyhodnocena jako `false`a je zobrazen druhý element `DisplayString`.  

### <a name="includeview-and-excludeview-attributes"></a>Atributy IncludeView a ExcludeView  
 Tyto atributy určují prvky, které mají být zobrazeny nebo zobrazeny v různých zobrazeních. Například s ohledem na specifikaci Natvis `std::vector`:  

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

 Jednoduché zobrazení nezobrazuje položky [size] a [Capacity] v jednoduchém zobrazení. Pokud jsme místo `ExcludeView`použili `IncludeView="simple"`, `[size]` a `[capacity]` položky se zobrazí v jednoduchém zobrazení, nikoli ve výchozím zobrazení.  

 Můžete použít atributy `IncludeView` a `ExcludeView` u typů i u jednotlivých členů.  

### <a name="BKMK_DisplayString"></a>Řetězec  
 Element `DisplayString` určuje řetězec, který se má zobrazit jako hodnota proměnné. Přijímá libovolné řetězce smíšené s výrazy. Vše uvnitř složených závorek je interpretováno jako výraz. Například záznam `DisplayString` například:  

```xml  
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  

```  

 Znamená, že proměnné typu `CPoint` se zobrazí takto:  

 ![Použití elementu DisplayString](../debugger/media/dbg-natvis-cpoint-displaystring.png "DBG_NATVIS_CPoint_DisplayString")  

 Ve výrazu `DisplayString` `x` a `y`, které jsou členy `CPoint`, jsou uvnitř složených závorek a jejich hodnoty jsou vyhodnocovány. Výraz také ukazuje, jak lze vytvořit složenou závorku pomocí dvojitých složených závorek (`{{` nebo `}}`).  

> [!NOTE]
> Element `DisplayString` je jediným prvkem, který přijímá libovolné řetězce a syntaxi složených závorek. Všechny ostatní prvky vizualizace přijímají pouze výrazy, které jsou vyhodnocovány pomocí ladicího programu.  

### <a name="BKMK_StringView"></a>StringView  
 Element `StringView` definuje výraz, jehož hodnota se bude odesílat do předdefinovaného Vizualizér textu. Předpokládejme například, že máme pro `ATL::CStringT` typ následující vizualizaci:  

```xml  
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>  

```  

 Objekt `CStringT` vypadá takto:  

 ![CStringt – element DisplayString](../debugger/media/dbg-natvis-displaystring-cstringt.png "DBG_NATVIS_DisplayString_CStringT")  

 Vizualizace zobrazuje objekt `CStringT` v okně proměnné takto:  

 Přidáním prvku `StringView` určíte ladicímu programu, že tato hodnota může být zobrazená vizualizací textu:  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

 Všimněte si ikony lupy zobrazené vedle níže uvedené hodnoty. Zvolením ikony se spustí Vizualizér textu, ve kterém se zobrazí řetězec, na který `m_pszData` odkazuje.  

 ![Data CStringt pomocí Vizualizér StringView](../debugger/media/dbg-natvis-stringview-cstringt.png "DBG_NATVIS_StringView_CStringT")  

> [!NOTE]
> Všimněte si, že výraz `{m_pszData,su}` obsahuje C++ specifikátor formátu `su` k zobrazení hodnoty jako řetězce Unicode. Další informace naleznete [v tématu C++ specifikátory formátu v](../debugger/format-specifiers-in-cpp.md) tématu.  

### <a name="BKMK_Expand"></a>Rozbalovací  
 Uzel `Expand` slouží k přizpůsobení podřízených objektů typu, když je uživatel rozbalí v oknech proměnných. Přijímá seznam podřízených uzlů, které definují podřízené prvky.  

 Uzel `Expand` je nepovinný.  

- Pokud v položce vizualizace není zadán uzel `Expand`, jsou použita výchozí pravidla rozbalování sady Visual Studio.  

- Pokud je uzel `Expand` zadaný bez podřízených uzlů pod ním, typ nebude možné rozšířit v oknech ladicího programu.  

#### <a name="BKMK_Item_expansion"></a>Rozšíření položky  
 `Item` element je nejzákladnější a nejběžnější prvek, který má být použit v uzlu `Expand`. `Item` definuje jeden podřízený element. Předpokládejme například, že máte třídu `CRect` s `top`, `left`, `right`a `bottom` jako své pole a následující položku vizualizace:  

```xml  
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  

```  

 Typ `CRect` bude vypadat takto:  

 ![CRect s rozšířením elementu Item](../debugger/media/dbg-natvis-expand-item-crect1.png "DBG_NATVIS_Expand_Item_CRect1")  

 Výrazy zadané v `Width` a `Height` prvky jsou vyhodnoceny a zobrazeny ve sloupci Value (hodnota). `[Raw View]` uzel je automaticky vytvořen pomocí ladicího programu při každém použití vlastního rozšíření. Je rozbalen na snímku obrazovky výše a ukazuje, jak se nezpracovaná zobrazení objektu liší od jeho vizualizace. Výchozí rozšíření sady Visual Studio vytvoří podstrom pro základní třídu a seznam všech datových členů základní třídy jako podřízených objektů.  

> [!NOTE]
> Pokud se výraz elementu Item odkazuje na komplexní typ, může být rozšiřitelný uzel `Item` sám.  

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

 ![std:: Vector s použitím rozšíření ArrayItems](../debugger/media/dbg-natvis-expand-arrayitems-stdvector.png "DBG_NATVIS_Expand_ArrayItems_StdVector")  

 Uzel `ArrayItems` musí mít minimálně:  

1. Výraz `Size` (který se musí vyhodnotit na celé číslo) pro ladicí program pro pochopení délky pole  

2. Výraz `ValuePointer`, který by měl ukazovat na první prvek (který musí být ukazatelem typu elementu, který není `void*`).  

   Výchozí hodnota dolní meze pole je 0. Hodnotu lze přepsat pomocí elementu `LowerBound` (příklady lze nalézt v souborech. Natvis dodaných se sadou Visual Studio).  

   Nyní můžete použít operátor `[]` s rozšířením `ArrayItems`, například `vector[i]`. Operátor [] lze použít s libovolnou vizualizací jednorozměrného pole, které používá `ArrayItems` nebo `IndexListItems`, a to i v případě, že samotný typ nepovoluje Tento operátor (například `CATLArray`).  

   Lze také zadat multidimenzionální pole. Ladicí program potřebuje pouze trochu více informací pro správné zobrazení podřízených elementů v tomto případě:  

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

 `Direction` určuje, zda je pole hlavním řádkem nebo pořadím hlavního sloupce. `Rank` určuje rozměr pole. Element `Size` přijímá implicitní parametr `$i`, který nahradí index dimenze, aby bylo možné najít délku pole v dané dimenzi. Například v předchozím příkladu, nad výraz `_M_extent.M_base[0]` by měl poskytnout délku dimenze 0th, `_M_extent._M_base[1]` 1. a tak dále.  

 Tady je postup, jak v ladicím programu vypadá dva dimenzionální `Concurrency::array` objekt:  

 ![Dvojrozměrné pole s rozšířením ArrayItems](../debugger/media/dbg-natvis-expand-arrayitems-2d.png "DBG_NATVIS_Expand_ArrayItems_2D")  

#### <a name="BKMK_IndexListItems_expansion"></a>Rozšíření IndexListItems  
 Rozšíření `ArrayItems` lze použít pouze v případě, že jsou prvky pole rozloženy souvisle v paměti. Ladicí program se dostane k dalšímu prvku jednoduchým zvýšením jeho ukazatele na aktuální prvek. Aby bylo možné podporovat případy, kdy potřebujete manipulovat s indexem na uzel hodnoty, lze použít uzly `IndexListItems`. Tady je vizualizace pomocí `IndexListItems`ho uzlu:  

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

 Nyní můžete použít operátor `[]` s rozšířením `IndexListItems`, například `vector[i]`. Operátor `[]` lze použít s libovolnou vizualizací jednorozměrného pole, které používá `ArrayItems` nebo `IndexListItems`, a to i v případě, že samotný typ Tento operátor nepovoluje (například `CATLArray`).  

 Jediným rozdílem mezi `ArrayItems` a `IndexListItems` je, že `ValueNode` očekává úplný výraz pro i<sup>th</sup> elementu s implicitním `$i`m parametrem.  

#### <a name="BKMK_LinkedListItems_expansion"></a>Rozšíření LinkedListItems  
 Pokud vizuální typ představuje propojený seznam, ladicí program může zobrazit jeho podřízené položky pomocí uzlu `LinkedListItems`. Toto je vizualizace pro `CAtlList` typ pomocí této funkce:  

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

- Výrazy `NextPointer` a `ValueNode` jsou vyhodnocovány v kontextu prvku propojeného seznamu uzlu a nikoli typu nadřazeného seznamu. V příkladu výše `CAtlList` má `CNode` třídu (nalezeno v `atlcoll.h`), která představuje uzel propojeného seznamu. `m_pNext` a `m_element` jsou pole této třídy `CNode` a nikoli `CAtlList` třídy.  

- `ValueNode` může být ponechán prázdný nebo obsahovat `this`, aby odkazoval na samotný uzel propojeného seznamu.  

#### <a name="customlistitems-expansion"></a>Rozšíření CustomListItems  
 Rozšíření `CustomListItems` umožňuje napsat vlastní logiku pro procházení datové struktury, jako je například zatřiďovací tabulka. Měli byste použít `CustomListItems` k vizualizaci datových struktur, ve kterých je vše, co potřebujete k vyhodnocení C++ , vyhodnotit prostřednictvím výrazů, ale nemusíte mít dost tvarovat pro `ArrayItems`, `TreeItems`nebo `LinkedListItems.`  

 Vizualizér pro CAtlMap je skvělým příkladem, kde je `CustomListItems` vhodné.  

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

#### <a name="BKMK_TreeItems_expansion"></a>Rozšíření TreeItems  
 Pokud vizuální typ představuje strom, ladicí program může projít stromovou strukturou a zobrazit jeho podřízené položky pomocí uzlu `TreeItems`. Toto je vizualizace pro `std::map` typ pomocí této funkce:  

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

 Syntaxe je velmi podobná `LinkedListItems` uzlu. `LeftPointer`, `RightPointer`a `ValueNode` jsou vyhodnocovány v kontextu třídy uzlu stromu a `ValueNode` mohou být ponechány prázdné nebo musí mít `this`, aby odkazovaly na samotný uzel stromu.  

#### <a name="BKMK_ExpandedItem_expansion"></a>Rozšíření ExpandedItem  
 Element `ExpandedItem` lze použít k vygenerování agregovaného podřízeného zobrazení zobrazením vlastností základních tříd nebo datových členů, jako kdyby byly podřízenými objekty typu vizuálu. Zadaný výraz je vyhodnocen a podřízené uzly výsledku jsou připojeny k podřízenému seznamu vizuálního typu. Předpokládejme například, že máme typ inteligentního ukazatele `auto_ptr<vector<int>>`, který se obvykle bude zobrazovat jako:  

 ![výchozí&#95;rozšíření&#60;auto&#60;PTR&#62; &#62; Vector int](../debugger/media/dbg-natvis-expand-expandeditem-default.png "DBG_NATVIS_Expand_ExpandedItem_Default")  

 Chcete-li zobrazit hodnoty vektoru, je nutné přejít na dvě úrovně v okně proměnné předávané prostřednictvím _Myptr členu. Přidáním prvku `ExpandedItem` můžete eliminovat `_Myptr` proměnnou z hierarchie a přímo zobrazit prvky Vector::  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 ![ExpandedItem&#95;rozšíření&#60;auto&#60;PTR&#62; &#62; Vector int](../debugger/media/dbg-natvis-expand-expandeditem-visualized.png "DBG_NATVIS_Expand_ExpandedItem_Visualized")  

 Následující příklad ukazuje, jak agregovat vlastnosti ze základní třídy v odvozené třídě. Předpokládejme, `CPanel` třída je odvozena z `CFrameworkElement`. Namísto opakování vlastností, které pocházejí ze základní `CFrameworkElement` třídy, `ExpandedItem` uzel umožňuje, aby tyto vlastnosti byly připojeny do podřízeného seznamu třídy `CPanel`. Zde je nutný specifikátor formátu **ND** , který vypíná vizualizaci pro odvozenou třídu. V opačném případě `*(CFrameworkElement*)this` výrazů způsobí, že se vizualizace `CPanel` znovu použije, protože výchozí typy vizualizací, které odpovídají pravidlům, považují za nejvhodnější. Použití specifikátoru formátu **ND** instruuje ladicí program, aby používal vizualizaci základní třídy nebo výchozí rozšíření základní třídy, pokud základní třída neobsahuje vizualizaci.  

```xml  
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  

```  

#### <a name="BKMK_Synthetic_Item_expansion"></a>Rozšíření syntetické položky  
 Kde `ExpandedItem` element poskytuje plošší zobrazení dat odstraněním hierarchií, `Synthetic` uzel v opačném případě. Umožňuje vytvořit umělou podřízenou prvek (tj. podřízený prvek, který není výsledkem výrazu). Tento podřízený element může obsahovat vlastní podřízené prvky. V následujícím příkladu vizualizace typu `Concurrency::array` používá `Synthetic` uzel k zobrazení diagnostické zprávy uživateli:  

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

 ![Concurrency:: Array s Sythentic elementu expansio](../debugger/media/dbg-natvis-expand-synthetic.png "DBG_NATVIS_Expand_Synthetic")  

### <a name="BKMK_HResult"></a>HResult  
 Element `HResult` umožňuje přizpůsobit informace, které se zobrazí pro HRESULT v oknech ladicího programu. Element `HRValue` musí obsahovat 32 hodnotu HRESULT, kterou chcete přizpůsobit. Element `HRDescription` obsahuje informace, které se zobrazí v ladicím programu.  

```  

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

### <a name="BKMK_UIVisualizer"></a>UIVisualizer  
 Element `UIVisualizer` registruje modul plug-in pro grafický Vizualizér pomocí ladicího programu. Modul plug-in pro grafický Vizualizér vytvoří dialogové okno nebo jiné rozhraní pro zobrazení proměnné nebo objektu způsobem, který je vhodný pro svůj datový typ. Modul plug-in Vizualizér musí být vytvořený jako [VSPackage](../extensibility/internals/vspackages.md) a musí vystavit službu, kterou může ladicí program spotřebovat. Soubor. Natvis obsahuje registrační informace pro modul plug-in, jako je jeho název, identifikátor GUID služby a také typy, které může vizualizovat.  

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

 `UIVisualizer` identifikuje dvojice atributů `Id` `ServiceId` - . `ServiceId` je identifikátor GUID služby, která je vystavena balíčkem Vizualizátor, `Id` je jedinečný identifikátor, který lze použít k odlišení vizualizací, pokud služba poskytuje více než jeden Vizualizér. V příkladu výše má stejná služba Vizualizér dva nástroje pro vizualizaci.  

 Atribut `MenuName` je to, co se uživatelům zobrazí jako název vizualizér, když otevřou rozevírací nabídku vedle ikony lupy v oknech proměnných ladicího programu, například:  

 ![Místní nabídka nabídky UIVisualizer](../debugger/media/dbg-natvis-vectorvisualizer.png "DBG_NATVIS_VectorVisualizer")  

 Každý typ definovaný v souboru. Natvis musí explicitně uvést seznam vizualizací uživatelského rozhraní, které je může zobrazit. Ladicí program odpovídá odkazům Vizualizátoru v položkách typu pro porovnávání typů s registrovanými vizualizacemi. Například následující položka typu pro `std::vector` odkazuje na UIVisualizer v našem příkladu výše.  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 Můžete vidět příklad UIVisualizer v rozšíření pro sledování obrázků, který se používá k zobrazení rastrových obrázků v paměti: [ImageWatch](https://visualstudiogallery.msdn.microsoft.com/e682d542-7ef3-402c-b857-bbfba714f78d)  

### <a name="customvisualizer-element"></a>Element CustomVisualizer  
 `CustomVisualizer` je bod rozšíření, který určuje rozšíření VSIX, které můžete napsat pro řízení vizualizace v kódu, který běží v aplikaci Visual Studio. Další informace o vytváření rozšíření VSIX naleznete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Zápis vlastního Vizualizátoru je mnohem více práce než zápis definice XML Natvis, ale nejste omezeni omezeními toho, co Natvis podporuje nebo nepodporuje. Vlastní nástroje pro vizualizace mají přístup k úplné sadě rozhraní API pro rozšiřitelnost ladicího programu, které lze použít k dotazování a úpravám laděného procesu procesu nebo komunikaci s jinými částmi sady Visual Studio.  

 Pro prvky CustomVisualizer můžete použít atributy `Condition`, `IncludeView`a `ExcludeView`.
