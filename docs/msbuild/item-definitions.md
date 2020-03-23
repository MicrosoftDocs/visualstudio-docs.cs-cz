---
title: Definice položek | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 18d6a2a30af4fb29a8d9e924c44c1570ff1efe29
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633704"
---
# <a name="item-definitions"></a>Definice položek

MSBuild 2.0 umožňuje statickou deklaraci položek v souborech projektu pomocí [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementu. Metadata však mohou být přidána pouze na úrovni položky, i v případě, že metadata jsou shodná pro všechny položky. Počínaje MSBuild 3.5, prvek projektu s názvem [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) překonává toto omezení. *ItemDefinitionGroup* umožňuje definovat sadu definic položek, které přidávají výchozí hodnoty metadat ke všem položkám v pojmenovaném typu položky.

Prvek *ItemDefinitionGroup* se zobrazí bezprostředně za elementem [Project](../msbuild/project-element-msbuild.md) souboru projektu. Definice položek poskytují následující funkce:

- Můžete definovat globální výchozí metadata pro položky mimo cíl. To znamená, že stejná metadata platí pro všechny položky zadaného typu.

- Typy položek mohou mít více definic. Při přidání další specifikace metadat k typu, poslední specifikace má přednost. \(Metadata se řídí stejným pořadím importu jako vlastnosti.\)

- Metadata mohou být aditivní. Například CDefines hodnoty jsou akumulovány podmíněně, v závislosti na vlastnosti, které jsou nastaveny. Například, `MT;STD_CALL;DEBUG;UNICODE`.

- Metadata lze odebrat.

- Podmínky lze použít k řízení zahrnutí metadat.

## <a name="item-metadata-default-values"></a>Výchozí hodnoty metadat položky

Metadata položky, která je definována v ItemDefinitionGroup je pouze deklarace výchozí metadata. Metadata se nepoužijí, pokud nedefinujete položku, která používá Skupinu položek k obsahující hodnoty metadat.

> [!NOTE]
> V mnoha příkladech v tomto tématu itemdefinitiongroup prvek je zobrazen, ale jeho odpovídající ItemGroup definice je vynechán pro přehlednost.

Metadata explicitně definovaná v ItemGroup má přednost před metadaty v ItemDefinitionGroup. Metadata v ItemDefinitionGroup se použijí pouze pro nedefinovaná metadata ve skupině itemgroup. Například:

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

V tomto příkladu je výchozí metadata "m" použita pro položku "i", protože metadata "m" nejsou explicitně definována položkou "i". Výchozí metadata "n" se však nepoužijí na položku "i", protože metadata "n" jsou již definována položkou "i".

> [!NOTE]
> Názvy elementů XML\-a parametrů rozlišují malá a velká písmena. Metadata položky\/a názvy\-vlastností položky nerozlišují malá a velká písmena. Proto ItemDefinitionGroup položky, které mají názvy, které se liší pouze podle případu by měly být považovány za stejné ItemGroup.

## <a name="value-sources"></a>Zdroje hodnot

Hodnoty pro metadata, která je definována v ItemDefinitionGroup může pocházet z mnoha různých zdrojů, takto:

- Vlastnost PropertyGroup

- Položka z itemdefinitiongroup

- Transformace položky u položky ItemDefinitionGroup

- Proměnná prostředí

- Globální vlastnost (z příkazového řádku *MSBuild.exe)*

- Rezervovaná vlastnost

- Známá metadata položky z itemdefinitiongroup

- CDATA \< \! \[sekce\[CDATA nic zde není analyzováno\]\]\>

> [!NOTE]
> Metadata položky z ItemGroup není užitečná v deklaraci metadat ItemDefinitionGroup, protože prvky ItemDefinitionGroup jsou zpracovány před prvky ItemGroup.

## <a name="additive-and-multiple-definitions"></a>Doplňkové látky a více definic

Při přidávání definic nebo použití více ItemDefinitionGroups, nezapomeňte následující:

- K typu je přidána další specifikace metadat.

- Poslední specifikace má přednost.

Pokud máte více ItemDefinitionGroups, každá následující specifikace přidá jeho metadata do předchozí definice. Například:

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

V tomto příkladu metadata "o" je přidán do "m" a "n".

Kromě toho lze také přidat dříve definované hodnoty metadat. Například:

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

V \(tomto příkladu je k nové hodnotě\) \(m2\)přidána dříve definovaná hodnota metadat "m" m1 , takže konečná hodnota je "m1;m2".

> [!NOTE]
> K tomu může dojít také ve stejné ItemDefinitionGroup.

Když přepíšete dříve definovaná metadata, má přednost poslední specifikace. V následujícím příkladu konečná hodnota metadat "m" přejde z "m1" na "m1a".

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

Podmínky v ItemDefinitionGroup můžete použít k řízení zahrnutí metadat. Například:

```xml
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
```

V tomto případě výchozí metadata "m1" na položku "i" je zahrnuta pouze v případě, že hodnota "Configuration" vlastnost je "Ladění".

> [!NOTE]
> V podmínkách jsou podporovány pouze místní odkazy na metadata.

Odkazy na metadata definovaná v dřívější skupině ItemDefinitionGroup jsou místní pro položku, nikoli pro skupinu definic. To znamená, že rozsah odkazů jsou specifické pro položku. Například:

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

Ve výše uvedeném příkladu položka "i" odkazuje na položku "test" v její stavu. Tato podmínka nikdy nebude splněna, protože MSBuild interpretuje odkaz na metadata jiné položky v ItemDefinitionGroup jako prázdný řetězec. Proto "m" by být nastavena na "m0."

```xml
  <ItemDefinitionGroup>
    <i>
      <m>m0</m>
      <yes>1</yes>
      <m Condition="'%(i.yes)'=='1'">m1</m>
    </i>
  </ItemDefinitionGroup>

```

Ve výše uvedeném příkladu "m" by být nastavena na hodnotu "m1" jako podmínka odkazuje na položku "i" je hodnota metadat pro položku "ano".

## <a name="override-and-delete-metadata"></a>Přepsání a odstranění metadat

Metadata definovaná v elementu ItemDefinitionGroup mohou být přepsána v pozdějším elementu ItemDefinitionGroup nastavením hodnoty metadat na jinou hodnotu. Můžete také efektivně odstranit položku metadat nastavením na prázdnou hodnotu. Například:

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

ItemDefinitionGroups mají globální rozsah na definované a globální vlastnosti, ať jsou definovány. Výchozí definice metadat v ItemDefinitionGroup může být rereferential. Následující používá například jednoduchý odkaz na metadata:

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

Následující však není platný:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>@(x)</m>
    </i>
</ItemDefinitionGroup>
```

Počínaje MSBuild 3.5, ItemGroups může být také rereferential. Například:

```xml
<ItemGroup>
    <item Include="a">
        <m>m1</m>
        <m>%(m);m2</m>
    </item>
</ItemGroup>
```

## <a name="see-also"></a>Viz také

- [Dávkování](../msbuild/msbuild-batching.md)
