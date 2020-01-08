---
title: Vytvoření kódu v procesu sestavení
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e01136b845124d74c22ceb1c7cab877a8e2d1d04
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590550"
---
# <a name="invoke-text-transformation-in-the-build-process"></a>Vyvolat transformaci textu v procesu sestavení

[Transformaci textu](../modeling/code-generation-and-t4-text-templates.md) lze vyvolat jako součást [procesu sestavení](/azure/devops/pipelines/index) řešení sady Visual Studio. Některé úlohy sestavení se specializují na transformaci textu. Úlohy sestavení T4 spouštějí textové šablony návrhu a rovněž kompilují textové šablony běhu (předzpracované).

V závislosti na tom, který stroj sestavení používáte, jsou určité rozdíly v tom, co úlohy sestavení mohou provádět. Při sestavování řešení v sadě Visual Studio může textová šablona získat přístup k rozhraní API sady Visual Studio (EnvDTE), pokud je nastaven atribut [hostspecific = "true"](../modeling/t4-template-directive.md) . To ale neplatí při sestavování řešení z příkazového řádku nebo při inicializaci sestavení serveru prostřednictvím sady Visual Studio. V těchto případech provádí sestavení nástroj MSBuild a používá se jiný hostitel T4. To znamená, že nemůžete mít přístup k objektům, jako jsou názvy souborů projektu stejným způsobem, když vytváříte textovou šablonu pomocí nástroje MSBuild. Můžete však [předat informace o prostředí do textových šablon a procesorů direktiv pomocí parametrů sestavení](#parameters).

## <a name="buildserver"></a>Konfigurace počítačů

Pokud chcete povolit úlohy sestavení ve vývojovém počítači, nainstalujte sadu Modeling SDK pro Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Pokud je [Server sestavení](/azure/devops/pipelines/agents/agents) spuštěn v počítači, ve kterém není nainstalována aplikace Visual Studio, zkopírujte následující soubory do počítače sestavení z vývojového počítače:

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VisualStudio\v16.0\TextTemplating

  - Microsoft. VisualStudio. TextTemplating. SDK. Host. 15.0. dll
  - Microsoft.TextTemplating.Build.Tasks.dll
  - Microsoft.TextTemplating.targets

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

  - Microsoft. VisualStudio. TextTemplating. 15.0. dll
  - Microsoft. VisualStudio. TextTemplating. Interfaces. 15.0. dll
  - Microsoft. VisualStudio. TextTemplating. VSHost. 15.0. dll

- % ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\IDE\PublicAssemblies

  - Microsoft. VisualStudio. TextTemplating. Modeling. 15.0. dll

> [!TIP]
> Pokud při spouštění cílů sestavení TextTemplating na serveru sestavení získáte `MissingMethodException` pro metodu Microsoft. CodeAnalysis, ujistěte se, že jsou sestavení Roslyn v adresáři s názvem *Roslyn* , který je ve stejném adresáři jako spustitelný soubor sestavení (například *MSBuild. exe*).

## <a name="edit-the-project-file"></a>Upravit soubor projektu

Upravte soubor projektu pro konfiguraci některých funkcí nástroje MSBuild, například import cílů transformace textu.

V **Průzkumník řešení**v místní nabídce projektu klikněte na **uvolnit** . Tím umožníte úpravu souborů .csproj nebo .vbproj v editoru XML. Po dokončení úprav klikněte na možnost **znovu načíst**.

## <a name="import-the-text-transformation-targets"></a>Importovat cíle transformace textu

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

- Přepsat soubory, které jsou jen pro čtení, například kvůli tomu, že nejsou rezervovány:

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

     Ve výchozím nastavení úloha T4 MSBuild znovu generuje výstupní soubor, pokud je starší než:

     - soubor šablony
     - Všechny zahrnuté soubory
     - všechny soubory, které byly dříve čteny šablonou nebo procesorem direktiv, kterou používá

     Toto je výkonnější test závislosti, než který je použit příkazem **Transform All Templates** v aplikaci Visual Studio, který porovnává pouze data šablony a výstupní soubor.

Pokud chcete v projektu provést pouze transformace textu, vyvolejte úlohu TransformAll:

`msbuild myProject.csproj /t:TransformAll`

Transformace konkrétní textové šablony:

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

U příkazu TransformFile lze použít zástupné znaky:

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Správy zdrojového kódu

Systém správy zdrojového kódu není nijak integrován. Můžete ale přidat vlastní rozšíření, například pro rezervaci a vrácení se změnami vygenerovaného souboru. Ve výchozím nastavení se úloha transformace textu vyhne přepsání souboru, který je označen jen pro čtení. Při výskytu takového souboru se v Seznam chyb sady Visual Studio zaznamená chyba a úloha se nezdařila.

Pokud chcete určit, že se soubory určené jen pro čtení mají přepisovat, vložte tuto vlastnost:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

Pokud neprovedete přizpůsobení kroku postprocessing, při přepisování souboru se do Seznam chyb zaznamená upozornění.

## <a name="customize-the-build-process"></a>Přizpůsobení procesu sestavení

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

V `AfterTransform`můžete odkazovat na seznamy souborů:

- GeneratedFiles – seznam souborů zapsaných procesem. U souborů, které přepsaly existující soubory jen pro čtení, bude `%(GeneratedFiles.ReadOnlyFileOverwritten)` true. Tyto soubory lze rezervovat ze správy zdrojového kódu.

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

Užitečnou složkou pro přesměrování je `$(IntermediateOutputPath)`.

Pokud zadáte název výstupního souboru, bude mít přednost před rozšířením zadaným v direktivě Output v šablonách.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Zadání OutputFileName nebo OutputFilePath se nedoporučuje, pokud také transformují šablony v rámci sady Visual Studio pomocí **transformace vše** nebo spuštěním generátoru Single File. V závislosti na tom, jakým způsobem jste transformaci aktivovali, skončíte s různými cestami k souborům. Tohle může být matoucí.

## <a name="add-reference-and-include-paths"></a>Přidat odkaz a zahrnout cesty

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

## <a name="parameters"></a>Předání dat kontextu sestavení do šablon

Hodnoty parametru lze nastavit v souboru projektu. Můžete například předat vlastnosti [sestavení](../msbuild/msbuild-properties.md) a [proměnné prostředí](../msbuild/how-to-use-environment-variables-in-a-build.md):

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

V procesoru direktiv můžete volat [ITextTemplatingEngineHost. neimplementuje atribut ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)):

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> `ResolveParameterValue` získá data z `T4ParameterValues` pouze při použití nástroje MSBuild. Při transformaci šablony pomocí sady Visual Studio mají parametry výchozí hodnoty.

