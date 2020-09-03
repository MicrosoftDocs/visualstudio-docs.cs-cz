---
title: Vložené úlohy nástroje MSBuild s RoslynCodeTaskFactory | Microsoft Docs
ms.date: 09/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a1f606ed9e3d42d9f57cb941ee9518c1abfbc47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85289206"
---
# <a name="msbuild-inline-tasks-with-roslyncodetaskfactory"></a>Vložené úlohy MSBuild s použitím RoslynCodeTaskFactory

Podobně jako [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), RoslynCodeTaskFactory využívá kompilátory Roslyn pro různé platformy ke generování sestavení úloh v paměti pro použití jako vložené úkoly.  RoslynCodeTaskFactory úkoly cílí na .NET Standard a můžou pracovat na modulech runtime .NET Framework a .NET Core i na jiných platformách, jako je Linux a Mac OS.

>[!NOTE]
>RoslynCodeTaskFactory je k dispozici pouze v MSBuild 15,8 a vyšších. Verze nástroje MSBuild následují po verzích sady Visual Studio, takže RoslynCodeTaskFactory je k dispozici v systému Visual Studio 2017 verze 15,8 a vyšší.

## <a name="the-structure-of-an-inline-task-with-roslyncodetaskfactory"></a>Struktura vložené úlohy pomocí RoslynCodeTaskFactory

 Vložené úkoly RoslynCodeTaskFactory jsou deklarovány stejným způsobem jako [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), jediným rozdílem, že cílí na .NET Standard.  Vložená úloha a `UsingTask` element, který obsahuje, jsou obvykle zahrnuty do souboru *. targets* a importovány do jiných souborů projektu podle potřeby. Zde je základní vložená úloha. Všimněte si, že nedělá nic.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task does nothing. -->
  <UsingTask
    TaskName="DoNothing"
    TaskFactory="RoslynCodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="" />
      <Using Namespace="" />
      <Code Type="Fragment" Language="cs">
      </Code>
    </Task>
  </UsingTask>
