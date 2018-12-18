---
title: 'Postupy: použití stejného cíle ve více souborech projektu | Dokumentace Microsoftu'
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
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b886c4865d715c4fee4e9385288f2e4eb15baa5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223337"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Postupy: Použití stejného cíle ve více souborech projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Pokud jste vytvořili několik [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] soubory projektu, jste možná zjistili, že budete muset použít stejné úlohy a cíle v různé soubory projektu. Namísto do každého souboru projektu, včetně úplný popis těchto úloh nebo cíle, můžete uložit cíl v souboru samostatný projekt a následným importem tohoto projektu do jiného projektu, kterou je potřeba použít cíl.  
  
## <a name="using-the-import-element"></a>Pomocí elementu  
 `Import` Element slouží k vložení jeden soubor projektu do jiného souboru projektu. Soubor projektu, která se importují musí být platný [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] soubor projektu a obsahuje kód XML ve správném formátu. `Project` Atribut určuje cestu k souboru importovaném projektu. Další informace o `Import` prvku, naleznete v tématu [Import – Element (MSBuild)](../msbuild/import-element-msbuild.md).  
  
#### <a name="to-import-a-project"></a>Chcete-li importovat projekt  
  
1.  Definujte v souboru importu projektu, všechny vlastnosti a položky, které se používají jako parametry pro vlastnosti, položky v importovaném projektu.  
  
2.  Použití `Import` prvek, který chcete importovat projekt. Příklad:  
  
     `<Import Project="MyCommon.targets"/>`  
  
3.  Následující `Import` elementu, definujte všechny vlastnosti a položky, které se musí přepsat výchozí definice vlastností a položek v importovaném projektu.  
  
## <a name="order-of-evaluation"></a>Pořadí vyhodnocení  
 Když [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] dosáhne `Import` element importovaném projektu účinně vložený do importu projektu na umístění `Import` elementu. Proto umístění `Import` prvek může mít vliv na hodnoty vlastností a položek. Je důležité pochopit vlastnosti a položky, které určil institut NIST importovaném projektu a vlastnosti a položky, které používá importovaném projektu.  
  
 Při sestavení projektu, budou se všechny vlastnosti vyčíslen první, za nímž následuje položky. Například následující kód XML definuje importovaný soubor projektu MyCommon.targets:  
  
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
  
 Následující kód XML definuje MyApp.proj, který importuje MyCommon.targets:  
  
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
  
 Po sestavení projektu, se zobrazí následující zpráva:  
  
 `Name="MyCommon"`  
  
 Vzhledem k tomu, že projekt je importovat po vlastnost `Name` je definována v MyApp.proj definici `Name` MyCommon.targets přepsání definice v MyApp.proj. Pokud projekt je importován před vlastnost, která je definována, sestavení zobrazí následující zpráva:  
  
 `Name="MyApp"`  
  
#### <a name="use-the-following-approach-when-importing-projects"></a>Použijte následující postup při importu projektů  
  
1.  Definování v souboru projektu, všechny vlastnosti a položky, které se používají jako parametry pro vlastnosti, položky v importovaném projektu.  
  
2.  Importujte projektu.  
  
3.  V souboru projektu definujte všechny vlastnosti a položky, které se musí přepsat výchozí definice vlastností a položek v importovaném projektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje MyCommon.targets soubor, který importuje druhý příklad kódu. Souboru .targets vyhodnotí jako vlastnosti z importu projektu ke konfiguraci sestavení.  
  
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
 Následující příklad importuje soubor MyCommon.targets.  
  
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
 [Import – Element (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Cíle](../msbuild/msbuild-targets.md)



