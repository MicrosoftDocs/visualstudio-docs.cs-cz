---
title: Pořadí sestavení cíle | Microsoft Docs
ms.date: 05/02/2019
ms.topic: conceptual
helpviewer_keywords:
- msbuild, build order
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee7a3c2530456a4c2b358fcea7507203feeb904b
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777878"
---
# <a name="target-build-order"></a>Pořadí cílového sestavení

Cíle musí být seřazené, pokud vstup na jeden cíl závisí na výstupu jiného cíle. Pomocí těchto atributů můžete určit pořadí, ve kterém se mají spouštět cíle:

- `InitialTargets`. Tento atribut `Project` určuje cíle, které se spustí jako první, a to i v případě, že jsou cíle zadány na příkazovém řádku nebo v atributu `DefaultTargets`.

- `DefaultTargets`. Tento atribut `Project` určuje, které cíle jsou spuštěny, pokud cíl není explicitně zadán na příkazovém řádku.

- `DependsOnTargets`. Tento atribut `Target` určuje cíle, které musí běžet předtím, než bude možné spustit tento cíl.

- `BeforeTargets` a `AfterTargets`. Tyto atributy `Target` určují, že tento cíl by měl běžet před zadanými cíli nebo po nich (MSBuild 4,0).

Cíl není během sestavení nikdy spuštěn dvakrát, i když na něm závisí další cíl sestavení. Po spuštění cíle je jeho příspěvek k sestavení dokončen.

Cíle mohou mít atribut `Condition`. Pokud je zadaná podmínka vyhodnocena jako `false`, cíl není proveden a nemá na sestavení žádný vliv. Další informace o podmínkách najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).

## <a name="initial-targets"></a>Počáteční cíle

Atribut `InitialTargets` prvku [projektu](../msbuild/project-element-msbuild.md) určuje cíle, které se spustí jako první, a to i v případě, že jsou cíle zadány na příkazovém řádku nebo v atributu `DefaultTargets`. Počáteční cíle se obvykle používají pro kontrolu chyb.

Hodnota atributu `InitialTargets` může být středníkem oddělený seznam cílů. Následující příklad určuje, že cílový `Warm` běží a pak `Eject` cílový běh.

```xml
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Importované projekty mohou mít své vlastní atributy `InitialTargets`. Všechny počáteční cíle jsou agregované dohromady a spouštěny v daném pořadí.

Další informace naleznete v tématu [How to: Určete, který cíl má být sestaven jako první](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="default-targets"></a>Výchozí cíle

Atribut `DefaultTargets` prvku [projektu](../msbuild/project-element-msbuild.md) určuje, který cíl nebo cíle jsou vytvořeny, pokud cíl není explicitně zadán v příkazovém řádku.

Hodnota atributu `DefaultTargets` může být středníkem oddělený seznam výchozích cílů. Následující příklad určuje, že cílový `Clean` běží a pak `Build` cílový běh.

```xml
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Výchozí cíle můžete přepsat pomocí přepínače **-target** na příkazovém řádku. Následující příklad určuje, že cílový `Build` běží a pak `Report` cílový běh. Pokud tímto způsobem určíte cíle, všechny výchozí cíle budou ignorovány.

 `msbuild -target:Build;Report`

Pokud jsou zadány počáteční cíle i výchozí cíle a pokud nejsou zadány žádné cíle příkazového řádku, MSBuild nejprve spustí počáteční cíle a potom spustí výchozí cíle.

Importované projekty mohou mít své vlastní atributy `DefaultTargets`. Byl zjištěn první atribut `DefaultTargets`, který určuje, které výchozí cíle budou spuštěny.

Další informace naleznete v tématu [How to: Určete, který cíl má být sestaven jako první](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="first-target"></a>První cíl

Pokud nejsou k dispozici žádné počáteční cíle, výchozí cíle nebo cíle příkazového řádku, nástroj MSBuild spustí první cíl, který nalezne v souboru projektu nebo v importovaných souborech projektu.

## <a name="target-dependencies"></a>Cílové závislosti

Cíle mohou vzájemně popsat vztahy závislosti. Atribut `DependsOnTargets` označuje, že cíl závisí na jiných cílech. Například

```xml
<Target Name="Serve" DependsOnTargets="Chop;Cook" />
```

informuje MSBuild, že cíl `Serve` závisí na cíli `Chop` a cíli `Cook`. Nástroj MSBuild spustí cíl `Chop` a poté spustí `Cook` cíl před tím, než spustí cíl `Serve`.

## <a name="beforetargets-and-aftertargets"></a>BeforeTargets a AfterTargets

V MSBuild 4,0 můžete zadat cílové pořadí pomocí atributů `BeforeTargets` a `AfterTargets`.

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

Chcete-li vytvořit zprostředkující cíl `Optimize`, který se spustí po cíli `Compile`, ale před cílem `Link`, přidejte následující cíl kdekoli v elementu `Project`.

```xml
<Target Name="Optimize"
    AfterTargets="Compile" BeforeTargets="Link">
    <Message Text="Optimizing" />
</Target>
```

## <a name="determine-the-target-build-order"></a>Určení pořadí cílového sestavení

MSBuild určuje pořadí cílového sestavení následujícím způsobem:

1. `InitialTargets` cílů se spouští.

2. Jsou spuštěny cíle zadané v příkazovém řádku pomocí přepínače **-target** . Pokud na příkazovém řádku neurčíte žádné cíle, `DefaultTargets` cíle se spustí. Pokud není k dispozici žádný, je spuštěn první cíl.

3. Je vyhodnocen atribut `Condition` cíle. Pokud je přítomen atribut `Condition` a je vyhodnocen jako `false`, cíl není proveden a další vliv na sestavení.

   Další cíle, které uvádějí podmíněný cíl ve `BeforeTargets` nebo `AfterTargets` se pořád spouštějí v předepsaném pořadí.

4. Předtím, než je cíl proveden nebo vynechán, jsou spuštěny jeho `DependsOnTargets` cíle, pokud není atribut `Condition` použit pro cíl a vyhodnocen jako `false`.

   > [!NOTE]
   > Cíl se považuje za přeskočený, pokud není proveden, protože jeho výstupní položky jsou aktuální (viz [přírůstkové sestavení](../msbuild/incremental-builds.md)). Tato kontroler se provádí těsně před provedením úkolů uvnitř cíle a nemá vliv na pořadí provádění cílů.

5. Předtím, než se cíl spustí nebo přeskočí, se spustí jakýkoliv jiný cíl, který uvádí cíl v atributu `BeforeTargets`.

6. Před provedením cíle se porovnají jeho atribut `Inputs` a atribut `Outputs`. Pokud nástroj MSBuild zjistí, že všechny výstupní soubory jsou zastaralé vzhledem k odpovídajícímu vstupnímu souboru nebo souborům, spustí nástroj MSBuild cíl. V opačném případě nástroj MSBuild přeskočí cíl.

7. Po spuštění nebo přeskočení cíle se spustí jakýkoli jiný cíl, který je uveden v atributu `AfterTargets`.

## <a name="see-also"></a>Viz také:

- [Cíle](../msbuild/msbuild-targets.md)