## <a name="msbuild"></a>Použít vlastnosti projektu v direktivách Assembly a include

Makra sady Visual Studio, jako je **$ (SolutionDir)** , nefungují v nástroji MSBuild. Místo toho můžete použít vlastnosti projektu.

Upravte soubor *. csproj* nebo *. vbproj* a definujte vlastnost projektu. Tento příklad definuje vlastnost s názvem **myLibFolder**:

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

**Proč bych chtěl transformovat šablony na serveru sestavení? V aplikaci Visual Studio už byly transformované šablony před vrácením kódu se změnami**

Pokud aktualizujete zahrnutý soubor nebo jiný soubor načtený šablonou, Visual Studio soubor netransformuje automaticky. Transformace šablon v rámci sestavení zajistí, že vše je aktuální.

**Jaké další možnosti jsou pro transformaci textových šablon?**

- [Nástroj TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) lze použít ve skriptech příkazů. Ve většině případů je snazší použít MSBuild.

- [Vyvolá transformaci textu v rozšíření sady Visual Studio](../modeling/invoking-text-transformation-in-a-vs-extension.md).

- [Textové šablony návrhu](../modeling/design-time-code-generation-by-using-t4-text-templates.md) jsou transformovány pomocí sady Visual Studio.

- [Běhové textové šablony](../modeling/run-time-text-generation-with-t4-text-templates.md) se transformují za běhu ve vaší aplikaci.

## <a name="see-also"></a>Viz také:

::: moniker range="vs-2017"

- V šabloně pro MSbuild s vlastností T4 je dobré doprovodné materiály na `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\msbuild\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

::: moniker range=">=vs-2019"

- V šabloně pro MSbuild s vlastností T4 je dobré doprovodné materiály na `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\msbuild\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

- [Zápis textové šablony T4](../modeling/writing-a-t4-text-template.md)
