---
title: Markupcompilepass2 – úloha | Dokumentace Microsoftu
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
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 360a6c4d3e389583eece1adcc915f26091283653
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942384"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 – úloha

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> Úloha provede značek druhého průchodu kompilace na [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] soubory, které odkazují na typy ve stejném projektu.

## <a name="task-parameters"></a>Parametry úlohy

| Parametr | Popis |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Volitelné **logická** parametru.<br /><br /> Určuje, jestli se má spustit úlohu v samostatném <xref:System.AppDomain>. Pokud tento parametr vrátí **false**, úloha běží ve stejném <xref:System.AppDomain> jako [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)], a ten poběží rychleji. Pokud se vrátí parametr **true**, bude spuštěna úloha za sekundu <xref:System.AppDomain> , která je oddělená od [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] a pomalejší. |
| `AssembliesGeneratedDuringBuild` | Volitelné **String []** parametru.<br /><br /> Určuje odkazy na sestavení, které se mění během procesu sestavení. Řešení sady Visual Studio může například obsahovat jeden projekt, který odkazuje kompilovaném výstupu z jiného projektu. V takovém případě kompilovaný výstup druhý projekt lze přidat do **AssembliesGeneratedDuringBuild**.<br /><br /> Poznámka: **AssembliesGeneratedDuringBuild** musí obsahovat odkazy na kompletní sadu sestavení, které jsou generovány pomocí sestavení řešení. |
| `AssemblyName` | Vyžaduje **řetězec** parametru.<br /><br /> Určuje krátký název sestavení, který je generován pro projekt. Například, pokud je generování projektu [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)] spustitelný soubor, jehož název je *WinExeAssembly.exe*, **AssemblyName** parametr má hodnotu **WinExeAssembly**. |
| `GeneratedBaml` | Volitelné **[] ITaskItem** výstupní parametr.<br /><br /> Obsahuje seznam generovaných souborů v [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] binárním formátu. |
| `KnownReferencePaths` | Volitelné **String []** parametru.<br /><br /> Určuje odkazy na sestavení, které se nikdy změněn během procesu sestavení. Zahrnuje sestavení, které jsou umístěné v [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)]v [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] instalační adresář a tak dále. |
| `Language` | Vyžaduje **řetězec** parametru.<br /><br /> Určuje spravovaného jazyka, který kompilátor podporuje. Platné možnosti jsou **jazyka C#**, **VB**, **JScript**, a **C++**. |
| `LocalizationDirectivesToLocFile` | Volitelné **řetězec** parametru.<br /><br /> Určuje, jak generovat informace o lokalizaci pro každý zdroj [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] souboru. Platné možnosti jsou **žádný**, **CommentsOnly**, a **všechny**. |
| `OutputPath` | Vyžaduje **řetězec** parametru.<br /><br /> Určuje adresář, ve kterém generované [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] formát binární soubory jsou vygenerovány. |
| `OutputType` | Vyžaduje **řetězec** parametru.<br /><br /> Určuje typ sestavení, který je generován projekt. Platné možnosti jsou **winexe**, **exe**, **knihovny**, a **netmodule**. |
| `References` | Volitelné **[] ITaskItem** parametru.<br /><br /> Určuje seznam odkazů na sestavení, která obsahují typy, které se používají v soubory [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory. Je jeden odkaz na sestavení, který byl vytvořen <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> úkolu, který se musí spustit před <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> úloh. |
| `RootNamespace` | Volitelné **řetězec** parametru.<br /><br /> Určuje kořenový obor názvů pro třídy, které jsou uvnitř projektu. **RootNamespace** se také používá jako výchozí obor názvů generovaného spravovaného kódu souboru, když odpovídající [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubor neobsahuje `x:Class` atribut. |
| `XAMLDebuggingInformation` | Volitelné **logická** parametru.<br /><br /> Když **true**, vygeneruje a součástí zkompilovaný diagnostické informace [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] k usnadnění ladění. |

## <a name="remarks"></a>Poznámky

Před spuštěním **markupcompilepass2 –**, budete muset vygenerovat dočasné sestavení, který obsahuje typy, které jsou používány [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory byly odloženo, jehož značky kompilace pass. Generování dočasného sestavení spuštěním **generatetemporarytargetassembly –** úloh.

Odkaz na generovaný dočasného sestavení je k dispozici na <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> při spuštění, což [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory, jejichž sestavení byla odložena v první kompilace označení předat nyní být zkompilovány do binárního formátu.

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> úlohu, která provede sekundy předat kompilace.

```xml
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

## <a name="see-also"></a>Viz také:

[Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)  
[WPF MSBuild – referenční dokumentace úlohy](../msbuild/wpf-msbuild-task-reference.md)  
[Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)  
[Referenční dokumentace úlohy nástroje MSBuild](../msbuild/msbuild-task-reference.md)  
[Sestavení aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)  
[Přehled aplikací prohlížeče WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)