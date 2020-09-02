---
title: 'Postupy: určení cíle, který se má sestavit jako první | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7656237be5cf7906293a294885cfa3e6c8bd4e36
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "82072525"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Postupy: určení prvního cíle sestavení

Soubor projektu může obsahovat jeden nebo více `Target` prvků, které definují, jak je projekt sestaven. Modul Microsoft Build Engine (MSBuild) sestaví první cíl, který najde, a všechny závislosti, pokud soubor projektu neobsahuje `DefaultTargets` atribut, `InitialTargets` atribut nebo cíl je zadán na příkazovém řádku pomocí přepínače **-target** .
## <a name="use-the-initialtargets-attribute"></a>Použití atributu InitialTargets

`InitialTargets`Atribut `Project` elementu určuje cíl, který bude spuštěn jako první, a to i v případě, že jsou cíle zadány v příkazovém řádku nebo v `DefaultTargets` atributu.

#### <a name="to-specify-one-initial-target"></a>Určení jednoho počátečního cíle

- Zadejte výchozí cíl v `InitialTargets` atributu `Project` elementu. Příklad:

   `<Project InitialTargets="Clean">`

  Můžete zadat více než jeden počáteční cíl v atributu zobrazením `InitialTargets` cílů v pořadí a použitím středníku pro oddělení jednotlivých cílů. Cíle v seznamu se spustí postupně.

#### <a name="to-specify-more-than-one-initial-target"></a>Určení více než jednoho počátečního cíle

- Seznam počátečních cílů oddělených středníky v `InitialTargets` atributu `Project` elementu. Pokud například chcete spustit `Clean` cíl a potom `Compile` cíl, zadejte:

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>Použití atributu DefaultTargets –

 `DefaultTargets`Atribut `Project` elementu určuje, který cíl nebo cíle jsou vytvořeny, pokud cíl není explicitně zadán na příkazovém řádku. Pokud jsou cíle zadány v atributech `InitialTargets` a `DefaultTargets` i v žádném cíli na příkazovém řádku, nástroj MSBuild spustí cíle zadané v `InitialTargets` atributu následovaný cíli určenými v `DefaultTargets` atributu.

#### <a name="to-specify-one-default-target"></a>Určení jednoho výchozího cíle

- Zadejte výchozí cíl v `DefaultTargets` atributu `Project` elementu. Příklad:

   `<Project DefaultTargets="Compile">`

  Můžete zadat více než jeden výchozí cíl v atributu zobrazením `DefaultTargets` cílů v pořadí a použitím středníku pro oddělení jednotlivých cílů. Cíle v seznamu se spustí postupně.

#### <a name="to-specify-more-than-one-default-target"></a>Určení více než jednoho výchozího cíle

- Seznam výchozích cílů oddělených středníky v `DefaultTargets` atributu `Project` elementu. Pokud například chcete spustit `Clean` cíl a potom `Compile` cíl, zadejte:

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>Použití přepínače-target

 Pokud v souboru projektu není definován výchozí cíl, nebo pokud nechcete použít tento výchozí cíl, můžete zadat jiný cíl pomocí příkazu pro přepínač příkazového řádku **target** . Cíl nebo cíle zadané s přepínačem **target** jsou spuštěny namísto cílů určených `DefaultTargets` atributem. Cíle zadané v `InitialTargets` atributu se vždycky spouštějí jako první.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Použití cíle jiného než výchozího cíle

- Zadejte cíl jako první cíl pomocí přepínače příkazového řádku **-target** . Příklad:

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Použití několika cílů kromě výchozích cílů

- Seznam cílů oddělených středníky nebo čárkami pomocí přepínače příkazového řádku **-target** . Příklad:

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>Viz také

- [Nástroji](../msbuild/msbuild.md)
- [Targets](../msbuild/msbuild-targets.md)
- [Postupy: vyčištění sestavení](../msbuild/how-to-clean-a-build.md)
