---
title: Úloha Markupcompilepass2 – | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f239670200a75dc3494b22b9a6aa761b1736119d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592214"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 – úloha

Úloha <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> provádí kompilaci kódu za sekundu do [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] souborů, které odkazují na typy ve stejném projektu.

## <a name="task-parameters"></a>Parametry úlohy

| Parametr | Popis |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Volitelný **logický** parametr.<br /><br /> Určuje, zda má být úloha spuštěna v samostatném <xref:System.AppDomain>. Pokud tento parametr vrátí **hodnotu false**, úloha bude spuštěna ve stejném <xref:System.AppDomain> jako [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)]a bude spuštěna rychleji. Pokud parametr vrátí **hodnotu true**, úloha se spustí ve druhém <xref:System.AppDomain>, který je izolovaný od [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] a běží pomaleji. |
| `AssembliesGeneratedDuringBuild` | Parametr volitelného **řetězce []** .<br /><br /> Určuje odkazy na sestavení, která se mění během procesu sestavení. Například řešení sady Visual Studio může obsahovat jeden projekt, který odkazuje na kompilovaný výstup jiného projektu. V tomto případě lze zkompilované výstupy druhého projektu přidat do **AssembliesGeneratedDuringBuild**.<br /><br /> Poznámka: **AssembliesGeneratedDuringBuild** musí obsahovat odkazy na úplnou sadu sestavení, která jsou generována řešením sestavení. |
| `AssemblyName` | Povinný parametr **řetězce**<br /><br /> Určuje krátký název sestavení, který je generován pro projekt. Například pokud projekt generuje [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)] spustitelný soubor, jehož název je *WinExeAssembly. exe*, parametr **AssemblyName** má hodnotu **WinExeAssembly**. |
| `GeneratedBaml` | Volitelný výstupní parametr **ITaskItem []** .<br /><br /> Obsahuje seznam generovaných souborů v [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] binárním formátu. |
| `KnownReferencePaths` | Parametr volitelného **řetězce []** .<br /><br /> Určuje odkazy na sestavení, která se během procesu sestavení nikdy nezměnila. Zahrnuje sestavení nacházející se v [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], v instalačním adresáři [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] a tak dále. |
| `Language` | Povinný parametr **řetězce**<br /><br /> Určuje spravovaný jazyk, který podporuje kompilátor. Platné možnosti jsou **C#** , **VB**, **JScript**a **C++** . |
| `LocalizationDirectivesToLocFile` | Volitelný **řetězcový** parametr.<br /><br /> Určuje, jak generovat informace o lokalizaci pro každý zdrojový [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubor. Platné možnosti jsou **none**, **CommentsOnly**a **All**. |
| `OutputPath` | Povinný parametr **řetězce**<br /><br /> Určuje adresář, ve kterém se generují generované soubory binárního formátu [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. |
| `OutputType` | Povinný parametr **řetězce**<br /><br /> Určuje typ sestavení generovaných projektem. Platné možnosti jsou **winexe**, **exe**, **Library**a **netmodule**. |
| `References` | Volitelný parametr **ITaskItem []** .<br /><br /> Určuje seznam odkazů ze souborů na sestavení, která obsahují typy používané v souborech [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. Jeden odkaz je na sestavení, které bylo vygenerováno úlohou <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>, které je třeba spustit před úlohou <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>. |
| `RootNamespace` | Volitelný **řetězcový** parametr.<br /><br /> Určuje kořenový obor názvů pro třídy, které jsou uvnitř projektu. **RootNamespace** se používá také jako výchozí obor názvů generovaného souboru spravovaného kódu, pokud odpovídající [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubor neobsahuje atribut `x:Class`. |
| `XAMLDebuggingInformation` | Volitelný **logický** parametr.<br /><br /> Je-li **nastavena hodnota true**, jsou generovány diagnostické informace a zahrnuty do zkompilovaných [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] za účelem podpory ladění. |

## <a name="remarks"></a>Poznámky

Než spustíte **MarkupCompilePass2 –** , musíte vygenerovat dočasné sestavení, které obsahuje typy, které jsou používány soubory [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)], jejichž průchod kompilací kódu byl odložen. Dočasné sestavení vygenerujete spuštěním úlohy **GenerateTemporaryTargetAssembly –** .

Odkaz na generované dočasné sestavení je <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> při spuštění, což umožňuje, aby soubory [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)], jejichž kompilace byla odložena v prvním průchodu kódu, byly nyní zkompilovány do binárního formátu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít úlohu <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> k provedení druhé kompilace Pass.

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

- [Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [WPF MSBuild – referenční dokumentace úlohy](../msbuild/wpf-msbuild-task-reference.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Referenční dokumentace úlohy nástroje MSBuild](../msbuild/msbuild-task-reference.md)
- [Sestavení aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Přehled aplikací prohlížeče WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
