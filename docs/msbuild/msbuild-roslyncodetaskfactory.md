---
title: MSBuild Vázací úkoly s RoslynCodeTaskFactory | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 658302de187d6bbeab67dedaaa816709f00436ed
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865372"
---
# <a name="msbuild-inline-tasks-with-roslyncodetaskfactory"></a>MSBuild vestavěné úlohy s RoslynCodeTaskFactory

Podobně jako [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), RoslynCodeTaskFactory používá kompilátory Roslyn napříč platformami ke generování sestavení úloh v paměti pro použití jako vsazené úlohy.  Úlohy RoslynCodeTaskFactory cílí na standard .NET a mohou pracovat na rozhraní .NET Framework a .NET Core runtimes, stejně jako na jiných platformách, jako je Linux a Mac OS.

>[!NOTE]
>RoslynCodeTaskFactory je k dispozici pouze v MSBuild 15.8 a vyšší. Verze MSBuild postupujte podle verzí sady Visual Studio, takže RoslynCodeTaskFactory je k dispozici v sadě Visual Studio 15.8 a vyšší.

## <a name="the-structure-of-an-inline-task-with-roslyncodetaskfactory"></a>Struktura inline úkolu s RoslynCodeTaskFactory

 RoslynCodeTaskFactory inline úkoly jsou deklarovány stejným způsobem jako [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), jediný rozdíl je, že cíl .NET Standard.  Vložených úkolů a `UsingTask` prvek, který jej obsahuje, jsou obvykle zahrnuty do souboru *.targets* a podle potřeby importovány do jiných souborů projektu. Zde je základní vsazený úkol. Všimněte si, že to nedělá nic.

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

 Prvek `UsingTask` v příkladu má tři atributy, které popisují úkol a inline task factory, který jej zkompiluje.

- Atribut `TaskName` pojmenuje úkol, v `DoNothing`tomto případě .

- Atribut `TaskFactory` pojmenuje třídu, která implementuje inline task factory.

- Atribut `AssemblyFile` udává umístění inline task factory. Případně můžete `AssemblyName` atribut použít k určení plně kvalifikovaného názvu třídy inline task factory, která se obvykle nachází v globální mezipaměti sestavení (GAC).

Zbývající prvky `DoNothing` úkolu jsou prázdné a jsou k dispozici pro ilustraci pořadí a strukturu včleněného úkolu. Podrobnější příklad je uveden dále v tomto tématu.

