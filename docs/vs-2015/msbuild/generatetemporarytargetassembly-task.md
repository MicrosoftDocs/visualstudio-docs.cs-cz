---
title: Úloha GenerateTemporaryTargetAssembly – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2ce412fdeb8d466708f3231cba14718d13720c69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65676654"
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>Úloha generuje sestavení, pokud alespoň jedna [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] Stránka v projektu odkazuje na typ, který je deklarován místně v daném projektu. Vygenerované sestavení je odebráno po dokončení procesu sestavení, nebo pokud proces sestavení není úspěšný.  
  
## <a name="task-parameters"></a>Parametry úlohy  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AssemblyName`|Povinný parametr **řetězce**<br /><br /> Určuje krátký název sestavení, který je generován pro projekt, a je také názvem cílového sestavení, které je dočasně vygenerováno. Například pokud projekt vygeneruje [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] spustitelný soubor, jehož název je **WinExeAssembly.exe**, parametr **AssemblyName** má hodnotu **WinExeAssembly**.|  
|`CompileTargetName`|Povinný parametr **řetězce**<br /><br /> Určuje název [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] cíle, který se používá ke generování sestavení ze souborů zdrojového kódu. Typickou hodnotou pro **CompileTargetName** je **CoreCompile**.|  
|`CompileTypeName`|Povinný parametr **řetězce**<br /><br /> Určuje typ kompilace, která je provedena cílem, který je určen parametrem **CompileTargetName** . Pro cíl **CoreCompile** je tato hodnota **zkompilována**.|  
|`CurrentProject`|Povinný parametr **řetězce**<br /><br /> Určuje úplnou cestu k [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)] souboru projektu pro projekt, který vyžaduje dočasné cílové sestavení.|  
|`GeneratedCodeFiles`|Volitelný parametr **ITaskItem []** .<br /><br /> Určuje seznam souborů spravovaného kódu specifických pro jazyk, které byly generovány úlohou [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) .|  
|`IntermediateOutputPath`|Povinný parametr **řetězce**<br /><br /> Určuje adresář, do kterého je vygenerováno dočasné cílové sestavení.|  
|`MSBuildBinPath`|Povinný parametr **řetězce**<br /><br /> Určuje umístění **MSBuild.exe**, které je vyžadováno pro zkompilování dočasného cílového sestavení.|  
|`ReferencePath`|Volitelný parametr **ITaskItem []** .<br /><br /> Určuje seznam sestavení podle cesty a názvu souboru, které jsou odkazovány typy, které jsou zkompilovány do dočasného cílového sestavení.|  
|`ReferencePathTypeName`|Povinný parametr **řetězce**<br /><br /> Určuje parametr, který je používán parametrem Target kompilace (**CompileTargetName**), který určuje seznam odkazů na sestavení (**ReferencePath**). Příslušná hodnota je **ReferencePath**.|  
  
## <a name="remarks"></a>Poznámky  
 První průchod kompilací kódu, který je spuštěn v [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md), zkompiluje [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubory do binárního formátu. V důsledku toho kompilátor potřebuje seznam odkazovaných sestavení, která obsahují typy používané [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubory. Pokud však [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubor používá typ, který je definován ve stejném projektu, odpovídající sestavení pro daný projekt není vytvořeno, dokud není projekt sestaven. Proto odkaz na sestavení nelze poskytnout během prvního průchodu kompilace kódu.  
  
 Místo toho **MarkupCompilePass1** odloží převod [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] souborů, které obsahují odkazy na typy ve stejném projektu, na druhý průchod kompilace kódu, který je proveden [MarkupCompilePass2 –](../msbuild/markupcompilepass2-task.md). Před provedením **MarkupCompilePass2 –** je vygenerováno dočasné sestavení. Toto sestavení obsahuje typy, které jsou používány soubory, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] jejichž průchod kompilací kódu byl odložen. Odkaz na vygenerované sestavení je k dispozici **MarkupCompilePass2 –** při spuštění, aby bylo možné převést odložené kompilační [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubory do binárního formátu.  
  
## <a name="example"></a>Příklad  
 Následující příklad generuje dočasné sestavení `Page1.xaml` , protože obsahuje odkaz na typ, který je ve stejném projektu.  
  
```  
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
 [Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)   
 [Sestavení aplikace WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Přehled aplikací Prohlížeče WPF XAML](https://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
