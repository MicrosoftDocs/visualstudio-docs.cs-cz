---
title: Úlohy MSBuild vložené | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/21/2017
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8cdb171d16b6612562ea21608cdeb622f4ef8bb5
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179044"
---
# <a name="msbuild-inline-tasks"></a>Vložené úlohy nástroje MSBuild
Úlohy nástroje MSBuild se obvykle vytvářejí kompilováním třídy, která implementuje <xref:Microsoft.Build.Framework.ITask> rozhraní. Další informace najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).  
  
 Počínaje rozhraním .NET Framework verze 4, můžete vytvořit úlohy vložené v souboru projektu. Není nutné vytvořit samostatné sestavení pro hostování úkolu. To umožňuje snadněji sledovat, zdrojový kód a snazší nasazování úkol. Zdrojový kód je integrovaná do skriptu.  
  

 V MSBuild 15.8 [RoslynCodeTaskFactory](../msbuild/msbuild-roslyncodetaskfactory.md) byla přidána, které můžete vytvořit .NET Standard multiplatformní vložené úlohy.  Pokud je potřeba použít vložené úlohy v rozhraní .NET Core, je nutné použít RoslynCodeTaskFactory.
## <a name="the-structure-of-an-inline-task"></a>Struktura vložené úlohy  
 Vložené úlohy je obsažena ve [UsingTask](../msbuild/usingtask-element-msbuild.md) elementu. Vložené úlohy a `UsingTask` element, který jej obsahuje, jsou typicky zahrnuty v *.targets* souboru a importovat do jiných souborů projektu podle potřeby. Tady je základní vložené úlohy. Všimněte si, že to nemá žádný účinek.  
  
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
  
 `UsingTask` Element v tomto příkladu má tři atributy, které popisují úlohy a vložené továrny úloh, který zkompiluje ho.  
  
-   `TaskName` Úkolu, názvy atributů v tomto případě `DoNothing`.  
  
-   `TaskFactory` Názvy atributů třídy, která implementuje vložený objekt pro vytváření úloh.  
  
-   `AssemblyFile` Atribut poskytuje umístění továrny úloh vložené. Alternativně můžete použít `AssemblyName` atribut zadat plně kvalifikovaný název třídu objektů factory vložené úlohy, která se obvykle nachází v globální mezipaměti sestavení (GAC).  

Zbývající prvky `DoNothing` úloh jsou prázdné a jsou k dispozici pro ilustraci pořadí a struktura vložené úlohy. Robustnější příkladu je uvedené dále v tomto tématu.  
  
