---
title: Generatetemporarytargetassembly – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5d4b5ee29ed19f121c6da357fa20242f6762e51c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892945"
---
# <a name="generatetemporarytargetassembly-task"></a>Generatetemporarytargetassembly – úloha
<xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> Úloh generuje sestavení, pokud se alespoň jeden [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] stránky v projektu odkazuje na typ, který je deklarován místně v daném projektu. Generované sestavení se odebere po dokončení procesu sestavení, nebo pokud proces sestavení se nezdaří.  
  
## <a name="task-parameters"></a>Parametry úlohy  
  
| Parametr | Popis |
|--------------------------| - |
| `AssemblyName` | Vyžaduje **řetězec** parametru.<br /><br /> Určuje krátký název sestavení, které se generuje pro projekt a je také název cílového sestavení, který je dočasně generován. Například, pokud projekt vygeneruje [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] spustitelný soubor, jehož název je *WinExeAssembly.exe*, **AssemblyName** parametr má hodnotu **WinExeAssembly**. |
| `CompileTargetName` | Vyžaduje **řetězec** parametru.<br /><br /> Určuje název [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] cíl, který se používá ke generování sestavení ze souborů zdrojového kódu. Typická hodnota **CompileTargetName** je **CoreCompile**. |
| `CompileTypeName` | Vyžaduje **řetězec** parametru.<br /><br /> Určuje typ kompilaci, která se provádí v cíli, která je zadána **CompileTargetName** parametru. Pro **CoreCompile** cíl, tato hodnota je **kompilaci**. |
| `CurrentProject` | Vyžaduje **řetězec** parametru.<br /><br /> Určuje úplnou cestu [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] soubor projektu pro projekt, který vyžaduje dočasné cílového sestavení. |
| `GeneratedCodeFiles` | Volitelné **[] ITaskItem** parametru.<br /><br /> Určuje seznam spravovaného kódu specifické pro jazyk soubory, které byly vytvořeny [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) úloh. |
| `IntermediateOutputPath` | Vyžaduje **řetězec** parametru.<br /><br /> Určuje adresář, generovaný dočasné cílového sestavení. |
| `MSBuildBinPath` | Vyžaduje **řetězec** parametru.<br /><br /> Určuje umístění *MSBuild.exe*, která se vyžaduje pro kompilaci dočasné cílového sestavení. |
| `ReferencePath` | Volitelné **[] ITaskItem** parametru.<br /><br /> Určuje seznam sestavení, cestu a název souboru, který je odkazováno dle typy, které jsou kompilovány do sestavení dočasný cílový. |
| `ReferencePathTypeName` | Vyžaduje **řetězec** parametru.<br /><br /> Určuje parametr, který je používán cíl kompilace (**CompileTargetName**) parametr, který určuje seznam odkazů na sestavení (**ReferencePath**). Odpovídající hodnota je **ReferencePath**. |
  
## <a name="remarks"></a>Poznámky  
 První fáze kompilace kódu, který běží podle [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md), zkompiluje [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory do binárního formátu. V důsledku toho kompilátor musí seznam odkazovaných sestavení, které obsahují typy, které jsou používány [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory. Nicméně pokud [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubor používá typ, který je definován ve stejném projektu, odpovídající sestavení pro tento projekt není vytvořeno, dokud sestavení projektu. Proto se odkaz na sestavení nelze zadat při prvním průchodu kód kompilace.  
  
 Místo toho **MarkupCompilePass1** odloží převodu [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] předat soubory, které obsahují odkazy na typy v rámci jednoho projektu do druhého kompilace kódu, který provádí [markupcompilepass2 –](../msbuild/markupcompilepass2-task.md). Před **markupcompilepass2 –** se provedl a vytvořil dočasný sestavení je generováno. Toto sestavení obsahuje typy, které jsou používány [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory, jehož značky kompilace pass byla odložena. Odkaz na vygenerované sestavení je k dispozici na **markupcompilepass2 –** během spuštění umožňující odložené kompilace [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory převést do binárního formátu.  
  
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
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Referenční dokumentace úlohy](../msbuild/wpf-msbuild-task-reference.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Sestavení aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [Přehled aplikací prohlížeče WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)