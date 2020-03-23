---
title: Cílová objednávka sestavení | Dokumenty společnosti Microsoft
ms.date: 05/02/2019
ms.topic: conceptual
helpviewer_keywords:
- msbuild, build order
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 607584b4b41bdfde224bdb35d30eec1c6c8a4197
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585454"
---
# <a name="target-build-order"></a>Cílová objednávka sestavení

Cíle musí být seřazeny, pokud vstup do jednoho cíle závisí na výstupu jiného cíle. Tyto atributy můžete použít k určení pořadí, ve kterém jsou cíle spuštěny:

- `InitialTargets`. Tento `Project` atribut určuje cíle, které budou spuštěny jako první, i `DefaultTargets` když jsou cíle zadány na příkazovém řádku nebo v atributu.

- `DefaultTargets`. Tento `Project` atribut určuje, které cíle jsou spuštěny, pokud cíl není v příkazovém řádku explicitně zadán.

- `DependsOnTargets`. Tento `Target` atribut určuje cíle, které musí být spuštěny před spuštěním tohoto cíle.

- `BeforeTargets` a `AfterTargets`. Tyto `Target` atributy určují, že tento cíl by měl být spuštěn před nebo za zadané cíle (MSBuild 4.0).

Cíl je nikdy spustit dvakrát během sestavení, i v případě, že závisí na následné cíl v sestavení. Po spuštění cíle je jeho příspěvek k sestavení dokončen.

Cíle mohou `Condition` mít atribut. Pokud zadaná podmínka `false`vyhodnotí , cíl není proveden a nemá žádný vliv na sestavení. Další informace o podmínkách naleznete v tématu [Podmínky](../msbuild/msbuild-conditions.md).

## <a name="initial-targets"></a>Počáteční cíle

Atribut `InitialTargets` [project](../msbuild/project-element-msbuild.md) element určuje cíle, které budou spuštěny jako první, i v `DefaultTargets` případě, že cíle jsou určeny na příkazovém řádku nebo v atributu. Počáteční cíle se obvykle používají pro kontrolu chyb.

Hodnota atributu `InitialTargets` může být středník-oddělené, seřazený seznam cílů. Následující příklad určuje, `Warm` že cíl běží `Eject` a pak se spustí cíl.

```xml
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Importované projekty mohou `InitialTargets` mít své vlastní atributy. Všechny počáteční cíle jsou agregovány společně a spustit v pořadí.

Další informace naleznete v [tématu How to: Specify which target to build first](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="default-targets"></a>Výchozí cíle

Atribut `DefaultTargets` prvku [Project](../msbuild/project-element-msbuild.md) určuje, který cíl nebo cíle jsou vytvořeny, pokud cíl není explicitně zadán v příkazovém řádku.

Hodnota atributu `DefaultTargets` může být středník-oddělený, seřazený seznam výchozích cílů. Následující příklad určuje, `Clean` že cíl běží `Build` a pak se spustí cíl.

```xml
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Výchozí cíle můžete přepsat pomocí přepínače **-target** na příkazovém řádku. Následující příklad určuje, `Build` že cíl běží `Report` a pak se spustí cíl. Zadáte-li cíle tímto způsobem, budou všechny výchozí cíle ignorovány.

 `msbuild -target:Build;Report`

Pokud jsou zadány oba počáteční cíle a výchozí cíle a pokud nejsou zadány žádné cíle příkazového řádku, MSBuild nejprve spustí počáteční cíle a potom spustí výchozí cíle.

Importované projekty mohou `DefaultTargets` mít své vlastní atributy. První `DefaultTargets` zjištěný atribut určuje, které výchozí cíle budou spuštěny.

Další informace naleznete v [tématu How to: Specify which target to build first](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="first-target"></a>První cíl

Pokud neexistují žádné počáteční cíle, výchozí cíle nebo cíle příkazového řádku, pak MSBuild spustí první cíl, se kterým narazí v souboru projektu nebo v jakémkoli importovaném souboru projektu.

## <a name="target-dependencies"></a>Cílové závislosti

Cíle mohou popisovat vzájemné vztahy závislostí. Atribut `DependsOnTargets` označuje, že cíl závisí na jiných cílech. Například:

```xml
<Target Name="Serve" DependsOnTargets="Chop;Cook" />
```

říká MSBuild, `Serve` že cíl `Chop` závisí `Cook` na cíl a cíl. MSBuild spustí `Chop` cíl a potom `Cook` spustí cíl `Serve` před spuštěním cíle.

## <a name="beforetargets-and-aftertargets"></a>Předcíle a AfterTargets

V MSBuild 4.0 můžete určit cílové `BeforeTargets` pořadí `AfterTargets` pomocí atributy a.

Zvažte následující skript.

```xml
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Compile">
        <Message Text="Compiling" />
    </Target>
    <Target Name="Link">
        <Message Text="Linking" />
    </Target>
</Project>
```

Chcete-li vytvořit `Optimize` zprostředkující `Compile` cíl, který `Link` běží za cílem, ale `Project` před cíl, přidejte následující cíl kdekoli v elementu.

```xml
<Target Name="Optimize"
    AfterTargets="Compile" BeforeTargets="Link">
    <Message Text="Optimizing" />
</Target>
```

## <a name="determine-the-target-build-order"></a>Určení pořadí sestavení cíle

MSBuild určuje pořadí sestavení cíl takto:

1. `InitialTargets`cíle jsou řízeny.

2. Cíle určené na příkazovém řádku přepínačem **-target** jsou spuštěny. Pokud na příkazovém řádku nezadáte `DefaultTargets` žádné cíle, budou cíle spuštěny. Pokud ani není k dispozici, pak je spuštěn první cíl zjištěna.

3. Atribut `Condition` cíle je vyhodnocen. Pokud `Condition` je atribut přítomen a `false`vyhodnocuje se na , cíl není proveden a nemá žádný další vliv na sestavení.

   Další cíle, které seznam `BeforeTargets` `AfterTargets` podmíněný cíl v nebo stále provést v předepsaném pořadí.

4. Před provedením cíle nebo přeskočena, jeho `DependsOnTargets` cíle `Condition` jsou spuštěny, pokud atribut `false`je použit a vyhodnotí .

   > [!NOTE]
   > Cíl je považován za přeskočený, pokud není proveden, protože jeho výstupní položky jsou aktuální (viz [přírůstkové sestavení).](../msbuild/incremental-builds.md) Tato kontrola se provádí těsně před provedením úlohy uvnitř cíle a nemá vliv na pořadí provádění cílů.

5. Před provedením nebo přeskočenou cílem je spuštěn jakýkoli `BeforeTargets` jiný cíl, který uvádí cíl v atributu.

6. Před provedením cíle jsou `Inputs` porovnány jeho atribut a `Outputs` atribut. Pokud MSBuild zjistí, že všechny výstupní soubory jsou zastaralé s ohledem na odpovídající vstupní soubor nebo soubory, pak MSBuild provede cíl. V opačném případě MSBuild přeskočí cíl.

7. Po provedení nebo přeskočenou cíl, všechny ostatní cíl, který uvádí v atributu `AfterTargets` je spuštěn.

## <a name="see-also"></a>Viz také

- [Cíle](../msbuild/msbuild-targets.md)
