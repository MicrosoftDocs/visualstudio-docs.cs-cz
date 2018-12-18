---
title: Markupcompilepass1 – úloha | Dokumentace Microsoftu
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
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
ms.assetid: 693d6945-fd6f-4698-8f64-9dfcb71052d3
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7db6923b0a729d909e22136bd3994af45dfe1da9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189355"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1 – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> Úloh převede bez možnosti lokalizace [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] soubory do kompilovaného binárního formátu projektu.  
  
## <a name="task-parameters"></a>Parametry úlohy  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AllGeneratedFiles`|Volitelné **[] ITaskItem** výstupní parametr.<br /><br /> Obsahuje úplný seznam souborů, které jsou generovány <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> úloh.|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Volitelné **logická** parametru.<br /><br /> Určuje, jestli se má spustit úlohu v samostatném <xref:System.AppDomain>. Pokud tento parametr vrátí **false**, úloha běží ve stejném <xref:System.AppDomain> jako [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] a ten poběží rychleji. Pokud se vrátí parametr **true**, bude spuštěna úloha za sekundu <xref:System.AppDomain> , která je oddělená od [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)] a pomalejší.|  
|`ApplicationMarkup`|Volitelné **[] ITaskItem** parametru.<br /><br /> Určuje název definice aplikace [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] souboru.|  
|`AssembliesGeneratedDuringBuild`|Volitelné **String []** parametru.<br /><br /> Určuje odkazy na sestavení, které se mění během procesu sestavení. Například [!INCLUDE[TLA#tla_visualstu2005](../includes/tlasharptla-visualstu2005-md.md)] řešení může obsahovat jeden projekt, který odkazuje kompilovaném výstupu z jiného projektu. V takovém případě kompilovaný výstup druhý projekt lze přidat do **AssembliesGeneratedDuringBuild** parametru.<br /><br /> Poznámka: **AssembliesGeneratedDuringBuild** parametr musí obsahovat odkazy na kompletní sadu sestavení, které jsou generovány pomocí sestavení řešení.|  
|`AssemblyName`|Vyžaduje **řetězec** parametru.<br /><br /> Určuje krátký název sestavení, který je generován pro projekt. Například, pokud je generování projektu [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] spustitelný soubor, jehož název je **WinExeAssembly.exe**, **AssemblyName** parametr má hodnotu **WinExeAssembly**.|  
|`AssemblyPublicKeyToken`|Volitelné **řetězec** parametru.<br /><br /> Určuje token veřejného klíče pro sestavení.|  
|`AssemblyVersion`|Volitelné **řetězec** parametru.<br /><br /> Určuje číslo verze sestavení.|  
|`ContentFiles`|Volitelné **[] ITaskItem** parametru.<br /><br /> Určuje seznam dojde ke ztrátě souborů obsahu.|  
|`DefineConstants`|Volitelné **řetězec** parametru.<br /><br /> Určuje, že aktuální hodnotu **DefineConstants**, se ukládají. která ovlivňuje cílový generování sestavení; Pokud tento parametr se změní, může být změněn veřejné rozhraní API v cílové sestavení a kompilace [!INCLUDE[TLA2#tla_titlexaml](../includes/tla2sharptla-titlexaml-md.md)] soubory, které odkazují na místní typy mohou být ovlivněny.|  
|`ExtraBuildControlFiles`|Volitelné **[] ITaskItem** parametru.<br /><br /> Určuje seznam souborů, které řídí, zda opětovné sestavení se aktivuje, když <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> úlohy znovu spustí, opětovné sestavení se aktivuje, pokud jeden z těchto souborů změny.|  
|`GeneratedBamlFiles`|Volitelné **[] ITaskItem** výstupní parametr.<br /><br /> Obsahuje seznam generovaných souborů v [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] binárním formátu.|  
|`GeneratedCodeFiles`|Volitelné **[] ITaskItem** výstupní parametr.<br /><br /> Obsahuje seznam souborů generovaných spravovaného kódu.|  
|`GeneratedLocalizationFiles`|Volitelné **[] ITaskItem** výstupní parametr.<br /><br /> Obsahuje seznam lokalizace souborů, které byly vytvořeny pro každý lokalizovatelné [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] souboru.|  
|`HostInBrowser`|Volitelné **řetězec** parametru.<br /><br /> Určuje, zda je sestavení vygenerované [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)]. Platné možnosti jsou **true** a **false**. Pokud **true**, kód se generuje pro podporu hostování prohlížeče.|  
|`KnownReferencePaths`|Volitelné **String []** parametru.<br /><br /> Určuje odkazy na sestavení, která během procesu sestavování nezměníte. Zahrnuje sestavení, které jsou umístěné v [!INCLUDE[TLA#tla_gac](../includes/tlasharptla-gac-md.md)]v [!INCLUDE[TLA#tla_netframewk](../includes/tlasharptla-netframewk-md.md)] instalační adresář a tak dále.|  
|`Language`|Vyžaduje **řetězec** parametru.<br /><br /> Určuje spravovaného jazyka, který kompilátor podporuje. Platné možnosti jsou **jazyka C#**, **VB**, **JScript**, a **C++**.|  
|`LanguageSourceExtension`|Volitelné **řetězec** parametru.<br /><br /> Určuje příponu, která se připojuje k rozšíření spravovaného kódu generovaného souboru:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Pokud **LanguageSourceExtension** parametr není nastaven s konkrétní hodnotou, je použit výchozí přípona názvu souboru zdroje pro jazyk: **.vb** pro [!INCLUDE[TLA#tla_visualb](../includes/tlasharptla-visualb-md.md)], **.csharp** pro [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)].|  
|`LocalizationDirectivesToLocFile`|Volitelné **řetězec** parametru.<br /><br /> Určuje, jak generovat informace o lokalizaci pro každý zdroj [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] souboru. Platné možnosti jsou **žádný**, **CommentsOnly**, a **všechny**.|  
|`OutputPath`|Vyžaduje **řetězec** parametru.<br /><br /> Určuje adresář, ve kterém generované spravovaných souborů s kódem a [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] formát binární soubory jsou vygenerovány.|  
|`OutputType`|Vyžaduje **řetězec** parametru.<br /><br /> Určuje typ sestavení, který je generován projekt. Platné možnosti jsou **winexe**, **exe**, **knihovny**, a **netmodule**.|  
|`PageMarkup`|Volitelné **[] ITaskItem** parametru.<br /><br /> Určuje seznam [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] souborů ke zpracování.|  
|`References`|Volitelné **[] ITaskItem** parametru.<br /><br /> Určuje seznam odkazů na sestavení, která obsahují typy, které se používají v soubory [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubory.|  
|`RequirePass2ForMainAssembly`|Volitelné **logická** výstupní parametr.<br /><br /> Určuje, zda projekt obsahuje bez možnosti lokalizace [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubory, které odkazují na místní typy, které jsou vloženy do hlavního sestavení.|  
|`RequirePass2ForSatelliteAssembly`|Volitelné **logická** výstupní parametr.<br /><br /> Určuje, zda projekt obsahuje lokalizovatelné [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubory, které odkazují na místní typy, které jsou vloženy do hlavního sestavení.|  
|`RootNamespace`|Volitelné **řetězec** parametru.<br /><br /> Určuje kořenový obor názvů pro třídy, které jsou uvnitř projektu. **RootNamespace** se také používá jako výchozí obor názvů generovaného spravovaného kódu souboru, když odpovídající [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubor neobsahuje `x:Class` atribut.|  
|`SourceCodeFiles`|Volitelné **[] ITaskItem** parametru.<br /><br /> Určuje seznam souborů kódu pro aktuální projekt. Seznam neobsahuje soubory generované spravovaný kód specifický pro jazyk.|  
|`UICulture`|Volitelné **řetězec** parametru.<br /><br /> Určuje satelitní sestavení pro jazykovou verzi uživatelského rozhraní, ve kterém generované [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] binární soubory jsou vloženy. Pokud **UICulture** není nastavena, generované [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] binární soubory jsou vloženy do hlavního sestavení.|  
|`XAMLDebuggingInformation`|Volitelné **logická** parametru.<br /><br /> Když **true**, vygeneruje a součástí zkompilovaný diagnostické informace [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] k usnadnění ladění.|  
  
## <a name="remarks"></a>Poznámky  
 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> Úkol obvykle zkompiluje [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] do binárního formátu a generuje soubory s kódem. Pokud [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubor obsahuje odkazy na typy, které jsou definovány ve stejném projektu, je jeho kompilace do binárního formátu odložit **MarkupCompilePass1** do druhého průchodu kompilace kódu ( **Markupcompilepass2 –**). Tyto soubory musí mít jeho kompilace odložené vzhledem k tomu, že musíte počkat, dokud jsou zkompilovány odkazované místně definované typy. Ale pokud [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubor má `x:Class` atribut, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> generuje soubor kódu pro konkrétní jazyk pro něj.  
  
 A [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubor je lokalizovatelný obsahuje elementy, které používají-li `x:Uid` atribut:  
  
```  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Uid="Page1Uid"  
    >  
  ...  
</Page>  
```  
  
 A [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubor odkazuje na typ místně definované při deklaruje [!INCLUDE[TLA#tla_xml](../includes/tlasharptla-xml-md.md)] obor názvů, který se používá `clr-namespace` hodnota, která má odkazovat na názvový prostor v aktuálním projektu:  
  
```  
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
  
 Pokud existuje [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] souboru je lokalizovatelný nebo odkazuje na typ místně definované, překontrolovat kompilace kódu se vyžaduje, což vyžaduje spuštění [generatetemporarytargetassembly –](../msbuild/generatetemporarytargetassembly-task.md) a pak [ Markupcompilepass2 –](../msbuild/markupcompilepass2-task.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak převést tři `Page` [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] souborů do binárních souborů. `Page1` obsahuje odkaz na typ, `Class1`, který je v kořenovém oboru názvů projektu a proto není převedena na binárních souborů v tomto průchodu kompilace kódu. Místo toho [generatetemporarytargetassembly –](../msbuild/generatetemporarytargetassembly-task.md) spouští a je následována [markupcompilepass2 –](../msbuild/markupcompilepass2-task.md).  
  
```  
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
 [Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Referenční dokumentace úlohy](../msbuild/wpf-msbuild-task-reference.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Sestavení aplikace WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Přehled aplikací Prohlížeče WPF XAML](http://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)



