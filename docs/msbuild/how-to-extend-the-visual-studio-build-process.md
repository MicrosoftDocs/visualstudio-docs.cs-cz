---
title: Rozšíření procesu sestavení
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 380933a07636cddd2bc32fb45f14f9b2a65830df
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058269"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Postupy: rozšíření procesu sestavení sady Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Procesu sestavení je definován pomocí posloupnosti [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] *.targets* soubory, které jsou importovány do souboru projektu. Jeden z nich importovat soubory, *cílů Microsoft.Common.targets*, je možné rozšířit, aby bylo možné spouštět vlastní úlohy na několika místech v procesu sestavení. Tento článek vysvětluje, dvě metody, které vám umožní rozšířit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] procesu sestavení:  
  
-   Přepsání konkrétní předdefinovaných cílů, které jsou definovány v *cílů Microsoft.Common.targets*.  
  
-   Přepsání "DependsOn" vlastnosti definované v *cílů Microsoft.Common.targets*.  
  
## <a name="override-predefined-targets"></a>Přepsání předdefinovaných cílů  
 *Cílů Microsoft.Common.targets* soubor obsahuje sadu předdefinovaných cílů prázdný, která je volána před a za některé z hlavních cílů v procesu sestavení. Například [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] volání `BeforeBuild` cíl před hlavním `CoreBuild` cíl a `AfterBuild` cílit po `CoreBuild` cíl. Ve výchozím nastavení, zaměřuje prázdné v *cílů Microsoft.Common.targets* Neprovádět žádnou akci, ale jejich výchozí chování můžete přepsat tak, že definujete cíle, které chcete v souboru projektu, který importuje *cílů Microsoft.Common.targets*. Přepsání předdefinovaných cílů, můžete pomocí [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] úkoly, které poskytují větší kontrolu nad procesem sestavení.  
  
#### <a name="to-override-a-predefined-target"></a>Chcete-li přepsat předdefinované cíle  
  
1.  Identifikujte předdefinované cíle v *cílů Microsoft.Common.targets* , kterou chcete přepsat. Najdete v následující tabulce pro úplný seznam cílů, které je možné bezpečně přepsat.  
  
2.  Definování cíle nebo cílů na konci souboru projektu je třeba bezprostředně před `</Project>` značky. Příklad:  
  
    ```xml  
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
  
3.  Vytváření souboru projektu.  

V následující tabulce jsou uvedeny všechny cíle v *cílů Microsoft.Common.targets* , můžete bez obav přepsat.  
  
|Název cíle|Popis|  
|-----------------|-----------------|  
|`BeforeCompile`, `AfterCompile`|Úlohy, které jsou vloženy do jednoho z těchto cílů spustit před nebo po dokončení základní kompilace. Většina nastavení se provádějí v jednom z těchto dva cíle.|  
|`BeforeBuild`, `AfterBuild`|Úlohy, které jsou vloženy v jednom z těchto cílů se spustí před nebo za všechno ostatní v sestavení. **Poznámka:** `BeforeBuild` a `AfterBuild` cíle jsou již definovány v komentářích ke konci většinu souborů projektu, vám umožňuje snadno přidat události před instrumentací a po sestavení do souboru projektu.|  
|`BeforeRebuild`, `AfterRebuild`|Úlohy, které jsou vloženy v jednom z těchto cílů spustit před nebo po základní znovu sestavit funkcí je vyvolána. Pořadí provádění cílů v *cílů Microsoft.Common.targets* je: `BeforeRebuild`, `Clean`, `Build`a potom `AfterRebuild`.|  
|`BeforeClean`, `AfterClean`|Úlohy, které jsou vloženy v jednom z těchto cílů spustit před nebo po základní vyčištění funkce vyvolána.|  
|`BeforePublish`, `AfterPublish`|Úlohy, které jsou vloženy v jednom z těchto cílů spustit před nebo po základní publikování funkcí je vyvolána.|  
|`BeforeResolveReference`, `AfterResolveReferences`|Úlohy, které jsou vloženy v jednom z těchto cílů spustit před nebo po odkazy na sestavení se vyřeší.|  
|`BeforeResGen`, `AfterResGen`|Úlohy, které jsou vloženy v jednom z těchto cílů spustit před nebo po generování prostředků.|  
  
## <a name="override-dependson-properties"></a>Přepsání vlastností DependsOn  
 Přepsání předdefinovaných cílů je snadný způsob, jak rozšíření procesu sestavení, ale protože [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] definice cílů vyhodnocuje postupně, neexistuje žádný způsob, jak zabránit jiný projekt, který importuje projektu z přepsání cíle, které jste již mají přepsat. Tak například poslední `AfterBuild` cíl v souboru projektu po jiné projekty byly naimportovány, bude ten, který se používá během sestavení.  
  
 Můžete chránit před neúmyslným přepsání cílů tak, že přepíšete DEPENDSON – vlastnosti, které se používají v `DependsOnTargets` atributy v průběhu *cílů Microsoft.Common.targets* souboru. Například `Build` obsahuje cíl `DependsOnTargets` hodnotu atributu `"$(BuildDependsOn)"`. Vezměte v úvahu:  
  
```xml  
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>  
```  
  
 Tato část XML označuje, že před `Build` můžete spustit cíl, všechny cíle zadané v `BuildDependsOn` vlastnosti musí spustit jako první. `BuildDependsOn` Vlastnost je definována jako:  
  
```xml  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Hodnota této vlastnosti můžete přepsat deklarováním jinou vlastnost s názvem `BuildDependsOn` na konci souboru projektu. Zahrnutím předchozí `BuildDependsOn` vlastnost v nové vlastnosti, můžete přidat nového cíle na začátek a konec cílového seznamu. Příklad:  
  
```xml  
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
  
#### <a name="to-override-a-dependson-property"></a>K přepsání vlastností DependsOn  
  
1.  Identifikujte předdefinovanou vlastnost DependsOn v *cílů Microsoft.Common.targets* , kterou chcete přepsat. Najdete v následující tabulce seznam běžně potlačených vlastností DependsOn.  
  
2.  Definujte další instanci vlastnosti nebo vlastnosti na konci souboru projektu. Například obsahovat vlastnost původní `$(BuildDependsOn)`, v nové vlastnosti.  
  
3.  Definujte vlastní cíle před nebo po definici vlastnosti.  
  
4.  Vytváření souboru projektu.  
  
### <a name="commonly-overridden-dependson-properties"></a>Běžně potlačených vlastností DependsOn  
  
|Název vlastnosti|Popis|  
|-------------------|-----------------|  
|`BuildDependsOn`|Vlastnost, která má přepsat, pokud chcete vložit vlastní cíle před nebo po dokončení celého sestavení.|  
|`CleanDependsOn`|Vlastnost, která má přepsat, pokud chcete vyčistit výstup z vlastního procesu sestavení.|  
|`CompileDependsOn`|Vlastnost, která má přepsat, pokud chcete vložit vlastní procesy před nebo po kompilační krok.|  
  
## <a name="see-also"></a>Viz také:  
 [Integrace se sadou Visual Studio](../msbuild/visual-studio-integration-msbuild.md)   
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)   
 [– soubory .targets](../msbuild/msbuild-dot-targets-files.md)