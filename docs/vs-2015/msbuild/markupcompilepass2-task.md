---
title: Markupcompilepass2 – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: ea61e827bfae47c3bea961cb15c208f585aa6ed9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49179226"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> Úloha provede značek druhého průchodu kompilace na [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] soubory, které odkazují na typy ve stejném projektu.  
  
## <a name="task-parameters"></a>Parametry úlohy  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Volitelné **logická** parametru.<br /><br /> Určuje, jestli se má spustit úlohu v samostatném <xref:System.AppDomain>. Pokud tento parametr vrátí **false**, úloha běží ve stejném <xref:System.AppDomain> jako [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)], a ten poběží rychleji. Pokud se vrátí parametr **true**, bude spuštěna úloha za sekundu <xref:System.AppDomain> , která je oddělená od [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)] a pomalejší.|  
|`AssembliesGeneratedDuringBuild`|Volitelné **String []** parametru.<br /><br /> Určuje odkazy na sestavení, které se mění během procesu sestavení. Například [!INCLUDE[TLA#tla_visualstu2005](../includes/tlasharptla-visualstu2005-md.md)] řešení může obsahovat jeden projekt, který odkazuje kompilovaném výstupu z jiného projektu. V takovém případě kompilovaný výstup druhý projekt lze přidat do **AssembliesGeneratedDuringBuild**.<br /><br /> Poznámka: **AssembliesGeneratedDuringBuild** musí obsahovat odkazy na kompletní sadu sestavení, které jsou generovány pomocí sestavení řešení.|  
|`AssemblyName`|Vyžaduje **řetězec** parametru.<br /><br /> Určuje krátký název sestavení, který je generován pro projekt. Například, pokud je generování projektu [!INCLUDE[TLA#tla_win](../includes/tlasharptla-win-md.md)] spustitelný soubor, jehož název je **WinExeAssembly.exe**, **AssemblyName** parametr má hodnotu **WinExeAssembly**.|  
|`GeneratedBaml`|Volitelné **[] ITaskItem** výstupní parametr.<br /><br /> Obsahuje seznam generovaných souborů v [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] binárním formátu.|  
|`KnownReferencePaths`|Volitelné **String []** parametru.<br /><br /> Určuje odkazy na sestavení, které se nikdy změněn během procesu sestavení. Zahrnuje sestavení, které jsou umístěné v [!INCLUDE[TLA#tla_gac](../includes/tlasharptla-gac-md.md)]v [!INCLUDE[TLA#tla_netframewk](../includes/tlasharptla-netframewk-md.md)] instalační adresář a tak dále.|  
|`Language`|Vyžaduje **řetězec** parametru.<br /><br /> Určuje spravovaného jazyka, který kompilátor podporuje. Platné možnosti jsou **jazyka C#**, **VB**, **JScript**, a **C++**.|  
|`LocalizationDirectivesToLocFile`|Volitelné **řetězec** parametru.<br /><br /> Určuje, jak generovat informace o lokalizaci pro každý zdroj [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] souboru. Platné možnosti jsou **žádný**, **CommentsOnly**, a **všechny**.|  
|`OutputPath`|Vyžaduje **řetězec** parametru.<br /><br /> Určuje adresář, ve kterém generované [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] formát binární soubory jsou vygenerovány.|  
|`OutputType`|Vyžaduje **řetězec** parametru.<br /><br /> Určuje typ sestavení, který je generován projekt. Platné možnosti jsou **winexe**, **exe**, **knihovny**, a **netmodule**.|  
|`References`|Volitelné **[] ITaskItem** parametru.<br /><br /> Určuje seznam odkazů na sestavení, která obsahují typy, které se používají v soubory [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubory. Je jeden odkaz na sestavení, který byl vytvořen <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> úkolu, který se musí spustit před <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> úloh.|  
|`RootNamespace`|Volitelné **řetězec** parametru.<br /><br /> Určuje kořenový obor názvů pro třídy, které jsou uvnitř projektu. **RootNamespace** se také používá jako výchozí obor názvů generovaného spravovaného kódu souboru, když odpovídající [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubor neobsahuje `x:Class` atribut.|  
|`XAMLDebuggingInformation`|Volitelné **logická** parametru.<br /><br /> Když **true**, vygeneruje a součástí zkompilovaný diagnostické informace [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] k usnadnění ladění.|  
  
## <a name="remarks"></a>Poznámky  
 Před spuštěním **markupcompilepass2 –**, budete muset vygenerovat dočasné sestavení, který obsahuje typy, které jsou používány [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubory byly odloženo, jehož značky kompilace pass. Generování dočasného sestavení spuštěním **generatetemporarytargetassembly –** úloh.  
  
 Odkaz na generovaný dočasného sestavení je k dispozici na <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> při spuštění, což [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubory, jejichž sestavení byla odložena v první kompilace označení předat nyní být zkompilovány do binárního formátu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> úlohu, která provede sekundy předat kompilace.  
  
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
 [Referenční dokumentace úlohy](../msbuild/wpf-msbuild-task-reference.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Sestavení aplikace WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Přehled aplikací Prohlížeče WPF XAML](http://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)



