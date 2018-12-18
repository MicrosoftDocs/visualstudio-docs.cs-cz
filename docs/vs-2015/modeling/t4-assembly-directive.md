---
title: T4 – Direktiva Assembly | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 44949749-ce3c-4fb5-8690-a17f1564ac2f
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 97e28347ba6985d99386647219f92aac9a221398
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873575"
---
# <a name="t4-assembly-directive"></a>T4 – direktiva Assembly
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] návrhová textová šablona `assembly` načte direktiva sestavení tak, aby kód šablony mohl používat jeho typy. Účinek se podobá přidání odkazu na sestavení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu.  
  
 Obecný přehled o psaní textových šablon, naleznete v tématu [vytvoření textové šablony T4](../modeling/writing-a-t4-text-template.md).  
  
> [!NOTE]
>  Není nutné `assembly` direktivy šablony textu za běhu (Předzpracované). Místo toho přidejte potřebná sestavení do **odkazy** z vaší [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu.  
  
## <a name="using-the-assembly-directive"></a>Použití direktivy assembly  
 Syntaxe této direktivy je následující:  
  
```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 Název sestavení by měl být jeden z následujících názvů:  
  
- Silný název sestavení v mezipaměti GAC, například `System.Xml.dll`. Můžete také použít dlouhou, například `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`. Další informace naleznete v tématu <xref:System.Reflection.AssemblyName>.  
  
- Absolutní cesta k sestavení  
  
  Můžete použít `$(variableName)` syntaxi odkazovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proměnné jako `$(SolutionDir)`, a `%VariableName%` na referenční proměnné prostředí. Příklad:  
  
```  
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>  
```  
  
 Direktiva assembly nemá žádný účinek na předzpracované textové šablony. Místo toho vložte potřebné odkazy **odkazy** část vaší [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. Další informace najdete v tématu [generování textu za běhu pomocí textových šablon T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="standard-assemblies"></a>Standardní sestavení  
 Následující sestavení se načítají automaticky, takže pro ně nemusíte psát direktivy sestavení:  
  
- `Microsoft.VisualStudio.TextTemplating.1*.dll`  
  
- `System.dll`  
  
- `WindowsBase.dll`  
  
  Pokud používáte vlastní direktivu, může procesor direktiv načíst další sestavení. Pokud například píšete šablony pro jazyk domény (DSL), nemusíte psát direktivy sestavení pro následující sestavení:  
  
- `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`  
  
- `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`  
  
- `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`  
  
- Sestavení obsahující váš kód DSL  
  
##  <a name="msbuild"></a> Používání vlastností projektu v nástroji MSBuild a sadě Visual Studio  
 Makra sady Visual Studio, například $(SolutionDir), nefungují v nástroji MSBuild. Chcete-li transformovat šablony v sestavovacím počítači, je nutné místo toho použít vlastnosti projektu.  
  
 Úpravou souboru .csproj nebo .vbproj definujte vlastnost projektu. Tento příklad definuje vlastnost s názvem `myLibFolder`:  
  
```xml  
<!-- Define a project property, myLibFolder: -->  
<PropertyGroup>  
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myLibFolder">  
      <Value>$(myLibFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 Tuto vlastnost projektu nyní můžete použít v textových šablonách, které se správně transformují jak v sadě Visual Studio, tak v nástroji MSBuild:  
  
```  
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>  
```  
  
## <a name="see-also"></a>Viz také  
 [T4 – direktiva Include](../modeling/t4-include-directive.md)



