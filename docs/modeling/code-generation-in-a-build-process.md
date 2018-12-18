---
title: Vytvoření kódu v procesu sestavení
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ef7c49c514c9104ee4659db983b04c27036df889
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281820"
---
# <a name="code-generation-in-a-build-process"></a>Generování kódu v procesu sestavení

[Transformace textu](../modeling/code-generation-and-t4-text-templates.md) lze vyvolat jako součást [proces sestavení](/azure/devops/pipelines/index) řešení sady Visual Studio. Některé úlohy sestavení se specializují na transformaci textu. Úlohy sestavení T4 spouštějí textové šablony návrhu a rovněž kompilují textové šablony běhu (předzpracované).

V závislosti na tom, který stroj sestavení používáte, jsou určité rozdíly v tom, co úlohy sestavení mohou provádět. Při sestavování řešení v sadě Visual Studio textové šablony můžete přístup k rozhraní API Visual Studio (EnvDTE) Pokud [hostspecific = "true"](../modeling/t4-template-directive.md) atribut je nastaven. To ale neplatí při sestavování řešení z příkazového řádku nebo při inicializaci sestavení na serveru pomocí sady Visual Studio. V těchto případech provádí sestavení nástroj MSBuild a používá se jiný hostitel T4.

To znamená, že můžete mít přístup k věci, jako jsou názvy souborů projektu v stejným způsobem jako při sestavování textové šablony v nástroji MSBuild. Můžete však [předání informací o prostředí do textových šablon a procesorů pro direktivy použít parametry sestavení](#parameters).

##  <a name="buildserver"></a> Konfigurace počítačů

Pokud chcete povolit úlohy sestavení na vašem vývojovém počítači, instalace Modeling SDK pro Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Pokud [váš server sestavení](/azure/devops/pipelines/agents/agents) se spustí na počítači, na kterém není nainstalována sada Visual Studio, zkopírujte následující soubory do počítače sestavení z vývojového počítače. Nahraďte nejnovější čísla verzí pro "*".

- $(ProgramFiles)\MSBuild\Microsoft\VisualStudio\v*.0\TextTemplating

    - Microsoft.VisualStudio.TextTemplating.Sdk.Host.*.0.dll

    - Microsoft.TextTemplating.Build.Tasks.dll

    - Microsoft.TextTemplating.targets

- *.0\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0 $(ProgramFiles) \Microsoft Visual Studio

    - Microsoft.VisualStudio.TextTemplating.*.0.dll

    - Microsoft.VisualStudio.TextTemplating.Interfaces.*.0.dll (několik souborů)

    - Microsoft.VisualStudio.TextTemplating.VSHost.*.0.dll

- *.0\Common7\IDE\PublicAssemblies\ $(ProgramFiles) \Microsoft Visual Studio

    - Microsoft.VisualStudio.TextTemplating.Modeling.*.0.dll

## <a name="to-edit-the-project-file"></a>Úprava souboru projektu

Budete muset úpravou souboru projektu ke konfiguraci některých funkcí v nástroji MSBuild.

V **Průzkumníka řešení**, zvolte **uvolnění** v místní nabídce projektu. Tím umožníte úpravu souborů .csproj nebo .vbproj v editoru XML.

Po dokončení úprav, vyberte **Reload**.

## <a name="import-the-text-transformation-targets"></a>Import cílů transformace textu

V souboru .vbproj nebo .csproj vyhledejte řádek podobný následujícímu:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- nebo –

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

Za tento řádek vložte import šablonování textu:

```xml
<!-- Optionally make the import portable across VS versions -->
  <PropertyGroup>
    <!-- Get the Visual Studio version - defaults to 10: -->
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">10.0</VisualStudioVersion>
    <!-- Keep the next element all on one line: -->
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>
  </PropertyGroup>

<!-- This is the important line: -->
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />
```

## <a name="transform-templates-in-a-build"></a>Transformace šablon v sestavení

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

## <a name="source-control"></a>Správy zdrojového kódu

Systém správy zdrojového kódu není nijak integrován. Můžete však přidat vlastní rozšíření, například pro rezervaci a vrácení vygenerovaného souboru. Úloha transformace textu ve výchozím nastavení zabraňuje přepsání souboru, který je určený jen pro čtení, a když na takový soubor narazí, bude do seznamu chyb sady Visual Studio zaprotokolována chyba a tato úloha selže.

Pokud chcete určit, že se soubory určené jen pro čtení mají přepisovat, vložte tuto vlastnost:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

Dokud tento krok následného zpracování neupravíte, při přepsání souboru se do seznamu chyb zaprotokoluje upozornění.

## <a name="customize-the-build-process"></a>Přizpůsobení procesu sestavení

Transformace textu se provede před všemi ostatními úlohami v procesu sestavení. Můžete definovat úkoly, které jsou vyvolány před a po transformaci nastavením vlastností `$(BeforeTransform)` a `$(AfterTransform)`:

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

V `AfterTransform`, lze odkazovat na seznamy souborů:

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

Užitečnou složkou k přesměrování je `$(IntermediateOutputPath).`

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

Nastavení OutputFileName nebo OutputFilePath není doporučeno, pokud rovněž transformujete šablony v sadě VS pomocí příkazu Transformovat vše nebo spuštěný generátor tvořený jedním souborem. Skončíte s odlišnými cestami souborů v závislosti na tom, jak jste transformaci spustili. To může být velmi matoucí.

## <a name="add-reference-and-include-paths"></a>Přidání odkazu a cest zahrnutí

Hostitel má nastavenu výchozí sadu cest, kde hledá sestavení odkazovaná v šablonách. Tuto sadu přidáte takto:

```xml
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

Chcete-li nastavit složky, ve kterých se budou hledat vkládané soubory, zadejte seznam s prvky oddělenými středníkem. Obvykle složku přidáte do existujícího seznamu složek.

```xml
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

##  <a name="parameters"></a> Předání kontextových dat sestavení do šablon

Hodnoty parametru lze nastavit v souboru projektu. Můžete například předat [sestavení](../msbuild/msbuild-properties.md) vlastnosti a [proměnné prostředí](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

V textové šabloně nastavte `hostspecific` v direktivě šablony. Použití [parametr](../modeling/t4-parameter-directive.md) – direktiva k získání hodnot:

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

V procesoru direktiv lze zavolat [ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)):

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> `ResolveParameterValue` získá data z `T4ParameterValues` pouze při použití nástroje MSBuild. Při transformaci šablony pomocí sady Visual Studio budou mít parametry výchozí hodnoty.

##  <a name="msbuild"></a> Používání vlastností projektu v sestavení a direktiv

Makra sady Visual Studio, jako jsou **$ (SolutionDir)** nefungují v nástroji MSBuild. Místo toho můžete použít vlastnosti projektu.

Upravit vaše *.csproj* nebo *.vbproj* souboru definujte vlastnost projektu. Tento příklad definuje vlastnost s názvem **myLibFolder**:

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

## <a name="q--a"></a>Dotazy a odpovědi

**Proč byste měli k transformaci šablon na sestavovacím serveru? Šablony již transformovaly v sadě Visual Studio před vrácením kódu.**

Při aktualizaci vkládaného souboru nebo jiného souboru čteného šablonou, Visual Studio nepodporuje transformaci souboru. Transformace šablon během sestavení zajišťuje, že všechno je v aktuálním stavu.

**Jaké jsou další možnosti transformace textových šablon?**

- [Nástroj TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) lze použít v příkazových skriptech. Ve většině případů je jednodušší použít nástroj MSBuild.

- [Volání transformací textu v rozšíření VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)

- [Návrhové textové šablony](../modeling/design-time-code-generation-by-using-t4-text-templates.md) jsou transformovány sadou Visual Studio.

- [Textové šablony běhu](../modeling/run-time-text-generation-with-t4-text-templates.md) jsou transformovány při běhu aplikace.

## <a name="see-also"></a>Viz také:

- Je dobré pokyny v šablona T4 nástroje MSbuild v *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\msbuild\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets*
- [Zápis textové šablony T4](../modeling/writing-a-t4-text-template.md)
