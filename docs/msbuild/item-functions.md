---
title: Funkce položek | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: af4fb872206611ea5eb1aa93b7aa759615b56e41
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633678"
---
# <a name="item-functions"></a>funkce položek

Kód v úkolech a cílech můžete volat funkce položky získat informace o položkách v projektu (v MSBuild 4.0 a novější). Tyto funkce zjednodušují získávání odlišných položek a jsou rychlejší než opakování položek.

## <a name="string-item-functions"></a>Funkce položky řetězce

Můžete použít metody řetězce a vlastnosti v rozhraní .NET Framework pracovat na libovolnou hodnotu položky. Pro <xref:System.String> metody zadejte název metody. Pro <xref:System.String> vlastnosti zadejte název vlastnosti za "get_".

Pro položky, které mají více řetězců, řetězec metoda nebo vlastnost běží na každém řetězci.

Následující příklad ukazuje, jak používat tyto funkce položky řetězce.

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

## <a name="intrinsic-item-functions"></a>Funkce vnitřní položky

V následující tabulce jsou uvedeny vnitřní funkce, které jsou k dispozici pro položky.

|Funkce|Příklad|Popis|
|--------------|-------------|-----------------|
|`Count`|`@(MyItem->Count())`|Vrátí počet položek.|
|`DirectoryName`|`@(MyItem->DirectoryName())`|Vrátí ekvivalent `Path.DirectoryName` pro každou položku.|
|`Distinct`|`@(MyItem->Distinct())`|Vrátí položky, `Include` které mají odlišné hodnoty. Metadata jsou ignorována. Porovnání je malá a velká písmena.|
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Vrátí položky, `itemspec` které mají odlišné hodnoty. Metadata jsou ignorována. Porovnání rozlišuje malá a velká písmena.|
|`Reverse`|`@(MyItem->Reverse())`|Vrátí položky v opačném pořadí.|
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Vrátí `boolean` a označující, zda má libovolná položka daný název a hodnotu metadat. Porovnání je malá a velká písmena.|
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Vrátí položky s jejich metadata vymazány. Pouze `itemspec` je zachována.|
|`HasMetadata`|`@(MyItem->HasMetadata("MetadataName"))`|Vrátí položky, které mají daný název metadat. Porovnání je malá a velká písmena.|
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Vrátí hodnoty metadat, které mají název metadat.|
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue"))`|Vrátí položky, které mají daný název metadat a hodnotu. Porovnání je malá a velká písmena.|

Následující příklad ukazuje, jak používat vnitřní funkce položky.

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

## <a name="see-also"></a>Viz také

- [Items](../msbuild/msbuild-items.md)
