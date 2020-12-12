---
title: T4 – direktiva Assembly
description: Přečtěte si, že v textové šabloně v době návrhu sady Visual Studio načte direktiva Assembly sestavení tak, aby kód šablony mohl použít jeho typy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41abd2b5a48f6e5e126747326e9815f3c2f46787
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363702"
---
# <a name="t4-assembly-directive"></a>T4 – direktiva Assembly

V textové šabloně návrhu sady Visual Studio `assembly` načte direktiva sestavení tak, aby kód šablony mohl použít jeho typy. Efekt je podobný přidání odkazu na sestavení v projektu sady Visual Studio.

 Obecný přehled o psaní textových šablon najdete v tématu [Vytvoření textové šablony T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> Tuto direktivu nepotřebujete `assembly` v textové šabloně běhu (předzpracované). Místo toho přidejte potřebná sestavení do **odkazů** projektu aplikace Visual Studio.

## <a name="using-the-assembly-directive"></a>Použití direktivy assembly
 Syntaxe této direktivy je následující:

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 Název sestavení by měl být jeden z následujících názvů:

- Silný název sestavení v globální mezipaměti sestavení (GAC), například `System.Xml.dll` . Můžete také použít dlouhý tvar, například `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"` . Další informace naleznete v tématu <xref:System.Reflection.AssemblyName>.

- Absolutní cesta k sestavení

  Syntaxi můžete použít `$(variableName)` k odkazování na proměnné sady Visual Studio, jako jsou `$(SolutionDir)` , a `%VariableName%` pro referenční proměnné prostředí. Příklad:

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 Direktiva assembly nemá žádný účinek na předzpracované textové šablony. Místo toho zahrňte nezbytné odkazy v části **reference** projektu sady Visual Studio. Další informace najdete v tématu [generování textu v době běhu s textovými šablonami T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

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

## <a name="using-project-properties-in-both-msbuild-and-visual-studio"></a><a name="msbuild"></a> Používání vlastností projektu v nástroji MSBuild i v aplikaci Visual Studio
 Makra sady Visual Studio, jako je $ (SolutionDir), nefungují v nástroji MSBuild. Chcete-li transformovat šablony v sestavovacím počítači, je nutné místo toho použít vlastnosti projektu.

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

## <a name="see-also"></a>Viz také:

- [T4 – direktiva Include](../modeling/t4-include-directive.md)
