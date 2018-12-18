---
title: Markupcompilepass1 – úloha | Dokumentace Microsoftu
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
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9db623dd06db06a1dfee3e22345564f888431d1c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855325"
---
# <a name="markupcompilepass1-task"></a>Markupcompilepass1 – úloha

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> Úloh převede bez možnosti lokalizace [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] soubory do kompilovaného binárního formátu projektu.

## <a name="task-parameters"></a>Parametry úlohy

| Parametr | Popis |
| - | - |
| `AllGeneratedFiles` | Volitelné **[] ITaskItem** výstupní parametr.<br /><br /> Obsahuje úplný seznam souborů, které jsou generovány <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> úloh. |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Volitelné **logická** parametru.<br /><br /> Určuje, jestli se má spustit úlohu v samostatném <xref:System.AppDomain>. Pokud tento parametr vrátí **false**, úloha běží ve stejném <xref:System.AppDomain> jako [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] a ten poběží rychleji. Pokud se vrátí parametr **true**, bude spuštěna úloha za sekundu <xref:System.AppDomain> , která je oddělená od [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] a pomalejší. |
| `ApplicationMarkup` | Volitelné **[] ITaskItem** parametru.<br /><br /> Určuje název definice aplikace [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] souboru. |
| `AssembliesGeneratedDuringBuild` | Volitelné **String []** parametru.<br /><br /> Určuje odkazy na sestavení, které se mění během procesu sestavení. Řešení sady Visual Studio může například obsahovat jeden projekt, který odkazuje kompilovaném výstupu z jiného projektu. V takovém případě kompilovaný výstup druhý projekt lze přidat do **AssembliesGeneratedDuringBuild** parametru.<br /><br /> Poznámka: **AssembliesGeneratedDuringBuild** parametr musí obsahovat odkazy na kompletní sadu sestavení, které jsou generovány pomocí sestavení řešení. |
| `AssemblyName` | Vyžaduje **řetězec** parametru.<br /><br /> Určuje krátký název sestavení, který je generován pro projekt. Například, pokud je generování projektu [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] spustitelný soubor, jehož název je *WinExeAssembly.exe*, **AssemblyName** parametr má hodnotu **WinExeAssembly**. |
| `AssemblyPublicKeyToken` | Volitelné **řetězec** parametru.<br /><br /> Určuje token veřejného klíče pro sestavení. |
| `AssemblyVersion` | Volitelné **řetězec** parametru.<br /><br /> Určuje číslo verze sestavení. |
| `ContentFiles` | Volitelné **[] ITaskItem** parametru.<br /><br /> Určuje seznam dojde ke ztrátě souborů obsahu. |
| `DefineConstants` | Volitelné **řetězec** parametru.<br /><br /> Určuje, že aktuální hodnotu **DefineConstants**, se ukládají. která ovlivňuje cílový generování sestavení; Pokud tento parametr se změní, může být změněn veřejné rozhraní API v cílové sestavení a kompilace [!INCLUDE[TLA2#tla_titlexaml](../msbuild/includes/tla2sharptla_titlexaml_md.md)] soubory, které odkazují na místní typy mohou být ovlivněny. |
| `ExtraBuildControlFiles` | Volitelné **[] ITaskItem** parametru.<br /><br /> Určuje seznam souborů, které řídí, zda opětovné sestavení se aktivuje, když <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> úlohy znovu spustí, opětovné sestavení se aktivuje, pokud jeden z těchto souborů změny. |
| `GeneratedBamlFiles` | Volitelné **[] ITaskItem** výstupní parametr.<br /><br /> Obsahuje seznam generovaných souborů v [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] binárním formátu. |
| `GeneratedCodeFiles` | Volitelné **[] ITaskItem** výstupní parametr.<br /><br /> Obsahuje seznam souborů generovaných spravovaného kódu. |
| `GeneratedLocalizationFiles` | Volitelné **[] ITaskItem** výstupní parametr.<br /><br /> Obsahuje seznam lokalizace souborů, které byly vytvořeny pro každý lokalizovatelné [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] souboru. |
| `HostInBrowser` | Volitelné **řetězec** parametru.<br /><br /> Určuje, zda je sestavení vygenerované [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)]. Platné možnosti jsou **true** a **false**. Pokud **true**, kód se generuje pro podporu hostování prohlížeče. |
| `KnownReferencePaths` | Volitelné **String []** parametru.<br /><br /> Určuje odkazy na sestavení, která během procesu sestavování nezměníte. Zahrnuje sestavení, které jsou umístěné v [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)]v [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] instalační adresář a tak dále. |
| `Language` | Vyžaduje **řetězec** parametru.<br /><br /> Určuje spravovaného jazyka, který kompilátor podporuje. Platné možnosti jsou **jazyka C#**, **VB**, **JScript**, a **C++**. |
| `LanguageSourceExtension` | Volitelné **řetězec** parametru.<br /><br /> Určuje příponu, která se připojuje k rozšíření spravovaného kódu generovaného souboru:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Pokud **LanguageSourceExtension** parametr není nastaven s konkrétní hodnotou, je použit výchozí přípona názvu souboru zdroje pro jazyk: *.vb* pro [!INCLUDE[TLA#tla_visualb](../msbuild/includes/tlasharptla_visualb_md.md)], *.csharp* pro [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)]. |
| `LocalizationDirectivesToLocFile` | Volitelné **řetězec** parametru.<br /><br /> Určuje, jak generovat informace o lokalizaci pro každý zdroj [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] souboru. Platné možnosti jsou **žádný**, **CommentsOnly**, a **všechny**. |
| `OutputPath` | Vyžaduje **řetězec** parametru.<br /><br /> Určuje adresář, ve kterém generované spravovaných souborů s kódem a [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] formát binární soubory jsou vygenerovány. |
| `OutputType` | Vyžaduje **řetězec** parametru.<br /><br /> Určuje typ sestavení, který je generován projekt. Platné možnosti jsou **winexe**, **exe**, **knihovny**, a **netmodule**. |
| `PageMarkup` | Volitelné **[] ITaskItem** parametru.<br /><br /> Určuje seznam [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] souborů ke zpracování. |
| `References` | Volitelné **[] ITaskItem** parametru.<br /><br /> Určuje seznam odkazů na sestavení, která obsahují typy, které se používají v soubory [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory. |
| `RequirePass2ForMainAssembly` | Volitelné **logická** výstupní parametr.<br /><br /> Určuje, zda projekt obsahuje bez možnosti lokalizace [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory, které odkazují na místní typy, které jsou vloženy do hlavního sestavení. |
| `RequirePass2ForSatelliteAssembly` | Volitelné **logická** výstupní parametr.<br /><br /> Určuje, zda projekt obsahuje lokalizovatelné [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory, které odkazují na místní typy, které jsou vloženy do hlavního sestavení. |
| `RootNamespace` | Volitelné **řetězec** parametru.<br /><br /> Určuje kořenový obor názvů pro třídy, které jsou uvnitř projektu. **RootNamespace** se také používá jako výchozí obor názvů generovaného spravovaného kódu souboru, když odpovídající [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubor neobsahuje `x:Class` atribut. |
| `SourceCodeFiles` | Volitelné **[] ITaskItem** parametru.<br /><br /> Určuje seznam souborů kódu pro aktuální projekt. Seznam neobsahuje soubory generované spravovaný kód specifický pro jazyk. |
| `UICulture` | Volitelné **řetězec** parametru.<br /><br /> Určuje satelitní sestavení pro jazykovou verzi uživatelského rozhraní, ve kterém generované [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] binární soubory jsou vloženy. Pokud **UICulture** není nastavena, generované [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] binární soubory jsou vloženy do hlavního sestavení. |
| `XAMLDebuggingInformation` | Volitelné **logická** parametru.<br /><br /> Když **true**, vygeneruje a součástí zkompilovaný diagnostické informace [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] k usnadnění ladění. |

## <a name="remarks"></a>Poznámky

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> Úkol obvykle zkompiluje [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] do binárního formátu a generuje soubory s kódem. Pokud [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubor obsahuje odkazy na typy, které jsou definovány ve stejném projektu, je jeho kompilace do binárního formátu odložit **MarkupCompilePass1** do druhého průchodu kompilace kódu ( **Markupcompilepass2 –**). Tyto soubory musí mít jeho kompilace odložené vzhledem k tomu, že musíte počkat, dokud jsou zkompilovány odkazované místně definované typy. Ale pokud [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubor má `x:Class` atribut, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> generuje soubor kódu pro konkrétní jazyk pro něj.

A [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubor je lokalizovatelný obsahuje elementy, které používají-li `x:Uid` atribut:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

A [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubor odkazuje na typ místně definované při deklaruje [!INCLUDE[TLA#tla_xml](../msbuild/includes/tlasharptla_xml_md.md)] obor názvů, který se používá `clr-namespace` hodnota, která má odkazovat na názvový prostor v aktuálním projektu:

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

Pokud existuje [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] souboru je lokalizovatelný nebo odkazuje na typ místně definované, překontrolovat kompilace kódu se vyžaduje, což vyžaduje spuštění [generatetemporarytargetassembly –](../msbuild/generatetemporarytargetassembly-task.md) a pak [ Markupcompilepass2 –](../msbuild/markupcompilepass2-task.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak převést tři *stránky* [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] souborů do binárních souborů. *Page1* obsahuje odkaz na typ, `Class1`, který je v kořenovém oboru názvů projektu a proto není převedena na binárních souborů v tomto průchodu kompilace kódu. Místo toho [generatetemporarytargetassembly –](../msbuild/generatetemporarytargetassembly-task.md) spouští a je následována [markupcompilepass2 –](../msbuild/markupcompilepass2-task.md).

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

## <a name="see-also"></a>Viz také:

[Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)  
[WPF MSBuild – referenční dokumentace úlohy](../msbuild/wpf-msbuild-task-reference.md)  
[Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)  
[Referenční dokumentace úlohy nástroje MSBuild](../msbuild/msbuild-task-reference.md)  
[Sestavení aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)  
[Přehled aplikací prohlížeče WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)