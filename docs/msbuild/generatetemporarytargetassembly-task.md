---
title: Generovat úkol Dočasného cíleního sestavení | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 69333b87720513244e90c131f052d11099b62e35
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634042"
---
# <a name="generatetemporarytargetassembly-task"></a>Úkol Generovat dočasné cílovou sestavě

Úkol <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> generuje sestavení, pokud alespoň jedna stránka XAML v projektu odkazuje na typ, který je deklarován místně v tomto projektu. Generované sestavení je odebráno po dokončení procesu sestavení nebo pokud se proces sestavení nezdaří.

## <a name="task-parameters"></a>Parametry úlohy

| Parametr | Popis |
|--------------------------| - |
| `AssemblyName` | Povinný **parametr String.**<br /><br /> Určuje krátký název sestavení, které je generováno pro projekt a je také název cílového sestavení, které je dočasně generováno. Například pokud projekt generuje spustitelný soubor systému Windows, jehož název je *WinExeAssembly.exe*, **parametr AssemblyName** má hodnotu **WinExeAssembly**. |
| `CompileTargetName` | Povinný **parametr String.**<br /><br /> Určuje název cíle MSBuild, který se používá ke generování sestavení ze souborů zdrojového kódu. Typická hodnota **compiletargetname** je **CoreCompile**. |
| `CompileTypeName` | Povinný **parametr String.**<br /><br /> Určuje typ kompilace, která je prováděna cílem, který je určen parametrem **CompileTargetName.** Pro **corecompile** cíl tato hodnota je **Compile**. |
| `CurrentProject` | Povinný **parametr String.**<br /><br /> Určuje úplnou cestu k souboru projektu MSBuild pro projekt, který vyžaduje dočasné cílové sestavení. |
| `GeneratedCodeFiles` | Volitelný parametr **ITaskItem[].**<br /><br /> Určuje seznam souborů spravovaného kódu specifických pro jazyk, které byly generovány úlohou [MarkupCompilePass1.](../msbuild/markupcompilepass1-task.md) |
| `IntermediateOutputPath` | Povinný **parametr String.**<br /><br /> Určuje adresář, do kterého je generováno dočasné cílové sestavení. |
| `MSBuildBinPath` | Povinný **parametr String.**<br /><br /> Určuje umístění souboru *MSBuild.exe*, který je nutný ke kompilaci dočasného cílového sestavení. |
| `ReferencePath` | Volitelný parametr **ITaskItem[].**<br /><br /> Určuje seznam sestavení podle cesty a názvu souboru, na které odkazují typy, které jsou kompilovány do dočasného cílového sestavení. |
| `ReferencePathTypeName` | Povinný **parametr String.**<br /><br /> Určuje parametr, který používá parametr compile target (**CompileTargetName**), který určuje seznam odkazů na sestavení (**ReferencePath**). Příslušnou hodnotou je **ReferencePath**. |

## <a name="remarks"></a>Poznámky

První průchod kompilace značek, který je spuštěn [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md), kompiluje soubory XAML do binárního formátu. V důsledku toho kompilátor potřebuje seznam odkazovaných sestavení, které obsahují typy, které jsou používány soubory XAML. Pokud však soubor XAML používá typ, který je definován ve stejném projektu, odpovídající sestavení pro tento projekt není vytvořeno, dokud není projekt sestaven. Proto nelze poskytnout odkaz na sestavení během prvního průchodu kompilace značek.

Místo toho **MarkupCompilePass1** odkládá převod souborů XAML, které obsahují odkazy na typy ve stejném projektu na druhý průchod kompilace značky, který je proveden [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md). Před **MarkupCompilePass2** je spuštěn, dočasné sestavení je generována. Toto sestavení obsahuje typy, které jsou používány soubory XAML, jejichž průchod kompilace značky byl odložen. Odkaz na generované sestavení je k dispozici **MarkupCompilePass2** při spuštění, aby odložené kompilace XAML soubory, které mají být převedeny do binárního formátu.

## <a name="example"></a>Příklad

Následující příklad generuje dočasné sestavení, protože *Page1.xaml* obsahuje odkaz na typ, který je ve stejném projektu.

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

## <a name="see-also"></a>Viz také

- [WPF MSBuild odkaz](../msbuild/wpf-msbuild-reference.md)
- [Odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Vytvoření aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Přehled aplikací prohlížeče WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
