---
title: Vestavěné úkoly msbuild | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: e68f2bdf0559dc2bea6bd349dbf5f9bedca3671e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633314"
---
# <a name="msbuild-inline-tasks"></a>MSBuild vsazené úkoly

Úlohy MSBuild jsou obvykle vytvořeny kompilací třídy, která implementuje <xref:Microsoft.Build.Framework.ITask> rozhraní. Další informace naleznete v [tématu Úkoly](../msbuild/msbuild-tasks.md).

 Počínaje rozhraním .NET Framework verze 4 můžete vytvořit úkoly vsazené do souboru projektu. Není třeba vytvořit samostatné sestavení pro hostování úkolu. To usnadňuje sledování zdrojového kódu a snadnější nasazení úlohy. Zdrojový kód je integrován do skriptu.

 V MSBuild 15.8 byla přidána [RoslynCodeTaskFactory,](../msbuild/msbuild-roslyncodetaskfactory.md) která může vytvářet inline úlohy .NET Standard napříč platformami.  Pokud potřebujete použít vsazené úlohy na .NET Core, musíte použít RoslynCodeTaskFactory.
## <a name="the-structure-of-an-inline-task"></a>Struktura vsazeného úkolu

 Vázací úkol je obsažen [pomocí usingtask](../msbuild/usingtask-element-msbuild.md) element. Vložených úkolů a `UsingTask` prvek, který jej obsahuje, jsou obvykle zahrnuty do souboru *.targets* a podle potřeby importovány do jiných souborů projektu. Zde je základní vsazený úkol. Všimněte si, že to nedělá nic.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task does nothing. -->
  <UsingTask
    TaskName="DoNothing"
    TaskFactory="CodeTaskFactory"
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

- Prvek `ParameterGroup` je volitelný. Pokud je zadán, deklaruje parametry pro úlohu. Další informace o vstupních a výstupních parametrech naleznete [v tématu Vstupní a výstupní parametry](#input-and-output-parameters) dále v tomto tématu.

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

## <a name="helloworld"></a>Helloworld

 Zde je robustnější vslaný úkol. Úloha HelloWorld zobrazí "Hello, world!" ve výchozím zařízení pro protokolování chyb, což je obvykle systémová konzola nebo okno Visual Studio **Output.** Prvek `Reference` v příkladu je zahrnuta pouze pro ilustraci.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task displays "Hello, world!" -->
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="CodeTaskFactory"
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

Pokud `Code` má prvek `Type` atribut `Fragment` `Method`nebo , pak vlastnosti jsou automaticky vytvořeny pro každý parametr. V opačném případě musí být vlastnosti explicitně deklarovány ve zdrojovém kódu úlohy a musí přesně odpovídat jejich definicím parametrů.

## <a name="example"></a>Příklad

 Následující váděná úloha nahradí každý výskyt tokenu v daném souboru danou hodnotou.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

  <UsingTask TaskName="TokenReplace" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll">
    <ParameterGroup>
      <Path ParameterType="System.String" Required="true" />
      <Token ParameterType="System.String" Required="true" />
      <Replacement ParameterType="System.String" Required="true" />
    </ParameterGroup>
    <Task>
      <Code Type="Fragment" Language="cs"><![CDATA[
string content = File.ReadAllText(Path);
content = content.Replace(Token, Replacement);
File.WriteAllText(Path, content);

]]></Code>
    </Task>
  </UsingTask>

  <Target Name='Demo' >
    <TokenReplace Path="C:\Project\Target.config" Token="$MyToken$" Replacement="MyValue"/>
  </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Návod: Vytvoření vřádkové úlohy](../msbuild/walkthrough-creating-an-inline-task.md)
