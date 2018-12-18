---
title: Položka Functions | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 85dd03080a9dda58532d656161c3c44ae4943251
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081345"
---
# <a name="item-functions"></a>funkce položek
Od verze MSBuild 4.0, kód v úlohy a cíle může volat funkce položek, chcete-li získat informace o položkách v projektu. Tyto funkce zjednodušují získávání Distinct() položek a jsou rychlejší než položky ve smyčce.  
  
## <a name="string-item-functions"></a>Řetězec funkce položek  
 Provozovat na libovolnou hodnotu položky, můžete použít metody řetězců a vlastností v rozhraní .NET Framework. Pro <xref:System.String> metody, zadejte název metody. Pro <xref:System.String> vlastnosti, zadejte název vlastnosti za "get_".  
  
 U položek, které mají více řetězců řetězec metody nebo vlastnosti běží na jednotlivých řetězců.  
  
 Následující příklad ukazuje, jak používat tyto položky funkce řetězec.  
  
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
  
## <a name="intrinsic-item-functions"></a>Funkce vnitřní položek  
 Následující tabulka uvádí vnitřní funkce, které jsou k dispozici pro položky.  
  
|Funkce|Příklad|Popis|  
|--------------|-------------|-----------------|  
|`Count`|`@(MyItem->Count())`|Vrátí počet položek.|  
|`DirectoryName`|`@(MyItem->DirectoryName())`|Vrátí ekvivalent `Path.DirectoryName` pro každou položku.|  
|`Distinct`|`@(MyItem->Distinct())`|Vrátí položky, které mají odlišné `Include` hodnoty. Metadata se ignoruje. Porovnání velká a malá písmena.|  
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Vrátí položky, které mají odlišné `itemspec` hodnoty. Metadata se ignoruje. Porovnání se rozlišují malá a velká písmena.|  
|`Reverse`|`@(MyItem->Reverse())`|Vrátí položky v obráceném pořadí.|  
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Vrátí `boolean` označující, zda má jakoukoli položku daná metadata název a hodnotu. Porovnání velká a malá písmena.|  
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Vrátí položky s jejich metadat vymazána. Pouze `itemspec` je zachován.|  
|`HasMetadata`|`@(MyItem->HasMetadata("MetadataName"))`|Vrátí položky, které mají název daná metadata. Porovnání velká a malá písmena.|  
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Vrátí hodnoty metadat, které mají název metadat.|  
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue"))`|Vrátí položky, které mají daná metadata název a hodnotu. Porovnání velká a malá písmena.|  
  
 Následující příklad ukazuje, jak používat funkce vnitřní položek.  
  
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
 [Položky](../msbuild/msbuild-items.md)
