---
title: Úloha Markupcompilepass2 – | Microsoft Docs
description: Naučte se, jak MSBuild používá úlohu Markupcompilepass2 – k provedení druhé Pass kompilace kódu na souborech XAML, které odkazují na typy ve stejném projektu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7425e0342974c3b000486f57227f768aac47b9ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966172"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 – úloha

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>Úloha provádí kompilaci kódu za sekundu v souborech XAML, které odkazují na typy ve stejném projektu.

## <a name="task-parameters"></a>Parametry úlohy

| Parametr | Popis |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Volitelný **logický** parametr.<br /><br /> Určuje, zda má být úloha spuštěna samostatně <xref:System.AppDomain> . Pokud tento parametr vrátí **hodnotu false**, úloha bude spuštěna ve stejném <xref:System.AppDomain> formátu jako MSBuild a bude spuštěna rychleji. Pokud parametr vrátí **hodnotu true**, úloha se spustí za sekundu <xref:System.AppDomain> , která je izolovaná od nástroje MSBuild a běží pomaleji. |
| `AssembliesGeneratedDuringBuild` | Parametr volitelného **řetězce []** .<br /><br /> Určuje odkazy na sestavení, která se mění během procesu sestavení. Například řešení sady Visual Studio může obsahovat jeden projekt, který odkazuje na kompilovaný výstup jiného projektu. V tomto případě lze zkompilované výstupy druhého projektu přidat do **AssembliesGeneratedDuringBuild**.<br /><br /> Poznámka: **AssembliesGeneratedDuringBuild** musí obsahovat odkazy na úplnou sadu sestavení, která jsou generována řešením sestavení. |
| `AssemblyName` | Povinný parametr **řetězce**<br /><br /> Určuje krátký název sestavení, který je generován pro projekt. Například pokud projekt generuje spustitelný soubor, jehož název je *WinExeAssembly.exe*, parametr **AssemblyName** má hodnotu **WinExeAssembly**. |
| `GeneratedBaml` | Volitelný výstupní parametr **ITaskItem []** .<br /><br /> Obsahuje seznam generovaných souborů v binárním formátu XAML. |
| `KnownReferencePaths` | Parametr volitelného **řetězce []** .<br /><br /> Určuje odkazy na sestavení, která se během procesu sestavení nikdy nezměnila. Zahrnuje sestavení, která jsou umístěna v globální mezipaměti sestavení (GAC), v instalačním adresáři rozhraní .NET atd. |
| `Language` | Povinný parametr **řetězce**<br /><br /> Určuje spravovaný jazyk, který podporuje kompilátor. Platné možnosti jsou **C#**, **VB**, **JScript** a **C++**. |
| `LocalizationDirectivesToLocFile` | Volitelný **řetězcový** parametr.<br /><br /> Určuje, jak generovat informace o lokalizaci pro každý zdrojový soubor XAML. Platné možnosti jsou **none**, **CommentsOnly** a **All**. |
| `OutputPath` | Povinný parametr **řetězce**<br /><br /> Určuje adresář, ve kterém jsou generovány vygenerované soubory binárního formátu XAML. |
| `OutputType` | Povinný parametr **řetězce**<br /><br /> Určuje typ sestavení generovaných projektem. Platné možnosti jsou **winexe**, **exe**, **Library** a **netmodule**. |
| `References` | Volitelný parametr **ITaskItem []** .<br /><br /> Určuje seznam odkazů ze souborů na sestavení, která obsahují typy používané v souborech XAML. Jeden odkaz je na sestavení, které bylo vygenerováno <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> úlohou, která musí být spuštěna před <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> úkolem. |
| `RootNamespace` | Volitelný **řetězcový** parametr.<br /><br /> Určuje kořenový obor názvů pro třídy, které jsou uvnitř projektu. **RootNamespace** se používá také jako výchozí obor názvů generovaného souboru spravovaného kódu, pokud odpovídající soubor XAML neobsahuje `x:Class` atribut. |
| `XAMLDebuggingInformation` | Volitelný **logický** parametr.<br /><br /> Je-li **nastavena hodnota true**, jsou generovány diagnostické informace a zahrnuty do zkompilovaného XAML za účelem podpory ladění. |

## <a name="remarks"></a>Poznámky

Před spuštěním **MarkupCompilePass2 –** musíte vygenerovat dočasné sestavení, které obsahuje typy, které jsou používány soubory XAML, jejichž předávání kódu bylo odloženo. Dočasné sestavení vygenerujete spuštěním úlohy **GenerateTemporaryTargetAssembly –** .

Odkaz na generované dočasné sestavení je k dispozici <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> při spuštění, což umožňuje, aby soubory XAML, jejichž kompilace byla odložena v prvním průchodu kódu, byly nyní kompilovány do binárního formátu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> úlohu k provedení druhé kompilace Pass.

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

## <a name="see-also"></a>Viz také

- [Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [WPF MSBuild – referenční dokumentace úlohy](../msbuild/wpf-msbuild-task-reference.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Referenční dokumentace úlohy nástroje MSBuild](../msbuild/msbuild-task-reference.md)
- [Sestavení aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Přehled aplikací prohlížeče WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
