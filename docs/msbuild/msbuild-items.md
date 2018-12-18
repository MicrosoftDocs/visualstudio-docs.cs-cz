---
title: Položky nástroje MSBuild | Dokumentace Microsoftu
description: Použijte atribut MSBuild obsahovat element ItemGroup a určete soubory, které mají být zahrnuty v sestavení
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 28d98b7c74ebc57bd5b7b529303f2f5a17277ff5
ms.sourcegitcommit: 6672a1e9d135d7e5cca3cceea07c6fe5a0871475
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2018
ms.locfileid: "47443594"
---
# <a name="msbuild-items"></a>Položky nástroje MSBuild
Položky nástroje MSBuild jsou vstupy do systému sestavení a obvykle představují soubory (soubory jsou určené v `Include` atributu). Položky jsou seskupeny do typů položek podle jejich názvy elementů. Seznam položek, které lze použít jako parametry pro úkoly jsou pojmenované typy položek. Úkoly pomocí hodnoty položek k provedení kroků procesu sestavení.  
  
 Protože položky jsou pojmenovány podle typu položky, do které patří, podmínky "item" a "položky hodnotu" zaměnitelné.  
  
##  <a name="create-items-in-a-project-file"></a>Vytvoření položky v souboru projektu  
 Deklarujete položky v souboru projektu jako podřízené prvky [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementu. Název podřízeného prvku je typ položky. `Include` Atribut elementu, který určuje položky (soubory), které chcete být součástí tohoto typu položky. Například následující XML kód vytvoří typ položky, který je pojmenován `Compile`, který obsahuje dva soubory.  
  
```xml  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 Položka *file2.cs* nenahrazuje položky *file1.cs*; místo toho se připojí název souboru do seznamu hodnot `Compile` typ položky.
  
 Následující XML kód vytvoří stejný typ položky deklarováním oba soubory v jednom `Include` atribut. Všimněte si, že názvy souborů jsou odděleny středníkem.  
  
```xml  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
##  <a name="create-items-during-execution"></a>Vytvářet položky za běhu  
 Položky, které jsou mimo [cílové](../msbuild/target-element-msbuild.md) prvky jsou přiřazeny hodnoty během fáze vyhodnocení sestavení. Během následující fáze vykonávání můžou položky vytvořit nebo upravit následujícími způsoby:  
  
-   Všechny úlohy lze generovat položky. Generovat položku, [úloh](../msbuild/task-element-msbuild.md) element musí mít podřízený [výstup](../msbuild/output-element-msbuild.md) element, který má `ItemName` atribut.  
  
-   [Createitem –](../msbuild/createitem-task.md) úloh lze generovat položky. Tento způsob využití je zastaralý.  
  
-   Od verze rozhraní .NET Framework 3.5 `Target` prvky mohou obsahovat [ItemGroup](../msbuild/itemgroup-element-msbuild.md) prvky, které mohou obsahovat položky elementy.  
  
##  <a name="reference-items-in-a-project-file"></a>Odkaz na položky v souboru projektu  
 Chcete-li odkazovat na typy položek v celém souboru projektu, použijte syntaxi @(\<ItemType >). Například typ položky v předchozím příkladu by odkazovat pomocí `@(Compile)`. Pomocí následující syntaxe můžete předat položek úkolů zadáním položky jako parametr dané úlohy. Další informace najdete v tématu [postupy: výběr souborů pro sestavení](../msbuild/how-to-select-the-files-to-build.md).  
  
 Ve výchozím nastavení jsou položky Typ položky oddělené středníkem (;) při je rozbalený. Pomocí syntaxe @(\<ItemType >, "\<oddělovač >') Chcete-li určit oddělovač jiné než výchozí. Další informace najdete v tématu [postupy: zobrazování seznamu položek oddělených čárkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md).  
  
##  <a name="use-wildcards-to-specify-items"></a>Pomocí zástupných znaků můžete zadat položky  

Můžete použít `**`, `*`, a `?` zástupné znaky jako vstupy pro sestavení namísto vypisování každého souboru zvlášť zadat skupiny souborů.
  
- `?` Zástupný znak odpovídá jednomu znaku.
- `*` Zástupný znak odpovídá nula nebo více znaků.
- `**` Sekvence znaků zástupný znak odpovídá část cesty.

Například můžete zadat všechny `.cs` soubory soubory v adresáři, který obsahuje projekt s použitím následující element v souboru projektu.

```xml  
<CSFile Include="*.cs"/>  
```  

Následující element vybere všechny `.vb` soubory na `D:` jednotky:

```xml  
<VBFile Include="D:/**/*.vb"/>  
```  

Pokud chcete zahrnout literálu `*` nebo `?` znaků položky bez rozšíření zástupného znaku, je nutné [řídicí zástupné znaky](../msbuild/how-to-escape-special-characters-in-msbuild.md).

Další informace o zástupných znacích naleznete v tématu [postupy: výběr souborů pro sestavení](../msbuild/how-to-select-the-files-to-build.md).  

##  <a name="use-the-exclude-attribute"></a>Použijte atribut vyloučení  
 Může obsahovat prvky položky `Exclude` atribut, který vyloučí konkrétní položky (soubory) z tohoto typu položky. `Exclude` Atribut se obvykle používá spolu s zástupné znaky. Například následující kód XML přidá každý *.cs* souborů v adresáři CSFile typu položky, s výjimkou *DoNotBuild.cs* souboru.  
  
```xml  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
 `Exclude` Atribut ovlivňuje pouze položky, které jsou přidány pomocí `Include` atribut v prvku položky, která obsahuje oba. V následujícím příkladu by vyjměte soubor *Form1.cs*, která byla přidána do předchozí prvek položky.  
  
```xml  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 Další informace najdete v tématu [postupy: vyloučení souborů ze sestavení](../msbuild/how-to-exclude-files-from-the-build.md).  
  
##  <a name="item-metadata"></a>Metadata položky  
 Položky mohou obsahovat metadata spolu s informacemi v `Include` a `Exclude` atributy. Tato metadata je možné podle úlohy, které vyžadují další informace o položkách nebo dávkové úlohy a cíle. Další informace najdete v tématu [dávkování](../msbuild/msbuild-batching.md).  
  
 Metadata jsou kolekce párů klíč hodnota, které jsou deklarovány v souboru projektu jako podřízené prvky prvku položek. Název podřízeného elementu je název metadat a hodnota podřízeného elementu je hodnota metadat.  
  
 Metadata jsou přidružené položky element, který jej obsahuje. Například následující kód XML přidá `Culture` metadata, která má hodnotu `Fr` zároveň *one.cs* a *two.cs* položky CSFile typ položky.  
  
```xml  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Položka může mít nula nebo více hodnot metadat. Kdykoli můžete změnit hodnoty metadat. Pokud nastavíte metadat na prázdnou hodnotu, efektivně ho odeberete ze sestavení.  
  
###  <a name="BKMK_ReferencingItemMetadata"></a> Odkazuje na metadata položky v souboru projektu  
 Metadata položek v celém souboru projektu můžete odkazovat pomocí syntaxe %(\<ItemMetadataName >). Pokud existuje nejednoznačnost kvalifikovat pomocí názvu typu položky odkazu. For example, můžete zadat %(\<ItemType.ItemMetaDataName >). Zobrazení metadat pro dávkové úlohy zprávy v následujícím příkladu. Další informace o tom, jak používat metadata položky pro dávkové zpracování, naleznete v tématu [metadata položek v dávkování úloh](../msbuild/item-metadata-in-task-batching.md).  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Stuff Include="One.cs" >  
            <Display>false</Display>  
        </Stuff>  
        <Stuff Include="Two.cs">  
            <Display>true</Display>  
        </Stuff>  
    </ItemGroup>  
    <Target Name="Batching">  
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>  
    </Target>  
</Project>  
```  
  
###  <a name="BKMK_WellKnownItemMetadata"></a> Metadata známé položky  
 Při přidání položky typů položek této položky je přiřazen některé známé metadat. For example, všechny položky mít dobře známý metadata %(\<název souboru >), jehož hodnota je název souboru položky. Další informace najdete v tématu [metadata známé položky](../msbuild/msbuild-well-known-item-metadata.md).  
  
###  <a name="BKMK_Transforming"></a> Transformace typy položek na základě metadat  
 Seznamy položek můžete transformovat do nové seznamy položek na základě metadat. Například můžete převést typ položky `CppFiles` , který obsahuje položky, které představují *.cpp* soubory na odpovídající seznam *.obj* soubory pomocí výrazu `@(CppFiles -> '%(Filename).obj')`.  
  
 Následující kód vytvoří `CultureResource` typ, který obsahuje všechny kopie položky `EmbeddedResource` položek se závislostmi `Culture` metadat. `Culture` Hodnota metadat se stane hodnota novými metadaty `CultureResource.TargetDirectory`.  
  
```xml  
<Target Name="ProcessCultureResources">  
    <ItemGroup>  
        <CultureResource Include="@(EmbeddedResource)"  
            Condition="'%(EmbeddedResource.Culture)' != ''">  
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>  
        </CultureResource>  
    </ItemGroup>  
</Target>  
```  
  
 Další informace najdete v tématu [transformuje](../msbuild/msbuild-transforms.md).  
  
##  <a name="item-definitions"></a>Definice položek  
 Spuštění v rozhraní .NET Framework 3.5, můžete přidat výchozí metadat na libovolný typ položky pomocí [ItemDefinitionGroup – element](../msbuild/itemdefinitiongroup-element-msbuild.md). Jako známá metadata metadat výchozí souvisí se všemi položkami typu položky, který zadáte. Můžete explicitně přepsat výchozí metadat v definici položky. Například následující kód XML poskytuje `Compile` položky *one.cs* a *three.cs* metadata `BuildDay` s hodnotou "Pondělí". Kód poskytuje položku *two.cs* metadata `BuildDay` s hodnotou "Úterý".  
  
```xml  
<ItemDefinitionGroup>  
    <Compile>  
        <BuildDay>Monday</BuildDay>  
    </Compile>  
</ItemDefinitionGroup>  
<ItemGroup>  
    <Compile Include="one.cs;three.cs" />  
    <Compile Include="two.cs">  
        <BuildDay>Tuesday</BuildDay>  
    </Compile>  
</ItemGroup>  
```  
  
 Další informace najdete v tématu [definice položek](../msbuild/item-definitions.md).  
  
##  <a name="attributes-for-items-in-an-itemgroup-of-a-target"></a>Atributy pro položky v ItemGroup cíl  
 Od verze rozhraní .NET Framework 3.5 `Target` prvky mohou obsahovat [ItemGroup](../msbuild/itemgroup-element-msbuild.md) prvky, které mohou obsahovat položky elementy. Atributy v této části jsou platné, pokud jsou zadány pro položku v `ItemGroup` , který je ve `Target`.  
  
###  <a name="BKMK_RemoveAttribute"></a> Odebrat atribut  
 `Remove` Atribut odebere konkrétní položky (soubory) z typu položky. Tento atribut byla zavedena v rozhraní .NET Framework 3.5, ale byla podporována pouze v rámci cíle do 15.0 nástroje MSBuild.
  
 Následující příklad odebere každý *.config* souboru z typu položky kompilace.  
  
```xml  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
###  <a name="BKMK_KeepMetadata"></a> Atribut KeepMetadata  
 Pokud v rámci cíle je generována položka, může obsahovat prvek položky `KeepMetadata` atribut. Pokud tento atribut není zadán, pouze metadata, která je zadána v středníkem oddělený seznam názvů budou přeneseny z položky zdroje cílovou položku. Prázdná hodnota pro tento atribut je ekvivalentní bez zadání. `KeepMetadata` Atribut byla zavedena v rozhraní .NET Framework 4.5.  
  
 Následující příklad ukazuje způsob použití `KeepMetadata` atribut.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0">  
  
    <ItemGroup>  
        <FirstItem Include="rhinoceros">  
            <Class>mammal</Class>  
            <Size>large</Size>  
        </FirstItem>  
  
    </ItemGroup>  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />  
        </ItemGroup>  
  
        <Message Text="FirstItem: %(FirstItem.Identity)" />  
        <Message Text="  Class: %(FirstItem.Class)" />  
        <Message Text="  Size:  %(FirstItem.Size)"  />  
  
        <Message Text="SecondItem: %(SecondItem.Identity)" />  
        <Message Text="  Class: %(SecondItem.Class)" />  
        <Message Text="  Size:  %(SecondItem.Size)"  />  
    </Target>  
</Project>  
  
<!--  
Output:  
  FirstItem: rhinoceros  
    Class: mammal  
    Size:  large  
  SecondItem: rhinoceros  
    Class: mammal  
    Size:   
-->  
```  
  
###  <a name="BKMK_RemoveMetadata"></a> Atribut RemoveMetadata  
 Pokud v rámci cíle je generována položka, může obsahovat prvek položky `RemoveMetadata` atribut. Pokud tento atribut je zadán, všechna metadata je přeneseny z položky zdroje do cílové položky s výjimkou metadat jejichž názvy jsou obsaženy v seznam názvů oddělených středníkem. Prázdná hodnota pro tento atribut je ekvivalentní bez zadání. `RemoveMetadata` Atribut byla zavedena v rozhraní .NET Framework 4.5.  
  
 Následující příklad ukazuje způsob použití `RemoveMetadata` atribut.  
  
```xml  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <MetadataToRemove>Size;Material</MetadataToRemove>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <Item1 Include="stapler">  
            <Size>medium</Size>  
            <Color>black</Color>  
            <Material>plastic</Material>  
        </Item1>  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />  
        </ItemGroup>  
  
        <Message Text="Item1: %(Item1.Identity)" />  
        <Message Text="  Size:     %(Item1.Size)" />  
        <Message Text="  Color:    %(Item1.Color)" />  
        <Message Text="  Material: %(Item1.Material)" />  
        <Message Text="Item2: %(Item2.Identity)" />  
        <Message Text="  Size:     %(Item2.Size)" />  
        <Message Text="  Color:    %(Item2.Color)" />  
        <Message Text="  Material: %(Item2.Material)" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: stapler  
    Size:     medium  
    Color:    black  
    Material: plastic  
  Item2: stapler  
    Size:       
    Color:    black  
    Material:   
-->  
```  
  
###  <a name="BKMK_KeepDuplicates"></a> Atribut KeepDuplicates  
 Pokud v rámci cíle je generována položka, může obsahovat prvek položky `KeepDuplicates` atribut. `KeepDuplicates` je `Boolean` atribut, který určuje, zda položka by měla přidat k cílové skupině, pokud je položka přesnou kopii existující položku.  
  
 Pokud zdrojové a cílové položky mají stejnou hodnotu zahrnout ale rozdílná metadata, přidá se položka i v případě `KeepDuplicates` je nastavena na `false`. Prázdná hodnota pro tento atribut je ekvivalentní bez zadání. `KeepDuplicates` Atribut byla zavedena v rozhraní .NET Framework 4.5.  
  
 Následující příklad ukazuje způsob použití `KeepDuplicates` atribut.  
  
```xml  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Item1 Include="hourglass;boomerang" />  
        <Item2 Include="hourglass;boomerang" />  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item1 Include="hourglass" KeepDuplicates="false" />  
            <Item2 Include="hourglass" />  
        </ItemGroup>  
  
        <Message Text="Item1: @(Item1)" />  
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />  
        <Message Text="Item2: @(Item2)" />  
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: hourglass;boomerang  
    hourglass  Count: 1  
    boomerang  Count: 1  
  Item2: hourglass;boomerang;hourglass  
    hourglass  Count: 2  
    boomerang  Count: 1  
-->  
```  
  
## <a name="see-also"></a>Viz také:  
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)  
 [Nástroj MSBuild](../msbuild/msbuild.md)   
 [Postupy: výběr souborů pro sestavení](../msbuild/how-to-select-the-files-to-build.md)   
 [Postupy: vyloučení souborů ze sestavení](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Postupy: zobrazování seznamu položek oddělených čárkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [Definice položek](../msbuild/item-definitions.md)   
 [Dávkové zpracování](../msbuild/msbuild-batching.md)   
 [Item – element (MSBuild)](../msbuild/item-element-msbuild.md)