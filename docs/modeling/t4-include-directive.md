---
title: T4 – direktiva Include
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1ee58c29be3c4dfb5e2148c54464a7a511d1839
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591850"
---
# <a name="t4-include-directive"></a>T4 – direktiva Include

V textové šabloně v aplikaci Visual Studio můžete vložit text z jiného souboru pomocí `<#@include#>` direktivy. `include`Direktivy lze umístit kdekoli v textové šabloně před blok funkce první třídy `<#+ ... #>` . Zahrnuté soubory mohou obsahovat také `include` direktivy a další direktivy. Díky tomu můžete kód šablony a často používaný text sdílet mezi šablonami.

## <a name="using-include-directives"></a>Použití direktiv include

```
<#@ include file="filePath" [once="true"] #>
```

- `filePath` může být absolutní nebo relativní k aktuálnímu souboru šablony.

   Kromě toho můžou konkrétní rozšíření sady Visual Studio určovat vlastní adresáře pro hledání souborů k zahrnutí. Pokud jste například nainstalovali sadu pro vizualizaci a modelování sady SDK (DSL Tools), přidá se do seznamu zahrnutí následující složka: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates` .

   Tyto další složky vkládaných souborů mohou záviset na příponě vkládaného souboru. Například složka pro zahrnutí nástrojů DSL je dostupná jenom pro zahrnutí souborů, které mají příponu souboru. `.tt`

- `filePath` může obsahovat proměnné prostředí, které jsou odděleny znakem "%". Příklad:

  ```
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>
  ```

- Název zahrnutého souboru nemusí používat rozšíření `".tt"` .

   Možná budete chtít použít jinou příponu, například `".t4"` pro zahrnuté soubory. Důvodem je, že když přidáte `.tt` soubor do projektu, sada Visual Studio automaticky nastaví **vlastní vlastnost nástroje** na `TextTemplatingFileGenerator` . Vkládané soubory obvykle nechcete transformovat individuálně.

   Na druhé straně byste měli vědět, že v některých případech přípona souboru ovlivňuje, v jakých dalších složkách se budou hledat vkládané soubory. To může být důležité, pokud máte vkládaný soubor, který obsahuje jiné soubory.

- Vložený obsah se zpracuje téměř jako kdyby byl součástí textové šablony, která ho vkládá. Můžete však zahrnout soubor, který obsahuje blok funkcí třídy `<#+...#>` i v případě, že `include` je za direktivou následován běžný text a standardní řídicí bloky.

- Použijte `once="true"` k zajištění toho, že šablona je obsažena pouze jednou, i když je vyvolána z více než jednoho jiného vloženého souboru.

   Tato funkce usnadňuje sestavování knihovny opakovaně použitelných fragmentů T4, které můžete zahrnout do, aniž byste se museli zabývat dalšími fragmenty kódu, které jsou již zahrnuty.  Předpokládejme například, že máte knihovnu velmi jemně odstupňovaných fragmentů, které se zabývat zpracováním šablon a generováním C#.  Tato možnost je používána některými dalšími nástroji pro konkrétní úkoly, jako je generování výjimek, které pak můžete použít ze všech dalších šablon specifických pro aplikace. Pokud si nakreslíte graf závislostí, uvidíte, že některé fragmenty kódu budou vloženy několikrát. Parametr ale `once` zabrání následným zahrnutím.

  **MyTextTemplate.tt:**

```
<#@ output extension=".txt" #>
Output message 1 (from top template).
<#@ include file="TextFile1.t4"#>
Output message 5 (from top template).
<#
   GenerateMessage(6); // defined in TextFile1.t4
   AnotherGenerateMessage(7); // defined in TextFile2.t4
#>
```

 **TextFile1. T4:**

```
   Output Message 2 (from included file).
<#@ include file="TextFile2.t4" #>
   Output Message 4 (from included file).
<#+ // Start of class feature control block.
void GenerateMessage(int n)
{
#>
   Output Message <#= n #> (from GenerateMessage method).
<#+
}
#>
```

 **TextFile2. T4:**

```
        Output Message 3 (from included file 2).
<#+ // Start of class feature control block.
void AnotherGenerateMessage(int n)
{
#>
       Output Message <#= n #> (from AnotherGenerateMessage method).
<#+
}
#>
```

 **Výsledný vygenerovaný soubor MyTextTemplate.txt:**

```
Output message 1 (from top template).
   Output Message 2 (from included file).
        Output Message 3 (from included file 2).

   Output Message 4 (from included file).

Output message 5 (from top template).
   Output Message 6 (from GenerateMessage method).
       Output Message 7 (from AnotherGenerateMessage method).
```

## <a name="using-project-properties-in-msbuild-and-visual-studio"></a><a name="msbuild"></a> Používání vlastností projektu v nástroji MSBuild a v aplikaci Visual Studio
 I když v direktivě include můžete použít makra sady Visual Studio, jako je $ (SolutionDir), nefungují v nástroji MSBuild. Chcete-li transformovat šablony v sestavovacím počítači, je nutné místo toho použít vlastnosti projektu.

 Úpravou souboru .csproj nebo .vbproj definujte vlastnost projektu. Tento příklad definuje vlastnost s názvem `myIncludeFolder` :

```xml
<!-- Define a project property, myIncludeFolder: -->
<PropertyGroup>
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myIncludeFolder">
      <Value>$(myIncludeFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

 Tuto vlastnost projektu nyní můžete použít v textových šablonách, které se správně transformují jak v sadě Visual Studio, tak v nástroji MSBuild:

```
<#@ include file="$(myIncludeFolder)\defs.tt" #>
```
