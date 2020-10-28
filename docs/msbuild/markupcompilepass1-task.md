---
title: Úloha MarkupCompilePass1 | Microsoft Docs
description: Naučte se, jak MSBuild používá úlohu MarkupCompilePass1 k převodu souborů projektu XAML, které nejsou lokalizovat do zkompilovaného binárního formátu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 775884692963da226947a8fac524a8bd440d6c8d
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904264"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1 – úloha

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>Úloha převede soubory projektu XAML, které nejsou lokalizovatelné, do zkompilovaného binárního formátu.

## <a name="task-parameters"></a>Parametry úlohy

| Parametr | Popis |
| - | - |
| `AllGeneratedFiles` | Volitelný výstupní parametr **ITaskItem []** .<br /><br /> Obsahuje úplný seznam souborů, které jsou generovány <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> úlohou. |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Volitelný **logický** parametr.<br /><br /> Určuje, zda má být úloha spuštěna samostatně <xref:System.AppDomain> . Pokud tento parametr vrátí **hodnotu false** , úloha bude spuštěna ve stejném <xref:System.AppDomain> formátu jako MSBuild a bude spuštěna rychleji. Pokud parametr vrátí **hodnotu true** , úloha se spustí za sekundu <xref:System.AppDomain> , která je izolovaná od nástroje MSBuild a běží pomaleji. |
| `ApplicationMarkup` | Volitelný parametr **ITaskItem []** .<br /><br /> Určuje název souboru XAML definice aplikace. |
| `AssembliesGeneratedDuringBuild` | Parametr volitelného **řetězce []** .<br /><br /> Určuje odkazy na sestavení, která se mění během procesu sestavení. Například řešení sady Visual Studio může obsahovat jeden projekt, který odkazuje na kompilovaný výstup jiného projektu. V tomto případě lze zkompilované výstupy druhého projektu přidat do parametru **AssembliesGeneratedDuringBuild** .<br /><br /> Poznámka: parametr **AssembliesGeneratedDuringBuild** musí obsahovat odkazy na úplnou sadu sestavení, která jsou generována řešením sestavení. |
| `AssemblyName` | Povinný parametr **řetězce**<br /><br /> Určuje krátký název sestavení, který je generován pro projekt. Například pokud projekt generuje spustitelný soubor systému Windows, jehož název je *WinExeAssembly.exe* , parametr **AssemblyName** má hodnotu **WinExeAssembly** . |
| `AssemblyPublicKeyToken` | Volitelný **řetězcový** parametr.<br /><br /> Určuje token veřejného klíče pro sestavení. |
| `AssemblyVersion` | Volitelný **řetězcový** parametr.<br /><br /> Určuje číslo verze sestavení. |
| `ContentFiles` | Volitelný parametr **ITaskItem []** .<br /><br /> Určuje seznam volných souborů obsahu. |
| `DefineConstants` | Volitelný **řetězcový** parametr.<br /><br /> Určuje, že aktuální hodnota **DefineConstants** je zachovaná. který ovlivňuje vytváření cílového sestavení; Pokud je tento parametr změněn, může být změněno veřejné rozhraní API v cílovém sestavení a bude ovlivněna kompilace souborů XAML, které odkazují na místní typy. |
| `ExtraBuildControlFiles` | Volitelný parametr **ITaskItem []** .<br /><br /> Určuje seznam souborů, které určují, jestli se při opakovaném spuštění úlohy aktivuje nové sestavení <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> ; nové sestavení se aktivuje, pokud se některý z těchto souborů změní. |
| `GeneratedBamlFiles` | Volitelný výstupní parametr **ITaskItem []** .<br /><br /> Obsahuje seznam generovaných souborů v binárním formátu XAML. |
| `GeneratedCodeFiles` | Volitelný výstupní parametr **ITaskItem []** .<br /><br /> Obsahuje seznam generovaných souborů spravovaného kódu. |
| `GeneratedLocalizationFiles` | Volitelný výstupní parametr **ITaskItem []** .<br /><br /> Obsahuje seznam souborů lokalizace, které byly vygenerovány pro každý Lokalizovatelný soubor XAML. |
| `HostInBrowser` | Volitelný **řetězcový** parametr.<br /><br /> Určuje, zda je vygenerované sestavení aplikace prohlížeče XAML (XBAP). Platné možnosti jsou **true** a **false** . Pokud má **hodnotu true** , vygeneruje se kód pro podporu hostování prohlížeče. |
| `KnownReferencePaths` | Parametr volitelného **řetězce []** .<br /><br /> Určuje odkazy na sestavení, která se během procesu sestavení nemění. Zahrnuje sestavení, která jsou umístěna v globální mezipaměti sestavení (GAC), v instalačním adresáři rozhraní .NET atd. |
| `Language` | Povinný parametr **řetězce**<br /><br /> Určuje spravovaný jazyk, který podporuje kompilátor. Platné možnosti jsou **C#** , **VB** , **JScript** a **C++** . |
| `LanguageSourceExtension` | Volitelný **řetězcový** parametr.<br /><br /> Určuje rozšíření, které je připojeno k rozšíření generovaného souboru spravovaného kódu:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Pokud parametr **LanguageSourceExtension** není nastaven s konkrétní hodnotou, použije se výchozí přípona názvu zdrojového souboru pro jazyk: *. vb* pro Visual Basic, *. CSharp* pro C#. |
| `LocalizationDirectivesToLocFile` | Volitelný **řetězcový** parametr.<br /><br /> Určuje, jak generovat informace o lokalizaci pro každý zdrojový soubor XAML. Platné možnosti jsou **none** , **CommentsOnly** a **All** . |
| `OutputPath` | Povinný parametr **řetězce**<br /><br /> Určuje adresář, ve kterém jsou vygenerovány soubory spravovaného kódu a binární formáty XAML. |
| `OutputType` | Povinný parametr **řetězce**<br /><br /> Určuje typ sestavení generovaných projektem. Platné možnosti jsou **winexe** , **exe** , **Library** a **netmodule** . |
| `PageMarkup` | Volitelný parametr **ITaskItem []** .<br /><br /> Určuje seznam souborů XAML, které mají být zpracovány. |
| `References` | Volitelný parametr **ITaskItem []** .<br /><br /> Určuje seznam odkazů ze souborů na sestavení, která obsahují typy používané v souborech XAML. |
| `RequirePass2ForMainAssembly` | Volitelný parametr **Boolean** Output.<br /><br /> Určuje, zda projekt obsahuje nelokalizovatelné soubory XAML, které odkazují na místní typy, které jsou vloženy do hlavního sestavení. |
| `RequirePass2ForSatelliteAssembly` | Volitelný parametr **Boolean** Output.<br /><br /> Určuje, zda projekt obsahuje lokalizovatelné soubory XAML, které odkazují na místní typy, které jsou vloženy do hlavního sestavení. |
| `RootNamespace` | Volitelný **řetězcový** parametr.<br /><br /> Určuje kořenový obor názvů pro třídy, které jsou uvnitř projektu. **RootNamespace** se používá také jako výchozí obor názvů generovaného souboru spravovaného kódu, pokud odpovídající soubor XAML neobsahuje `x:Class` atribut. |
| `SourceCodeFiles` | Volitelný parametr **ITaskItem []** .<br /><br /> Určuje seznam kódových souborů pro aktuální projekt. Seznam neobsahuje vygenerované soubory spravovaného kódu, které jsou specifické pro daný jazyk. |
| `UICulture` | Volitelný **řetězcový** parametr.<br /><br /> Určuje satelitní sestavení pro jazykovou verzi uživatelského rozhraní, ve kterém jsou vloženy vygenerované soubory binárního formátu XAML. Pokud není nastavena sada **UICulture** , jsou vygenerované soubory binárního formátu XAML vloženy do hlavního sestavení. |
| `XAMLDebuggingInformation` | Volitelný **logický** parametr.<br /><br /> Je-li **nastavena hodnota true** , jsou generovány diagnostické informace a zahrnuty do zkompilovaného XAML za účelem podpory ladění. |

