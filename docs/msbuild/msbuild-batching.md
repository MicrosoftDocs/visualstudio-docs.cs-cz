---
title: Dávkování nástroje MSBuild | Microsoft Docs
ms.date: 06/09/2020
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d7c72d1da270220144cd5e6167ebecb66462ba9
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289271"
---
# <a name="msbuild-batching"></a>Dávkování nástroje MSBuild

Nástroj MSBuild rozdělí seznamy položek do různých kategorií nebo dávek na základě metadat položky a spustí cíl nebo úlohu jednou při každé dávce.

## <a name="task-batching"></a>Dávkování úloh

Dávkování úloh umožňuje zjednodušit soubory projektu tím, že poskytuje způsob, jak rozdělit seznamy položek do různých dávek a předat každou z těchto dávek do úlohy samostatně. To znamená, že soubor projektu potřebuje mít úlohu a její atributy deklarované pouze jednou, i když je možné ji spustit několikrát.

Určíte, že chcete, aby nástroj MSBuild prováděl dávkování s úkolem pomocí `%(ItemMetaDataName)` zápisu v jednom z atributů úkolu. V následujícím příkladu je rozdělen `Example` seznam položek na dávky založené na `Color` hodnotě metadat položky a každý z těchto dávek se do úlohy předává `MyTask` samostatně.

> [!NOTE]
> Pokud neodkazujte na seznam položek jinde v atributech úlohy nebo název metadat může být nejednoznačný, můžete použít notaci%(<ItemCollection. ItemMetaDataName>) k úplnému zařazení hodnoty metadat položky, která se má použít pro dávkování.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Konkrétnější příklady dávkování najdete [v tématu Metadata položek v dávkování úloh](../msbuild/item-metadata-in-task-batching.md).

## <a name="target-batching"></a>Dávkování cíle

Nástroj MSBuild kontroluje, zda jsou vstupy a výstupy cíle aktuální předtím, než spustí cíl. Pokud jsou vstupy i výstupy aktuální, přeskočí se cíl. Pokud úloha v cíli používá dávkování, nástroj MSBuild potřebuje určit, jestli jsou vstupy a výstupy pro každou dávku položek aktuální. V opačném případě se cíl spustí pokaždé, když je dosaženo.

Následující příklad ukazuje `Target` prvek, který obsahuje `Outputs` atribut se `%(ItemMetadataName)` zápisem. Nástroj MSBuild rozdělí `Example` seznam položek na dávky založené na `Color` metadatech položky a analyzuje časová razítka výstupních souborů pro každou dávku. Pokud výstupy ze dávky nejsou aktuální, je cíl spuštěn. V opačném případě se cíl přeskočí.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask"
        Inputs="@(Example)"
        Outputs="%(Color)\MyFile.txt">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Další příklad cílového dávkování najdete v tématu [Metadata položek v cílové dávce](../msbuild/item-metadata-in-target-batching.md).

## <a name="item-and-property-mutations"></a>Mutace položek a vlastností

Tato část popisuje, jak porozumět důsledkům změny vlastností nebo metadat položek při použití cílového dávkování nebo dávkování úloh.

Vzhledem k tomu, že cílové dávkové zpracování a dávkování úloh jsou dvě různé operace nástroje MSBuild, je důležité pochopit přesně to, která forma dávkování MSBuild používá v každém případě. Pokud se syntaxe dávkování `%(ItemMetadataName)` objeví v úloze v cíli, ale ne v atributu v cíli, nástroj MSBuild použije dávkování úloh. Jediným způsobem, jak určit cílové dávkové zpracování, je použití syntaxe dávkování u cílového atributu, obvykle `Outputs` atributu.

Pro dávkové zpracování dávkování a dávkování úloh je možné dávky považovat za nezávisle. Všechny dávky začínají kopií stejného počátečního stavu hodnot metadat vlastností a položek. Jakékoli mutace hodnot vlastností během provádění dávky nejsou viditelné pro ostatní dávky. Uvažujte následující příklad:

```xml
  <ItemGroup>
    <Thing Include="2" Color="blue" />
    <Thing Include="1" Color="red" />
  </ItemGroup>

  <Target Name="DemoIndependentBatches">
    <ItemGroup>
      <Thing Condition=" '%(Color)' == 'blue' ">
        <Color>red</Color>
        <NeededColorChange>true</NeededColorChange>
      </Thing>
    </ItemGroup>
    <Message Importance="high"
             Text="Things: @(Thing->'%(Identity) is %(Color); needed change=%(NeededColorChange)')"/>
  </Target>
```

Výstup bude následující:

```output
Target DemoIndependentBatches:
  Things: 2 is red; needed change=true;1 is red; needed change=
```

