---
title: T4 – direktiva Assembly
description: Zjistíte, že Visual Studio šablony návrhu načte direktiva assembly sestavení tak, aby kód šablony mohl používat jeho typy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 38b5a7fe2308884d4837a068770af67435ada70e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386355"
---
# <a name="t4-assembly-directive"></a>T4 – direktiva Assembly

V Visual Studio šablony v době návrhu načte direktiva sestavení, aby kód šablony mohl `assembly` používat své typy. Účinek je podobný přidání odkazu na sestavení do Visual Studio projektu.

 Obecný přehled psaní textových šablon najdete v tématu [Zápis textové šablony T4.](../modeling/writing-a-t4-text-template.md)

> [!NOTE]
> Direktivu v textové šabloně `assembly` běhu (předzpracované) nepotřebujete. Místo toho přidejte potřebná sestavení **do odkazů** vašeho Visual Studio projektu.

## <a name="using-the-assembly-directive"></a>Použití direktivy assembly
 Syntaxe této direktivy je následující:

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 Název sestavení by měl být jeden z následujících názvů:

- Silný název sestavení v GAC, například `System.Xml.dll` . Můžete také použít dlouhý tvar, například `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"` . Další informace naleznete v tématu <xref:System.Reflection.AssemblyName>.

- Absolutní cesta k sestavení

  Syntaxi můžete použít k odkazování na proměnné Visual Studio, jako je , a k `$(variableName)` `$(SolutionDir)` `%VariableName%` odkazování na proměnné prostředí. Příklad:

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 Direktiva assembly nemá žádný účinek na předzpracované textové šablony. Místo toho do části Odkazy vašeho projektu **projektu** Visual Studio odkazy. Další informace najdete v tématu Generování textu za běhu pomocí [textových šablon T4.](../modeling/run-time-text-generation-with-t4-text-templates.md)

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

## <a name="using-project-properties-in-both-msbuild-and-visual-studio"></a><a name="msbuild"></a> Použití vlastností projektu v nástroji MSBuild i Visual Studio
 Visual Studio jako $(SolutionDir) nefungují v nástroji MSBuild. Chcete-li transformovat šablony v sestavovacím počítači, je nutné místo toho použít vlastnosti projektu.

 Úpravou souboru .csproj nebo .vbproj definujte vlastnost projektu. Tento příklad definuje vlastnost s názvem `myLibFolder` :

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

- [T4 – direktiva Include](../modeling/t4-include-directive.md)
