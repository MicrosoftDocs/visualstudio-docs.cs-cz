---
title: Pořadí sestavení cíle | Microsoft Docs
description: Zjistěte, jak určit pořadí, ve kterém jsou spuštěny cíle nástroje MSBuild, pokud vstup na jeden cíl závisí na výstupu jiného cíle.
ms.custom: SEO-VS-2020
ms.date: 05/02/2019
ms.topic: conceptual
helpviewer_keywords:
- msbuild, build order
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 873f669890e84281f73a96fa1739d267c10e83a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966133"
---
# <a name="target-build-order"></a>Pořadí sestavení cílů

Cíle musí být seřazené, pokud vstup na jeden cíl závisí na výstupu jiného cíle. Pomocí těchto atributů můžete určit pořadí, ve kterém se mají spouštět cíle:

- `InitialTargets`. Tento `Project` atribut určuje cíle, které se spustí jako první, a to i v případě, že jsou cíle zadány na příkazovém řádku nebo v `DefaultTargets` atributu.

- `DefaultTargets`. Tento `Project` atribut určuje, které cíle jsou spuštěny, pokud cíl není explicitně zadán na příkazovém řádku.

- `DependsOnTargets`. Tento `Target` atribut určuje cíle, které musí běžet předtím, než bude možné spustit tento cíl.

- `BeforeTargets` a `AfterTargets` . Tyto `Target` atributy určují, že tento cíl by měl běžet před zadanými cíli nebo po nich (MSBuild 4,0).

Cíl není během sestavení nikdy spuštěn dvakrát, i když na něm závisí další cíl sestavení. Po spuštění cíle je jeho příspěvek k sestavení dokončen.

Cíle mohou mít `Condition` atribut. Pokud je zadaná podmínka vyhodnocena jako `false` , cíl není proveden a nemá na sestavení žádný vliv. Další informace o podmínkách najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).

## <a name="initial-targets"></a>Počáteční cíle

`InitialTargets`Atribut prvku [projektu](../msbuild/project-element-msbuild.md) určuje cíle, které se spustí jako první, a to i v případě, že jsou cíle zadány na příkazovém řádku nebo v `DefaultTargets` atributu. Počáteční cíle se obvykle používají pro kontrolu chyb.

Hodnota `InitialTargets` atributu může být středníkem oddělený seznam cílů. Následující příklad určuje, že `Warm` cílový běh a pak `Eject` cílové spuštění.

```xml
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Importované projekty mohou mít své vlastní `InitialTargets` atributy. Všechny počáteční cíle jsou agregované dohromady a spouštěny v daném pořadí.

Další informace naleznete v tématu [How to: Určete, který cíl má být sestaven jako první](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="default-targets"></a>Výchozí cíle

`DefaultTargets`Atribut prvku [projektu](../msbuild/project-element-msbuild.md) určuje, který cíl nebo cíle jsou vytvořeny, pokud cíl není explicitně zadán v příkazovém řádku.

Hodnota `DefaultTargets` atributu může být středníkem oddělený seznam výchozích cílů. Následující příklad určuje, že `Clean` cílový běh a pak `Build` cílové spuštění.

```xml
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Výchozí cíle můžete přepsat pomocí přepínače **-target** na příkazovém řádku. Následující příklad určuje, že `Build` cílový běh a pak `Report` cílové spuštění. Pokud tímto způsobem určíte cíle, všechny výchozí cíle budou ignorovány.

 `msbuild -target:Build;Report`

Pokud jsou zadány počáteční cíle i výchozí cíle a pokud nejsou zadány žádné cíle příkazového řádku, MSBuild nejprve spustí počáteční cíle a potom spustí výchozí cíle.

Importované projekty mohou mít své vlastní `DefaultTargets` atributy. První `DefaultTargets` nalezený atribut určuje, které výchozí cíle budou spuštěny.

Další informace naleznete v tématu [How to: Určete, který cíl má být sestaven jako první](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="first-target"></a>První cíl

Pokud nejsou k dispozici žádné počáteční cíle, výchozí cíle nebo cíle příkazového řádku, nástroj MSBuild spustí první cíl, který nalezne v souboru projektu nebo v importovaných souborech projektu.

## <a name="target-dependencies"></a>Cílové závislosti

Cíle mohou vzájemně popsat vztahy závislosti. `DependsOnTargets`Atribut označuje, že cíl závisí na jiných cílech. Třeba

```xml
<Target Name="Serve" DependsOnTargets="Chop;Cook" />
```

informuje MSBuild, že `Serve` cíl závisí na `Chop` cíli a `Cook` cíli. Nástroj MSBuild spustí `Chop` cíl a poté spustí `Cook` cíl před tím, než spustí `Serve` cíl.

## <a name="beforetargets-and-aftertargets"></a>BeforeTargets a AfterTargets

V MSBuild 4,0 můžete zadat cílové pořadí pomocí `BeforeTargets` `AfterTargets` atributů a.

Vezměte v úvahu následující skript.

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

Chcete-li vytvořit zprostředkující cíl, `Optimize` který bude spuštěn po `Compile` cíli, ale před `Link` cílem, přidejte následující cíl kdekoli v `Project` elementu.

```xml
<Target Name="Optimize"
    AfterTargets="Compile" BeforeTargets="Link">
    <Message Text="Optimizing" />
</Target>
```

## <a name="determine-the-target-build-order"></a>Určení pořadí cílového sestavení

MSBuild určuje pořadí cílového sestavení následujícím způsobem:

1. `InitialTargets` cíle jsou spuštěny.

2. Jsou spuštěny cíle zadané v příkazovém řádku pomocí přepínače **-target** . Pokud na příkazovém řádku neurčíte žádné cíle, budou se tyto `DefaultTargets` cíle spouštět. Pokud není k dispozici žádný, je spuštěn první cíl.

3. `Condition`Atribut cíle je vyhodnocen. Pokud `Condition` je přítomen atribut a je vyhodnocen jako `false` , cíl není proveden a další vliv na sestavení.

   Další cíle, které uvádějí podmíněný cíl v `BeforeTargets` nebo `AfterTargets` stále spouštěné v předepsaném pořadí.

4. Předtím, než je cíl proveden nebo vynechán, `DependsOnTargets` se spustí jeho cíle, pokud `Condition` atribut není použit pro cíl a vyhodnocen jako `false` .

   > [!NOTE]
   > Cíl se považuje za přeskočený, pokud není proveden, protože jeho výstupní položky jsou aktuální (viz [přírůstkové sestavení](../msbuild/incremental-builds.md)). Tato kontroler se provádí těsně před provedením úkolů uvnitř cíle a nemá vliv na pořadí provádění cílů.

5. Předtím, než se cíl spustí nebo přeskočí, se spustí jakýkoliv jiný cíl, který uvádí cíl v `BeforeTargets` atributu.

6. Před provedením cíle je porovnán jeho `Inputs` atribut a atribut `Outputs` . Pokud nástroj MSBuild zjistí, že všechny výstupní soubory jsou zastaralé vzhledem k odpovídajícímu vstupnímu souboru nebo souborům, spustí nástroj MSBuild cíl. V opačném případě nástroj MSBuild přeskočí cíl.

7. Po spuštění nebo přeskočení cíle se spustí jakýkoli jiný cíl, který je uveden v `AfterTargets` atributu.

## <a name="see-also"></a>Viz také

- [Targets](../msbuild/msbuild-targets.md)