- Prvek `ParameterGroup` je volitelný. Pokud je zadán, deklaruje parametry pro úlohu. Další informace o vstupních a výstupních parametrech naleznete v tématu [Vstupní a výstupní parametry](#input-and-output-parameters) dále v tomto tématu.

- Prvek `Task` popisuje a obsahuje zdrojový kód úlohy.

- Prvek `Reference` určuje odkazy na sestavení .NET, které používáte v kódu. To je ekvivalentní přidání odkazu na projekt v sadě Visual Studio. Atribut `Include` určuje cestu odkazovaného sestavení.

- Prvek `Using` obsahuje seznam oborů názvů, ke kterým chcete získat přístup. To se `Using` podobá příkazu v jazyce Visual C#. Atribut `Namespace` určuje obor názvů, který má být zahrnut.

`Reference`a `Using` prvky jsou jazykově nevýrazné. Vložená úloha může být zapsána v některém z podporovaných jazyků .NET CodeDom, například v jazyce Visual Basic nebo Visual C#.

> [!NOTE]
> Prvky obsažené `Task` v elementu jsou specifické pro továrnu úloh, v tomto případě továrnu úloh kódu.

### <a name="code-element"></a>Element kódu

Poslední podřízený prvek, `Task` který se `Code` zobrazí v rámci prvku je prvek. Prvek `Code` obsahuje nebo vyhledá kód, který chcete zkompilovat do úkolu. Co vložíte `Code` do prvku, závisí na tom, jak chcete úkol napsat.

Atribut `Language` určuje jazyk, ve kterém je kód zapsán. Přijatelné hodnoty `cs` jsou pro `vb` C#, pro visual basic.

Atribut `Type` určuje typ kódu, který se `Code` nachází v prvku.

- Pokud `Type` je hodnota `Class`, `Code` pak prvek obsahuje kód pro třídu, která je odvozena <xref:Microsoft.Build.Framework.ITask> z rozhraní.

- Pokud `Type` je `Method`hodnota , pak kód definuje přepsání `Execute` metody <xref:Microsoft.Build.Framework.ITask> rozhraní.

- Pokud `Type` je hodnota `Fragment`, pak kód definuje obsah `Execute` metody, ale ne `return` podpis nebo příkaz.

Samotný kód se obvykle `<![CDATA[` zobrazuje mezi `]]>` značkou a značkou. Vzhledem k tomu, že kód je v části CDATA, nemusíte se\<starat o úniku vyhrazené znaky, například " " nebo ">".

Případně můžete pomocí atributu `Source` `Code` prvku určit umístění souboru, který obsahuje kód pro váš úkol. Kód ve zdrojovém souboru musí být typu, který je určen atributem. `Type` Pokud `Source` je atribut přítomen, výchozí `Type` `Class`hodnota je . Pokud `Source` není k dispozici, `Fragment`výchozí hodnota je .

> [!NOTE]
> Při definování třídy úkolu ve zdrojovém souboru `TaskName` musí název třídy souhlasit s atributem odpovídajícího prvku [UsingTask.](../msbuild/usingtask-element-msbuild.md)

## <a name="hello-world"></a>Hello World

 Zde je robustnější inline úkol s RoslynCodeTaskFactory. Úloha HelloWorld zobrazí "Hello, world!" ve výchozím zařízení pro protokolování chyb, což je obvykle systémová konzola nebo okno Visual Studio **Output.** Prvek `Reference` v příkladu je zahrnuta pouze pro ilustraci.

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

Úlohu HelloWorld můžete uložit do souboru s názvem *HelloWorld.targets*a potom ji vyvolat z projektu následujícím způsobem.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="HelloWorld.targets" />
  <Target Name="Hello">
    <HelloWorld />
  </Target>
</Project>
```

## <a name="input-and-output-parameters"></a>Vstupní a výstupní parametry

 Parametry vřádítek jsou `ParameterGroup` podřízené prvky prvku. Každý parametr přebírá název prvku, který jej definuje. Následující kód definuje parametr `Text`.

```xml
<ParameterGroup>
    <Text />
</ParameterGroup>
```

Parametry mohou mít jeden nebo více z těchto atributů:

- `Required`je volitelný atribut, `false` který je ve výchozím nastavení. Pokud `true`, pak parametr je povinný a musí být uvedena hodnota před voláním úkolu.

- `ParameterType`je volitelný atribut, `System.String` který je ve výchozím nastavení. Může být nastavena na libovolný plně kvalifikovaný typ, který je buď položkou, nebo hodnotou, kterou lze převést na řetězec a z něj pomocí system.convert.changetype. (Jinými slovy, libovolný typ, který lze předat externímu úkolu a z ní.)

- `Output`je volitelný atribut, `false` který je ve výchozím nastavení. Pokud `true`, pak parametr musí být uvedena hodnota před vrácením z Execute metoda.

Například:

```xml
<ParameterGroup>
    <Expression Required="true" />
    <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
    <Tally ParameterType="System.Int32" Output="true" />
</ParameterGroup>
```

definuje tyto tři parametry:

- `Expression`je povinný vstupní parametr typu System.String.

- `Files`je povinný vstupní parametr seznamu položek.

- `Tally`je výstupní parametr typu System.Int32.

Pokud `Code` má prvek `Type` atribut `Fragment` `Method`nebo , pak vlastnosti jsou automaticky vytvořeny pro každý parametr.  V RoslynCodeTaskFactory, `Code` pokud prvek `Type` má `Class`atribut , pak není `ParameterGroup`nutné zadat , protože je odvozen ze zdrojového `CodeTaskFactory`kódu (to je rozdíl od ). V opačném případě musí být vlastnosti explicitně deklarovány ve zdrojovém kódu úlohy a musí přesně odpovídat jejich definicím parametrů.

## <a name="example"></a>Příklad

 Následující vložkový úkol protokoluje některé zprávy a vrátí řetězec.

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

Tyto vsazené úkoly mohou kombinovat cesty a získat název souboru.

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

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Návod: Vytvoření vřádkové úlohy](../msbuild/walkthrough-creating-an-inline-task.md)
