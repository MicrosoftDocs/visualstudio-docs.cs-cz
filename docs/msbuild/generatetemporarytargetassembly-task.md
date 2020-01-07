---
title: Úloha GenerateTemporaryTargetAssembly – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- build process [WPF MSBuild], XAML page refers to a locally declared type
- GenerateTemporaryTargetAssembly task [WPF MSBuild]
- GenerateTemporaryTargetAssembly task [WPF MSBuild], parameters
- creating an assembly [WPF MSBuild], XAML page refers to a locally declared type
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 634cf365c0cd42e3eb146b74a137a66f742a8730
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594809"
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly – – úloha
Úloha <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> generuje sestavení, pokud alespoň jedna [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] stránka v projektu odkazuje na typ, který je deklarován místně v daném projektu. Vygenerované sestavení je odebráno po dokončení procesu sestavení, nebo pokud proces sestavení není úspěšný.

## <a name="task-parameters"></a>Parametry úlohy

| Parametr | Popis |
|--------------------------| - |
| `AssemblyName` | Povinný parametr **řetězce**<br /><br /> Určuje krátký název sestavení, který je generován pro projekt, a je také názvem cílového sestavení, které je dočasně vygenerováno. Například pokud projekt generuje [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] spustitelný soubor, jehož název je *WinExeAssembly. exe*, parametr **AssemblyName** má hodnotu **WinExeAssembly**. |
| `CompileTargetName` | Povinný parametr **řetězce**<br /><br /> Určuje název [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] cíl, který se používá ke generování sestavení ze souborů zdrojového kódu. Typickou hodnotou pro **CompileTargetName** je **CoreCompile**. |
| `CompileTypeName` | Povinný parametr **řetězce**<br /><br /> Určuje typ kompilace, která je provedena cílem, který je určen parametrem **CompileTargetName** . Pro cíl **CoreCompile** je tato hodnota **zkompilována**. |
| `CurrentProject` | Povinný parametr **řetězce**<br /><br /> Určuje úplnou cestu souboru projektu [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] projektu, který vyžaduje dočasné cílové sestavení. |
| `GeneratedCodeFiles` | Volitelný parametr **ITaskItem []** .<br /><br /> Určuje seznam souborů spravovaného kódu specifických pro jazyk, které byly generovány úlohou [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) . |
| `IntermediateOutputPath` | Povinný parametr **řetězce**<br /><br /> Určuje adresář, do kterého je vygenerováno dočasné cílové sestavení. |
| `MSBuildBinPath` | Povinný parametr **řetězce**<br /><br /> Určuje umístění souboru *MSBuild. exe*, který je požadován pro zkompilování dočasného cílového sestavení. |
| `ReferencePath` | Volitelný parametr **ITaskItem []** .<br /><br /> Určuje seznam sestavení podle cesty a názvu souboru, které jsou odkazovány typy, které jsou zkompilovány do dočasného cílového sestavení. |
| `ReferencePathTypeName` | Povinný parametr **řetězce**<br /><br /> Určuje parametr, který je používán parametrem Target kompilace (**CompileTargetName**), který určuje seznam odkazů na sestavení (**ReferencePath**). Příslušná hodnota je **ReferencePath**. |

## <a name="remarks"></a>Poznámky
První průchod kompilací kódu, který je spuštěn v [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md), kompiluje [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory do binárního formátu. V důsledku toho kompilátor potřebuje seznam odkazovaných sestavení, která obsahují typy používané soubory [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. Pokud však soubor [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] používá typ, který je definován ve stejném projektu, odpovídající sestavení pro daný projekt není vytvořeno, dokud není projekt sestaven. Proto odkaz na sestavení nelze poskytnout během prvního průchodu kompilace kódu.

Místo toho **MarkupCompilePass1** odloží převod [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] souborů, které obsahují odkazy na typy ve stejném projektu, na druhý průchod kompilace kódu, který je spouštěn [MarkupCompilePass2 –](../msbuild/markupcompilepass2-task.md). Před provedením **MarkupCompilePass2 –** je vygenerováno dočasné sestavení. Toto sestavení obsahuje typy, které jsou používány [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory, jejichž průchod kompilací kódu byl odložen. Odkaz na vygenerované sestavení je k dispozici **MarkupCompilePass2 –** při spuštění, aby bylo možné odložit kompilaci [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory převést do binárního formátu.

## <a name="example"></a>Příklad
Následující příklad generuje dočasné sestavení, protože *Page1. XAML* obsahuje odkaz na typ, který je ve stejném projektu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="GenerateTemporaryTargetAssemblyTask">
    <GenerateTemporaryTargetAssembly
      AssemblyName="WPFMSBuildSample"
      CompileTargetName="CoreCompile"
      CompileTypeName="Compile"
      CurrentProject="FullBuild.proj"
      GeneratedCodeFiles="obj\debug\app.g.cs;obj\debug\Page1.g.cs;obj\debug\Page2.g.cs"
      ReferencePath="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll"
      IntermediateOutputPath=".\obj\debug\"
      MSBuildBinPath="$(MSBuildBinPath)"
      ReferencePathTypeName="ReferencePath"/>
  </Target>
</Project>
```

## <a name="see-also"></a>Viz také:
- [Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Sestavení aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Přehled aplikací prohlížeče WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