-   `ParameterGroup` Element je volitelné. -Li zadána, deklaruje parametry pro úlohu. Další informace o vstupních a výstupních parametrech najdete v části [vstupní a výstupní parametry](#input-and-output-parameters) dále v tomto tématu.  
  
-   `Task` Prvek popisuje a obsahuje zdrojový kód úkolu.  
  
-   `Reference` Prvek určuje odkazy na sestavení .NET, které používáte ve vašem kódu. Jde o ekvivalent k přidání odkazu na projekt v sadě Visual Studio. `Include` Atribut určuje cestu k odkazovanému sestavení.  
  
-   `Using` Prvek obsahuje seznam obory názvů, které chcete získat přístup. To se podobá `Using` příkaz v jazyce Visual C#. `Namespace` Atribut určuje obor názvů, které chcete zahrnout.  

`Reference` a `Using` prvky jsou jazykově nezávislé. Vložené úlohy je možné psát v jedné z podporovaných jazyků .NET CodeDom, například Visual Basic nebo Visual C#.  
  
> [!NOTE]
>  Elementů obsažených `Task` element jsou specifické pro továrny úloh, v tomto případě továrny úloh kódu.  
  
### <a name="code-element"></a>Element kódu  
 Poslední podřízený element má zobrazit `Task` prvek je `Code` elementu. `Code` Obsahuje element, nebo vyhledá kód, který má být zkompilovány do úlohy. Umístit do `Code` element závisí na způsob zápisu úkolu.  
  
 `Language` Atribut určuje jazyk, ve kterém je napsán kód. Přípustné hodnoty jsou `cs` pro jazyk C#, `vb` v jazyce Visual Basic.  
  
 `Type` Atribut určuje typ kódu, který se nachází v `Code` elementu.  
  
-   Pokud hodnota `Type` je `Class`, pak bude `Code` prvek obsahuje kód, který je odvozen od třídy <xref:Microsoft.Build.Framework.ITask> rozhraní.  
  
-   Pokud hodnota `Type` je `Method`, kód definuje přepsání `Execute` metodu <xref:Microsoft.Build.Framework.ITask> rozhraní.  
  
-   Pokud hodnota `Type` je `Fragment`, kód definuje obsah `Execute` metody, ale ne podpis nebo `return` příkazu.  

Samotný kód se obvykle zobrazuje mezi `<![CDATA[` značky a `]]>` značky. Protože kód je v oddílu CDATA, si nemusíte dělat starosti o uvozovací znaky vyhrazené znaky, například "\<" nebo ">".  
  
Alternativně můžete použít `Source` atribut `Code` element k určení umístění souboru, který obsahuje kód pro vaše úlohy. Kód ve zdrojovém souboru musí být typu, který je určen `Type` atribut. Pokud `Source` atribut je k dispozici, výchozí hodnota `Type` je `Class`. Pokud `Source` není k dispozici, výchozí hodnota je `Fragment`.  
  
> [!NOTE]
>  Při definování třídy úloh ve zdrojovém souboru, název třídy, musíte souhlasit s `TaskName` atribut k odpovídající položce [UsingTask](../msbuild/usingtask-element-msbuild.md) elementu.  
  
## <a name="helloworld"></a>Hello World  
 Tady je robustnější vložené úlohy. Úloha HelloWorld zobrazí "Hello, world!" v zařízení výchozí protokolování chyb, což je obvykle systémové konzoly nebo Visual Studio **výstup** okna. `Reference` Element v tomto příkladu je zahrnuta pouze pro ilustraci.  
  
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
  
 Úloha HelloWorld může uložit v souboru s názvem *HelloWorld.targets*a pak ho následujícím způsobem vyvolat z projektu.  
  
```xml  
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <Import Project="HelloWorld.targets" />  
  <Target Name="Hello">  
    <HelloWorld />  
  </Target>  
</Project>  
```  
  
## <a name="input-and-output-parameters"></a>Vstupní a výstupní parametry  
 Parametry úlohy vložené jsou podřízené prvky `ParameterGroup` elementu. Každý parametr přebírá název elementu, který ji definuje. Následující kód definuje parametr `Text`.  
  
```xml  
<ParameterGroup>  
    <Text />  
</ParameterGroup>  
```  
  
 Parametry může mít jeden nebo více z těchto atributů:  
  
-   `Required` je volitelný atribut, který je `false` ve výchozím nastavení. Pokud `true`, pak parametr je povinný a musí zadat hodnota před voláním úkolu.  
  
-   `ParameterType` je volitelný atribut, který je `System.String` ve výchozím nastavení. Může být nastavená na všechny plně kvalifikovaný typ, který je buď hodnotu, která lze převést do a z řetězce pomocí System.Convert.ChangeType nebo položky. (Jinými slovy, jakýkoli typ, který lze předat do a z externích úkolů.)  
  
-   `Output` je volitelný atribut, který je `false` ve výchozím nastavení. Pokud `true`, pak tento parametr se musí předávat hodnotu před návratem z metody Execute.  
  
Například  
  
```xml  
<ParameterGroup>  
    <Expression Required="true" />  
      <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />  
    <Tally ParameterType="System.Int32" Output="true" />  
</ParameterGroup>  
```  
  
definuje tyto tři parametry:  
  
-   `Expression` je povinný vstupní parametr typu System.String.  
  
-   `Files` je vstupní parametr požadovanou položku seznamu.  
  
-   `Tally` je výstupní parametr typu System.Int32.  

Pokud `Code` element má `Type` atribut `Fragment` nebo `Method`, pak vlastností se automaticky vytvoří pro každý parametr. V opačném případě vlastnosti musí být explicitně deklarovány ve zdrojovém kódu úkolu a musí přesně odpovídat jejich definice parametru.  
  
## <a name="example"></a>Příklad  
 Následující vložené úlohy nahradí všechny výskyty token v daném souboru předané hodnoty.  
  
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
  
## <a name="see-also"></a>Viz také:  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Návod: Vytvoření vložené úlohy](../msbuild/walkthrough-creating-an-inline-task.md)