</Project>
```

 `UsingTask`Element v příkladu má tři atributy, které popisují úlohu a vložený objekt pro vytváření úloh, který jej zkompiluje.

- `TaskName`Atribut pojmenuje úlohu, v tomto případě `DoNothing` .

- `TaskFactory`Atribut vyjmenovává třídu, která implementuje vložený objekt pro vytváření úloh.

- `AssemblyFile`Atribut poskytuje umístění vloženého objektu pro vytváření úloh. Alternativně můžete použít `AssemblyName` atribut k určení plně kvalifikovaného názvu vložené třídy úlohy Factory, která se obvykle nachází v globální mezipaměti sestavení (GAC).

Zbývající prvky `DoNothing` úkolu jsou prázdné a jsou k dispozici k ilustraci pořadí a struktury vložené úlohy. Robustnější příklad je uveden dále v tomto tématu.

- `ParameterGroup`Element je nepovinný. Je-li tento parametr zadán, deklaruje parametry pro úlohu. Další informace o vstupních a výstupních parametrech naleznete v části [vstupní a výstupní parametry](#input-and-output-parameters) dále v tomto tématu.

- `Task`Element popisuje a obsahuje zdrojový kód úkolu.

- `Reference`Element určuje odkazy na sestavení .NET, která používáte ve svém kódu. To je ekvivalentní přidání odkazu na projekt v aplikaci Visual Studio. `Include`Atribut určuje cestu odkazovaného sestavení.

- `Using`Element vypíše obory názvů, ke kterým chcete získat přístup. To se podobá `Using` příkazu v jazyce Visual C#. `Namespace`Atribut určuje obor názvů, který se má zahrnout.

`Reference` a `Using` elementy jsou Language-nezávislá. Vložené úkoly lze zapsat v jednom z podporovaných jazyků rozhraní .NET CodeDom, například Visual Basic nebo Visual C#.

> [!NOTE]
> Prvky obsažené v `Task` elementu jsou specifické pro objekt pro vytváření úloh, v tomto případě objekt pro vytváření úloh kódu.

### <a name="code-element"></a>Element kódu

Poslední podřízený element, který se má zobrazit v rámci `Task` elementu, je `Code` element. `Code`Element obsahuje nebo vyhledá kód, který chcete zkompilovat do úlohy. Co vložíte do `Code` prvku závisí na tom, jak chcete vytvořit úlohu.

`Language`Atribut určuje jazyk, ve kterém je kód napsán. Přijatelné hodnoty jsou `cs` pro jazyk C# `vb` pro Visual Basic.

`Type`Atribut určuje typ kódu, který se nachází v `Code` elementu.

- Pokud `Type` je hodnota `Class` , pak `Code` element obsahuje kód pro třídu, která je odvozena z <xref:Microsoft.Build.Framework.ITask> rozhraní.

- Pokud `Type` je hodnota `Method` , pak kód definuje přepsání `Execute` metody <xref:Microsoft.Build.Framework.ITask> rozhraní.

- Pokud `Type` je hodnota `Fragment` , pak kód definuje obsah `Execute` metody, ale ne signaturu nebo `return` příkaz.

Samotný kód se obvykle objevuje mezi `<![CDATA[` značkou a `]]>` značkou. Vzhledem k tomu, že kód je v oddílu CDATA, nemusíte se starat o rezervované znaky, například " \<" or "> ".

Alternativně můžete použít `Source` atribut `Code` prvku k určení umístění souboru, který obsahuje kód pro úlohu. Kód ve zdrojovém souboru musí být typu, který je určen `Type` atributem. Pokud `Source` je přítomen atribut, výchozí hodnota `Type` je `Class` . Pokud není k `Source` dispozici, je výchozí hodnota `Fragment` .

> [!NOTE]
> Při definování třídy Task ve zdrojovém souboru musí souhlasit název třídy s `TaskName` atributem odpovídajícího elementu [UsingTask](../msbuild/usingtask-element-msbuild.md) .

## <a name="hello-world"></a>Hello World

 Tady je robustnější vložená úloha s RoslynCodeTaskFactory. V úloze HelloWorld se zobrazí text Hello, World! na výchozím zařízení pro protokolování chyb, což je obvykle systémová konzola nebo okno **výstup** sady Visual Studio. `Reference`Element v příkladu je zahrnut pouze pro ilustraci.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task displays "Hello, world!" -->
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="RoslynCodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="System.Xml"/>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
<![CDATA[
// Display "Hello, world!"
Log.LogError("Hello, world!");
]]>
      </Code>
    </Task>
  </UsingTask>
</Project>
```

Můžete uložit úlohu HelloWorld v souboru s názvem *HelloWorld. targets*a potom ji vyvolat z projektu následujícím způsobem.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="HelloWorld.targets" />
  <Target Name="Hello">
    <HelloWorld />
  </Target>
</Project>
```

## <a name="input-and-output-parameters"></a>Vstupní a výstupní parametry

 Vložené parametry úlohy jsou podřízené prvky `ParameterGroup` elementu. Každý parametr přebírá název elementu, který ho definuje. Tento parametr definuje následující kód `Text` .

```xml
<ParameterGroup>
    <Text />
</ParameterGroup>
```

Parametry mohou mít jeden nebo více z těchto atributů:

- `Required` je volitelný atribut, který je `false` ve výchozím nastavení. Pokud je `true` , pak je vyžadován parametr a před voláním úlohy musí být předána hodnota.

- `ParameterType` je volitelný atribut, který je `System.String` ve výchozím nastavení. Může být nastaven na libovolný plně kvalifikovaný typ, který je buď položka, nebo hodnota, která může být převedena na řetězec a z řetězce pomocí System. Convert. ChangeType. (Jinými slovy, jakýkoli typ, který lze předat do a z vnějšího úkolu.)

- `Output` je volitelný atribut, který je `false` ve výchozím nastavení. Pokud `true` , pak musí být parametru předána hodnota před návratem z metody Execute.

Příklad:

```xml
<ParameterGroup>
    <Expression Required="true" />
    <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
    <Tally ParameterType="System.Int32" Output="true" />
