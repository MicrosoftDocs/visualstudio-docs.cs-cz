---
title: Položka Functions | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 687d740a379bd3b04bd47d0d2e3111bb71e7934d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207919"
---
# <a name="item-functions"></a>Funkce položek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Od verze MSBuild 4.0, kód v úlohy a cíle může volat funkce položek, chcete-li získat informace o položkách v projektu. Tyto funkce zjednodušují získávání Distinct() položek a jsou rychlejší než položky ve smyčce.  
  
## <a name="string-item-functions"></a>Řetězec funkce položek  
 Provozovat na libovolnou hodnotu položky, můžete použít metody řetězců a vlastností v rozhraní .NET Framework. Pro <xref:System.String> metody, zadejte název metody. Pro <xref:System.String> vlastnosti, zadejte název vlastnosti za "get_".  
  
 U položek, které mají více řetězců řetězec metody nebo vlastnosti běží na jednotlivých řetězců.  
  
 Následující příklad ukazuje, jak používat tyto položky funkce řetězec.  
  
```  
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
|`HasMetadata`|`@(MyItem->HasMetadataValue("MetadataName")`|Vrátí položky, které mají název daná metadata. Porovnání velká a malá písmena.|  
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Vrátí hodnoty metadat, které mají název metadat.|  
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue")`|Vrátí položky, které mají daná metadata název a hodnotu. Porovnání velká a malá písmena.|  
  
 Následující příklad ukazuje, jak používat funkce vnitřní položek.  
  
```  
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
 [Položky](../msbuild/msbuild-items.md)



