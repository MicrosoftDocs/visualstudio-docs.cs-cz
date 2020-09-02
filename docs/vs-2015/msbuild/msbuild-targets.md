---
title: Cíle nástroje MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- MSBuild, targets
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4cc8d9654fc2d277f0b7c69483ab46aa3209983
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157612"
---
# <a name="msbuild-targets"></a>Cíle nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cílí na seskupení úkolů v určitém pořadí a umožňuje procesu sestavení připustit je menší jednotky. Například jeden cíl může odstranit všechny soubory ve výstupním adresáři pro přípravu sestavení, zatímco další zkompiluje vstupy pro projekt a umístí je do prázdného adresáře. Další informace o úlohách najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).  
  
## <a name="declaring-targets-in-the-project-file"></a>Deklarování cílů v souboru projektu  
 Cíle jsou deklarovány v souboru projektu s [cílovým](../msbuild/target-element-msbuild.md) elementem. Například následující kód XML vytvoří cíl s názvem konstrukce, který pak zavolá úlohu CSC s typem položky kompilace.  
  
```  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 Podobně jako vlastnosti MSBuild lze cíle předefinovat. Příklad:  
  
```  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 Pokud se AfterBuild spustí, zobrazí se pouze "druhý výskyt".  
  
## <a name="target-build-order"></a>Pořadí sestavení cílů  
 Cíle musí být seřazené, pokud vstup na jeden cíl závisí na výstupu jiného cíle. Existuje několik způsobů, jak zadat pořadí, ve kterém se cíle spouštějí.  
  
- Počáteční cíle  
  
- Výchozí cíle  
  
- První cíl  
  
- Cílové závislosti  
  
- `BeforeTargets` a `AfterTargets` (MSBuild 4,0)  
  
  Cíl se nikdy nespustí dvakrát během jednoho sestavení, a to i v případě, že na něm závisí další cíl sestavení. Po spuštění cíle se jeho příspěvek k sestavení dokončí.  
  
  Podrobnosti a další informace o cílové objednávce sestavení naleznete v tématu [cílové pořadí sestavení](../msbuild/target-build-order.md).  
  
## <a name="target-batching"></a>Dávkování cíle  
 Cílový element může mít `Outputs` atribut, který určuje metadata ve formátu% (metadata). V takovém případě nástroj MSBuild spustí cíl jednou pro každou jedinečnou hodnotu metadat, seskupení nebo dávkování položek, které mají tuto hodnotu metadat. Příklad:  
  
```  
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
  
 dávkuje referenční položky podle jejich metadat RequiredTargetFramework. Výstup cíle vypadá takto:  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
```  
  
 Cílové dávkové zpracování se v reálných sestaveních používá zřídka. Dávkování úloh je běžnější. Další informace najdete v tématu [dávkování](../msbuild/msbuild-batching.md).  
  
## <a name="incremental-builds"></a>Přírůstková sestavení  
 Přírůstková sestavení jsou sestavení optimalizovaná tak, aby se neprováděly cíle s výstupními soubory, které jsou aktuální, s ohledem na jejich odpovídající vstupní soubory. Cílový element může mít oba `Inputs` atributy i `Outputs` , které označují, jaké položky cíl očekává jako vstup a jaké položky generuje jako výstup.  
  
 Pokud jsou všechny výstupní položky aktuální, nástroj MSBuild přeskočí cíl, což významně zlepšuje rychlost sestavení. Tento postup se nazývá přírůstkové sestavení cíle. Pokud jsou pouze některé soubory aktuální, nástroj MSBuild spustí cíl bez aktuálnosti položek. Toto se nazývá částečné přírůstkové sestavení cíle. Další informace naleznete v tématu [přírůstkové sestavení](../msbuild/incremental-builds.md).  
  
## <a name="see-also"></a>Viz také  
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)   
 [Postupy: Použití stejného cíle ve více souborech projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
