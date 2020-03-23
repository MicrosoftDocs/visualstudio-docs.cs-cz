---
title: MarkupCompilePass1 Úkol | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: a847f096edf5e42623cb2cb32cf4fd871a89aad7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633509"
---
# <a name="markupcompilepass1-task"></a>Úloha MarkupCompilePass1

Úkol <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> převede nelokalizovatelné soubory projektu XAML na zkompilovaný binární formát.

## <a name="task-parameters"></a>Parametry úlohy

| Parametr | Popis |
| - | - |
| `AllGeneratedFiles` | Volitelný výstupní parametr **ITaskItem[].**<br /><br /> Obsahuje úplný seznam souborů, které jsou <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> generovány úkolem. |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Volitelný **logický** parametr.<br /><br /> Určuje, zda má být úloha spuštěna v samostatném souboru <xref:System.AppDomain>. Pokud tento parametr vrátí **hodnotu**false <xref:System.AppDomain> , úloha se spustí stejně jako MSBuild a běží rychleji. Pokud parametr vrátí **hodnotu true**, <xref:System.AppDomain> úloha se spustí v sekundě, která je izolována od MSBuild a běží pomaleji. |
| `ApplicationMarkup` | Volitelný parametr **ITaskItem[].**<br /><br /> Určuje název souboru XAML definice aplikace. |
| `AssembliesGeneratedDuringBuild` | Volitelný **parametr String[].**<br /><br /> Určuje odkazy na sestavení, která se během procesu sestavení mění. Například řešení sady Visual Studio může obsahovat jeden projekt, který odkazuje na zkompilovaný výstup jiného projektu. V tomto případě zkompilovaný výstup druhého projektu lze přidat do **assembliesGeneratedDuringBuild** parametr.<br /><br /> Poznámka: Parametr **AssembliesGeneratedDuringBuild** musí obsahovat odkazy na úplnou sadu sestavení, které jsou generovány řešením sestavení. |
| `AssemblyName` | Povinný parametr **řetězce.**<br /><br /> Určuje krátký název sestavení, které je generováno pro projekt. Například pokud projekt generuje spustitelný soubor systému Windows, jehož název je *WinExeAssembly.exe*, **parametr AssemblyName** má hodnotu **WinExeAssembly**. |
| `AssemblyPublicKeyToken` | Volitelný **parametr String.**<br /><br /> Určuje token veřejného klíče pro sestavení. |
| `AssemblyVersion` | Volitelný **parametr String.**<br /><br /> Určuje číslo verze sestavení. |
| `ContentFiles` | Volitelný parametr **ITaskItem[].**<br /><br /> Určuje seznam volných souborů obsahu. |
| `DefineConstants` | Volitelný **parametr String.**<br /><br /> Určuje, že aktuální hodnota **DefineConstants**, je zachována. která má vliv na generování cílových sestavení; Pokud se tento parametr změní, může být změněno veřejné rozhraní API v cílovém sestavení a může být ovlivněna kompilace souborů XAML, které odkazují na místní typy. |
| `ExtraBuildControlFiles` | Volitelný parametr **ITaskItem[].**<br /><br /> Určuje seznam souborů, které řídí, zda je <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> při opakování úlohy spuštěno opětovné sestavení. opětovné sestavení se aktivuje, pokud se jeden z těchto souborů změní. |
| `GeneratedBamlFiles` | Volitelný výstupní parametr **ITaskItem[].**<br /><br /> Obsahuje seznam generovaných souborů v binárním formátu XAML. |
| `GeneratedCodeFiles` | Volitelný výstupní parametr **ITaskItem[].**<br /><br /> Obsahuje seznam generovaných souborů spravovaného kódu. |
| `GeneratedLocalizationFiles` | Volitelný výstupní parametr **ITaskItem[].**<br /><br /> Obsahuje seznam lokalizačních souborů, které byly generovány pro každý lokalizovatelný soubor XAML. |
| `HostInBrowser` | Volitelný **parametr String.**<br /><br /> Určuje, zda je generované sestavení aplikací prohlížeče XAML (XBAP). Platné možnosti jsou **pravdivé** a **nepravdivé**. Pokud **true**, kód je generován pro podporu hosting prohlížeče. |
| `KnownReferencePaths` | Volitelný **parametr String[].**<br /><br /> Určuje odkazy na sestavení, která se během procesu sestavení nemění. Zahrnuje sestavení, která jsou umístěna v globální mezipaměti sestavení (GAC), v instalačním adresáři rozhraní .NET a tak dále. |
| `Language` | Povinný **parametr String.**<br /><br /> Určuje spravovaný jazyk, který kompilátor podporuje. Platné možnosti jsou **C#**, **VB**, **JScript**a **C++**. |
| `LanguageSourceExtension` | Volitelný **parametr String.**<br /><br /> Určuje příponu, která je připojena k příponě generovaného souboru spravovaného kódu:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Pokud parametr **LanguageSourceExtension** není nastaven s určitou hodnotou, použije se výchozí přípona názvu zdrojového souboru pro jazyk: *.vb* pro visual basic, *.csharp* pro C#. |
| `LocalizationDirectivesToLocFile` | Volitelný **parametr String.**<br /><br /> Určuje způsob generování informací o lokalizaci pro každý zdrojový soubor XAML. Platné možnosti jsou **Žádné**, **CommentsOnly**a **All**. |
| `OutputPath` | Povinný **parametr String.**<br /><br /> Určuje adresář, ve kterém jsou generovány generované soubory spravovaného kódu a binární formátové soubory XAML. |
| `OutputType` | Povinný **parametr String.**<br /><br /> Určuje typ sestavení, které je generováno projektem. Platné možnosti jsou **winexe**, **exe**, **knihovna**a **netmodule**. |
| `PageMarkup` | Volitelný parametr **ITaskItem[].**<br /><br /> Určuje seznam souborů XAML ke zpracování. |
| `References` | Volitelný parametr **ITaskItem[].**<br /><br /> Určuje seznam odkazů ze souborů na sestavení, které obsahují typy, které se používají v souborech XAML. |
| `RequirePass2ForMainAssembly` | Volitelný **logický** výstupní parametr.<br /><br /> Označuje, zda projekt obsahuje nelokalizovatelné soubory XAML, které odkazují na místní typy, které jsou vloženy do hlavního sestavení. |
| `RequirePass2ForSatelliteAssembly` | Volitelný **logický** výstupní parametr.<br /><br /> Označuje, zda projekt obsahuje lokalizovatelné soubory XAML, které odkazují na místní typy, které jsou vloženy do hlavního sestavení. |
| `RootNamespace` | Volitelný **parametr String.**<br /><br /> Určuje kořenový obor názvů pro třídy, které jsou uvnitř projektu. **RootNamespace** se také používá jako výchozí obor názvů generovaného souboru spravovaného kódu, `x:Class` pokud odpovídající soubor XAML neobsahuje atribut. |
| `SourceCodeFiles` | Volitelný parametr **ITaskItem[].**<br /><br /> Určuje seznam souborů kódu pro aktuální projekt. Seznam neobsahuje generované soubory spravovaného kódu specifické pro jazyk. |
| `UICulture` | Volitelný **parametr String.**<br /><br /> Určuje satelitní sestavení pro jazykovou verzi uživatelského zařízení, ve kterém jsou vloženy generované soubory binárního formátu XAML. Pokud **UICulture** není nastavena, generované soubory binárního formátu XAML jsou vloženy do hlavního sestavení. |
| `XAMLDebuggingInformation` | Volitelný **logický** parametr.<br /><br /> Pokud **je true**, diagnostické informace jsou generovány a zahrnuty do kompilované XAML za účelem podpory ladění. |

