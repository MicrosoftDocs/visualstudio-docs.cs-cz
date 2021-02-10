---
title: Úloha CombinePath – | Microsoft Docs
description: Přečtěte si, jak pomocí úlohy MSBuild CombinePath – kombinovat zadané cesty do jedné cesty.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1eb27a311f1b61e3e36b4c9eaa65de7f3fd8f1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939497"
---
# <a name="combinepath-task"></a>CombinePath – úloha

Zkombinuje zadané cesty do jedné cesty.
## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry [úlohy CombinePath –](../msbuild/combinepath-task.md).


|Parametr|Popis|
|---------------|-----------------|
|`BasePath`|Požadovaný parametr `String`.<br /><br /> Základní cesta, která se má zkombinovat s ostatními cestami. Může se jednat o relativní cestu, absolutní cestu nebo prázdnou hodnotu.|
|`Paths`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Seznam jednotlivých cest, které mají být kombinovány s BasePath, aby tvořily kombinovanou cestu. Cesty mohou být relativní nebo absolutní.|
|`CombinedPaths`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Kombinovaná cesta, která je vytvořena touto úlohou.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

 Následující příklad ukazuje, jak vytvořit strukturu výstupní složky pomocí pro vytvoření `CombinePath` vlastnosti `$(OutputDirectory)` kombinováním kořenové cesty `$(PublishRoot)` zřetězené s `$(ReleaseDirectory)` a seznamem podsložek `$(LangDirectories)` .

 ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <PublishRoot>C:\Site1\Release</PublishRoot>
  </PropertyGroup>

  <ItemGroup>
    <LangDirectories Include="en-us\;fr-fr\"/>
  </ItemGroup>

  <Target Name="CreateOutputDirectories" AfterTargets="Build">
    <CombinePath BasePath="$(PublishRoot)" Paths="@(LangDirectories)" >
      <Output TaskParameter="CombinedPaths" ItemName="OutputDirectories"/>
    </CombinePath>
    <MakeDir Directories="@(OutputDirectories)" />
  </Target>
```

Jedinou vlastností, která `CombinePath` umožňuje být seznam `Paths` , je v tomto případě výstup také seznamem. Pokud je tedy `$(PublishRoot)` *C:\Site1 \\* a `$(ReleaseDirectory)` *verze \\* a `@(LangDirectories)` je *en-US \; fr-FR \\*, pak v tomto příkladu se vytvoří tyto složky:

- C:\Site1\Release\en-us\
- C:\Site1\Release\fr-fr\

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
