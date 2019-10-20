---
title: Generování kódu v procesu sestavení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
ms.assetid: 4da43429-2a11-4d7e-b2e0-9e4af7033b5a
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 81c4160ca6d03d55d631cd4dad8c3bce01fa9722
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667869"
---
# <a name="code-generation-in-a-build-process"></a>Vytvoření kódu v procesu sestavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Transformaci textu lze vyvolat jako součást procesu sestavení řešení sady Visual Studio. Některé úlohy sestavení se specializují na transformaci textu. Úlohy sestavení T4 spouštějí textové šablony návrhu a rovněž kompilují textové šablony běhu (předzpracované).

V závislosti na tom, který stroj sestavení používáte, jsou určité rozdíly v tom, co úlohy sestavení mohou provádět. Při sestavování řešení v sadě Visual Studio může textová šablona získat přístup k rozhraní API sady Visual Studio (EnvDTE), pokud je nastaven atribut [hostspecific = "true"](../modeling/t4-template-directive.md) . To ale neplatí při sestavování řešení z příkazového řádku nebo při inicializaci sestavení na serveru prostřednictvím sady Visual Studio. V těchto případech provádí sestavení nástroj MSBuild a používá se jiný hostitel T4.

To znamená, že k různým položkám (například k názvům projektů) nelze získat přístup stejně jako při sestavování textové šablony v nástroji MSBuild. Můžete však [předat informace o prostředí do textových šablon a procesorů direktiv pomocí parametrů sestavení](#parameters).

## <a name="buildserver"></a>Konfigurace počítačů

Pokud chcete povolit úlohy sestavení ve vývojovém počítači, nainstalujte [sadu Modeling SDK pro Visual Studio](https://www.microsoft.com/download/details.aspx?id=48148).

Pokud je [Server sestavení](https://msdn.microsoft.com/library/788443c3-0547-452e-959c-4805573813a9) spuštěn v počítači, na kterém není nainstalována aplikace Visual Studio, zkopírujte následující soubory do počítače sestavení z vývojového počítače. Nahradí nejnovější čísla verzí hvězdičkou (*).

- $ (ProgramFiles) \MSBuild\Microsoft\VisualStudio\v *. 0 \ TextTemplating

  - Microsoft. VisualStudio. TextTemplating. SDK. Host. *. 0. dll

  - Microsoft.TextTemplating.Build.Tasks.dll

  - Microsoft.TextTemplating.targets

- $ (ProgramFiles) \Microsoft Visual Studio *. 0 \ VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

  - Microsoft. VisualStudio. TextTemplating. *. 0. dll

  - Microsoft. VisualStudio. TextTemplating. Interfaces. *. 0. dll (několik souborů)

  - Microsoft. VisualStudio. TextTemplating. VSHost. *. 0. dll

- $ (ProgramFiles) \Microsoft Visual Studio *. 0 \ Common7\IDE\PublicAssemblies\

  - Microsoft. VisualStudio. TextTemplating. Modeling. *. 0. dll

## <a name="to-edit-the-project-file"></a>Úprava souboru projektu

Některé funkce nástroje MSBuild budete muset nakonfigurovat úpravou souboru projektu.

V Průzkumníku řešení vyberte možnost **uvolnit** z místní nabídky projektu. Tím umožníte úpravu souborů .csproj nebo .vbproj v editoru XML.

Po dokončení úprav klikněte na možnost **znovu načíst**.

## <a name="import-the-text-transformation-targets"></a>Import cílů transformace textu

V souboru .vbproj nebo .csproj vyhledejte řádek podobný následujícímu:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- nebo-

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

Za tento řádek vložte import šablonování textu:

```xml
<!-- Optionally make the import portable across VS versions -->
  <PropertyGroup>
    <!-- Get the Visual Studio version – defaults to 10: -->
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">10.0</VisualStudioVersion>
    <!-- Keep the next element all on one line: -->
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>
  </PropertyGroup>

<!-- This is the important line: -->
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />
```

## <a name="transforming-templates-in-a-build"></a>Transformace šablon v sestavení

Do souboru projektu lze vložit některé vlastnosti, které slouží k řízení úlohy transformace:

- Spuštění úlohy transformace na začátku každého sestavení:

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

- Přepsání souborů, které jsou určeny jen pro čtení, protože například nejsou rezervovány:

    ```xml
    <PropertyGroup>
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>
    </PropertyGroup>
    ```

- Transformace všech šablon při každém spuštění:

    ```xml
    <PropertyGroup>
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>
    </PropertyGroup>
    ```

     Ve výchozím nastavení úloha T4 nástroje MSBuild znovu vygeneruje výstupní soubor, pokud je starší než její soubory šablony, nebo všechny vložené soubory, nebo všechny soubory, které byly předtím čteny šablonou nebo procesorem direktiv, který používá. Jedná se o mnohem komplexnější test závislostí, než jaký používá příkaz Transformovat všechny šablony v sadě Visual Studio, který pouze porovnává datum šablony a výstupního souboru.

Pokud chcete v projektu provést pouze transformace textu, vyvolejte úlohu TransformAll:

`msbuild myProject.csproj /t:TransformAll`

Transformace konkrétní textové šablony:

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

U příkazu TransformFile lze použít zástupné znaky:

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Správa zdrojového kódu

Systém správy zdrojového kódu není nijak integrován. Můžete však přidat vlastní rozšíření, například pro rezervaci a vrácení vygenerovaného souboru. Úloha transformace textu ve výchozím nastavení zabraňuje přepsání souboru, který je určený jen pro čtení, a když na takový soubor narazí, bude do seznamu chyb sady Visual Studio zaprotokolována chyba a tato úloha selže.

Pokud chcete určit, že se soubory určené jen pro čtení mají přepisovat, vložte tuto vlastnost:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

Dokud tento krok následného zpracování neupravíte, při přepsání souboru se do seznamu chyb zaprotokoluje upozornění.

## <a name="customizing-the-build-process"></a>Přizpůsobení procesu sestavení

Transformace textu se provede před všemi ostatními úlohami v procesu sestavení. Můžete definovat úkoly, které jsou vyvolány před a po transformaci, nastavením vlastností `$(BeforeTransform)` a `$(AfterTransform)`:

```xml
<PropertyGroup>
    <BeforeTransform>CustomPreTransform</BeforeTransform>
    <AfterTransform>CustomPostTransform</AfterTransform>
  </PropertyGroup>
  <Target Name="CustomPreTransform">
    <Message Text="In CustomPreTransform..." Importance="High" />
  </Target>
  <Target Name="CustomPostTransform">
    <Message Text="In CustomPostTransform..." Importance="High" />
  </Target>
```

V `AfterTransform` můžete odkazovat na seznamy souborů:

- GeneratedFiles – seznam souborů zapsaných procesem. U souborů, které přepsaly existující soubory určené jen pro čtení, bude mít %(GeneratedFiles.ReadOnlyFileOverwritten) hodnotu true. Tyto soubory lze rezervovat ze správy zdrojového kódu.

- NonGeneratedFiles – seznam souborů určených jen pro čtení, které nebyly přepsány.

  Lze například definovat úlohu, která rezervuje GeneratedFiles.

## <a name="outputfilepath-and-outputfilename"></a>OutputFilePath a OutputFileName

Tyto vlastnosti používá pouze nástroj MSBuild. Neovlivňují generování kódu v sadě Visual Studio. Slouží k přesměrování vygenerovaného výstupního souboru do jiné složky nebo souboru. Cílová složka již musí existovat.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFilePath>MyFolder</OutputFilePath>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Užitečnou složkou pro přesměrování je `$(IntermediateOutputPath).`

Zadáte-li název výstupního souboru, bude mít přednost před příponou zadanou v direktivě output v šablonách.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Nastavení OutputFileName nebo OutputFilePath není doporučeno, pokud rovněž transformujete šablony v sadě VS pomocí příkazu Transformovat vše nebo spuštěním generátoru jednotlivých souborů. Skončíte s odlišnými cestami souborů v závislosti na tom, jak jste transformaci spustili. To může být velmi matoucí.

## <a name="adding-reference-and-include-paths"></a>Přidání odkazu a cest k vkládaným souborům

Hostitel má nastavenu výchozí sadu cest, kde hledá sestavení odkazovaná v šablonách. Tuto sadu přidáte takto:

```
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

Chcete-li nastavit složky, ve kterých se budou hledat vkládané soubory, zadejte seznam s prvky oddělenými středníkem. Obvykle složku přidáte do existujícího seznamu složek.

```
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

## <a name="parameters"></a>Předání dat kontextu sestavení do šablon

Hodnoty parametru lze nastavit v souboru projektu. Můžete například předat vlastnosti sestavení a [proměnné prostředí](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

V textové šabloně nastavte `hostspecific` v direktivě Template. K získání hodnot Použijte direktivu [Parameter](../modeling/t4-parameter-directive.md) :

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

## <a name="msbuild"></a>Používání vlastností projektu v direktivách sestavení a zahrnutí

Makra sady Visual Studio, například $(SolutionDir), nefungují v nástroji MSBuild. Místo toho můžete použít vlastnosti projektu.

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

Nyní můžete vlastnost projektu použít v direktivách assembly a include:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
<#@ include file="$(myLibFolder)\MyIncludeFile.t4" #>
```

 Tyto direktivy získají z T4parameterValues hodnoty v hostitelích MSBuild i Visual Studio.

## <a name="q--a"></a>Otázka & A

**Proč bych chtěl transformovat šablony na serveru sestavení? V aplikaci Visual Studio už byly transformované šablony před vrácením kódu se změnami**

Při aktualizaci vkládaného souboru nebo jiného souboru čteného šablonou netransformuje Visual Studio tento soubor automaticky. Transformace šablon během sestavení zajišťuje, že je vše v aktuálním stavu.

**Jaké další možnosti jsou pro transformaci textových šablon?**

- [Nástroj TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) lze použít ve skriptech příkazů. Ve většině případů je jednodušší použít nástroj MSBuild.

- [Volání transformací textu v rozšíření VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)

- [Textové šablony návrhu](../modeling/design-time-code-generation-by-using-t4-text-templates.md) jsou transformovány pomocí sady Visual Studio.

- [Textové šablony běhu](../modeling/run-time-text-generation-with-t4-text-templates.md) jsou transformované v době běhu aplikace.

## <a name="read-more"></a>Další informace

Dobrý návod poskytuje šablona T4 nástroje MSbuild, $(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets.

- [Zápis textové šablony T4](../modeling/writing-a-t4-text-template.md)
- [Sada SDK pro vizualizaci a modelování sady Visual Studio](http://go.microsoft.com/fwlink/?LinkID=185579)
- [Oleg Sych: Princip integrace s T4: MSBuild](https://github.com/olegsych/T4Toolbox)
