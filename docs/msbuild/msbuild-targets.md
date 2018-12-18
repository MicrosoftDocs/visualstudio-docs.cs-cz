---
title: Cíle nástroje MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, targets
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3700074a1d087c0626a86559ff1342698d8a4628
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176110"
---
# <a name="msbuild-targets"></a>Cíle nástroje MSBuild
Cíle seskupují úkoly v určitém pořadí a povolit procesu sestavení, abychom promítnout do menších jednotek. Například jeden cíl může odstranit všechny soubory ve výstupním adresáři připravit pro sestavení, zatímco jiné zkompiluje vstupy pro projekt a umístí je do prázdného adresáře. Další informace o úlohách najdete v části [úlohy](../msbuild/msbuild-tasks.md).  
  
## <a name="declare-targets-in-the-project-file"></a>Deklarovat cíle v souboru projektu  
 Cíle jsou deklarovány v souboru projektu se [cílové](../msbuild/target-element-msbuild.md) elementu. Například následující XML kód vytvoří cíl s názvem konstrukce, která potom volá CSC – úloha s typem položky kompilace.  
  
```xml  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 Stejně jako vlastnosti nástroje MSBuild lze redefinovat cíle. Například  
  
```xml  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 Pokud AfterBuild spustí, zobrazí se pouze "druhého výskytu".  
  
## <a name="target-build-order"></a>Pořadí sestavení cílů  
 Pokud vstup pro jeden cíl závisí na výstupu jiný cíl, musejí být seřazeny cíle. Existuje několik způsobů, jak určit pořadí, ve které cíle spuštění.  
  
-   Počáteční cíle  
  
-   Výchozí cíle  
  
-   První cíl  
  
-   Závislosti cílů  
  
-   `BeforeTargets` a `AfterTargets` (MSBuild 4.0)  

Cíl se nikdy nespustí dvakrát během jednoho sestavení, i v případě, že na něm závisí následující cíl v sestavení. Jakmile se spustí cíl, jeho příspěvku k sestavení je dokončena.  

Pořadí sestavení, podrobnosti a další informace o cíli, najdete v části [pořadí sestavení cílové](../msbuild/target-build-order.md).  

## <a name="target-batching"></a>Dávkování cíle  
Cílový prvek může mít `Outputs` atribut, který určuje metadat ve formě %(\<metadat >). Pokud ano, MSBuild spustí cíl jednou pro každou hodnotu jedinečná metadata seskupení nebo "dávkování" s touto hodnotou metadat položky. Například  
  
```xml  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 Odkaz na položky podle jejich metadat RequiredTargetFramework dávky. Výstup cíle by měl vypadat takto:  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
```  
  
 Dávkování cíle je zřídka používané skutečných sestavení. Dávkování úloh je běžné. Další informace najdete v tématu [dávkování](../msbuild/msbuild-batching.md).  
  
## <a name="incremental-builds"></a>Přírůstková sestavení  
 Přírůstková sestavení jsou sestavení, které jsou optimalizované tak, že nejsou provedeny cílů se výstupní soubory, které jsou aktuální s ohledem na jejich odpovídající vstupní soubory. Cílový prvek může mít obě `Inputs` a `Outputs` označující položky cíl jako vstup očekává atributy, a co položky, se vytvoří jako výstup.  
  
 Pokud jsou všechny výstupní položky aktuální, MSBuild vynechává cíl, který výrazně zvyšuje rychlost sestavení. Tomu se říká cíle pro přírůstkové sestavení. Pokud jen některé soubory jsou aktuální, MSBuild spustí cíl bez aktuální položky. Tomu se říká částečné přírůstkové sestavení cíle. Další informace najdete v tématu [přírůstková sestavení](../msbuild/incremental-builds.md).  
  
## <a name="see-also"></a>Viz také:  
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)   
 [Postupy: použití stejného cíle ve více souborech projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)