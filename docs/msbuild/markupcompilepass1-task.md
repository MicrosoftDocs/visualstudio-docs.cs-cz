---
title: Úloha MarkupCompilePass1 | Microsoft Docs
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
ms.openlocfilehash: d72b0a63235de4cc93e97f6e85dc5728e5ebbf43
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579664"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1 – úloha

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> úkol převede nelokalizovatelné soubory projektu [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] na kompilovaný binární formát.

## <a name="task-parameters"></a>Parametry úlohy

| Parametr | Popis |
| - | - |
| `AllGeneratedFiles` | Volitelný výstupní parametr **ITaskItem []** .<br /><br /> Obsahuje úplný seznam souborů, které jsou generovány úlohou <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>. |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Volitelný **logický** parametr.<br /><br /> Určuje, zda má být úloha spuštěna v samostatném <xref:System.AppDomain>. Pokud tento parametr vrátí **hodnotu false**, úloha se spustí ve stejném <xref:System.AppDomain> jako [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] a rychlejší. Pokud parametr vrátí **hodnotu true**, úloha se spustí ve druhém <xref:System.AppDomain>, který je izolovaný od [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] a běží pomaleji. |
| `ApplicationMarkup` | Volitelný parametr **ITaskItem []** .<br /><br /> Určuje název souboru [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] definice aplikace. |
| `AssembliesGeneratedDuringBuild` | Parametr volitelného **řetězce []** .<br /><br /> Určuje odkazy na sestavení, která se mění během procesu sestavení. Například řešení sady Visual Studio může obsahovat jeden projekt, který odkazuje na kompilovaný výstup jiného projektu. V tomto případě lze zkompilované výstupy druhého projektu přidat do parametru **AssembliesGeneratedDuringBuild** .<br /><br /> Poznámka: parametr **AssembliesGeneratedDuringBuild** musí obsahovat odkazy na úplnou sadu sestavení, která jsou generována řešením sestavení. |
| `AssemblyName` | Povinný parametr **řetězce**<br /><br /> Určuje krátký název sestavení, který je generován pro projekt. Například pokud projekt generuje [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] spustitelný soubor, jehož název je *WinExeAssembly. exe*, parametr **AssemblyName** má hodnotu **WinExeAssembly**. |
| `AssemblyPublicKeyToken` | Volitelný **řetězcový** parametr.<br /><br /> Určuje token veřejného klíče pro sestavení. |
| `AssemblyVersion` | Volitelný **řetězcový** parametr.<br /><br /> Určuje číslo verze sestavení. |
| `ContentFiles` | Volitelný parametr **ITaskItem []** .<br /><br /> Určuje seznam volných souborů obsahu. |
| `DefineConstants` | Volitelný **řetězcový** parametr.<br /><br /> Určuje, že aktuální hodnota **DefineConstants**je zachovaná. který ovlivňuje vytváření cílového sestavení; Pokud je tento parametr změněn, může být ovlivněno veřejné rozhraní API v cílovém sestavení a kompilace [!INCLUDE[TLA2#tla_titlexaml](../msbuild/includes/tla2sharptla_titlexaml_md.md)] souborů, které odkazují na místní typy. |
| `ExtraBuildControlFiles` | Volitelný parametr **ITaskItem []** .<br /><br /> Určuje seznam souborů, které určují, jestli se při opakovaném spuštění úlohy <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> spustí znovu sestavení; opětovné sestavení se aktivuje, pokud se některý z těchto souborů změní. |
| `GeneratedBamlFiles` | Volitelný výstupní parametr **ITaskItem []** .<br /><br /> Obsahuje seznam generovaných souborů v [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] binárním formátu. |
| `GeneratedCodeFiles` | Volitelný výstupní parametr **ITaskItem []** .<br /><br /> Obsahuje seznam generovaných souborů spravovaného kódu. |
| `GeneratedLocalizationFiles` | Volitelný výstupní parametr **ITaskItem []** .<br /><br /> Obsahuje seznam souborů lokalizace, které byly vygenerovány pro každý Lokalizovatelný [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubor. |
| `HostInBrowser` | Volitelný **řetězcový** parametr.<br /><br /> Určuje, zda je generované sestavení [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)]. Platné možnosti jsou **true** a **false**. Pokud má **hodnotu true**, vygeneruje se kód pro podporu hostování prohlížeče. |
| `KnownReferencePaths` | Parametr volitelného **řetězce []** .<br /><br /> Určuje odkazy na sestavení, která se během procesu sestavení nemění. Zahrnuje sestavení nacházející se v [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], v instalačním adresáři [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] a tak dále. |
| `Language` | Povinný parametr **řetězce**<br /><br /> Určuje spravovaný jazyk, který podporuje kompilátor. Platné možnosti jsou **C#** , **VB**, **JScript**a **C++** . |
| `LanguageSourceExtension` | Volitelný **řetězcový** parametr.<br /><br /> Určuje rozšíření, které je připojeno k rozšíření generovaného souboru spravovaného kódu:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Pokud parametr **LanguageSourceExtension** není nastaven s konkrétní hodnotou, použije se výchozí přípona názvu zdrojového souboru pro jazyk: *. vb* pro [!INCLUDE[TLA#tla_visualb](../msbuild/includes/tlasharptla_visualb_md.md)], *. CSharp* pro [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)]. |
| `LocalizationDirectivesToLocFile` | Volitelný **řetězcový** parametr.<br /><br /> Určuje, jak generovat informace o lokalizaci pro každý zdrojový [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubor. Platné možnosti jsou **none**, **CommentsOnly**a **All**. |
| `OutputPath` | Povinný parametr **řetězce**<br /><br /> Určuje adresář, ve kterém jsou vygenerovány soubory spravovaného kódu a [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] binárního formátu. |
| `OutputType` | Povinný parametr **řetězce**<br /><br /> Určuje typ sestavení generovaných projektem. Platné možnosti jsou **winexe**, **exe**, **Library**a **netmodule**. |
| `PageMarkup` | Volitelný parametr **ITaskItem []** .<br /><br /> Určuje seznam [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] souborů, které se mají zpracovat. |
| `References` | Volitelný parametr **ITaskItem []** .<br /><br /> Určuje seznam odkazů ze souborů na sestavení, která obsahují typy používané v souborech [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. |
| `RequirePass2ForMainAssembly` | Volitelný parametr **Boolean** Output.<br /><br /> Určuje, zda projekt obsahuje soubory, které nejsou lokalizovatelné [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)], které odkazují na místní typy, které jsou vloženy do hlavního sestavení. |
| `RequirePass2ForSatelliteAssembly` | Volitelný parametr **Boolean** Output.<br /><br /> Určuje, zda projekt obsahuje lokalizovatelné [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory, které odkazují na místní typy, které jsou vloženy do hlavního sestavení. |
| `RootNamespace` | Volitelný **řetězcový** parametr.<br /><br /> Určuje kořenový obor názvů pro třídy, které jsou uvnitř projektu. **RootNamespace** se používá také jako výchozí obor názvů generovaného souboru spravovaného kódu, pokud odpovídající [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubor neobsahuje atribut `x:Class`. |
| `SourceCodeFiles` | Volitelný parametr **ITaskItem []** .<br /><br /> Určuje seznam kódových souborů pro aktuální projekt. Seznam neobsahuje vygenerované soubory spravovaného kódu, které jsou specifické pro daný jazyk. |
| `UICulture` | Volitelný **řetězcový** parametr.<br /><br /> Určuje satelitní sestavení pro jazykovou verzi uživatelského rozhraní, ve kterém jsou vloženy soubory binárního formátu [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. Není-li nastavena sada **UICulture** , jsou vygenerované soubory binárního formátu [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] do hlavního sestavení vloženy. |
| `XAMLDebuggingInformation` | Volitelný **logický** parametr.<br /><br /> Je-li **nastavena hodnota true**, jsou generovány diagnostické informace a zahrnuty do zkompilovaných [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] za účelem podpory ladění. |

## <a name="remarks"></a>Poznámky

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> úloha obvykle kompiluje [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] do binárního formátu a generuje soubory kódu. Pokud soubor [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] obsahuje odkazy na typy, které jsou definovány ve stejném projektu, jeho kompilace do binárního formátu je odložena **MarkupCompilePass1** do druhé Pass kompilace kódu (**MarkupCompilePass2 –** ). Pro tyto soubory musí být kompilace odložena, protože musí počkat, dokud nebudou zkompilovány místně definované typy. Pokud ale [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubor obsahuje atribut `x:Class`, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> pro něj vygeneruje soubor kódu specifický pro daný jazyk.

Soubor [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] lze lokalizovat, pokud obsahuje prvky, které používají atribut `x:Uid`:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

[!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubor odkazuje na místně definovaný typ při deklaraci oboru názvů [!INCLUDE[TLA#tla_xml](../msbuild/includes/tlasharptla_xml_md.md)], který používá hodnotu `clr-namespace` pro odkazování na obor názvů v aktuálním projektu:

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

Pokud je soubor [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] lokalizovatelné nebo odkazuje na místně definovaný typ, je vyžadován druhý průchod kompilace kódu, který vyžaduje spuštění [GenerateTemporaryTargetAssembly –](../msbuild/generatetemporarytargetassembly-task.md) a pak [MarkupCompilePass2 –](../msbuild/markupcompilepass2-task.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak převést tři *stránky* [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory do binárních formátů souborů. *Page1* obsahuje odkaz na typ, `Class1`, který je v kořenovém oboru názvů projektu, a proto není převeden do binárních formátů souborů v tomto průchodu kompilace kódu. Místo toho se spustí [GenerateTemporaryTargetAssembly –](../msbuild/generatetemporarytargetassembly-task.md) a za ním následuje [MarkupCompilePass2 –](../msbuild/markupcompilepass2-task.md).

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