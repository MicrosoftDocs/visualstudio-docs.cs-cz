---
title: 'Postupy: rozšíření procesu sestavení | Dokumentace Microsoftu'
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
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e552b75ea5ba34004d0c53850f1af77a120b20cb
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53050254"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Postupy: Rozšíření procesu sestavení sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Procesu sestavení je definován pomocí posloupnosti [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] – soubory .targets, které jsou importovány do souboru projektu. Některý z těchto importovaných souborů webu Microsoft.Common.targets je možné rozšířit, aby bylo možné spouštět vlastní úlohy na několika místech v procesu sestavení. Toto téma vysvětluje, dvě metody, které vám umožní rozšířit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] procesu sestavení:

-   Přepsání konkrétní předdefinovaných cílů, které jsou definované v Microsoft.Common.targets.

-   Přepsání vlastností "DependsOn" definované v Microsoft.Common.targets.

## <a name="overriding-predefined-targets"></a>Přepsání předdefinovaných cílů
 Soubor cílů Microsoft.Common.targets obsahuje sadu předdefinovaných prázdný cílů, které jsou volány před a za některé z hlavních cílů v procesu sestavení. Například [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] volání `BeforeBuild` cíl před hlavním `CoreBuild` cíl a `AfterBuild` cílit po `CoreBuild` cíl. Ve výchozím nastavení prázdný cíle v Microsoft.Common.targets Neprovádět žádnou akci, ale jejich výchozí chování můžete přepsat tak, že definujete, které chcete v souboru projektu, který importuje Microsoft.Common.targets cíle. Díky tomu můžete použít [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] úkoly, které poskytují větší kontrolu nad procesem sestavení.

#### <a name="to-override-a-predefined-target"></a>Chcete-li přepsat předdefinované cíle

1. Identifikujte předdefinované cíle v Microsoft.Common.targets, kterou chcete přepsat. Najdete v následující tabulce pro úplný seznam cílů, které je možné bezpečně přepsat.

2. Definování cíle nebo cílů na konci souboru projektu je třeba bezprostředně před `</Project>` značky. Příklad:

   ```
   <Project>
       ...
       <Target Name="BeforeBuild">
           <!-- Insert tasks to run before build here -->
       </Target>
       <Target Name="AfterBuild">
           <!-- Insert tasks to run after build here -->
       </Target>
   </Project>
   ```

3. Vytváření souboru projektu.

   V následující tabulce jsou uvedeny všech cílů v Microsoft.Common.targets, můžete bez obav přepsat.

|Cílový název|Popis|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Vložit do jednoho z těchto cílů spustit před nebo po dokončení základní kompilace úlohy. Většina nastavení se provádějí v jednom z těchto dva cíle.|
|`BeforeBuild`, `AfterBuild`|Vložit v jednom z těchto cílů spustí před nebo za všechno ostatní v sestavení. **Poznámka:** `BeforeBuild` a `AfterBuild` cíle jsou již definovány v komentářích ke konci většinu souborů projektu. To umožňuje snadno přidat události před instrumentací a po sestavení do souboru projektu.|
|`BeforeRebuild`, `AfterRebuild`|Úlohy vložení v jednom z těchto cílů spustit před nebo po základní znovu sestavit funkcí je vyvolána. Pořadí provádění cílů v Microsoft.Common.targets: `BeforeRebuild`, `Clean`, `Build`a potom `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Vložit v jednom z těchto cílů úlohy spustí před nebo po základní vyčištění funkce vyvolána.|
|`BeforePublish`, `AfterPublish`|Úlohy vložení v jednom z těchto cílů spustit před nebo po publikovat základní funkce, je vyvolána.|
|`BeforeResolveReference`, `AfterResolveReferences`|Úlohy vložen v jednom z těchto cílů spustit před nebo po odkazy na sestavení se vyřeší.|
|`BeforeResGen`, `AfterResGen`|Úlohy vložen v jednom z těchto cílů spustit před nebo po generování prostředků.|

## <a name="overriding-dependson-properties"></a>Přepsání vlastností "DependsOn"
 Přepsání předdefinovaných cílů je snadný způsob, jak rozšíření procesu sestavení, ale protože [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] definice cílů vyhodnocuje postupně, neexistuje žádný způsob, jak zabránit jiný projekt, který importuje projektu z přepsání cíle, které jste již mají přepsat. Tak například poslední `AfterBuild` cíl v souboru projektu po jiné projekty byly naimportovány, bude ten, který se používá během sestavení.

 Můžete chránit před neúmyslným přepsání cílů tak, že přepíšete "DependsOn" vlastnosti, které se používají v `DependsOnTargets` atributů v rámci souboru cílů Microsoft.Common.targets. Například `Build` obsahuje cíl `DependsOnTargets` hodnotu atributu `"$(BuildDependsOn)"`. Vezměte v úvahu:

```
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

 Tato část XML označuje, že před `Build` můžete spustit cíl, všechny cíle zadané v `BuildDependsOn` vlastnosti musí spustit jako první. `BuildDependsOn` Vlastnost je definována jako:

```
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

 Hodnota této vlastnosti můžete přepsat deklarováním jinou vlastnost s názvem `BuildDependsOn` na konci souboru projektu. Zahrnutím předchozí `BuildDependsOn` vlastnost v nové vlastnosti, můžete přidat nového cíle na začátek a konec cílového seznamu. Příklad:

```
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

 Projekty, které importuje soubory projektu můžete přepsat tyto vlastnosti, aniž byste museli přepsat přizpůsobení, které jste provedli.

#### <a name="to-override-a-dependson-property"></a>Chcete-li přepsat vlastnost "DependsOn"

1.  Identifikujte předdefinovanou vlastnost "DependsOn" v Microsoft.Common.targets, kterou chcete přepsat. Najdete v následující tabulce pro seznam vlastností běžně přepsané "DependsOn".

2.  Definujte další instanci vlastnosti nebo vlastnosti na konci souboru projektu. Například obsahovat vlastnost původní `$(BuildDependsOn)`, v nové vlastnosti.

3.  Definujte vlastní cíle před nebo po definici vlastnosti.

4.  Vytváření souboru projektu.

### <a name="commonly-overridden-dependson-properties"></a>Běžně přepisované "DependsOn" vlastnosti

|Název vlastnosti|Popis|
|-------------------|-----------------|
|`BuildDependsOn`|Vlastnost, která má přepsat, pokud chcete vložit vlastní cíle před nebo po dokončení celého sestavení.|
|`CleanDependsOn`|Vlastnost, která má přepsat, pokud chcete vyčistit výstup z vlastního procesu sestavení.|
|`CompileDependsOn`|Vlastnost, která má přepsat, pokud chcete vložit vlastní procesy před nebo po kompilační krok.|

## <a name="see-also"></a>Viz také
 [Integrace se sadou Visual Studio](../msbuild/visual-studio-integration-msbuild.md) [koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md) [. Soubory cíle](../msbuild/msbuild-dot-targets-files.md)