`ItemGroup`V cíli je implicitně úkol a s `%(Color)` `Condition` atributem v je provedena dávkování úloh. Existují dvě dávky: jeden pro červený a druhý pro modrou. Vlastnost `%(NeededColorChange)` je nastavena pouze v případě, že jsou `%(Color)` metadata modrá a nastavení ovlivňuje pouze jednotlivé položky, které odpovídají dané podmínce při spuštění modré dávky. `Message` `Text` Atribut úkolu neaktivuje dávkování bez ohledu na `%(ItemMetadataName)` syntaxi, protože se používá uvnitř transformace položky.

Dávky běží nezávisle, ale ne paralelně. Díky tomu se při přístupu k hodnotám metadat, které se mění v dávkovém provádění, liší. V případě, kdy jste vlastnost nastavili na základě některých metadat v dávkovém spuštění, by vlastnost měla vzít *Poslední* sadu hodnot:

```xml
   <PropertyGroup>
       <SomeProperty>%(SomeItem.MetadataValue)</SomeProperty>
   </PropertyGroup>
```

Po provedení dávky vlastnost uchová konečnou hodnotu `%(MetadataValue)` .

I když se dávky spouštějí nezávisle, je důležité vzít v úvahu rozdíl mezi cílovou dávkování a dávkování úloh a zjistit, který typ se vztahuje na vaši situaci. Vezměte v úvahu následující příklad, který vám pomůže lépe pochopit důležitost tohoto rozdílu.

Úlohy mohou být implicitní, spíše než explicitní, což může být matoucí, pokud dojde k dávkám úloh s implicitními úkoly. Pokud `PropertyGroup` `ItemGroup` se prvek nebo zobrazí v `Target` , každá deklarace vlastnosti ve skupině je implicitně zpracována podobně jako samostatný [CreateProperty –](createproperty-task.md) nebo [CreateItem –](createitem-task.md) úloha. To znamená, že chování je odlišné v případě, kdy je cíl dávkově vytvořen, versus když není cíl dávkově (tj. Pokud nemá `%(ItemMetadataName)` syntaxi v `Outputs` atributu). Pokud je cíl v dávce, provede se `ItemGroup` jednou pro každý cíl, ale pokud není cíl dávkování, implicitní ekvivalenty `CreateItem` nebo `CreateProperty` úlohy se dávkují pomocí dávkování úloh, takže cíl se spustí jenom jednou a každá položka nebo vlastnost ve skupině se dávkuje samostatně pomocí dávkování úloh.

Následující příklad znázorňuje cílové dávkové zpracování vs. dávkování úloh v případě, kdy se metadata použijí. Vezměte v úvahu situaci, kdy máte složky a a B s některými soubory:

```
A\1.stub
B\2.stub
B\3.stub
```

Teď se podívejte na výstup těchto dvou podobných projektů.

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build" Outputs="%(StubDirs.Identity)">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

Výstup bude následující:

```output
Test1:
  >> A\ 'A\' 'A'
Test1:
  >> B\ 'B\' 'B'
```

Nyní odeberte `Outputs` atribut, který zadává cílové dávkování.

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

Výstup bude následující:

```output
Test1:
  >> A\ 'B\' 'B'
  >> B\ 'B\' 'B'
```

Všimněte si, že záhlaví `Test1` je vytištěno pouze jednou, ale v předchozím příkladu bylo dvakrát vytištěno. To znamená, že cíl není v dávce.  V důsledku toho je výstup matoucí odlišně.

Důvodem je, že při použití cílového dávkového zpracování každá cílová dávka provede vše v cíli s vlastní nezávislou kopií všech vlastností a položek, ale když atribut vynecháte `Outputs` , budou jednotlivé řádky ve skupině vlastností považovány za jedinečné, potenciálně dávkové úkoly. V tomto případě `ComponentDir` se úkol dávkuje (používá `%(ItemMetadataName)` syntaxi), takže v době, kdy se `ComponentName` řádek spustí, se obě dávky `ComponentDir` řádku dokončí a druhá z nich určila hodnotu, jak je vidět na druhém řádku.

## <a name="property-functions-using-metadata"></a>Funkce vlastností pomocí metadat

Dávkování lze řídit funkcemi vlastností, které zahrnují metadata. Třeba

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

používá <xref:System.IO.Path.Combine%2A> ke kombinování cesty ke kořenové složce s cestou položky kompilace.

Funkce vlastností se nesmí vyskytovat v hodnotách metadat. Třeba

`%(Compile.FullPath.Substring(0,3))`

není povoleno.

Další informace o funkcích vlastností naleznete v tématu [funkce vlastností](../msbuild/property-functions.md).

## <a name="see-also"></a>Viz také

- [ItemMetadata – – element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md)
