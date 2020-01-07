---
title: Funkce položky | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65ca003375e54248852f5942bd2b5f62fe21a06c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573791"
---
# <a name="item-functions"></a>funkce položek
Počínaje nástrojem MSBuild 4,0 může kód v úlohách a cílech volat funkce položek a získat informace o položkách v projektu. Tyto funkce zjednodušují získání jedinečných položek () a jsou rychlejší než přechází mezi položkami.

## <a name="string-item-functions"></a>Funkce položky řetězce
Můžete použít metody a vlastnosti řetězce v .NET Framework k provozování libovolné hodnoty položky. Pro <xref:System.String> metody zadejte název metody. Pro <xref:System.String> vlastnosti zadejte název vlastnosti za "get_".

Pro položky, které mají více řetězců, je řetězcová metoda nebo vlastnost spuštěna na každém řetězci.

Následující příklad ukazuje, jak použít tyto funkce řetězcové položky.

```xml
<ItemGroup>
    <theItem Include="andromeda;tadpole;cartwheel" />
</ItemGroup>

<Target Name = "go">
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />
    <Message Text="Length   @(theItem->get_Length())" />
    <Message Text="Chars    @(theItem->get_Chars(2))" />
</Target>

  <!--
  Output:
    IndexOf  3;-1;2
    Replace  andromeda;pinwheel;cartwheel
    Length   9;7;9
    Chars    d;d;r
  -->
```

## <a name="intrinsic-item-functions"></a>Funkce vnitřních položek
Následující tabulka uvádí vnitřní funkce dostupné pro položky.

|Funkce|Příklad|Popis|
|--------------|-------------|-----------------|
|`Count`|`@(MyItem->Count())`|Vrátí počet položek.|
|`DirectoryName`|`@(MyItem->DirectoryName())`|Vrátí ekvivalent `Path.DirectoryName` pro každou položku.|
|`Distinct`|`@(MyItem->Distinct())`|Vrátí položky, které mají odlišné hodnoty `Include`. Metadata se ignorují. V porovnání se nerozlišují malá a velká písmena.|
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Vrátí položky, které mají odlišné hodnoty `itemspec`. Metadata se ignorují. Porovnávání rozlišuje velká a malá písmena.|
|`Reverse`|`@(MyItem->Reverse())`|Vrátí položky v opačném pořadí.|
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Vrátí `boolean` k označení, zda má nějaká položka název a hodnotu metadat. V porovnání se nerozlišují malá a velká písmena.|
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Vrátí položky s metadaty, které jsou vymazány. Zachová se jenom `itemspec`.|
|`HasMetadata`|`@(MyItem->HasMetadata("MetadataName"))`|Vrátí položky, které mají daný název metadat. V porovnání se nerozlišují malá a velká písmena.|
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Vrátí hodnoty metadat, které mají název metadat.|
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue"))`|Vrátí položky, které mají zadaný název a hodnotu metadat. V porovnání se nerozlišují malá a velká písmena.|

Následující příklad ukazuje, jak používat funkce vnitřních položek.

```xml
<ItemGroup>
    <TheItem Include="first">
        <Plant>geranium</Plant>
    </TheItem>
    <TheItem Include="second">
        <Plant>algae</Plant>
    </TheItem>
    <TheItem Include="third">
        <Plant>geranium</Plant>
    </TheItem>
</ItemGroup>

<Target Name="go">
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />
    <Message Text=" " />
    <Message Text="Count:   @(theItem->Count())" />
    <Message Text="Reverse: @(theItem->Reverse())" />
</Target>

  <!--
  Output:
    MetaData:    geranium;algae;geranium
    HasMetadata: first;second;third
    WithMetadataValue: first;third

    Count:   3
    Reverse: third;second;first
  -->
```

## <a name="see-also"></a>Viz také:
- [Položky](../msbuild/msbuild-items.md)
