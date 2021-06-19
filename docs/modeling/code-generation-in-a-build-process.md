---
title: Vytvoření kódu v procesu sestavení
description: Zjistěte, jak lze transformaci textu vyvolat jako součást procesu sestavení Visual Studio řešení.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: how-to
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7db1b41df5007678c84be71f34aea110c04348c1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389745"
---
# <a name="invoke-text-transformation-in-the-build-process"></a>Vyvolání transformace textu v procesu sestavení

[Transformaci](../modeling/code-generation-and-t4-text-templates.md) textu je možné vyvolat jako součást procesu sestavení [Visual Studio](/azure/devops/pipelines/index) řešení. Některé úlohy sestavení se specializují na transformaci textu. Úlohy sestavení T4 spouštějí textové šablony návrhu a rovněž kompilují textové šablony běhu (předzpracované).

V závislosti na tom, který stroj sestavení používáte, jsou určité rozdíly v tom, co úlohy sestavení mohou provádět. Když sestavíte řešení v Visual Studio, bude mít textová šablona přístup k rozhraní Visual Studio API (EnvDTE), pokud je nastavený atribut [hostspecific="true".](../modeling/t4-template-directive.md) To ale není pravda, když sestavíte řešení z příkazového řádku nebo když zahájíte sestavení serveru prostřednictvím Visual Studio. V těchto případech provádí sestavení nástroj MSBuild a používá se jiný hostitel T4. To znamená, že při vytváření textové šablony pomocí nástroje MSBuild nemůžete stejným způsobem přistupovat k věcem, jako jsou názvy souborů projektu. Informace o prostředí však [můžete předat do textových šablon](#parameters)a procesorů direktiv pomocí parametrů sestavení .

## <a name="configure-your-machines"></a><a name="buildserver"></a> Konfigurace počítačů

Pokud chcete na vývojovém počítači povolit úlohy sestavení, nainstalujte sadu Modeling SDK pro Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Pokud [je váš sestavovací server](/azure/devops/pipelines/agents/agents) spuštěný v počítači, který nemá nainstalované Visual Studio, zkopírujte z počítače pro vývoj do počítače sestavení následující soubory:

- %ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VisualStudio\v16.0\TextTemplating

  - Microsoft.VisualStudio.TextTemplating.Sdk.Host.15.0.dll
  - Microsoft.TextTemplating.Build.Tasks.dll
  - Microsoft.TextTemplating.targets

- %ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

  - Microsoft.VisualStudio.TextTemplating.15.0.dll
  - Microsoft.VisualStudio.TextTemplating.Interfaces.15.0.dll
  - Microsoft.VisualStudio.TextTemplating.VSHost.15.0.dll

- %ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\IDE\PublicAssemblies

  - Microsoft.VisualStudio.TextTemplating.Modeling.15.0.dll

> [!TIP]
> Pokud při spuštění cíle sestavení TextTemplating na serveru sestavení získáte pro metodu Microsoft.CodeAnalysis, ujistěte se, že sestavení Roslyn jsou v adresáři s názvem `MissingMethodException` *Roslyn,* který je ve stejném adresáři jako spustitelný soubor sestavení (například *msbuild.exe*).

## <a name="edit-the-project-file"></a>Úprava souboru projektu

Upravte soubor projektu a nakonfigurujte některé funkce nástroje MSBuild, například import cílů transformace textu.

V **Průzkumník řešení** **klikněte** pravým tlačítkem na projekt a zvolte Uvolnit. Tím umožníte úpravu souborů .csproj nebo .vbproj v editoru XML. Až dokončíte úpravy, zvolte Znovu **načíst.**

## <a name="import-the-text-transformation-targets"></a>Import cílů transformace textu

V souboru .vbproj nebo .csproj vyhledejte řádek podobný následujícímu:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- nebo –

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

Za tento řádek vložte import šablonování textu:

::: moniker range=">=vs-2019"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets" />
```

::: moniker-end

::: moniker range="vs-2017"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
```

::: moniker-end

## <a name="transform-templates-in-a-build"></a>Transformace šablon v sestavení

Do souboru projektu lze vložit některé vlastnosti, které slouží k řízení úlohy transformace:

- Spuštění úlohy transformace na začátku každého sestavení:

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

- Přepište soubory, které jsou jen pro čtení, například proto, že nejsou rezervovány:

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

     Úloha T4 MSBuild ve výchozím nastavení znovu vygeneruje výstupní soubor, pokud je starší než:

     - jeho soubor šablony
     - všechny zahrnuté soubory
     - všechny soubory, které byly dříve čtené šablonou nebo procesorem direktiv, který používá

     Jedná se o výkonnější test závislostí, než jaký používá příkaz Transformovat všechny šablony v nástroji Visual Studio, který porovnává pouze data šablony a výstupního souboru. 

Pokud chcete v projektu provést pouze transformace textu, vyvolejte úlohu TransformAll:

`msbuild myProject.csproj /t:TransformAll`

Transformace konkrétní textové šablony:

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

U příkazu TransformFile lze použít zástupné znaky:

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Správa zdrojového kódu

Systém správy zdrojového kódu není nijak integrován. Můžete ale přidat vlastní rozšíření, například k tomu, abyste si mohli vygenerovaný soubor rezervujete a vhodíte ho. Úloha transformace textu ve výchozím nastavení zabraňuje přepsání souboru, který je označený jako jen pro čtení. Pokud je takový soubor zjištěn, do protokolu se zaprotokoluje chyba Visual Studio Seznam chyb úloha selže.

Pokud chcete určit, že se soubory určené jen pro čtení mají přepisovat, vložte tuto vlastnost:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

Pokud krok následného zpracování neupravíte, zaprotokoluje se do protokolu Seznam chyb při přepsání souboru.

## <a name="customize-the-build-process"></a>Přizpůsobení procesu sestavení

Transformace textu se provede před všemi ostatními úlohami v procesu sestavení. Úlohy, které jsou vyvolány před a po transformaci, můžete definovat nastavením vlastností a `$(BeforeTransform)` `$(AfterTransform)` :

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

- GeneratedFiles – seznam souborů zapsaných procesem. Pro soubory, které překrály existující soubory jen pro `%(GeneratedFiles.ReadOnlyFileOverwritten)` čtení, bude mít tato hodnota hodnotu true. Tyto soubory lze rezervovat ze správy zdrojového kódu.

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

Užitečná složka pro přesměrování na je `$(IntermediateOutputPath)` .

Pokud zadáte výstupní název souboru, bude mít přednost před příponou zadanou v direktivě output v šablonách.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Zadání OutputFileName nebo OutputFilePath se nedoporučuje, pokud také transformujete šablony uvnitř Visual Studio pomocí možnosti **Transformovat** vše nebo spustíte generátor jediného souboru. V závislosti na tom, jak jste transformaci aktivoval, budete mít různé cesty k souborům. Tohle může být matoucí.

## <a name="add-reference-and-include-paths"></a>Přidání odkazů a cest k zahrnutí

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

## <a name="pass-build-context-data-into-the-templates"></a><a name="parameters"></a> Předání kontextových dat sestavení do šablon

Hodnoty parametru lze nastavit v souboru projektu. Můžete například předat vlastnosti [sestavení](../msbuild/msbuild-properties.md) a proměnné [prostředí](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

V textové šabloně nastavte `hostspecific` v direktivě template. K získání [hodnot](../modeling/t4-parameter-directive.md) použijte direktivu parameter:

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

V procesoru direktiv můžete volat [ITextTemplatingEngineHost.ResolveParameterValue:](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\))

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> `ResolveParameterValue` získá data `T4ParameterValues` pouze při použití nástroje MSBuild. Při transformaci šablony pomocí Visual Studio mají parametry výchozí hodnoty.

## <a name="use-project-properties-in-assembly-and-include-directives"></a><a name="msbuild"></a> Použití vlastností projektu v direktivách sestavení a include

Visual Studio jako **$(SolutionDir)** nefungují v nástroji MSBuild. Místo toho můžete použít vlastnosti projektu.

Upravte soubor *.csproj* nebo *.vbproj* a definujte vlastnost projektu. Tento příklad definuje vlastnost **myLibFolder**:

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

## <a name="q--a"></a>Otázky a odpovědi

**Proč bychom chtěli transformovat šablony na build serveru? Už jsem transformoval šablony v Visual Studio před tím, než jsem se přihlásil(a) ke svému kódu.**

Pokud aktualizujete zahrnutý soubor nebo jiný soubor přečtené šablonou, Visual Studio soubor automaticky netransformuje. Transformace šablon v rámci sestavení zajišťuje, že je vše aktuální.

**Jaké další možnosti existují pro transformaci textových šablon?**

- Nástroj [TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) lze použít ve skriptech příkazů. Ve většině případů je snazší použít MSBuild.

- [Vyvolá transformaci textu v rozšíření sady Visual Studio](../modeling/invoking-text-transformation-in-a-vs-extension.md).

- [Textové šablony návrhu](../modeling/design-time-code-generation-by-using-t4-text-templates.md) jsou transformovány pomocí sady Visual Studio.

- [Běhové textové šablony](../modeling/run-time-text-generation-with-t4-text-templates.md) se transformují za běhu ve vaší aplikaci.

## <a name="see-also"></a>Viz také

::: moniker range="vs-2017"

- V šabloně s vlastností T4 pro MSbuild v je dobré doprovodné materiály. `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\msbuild\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

::: moniker range=">=vs-2019"

- V šabloně s vlastností T4 pro MSbuild v je dobré doprovodné materiály. `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\msbuild\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

- [Zápis textové šablony T4](../modeling/writing-a-t4-text-template.md)
