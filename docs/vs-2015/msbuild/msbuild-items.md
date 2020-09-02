---
title: Položky nástroje MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 19f22fc56881287cfb501143aaa4397f9a035d78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821636"
---
# <a name="msbuild-items"></a>Položky nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Položky nástroje MSBuild jsou vstupy do systému sestavení a obvykle představují soubory. Položky jsou seskupeny do typů položek na základě jejich názvů prvků. Typy položek jsou pojmenované seznamy položek, které lze použít jako parametry pro úlohy. Úkoly používají hodnoty položek k provedení kroků procesu sestavení.  
  
 Vzhledem k tomu, že položky jsou pojmenovány typem položky, ke kterým patří, je možné použít "položku" a "hodnotu položky", které jsou zaměnitelné.  
  
 **V tomto tématu**  
  
- [Vytváření položek v souboru projektu](#BKMK_Creating1)  
  
- [Vytváření položek během provádění](#BKMK_Creating2)  
  
- [Odkazování na položky v souboru projektu](#BKMK_ReferencingItems)  
  
- [Zadání položek pomocí zástupných znaků](#BKMK_Wildcards)  
  
- [Použití atributu Exclude](#BKMK_ExcludeAttribute)  
  
- [Metadata položky](#BKMK_ItemMetadata)  
  
  - [Odkazování na metadata položky v souboru projektu](#BKMK_ReferencingItemMetadata)  

  - [Metadata známé položky](#BKMK_WellKnownItemMetadata)  

  - [Transformace typů položek pomocí metadat](#BKMK_Transforming)  
  
- [Definice položek](#BKMK_ItemDefinitions)  
  
- [Atributy pro položky v instanci položky cíle](#BKMK_AttributesWithinTargets)  
  
  - [Odebrat atribut](#BKMK_RemoveAttribute)  

  - [KeepMetadata – atribut](#BKMK_KeepMetadata)  

  - [RemoveMetadata – atribut](#BKMK_RemoveMetadata)  

  - [KeepDuplicates – atribut](#BKMK_KeepDuplicates)  
  
## <a name="creating-items-in-a-project-file"></a><a name="BKMK_Creating1"></a> Vytváření položek v souboru projektu  
 Položky v souboru projektu deklarujete jako podřízené prvky elementu [ItemCollection](../msbuild/itemgroup-element-msbuild.md) . Název podřízeného prvku je typ položky. `Include`Atribut elementu určuje položky (soubory), které mají být zahrnuty do daného typu položky. Například následující kód XML vytvoří typ položky s názvem `Compile` , který obsahuje dva soubory.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 Položka "file2.cs" nenahrazuje položku "file1.cs"; místo toho se název souboru připojí k seznamu hodnot pro daný `Compile` typ položky. Nemůžete odebrat položku z typu položky během fáze hodnocení sestavení.  
  
 Následující kód XML vytvoří stejný typ položky deklarováním obou souborů v jednom `Include` atributu. Všimněte si, že názvy souborů jsou oddělené středníkem.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
## <a name="creating-items-during-execution"></a><a name="BKMK_Creating2"></a> Vytváření položek během provádění  
 K položkám, které jsou mimo [cílové](../msbuild/target-element-msbuild.md) prvky, jsou přiřazeny hodnoty během fáze hodnocení sestavení. Během následné fáze provádění lze položky vytvořit nebo upravit následujícími způsoby:  
  
- Libovolný úkol může vygenerovat položku. Chcete-li vygenerovat položku, musí mít element [Task](../msbuild/task-element-msbuild.md) podřízený element [Output](../msbuild/output-element-msbuild.md) , který má `ItemName` atribut.  
  
- Úkol [CreateItem –](../msbuild/createitem-task.md) může vygenerovat položku. Tento způsob využití je zastaralý.  
  
- Počínaje .NET Framework 3,5 `Target` prvky mohou obsahovat prvky [položky](../msbuild/itemgroup-element-msbuild.md) , které mohou obsahovat prvky položky.  
  
## <a name="referencing-items-in-a-project-file"></a><a name="BKMK_ReferencingItems"></a> Odkazování na položky v souboru projektu  
 Chcete-li odkazovat na typy položek v celém souboru projektu, použijte syntaxi @ ( `ItemType` ). Například byste odkazovali na typ položky v předchozím příkladu pomocí `@(Compile)` . Pomocí této syntaxe můžete předat položky úkolů zadáním typu položky jako parametru této úlohy. Další informace najdete v tématu [Postupy: výběr souborů pro sestavení](../msbuild/how-to-select-the-files-to-build.md).  
  
 Ve výchozím nastavení jsou položky typu položky oddělené středníky (;) Když je rozbalený. Syntaxi @ (*ItemType*, '*oddělovač*') můžete použít k určení oddělovače, který je jiný než výchozí. Další informace najdete v tématu [Postup: zobrazení seznamu položek oddělených čárkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md).  
  
## <a name="using-wildcards-to-specify-items"></a><a name="BKMK_Wildcards"></a> Zadání položek pomocí zástupných znaků  
 Můžete použít * *, \* a? zástupné znaky pro určení skupiny souborů jako vstupů pro sestavení místo výpisu každého souboru samostatně.  
  
- Znak ? zástupný znak odpovídá jednomu znaku.  
  
- Zástupný znak * odpovídá žádnému nebo více znakům.  
  
- Sekvence zástupného znaku * * odpovídá částečné cestě.  
  
  Můžete například zadat všechny soubory. cs v adresáři, který obsahuje soubor projektu, pomocí následujícího elementu v souboru projektu.  
  
```  
<CSFile Include="*.cs"/>  
```  
  
 Následující prvek vybere všechny soubory. vb na jednotce D::  
  
```  
<VBFile Include="D:/**/*.vb"/>  
```  
  
 Další informace o zástupných znacích naleznete v tématu [How to: vyberte soubory, které chcete sestavit](../msbuild/how-to-select-the-files-to-build.md).  
  
## <a name="using-the-exclude-attribute"></a><a name="BKMK_ExcludeAttribute"></a> Použití atributu Exclude  
 Prvky položky mohou obsahovat `Exclude` atribut, který vylučuje konkrétní položky (soubory) z typu položky. `Exclude`Atribut se obvykle používá společně se zástupnými znaky. Například následující kód XML přidá každý soubor. cs v adresáři do typu položky CSFile, s výjimkou `DoNotBuild.cs` souboru.  
  
```  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
 `Exclude`Atribut ovlivňuje pouze položky, které jsou přidány `Include` atributem v prvku Item, který je obsahuje obě. Následující příklad nevylučuje soubor Form1.cs, který byl přidán do předchozí položky elementu.  
  
```  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 Další informace najdete v tématu [Postup: vyloučení souborů ze sestavení](../msbuild/how-to-exclude-files-from-the-build.md).  
  
## <a name="item-metadata"></a><a name="BKMK_ItemMetadata"></a> Metadata položky  
 Kromě informací v atributech a můžou položky obsahovat i metadata `Include` `Exclude` . Tato metadata mohou být používána úkoly, které vyžadují další informace o položkách nebo úlohách a cílech Batch. Další informace najdete v tématu [dávkování](../msbuild/msbuild-batching.md).  
  
 Metadata je kolekce párů klíč-hodnota, které jsou deklarovány v souboru projektu jako podřízené prvky elementu Item. Název podřízeného prvku je název metadat a hodnota podřízeného elementu je hodnota metadat.  
  
 Metadata jsou přidružena k elementu Item, který jej obsahuje. Například následující kód XML přidá `Culture` metadata, která mají hodnotu `Fr` pro "One.cs" a "Two.cs" položky typu položky CSFile.  
  
```  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Položka může mít nula nebo více hodnot metadat. Hodnoty metadat můžete kdykoli změnit. Pokud nastavíte metadata na prázdnou hodnotu, můžete ji efektivně odebrat ze sestavení.  
  
### <a name="referencing-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> Odkazování na metadata položky v souboru projektu  
 Metadata položky můžete odkazovat v celém souboru projektu pomocí syntaxe%( `ItemMetadataName` ). Pokud existuje nejednoznačnost, můžete kvalifikovat odkaz pomocí názvu typu položky. Můžete například zadat%(*ItemType. ItemMetaDataName*). Následující příklad používá metadata zobrazení k dávkování úlohy zprávy. Další informace o tom, jak používat metadata položek pro dávkování, najdete v tématu [Metadata položek v dávkování úloh](../msbuild/item-metadata-in-task-batching.md).  
  
```  
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
  
### <a name="well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a> Dobře známá metadata položky  
 Když je položka přidána do typu položky, je tato položka přiřazena dobře známým metadatům. Všechny položky mají například dobře známá metadata `%(Filename)` , jejichž hodnota je název souboru položky. Další informace najdete v tématu [známá metadata položek](../msbuild/msbuild-well-known-item-metadata.md).  
  
### <a name="transforming-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> Transformace typů položek pomocí metadat  
 Seznamy položek můžete transformovat do seznamů nové položky pomocí metadat. Například můžete převést typ položky `CppFiles` , který obsahuje položky, které reprezentují soubory. cpp, do odpovídajícího seznamu souborů. obj pomocí výrazu `@(CppFiles -> '%(Filename).obj')` .  
  
 Následující kód vytvoří `CultureResource` typ položky, který obsahuje kopie všech `EmbeddedResource` položek s `Culture` metadaty. `Culture`Hodnota metadata se zobrazí jako hodnota nových metadat `CultureResource.TargetDirectory` .  
  
```  
<Target Name="ProcessCultureResources">  
    <ItemGroup>  
        <CultureResource Include="@(EmbeddedResource)"  
            Condition="'%(EmbeddedResource.Culture)' != ''">  
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>  
        </CultureResource>  
    </ItemGroup>  
</Target>  
```  
  
 Další informace najdete v tématu [transformace](../msbuild/msbuild-transforms.md).  
  
## <a name="item-definitions"></a><a name="BKMK_ItemDefinitions"></a> Definice položek  
 Počínaje .NET Framework 3,5 můžete přidat výchozí metadata k libovolnému typu položky pomocí [elementu ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md). Podobně jako dobře známá metadata jsou výchozí metadata přidružena ke všem položkám typu položky, které zadáte. Výchozí metadata můžete explicitně přepsat v definici položky. Například následující kód XML poskytuje `Compile` položky "One.cs" a "Three.cs" metadata `BuildDay` s hodnotou "pondělí". Kód přiřadí položku "two.cs" metadata `BuildDay` s hodnotou "úterý".  
  
```  
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
  
 Další informace naleznete v tématu [Definice položek](../msbuild/item-definitions.md).  
  
## <a name="attributes-for-items-in-an-itemgroup-of-a-target"></a><a name="BKMK_AttributesWithinTargets"></a> Atributy pro položky v instanci položky cíle  
 Počínaje .NET Framework 3,5 `Target` prvky mohou obsahovat prvky [položky](../msbuild/itemgroup-element-msbuild.md) , které mohou obsahovat prvky položky. Atributy v této části jsou platné, pokud jsou zadány pro položku v objektu `ItemGroup` , který je v `Target` .  
  
### <a name="remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> Odebrat atribut  
 Položky v `ItemGroup` cíli mohou obsahovat `Remove` atribut, který odebere konkrétní položky (soubory) z typu položky. Tento atribut byl představen v .NET Framework 3,5.  
  
 Následující příklad odebere každý soubor. config z typu položky kompilace.  
  
```  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
### <a name="keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a> KeepMetadata – atribut  
 Pokud je položka generována v rámci cíle, element Item může `KeepMetadata` atribut obsahovat. Pokud je tento atribut zadán, budou ze zdrojové položky do cílové položky přenesena pouze metadata, která jsou zadána v seznamu názvů oddělených středníkem. Prázdná hodnota pro tento atribut je ekvivalentní s jeho zadáním. `KeepMetadata`Atribut byl představen v .NET Framework 4,5.  
  
 Následující příklad ukazuje, jak použít `KeepMetadata` atribut.  
  
```  
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
  
### <a name="removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a> RemoveMetadata – atribut  
 Pokud je položka generována v rámci cíle, element Item může `RemoveMetadata` atribut obsahovat. Je-li tento atribut zadán, jsou všechna metadata přenesena ze zdrojové položky do cílové položky s výjimkou metadat, jejichž názvy jsou obsaženy v seznamu názvů oddělených středníkem. Prázdná hodnota pro tento atribut je ekvivalentní s jeho zadáním. `RemoveMetadata`Atribut byl představen v .NET Framework 4,5.  
  
 Následující příklad ukazuje, jak použít `RemoveMetadata` atribut.  
  
```  
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
  
### <a name="keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> KeepDuplicates – atribut  
 Pokud je položka generována v rámci cíle, element Item může `KeepDuplicates` atribut obsahovat. `KeepDuplicates` je `Boolean` atribut, který určuje, zda má být položka přidána do cílové skupiny, pokud je položka přesným duplikátem existující položky.  
  
 Pokud má zdrojová a cílová položka stejnou hodnotu zahrnutí, ale odlišná metadata, položka je přidána i v případě, že `KeepDuplicates` je nastavena na `false` . Prázdná hodnota pro tento atribut je ekvivalentní s jeho zadáním. `KeepDuplicates`Atribut byl představen v .NET Framework 4,5.  
  
 Následující příklad ukazuje, jak použít `KeepDuplicates` atribut.  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)  
 [Nástroji](msbuild.md)   
 [Postupy: výběr souborů k sestavení](../msbuild/how-to-select-the-files-to-build.md)   
 [Postupy: vyloučení souborů ze sestavení](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Postupy: zobrazení seznamu položek oddělených čárkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [Definice položek](../msbuild/item-definitions.md)   
 [Dávkování](../msbuild/msbuild-batching.md)   
 [Item – prvek (MSBuild)](../msbuild/item-element-msbuild.md)
