---
title: Cílové pořadí sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/04/2018
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, build order
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13405d197fc5ab64d4c7b7040580f073e36f98c7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812657"
---
# <a name="target-build-order"></a>Pořadí sestavení cílů
Pokud vstup pro jeden cíl závisí na výstupu jiný cíl, musejí být seřazeny cíle. Tyto atributy můžete určit pořadí, ve kterém jsou spuštěny cíle:  
  
- `InitialTargets`. To `Project` atribut určuje cíle, které bude spuštěn jako první, a to i v případě, že cíle jsou zadány v příkazovém řádku nebo v `DefaultTargets` atribut.  
  
- `DefaultTargets`. To `Project` atribut určuje cíle, které jsou spuštěny. Pokud cíl není explicitně zadána na příkazovém řádku.  
  
- `DependsOnTargets`. To `Target` atribut určuje cíle, které musí spustit před spuštěním tohoto cíle.  
  
- `BeforeTargets` a `AfterTargets`. Tyto `Target` atributy určují, že tento cíl by měl spustit před nebo po zadaného cíle (MSBuild 4.0).  
  
  Cíl je nespouštět dvakrát během sestavení, i v případě, že na něm závisí následující cíl v sestavení. Po spuštění cíle svůj příspěvek k sestavení je dokončena.  
  
  Cíle může mít `Condition` atribut. Pokud se zadaná podmínka vyhodnotí jako `false`, cíl není spuštěn a nemá žádný vliv na sestavení. Další informace o podmínkách najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).  
  
## <a name="initial-targets"></a>Počáteční cíle  
 `InitialTargets` Atribut [projektu](../msbuild/project-element-msbuild.md) prvek určuje cíle, které bude spuštěn jako první, i v případě, že cíle jsou zadány v příkazovém řádku nebo v `DefaultTargets` atribut. Počáteční cíle se obvykle používají pro kontrolu chyb.  
  
 Hodnota `InitialTargets` atribut může být oddělený středníkem, seřazený seznam cílů. Následující příklad určuje, že `Warm` cíl spuštění a pak `Eject` cílit na spuštění.  
  
```xml  
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Importované projekty mohou mít své vlastní `InitialTargets` atributy. Všechny počáteční cíle jsou agregovány dohromady a spusťte v uvedeném pořadí.  
  
 Další informace najdete v tématu [jak: Zadejte cíl, které k vytvoření první](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## <a name="default-targets"></a>Výchozí cíle  
 `DefaultTargets` Atribut [projektu](../msbuild/project-element-msbuild.md) element určuje, které cíl nebo cíle jsou sestaveny Pokud cíl není explicitně zadán v příkazovém řádku.  
  
 Hodnota `DefaultTargets` atribut může být oddělený středníkem, seřazený seznam výchozí cíle. Následující příklad určuje, že `Clean` cíl spuštění a pak `Build` cílit na spuštění.  
  
```xml  
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Výchozí cíle lze přepsat pomocí **-target** přepnout na příkazovém řádku. Následující příklad určuje, že `Build` cíl spuštění a pak `Report` cílit na spuštění. Když zadáte cíle tímto způsobem, jsou ignorovány všechny výchozí cíle.  
  
 `msbuild -target:Build;Report`  
  
 Pokud jsou zadané počáteční cíle a výchozí cíle, a pokud nejsou zadány žádné příkazového řádku cíle, MSBuild spustí počáteční cíle nejprve a pak spustí výchozí cíle.  
  
 Importované projekty mohou mít své vlastní `DefaultTargets` atributy. První `DefaultTargets` atribut určí výchozí cíle se spustí.  
  
 Další informace najdete v tématu [jak: Zadejte cíl, které k vytvoření první](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## <a name="first-target"></a>První cíl  
 Pokud nástroj MSBuild spustí první cíl neexistují žádné počáteční cíle, výchozí cíle nebo cílů příkazového řádku, zjistí v souboru projektu nebo libovolný importovaný projekt soubory.  
  
## <a name="target-dependencies"></a>Závislosti cílů  
 Cíle lze popsat vztahů závislosti mezi sebou. `DependsOnTargets` Atribut označuje, že cíl závisí na jiné cíle. Například  
  
```xml  
<Target Name="Serve" DependsOnTargets="Chop;Cook" />  
```  
  
 říká MSBuild, který `Serve` cíl závislý, `Chop` cíl a `Cook` cíl. MSBuild spustí `Chop` cíle a spuštění `Cook` cílit před jejím spuštěním `Serve` cíl.  
  
## <a name="beforetargets-and-aftertargets"></a>BeforeTargets a AfterTargets  
 V MSBuild 4.0, můžete určit pořadí cílů s použitím `BeforeTargets` a `AfterTargets` atributy.  
  
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
  
 K vytvoření přechodného cíle `Optimize` , který spouští po `Compile` cílit, ale předtím, než `Link` cílové, přidejte následující cíl kdekoli v `Project` elementu.  
  
```xml  
<Target Name="Optimize"   
    AfterTargets="Compile" BeforeTargets="Link">  
    <Message Text="Optimizing" />  
</Target>  
```  
  
## <a name="determine-the-target-build-order"></a>Určení pořadí sestavení cílů  
 MSBuild určuje pořadí sestavení cílů následujícím způsobem:  
  
1.  `InitialTargets` cíle jsou spuštěny.  
  
2.  Cíle zadané na příkazovém řádku ve **-target** přepínače jsou spuštěny. Pokud zadáte žádné cíle na příkazovém řádku, pak bude `DefaultTargets` spuštění cíle. Pokud ani jedno je k dispozici, došlo k prvnímu cíli běží.  
  
3.  `Condition` Atribut cíle vyhodnocena. Pokud `Condition` atribut je k dispozici a je vyhodnocena jako `false`, cíl není spuštěn a nemá žádné další vliv na sestavení.

    Cíle, které uvádějí podmíněné cíl `BeforeTargets` nebo `AfterTargets` spustit v předepsané pořadí
  
4.  Předtím, než je cíl proveden nebo vynechán, pokud jeho `Condition` atribut chybí, nebo nevyhodnotil `false`, jeho `DependsOnTargets` spuštění cíle.  
  
5.  Předtím, než je cíl proveden nebo vynechán, všechny cíl, který zobrazí ho v `BeforeTargets` atribut běží.  
  
6.  Před provedením cíl jeho `Inputs` atribut a `Outputs` jsou porovnány atribut. Pokud nástroj MSBuild zjistí, že všechny výstupní soubory jsou aktuální s ohledem na odpovídající vstupní soubor nebo soubory, pak nástroj MSBuild spustí cíl. V opačném případě MSBuild vynechává cíl.  
  
7.  Poté, co je cíl proveden nebo vynechán, všechny cíl, který zobrazí ho v `AfterTargets` atribut běží.  
  
## <a name="see-also"></a>Viz také:  
 [Cíle](../msbuild/msbuild-targets.md)
