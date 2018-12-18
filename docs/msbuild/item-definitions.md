---
title: Definice položek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c267c8a0d76fdda08112e428c0fc7403daa1f30
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178559"
---
# <a name="item-definitions"></a>Definice položek
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 umožňuje statických deklarací položky v souborech projektu pomocí [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementu. Však může být přidají metadata pouze na úrovni položek, i v případě, že metadata jsou stejné pro všechny položky. Počínaje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, prvek projektu s názvem [ItemDefinitionGroup –](../msbuild/itemdefinitiongroup-element-msbuild.md) překonává toto omezení. *ItemDefinitionGroup –* umožňuje definovat sadu definice položek, které přidávají výchozí hodnoty metadat pro všechny položky v typu s názvem položky.  
  
 *ItemDefinitionGroup –* elementu se zobrazí okamžitě po [projektu](../msbuild/project-element-msbuild.md) prvek souboru projektu. Definice položek poskytují následující funkce:  
  
-   Můžete definovat globální výchozí nastavení metadat pro položky mimo cíl. To znamená na stejná metadata platí pro všechny položky zadaného typu.  
  
-   Typy položek může mít několik definic. Při přidání dalších metadat specifikace typu, poslední specifikace přednost. \(Metadata se řídí stejným pořadím importu následujícím způsobem vlastnosti.\)  
  
-   Může být metadata sčítání. Například jsou hodnoty CDefines shromážděna podmíněně, v závislosti na vlastnosti, které jsou nastavena. Například `MT;STD_CALL;DEBUG;UNICODE`.  
  
-   Metadata se dá odebrat.  
  
-   Podmínky lze použít k řízení zahrnutí metadat.  
  
## <a name="item-metadata-default-values"></a>Položka metadat výchozí hodnoty  
 Metadata položky, která je definována v ItemDefinitionGroup – je jenom deklarace výchozí metadat. Metadata nelze použít, dokud nedefinujete položku, která se používá ItemGroup tak, aby obsahovala hodnoty metadat.  
  
> [!NOTE]
>  V mnoha příkladech v tomto tématu se zobrazí ItemDefinitionGroup – element, ale pro přehlednost je vynecháno jeho odpovídající ItemGroup definici.  
  
 Metadata explicitně definované v ItemGroup má přednost před metadat v ItemDefinitionGroup –. Metadata v ItemDefinitionGroup – platí jenom pro nedefinovaný metadata ItemGroup. Příklad:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>        
</ItemDefinitionGroup>  
<ItemGroup>  
    <i Include="a">  
        <o>o1</o>  
        <n>n2</n>  
    </i>  
</ItemGroup>  
```  
  
 V tomto příkladu je použít výchozí metadat "m" k položce "i", protože metadata "m" není explicitně určené položky "i". Výchozí metadat "n" však není použít k položce "i", protože metadata "n" je již definován položky "i".  
  
> [!NOTE]
>  Názvy – Element XML a parametru jsou případ\-citlivé. Položka metadat a položky\/názvy vlastností nejsou případu\-citlivé. ItemDefinitionGroup – položky, které mají názvy, které se liší pouze velikostí písma proto mají být považována za stejné ItemGroup.  
  
## <a name="value-sources"></a>Hodnota zdroje  
 Hodnoty pro metadata, která je definována v ItemDefinitionGroup – mohou pocházet z mnoha různých zdrojů, následujícím způsobem:  
  
-   PropertyGroup – vlastnost  
  
-   Položku ze ItemDefinitionGroup –  
  
-   Položka transformaci ItemDefinitionGroup – položky  
  
-   Proměnná prostředí  
  
-   Global – vlastnost (z *MSBuild.exe* příkazového řádku)  
  
-   Rezervované vlastnosti  
  
-   Metadata známé na položku ze ItemDefinitionGroup –  
  
-   Oddíl CDATA \< \! \[CDATA\[nic tady není analyzovat\]\]\>  
  
> [!NOTE]
>  Metadata položky ze ItemGroup není užitečné při deklaraci ItemDefinitionGroup – metadat, protože ItemDefinitionGroup – prvky se zpracovávají před ItemGroup prvky.  
  
## <a name="additive-and-multiple-definitions"></a>Additive a několik definic  
 Při přidávání definic nebo používání více ItemDefinitionGroups, mějte na paměti následující:  
  
-   Specifikace další metadata se přidá do typu.  
  
-   Poslední specifikace přednost.  
  
Pokud máte více ItemDefinitionGroups, každé následné specifikace přidá jeho metadata do předchozí definice. Příklad:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <o>o1</o>  
    </i>  
</ItemDefinitionGroup>  
```  
  
V tomto příkladu se přidají metadata "o" a "m", "n".  
  
Kromě toho je možné přidat také hodnoty dříve definovaná metadata. Příklad:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
V tomto příkladu, dříve definovanou hodnotu pro metadata "m" \(m1\) přidá novou hodnotu \(m2\), tak, aby konečná hodnota "m1; m2".  
  
> [!NOTE]
>  Tato situace může také nastat ve stejném ItemDefinitionGroup –.  
  
Při přepsání dříve definovaných metadat poslední specifikace přednost. V následujícím příkladu přejde konečná hodnota metadat "m" z "m1" na "m1a".  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>m1a</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
## <a name="use-conditions-in-an-itemdefinitiongroup"></a>Podmínky použití v ItemDefinitionGroup –  
 Podmínky v ItemDefinitionGroup – slouží k řízení zahrnutí metadat. Příklad:  
  
```xml  
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
V takovém případě je součástí výchozí metadat "m1" položka "i", pouze v případě, že hodnota vlastnosti "Konfigurace" je "Debug".  
  
> [!NOTE]
>  V podmínkách jsou podporovány pouze odkazy na místních metadat.  
  
Odkazy na metadata definované v předchozích ItemDefinitionGroup – jsou místní položka není definice skupiny. To znamená oboru odkazů jsou specifické pro položku. Příklad:  
  
```xml  
<ItemDefinitionGroup>  
    <test>  
        <yes>1</yes>  
    </test>  
    <i> 
        <m>m0</m>
        <m Condition="'%(test.yes)'=='1'">m1</m>  
    </i>  
</ItemDefinitionGroup>  
  
```  
  
V příkladu výše položka "i" odkazuje na položku "test" v jeho stavu. Tento stav bude nikdy hodnotu true, protože MSBuild interpretuje odkaz na další položku metadat v ItemDefinitionGroup – jako prázdný řetězec. Proto se nastavuje "m" k "m0."
 
```xml 
  <ItemDefinitionGroup>
    <i>
      <m>m0</m>
      <yes>1</yes>
      <m Condition="'%(i.yes)'=='1'">m1</m>
    </i>
  </ItemDefinitionGroup>

```

V příkladu výše, "m" se nastavuje na hodnotu "m1" jako odkazy na podmínky položky "i". hodnota metadat pro položku "Ano". 
  
## <a name="override-and-delete-metadata"></a>Přepsat a odstranění metadat  
 Metadata definované v ItemDefinitionGroup – element lze přepsat v pozdější ItemDefinitionGroup – element tak, že nastavíte hodnotu metadat na prázdnou hodnotu. Můžete také fakticky odstranit položku metadat nastavením na prázdnou hodnotu. Příklad:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m></m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
Položka "i" stále obsahuje metadata "m", ale její hodnota je prázdná.  
  
## <a name="scope-of-metadata"></a>Obor metadat  
 ItemDefinitionGroups mají globální rozsah na definované a globální vlastnosti, bez ohledu na to jsou definovány. Výchozí definice metadat v ItemDefinitionGroup – můžete používat referenci na sebe. Následující příklad používá odkaz na jednoduché metadata:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
Odkaz na kvalifikovaný metadata je také možné:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
      <m>m1</m>  
      <m>%(i.m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
Nicméně toto není platná:  
  
```xml  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>@(x)</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
Počínaje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, ItemGroups může být také odkazující na sebe. Příklad:  
  
```xml  
<ItemGroup>  
    <item Include="a">  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </item>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Viz také:  
 [Dávkové zpracování](../msbuild/msbuild-batching.md)
