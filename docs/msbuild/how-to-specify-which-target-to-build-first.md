---
title: 'Postup: Určení cíle, který chcete sestavit jako první | Dokumenty společnosti Microsoft'
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
ms.sourcegitcommit: 0b8497b720eb06bed8ce2194731177161b65eb84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82072525"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Postup: Určete, který cíl má být sestavován jako první

Soubor projektu může obsahovat `Target` jeden nebo více prvků, které definují způsob vytvoření projektu. Modul Microsoft Build Engine (MSBuild) vytvoří první cíl, který najde, a všechny `DefaultTargets` závislosti, `InitialTargets` pokud soubor projektu obsahuje atribut, atribut nebo cíl je určen na příkazovém řádku pomocí **přepínače -target.**
## <a name="use-the-initialtargets-attribute"></a>Použití atributu InitialTargets

Atribut `InitialTargets` `Project` prvku určuje cíl, který bude spuštěn jako první, i když jsou `DefaultTargets` cíle zadány na příkazovém řádku nebo v atributu.

#### <a name="to-specify-one-initial-target"></a>Určení jednoho počátečního cíle

- Zadejte výchozí cíl `InitialTargets` v `Project` atributu prvku. Příklad:

   `<Project InitialTargets="Clean">`

  Můžete zadat více než jeden `InitialTargets` počáteční cíl v atributu výpis cíle v pořadí a pomocí středníku oddělit každý cíl. Cíle v seznamu budou spuštěny postupně.

#### <a name="to-specify-more-than-one-initial-target"></a>Určení více než jednoho počátečního cíle

- V `InitialTargets` atributu `Project` prvku uveďte počáteční cíle oddělené středníky. Chcete-li například `Clean` spustit cíl `Compile` a pak cíl, zadejte:

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>Použití atributu DefaultTargets

 Atribut `DefaultTargets` `Project` prvku určuje, který cíl nebo cíle jsou vytvořeny, pokud cíl není zadán explicitně na příkazovém řádku. Pokud jsou cíle `InitialTargets` zadány `DefaultTargets` v atributech a na příkazovém řádku není zadán žádný `InitialTargets` cíl, msbuild `DefaultTargets` spustí cíle zadané v atributu následované cíli zadanými v atributu.

#### <a name="to-specify-one-default-target"></a>Určení jednoho výchozího cíle

- Zadejte výchozí cíl `DefaultTargets` v `Project` atributu prvku. Příklad:

   `<Project DefaultTargets="Compile">`

  Můžete zadat více než jeden `DefaultTargets` výchozí cíl v atributu výpis cíle v pořadí a pomocí středníku oddělit každý cíl. Cíle v seznamu budou spuštěny postupně.

#### <a name="to-specify-more-than-one-default-target"></a>Určení více než jednoho výchozího cíle

- V `DefaultTargets` atributu `Project` prvku uveďte výchozí cíle oddělené středníky. Chcete-li například `Clean` spustit cíl `Compile` a pak cíl, zadejte:

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>Použití přepínače -target

 Pokud výchozí cíl není definován v souboru projektu nebo pokud nechcete použít tento výchozí cíl, můžete použít příkazový řádek přepínač **-target** k určení jiného cíle. Cíl nebo cíle zadané pomocí **přepínače -target** jsou spuštěny namísto cílů určených atributem. `DefaultTargets` Cíle zadané `InitialTargets` v atributu jsou vždy spuštěny jako první.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>První použití jiného než výchozího cíle

- Zadejte cíl jako první cíl pomocí přepínače příkazového řádku **-target.** Příklad:

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>První použití několika cílů než výchozích cílů

- Seznam cílů oddělených středníky nebo čárkami pomocí přepínače příkazového řádku **-target.** Příklad:

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>Viz také

- [MSBuild](../msbuild/msbuild.md)
- [Cíle](../msbuild/msbuild-targets.md)
- [Postup: Čištění sestavení](../msbuild/how-to-clean-a-build.md)