## <a name="remarks"></a>Poznámky

Úloha <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> obvykle kompiluje XAML do binárního formátu a generuje soubory kódu. Pokud soubor XAML obsahuje odkazy na typy, které jsou definovány ve stejném projektu, jeho kompilace do binárního formátu je odložena **MarkupCompilePass1** na druhý průchod kompilace značky (**MarkupCompilePass2**). Tyto soubory musí mít jejich kompilace odloženo, protože musí počkat, dokud jsou zkompilovány odkazované místně definované typy. Pokud však soubor XAML `x:Class` má <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> atribut, vygeneruje pro něj soubor kódu specifický pro daný jazyk.

Soubor XAML je lokalizovatelný, pokud obsahuje `x:Uid` prvky, které používají atribut:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

Soubor XAML odkazuje na místně definovaný typ, když deklaruje `clr-namespace` obor názvů XML, který používá hodnotu k odkazování na obor názvů v aktuálním projektu:

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

Pokud některý soubor XAML je lokalizovatelný nebo odkazuje na místně definovaný typ, je vyžadován druhý průchod kompilace značek, který vyžaduje spuštění [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) a pak [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak převést tři soubory *Page* XAML na binární formátsouborů. *Stránka1* obsahuje odkaz na `Class1`typ , který je v kořenovém oboru názvů projektu a proto není převeden na binární formát souborů v této projít kompilace značky. Místo toho [generateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) je proveden a následuje [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).

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

- [WPF MSBuild odkaz](../msbuild/wpf-msbuild-reference.md)
- [WPF MSBuild odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Odkaz na úkol MSBuild](../msbuild/msbuild-task-reference.md)
- [Vytvoření aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Přehled aplikací prohlížeče WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)