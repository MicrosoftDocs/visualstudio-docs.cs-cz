---
title: Definice položek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95275f90af0fbf6f002a7e3a127e7d7ca7d08a39
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573778"
---
# <a name="item-definitions"></a>Definice položek
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2,0 umožňuje statické deklaraci položek v souborech projektu pomocí elementu [ItemCollection](../msbuild/itemgroup-element-msbuild.md) . Metadata však mohou být přidána pouze na úrovni položky, i když jsou metadata identická pro všechny položky. Počínaje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3,5 je toto omezení předáno prvkem projektu s názvem [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) . *ItemDefinitionGroup* umožňuje definovat sadu definic položek, které přidávají výchozí hodnoty metadat všem položkám v typu pojmenované položky.

Element *ItemDefinitionGroup* se zobrazí hned po elementu [projektu](../msbuild/project-element-msbuild.md) souboru projektu. Definice položek poskytují následující funkce:

- Můžete definovat globální výchozí metadata pro položky mimo cíl. To znamená, že stejná metadata platí pro všechny položky zadaného typu.

- Typy položek mohou mít více definicí. Při přidání dalších specifikací metadat k typu má přednost poslední specifikace. \(metadata následují po stejném pořadí importu jako vlastnosti.\)

- Metadata lze přidávat. Například hodnoty CDefines se sčítají podmíněně v závislosti na vlastnostech, které se nastavují. Například `MT;STD_CALL;DEBUG;UNICODE`.

- Metadata je možné odebrat.

- Podmínky lze použít k řízení zahrnutí metadat.

## <a name="item-metadata-default-values"></a>Výchozí hodnoty metadat položky
Metadata položky, která jsou definována v ItemDefinitionGroup, jsou pouze deklarace výchozích metadat. Metadata se nevztahují, pokud nedefinujete položku, která používá danou položku, aby obsahovala hodnoty metadat.

> [!NOTE]
> V mnoha příkladech v tomto tématu je zobrazen element ItemDefinitionGroup, ale jeho odpovídající definice objektu Item je vynechána pro přehlednost.

Metadata explicitně definovaná v objektu ItemCollection mají přednost před metadaty v ItemDefinitionGroup. Metadata v ItemDefinitionGroup se aplikují pouze pro nedefinovaná metadata ve více položkách. Příklad:

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

V tomto příkladu se výchozí metadata "m" aplikují na položku "i", protože metadata "m" nejsou explicitně definována položkou "i". Výchozí metadata "n" však nejsou použita na položku "i", protože metadata "n" jsou již definována položkou "i".

> [!NOTE]
> V názvech elementů XML a parametrů jsou rozlišována malá a velká písmena\-. V názvech a položkách\/ch vlastností položky nejsou rozlišována velká a malá písmena\-. Proto by ItemDefinitionGroup položky, které mají názvy, které se liší pouze písmenem Case, měly být považovány za stejné pole Item.

## <a name="value-sources"></a>Zdroje hodnot
Hodnoty metadat, které jsou definovány ve ItemDefinitionGroup, mohou pocházet z mnoha různých zdrojů, a to následujícím způsobem:

- Vlastnost Property

- Položka z ItemDefinitionGroup

- Transformace položky u položky ItemDefinitionGroup

- Proměnná prostředí

- Globální vlastnost (z příkazového řádku *MSBuild. exe* )

- Rezervovaná vlastnost

- Dobře známá metadata položky z ItemDefinitionGroup

- CDATA oddílu \<\!\[CDATA\[cokoli zde není analyzováno\]\]\>

> [!NOTE]
> Metadata položky ze složky Item nejsou užitečná v deklaraci metadat ItemDefinitionGroup, protože prvky ItemDefinitionGroup jsou zpracovávány před prvky Item.

## <a name="additive-and-multiple-definitions"></a>Doplňková a vícenásobná definice
Pokud přidáte definice nebo použijete více ItemDefinitionGroups, pamatujte na následující:

- Do tohoto typu se přidá další specifikace metadat.

- Poslední specifikace má přednost.

Pokud máte více ItemDefinitionGroups, každá další specifikace přidá svá metadata do předchozí definice. Příklad:

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

V tomto příkladu se metadata "o" přidají do "m" a "n".

Kromě toho je možné přidat i dříve definované hodnoty metadat. Příklad:

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

V tomto příkladu se dříve definovaná hodnota pro metadata "m" \(M1\) přidána do nové hodnoty \(m2\), takže konečná hodnota je M1; m2.

> [!NOTE]
> K tomu může dojít také ve stejném ItemDefinitionGroup.

Pokud přepíšete dříve definovaná metadata, má přednost poslední specifikace. V následujícím příkladu poslední hodnota metadat "m" přechází z "M1" na "M1A".

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

## <a name="use-conditions-in-an-itemdefinitiongroup"></a>Použití podmínek v ItemDefinitionGroup
Můžete použít podmínky v ItemDefinitionGroup k řízení zahrnutí metadat. Příklad:

```xml
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
```

V tomto případě je výchozí metadata "M1" u položky "i" obsažena pouze v případě, že hodnota vlastnosti "konfigurace" je "ladit".

> [!NOTE]
> V podmínkách jsou podporovány pouze místní odkazy na metadata.

Odkazy na metadata definovaná v dřívějším ItemDefinitionGroup jsou místní pro položku, nikoli pro skupinu definic. To znamená, že rozsah odkazů je specifický pro položky. Příklad:

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

Ve výše uvedeném příkladu položka "i" odkazuje na položku "test" ve své podmínce. Tato podmínka nebude nikdy pravdivá, protože nástroj MSBuild interpretuje odkaz na metadata jiné položky v ItemDefinitionGroup jako prázdný řetězec. Proto bude "m" nastaven na "M0".

```xml
  <ItemDefinitionGroup>
    <i>
      <m>m0</m>
      <yes>1</yes>
      <m Condition="'%(i.yes)'=='1'">m1</m>
    </i>
  </ItemDefinitionGroup>

```

Ve výše uvedeném příkladu by se hodnota "m" nastavila na hodnotu "M1", protože položka odkazuje na metadata položky "i" pro položku "Ano".

## <a name="override-and-delete-metadata"></a>Přepsat a odstranit metadata
Metadata definovaná v elementu ItemDefinitionGroup lze přepsat v pozdějším elementu ItemDefinitionGroup nastavením hodnoty metadata na prázdnou. Můžete také efektivně odstranit položku metadat tím, že ji nastavíte na prázdnou hodnotu. Příklad:

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

Položka "i" stále obsahuje metadata "m", ale její hodnota je nyní prázdná.

## <a name="scope-of-metadata"></a>Rozsah metadat
ItemDefinitionGroups mají globální rozsah u definovaných a globálních vlastností bez ohledu na jejich definování. Výchozí definice metadat v ItemDefinitionGroup můžou být odkazující samy na sebe. Například následující příklad používá jednoduchou referenci metadat:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(m);m2</m>
    </i>
</ItemDefinitionGroup>
```

Lze také použít kvalifikovaný odkaz na metadata:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(i.m);m2</m>
    </i>
</ItemDefinitionGroup>
```

Následující jsou však neplatné:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>@(x)</m>
    </i>
</ItemDefinitionGroup>
```

Počínaje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3,5 může být ItemGroups také odkazující na sebe. Příklad:

```xml
<ItemGroup>
    <item Include="a">
        <m>m1</m>
        <m>%(m);m2</m>
    </item>
</ItemGroup>
```

## <a name="see-also"></a>Viz také:
- [Dávkování](../msbuild/msbuild-batching.md)