</ParameterGroup>
```

definuje tyto tři parametry:

- `Expression` je požadovaný vstupní parametr typu System. String.

- `Files` je požadovaný vstupní parametr seznamu položek.

- `Tally` je výstupní parametr typu System. Int32.

Pokud `Code` má element `Type` atribut `Fragment` nebo `Method` , pak se automaticky vytvoří vlastnosti pro každý parametr.  V RoslynCodeTaskFactory, pokud `Code` má element `Type` atribut `Class` , pak nemusíte určovat `ParameterGroup` , protože je odvozen ze zdrojového kódu (Jedná se o rozdíl od `CodeTaskFactory` ). V opačném případě musí být vlastnosti explicitně deklarovány ve zdrojovém kódu úlohy a musí přesně odpovídat definicím parametrů.

## <a name="example"></a>Příklad

 Následující vložený úkol zapíše zprávy do protokolu a vrátí řetězec.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="MySample"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Parameter1 ParameterType="System.String" Required="true" />
            <Parameter2 ParameterType="System.String" />
            <Parameter3 ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
              <![CDATA[
              Log.LogMessage(MessageImportance.High, "Hello from an inline task created by Roslyn!");
              Log.LogMessageFromText($"Parameter1: '{Parameter1}'", MessageImportance.High);
              Log.LogMessageFromText($"Parameter2: '{Parameter2}'", MessageImportance.High);
              Parameter3 = "A value from the Roslyn CodeTaskFactory";
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
      <MySample Parameter1="A value for parameter 1" Parameter2="A value for parameter 2">
          <Output TaskParameter="Parameter3" PropertyName="NewProperty" />
      </MySample>

      <Message Text="NewProperty: '$(NewProperty)'" />
    </Target>
</Project>
```

Tyto vložené úlohy můžou kombinovat cesty a získat název souboru.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="PathCombine"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Paths ParameterType="System.String[]" Required="true" />
            <Combined ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            Combined = Path.Combine(Paths);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <UsingTask TaskName="PathGetFileName"
             TaskFactory="RoslynCodeTaskFactory"
             AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Path ParameterType="System.String" Required="true" />
            <FileName ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            FileName = System.IO.Path.GetFileName(Path);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
        <PathCombine Paths="$(Temp);MyFolder;$([System.Guid]::NewGuid()).txt">
            <Output TaskParameter="Combined" PropertyName="MyCombinedPaths" />
        </PathCombine>

        <Message Text="Combined Paths: '$(MyCombinedPaths)'" />

        <PathGetFileName Path="$(MyCombinedPaths)">
            <Output TaskParameter="FileName" PropertyName="MyFileName" />
        </PathGetFileName>

        <Message Text="File name: '$(MyFileName)'" />
    </Target>
</Project>
```

## <a name="provide-backward-compatibility"></a>Zajištění zpětné kompatibility

`RoslynCodeTaskFactory` první se stala dostupná ve verzi MSBuild 15,8. Předpokládejme, že máte situaci, kdy chcete podporovat předchozí verze sady Visual Studio a nástroje MSBuild, kdy služba `RoslynCodeTaskFactory` nebyla k dispozici, ale `CodeTaskFactory` chtěli byste použít stejný skript sestavení. Můžete použít `Choose` konstrukce, která používá `$(MSBuildVersion)` vlastnost k rozhodnutí v čase sestavení, zda se má použít `RoslynCodeTaskFactory` nebo přejít zpět na `CodeTaskFactory` , jako v následujícím příkladu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <Choose>
    <When Condition=" '$(MSBuildVersion.Substring(0,2))' >= 16 Or
    ('$(MSBuildVersion.Substring(0,2))' == 15 And '$(MSBuildVersion.Substring(3,1))' >= 8)">
      <PropertyGroup>
        <TaskFactory>RoslynCodeTaskFactory</TaskFactory>
      </PropertyGroup>
    </When>
    <Otherwise>
      <PropertyGroup>
        <TaskFactory>CodeTaskFactory</TaskFactory>
      </PropertyGroup>
    </Otherwise>
  </Choose>
  
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="$(TaskFactory)"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll">
    <ParameterGroup />
    <Task>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
        <![CDATA[
         Log.LogError("Using RoslynCodeTaskFactory");
      ]]>
      </Code>
    </Task>
  </UsingTask>

  <Target Name="RunTask" AfterTargets="Build">
    <Message Text="MSBuildVersion: $(MSBuildVersion)"/>
    <Message Text="TaskFactory: $(TaskFactory)"/>
    <HelloWorld />
  </Target>

</Project>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Návod: Vytvoření vložené úlohy](../msbuild/walkthrough-creating-an-inline-task.md)
