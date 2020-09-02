---
title: Úloha Markupcompilepass2 – | Microsoft Docs
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
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
ms.assetid: 1d25689a-d21f-4b05-be26-95aa0ed4fd03
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 47e27dbfa221a9476488d563ae2a48235a08f769
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703467"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>Úloha provádí kompilaci kódu za sekundu do [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] souborů, které odkazují na typy ve stejném projektu.  
  
## <a name="task-parameters"></a>Parametry úlohy  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Volitelný **logický** parametr.<br /><br /> Určuje, zda má být úloha spuštěna samostatně <xref:System.AppDomain> . Pokud tento parametr vrátí **hodnotu false**, úloha bude spuštěna ve stejném <xref:System.AppDomain> formátu [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] a bude spuštěna rychleji. Pokud parametr vrátí **hodnotu true**, úloha se spustí za sekundu <xref:System.AppDomain> , která je izolovaná od [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)] a bude pomalejší.|  
|`AssembliesGeneratedDuringBuild`|Parametr volitelného **řetězce []** .<br /><br /> Určuje odkazy na sestavení, která se mění během procesu sestavení. Například [!INCLUDE[TLA#tla_visualstu2005](../includes/tlasharptla-visualstu2005-md.md)] řešení může obsahovat jeden projekt, který odkazuje na kompilovaný výstup jiného projektu. V tomto případě lze zkompilované výstupy druhého projektu přidat do **AssembliesGeneratedDuringBuild**.<br /><br /> Poznámka: **AssembliesGeneratedDuringBuild** musí obsahovat odkazy na úplnou sadu sestavení, která jsou generována řešením sestavení.|  
|`AssemblyName`|Povinný parametr **řetězce**<br /><br /> Určuje krátký název sestavení, který je generován pro projekt. Například pokud projekt generuje [!INCLUDE[TLA#tla_win](../includes/tlasharptla-win-md.md)] spustitelný soubor, jehož název je **WinExeAssembly.exe**, parametr **AssemblyName** má hodnotu **WinExeAssembly**.|  
|`GeneratedBaml`|Volitelný výstupní parametr **ITaskItem []** .<br /><br /> Obsahuje seznam generovaných souborů v [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] binárním formátu.|  
|`KnownReferencePaths`|Parametr volitelného **řetězce []** .<br /><br /> Určuje odkazy na sestavení, která se během procesu sestavení nikdy nezměnila. Zahrnuje sestavení, která jsou umístěna v [!INCLUDE[TLA#tla_gac](../includes/tlasharptla-gac-md.md)] , v [!INCLUDE[TLA#tla_netframewk](../includes/tlasharptla-netframewk-md.md)] instalačním adresáři a tak dále.|  
|`Language`|Povinný parametr **řetězce**<br /><br /> Určuje spravovaný jazyk, který podporuje kompilátor. Platné možnosti jsou **C#**, **VB**, **JScript**a **C++**.|  
|`LocalizationDirectivesToLocFile`|Volitelný **řetězcový** parametr.<br /><br /> Určuje, jak generovat informace o lokalizaci pro každý zdrojový [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubor. Platné možnosti jsou **none**, **CommentsOnly**a **All**.|  
|`OutputPath`|Povinný parametr **řetězce**<br /><br /> Určuje adresář, ve kterém jsou vygenerované [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubory binárního formátu.|  
|`OutputType`|Povinný parametr **řetězce**<br /><br /> Určuje typ sestavení generovaných projektem. Platné možnosti jsou **winexe**, **exe**, **Library**a **netmodule**.|  
|`References`|Volitelný parametr **ITaskItem []** .<br /><br /> Určuje seznam odkazů ze souborů na sestavení, která obsahují typy používané v [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] souborech. Jeden odkaz je na sestavení, které bylo vygenerováno <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> úlohou, která musí být spuštěna před <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> úkolem.|  
|`RootNamespace`|Volitelný **řetězcový** parametr.<br /><br /> Určuje kořenový obor názvů pro třídy, které jsou uvnitř projektu. **RootNamespace** se používá také jako výchozí obor názvů generovaného souboru spravovaného kódu, pokud odpovídající [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubor neobsahuje `x:Class` atribut.|  
|`XAMLDebuggingInformation`|Volitelný **logický** parametr.<br /><br /> Je-li **nastavena hodnota true**, jsou generovány diagnostické informace a zahrnuty do kompilace, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] aby bylo možné získat podporu ladění.|  
  
## <a name="remarks"></a>Poznámky  
 Než spustíte **MarkupCompilePass2 –**, musíte vygenerovat dočasné sestavení, které obsahuje typy, které jsou používány [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubory, jejichž průchod kompilací kódu byl odložen. Dočasné sestavení vygenerujete spuštěním úlohy **GenerateTemporaryTargetAssembly –** .  
  
 Odkaz na generované dočasné sestavení je k dispozici <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> při spuštění, což umožňuje, aby [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubory, jejichž kompilace byla odložena v prvním průchodu kódu, byly nyní zkompilovány do binárního formátu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> úlohu k provedení druhé kompilace Pass.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass2Task">  
    <MarkupCompilePass2   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
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
