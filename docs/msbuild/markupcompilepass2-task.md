---
title: MarkupCompilePass2 Úkol | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: d18bc3638454e2a6b034cd2e35c3a158361a033e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633522"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 – úloha

Úloha <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> provádí kompilaci značek druhého průchodu na souborech XAML, které odkazují na typy ve stejném projektu.

## <a name="task-parameters"></a>Parametry úlohy

| Parametr | Popis |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Volitelný **logický** parametr.<br /><br /> Určuje, zda má být úloha spuštěna v samostatném souboru <xref:System.AppDomain>. Pokud tento parametr vrátí **false**, <xref:System.AppDomain> úloha běží ve stejném jako MSBuild a běží rychleji. Pokud parametr vrátí **hodnotu true**, <xref:System.AppDomain> úloha se spustí v sekundě, která je izolována od MSBuild a běží pomaleji. |
| `AssembliesGeneratedDuringBuild` | Volitelný **parametr String[].**<br /><br /> Určuje odkazy na sestavení, která se během procesu sestavení mění. Například řešení sady Visual Studio může obsahovat jeden projekt, který odkazuje na zkompilovaný výstup jiného projektu. V tomto případě zkompilovaný výstup druhého projektu lze přidat do **AssembliesGeneratedDuringBuild**.<br /><br /> Poznámka: **SestaveníGeneratedDuringBuild** musí obsahovat odkazy na úplnou sadu sestavení, které jsou generovány řešením sestavení. |
| `AssemblyName` | Povinný **parametr String.**<br /><br /> Určuje krátký název sestavení, které je generováno pro projekt. Například pokud projekt generuje spustitelný soubor, jehož název je *WinExeAssembly.exe*, **parametr AssemblyName** má hodnotu **WinExeAssembly**. |
| `GeneratedBaml` | Volitelný výstupní parametr **ITaskItem[].**<br /><br /> Obsahuje seznam generovaných souborů v binárním formátu XAML. |
| `KnownReferencePaths` | Volitelný **parametr String[].**<br /><br /> Určuje odkazy na sestavení, která se během procesu sestavení nikdy nezmění. Zahrnuje sestavení, která jsou umístěna v globální mezipaměti sestavení (GAC), v instalačním adresáři rozhraní .NET a tak dále. |
| `Language` | Povinný **parametr String.**<br /><br /> Určuje spravovaný jazyk, který kompilátor podporuje. Platné možnosti jsou **C#**, **VB**, **JScript**a **C++**. |
| `LocalizationDirectivesToLocFile` | Volitelný **parametr String.**<br /><br /> Určuje způsob generování informací o lokalizaci pro každý zdrojový soubor XAML. Platné možnosti jsou **Žádné**, **CommentsOnly**a **All**. |
| `OutputPath` | Povinný **parametr String.**<br /><br /> Určuje adresář, ve kterém jsou generovány generované binární formátové soubory XAML. |
| `OutputType` | Povinný **parametr String.**<br /><br /> Určuje typ sestavení, které je generováno projektem. Platné možnosti jsou **winexe**, **exe**, **knihovna**a **netmodule**. |
| `References` | Volitelný parametr **ITaskItem[].**<br /><br /> Určuje seznam odkazů ze souborů na sestavení, které obsahují typy, které se používají v souborech XAML. Jeden odkaz je sestavení, které bylo <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> generováno úlohou, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> která musí být spuštěna před úlohou. |
| `RootNamespace` | Volitelný **parametr String.**<br /><br /> Určuje kořenový obor názvů pro třídy, které jsou uvnitř projektu. **RootNamespace** se také používá jako výchozí obor názvů generovaného souboru spravovaného kódu, `x:Class` pokud odpovídající soubor XAML neobsahuje atribut. |
| `XAMLDebuggingInformation` | Volitelný **logický** parametr.<br /><br /> Pokud **je true**, diagnostické informace jsou generovány a zahrnuty do kompilované XAML za účelem podpory ladění. |

## <a name="remarks"></a>Poznámky

Před spuštěním **MarkupCompilePass2**, musíte vygenerovat dočasné sestavení, které obsahuje typy, které jsou používány soubory XAML, jejichž kompilace značky pass byly odloženy. Dočasné sestavení vygenerujete spuštěním úlohy **GenerateTemporaryTargetAssembly.**

Odkaz na generované dočasné sestavení je <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> k dispozici při spuštění, což umožňuje Soubory XAML, jejichž kompilace byla odložena v první průchod kompilace značky nyní být zkompilovány do binárního formátu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> použít úlohu k provedení kompilace druhého průchodu.

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

- [WPF MSBuild odkaz](../msbuild/wpf-msbuild-reference.md)
- [WPF MSBuild odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Odkaz na úkol MSBuild](../msbuild/msbuild-task-reference.md)
- [Vytvoření aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Přehled aplikací prohlížeče WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
