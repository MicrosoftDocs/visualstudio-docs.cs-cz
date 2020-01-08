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
ms.openlocfilehash: eb91ffd6ad626a148c3f3ad71c307fc0d0df2c75
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585896"
---
# <a name="msbuild-inline-tasks-with-roslyncodetaskfactory"></a>Vložené úlohy nástroje MSBuild s RoslynCodeTaskFactory
Podobně jako [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), RoslynCodeTaskFactory využívá kompilátory Roslyn pro různé platformy ke generování sestavení úloh v paměti pro použití jako vložené úkoly.  RoslynCodeTaskFactory úkoly cílí na .NET Standard a můžou pracovat na modulech runtime .NET Framework a .NET Core i na jiných platformách, jako je Linux a Mac OS.

>[!NOTE]
>RoslynCodeTaskFactory je k dispozici pouze v MSBuild 15,8 a vyšších.

## <a name="the-structure-of-an-inline-task-with-roslyncodetaskfactory"></a>Struktura vložené úlohy pomocí RoslynCodeTaskFactory
 Vložené úkoly RoslynCodeTaskFactory jsou deklarovány stejným způsobem jako [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), jediným rozdílem, že cílí na .NET Standard.  Vložená úloha a prvek `UsingTask`, který obsahuje, jsou obvykle zahrnuty do souboru *. targets* a importovány do jiných souborů projektu podle potřeby. Zde je základní vložená úloha. Všimněte si, že nedělá nic.

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

 Element `UsingTask` v příkladu má tři atributy, které popisují úlohu a vložený objekt pro vytváření úloh, který ho zkompiluje.

- Atribut `TaskName` pojmenuje úkol, v tomto případě `DoNothing`.

- Atribut `TaskFactory` pojmenovává třídu, která implementuje vložený objekt pro vytváření úloh.

- Atribut `AssemblyFile` poskytuje umístění vloženého objektu pro vytváření úloh. Alternativně můžete použít atribut `AssemblyName` k určení plně kvalifikovaného názvu vložené třídy úlohy Factory, která se obvykle nachází v globální mezipaměti sestavení (GAC).

Zbývající prvky `DoNothing` úlohy jsou prázdné a jsou k dispozici k ilustraci pořadí a struktury vložené úlohy. Robustnější příklad je uveden dále v tomto tématu.

- Element `ParameterGroup` je nepovinný. Je-li tento parametr zadán, deklaruje parametry pro úlohu. Další informace o vstupních a výstupních parametrech naleznete v části [vstupní a výstupní parametry](#input-and-output-parameters) dále v tomto tématu.

- Element `Task` popisuje a obsahuje zdrojový kód úkolu.

- Element `Reference` Určuje odkazy na sestavení .NET, která používáte ve svém kódu. To je ekvivalentní přidání odkazu na projekt v aplikaci Visual Studio. Atribut `Include` Určuje cestu odkazovaného sestavení.

- Element `Using` obsahuje seznam oborů názvů, ke kterým chcete získat přístup. To se podobá příkazu `Using` v vizuálu C#. Atribut `Namespace` určuje obor názvů, který se má zahrnout.

prvky `Reference` a `Using` jsou nezávislá jazyka. Vložené úkoly lze zapsat v libovolném z podporovaných jazyků rozhraní .NET CodeDom, například Visual Basic nebo vizuálu C#.

> [!NOTE]
> Prvky, které jsou obsaženy v prvku `Task`, jsou specifické pro objekt pro vytváření úloh, v tomto případě objekt pro vytváření úloh kódu.

### <a name="code-element"></a>Element kódu
Poslední podřízený element, který se má zobrazit v prvku `Task` je `Code` element. Element `Code` obsahuje nebo vyhledá kód, který chcete zkompilovat do úlohy. Co vložíte do prvku `Code` závisí na tom, jak chcete vytvořit úlohu.

Atribut `Language` určuje jazyk, ve kterém je kód napsán. Přijatelné hodnoty jsou `cs` pro C#`vb` Visual Basic.

Atribut `Type` určuje typ kódu, který se nachází v prvku `Code`.

- Pokud je hodnota `Type` `Class`, pak element `Code` obsahuje kód pro třídu, která je odvozena z rozhraní <xref:Microsoft.Build.Framework.ITask>.

- Pokud je hodnota `Type` `Method`, pak kód definuje přepsání metody `Execute` <xref:Microsoft.Build.Framework.ITask> rozhraní.

- Pokud je hodnota `Type` `Fragment`, pak kód definuje obsah metody `Execute`, ale ne signaturu nebo příkaz `return`.

Samotný kód se obvykle zobrazuje mezi značkou `<![CDATA[` a značkou `]]>`. Vzhledem k tomu, že kód je v oddílu CDATA, nemusíte se starat o rezervované znaky, například "\<" nebo ">".

Alternativně můžete použít atribut `Source` elementu `Code` k určení umístění souboru, který obsahuje kód pro úlohu. Kód ve zdrojovém souboru musí být typu, který je určen atributem `Type`. Pokud je přítomen atribut `Source`, je výchozí hodnota `Type` `Class`. Pokud `Source` není k dispozici, je výchozí hodnota `Fragment`.

> [!NOTE]
> Při definování třídy Task ve zdrojovém souboru musí souhlasit název třídy s atributem `TaskName` odpovídajícího elementu [UsingTask](../msbuild/usingtask-element-msbuild.md) .

## <a name="hello-world"></a>Hello World
 Tady je robustnější vložená úloha s RoslynCodeTaskFactory. V úloze HelloWorld se zobrazí text Hello, World! na výchozím zařízení pro protokolování chyb, což je obvykle systémová konzola nebo okno **výstup** sady Visual Studio. Element `Reference` v příkladu je zahrnut pouze pro ilustraci.

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
 Vložené parametry úlohy jsou podřízené prvky `ParameterGroup`ho prvku. Každý parametr přebírá název elementu, který ho definuje. Následující kód definuje parametr `Text`.

```xml
<ParameterGroup>
    <Text />
</ParameterGroup>
```

Parametry mohou mít jeden nebo více z těchto atributů:

- `Required` je volitelný atribut, který je ve výchozím nastavení `false`. Je-li `true`, je vyžadován parametr a před voláním úlohy musí být předána hodnota.

- `ParameterType` je volitelný atribut, který je ve výchozím nastavení `System.String`. Může být nastaven na libovolný plně kvalifikovaný typ, který je buď položka, nebo hodnota, která může být převedena na řetězec a z řetězce pomocí System. Convert. ChangeType. (Jinými slovy, jakýkoli typ, který lze předat do a z vnějšího úkolu.)

- `Output` je volitelný atribut, který je ve výchozím nastavení `false`. Pokud `true`, musí být parametru předána hodnota před návratem z metody Execute.

Například

```xml
<ParameterGroup>
    <Expression Required="true" />
    <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
    <Tally ParameterType="System.Int32" Output="true" />
</ParameterGroup>
```

definuje tyto tři parametry:

- `Expression` je povinný vstupní parametr typu System. String.

- `Files` je požadovaný vstupní parametr seznamu položek.

- `Tally` je výstupní parametr typu System. Int32.

Pokud má element `Code` `Type` atribut `Fragment` nebo `Method`, jsou automaticky vytvořeny vlastnosti pro každý parametr. V opačném případě musí být vlastnosti explicitně deklarovány ve zdrojovém kódu úlohy a musí přesně odpovídat definicím parametrů.

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

## <a name="see-also"></a>Viz také:
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Návod: Vytvoření vložené úlohy](../msbuild/walkthrough-creating-an-inline-task.md)
