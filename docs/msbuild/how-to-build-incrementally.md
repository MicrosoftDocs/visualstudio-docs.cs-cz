---
title: 'Postupy: přírůstkové sestavování | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f9e0251d41feb5bd9c61a719d932c6fd954be947
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932426"
---
# <a name="how-to-build-incrementally"></a>Postupy: přírůstkové sestavování
Při sestavování velkých projektů, je důležité nejsou, která dříve vytvořená součásti, které jsou stále aktuální znovu sestavit. Pokud všechny cíle jsou sestaveny pokaždé, když každého sestavení bude trvat dlouhou dobu pro dokončení. Chcete-li povolit přírůstkové buildy (sestavení, ve kterém jen pro tyto cíle, které nejsou sestavené před nebo, zaměřuje jsou zastaralé, jsou znovu sestavit), [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) můžete porovnat časová razítka vstupních souborů s časovými razítky výstupních souborů a zjistěte, jestli se má přeskočit, sestavení nebo částečně znovu sestavit cíl. Musí však být mapování 1: 1 mezi vstupy a výstupy. Použití transformací umožňující cíle k identifikaci této přímé mapování. Další informace o transformace, najdete v části [transformuje](../msbuild/msbuild-transforms.md).  
  
## <a name="specify-inputs-and-outputs"></a>Zadejte vstupy a výstupy  
 Cíl může postupně sestavena, pokud jsou zadané vstupy a výstupy v souboru projektu.  
  
#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>K určení vstupů a výstupů pro cíl  
  
- Použití `Inputs` a `Outputs` atributy `Target` elementu. Příklad:  
  
  ```xml  
  <Target Name="Build"  
      Inputs="@(CSFile)"  
      Outputs="hello.exe">  
  ```  
  
  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] můžete porovnat časová razítka vstupních souborů s časovými razítky výstupních souborů a určit, jestli se má přeskočit, sestavení nebo částečně znovu sestavit cíl. V následujícím příkladu, pokud jakýkoli soubor v `@(CSFile)` seznam položek je novější než *hello.exe* souboru [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] spustí cíl; v opačném případě bude přeskočen:  
  
```xml  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 Když v cíli jsou zadané vstupy a výstupy, každý výstup můžete mapovat pouze jeden vstup nebo může být žádné přímé mapování mezi vstupy a výstupy. V předchozím [CSC – úloha](../msbuild/csc-task.md), například výstupu *hello.exe*, nelze mapovat na jakýkoli jeden vstup - závisí na všechny z nich.  
  
> [!NOTE]
>  Cíl, ve které není žádné přímé mapování mezi vstupy a výstupy vždy sestavovat častěji než cíl, ve kterém každý výstup můžete mapovat pouze jeden vstup protože [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nelze určit výstupy, které je třeba znovu sestavit některých vstupních hodnot změnila-li .  
  
 Úlohy, ve kterých můžete identifikovat přímé mapování mezi vstupů a výstupů, jako [LC – úloha](../msbuild/lc-task.md), jsou nejvhodnější pro přírůstkové sestavení, na rozdíl od úlohy, jako je například [Csc](../msbuild/csc-task.md) a [Vbc –](../msbuild/vbc-task.md), který vytvoří jeden výstupní sestavení z počet vstupů.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá projekt, který vytvoří soubory nápovědy pro hypotetické systému nápovědy. Projekt funguje tak, že převod zdroj *.txt* soubory do zprostředkující *.content* soubory, které pak spolu se soubory XML metadat k vytvoření finální *.help* souboru používá systém nápovědy. Projekt používá hypotetické následující úkoly:  
  
-   `GenerateContentFiles`: Převede *.txt* soubory do *.content* soubory.  
  
-   `BuildHelp`: Kombinuje *.content* soubory a soubory XML metadat k sestavení konečné *.help* souboru.  
  

 Pomocí transformace vytvoří mapování 1: 1 mezi vstupy a výstupy projektu `GenerateContentFiles` úloh. Další informace najdete v tématu [transformuje](../msbuild/msbuild-transforms.md). Navíc `Output` prvek je nastaven na hodnotu automaticky použít výstup z `GenerateContentFiles` úkolu jako vstupy pro `BuildHelp` úloh.  
  
 Tento soubor projektu obsahuje i `Convert` a `Build` cíle. `GenerateContentFiles` a `BuildHelp` úkoly jsou umístěny v `Convert` a `Build` cílí v uvedeném pořadí tak, aby každý cíl je možné sestavit přírůstkově. S použitím `Output` elementu, výstupy `GenerateContentFiles` úloh jsou umístěny v `ContentFile` seznam položek, které lze použít jako vstupy pro `BuildHelp` úloh. Použití `Output` element tímto způsobem automaticky poskytuje výstupy z jednoho úkolu jako vstupy pro jiné úlohy tak, aby nebylo nutné jednotlivé položky seznamu nebo položky seznamů ručně v jednotlivých úkolech.  
  
> [!NOTE]
>  I když `GenerateContentFiles` cílové můžete sestavit přírůstkově, všechny výstupy z tohoto cíle jsou vždy vyžaduje jako vstup pro `BuildHelp` cíl. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] všechny výstupy z jednoho cíle automaticky poskytuje jako vstupy pro jiný cíl při použití `Output` elementu.  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <TXTFile Include="*.txt"/>  
        <XMLFiles Include="\metadata\*.xml"/>  
    </ItemGroup>  
  
    <Target Name = "Convert"  
        Inputs="@(TXTFile)"  
        Outputs="@(TXTFile->'%(Filename).content')">  
  
        <GenerateContentFiles  
            Sources = "@(TXTFile)">  
            <Output TaskParameter = "OutputContentFiles"  
                ItemName = "ContentFiles"/>  
        </GenerateContentFiles>  
    </Target>  
  
    <Target Name = "Build" DependsOnTargets = "Convert"  
        Inputs="@(ContentFiles);@(XMLFiles)"  
        Outputs="$(MSBuildProjectName).help">  
  
        <BuildHelp  
            ContentFiles = "@(ContentFiles)"  
            MetadataFiles = "@(XMLFiles)"  
            OutputFileName = "$(MSBuildProjectName).help"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také:  
 [Cíle](../msbuild/msbuild-targets.md)   
 [Target – element (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Transformace](../msbuild/msbuild-transforms.md)   
 [CSC – úloha](../msbuild/csc-task.md)   
 [Vbc – úloha](../msbuild/vbc-task.md)
