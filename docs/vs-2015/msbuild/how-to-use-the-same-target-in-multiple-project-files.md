---
title: 'Postupy: použití stejného cíle ve více souborech projektu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d388d32b288e47a7e92f5d0f727230ffa00a2621
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178324"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Postupy: Použití stejného cíle ve více souborech projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud jste vytvořili několik [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souborů projektu, možná jste zjistili, že je nutné použít stejné úlohy a cíle v různých souborech projektu. Místo zahrnutí úplný popis těchto úkolů nebo cílů do každého souboru projektu můžete uložit cíl do samostatného souboru projektu a pak tento projekt importovat do jakéhokoli jiného projektu, který potřebuje použít cíl.  
  
## <a name="using-the-import-element"></a>Použití elementu import  
 `Import`Element se používá k vložení jednoho souboru projektu do jiného souboru projektu. Soubor projektu, který se má importovat, musí být platným [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souborem projektu a obsahovat kód XML ve správném formátu. `Project`Atribut určuje cestu k importovanému souboru projektu. Další informace o elementu naleznete `Import` v tématu [Import element (MSBuild)](../msbuild/import-element-msbuild.md).  
  
#### <a name="to-import-a-project"></a>Import projektu  
  
1. Definujte v importovaném souboru projektu všechny vlastnosti a položky, které jsou používány jako parametry pro vlastnosti a položky v importovaném projektu.  
  
2. Použijte `Import` prvek pro import projektu. Příklad:  
  
     `<Import Project="MyCommon.targets"/>`  
  
3. Po `Import` elementu definujte všechny vlastnosti a položky, které musí přepsat výchozí definice vlastností a položek v importovaném projektu.  
  
## <a name="order-of-evaluation"></a>Pořadí vyhodnocení  
 Při [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] dosažení `Import` prvku se importovaný projekt efektivně vloží do importovaného projektu v umístění `Import` elementu. Proto umístění `Import` elementu může ovlivnit hodnoty vlastností a položek. Je důležité porozumět vlastnostem a položkám, které jsou nastaveny v importovaném projektu, a vlastnosti a položky, které používá importovaný projekt.  
  
 Při sestavení projektu všechny vlastnosti jsou vyhodnoceny jako první, následované položkami. Například následující kód XML definuje importovaný soubor projektu MyCommon. targets:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyCommon</Name>  
    </PropertyGroup>  
  
    <Target Name="Go">  
        <Message Text="Name=$(Name)"/>  
    </Target>  
</Project>  
```  
  
 Následující kód XML definuje MyApp. proj, který importuje MyCommon. targets:  
  
```  
<Project  
    DefaultTargets="Go"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyApp</Name>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
 Při sestavení projektu se zobrazí následující zpráva:  
  
 `Name="MyCommon"`  
  
 Vzhledem k tomu, že projekt je importován poté, co byla vlastnost `Name` definována v MyApp. proj, definice `Name` v MyCommon. targets přepíše definici v MyApp. proj. Pokud je projekt importován před definováním názvu vlastnosti, sestavení zobrazí následující zprávu:  
  
 `Name="MyApp"`  
  
#### <a name="use-the-following-approach-when-importing-projects"></a>Při importu projektů použijte následující postup.  
  
1. V souboru projektu definujte všechny vlastnosti a položky, které jsou používány jako parametry pro vlastnosti a položky v importovaném projektu.  
  
2. Importujte projekt.  
  
3. V souboru projektu definujte všechny vlastnosti a položky, které musí přepsat výchozí definice vlastností a položek v importovaném projektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje soubor MyCommon. targets, který naimportuje druhý příklad kódu. Soubor. targets vyhodnocuje vlastnosti z importu projektu pro konfiguraci sestavení.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>  
        <appname>$(MSBuildProjectName)</appname>  
    <PropertyGroup>  
    <Target Name="Build">  
        <Csc Sources="hello.cs"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu importuje soubor MyCommon. targets.  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor>RETAIL</Flavor>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Import – element (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Targets](../msbuild/msbuild-targets.md)