## <a name="remarks"></a>Poznámky

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>Úloha obvykle KOMPILUJE XAML do binárního formátu a generuje soubory kódu. Pokud soubor XAML obsahuje odkazy na typy, které jsou definovány ve stejném projektu, jeho kompilace do binárního formátu je odložena **MarkupCompilePass1** do druhé Pass kompilace kódu ( **MarkupCompilePass2 –** ). Pro tyto soubory musí být kompilace odložena, protože musí počkat, dokud nebudou zkompilovány místně definované typy. Pokud však soubor XAML obsahuje `x:Class` atribut, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> vygeneruje pro něj soubor kódu specifický pro daný jazyk.

Soubor XAML lze lokalizovat, pokud obsahuje prvky, které používají `x:Uid` atribut:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

Soubor XAML odkazuje na místně definovaný typ při deklaraci oboru názvů XML, který používá `clr-namespace` hodnotu pro odkazování na obor názvů v aktuálním projektu:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"
    >
    <Grid>
      <Grid.Resources>
        <localNameSpace:LocalType x:Key="localType" />
      </Grid.Resources>
      ...
    </Grid>
</Page>
```

Pokud je nějaký soubor XAML lokalizovatelné nebo odkazuje na místně definovaný typ, je vyžadován druhý průchod kompilace kódu, který vyžaduje spuštění [GenerateTemporaryTargetAssembly –](../msbuild/generatetemporarytargetassembly-task.md) a pak [MarkupCompilePass2 –](../msbuild/markupcompilepass2-task.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak převést tři soubory XAML *stránky* do binárních formátů souborů. *Page1* obsahuje odkaz na typ, `Class1` který je v kořenovém oboru názvů projektu, a proto není převeden do binárních formátů souborů v tomto průchodu kompilace kódu. Místo toho se spustí [GenerateTemporaryTargetAssembly –](../msbuild/generatetemporarytargetassembly-task.md) a za ním následuje [MarkupCompilePass2 –](../msbuild/markupcompilepass2-task.md).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass1Task">
    <MarkupCompilePass1
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      ApplicationMarkup="App.xaml"
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"
      SourceCodeFiles="Class1.cs"
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
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