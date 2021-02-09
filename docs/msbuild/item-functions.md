---
title: Funkce položky | Microsoft Docs
description: Přečtěte si, jak kód MSBuild v úlohách a cílech může volat funkce položky a získat informace o položkách v projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 64759ba2b973c0acf7f2aad20b065fbd99d4d289
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913958"
---
# <a name="item-functions"></a>funkce položek

Kód v úlohách a cílech může volat funkce položek pro získání informací o položkách projektu (v MSBuild 4,0 a novějším). Tyto funkce zjednodušují získání jedinečných položek a jsou rychlejší než procházení položek prostřednictvím smyčky.

## <a name="string-item-functions"></a>Funkce položky řetězce

Můžete použít metody a vlastnosti řetězce v .NET Framework k provozování libovolné hodnoty položky. Pro <xref:System.String> metody zadejte název metody. Pro <xref:System.String> Vlastnosti zadejte název vlastnosti po "get_".

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

|Funkce|Příklad|Description|
|--------------|-------------|-----------------|
|`Count`|`@(MyItem->Count())`|Vrátí počet položek.|
|`DirectoryName`|`@(MyItem->DirectoryName())`|Vrátí ekvivalent `Path.DirectoryName` pro každou položku.|
|`Distinct`|`@(MyItem->Distinct())`|Vrátí položky, které mají odlišné `Include` hodnoty. Metadata se ignorují. V porovnání se nerozlišují malá a velká písmena.|
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Vrátí položky, které mají odlišné `itemspec` hodnoty. Metadata se ignorují. Porovnávání rozlišuje velká a malá písmena.|
|`Reverse`|`@(MyItem->Reverse())`|Vrátí položky v opačném pořadí.|
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Vrátí hodnotu `boolean` určující, zda má nějaká položka název a hodnotu metadat. V porovnání se nerozlišují malá a velká písmena.|
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Vrátí položky s metadaty, které jsou vymazány. `itemspec`Zachová se jenom.|
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

## <a name="msbuild-condition-functions"></a>Funkce podmínky nástroje MSBuild

Funkce `Exists` a `HasTrailingSlash` nejsou funkcemi položky. Jsou k dispozici pro použití s `Condition` atributem. Viz [podmínky nástroje MSBuild](msbuild-conditions.md).

## <a name="see-also"></a>Viz také

- [Položky](../msbuild/msbuild-items.md)
